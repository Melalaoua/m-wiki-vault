---
type: map
title: "OAD Mobile Health System"
aliases: []
tags: [map, phd]
updated: 2026-07-14
status: stable
---

# OAD Mobile Health System

The [[OAD]] (Outil d'Aide au Diagnostic) is an Android tablet application designed to assist healthcare workers in resource-constrained settings like the Central African Republic. The system leverages a [[Syndromic Approach]], a diagnostic strategy relying on clinical signs to guide the management of conditions such as non-malarial febrile illnesses without requiring advanced laboratory confirmation. The client software is developed in [[React Native]], an open-source UI framework selected over low-code alternatives to provide complete UI/UX control, despite the higher engineering cost and need for full-stack expertise. To circumvent unreliable internet access in the field, the application implements an [[Offline-First Architecture]], prioritizing local device storage to guarantee continuous operability and automatically synchronizing databases with distant servers once network connectivity is reestablished.

## Pages in this area

- [[phd/wiki/entities/oad|OAD]]
- [[phd/wiki/concepts/offline-first-architecture|Offline-First Architecture]]
- [[phd/wiki/concepts/react-native|React Native]]
- [[phd/wiki/concepts/syndromic-approach|Syndromic Approach]]
