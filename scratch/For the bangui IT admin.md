Action summary (your Q18 request)

1. Information to get from the Bangui technical admin

Ask all seven at once — a second round trip costs days:

1. Relay hostname and port. Submission on 587, implicit TLS on 465, or an internal relay on 25?
2. Credentials — username and password, and whether they can issue an application-specific one rather than sharing a human's.
3. Which sending domain is authorised, i.e. what may appear in From:. This is the one that silently ruins everything: if SPF/DKIM don't align with the domain we send as, mail is spam-foldered or bounced with no error we can detect.
4. Is outbound 587/465 open from the server's network? Many hosts block outbound mail ports by default and it is a support-ticket fix, not a config one.
5. Per-message recipient caps or rate limits. We fan out one message to every active expert as envelope recipients; a relay capping recipients-per-message would need a different strategy.
6. A monitored mailbox for Reply-To, or confirmation that replies should go nowhere.
7. TLS specifics — is STARTTLS mandatory, and is the certificate publicly trusted or self-signed? A self-signed cert needs explicit handling rather than a silent failure.

8. What you do once you have the answers

9. Fill the new keys in the server's .env: SMTP_HOST, SMTP_PORT, SMTP_USERNAME, SMTP_PASSWORD, SMTP_TLS, SMTP_FROM, SMTP_REPLY_TO. (I'll add them to .env.example and to the api service's environment block in docker-compose.yml as part of the D work — you only fill values.)
10. Restart the api container. The migration runs itself at startup via main.py.
11. Add at least one active recipient before any tablet completes a case. Per Q13 an empty roster returns 503, so cases queue rather than deliver — correct, but it looks like an outage if you weren't expecting it.
12. Run list_devices.py, then grant_recipient_admin.py for any tablet enrolled after the migration. Devices enrolled before it are already flagged, per Q21(b).
13. Send one real test case and check where it lands — with both a Gmail recipient and an institutional one. This is the step that catches the deliverability problem from Q4, and nothing in the code can catch it for you: from the server's side a spam-foldered mail and a delivered mail are identical.

14. What to hand the implementing agent

Don't hand it a prompt carrying twenty-four decisions — it'll drift. The right move is that I write the settled decisions into docs/handoffs/oad-server-case-notification.md as a dated decisions section, since that document is already the canonical spec for this feature and already travels between the two repos. Then the prompt is short and the spec is the contract:

Implement work item B of docs/handoffs/oad-server-case-notification.md,
following the "Decisions — 2026-08-17" section of that document exactly.
Match the conventions in api/README.md: uv add for dependencies, one
migration off head b2f1a4d57c80, models registered in models/__init__.py
and in the asserted table set in tests/test_models_package.py.
Gates: uv run pytest, uv run ty check, uv run ruff check . — all clean.

Then the same for C+D as the second change, per Q22(c).
