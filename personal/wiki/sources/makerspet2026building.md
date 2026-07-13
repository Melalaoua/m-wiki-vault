---
type: source
title: "Building an Open-Source Robot Vacuum — Meet OOMWOO"
citekey: makerspet2026building
source_type: article
captured: 2026-07-13
site: makerspet.com
url: https://makerspet.com/blog/building-an-open-source-robot-vacuum-meet-oomwoo/
aliases: []
tags: [source, personal]
updated: 2026-07-13
status: developing
---

# Building an Open-Source Robot Vacuum — Meet OOMWOO

Original: [[personal/raw/makerspet.com/building-an-open-source-robot-vacuum-meet-oomwoo]]

Today marks the launch of [[OOMWOO]], an ambitious open-source home [[Robot Vacuum]] project by [[Maker's Pet]]. The vacuum is entirely open across hardware, firmware, and software, and is being built in public from day one.

Crucially, OOMWOO is local-first: it requires no cloud connectivity and avoids vendor lock-in by integrating natively with [[Home Assistant]]. The robot navigates using an affordable 2D LiDAR and [[ROS 2]] (via [[Nav2]]), and is designed with a 3D-printable, hackable chassis powered by a [[Raspberry Pi]] and/or [[ESP32]]. The name "OOMWOO" is notably a rotational ambigram.

Currently, the project is in its early hardware sourcing phase, but the software development environment is already live. Users can simulate the robot using [[Gazebo]] or use a "placeholder" consumer vacuum (like the Proscenic M6 Pro) to test code at home. 

The project is organized to be built massively in parallel by the maker community. Work is divided into modular "Requests for Contributions" (RFCs) available on GitHub, allowing contributors to create 3D models, reverse-engineer specs, or write navigation code simultaneously. A full Bill of Materials (BOM) will be provided for those who wish to source parts independently, though [[Maker's Pet]] will also offer an optional convenience parts kit.

## Key claims

- OOMWOO is designed to operate entirely locally, with no dependency on cloud services for its core cleaning functions. ([[personal/raw/makerspet.com/building-an-open-source-robot-vacuum-meet-oomwoo#What OOMWOO is]]) — "Local-first — no cloud needed for everyday cleaning, ever"
- The software environment for OOMWOO is already complete enough to run a simulation in a matter of minutes. ([[personal/raw/makerspet.com/building-an-open-source-robot-vacuum-meet-oomwoo#Where the project is today]]) — "You can install it and run OOMWOO (in simulation, no hardware) in, say, 15 minutes."
- The development is structured into independent modules to allow multiple community members to contribute concurrently. ([[personal/raw/makerspet.com/building-an-open-source-robot-vacuum-meet-oomwoo#Build it with me — massively in parallel]]) — "The robot and its software are split into self-contained modules (also known as Requests for Contributions)."
