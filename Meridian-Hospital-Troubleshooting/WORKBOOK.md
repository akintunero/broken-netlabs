# Meridian General Hospital Network - Troubleshooting Workbook

You are the on-call network engineer. The network worked before the weekend change; now users and services are broken. There are 20 separate problems. Find each one, fix it on the correct device, and record what you did.

Login: console and enable password `Lab#2026`, user `netadmin`, domain `hospital.lab`. Open `Meridian-Troubleshooting-Student.pkt`.

Rules
- Prove the cause with `show` commands before you change anything.
- Fix the root cause, not the symptom.
- `write memory` on every device you change.
- Allow up to five minutes for spanning-tree, EtherChannel and routing to converge after a fix.

## Step M5 (manual): connect the wireless clients

Packet Tracer cannot pre-associate wireless clients in this file. Do this after the wired network works.

1. On MH-LT01 open Config > Wireless0 and join `MG-STAFF`, WPA2-PSK, passphrase `Lab#2026`.
2. On MH-TAB01 join `MG-GUEST`, WPA2-PSK, passphrase `Guest#2026`.
3. On CL-LT01 join `MG-CL-STAFF`, WPA2-PSK, passphrase `Lab#2026`.
4. Check each client gets an address by DHCP. Guests must reach only DNS and the internet.

## Reported tickets

| # | Ticket |
|---|---|
| 1 | A ward PC cannot reach the electronic health record server. |
| 2 | Lab PC1 cannot reach its gateway. |
| 3 | A clinic administration PC that uses DHCP gets no address. |
| 4 | Emergency department PCs cannot reach their gateway. |
| 5 | The data centre application server is unreachable from the wards. |
| 6 | The spanning-tree root for the main hospital is not on the primary core. |
| 7 | An administration PC gets an address but cannot leave its subnet. |
| 8 | Ward PCs cannot reach any server in the server room. |
| 9 | Console messages on a ward switch complain about an uplink mismatch. |
| 10 | Administration PC1 is dead; its switch port has shut itself down. |
| 11 | The link between the two clinic core switches is not forming a working bundle. |
| 12 | Only some main-hospital users are translated to the internet. |
| 13 | Nothing in the hospital can reach the simulated internet, although the edge router is up. |
| 14 | The main hospital cannot reach the application server in the data centre. |
| 15 | Administration can reach clinical wards, which policy forbids. |
| 16 | The database server cannot be reached from the application server. |
| 17 | The EHR name resolves, but to the wrong server. |
| 18 | Nobody can reach the management address of the emergency switch. |
| 19 | The clinic cannot reach the lab information server. |
| 20 | A medical device cannot reach the EHR server it needs. |

Some tickets only become visible after another is fixed.

For each ticket record: Symptom - Device - Commands used - Root cause - Fix - Verification.

## Discussion questions (not scored in Packet Tracer)

1. Which hospital traffic would you prioritise with QoS (EHR, PACS imaging, voice, guest), and on which links?
2. Why is management restricted to the management VLANs, and how would you prove it works?
3. Why do medical devices have their own VLAN and ACL, and what would you add in a real hospital?

Finish with a connectivity check between the hospital, clinic, data centre and the simulated internet (198.51.100.1).
