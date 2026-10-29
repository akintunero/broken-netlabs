# Harbourline Campus Network - Troubleshooting Workbook

You are the on-call network engineer. The campus worked before the weekend change; now users and services are broken. There are 20 separate problems. Find each one, fix it on the correct device, and record what you did.

Login: console and enable password `Lab#2026`, user `netadmin`, domain `campus.lab`. Open `Harbourline-Troubleshooting-Student.pkt`.

Rules
- Prove the cause with `show` commands before you change anything.
- Fix the root cause, not the symptom.
- `write memory` on every device you change.
- Allow two to three minutes for routing, spanning-tree and EtherChannel to converge after a fix.

## Step M5 (manual): connect the wireless clients

Packet Tracer cannot pre-associate wireless clients in this file. Do this after the wired network works.

1. On MC-LT01 open Config > Wireless0 and join `HL-STAFF`, WPA2-PSK, passphrase `Lab#2026`.
2. On MC-TAB01 join `HL-GUEST`, WPA2-PSK, passphrase `Guest#2026`.
3. On RC-LT01 join `HL-RC-STAFF`, WPA2-PSK, passphrase `Lab#2026`.
4. Check each client gets an address by DHCP and reaches its default gateway.

## Reported tickets

| # | Ticket |
|---|---|
| 1 | The depot PC cannot reach any server in the data centre. |
| 2 | An Admin PC on the first desk of building A cannot reach its gateway. |
| 3 | The depot PC cannot reach its own gateway. |
| 4 | A Sales PC that uses DHCP gets no address. |
| 5 | The depot LAN is completely down. |
| 6 | A Remote Labs PC gets an address but cannot leave its subnet. |
| 7 | Nobody can reach the management address of a building B switch. |
| 8 | Main campus users cannot reach the servers in the server room. |
| 9 | Console messages on a building C switch complain about a mismatch on an uplink. |
| 10 | The spanning-tree root for the main campus is not where the design says it should be. |
| 11 | The link between the two remote-campus core switches is not forming a working bundle. |
| 12 | The third Admin PC is dead; its switch port has shut itself down. |
| 13 | Only some main campus users are translated to the internet. |
| 14 | Nothing in the campus can reach the simulated internet, although the edge router is up. |
| 15 | The main campus cannot reach the application server in the data centre. |
| 16 | Engineering can reach Sales, which policy forbids. |
| 17 | The main campus cannot reach the depot LAN, although the depot router is up. |
| 18 | The remote campus cannot reach the file server in the data centre. |
| 19 | The database server cannot be reached from the application server. |
| 20 | The application name resolves, but to the wrong server. |

Some tickets only become visible after another is fixed.

For each ticket record: Symptom - Device - Commands used - Root cause - Fix - Verification.

Finish with a connectivity check between the main campus, remote campus, depot, data centre and the simulated internet (198.51.100.1).
