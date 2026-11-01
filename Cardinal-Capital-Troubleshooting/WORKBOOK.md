# Cardinal Capital Investment Bank Network - Troubleshooting Workbook

You are the on-call network engineer. The network worked before the weekend change; now users and services are broken. There are 20 separate problems. Find each one, fix it on the correct device, and record what you did.

Login: console and enable password `Lab#2026`, user `netadmin`, domain `cardinal.lab`. Open `Cardinal-Troubleshooting-Student.pkt`.

Rules
- Prove the cause with `show` commands before you change anything.
- Fix the root cause, not the symptom.
- `write memory` on every device you change.
- Allow up to five minutes for spanning-tree, EtherChannel and routing to converge after a fix. Renew DHCP clients after fixing them.

## Reported tickets

| # | Ticket |
|---|---|
| 1 | A trading PC cannot reach any server. |
| 2 | An employee PC cannot reach its gateway. |
| 3 | A New York employee PC that uses DHCP gets no address. |
| 4 | The risk desk PC cannot reach its gateway. |
| 5 | The trading engine cannot reach the database server in the data centre. |
| 6 | The spanning-tree root for London is not on the primary core. |
| 7 | An administration PC gets an address but cannot leave its subnet. |
| 8 | Trading PCs cannot reach any server in the London server room. |
| 9 | Console messages on a New York switch complain about an uplink mismatch. |
| 10 | The market-data feed server is dead; its switch port has shut itself down. |
| 11 | The link between the two London core switches is not forming a working bundle. |
| 12 | London users reach the internet but New York users do not. |
| 13 | Nothing in the bank can reach the simulated internet, although the edge router is up. |
| 14 | The risk desk cannot reach the database tier. |
| 15 | The market-data feed cannot reach the trading desks. |
| 16 | Employees can reach risk systems, which policy forbids. |
| 17 | New York trading PCs cannot reach their gateway. |
| 18 | The trading engine name resolves, but to an address that does not answer. |
| 19 | The risk desk PC cannot reach the risk server. |
| 20 | The second market-data server cannot reach the data centre. |

Some tickets only become visible after another is fixed.

For each ticket record: Symptom - Device - Commands used - Root cause - Fix - Verification.

## Discussion questions (not scored in Packet Tracer)

1. Which trading traffic would you prioritise with QoS (market data, order flow, voice, bulk backup), and on which links?
2. Why are trading, employee, risk and market-data traffic segmented with ACLs, and how would you prove each rule works?
3. How do HSRP and the paired WAN routers keep trading alive when one device or link fails, and how would you test that?
4. Why is management restricted to the management VLANs, and what would you add in a real bank?

Finish with a connectivity check between London, New York, the data centre and the simulated internet (198.51.100.1).
