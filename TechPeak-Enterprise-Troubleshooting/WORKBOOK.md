# TechPeak Enterprise Network - Troubleshooting Workbook

You have been called in as the on-call network engineer. The TechPeak network was working last week; after a change window several users and services are broken. There are 16 separate problems. Find each one, fix it on the correct device, and record what you did.

Login: console and enable password `Lab#2026`, domain `techpeak.lab`. Open `TechPeak-Troubleshooting-Student.pkt`.

Rules
- Use show commands to prove the cause before you change anything.
- Fix the root cause, not the symptom (no extra static routes or ACL bypasses).
- `write memory` on every device you change.

Reported tickets
1. PC1 cannot reach anything on its VLAN 10 gateway.
2. VLAN 20 users on floor 4 (PC6) have no connectivity.
3. HQ servers (10.10.2.x) are unreachable from users.
4. PC4 is dead.
5. Finance (PC5) cannot reach its gateway.
6. WAN-B (R4) lost its link to HQ-CORE2.
7. Lagos office is isolated from the rest of the WAN.
8. HQ cannot reach any branch networks, although routers are up.
9. Branch offices cannot reach the internet; HQ can.
10. DC-B servers are unreachable from Lagos.
11. Manchester users cannot reach their gateway.
12. The HQ-ACC1 switch cannot be managed from another subnet.
13. Console messages on HQ-CORE2 mention HSRP.
14. DCA-SRV1 cannot be reached from other sites.
15. DCA-SW2 has lost uplink redundancy.
16. PC3 cannot reach its gateway.

For each ticket record: Symptom - Device - Commands used - Root cause - Fix - Verification.
Finish by pinging between every site and to 203.0.113.1 (internet).
