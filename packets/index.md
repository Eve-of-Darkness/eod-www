---
layout: page
title: Packet Documentation
permalink: /packets/
---

This is a list of packets that you'll see while interacting with DAoC if you
ever take a peek at `Dawn of Light` or the newly formed project `Eve of
Darkness`.  **Note::** At this time UDP is not supported by the portal launcher
so these packets will not be documented at this time.

## [Client Packet Anatomy](#client-packet-anatomy)

All TCP packets that come from the client have this same general shape:

| **Segment**  | **Byte Size** | **Description**                              |
|-------------:|:-------------:|----------------------------------------------|
|       `size` | 2  | The first two bytes describe how big the data payload is|
|   `sequence` | 2  | The nth packet sent by the client                       |
|    `session` | 2  | The assigned session id assigned by the server          |
|  `parameter` | 2  | Not known yet where this is used.                       |
|         `id` | 2  | Identifies what kind of packet it is                    |
|       `data` | 1+ | The payload of the packet and is `size` bytes big       |
|   `checksum` | 2  | Checksum of the data to ensure the packet is correct    |
|-----------------------------------------------------------------------------|

Whenever this document talks about client packets it will focus on the `data`
and `id` segments only; unless otherwise specified.

## [Server Packet Anatomy](#server-packet-anatomy)

TCP packets that the server sends are far less complex and take this shape:

| **Segment** | **Byte Size** | **Description**                               |
|------------:|:-------------:|-----------------------------------------------|
|      `size` | 2             | Byte size of the data payload                 |
|        `id` | 1             | Identifies what kind of packet this is        |
|      `data` | 1+            | Payload of the packet and is `size` bytes big |
|-----------------------------------------------------------------------------|
