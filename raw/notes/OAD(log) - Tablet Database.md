Today I need to do some real tryouts from the tablet to the server based on what has been done yesterday in [[OAD(log) - Server]]

I'm impressed by my quick developing speed using AI. In one afternoon I have done a month's worth of work. A huge part accounting for me checking the code, understanding it, testing it, only 10 min of code generation give or takes.

Anyway I'll now switch back to the tablet and refactor the database module. Too cluttered, lot of mistakes, repetitive calls (creating multiple patient id for no reason)

I'll refactor to the ground and do some calls from the tablet to the server.

11h00 : Applying real table to postgresql's tables based on what defined in dbdiagram.io

13h00: Looks like i needs to add a 2nd field to tutor to allow double foreign key in patients table. that's inconsitent, I need to probe later if that's not tweakable. Maybe an association table if no solutions found ?

Docker command to exit & delete all containers : 
sudo docker rm $(sudo docker ps -a -q) --force

Delete all volumes, etc :
sudo docker system prune --all --volumes
sudo docker volume rm $(sudo docker volume list -q)

To fix your current state, reset the stale Docker volume:


docker compose down -v
docker compose up
The -v flag removes the pg_data volume so PostgreSQL starts clean. After this, the migration will succeed and future restarts won't fail even if the volume somehow has partial state.


TO do on Monday : 
We need to separate database handling from UI state
That means that patient, tutor, consultations, healthstaff will be directly handled in the database instead of using Zustand as middleman.

Zustand will still be used for UI-state and pointer

The overlap risk is when you start caching RxDB data into Zustand
(e.g. storing a fetched patient object in a Zustand slice). 
That creates a dual source of truth and stale-data bugs. 
Instead, query RxDB directly in your components via its React hooks (useRxQuery) and let Zustand stay purely UI-side.


RxDB                          Zustand
─────────────────────         ─────────────────────
Patient records               Active patient ID (pointer only)
Diagnostic sessions           Current wizard step
Lab test results              Modal/drawer open state
Sync metadata                 Form draft before submission
Pathology scores              Selected filter in list view



https://rxdb.info/react-native-database.html


### Monday 30/03/2026
Arrived late this morning, did some paperworks for the thesis [[ED414-Checklist-Year1]] (CIF, CSI). 

Had launch and i'm not diggin in my to do list for today.
I've got a big refactor to do on the tablet, a healthy task. I need to decouple the data management from the Zustand. It creates double data management and is just error-prone. Instead i'll direclty interact with the database from the react components.

I'll first update my Github Board & Issue before proceeding.

14h54 : Struggling, I want to delete the whole module and startover, there is too much concerns going through my head. I don't know where to start. Each step i'm doing is cribbled with questions as : "is it efficient ? Is it the best way ? Est-ce que j'ai couvert tout les angles ? Gotta stay focused, proceed methodically. One step at a time. I gotta go back to the database schema, it's inconsistent, not answering all of my questions.


16h59 : Proceed to do a deep dive into the data and come up with a definite, solid, definition of my data models, still a lot to do.

17h59: I managed to get a first hold on my database codebase. I have fully refactored/mastered the schemas side. It's much easier to understand the rest (methods, collections). I'll need to change a lot of things made by Opus in there. AI is useful to some degrees, but if you don't understand/ agree to the code made there, you'll get utimately lost. It still a huge tool to really kickstart projects and ideas. But everything made here needs to be deepened, understood. Nonetheless, when i'll master theses codes good practices, it'll much easier and faster to use AI. As I did on the API-side where I had minimal code to change. A huge part of code malformed comes from the initial prompt.

What to do tomorrow : 
Implements the /methods /collection folders where a lot of the algorithm will move there/ be called here.
If methods & collections implemented, update the UI layers accordingly.
I have a welcoming meeting to Icube member tomorrow morning, this will definetly slow down my progress.


31 March 2026: Lock and loaded
15h25: Slowly working my way towards the collections methods. Once that is clear, I'll be able to go back to ui-side elements. 
Here what i've decided :
- Calculus fields will be separate tables or zustand-only datas.
- Encryption is handled by RxdB this removing the encryption field from the database.
- Collection will handle basic CRUD methods 
- Rest of the algorithm stays the same in src/features/diagnostic

I'm happy with the work being done, I have a clear separation of concerns, less cluttered code.

16h05: Okay all clear on collections. Now I need to dig in on hooks and how to build them. One step before switching to UI (this part scare me)

What to do tomorrow : 
Add React's hooks for the database
Add calculus to store / or database up 2 u
Implements thoses hooks inside the components
Test !



### Tuesday 1 April

Arrived at work at 10:30 am, here's what AI done immediately. 
Here's a summary of what was created under src/core/database/hooks/:

useRxQuery.ts — base primitives:

useRxQuery(queryFactory, collectionName) — subscribes to any RxDB query observable, reacts to live updates
useRxDocument(id, collectionName) — subscribes to a single document by ID
Per-collection hooks (all follow the same pattern):

- usePatients.ts	useAllPatients, usePatientById	- usePatientActions → { create, update, remove }

- useTutors.ts	useAllTutors, useTutorById	useTutorActions → { create, update, remove }

- useConsultations.ts	useAllConsultations, 
- useConsultationById, useConsultationsByPatient, - 

- useConsultationsByStaff	useConsultationActions → { create, update, archive, remove }

- useHealthStaff.ts	useAllHealthStaff, useHealthStaffById	

- useHealthStaffActions → { create, update, remove }

- useSymptoms.ts	useAllSymptoms, 

- useSymptomsByConsultation, useSymptomById 

- useSymptomActions → { create, bulkCreate, update, remove }

- useHypotheses.ts	useAllHypotheses, 

- useHypothesesByConsultation, useHypothesisById	

- useHypothesisActions → { create, bulkCreate, update, remove }

- useLabTests.ts	useAllLabTests, 

- useLabTestsByConsultation, useLabTestById	

- useLabTestActions → { create, bulkCreate, update, remove }

- useCombinedLabTests.ts	useAllCombinedLabTests, 

- useCombinedLabTestsByConsultation, useCombinedLabTestById	

- useCombinedLabTestActions → { create, bulkCreate, update, remove }
One note: useConsultationActions().archive(id) does an incrementalPatch({ status: 'archived' }) directly — this is what the consultations screen expects, but the ConsultationDocumentType schema doesn't have a status field yet. You'll need to add status to consultation.schema.ts for that action to work at runtime.

16h05 : Not proud of today. I'm struggling on implementing the database into the auth layer. I cannot manage to startup the database correclty, it run twice (normal with react in dev mode) causing a crash (cannot have 2 instance of the db). I'm confused as to why it's not retrieving the database from first instance. 

Managed to find a fix that deletes the database if this happens, and rebuilds it. But now the auth is not working ()
Code: healthStaff.collection.ts
  15 | function getCollection(): HealthStaffCollection {
  16 |  const db = getDatabase();
> 17 |  if (!db) throw new Error("Database not initialized");
     |                          ^
  18 |  return db.healthStaff;
  19 | }
  20 |

Gotta work on this after gym.


### April 2nd
Its 10 pm Spend the whole day working on this bug where database would not init correclty. I spent so much time refctoring the database module, using AI, addin libraries, removing libraries, erasing cache, hell I even refactored the android tablet.

But I finally did it, I've learnt a lot from this.

Commit & pushing, bye.

### April, the 7th

##### Plan: Introduce a Repository/Service layer between RxDB and the UI
---
###### Current State

- **`usePatientStore`** (zustand) = `useDiagnosticStore` which only contains **UI state**: `NavSlice` (step navigation) + `PanelSlice` (panel ordering/views)
- **Data fields** like `patientInfo`, `setFieldData`, `entryPoint`, `symptoms`, `hypotheses`, `labTests` are still referenced by UI components (e.g. [PatientInfoForm.tsx:53](vscode-webview://115akg0fae33gd2smll3hhja6h3faqs8jdi7u4912rs0chpiblue/src/features/patient/components/patientForm/PatientInfoForm.tsx#L53), [useEntryPointValidation.ts:10](vscode-webview://115akg0fae33gd2smll3hhja6h3faqs8jdi7u4912rs0chpiblue/src/features/diagnostic/hooks/validation/useEntryPointValidation.ts#L10)) but their slices have been **removed** from the store — they should now live in RxDB
- **Database** ([database.ts](vscode-webview://115akg0fae33gd2smll3hhja6h3faqs8jdi7u4912rs0chpiblue/src/core/database/database.ts)) has collection types defined (`PatientCollection`, `ConsultationCollection`, etc.) but `OADDatabaseCollections` currently only exposes `healthstaff` — the rest are commented out
- The DB is accessed via a singleton `getDb()` / `initializeDb()`

###### Architecture: Repository + React Hook pattern

Instead of using RxDB documents directly in components, introduce a **repository layer**:

```
UI Component → usePatient() hook → PatientRepository → RxDB Collection
```

- **`PatientRepository`** — plain class/module with methods like `create()`, `findById()`, `update()`. Operates on RxDB collections, returns plain data (not RxDocuments)
- **`usePatient()` hook** — subscribes to RxDB observables (via `query.$.subscribe()`), exposes reactive data + mutation functions to components
- **Zustand store** — remains for UI-only state (nav steps, panels, drawer)

##### Phase 1: Handle "New Patient" creation

Here are the specific modifications:

###### 1. Uncomment `patients` collection in `OADDatabaseCollections`

In [database.ts:44](vscode-webview://115akg0fae33gd2smll3hhja6h3faqs8jdi7u4912rs0chpiblue/src/core/database/database.ts#L44), uncomment `patients: PatientCollection` and add it to the `initializeDb()` collection setup.

###### 2. Create `src/core/database/repositories/patientRepository.ts`

```typescript
// Methods:
// - createPatient(data: PatientData): Promise<string>  → inserts into RxDB, returns patient ID
// - getPatient$(id: string): Observable<PatientDocumentType | null>  → observable for reactivity
// - updatePatient(id: string, fields: Partial<PatientData>): Promise<void>
```

The repository uses `getDb().patients` internally. It maps between `PatientData` (app types) and `PatientDocumentType` (DB schema).

###### 3. Create `src/features/patient/hooks/usePatient.ts`

```typescript
// - Wraps patientRepository with React state via useEffect + subscribe
// - Exposes: { patient, createPatient, updateField, isLoading }
// - On createPatient: calls repo.createPatient(), stores the returned ID in zustand as a pointer
// - Subscribes to repo.getPatient$(id) for reactive updates
```

###### 4. Add `currentPatientId` to zustand store

In [patientStore.ts](vscode-webview://115akg0fae33gd2smll3hhja6h3faqs8jdi7u4912rs0chpiblue/src/core/store/patientStore.ts), add a `currentPatientId: string | null` field + `setCurrentPatientId` action. This is the **pointer** from zustand to the RxDB document.

###### 5. Update `PatientInfoForm` to use `usePatient()`

Replace `usePatientStore((state) => state.patientInfo)` and `state.setFieldData` with the new hook's `patient` and `updateField`.

###### 6. Update `useEntryPointValidation`

Replace zustand selectors for `patientInfo.*` with values from `usePatient()`.

---

##### Next Steps (after Phase 1)

1. **Phase 2 — EntryPoints**: Same pattern for `entryPoint` data → `EntryPointRepository` + `useEntryPoint()` hook
2. **Phase 3 — Symptoms**: `SymptomsRepository` + `useSymptoms()` hook
3. **Phase 4 — Hypotheses**: `HypothesesRepository` + `useHypotheses()` hook
4. **Phase 5 — Lab Tests**: `LabTestsRepository` + `useLabTests()` hook
5. **Phase 6 — Consultations/Results**: Final data entities
6. **Phase 7 — Cleanup**: Remove all dead zustand data slices, old test mocks referencing `usePatientStore.getState().patientInfo`, update tests to use repository mocks

Each phase follows the same pattern: **Repository → Hook → Update consumers → Test**.

Prompt to model claude sonnet 4.6 (medium effort) : 
\<context>1. **Phase 1 — EntryPoints**: Same pattern for `entryPoint` data → `EntryPointRepository` + `useEntryPoint()` hook 2. **Phase 2 — Symptoms**: `SymptomsRepository` + `useSymptoms()` hook 3. **Phase 3 — Hypotheses**: `HypothesesRepository` + `useHypotheses()` hook 4. **Phase 4 — Lab Tests**: `LabTestsRepository` + `useLabTests()` hook 5. **Phase 5 — Consultations/Results**: Final data entities 6. **Phase 6 — Cleanup**: Remove all dead zustand data slices, old test mocks referencing `usePatientStore.getState().patientInfo`, update tests to use repository mocks Each phase follows the same pattern: **Repository → Hook → Update consumers → Test**.\</context>
\<task>Complete phase 1\</task>
\<requirements> Use jcodemunch-mcp for code lookup whenever available. Prefer symbol search, outlines, and targeted retrieval over reading full files. Use context7 for libraries documentation.\</requirements>

15h47: I'm going -almost- from scratch again. Taking what's been done with the AI and refactoring other things, almost clean slate. I'm progressing, and i feel more motivated and lost when i break things and rebuild them.

== Break for my psy seance ==
Where to pick up after : 
- Create a store from zustand after (lets get back to it) ask the AI about it
- Add a middle man to sync automatically to the repo
- Update UI to use the store
- Keep the DiagnosticDataprovider strategy, works well


Okay I need to shift the UX flow for the app. Instead of jumping directly into the diagnostic. We need to bump into the home of the user/healthstaff.

Diagnostic is entered through a button, which will lead to patient onboarding (exists or not ?) and then consultation creation. doing so will avoid all the headache on fetching the patient if exist while filling the consultation etc etc.

18h24: Did a lot of cleaning of the repository, much more clean now, take a long break.

Where to pick up after :
Add New patient (look up for existing)
Add New Consultation (after patient is set)
Use the proper hooks and call repositories in the UI components.

22h10 : Managed to have working onboarding patient, working components. 


What to do next : 
- Apply the diagnostic Engine to the components and the database
- Patient refetching not working (not saved ?)
- Modifying fields is laggy since it's making request at every modification



### April, the 9th
Struggled a long time with AI trying different strategy, engulfing myself in a botomless pit of refactoring.

Decided to go clean slate but using scrapes from the work done by the AI. I'm learning a lot from this, i'm understanding what important pieces i need to build first in software. Defining my models and building from this is important. Defining my types from theses models will structurate the rest of my app onward.

I managed to build up the dEngine (diagnostic Engine) from the ashes of the previous one. Cleaner, better separation of concern.

What needs to be done tomorrow : 
- Refactor the Store
- Refactor the UI.

### April, the 14th.

Refactored the repositories based on the new types. Realized that my data types were inversed : i should be coming FROM the database types and not the opposite way. correcting this now.

I'll go full on the models-repository-services pattern. Neeeds to refactor again repositories. 17h15 : done

Proceeding to the creation of the DiagnosticService (using AI) : Almost finished

What do next :
- Add calculus to database ? Since we moving to subscribing directly from database and avoiding to store any data in double. Or we can rebuild the calculus everytime. 
- Remove patientStore remnants
- Components will subscribe (hooks usePatient useConsultation).
- Components will use DiagnosticService passing their consultation & patient instances
- Rebuild the UI (use the old versions but cleaner)


### April, the 15th

I created the new CalculusSlice from the patientStore that effectively tracks the calculus in memory. Rewrote the diagnosticService to be stateless and requires the calculus in input.
Had some errors on my repository. But I managed to work properly with proper typescript types. I realize the importance to have good types system setup, it influence everything downstream. 
Lunch break, I'll switch to components and UI, last step before final test for API server.

After intensive use of AI, and some git issues, the app now starts with minimal functionality. Components and UI is not reintegrated yet but atleast core seems to starts properly.


### April, the 16th

Bad day

### April, the 17th
started digging in the UI coded by the AI yesterday. It's really good but it needs a LOT of polish, it feels soul-less.

I managed to refactor the side and top bar nav.
I slowly started to replace mock data with database calls. I'm progressing without many errors or issues.

What's needs to be done : 
- Go page by page and remove mock data : what's alrready done is index.ts | patients.ts.
- Once mock data is gone : needs to polish the UI and test if everything checks out dynamically
- After that : need to retest the app if everything is good (dEngine jest testing)
- I need to build the list of potential tablets for the app and send them to ESI for a proper "devis" (whats the english word?).



### April, the 20th
Worked on the diagnostic flow (page consultation)
It went pretty messy using AI, I struggled without AI, and finished by using AI.
I think i need to clean-slate this part (only this part) because it's getting messy again.

I'm lacking time so I need to decide what to do quick.
I haven't sent the devis to ESI, too.

I fixed the consultation onboarding.
However clicking symptoms etc seems laggy & clunky
I need to investigate this tomorrow.


### April, the 21th
