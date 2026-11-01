# Brightway Retail Hub-and-Spoke WAN - Troubleshooting Workbook

You are the on-call network engineer. The network worked before the rollout; now stores and services are broken. There are 20 separate problems. Find each one, fix it on the correct device, and record what you did.

Login: console and enable password `Lab#2026`, user `netadmin`, domain `brightway.lab`. Open `Brightway-Troubleshooting-Student.pkt`.

Rules
- Prove the cause with `show` commands before you change anything.
- Fix the root cause, not the symptom.
- `write memory` on every device you change.
- Allow up to five minutes for spanning-tree, EtherChannel and OSPF to converge after a fix. Renew DHCP clients after fixing them.

## Reported tickets

| # | Ticket |
|---|---|
| 1 | Store 2's POS terminal cannot reach the POS server. |
| 2 | Store 3's staff PC cannot reach its router. |
| 3 | Store 4's staff PC that uses DHCP gets no address. |
| 4 | Store 5's staff PC cannot reach its router. |
| 5 | Store 6 is completely offline; its POS cannot reach head office. |
| 6 | The spanning-tree root at head office is not on the primary hub core. |
| 7 | Store 2's staff PC gets an address but cannot leave its store. |
| 8 | Stores cannot reach any server in the head office server room. |
| 9 | Console messages on a store switch complain about an uplink mismatch. |
| 10 | Store 1's POS terminal is dead; its switch port has shut itself down. |
| 11 | The link between the two hub core switches is not forming a working bundle. |
| 12 | Head office reaches the internet but the stores do not. |
| 13 | Nothing in the chain can reach the simulated internet, although the edge router is up. |
| 14 | Store 3 can send traffic out, but head office cannot reply to it. |
| 15 | Store 1 staff can reach the POS server, which policy forbids. |
| 16 | Store 2's POS terminal still cannot reach the POS server after the first fixes. |
| 17 | Head office users can reach the POS server, which policy forbids. |
| 18 | The POS server name resolves, but to an address that does not answer. |
| 19 | A head office user PC cannot reach its gateway. |
| 20 | A second head office PC cannot reach anything outside its subnet. |

Some tickets only become visible after another is fixed.

For each ticket record: Symptom - Device - Commands used - Root cause - Fix - Verification.

## Discussion questions (not scored in Packet Tracer)

1. Which store traffic would you prioritise with QoS (card payments, inventory sync, staff web, updates), and on which links?
2. The stores have a primary and a backup WAN link. How does OSPF choose between them, and how would you prove the backup works without breaking trading?
3. Why are POS terminals, staff PCs and management in separate VLANs, and what would you add to meet card-payment security standards?
4. Why is management allowed only from the head office management VLAN?

Finish with a connectivity check from every store to head office, store to store, and to the simulated internet (198.51.100.1).
