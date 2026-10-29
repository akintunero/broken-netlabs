# Harbourline Campus Network: The Merger Monday

## The story

Harbourline is a growing UK company that has just merged two sites into one campus network. The main campus has three office buildings, a Wi-Fi switch and a server room, all behind a pair of HSRP core switches. A remote campus has two buildings and its own pair of cores. A small depot hangs off the WAN, and a data centre hosts the application, file and database servers.

The IT team spent the weekend renumbering VLANs, rebuilding the trunks, moving DHCP to a central server and tightening the access layer. It is Monday at 08:00 and the service desk already has twenty tickets. A depot PC cannot reach anything. Sales staff are not getting addresses. One port has locked itself. Nobody on the remote campus can get out to the internet. And someone says Engineering can now see Sales, which should never happen.

The network architect has left for the day. You are the engineer on shift. There is no change log, only the network and the tickets.

Work out what is broken, prove why, fix it properly, and leave the campus in a state you would hand to the next shift.

## What you receive

| File | Purpose |
|---|---|
| `Harbourline-Troubleshooting-Student.pkt` | The campus network, for Cisco Packet Tracer 9.0.1 |
| `WORKBOOK.md` | The 20 tickets, the wireless step and a fix log template |

Console and enable password on every device: `Lab#2026`. Username `netadmin`. Domain `campus.lab`.

## What the network looks like

- **Main campus:** two HSRP core switches, six building access switches (A, B, C), a Wi-Fi switch and a server switch. Edge router and a simulated ISP.
- **WAN:** two WAN routers, each connecting to the remote campus, the depot and the data centre.
- **Remote campus:** two HSRP cores, four access switches and a Wi-Fi switch, behind two routers.
- **Depot:** one router and switch (router-on-a-stick).
- **Data centre:** a router, two switches in an EtherChannel, and three servers.
- Addresses come from `10.<site>.<vlan>.0/24`. Some PCs and all wireless clients use DHCP, so use `ipconfig`.

## What is expected of you

Treat this as a real incident, not a puzzle.

1. **Work the tickets in a sensible order.** Start with what affects the most users. Some faults hide behind others.
2. **Prove the cause before you change anything.** Keep the `show` output that shows the fault.
3. **Fix the root cause.** No workarounds such as extra static routes or removing ACLs.
4. **Change as little as possible.** Touch only the device and the lines that are wrong.
5. **Verify after every fix** and confirm nothing else broke.
6. **Save your work** with `write memory` on every device you change.
7. **Document as you go:** symptom, device, commands used, root cause, fix, verification.
8. **Be patient.** Give routing, spanning-tree and EtherChannel changes two to three minutes to converge.
9. **Finish with an end-to-end check:** main campus, remote campus, depot and data centre reach each other and the simulated internet (198.51.100.1).

Some blocks are deliberate policy. Engineering and Sales must not reach each other, the depot must not reach the database tier, and guest Wi-Fi may only use DNS and the internet. Do not "fix" those.

## Tips from the shift handover

- Start at the bottom: link, VLAN, IP and gateway, then routing, then policy.
- Compare neighbours. If two similar devices differ, one of them is wrong.
- Read the console messages; they often name the problem.
- A fault that tests fine may still be a policy fault. Test what should be blocked as well as what should work.
- Do not guess. Run another `show` command.

Good luck. The service desk is waiting.
