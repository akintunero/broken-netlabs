# National Bank Network: The Friday Night Migration

## The story

It is 06:50 on Monday. National Bank, a UK retail bank, spent the weekend moving its head office, its Manchester, Leeds, Edinburgh, Birmingham, Bristol and Cardiff branches, its data centre and its disaster-recovery site onto a new design: OSPF at head office, EIGRP across the WAN, a firewall pair at the edge with a DMZ for the public web servers, and a wireless network for staff and guests.

The change manager signed the weekend off as "successful". By 07:30 the service desk has twenty-six tickets. Some branches cannot get an address. A finance clerk is locked out of their own port. The public web servers cannot be reached from the internet. The data centre, the DR site and the branches do not agree about who can reach whom.

The senior network engineer is unavailable. You are the engineer on call and you have been handed the console. There is no change log, only the network and the tickets.

Your job is to work out what is broken, prove why, fix it properly, and leave the network in a state you would be happy to hand over to the next shift.

## What you receive

| File | Purpose |
|---|---|
| `NationalBank-Troubleshooting-Student.pkt` | The network, opened in Cisco Packet Tracer 9.0.1 |
| `WORKBOOK.md` | The 26 tickets, the wireless step and your fix log template |

Console and enable password on every device: `Lab#2026`. Username `netadmin`. Domain `natbank.lab`.

## What the network looks like

- Head office with a dual-core pair (HSRP), three access switches, a server switch and a Wi-Fi switch.
- An edge router, a Cisco ASA firewall (inside, DMZ and outside zones) and two ISP routers.
- A WAN router that redistributes between OSPF (head office) and EIGRP (the WAN), with two branch chains and a data-centre/DR ring.
- Six branches (Manchester, Leeds, Edinburgh, Birmingham, Bristol, Cardiff), a data centre and a DR site.
- Servers use static addresses. Cardiff and the Loans PC use DHCP, so their addresses can change; use `ipconfig`.

## What is expected of you

Treat this as a real incident, not a puzzle.

1. **Work the tickets in a sensible order.** Start with what affects the most users. Some faults hide behind others, so a ping that fails may have more than one cause.
2. **Prove the cause before you change anything.** Use `show` commands and keep the output that shows the fault. "I changed it and it worked" is not a diagnosis.
3. **Fix the root cause.** No shortcuts such as extra static routes, removing ACLs or switching off a feature to make a ping pass. A workaround is not a fix.
4. **Change as little as possible.** Touch only the device and the lines that are wrong.
5. **Verify after every fix** with the test that failed, and confirm nothing else broke.
6. **Save your work** with `write memory` on every device you change.
7. **Document as you go.** For each ticket write: symptom, device, commands used, root cause, fix, how you verified.
8. **Be patient.** After a routing, switching or EtherChannel fix, give the network two to three minutes to converge before you decide the fix did not work.
9. **Finish with an end-to-end check:** every site reaches every other site you are permitted to reach, the servers, and the simulated internet (198.51.100.65 and 192.0.2.65).

Some blocks are deliberate policy, not faults. Branches are not meant to reach the application tier, and Finance is not meant to reach Operations. Do not "fix" those.

## How you will be judged (if this is an assessed lab)

- Did you find all 26 root causes?
- Is the evidence in your notes before each change?
- Are the fixes minimal and correct?
- Is the final network reachable as designed, and is the configuration saved?

## Tips from the on-call rota

- Start at the bottom: link, VLAN, IP address and gateway, then routing, then policy.
- Compare neighbours. If two similar devices differ, one of them is wrong.
- Read the console messages. They often name the problem.
- Firewall tip: on the ASA in Packet Tracer, an access list or NAT object that looks right in the configuration may not take effect until it is re-applied. If the configuration is correct but traffic still fails, remove and re-apply the `access-group` or the `nat` line.
- Do not guess. If you are not sure, run another `show` command.

Good luck. The service desk is waiting.
