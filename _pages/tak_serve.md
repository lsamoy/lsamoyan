---
layout: default
title: TAK Development
filename: tak_serve.md
permalink: /tak_server
---

# Centralized TAK

## Purpose

Provide a centralized management dashboard for all TAK devices within the office. Utilized ZeroTier for network management for devices connected to the ZT subnet aligned with the TAK server.

## Instructions

Truly, this project was one of following directions for the most part. The directions for hosting the TAK server can be found here:

https://themodernham.com/create-your-own-tak-server-in-the-cloud-or-at-home/

The difficulty came with installing ZeroTier on the Raspberry Pi, and getting the Docker container which the TAK server was being hosted to to communicate with ZT. Using the ZT dashboard, we created a subnet for that can be accessed on the larger ZT network. Then, the following directions were followed to install and connect the ZT server.

https://fleetstack.io/blog/install-zerotier-on-raspberry-pi-guide


## Results

Now, as an office that does testing and utilizes TAK frequently, there was a centralized system to manage the platforms and track devices. It also allows for communication between all devices aligned, and putting them on their own subnet makes it easier to configure without damaging the larger network. It also makes them privatized so not anyone connected can access the location information and other data.
