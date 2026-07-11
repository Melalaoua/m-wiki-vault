---
type: concept
title: "Multi-Category Security (MCS)"
aliases: []
tags: [concept, personal]
---

# Multi-Category Security (MCS)

Multi-Category Security (MCS) is an access control mechanism typically used in conjunction with [[selinux|SELinux]]. It provides an additional layer of isolation by assigning unique labels to processes. In container environments like [[wiki/entities/docker|Docker]] or [[wiki/entities/podman|Podman]], MCS ensures that even containers operating under the identical type enforcement (e.g., `container_t`) remain fully segregated from one another.

Source: [[unix2026the|The Insecurity of Debian]]
