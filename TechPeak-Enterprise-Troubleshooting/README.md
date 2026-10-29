# TechPeak Enterprise: The Monday Morning Outage

## The story

It is 07:40 on Monday. TechPeak, a London company with a head office, two data centres and branch offices in London, Lagos and Manchester, has just come out of a weekend change window. The change manager signed it off as "successful".

By 07:55 the service desk has sixteen tickets. A finance user cannot reach their gateway. Lagos has gone quiet. Manchester cannot get out of its own subnet. A server in the data centre is unreachable, and branch users cannot get online.

The senior engineer is on a flight. You are the on-call network engineer, and you have been handed the console. Nobody knows exactly what changed. You do not have a change log, only the network and the tickets.

Your job is to work out what is broken, prove why, fix it properly, and leave the network in a state you would be happy to hand over.

## What you receive

| File | Purpose |
|---|---|
| `TechPeak-Troubleshooting-Student.pkt` | The network, opened in Cisco Packet Tracer 9.0.1 |
| `WORKBOOK.md` | The 16 tickets and your fix log template |

Console and enable password on every device: `Lab#2026`. Domain: `techpeak.lab`.

## What the network looks like

- HQ with a dual-core pair (HSRP), access switches, a server switch and an internet edge with NAT.
- Two WAN routers and an EIGRP ring linking the sites, with redistribution into OSPF at HQ.
- Data centres A and B, and branches in London, Lagos and Manchester.
- Addresses are DHCP for PCs (they can change on every run; use `ipconfig`), static for servers.

## What is expected of you

Treat this as a real incident, not a puzzle.

1. **Work the tickets in a sensible order.** Start with what affects the most users. Some faults hide behind others, so a ping that fails may have two causes.
2. **Prove the cause before you change anything.** Use `show` commands and record the output that shows the fault. "I changed it and it worked" is not a diagnosis.
3. **Fix the root cause.** No shortcuts such as extra static routes, removing ACLs or turning off a feature to make a ping pass. A workaround is not a fix.
4. **Change as little as possible.** Touch only the device and the lines that are wrong.
5. **Verify after every fix** with the same test that failed, and confirm nothing else broke.
6. **Save your work** with `write memory` on every device you change.
7. **Document as you go.** For each ticket write: symptom, device, commands used, root cause, fix, how you verified. A handover note is part of the job.
8. **Finish with an end-to-end check:** every site can reach every other site, the servers, and 203.0.113.1.

## How you will be judged (if this is an assessed lab)

- Did you find all 16 root causes?
- Is the evidence in your notes before each change?
- Are the fixes minimal and correct?
- Is the final network fully reachable, and is the configuration saved?

## Tips from the on-call rota

- Start at the bottom: link, VLAN, IP address, gateway, then routing, then policy.
- Compare neighbours. If two similar devices differ, one of them is wrong.
- Read the console messages. They often name the problem.
- Do not guess. If you are not sure, run another `show` command.

Good luck. The service desk is waiting.
