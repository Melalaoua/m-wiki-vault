---
type: source
title: "OAD(log) - Tablet Database"
citekey: notes2026oadlog
source_type: article
captured: 2026-07-14
site: notes
url: 
aliases: []
tags: [source, phd]
updated: 2026-07-14
status: developing
---

# OAD(log) - Tablet Database

Original: [[raw/notes/OAD(log) - Tablet Database]]

This log covers a major architectural refactoring of the [[OAD Mobile Health Application]] (tablet) from late March to mid-April 2026. The work primarily focused on decoupling database handling from UI state management, aiming to support a robust [[Offline-First Architecture]] for the [[OAD]] project.

### Architectural Shift: RxDB and Zustand
The initial architecture suffered from data overlap risks by caching [[RxDB]] data directly into [[Zustand]] (e.g., storing fetched patient objects in a Zustand slice). This created a dual source of truth and led to stale-data bugs. The refactor enforced a strict boundary:
- **[[RxDB]]**: Handles all domain data (Patient records, Diagnostic sessions, Lab results, Sync metadata, Pathology scores).
- **[[Zustand]]**: Strictly reserved for UI state (Active patient ID pointers, current wizard steps, modal states, form drafts).

### Model-Repository-Service Pattern
To prevent React components from coupling directly to RxDB documents, a Repository layer was introduced. The new flow dictates:
`UI Component -> usePatient() hook -> PatientRepository -> RxDB Collection`
- **Repositories** interact with RxDB collections and return plain data.
- **Hooks** subscribe to RxDB observables for reactivity.
- **Types** were inverted to derive *from* the database schemas rather than the app types, establishing the database as the foundational source of truth.

### Diagnostic Engine and AI Code Generation
The Diagnostic Engine (`dEngine`) was rebuilt into a stateless `DiagnosticService` that relies on a `CalculusSlice` for in-memory calculations. Throughout this month-long refactor, AI (Claude) was heavily utilized. While the AI provided immense initial speed (e.g., writing the CRUD hooks and API boilerplate), it also introduced complexity and 'soulless' UI that required extensive manual refactoring. The author noted that utilizing AI effectively requires a deep, pre-existing mastery of the architecture and data models.

Additionally, administrative tasks for the [[PhD]] (CSI, CIF) were completed during this period, and plans were made to procure physical tablets for field testing.

## Key claims

- Storing fetched database objects in a UI state manager creates a dual source of truth and causes stale-data bugs. ([[raw/notes/OAD(log) - Tablet Database#TO do on Monday :]]) — "The overlap risk is when you start caching RxDB data into Zustand (e.g. storing a fetched patient object in a Zustand slice). That creates a dual source of truth and stale-data bugs."
- Software types and data models should be derived from the database types, not vice versa. ([[raw/notes/OAD(log) - Tablet Database#### April, the 14th.]]) — "Realized that my data types were inversed : i should be coming FROM the database types and not the opposite way. correcting this now."
- AI code generation can cause severe confusion if the developer does not fully understand or agree with the underlying architecture it produces. ([[raw/notes/OAD(log) - Tablet Database#17h59:]]) — "AI is useful to some degrees, but if you don't understand/ agree to the code made there, you'll get utimately lost."
