---
type: raw
source_type: article
title: "The Insecurity of Debian"
url: https://unix.foo/posts/insecurity-of-debian/
site: unix.foo
captured: 2026-06-22
byline: Cyrus
tags: [personal]
---

In June of 2023 Red Hat made a controversial decision to change how they distribute the source code behind Red Hat Enterprise Linux (RHEL). There have been a lot of keyboards tapped angrily across social media that left many uncertain about the ramifications of the decision. There were many questions about the future viability of downstream rebuilds of RHEL affecting distributions like Rocky Linux, AlmaLinux, Oracle Linux, and others. Each have since made announcements to try and calm their communities.

Still. Many in the open source community have interpreted Red Hat’s decision for what it really was: A dick move.

There has been a steady uptick of people stating that they will migrate (or already have) to Debian – seeking refuge from what they see as greedy corporate influence. I understand the sentiment fully. However, there’s a problem here that I want to talk about: security.

The ugly truth is that security is hard. It’s tedious. Unpleasant. And requires a lot of work to get right.

Debian does not do enough here to protect users.

Long ago, Red Hat embraced the usage of [SELinux](https://en.wikipedia.org/wiki/Security-Enhanced_Linux) . And they took it beyond just enabling the feature in their kernel. They put in the arduous work of crafting default SELinux policies for their distribution.

These [policies ship enabled by default](https://www.redhat.com/sysadmin/selinux-kata-containers) in their distribution. The policies help protect a variety of daemons that run by default on RHEL, as well as many of the most popular daemons folks tend to use on the server.

Apache, nginx, MariaDB, PostgreSQL, OpenSSH, etc. are all covered by SELinux policies that ship on RHEL distributions.

The protection even extends to containers. Containers are increasingly the preferred method for developers to deploy their software – myself included. A common misconception is that if you run something in a container, it’s inherently secure. This is absolutely not true. Containers by themselves do not solve a security problem. They solve a software distribution problem. They give a false impression of security to those that run them.

On Red Hat based distributions, you can use a drop-in Docker alternative named podman which allows you to run containers without needing a daemon (unlike Docker) and it provides other benefits like being able to run fully root-less. But Red Hat takes it a step further here and applies strong default SELinux policies that separate the container from the host OS and even from other containers!

There have been numerous [examples](https://www.redhat.com/en/blog/latest-container-exploit-runc-can-be-blocked-selinux?intcmp=701f20000012ngPAAQ) of being able to escape from a container and touch the host OS or other containers. This is where tools like SELinux step in. The application of SELinux policies on a container allows for a hardened sarcophagus to place your application in which mitigates the risk of unknown future exploits. And it’s nearly effortless to use on RHEL.

Red Hat was aware that unless they put in the work on these default policies, their users would simply not embrace the technology and millions of servers would remain vulnerable. Because let’s be real here. SELinux is hard. The policy language and tooling is cumbersome, obtuse, and is about as appealing as filling out tax forms. It frankly sucks to use – if you are manually creating your own policies that is.

But due to the work Red Hat has put in, the usage of SELinux on RHEL is mostly transparent and provides real security benefits to their users.

## [Debian’s Approach](#debians-approach)

Debian, a stalwart of the open-source community, is revered for its stability and extensive software library. I am a fan and [donate](https://www.debian.org/donations) to the project every year (you should too!) even though I don’t run it in production environments.

However, its default security framework leaves much to be desired. Debian’s decision to enable [AppArmor](https://en.wikipedia.org/wiki/AppArmor) by default starting with version 10 signifies a positive step towards improved security, yet it falls short due to the half-baked implementation across the system.

Debian’s reliance on AppArmor and its default configurations reveals a systemic issue with its approach to security. While AppArmor is capable of providing robust security when properly configured, Debian’s out-of-the-box settings fail to leverage its full potential:

**Limited Default Profiles:** Debian ships with a minimal set of AppArmor profiles, leaving many critical services unprotected.

**Reactive vs. Proactive Stance:** Debian’s security model often relies on users to implement stricter policies, rather than providing a secure-by-default configuration.

**Inconsistent Application:** Unlike SELinux in Red Hat systems, which applies to the entire system consistently, AppArmor in Debian is applied piecemeal, leading to potential security gaps.

**Lack of Resources:** Debian as a community-driven project lacks the resources to develop and maintain comprehensive security policies comparable to those provided by Red Hat.

It’s very common for folks to run container workloads on Debian via Docker – which [does automatically generate](https://docs.docker.com/engine/security/apparmor/) and load a default AppArmor profile for containers named `docker-default`. Unfortunately, it’s not a very strong profile for security and is overly permissive.

This profile, while providing some protection, [leaves significant attack surfaces](https://github.com/moby/moby/blob/master/profiles/apparmor/template.go) exposed. For instance:

```
  network,
  capability,
  file,
  umount,
  # Host (privileged) processes may send signals to container processes.
  signal (receive) peer=unconfined,
  # runc may send signals to container processes (for "docker stop").
  signal (receive) peer=runc,
  # crun may send signals to container processes (for "docker stop" when used with crun OCI runtime).
  signal (receive) peer=crun,
  # dockerd may send signals to container processes (for "docker kill").
  signal (receive) peer={{.DaemonProfile}},
  # Container processes may send signals amongst themselves.
  signal (send,receive) peer={{.Name}},
  deny @{PROC}/* w,   # deny write for all files directly in /proc (not in a subdir)
  # deny write to files not in /proc/<number>/** or /proc/sys/**
  deny @{PROC}/{[^1-9],[^1-9][^0-9],[^1-9s][^0-9y][^0-9s],[^1-9][^0-9][^0-9][^0-9/]*}/** w,
  deny @{PROC}/sys/[^k]** w,  # deny /proc/sys except /proc/sys/k* (effectively /proc/sys/kernel)
  deny @{PROC}/sys/kernel/{?,??,[^s][^h][^m]**} w,  # deny everything except shm* in /proc/sys/kernel/
  deny @{PROC}/sysrq-trigger rwklx,
  deny @{PROC}/kcore rwklx,
  deny mount,
  deny /sys/[^f]*/** wklx,
  deny /sys/f[^s]*/** wklx,
  deny /sys/fs/[^c]*/** wklx,
  deny /sys/fs/c[^g]*/** wklx,
  deny /sys/fs/cg[^r]*/** wklx,
  deny /sys/firmware/** rwklx,
  deny /sys/devices/virtual/powercap/** rwklx,
  deny /sys/kernel/security/** rwklx,
```

The **network** rule allows all network-related syscalls without restriction.

The **capability** rule, without specific denials, permits most capabilities by default.

The **file** rule grants broad file access permissions, relying on specific deny rules for protection.

## [AppArmor vs. SELinux](#apparmor-vs-selinux)

The fundamental difference between AppArmor and SELinux lies in their approach to Mandatory Access Control (MAC). AppArmor operates on a path-based model, while SELinux employs a significantly more complex type enforcement system. This distinction becomes particularly evident in container environments.

SELinux applies a type to every object in the system - files, processes, ports, you name it. When you launch a container on a SELinux-enabled RHEL system, it’s immediately assigned the **container\_t** type – a strict access control mechanism. The **container\_t** type effectively cordons off the container, preventing it from interacting with any object not explicitly labeled for container use.

But SELinux doesn’t stop at type enforcement. It takes container isolation a step further with [Multi-Category Security (MCS)](https://en.wikipedia.org/wiki/Multi_categories_security) labels. These labels function as an additional layer of segregation, ensuring that even containers of the same type (**container\_t**) remain isolated from each other. Each container gets its own unique MCS label, creating what amounts to a private sandbox within the broader **container\_t** environment.

AppArmor, in contrast, doesn’t concern itself with types or categories. It focuses on limiting the capabilities of specific programs based on pre-defined profiles. These profiles specify which files a program can access and which operations it can perform. While this approach is more straightforward to implement and understand, it lacks the granularity and system-wide consistency of SELinux’s type enforcement. Almost no mainstream Linux distribution distributes comprehensive AppArmor profiles for all common network-facing daemons by default.

The practical implications of these differences are significant. In a SELinux environment, a compromised container faces substantial hurdles in accessing or affecting the host system or other containers, thanks to the dual barriers of type enforcement and MCS labels.

This isn’t to say one is universally superior to the other. SELinux offers more robust isolation but at the cost of increased complexity and potential performance overhead. AppArmor provides a simpler, more approachable security model that can still be quite effective when configured properly. The root of my point though is that Red Hat has put in the work here to make the use of SELinux and containers seamless and easy for its users. You aren’t left to fend for yourself.

In the end, the choice between Debian and Red Hat isn’t just about corporate influence versus community-driven development. It’s also a choice between a system that assumes the best and one that prepares for the worst. Unfortunately in today’s highly connected world, pessimism is a necessity.
