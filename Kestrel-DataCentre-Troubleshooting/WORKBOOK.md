# Kestrel Enterprise Data Centre and Server Farm - Troubleshooting Workbook

You are the on-call network engineer. The network worked before the weekend refresh; now servers and services are broken. There are 20 separate problems. Find each one, fix it on the correct device, and record what you did.

Login: console and enable password `Lab#2026`, user `netadmin`, domain `kestrel.lab`. Open `Kestrel-Troubleshooting-Student.pkt`.

Rules
- Prove the cause with `show` commands before you change anything.
- Fix the root cause, not the symptom.
- `write memory` on every device you change.
- Allow up to five minutes for spanning-tree, EtherChannel and OSPF to converge after a fix. Renew DHCP clients after fixing them.

## Reported tickets

| # | Ticket |
|---|---|
| 1 | Web node 2 cannot reach the application tier. |
| 2 | Web node 3 cannot reach its gateway. |
| 3 | Campus user PCs that use DHCP get no address. |
| 4 | The application servers cannot reach their gateway. |
| 5 | Database server 1 is offline. |
| 6 | The spanning-tree root for the web and application pod is not on the primary aggregation switch. |
| 7 | Campus users get an address but cannot leave their subnet. |
| 8 | The link between the two data aggregation switches is not forming a full bundle. |
| 9 | Console messages on an infrastructure switch complain about an uplink mismatch. |
| 10 | The engineering PC is dead; its switch port has shut itself down. |
| 11 | The secondary application aggregation switch logs repeated gateway warnings. |
| 12 | The partner can no longer reach the web portal. |
| 13 | Campus cannot reach the simulated internet. |
| 14 | Nothing in the data centre can reach the simulated internet, although the edge routers are up. |
| 15 | The partner can reach the application tier, which policy forbids. |
| 16 | The database tier can reach the campus, which policy forbids. |
| 17 | The application tier cannot reach the database after the earlier fixes. |
| 18 | The web service name resolves, but to an address that does not answer. |
| 19 | The operations PC cannot reach anything in the data centre. |
| 20 | The cache node cannot reach its gateway. |

Some tickets only become visible after another is fixed.

For each ticket record: Symptom - Device - Commands used - Root cause - Fix - Verification.

## Discussion questions (not scored in Packet Tracer)

1. Which traffic would you prioritise with QoS (database replication, storage and backup, user web traffic, monitoring), and on which links?
2. Each pod has two aggregation switches with HSRP and an EtherChannel between them. What failures does this design survive, and which does it not?
3. The two edge routers each NAT to their own provider. What problems can asymmetric routing cause here, and how would you detect them?
4. Why is the database tier blocked from initiating connections to campus users, and what would you add on a real firewall?

Finish with a connectivity check from campus to the web tier, from the app tier to the database, from operations to every tier, and to the simulated internet (198.51.100.1).
