# National Bank Network - Troubleshooting Workbook

You are the on-call network engineer. The network worked before the weekend migration; now users and services are broken. There are 26 separate problems. Find each one, fix it on the correct device, and record what you did.

Login: console and enable password `Lab#2026`, user `netadmin`, domain `natbank.lab`. Open `NationalBank-Troubleshooting-Student.pkt`.

Rules
- Prove the cause with `show` commands before you change anything.
- Fix the root cause, not the symptom (no extra static routes or ACL bypasses).
- `write memory` on every device you change.
- Allow two to three minutes for routing and switching to converge after a fix.

## Step M5 (manual): connect the wireless clients

Packet Tracer cannot pre-associate wireless clients in this file, so do this yourself after the wired network works.

1. On HQ-LT01 and HQ-TAB01 open Config > Wireless0 and join SSID `NB-STAFF`, WPA2-PSK, passphrase `Lab#2026`.
2. On BRS-LT01 join `NB-BRS-STAFF`, WPA2-PSK, passphrase `Lab#2026`.
3. Guest SSIDs are `NB-GUEST` and `NB-BRS-GUEST` with passphrase `Guest#2026`.
4. Check each client gets an address by DHCP and can reach its default gateway.

## Reported tickets

| # | Ticket |
|---|---|
| 1 | Bristol PC cannot reach head-office servers. |
| 2 | PC4 on floor 2 cannot reach its gateway. |
| 3 | Leeds PC cannot reach its default gateway. |
| 4 | The Loans PC at head office gets no IP address. |
| 5 | Bristol PC cannot reach its own branch router. |
| 6 | Cardiff PCs get an address but cannot leave their subnet. |
| 7 | Nobody at head office can reach the Manchester switch management address. |
| 8 | Head-office users cannot reach the HQ servers. |
| 9 | Console messages on an access switch complain about a mismatch on an uplink. |
| 10 | The spanning-tree root is not where the design says it should be. |
| 11 | The link between the two core switches is not forming a working bundle. |
| 12 | The Finance PC at the first desk is dead; its port is shut down by the switch. |
| 13 | Internal users cannot reach the public side of the firewall, although the firewall is up. |
| 14 | Head office cannot reach any branch beyond the first WAN link, although the routers are up. |
| 15 | The Cardiff router has no routing neighbours. |
| 16 | Head office cannot reach the simulated internet. |
| 17 | Only some head-office departments are translated to the internet. |
| 18 | The Operations PC cannot reach its own gateway. |
| 19 | Head office cannot reach the application server in the data centre. |
| 20 | The application name resolves, but to the wrong server. |
| 21 | Edinburgh users have no connectivity. |
| 22 | The internet cannot reach the published web server and customer portal. |
| 23 | The customer portal is not reachable on its published address. |
| 24 | The DMZ is not treated as the trusted zone the design requires. |
| 25 | The data centre reaches the branches by an unexpected path. |
| 26 | The disaster-recovery router is missing from the routing design. |

Tickets 25 and 26 are related. Some tickets only become visible after another is fixed.

For each ticket record: Symptom - Device - Commands used - Root cause - Fix - Verification.

Finish with a connectivity check between head office, every branch, the servers, the data centre, the DR site and the simulated internet (198.51.100.65 and 192.0.2.65).
