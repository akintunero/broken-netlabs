# Meridian General Hospital Network: The Night Shift

## The story

Meridian General is a regional hospital with a main site, an outpatient clinic across town and a data centre that runs the electronic health record, imaging and lab systems. Over the weekend the IT team consolidated the network: new VLANs for wards, labs, administration and medical devices, central DHCP and DNS, a hardened management plane and a refreshed WAN.

It is 02:10 on Monday and you are the engineer on call. The overnight nurses have already phoned in twenty problems. A ward PC cannot reach the patient record. A lab PC is stuck on a dead port. Clinic staff are not getting addresses. The administration team can suddenly see clinical systems, and a medical device cannot reach the records server it needs.

Patient care depends on this network. The architect is unreachable. You have the console and the tickets.

Work out what is broken, prove why, fix it properly and leave the hospital in a state you would hand to the next shift.

## What you receive

| File | Purpose |
|---|---|
| `Meridian-Troubleshooting-Student.pkt` | The hospital network for Cisco Packet Tracer 9.0.1 |
| `WORKBOOK.md` | The 20 tickets, the wireless step, discussion questions and a fix log template |

Console and enable password on every device: `Lab#2026`. Username `netadmin`. Domain `hospital.lab`.

## What the network looks like

- **Main hospital:** two HSRP core switches, ward, emergency, lab and administration access switches, a Wi-Fi switch and a server switch holding DHCP/DNS, syslog, the EHR and PACS servers. Medical devices sit in their own VLAN.
- **Edge and WAN:** an edge router with NAT to a simulated ISP, and two WAN routers.
- **Outpatient clinic:** two routers, two HSRP cores, two access switches and a Wi-Fi switch.
- **Data centre:** two routers, two HSRP cores, and application, lab, database and backup servers.
- Addresses follow `10.<site>.<vlan>.0/24` (main 1, clinic 2, data centre 3). Some PCs and all wireless clients use DHCP.

## What is expected of you

1. **Work the tickets in a sensible order.** Start with what affects the most users and patient care. Some faults hide behind others.
2. **Prove the cause before you change anything,** and keep the `show` output.
3. **Fix the root cause.** No workarounds such as extra static routes or removing ACLs.
4. **Change as little as possible.**
5. **Verify after every fix** and confirm nothing else broke.
6. **Save your work** with `write memory`.
7. **Document as you go:** symptom, device, commands, root cause, fix, verification.
8. **Be patient.** Allow up to five minutes for spanning-tree, EtherChannel and routing to settle.
9. **Finish with an end-to-end check** of the hospital, clinic, data centre and the simulated internet (198.51.100.1).

Some blocks are deliberate policy: administration must not reach clinical wards, medical devices reach only the EHR, PACS and DNS, guest Wi-Fi reaches only DNS and the internet, the clinic must not reach the database tier directly, and management is allowed only from the management VLANs. Do not "fix" those.

## Tips from the shift handover

- Start at the bottom: link, VLAN, IP and gateway, then routing, then policy.
- Compare neighbours. If two similar devices differ, one of them is wrong.
- Test what should be blocked as well as what should work.
- Read console messages; they often name the problem.
- Do not guess. Run another `show` command.

Good luck. The ward is waiting.
