---
type: concept
title: "SELinux"
aliases: []
tags: [concept, personal]
---

# SELinux

SELinux is a [[wiki/concepts/mandatory-access-control|Mandatory Access Control]] framework heavily utilized in [[wiki/entities/red-hat-enterprise-linux|RHEL]]. It uses a type enforcement system (assigning types like `container_t` to processes and objects) to enforce strict access barriers. To achieve even deeper isolation, particularly for containerized workloads, SELinux utilizes [[wiki/concepts/multi-category-security|Multi-Category Security (MCS)]] labels, effectively sandboxing processes that share the same base type.

Source: [[unix2026the|The Insecurity of Debian]]
