---
layout: page
title: Packet Documentation
permalink: /packets/
---

This is a list of packets that you'll see while interacting with DAoC if you
ever take a peek at `Dawn of Light` or the newly formed project `Eve of
Darkness`.  **Note::** At this time UDP is not supported by the portal launcher
so these packets will not be documented at this time.

-------------------------------------------------------------------------------

## How to Read Packet Formats

Packet formats detailed later in this document are notated in Elixir binary
format for ease of reading.  For a quick reference here is a packet where the
first bit of the first byte is an on/off flag and the last 5 bits are an
integer detailing an id of some kind.  Following that is a field of 24 bytes
for a short description.

```elixir
<<on_off::1, _::2, system_id::5, short_desc::bytes-size(24)>>
```

[Here](https://hexdocs.pm/elixir/Kernel.SpecialForms.html#%3C%3C%3E%3E/1) is a
link for a more in depth explanation of the binary matching.

-------------------------------------------------------------------------------

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

-------------------------------------------------------------------------------

## [Server Packet Anatomy](#server-packet-anatomy)

TCP packets that the server sends are far less complex and take this shape:

| **Segment** | **Byte Size** | **Description**                               |
|------------:|:-------------:|-----------------------------------------------|
|      `size` | 2             | Byte size of the data payload                 |
|        `id` | 1             | Identifies what kind of packet this is        |
|      `data` | 1+            | Payload of the packet and is `size` bytes big |
|-----------------------------------------------------------------------------|

All server packets will be referenced with their `id` and the `data` unless
otherwise specified.

-------------------------------------------------------------------------------

## [Client Packets](#client-packets)

* [0xF4 Handshake Request](#client-0xF4)
* [0xA7 Login Request](#client-0xA7)
* [0xA3 Ping Request](#client-0xA3)







-------------------------------------------------------------------------------

#### [0xF4 Handshake Request](#client-0xF4)

This is the first packet that the client sends when the game client attempts to
connect to the server.  In this packet is information about the client.  Here
is the breakdown of the packet data structure:

```elixir
<<addons::4, type::4, major::8, minor::8, patch::8, rev::8, build::16>>
```

* `addons` : Certain bits in this determine what additional packs are installed
  * 


#### [0xA7 Login Request](#client-0xA7)

#### [0xA3 Ping Request](#client-0xA3)
