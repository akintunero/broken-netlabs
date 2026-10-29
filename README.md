# Enterprise Network Troubleshooting Labs

Four Cisco Packet Tracer networks, each deliberately broken. Your job is to find the faults, prove the cause, fix them properly and document what you did. They are built to feel like a real incident: no change log, a pile of tickets, and a network that worked until the weekend.

## Start here

1. Install **Cisco Packet Tracer 9.0.1**.
2. Pick a lab folder from the table below. Start with the smallest if this is your first time.
3. Read that folder's `README.md` first. It gives you the story, the network layout, the logins and what is expected of you.
4. Open the `.pkt` file in Packet Tracer and work through `WORKBOOK.md`.

## The labs

| Lab | Folder | Size | Tickets |
|---|---|---|---|
| TechPeak Enterprise | `TechPeak-Enterprise-Troubleshooting` | 42 devices, head office, two data centres and branches | 16 |
| Harbourline Campus | `Harbourline-Campus-Troubleshooting` | 52 devices, main campus, remote campus, depot and data centre | 20 |
| Meridian General Hospital | `Meridian-Hospital-Troubleshooting` | 49 devices, hospital, clinic and data centre, with segmentation and ACL policy | 20 |
| National Bank | `NationalBank-Enterprise-Troubleshooting` | 59 devices, head office, branches, DMZ, firewall and DR | 26 |

Every lab folder contains:

- `*.pkt`: the broken network to open in Packet Tracer.
- `README.md`: the story, the network overview and what is expected of you.
- `WORKBOOK.md`: the tickets, the wireless step and a fix log template.

## How to work a lab

- Treat it as an incident, not a puzzle. Start with what affects the most users.
- Prove the cause with `show` commands before you change anything, and keep the output.
- Fix the root cause with the smallest change. No workarounds such as extra static routes or removing ACLs.
- Verify after every fix and check you have not broken something else.
- Save with `write memory` on every device you change.
- Be patient. Routing, spanning-tree and EtherChannel can take two to five minutes to settle.
- Some blocks are deliberate policy, not faults. Each lab's README lists what must stay blocked.
- Some faults hide behind others, so a test that still fails after a fix may have a second cause.

## Wireless

Packet Tracer cannot pre-connect wireless clients in these files, so each workbook has a short manual step (M5). Do it after the wired network works.

## Keeping a record

For each ticket write down: symptom, device, commands used, root cause, fix and how you verified it. Employers and assessors value this evidence as much as the fix itself.

## Good to know

- Open the `.pkt` straight from the folder. Do not edit the README or workbook files while you work; copy the fix log into your own notes.
- If you are stuck, step back to the bottom of the stack: link, VLAN, IP address and gateway, then routing, then policy.

Good luck.
