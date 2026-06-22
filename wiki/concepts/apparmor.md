---
type: concept
title: "AppArmor"
aliases: []
tags: [concept, personal]
---

# AppArmor

AppArmor is a path-based [[wiki/concepts/mandatory-access-control|Mandatory Access Control]] system that is enabled by default in [[wiki/entities/debian|Debian]]. It operates by limiting the capabilities of specific programs according to predefined profiles. Critics often point out that default profiles (such as those for [[wiki/entities/docker|Docker]]) can be overly permissive, lacking the systemic granularity seen in [[wiki/concepts/selinux|SELinux]].

Source: [[wiki/sources/unix2026the|The Insecurity of Debian]]
