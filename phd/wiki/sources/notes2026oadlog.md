---
type: source
title: "OAD(log) - MVP Sprint"
citekey: notes2026oadlog
source_type: article
captured: 2026-07-13
site: notes
url: 
aliases: []
tags: [source, phd]
updated: 2026-07-13
status: developing
---

# OAD(log) - MVP Sprint

Original: [[raw/notes/OAD(log) - MVP Sprint]]

After completing [[OAD(log) - Server]] and [[OAD(log) - Tablet Database]], it's time to do a final sprint for the MVP targetting 29th may for a trip to Africa 8th june

### To do 
- Serveur distant fonctionnel et communiquant avec l'[[OAD]] : les données sont effectivement centralisées.
- Secteur Traitement intégré dans le flux diagnostique.
- Changement onboarding enfant : renseigner le nom/prénom au lieu des initiales (le patient peut être retrouvé plus facilement).
- Mise en place d'un admin/superviseur par tablette (username & mot de passe connus). Seuls ces derniers peuvent créer des comptes "classiques" soignant : chaque compte (soignant, admin, superviseur) décrypte la base de données.
- De facto avec le point précédent : les informations du compte soignant seront systématiquement renseignées dans la consultation pour traçage.  
- Détection de symptome qui requiert l'âge et automatiquement coché selon l'âge de l'enfant.
- Commentaires quantitatifs sur les tests rapides.
- Secteur Mailing automatique : basse priorité mais objectif à intégrer -> informer au plus vite si ce dernier n'est pas réalisable (pour coordonner les opérations sur le terrain pendant l'étude).

### April, the 27th
I did final tests to check if tablet & server communicate, it works. Further tests required to check the system is resilient.
I migrated the initials field to firstname & lastname for patients
Added healthstaff firstname & lastname to consultation data.

### May, the 04th 
I made good progress today. Once again, AI helped me a lot. I found a good rythm on how to work with it. I build a consistent prompt (improved a lot which details to give or not), AI comes back with a fully laid out plan, i read it all, AI implement, I review every file written and I test, rince & repeat.

I'm learning vim with a new editor ([[Zed]]) on top of it, once i get the hand of it i'll manage to code and navigate much faster.

Looking at the checklist : 
- I still to do the treatment category.
- Some small requests on quality of life using the [[OAD Mobile Health Application|app]].
- rebuild the final UI.

### May, the 06th
Implemented the treatments, it's currently flawed and I detected many bugs in the excel version. Some key features are missing on my end (calculate the dosage depending on weight, age, etc...)
I need to add testing on treatments.

### May, the 07th
Didn't work today, had a meeting with the colleagues today.
Papier Oxford même objectifs que OAD. Durée du diagnostic trop long => timer les consultations.
RUNNING OUT OF TIIIME

### May, the 08th
The excel is too inconsistent, too noisy. The id doesn't match, the underlying system is not typed correctly. IT's a nightmare to work in this conditions. We NEED to emancipate the app from this excel otherwise it's going straight to the wall.
Wanted to do some testing but the excel is still full of bug again.
I have to do testing manually, for real.

### May, the 10th
I used [[Claude|claude Design]] to redefine the UI of the OAD app. I'm satisfied with the proposed content. Much better than what I did. I'll try implementation with [[Claude|claude Code]] now.

### May, The 11th
UI v4 is almost fully integrated, much cleaner, much more complete. Need a lot of polishing though.
What to do tomorrow :
- Onboarding doesnt' seems to trigger properly, check
- Login flow need to be polished
- Patient/consultation is not consistent when switching tabs, need to investigate this.
- Symptoms select needs to be more clear, symptom grouping is bugged.
- Add timer to consultation
- Add numerical values to labtests
- Add auto toggle for specific symptoms

### May, the 12th
Finished & polished the auth flow, migrated UI to use [[Tamagui]] tokens instead of stylesheet.
Progression : nominal.
What to do tomorrow : same as yesterday.

### May, the 13th
Need to keep in store the currentConsultationId / currentPatientId to allow switching freely the page of the app without loosing progression.
Switch steps in current consultation loose the data entrypoint restore to base, patient step restore to base.
Switch to full [[Tamagui|tamagUI]]

### May, the 14th
Made tremendous achievments today.
Managed to code with multiple claude agents each on a separate branch. Interacting with them while doing my own things on my branch was fairly easy. It's a bit boring to code manually now knowing they can do much more must faster.
I'm getting a better hand on how to manage them effectively and how to distribute my tasks rapidly.
I've made good progress on the UI on the task. Lot more to do.

### May, the 15th
Realizing how fast i'm working with AI.
For instance today : 
One agent is doing all the auth flow for the app : adding [[JWT]] auth, [[Caddy]] implementation.
On the other hand i'm interacting with multiple agent on the UI.
Very impressive.

Update 17h16: Finished the JWT auth, need to be battle-tested. AI is very powerful to ship product rapidly, i need to be wary to read every line, understand every concept, to avoid loosing my grip on my codebase (happent multiple time before, needed to clean slate everytime).

### May, the 18th
Feedback from opus 4.7 : 

__Engine ruleset version is not snapshotted on consultations__
The consultation document stores `hypotheses[].p0` (good — priors are frozen), but **nowhere** captures the version of `pathologies.json`, `decayDelta.json`, `thresholds.json`, `treatments.json` used. Implications:
- Purpose #5 (impact study before/after) becomes hard to audit: which weights produced which recommendation?
- A clinician disputing a recommendation later cannot reproduce it.
- Treatments and decay weights change → historical consultations look inconsistent in dashboards.
Add `engineVersion: string` (or a hash of the bundled JSON) to the consultation schema and stamp it at `initDiagnosis`. Cheap, irreversible benefit.

__`healthStaff` is not in `SYNC_COLLECTIONS`, but consultations reference `healthStaffId` `src/core/database/sync/config.ts:3`.__
Every device generates its own staff UUIDs (PIN-bound, never synced). When consultations sync to the server, `health_staff_id` values from different devices live in different namespaces. For purposes 5–6 (study impact, socio-economic analysis), you cannot:
- Identify the same clinician across devices.
- Compute per-clinician performance.
- Detect duplicate enrollments.
You probably need a server-issued staff identity (or a deterministic mapping at enrollment).

12h22: Switching user keeps highlights some caveats : 
Dashboard is displaying overall data (should be only the user)
Patients counter is displaying overall data (should be only the user)

### May, the 21th
Need to add disconnect button
Remove taille
Retirer urgence.

### May, the 26th
TODO : Add notes to alembic and sqlAlchemy tables in [[OAD Technical Infrastructure and Evaluation|OAd Server]]

### May, the 29th
Mvp is aimed to be released today in beta. Worked a lot with AI this week, much faster, quicker, better.
I'll finally start my [[PhD]] bibliography now. June will be insightful.

### Expo and ADB Issues
Your build is fine and Metro is fine. The problem was **discovery**, not connectivity:
- This is an **expo-dev-client** build. Its launcher screen finds dev servers by scanning the local network via mDNS (`_expo._tcp.local`).
- Your phone is connected over **USB**, not sharing a LAN with your machine — so mDNS finds nothing and the launcher shows "no server detected."
- Meanwhile `adb reverse tcp:8081 tcp:8081` *was* already routing the phone's `localhost:8081` to your machine's Metro. The launcher just never tried that address on its own.

## How to connect (any of these)
1. **In the dev launcher UI on the phone** — tap **"Enter URL manually"** and type `http://localhost:8081`. This is the normal manual path.
2. **From your machine**:
   ```bash
   adb reverse tcp:8081 tcp:8081
   adb shell am start -a android.intent.action.VIEW \
     -d "oad://expo-development-client/?url=http%3A%2F%2Flocalhost%3A8081" \
     com.oad.strasbourg
   ```

## Key claims

- Relying on inconsistent and untyped Excel models for the diagnostic app causes critical development bottlenecks. ([[raw/notes/OAD(log) - MVP Sprint#### May, the 08th]]) — "The excel is too inconsistent, too noisy. The id doesn't match, the underlying system is not typed correctly. IT's a nightmare to work in this conditions. We NEED to emancipate the app from this excel otherwise it's going straight to the wall."
- Deploying multiple AI agents on separate git branches significantly accelerates feature implementation. ([[raw/notes/OAD(log) - MVP Sprint#### May, the 14th]]) — "Managed to code with multiple claude agents each on a separate branch. Interacting with them while doing my own things on my branch was fairly easy."
- Failing to snapshot the underlying ruleset version in medical consultations jeopardizes the auditability and reproducibility of the clinical impact study. ([[raw/notes/OAD(log) - MVP Sprint#### May, the 18th]]) — "The consultation document stores hypotheses[].p0 (good — priors are frozen), but nowhere captures the version of pathologies.json... Purpose #5 (impact study before/after) becomes hard to audit: which weights produced which recommendation?"
- Local device-generated UUIDs for staff accounts break long-term clinical data analysis when synced to a centralized server. ([[raw/notes/OAD(log) - MVP Sprint#### May, the 18th]]) — "Every device generates its own staff UUIDs (PIN-bound, never synced). When consultations sync to the server, health_staff_id values from different devices live in different namespaces... you cannot: Identify the same clinician across devices."
