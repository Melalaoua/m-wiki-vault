---
type: concept
title: "RxDB"
aliases: []
tags: [concept, phd]
updated: 2026-07-14
status: developing
---

# RxDB

RxDB (Reactive Database) is a local, NoSQL, offline-first database for JavaScript applications. In the [[oad-mobile-health-application]], it serves as the foundational data layer, providing reactive queries (via observables) that synchronize seamlessly with UI components through custom React hooks. Utilizing RxDB directly for domain data prevents the dual-source-of-truth problems often encountered when caching database records in state managers like [[Zustand]].

Source: [[notes2026oadlogtablet|OAD(log) - Tablet Database]]
