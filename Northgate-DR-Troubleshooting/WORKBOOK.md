# Northgate Hosting Primary and DR Data Centres - Troubleshooting Workbook

You are the on-call network engineer. The network worked before the weekend change; now services are broken. There are 20 separate problems. Find each one, fix it on the correct device, and record what you did.

Login: console and enable password `Lab#2026`, user `netadmin`, domain `northgate.lab`. Open `Northgate-Troubleshooting-Student.pkt`.

Rules
- Prove the cause with `show` commands before you change anything.
- Fix the root cause, not the symptom.
- `write memory` on every device you change.
- Allow up to five minutes for spanning-tree, EtherChannel and routing to converge after a fix. Renew DHCP clients after fixing them.

## Reported tickets

| # | Ticket |
|---|---|
| 1 | The second primary web server cannot reach the database. |
| 2 | The primary database server cannot reach its gateway. |
| 3 | An office user PC that uses DHCP gets no address. |
| 4 | The DR database server cannot reach its gateway. |
| 5 | The primary backup server is unreachable. |
| 6 | The spanning-tree root for the primary data centre is not on the primary core. |
| 7 | An office user gets an address but cannot leave the office subnet. |
| 8 | Operations cannot reach the primary authentication and DNS server. |
| 9 | Console messages on a DR switch complain about an uplink mismatch. |
| 10 | An office user PC is dead; its switch port has shut itself down. |
| 11 | The link between the two DR core switches is not forming a working bundle. |
| 12 | The primary data centre reaches the internet but the DR site does not. |
| 13 | Nothing in either data centre or the office can reach the simulated internet, although the edge router is up. |
| 14 | Operations cannot reach the DR web tier. |
| 15 | Office users can reach the primary database, which policy forbids. |
| 16 | The web tier can reach the backup network, which policy forbids. |
| 17 | The DR authentication server cannot reach its gateway. |
| 18 | The public web name resolves, but to an address that does not answer. |
| 19 | The DR database cannot reach the primary database for replication. |
| 20 | The primary authentication server cannot reach its DR counterpart. |

Some tickets only become visible after another is fixed.

For each ticket record: Symptom - Device - Commands used - Root cause - Fix - Verification.

## Discussion questions (not scored in Packet Tracer)

1. Which traffic would you prioritise with QoS during a failover (replication, web, authentication, backup), and on which links?
2. How would you rehearse a failover between the sites, and what would you check before and after to prove recovery?
3. The WAN routers carry floating static routes toward the DR site as a backup. When would they take over, and how would you test them?
4. Why is management restricted to the management VLANs, and what would you add in a real hosting provider?

Finish with a connectivity check across both data centres, the office and the simulated internet (198.51.100.1).
