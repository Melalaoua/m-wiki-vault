---
type: map
title: "Mandatory Access Control Systems"
aliases: []
tags: [map, personal]
updated: 2026-07-11
status: stable
---

# Mandatory Access Control Systems

Mandatory Access Control frameworks enforce strict access barriers within Linux environments, with distinct architectural approaches demonstrated by [[SELinux]] and [[AppArmor]]. [[SELinux]], heavily utilized in RHEL, enforces systemic granularity through a type enforcement system that assigns types like container_t to processes and objects. For deeper isolation of containerized workloads in Docker or Podman, it integrates [[Multi-Category Security (MCS)]], which assigns unique labels to fully segregate processes that share identical base type enforcements. In contrast, [[AppArmor]] serves as a path-based system enabled by default in Debian, limiting program capabilities via predefined profiles. Critics note that [[AppArmor]] default profiles for applications like Docker can be overly permissive, lacking the robust, multi-layered isolation achieved by combining [[SELinux]] and [[Multi-Category Security (MCS)]].

## Pages in this area

- [[wiki/concepts/selinux|SELinux]]
- [[wiki/concepts/apparmor|AppArmor]]
- [[wiki/concepts/multi-category-security-mcs|Multi-Category Security (MCS)]]
