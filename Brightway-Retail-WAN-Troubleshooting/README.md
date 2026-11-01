# Brightway Retail: Black Friday Eve

## The story

Brightway Retail runs six high-street stores. Every store connects back to the head office over a hub-and-spoke WAN: a primary link to the first hub switch and a backup link to the second. The head office hosts the point-of-sale (POS) server, the inventory server, DHCP/DNS and logging, and gives the whole chain its internet access.

It is the evening before the biggest trading day of the year. The last-minute store rollout changed addressing, access rules and the hub, and now the tills are failing in different ways in different stores. One store's POS cannot reach the POS server. Another store's staff PCs get no addresses. One store has gone silent altogether. The stores have lost the internet. And some rules that keep staff away from the till systems have quietly vanished.

You are the on-call network engineer. The operations manager is already asking for a status. You have the console and the tickets.

Work out what is broken, prove why, fix it properly and leave every store ready to trade.

## What you receive

| File | Purpose |
|---|---|
| `Brightway-Troubleshooting-Student.pkt` | The head office and six stores for Cisco Packet Tracer 9.0.1 |
| `WORKBOOK.md` | The 20 tickets, discussion questions and a fix log template |

Console and enable password on every device: `Lab#2026`. Username `netadmin`. Domain `brightway.lab`.

## What the network looks like

- **Head office:** two hub core switches (HSRP) that also terminate the WAN, a server switch (POS, inventory, DHCP/DNS, syslog), a user switch, and an edge router with NAT to a simulated ISP.
- **Six stores:** each has a router, a small switch, a POS terminal and a staff PC. The router uses router-on-a-stick with VLAN 10 (POS), VLAN 20 (staff) and VLAN 50 (management). Each store router has a primary link to hub core 1 and a backup link to hub core 2.
- Addresses: head office `10.1.x.0/24`; store *n* uses `10.(10+n).x.0/24`. OSPF runs across the WAN. Staff PCs and head office users use DHCP.

## What is expected of you

1. **Work the tickets in a sensible order.** Start with what affects the most stores. Some faults hide behind others.
2. **Prove the cause before you change anything,** and keep the `show` output.
3. **Fix the root cause.** No workarounds such as extra static routes or removing ACLs.
4. **Change as little as possible.**
5. **Verify after every fix** and confirm nothing else broke.
6. **Save your work** with `write memory`.
7. **Document as you go:** symptom, device, commands, root cause, fix, verification.
8. **Be patient.** Allow up to five minutes for spanning-tree, EtherChannel and OSPF to settle, and renew DHCP after a fix.
9. **Finish with an end-to-end check:** every store to head office, store to store, and the simulated internet (198.51.100.1).

Some blocks are deliberate policy: POS terminals may reach only the POS server and DHCP/DNS, staff must not reach the POS server or their store's POS VLAN, head office users must not reach the POS server, and management is allowed only from the head office management VLAN. Do not "fix" those.

## Tips from the shift handover

- Start at the bottom: link, VLAN, IP and gateway, then routing, then policy.
- Compare one store with another. They are built from the same template.
- Test what should be blocked as well as what should work.
- Read console messages; they often name the problem.
- Do not guess. Run another `show` command.

Good luck. The tills open at 08:00.
