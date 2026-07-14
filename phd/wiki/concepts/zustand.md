---
type: concept
title: "Zustand"
aliases: []
tags: [concept, phd]
updated: 2026-07-14
status: developing
---

# Zustand

Zustand is a lightweight state management solution for React applications. To avoid stale-data bugs and overlapping state concerns, best practices in applications like the [[oad-mobile-health-application]] dictate that Zustand should be used strictly for UI-side state (e.g., active step navigation, modal states, ID pointers) rather than caching domain data fetched from databases like [[RxDB]].

Source: [[notes2026oadlogtablet|OAD(log) - Tablet Database]]
