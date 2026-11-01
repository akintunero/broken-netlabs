# Broken Netlabs

Hands-on Cisco networking practice in two flavours: **troubleshooting broken production networks** and **building enterprise networks from scratch**. Everything runs in Cisco Packet Tracer or, for the greenfield curriculum, any simulator you prefer.

---

## Troubleshooting Labs

Eight Cisco Packet Tracer networks, each deliberately broken. Your job is to find the faults, prove the cause, fix them properly and document what you did. They are built to feel like a real incident: no change log, a pile of tickets, and a network that worked until the weekend.

### Start here

1. Install **Cisco Packet Tracer**.
2. Pick a lab folder from the table below. Start with the smallest if this is your first time.
3. Read that folder's `README.md` first. It gives you the story, the network layout, the logins and what is expected of you.
4. Open the `.pkt` file in Packet Tracer and work through `WORKBOOK.md`.

### The labs

| Lab | Folder | Size | Tickets |
|---|---|---|---|
| TechPeak Enterprise | `TechPeak-Enterprise-Troubleshooting` | 42 devices, head office, two data centres and branches | 16 |
| Harbourline Campus | `Harbourline-Campus-Troubleshooting` | 52 devices, main campus, remote campus, depot and data centre | 20 |
| Meridian General Hospital | `Meridian-Hospital-Troubleshooting` | 49 devices, hospital, clinic and data centre, with segmentation and ACL policy | 20 |
| National Bank | `NationalBank-Enterprise-Troubleshooting` | 59 devices, head office, branches, DMZ, firewall and DR | 26 |
| Brightway Retail | `Brightway-Retail-WAN-Troubleshooting` | ~20+ devices, head office hub-and-spoke WAN to six retail stores | 20 |
| Cardinal Capital | `Cardinal-Capital-Troubleshooting` | ~25+ devices, London HQ, New York office and data centre for an investment bank | 20 |
| Kestrel DataCentre | `Kestrel-DataCentre-Troubleshooting` | ~20+ devices, tiered data centre with campus office and partner extranet | 20 |
| Northgate DR | `Northgate-DR-Troubleshooting` | ~25+ devices, primary DC, disaster-recovery DC and operations office | 20 |

Every lab folder contains:

- `*.pkt`: the broken network to open in Packet Tracer.
- `README.md`: the story, the network overview and what is expected of you.
- `WORKBOOK.md`: the tickets, the wireless step and a fix log template.

### How to work a lab

- Treat it as an incident, not a puzzle. Start with what affects the most users.
- Prove the cause with `show` commands before you change anything, and keep the output.
- Fix the root cause with the smallest change. No workarounds such as extra static routes or removing ACLs.
- Verify after every fix and check you have not broken something else.
- Save with `write memory` on every device you change.
- Be patient. Routing, spanning-tree and EtherChannel can take two to five minutes to settle.
- Some blocks are deliberate policy, not faults. Each lab's README lists what must stay blocked.
- Some faults hide behind others, so a test that still fails after a fix may have a second cause.

### Wireless

Packet Tracer cannot pre-connect wireless clients in these files, so each workbook has a short manual step (M5). Do it after the wired network works.

### Keeping a record

For each ticket write down: symptom, device, commands used, root cause, fix and how you verified it. Employers and assessors value this evidence as much as the fix itself.

### Good to know

- Open the `.pkt` straight from the folder. Do not edit the README or workbook files while you work; copy the fix log into your own notes.
- If you are stuck, step back to the bottom of the stack: link, VLAN, IP address and gateway, then routing, then policy.

---

## CCNA in 90 Days – Greenfield Build Curriculum

Located in [`ccna-in-90-greenfield/ccnain90/`](./ccna-in-90-greenfield/ccnain90/).

A **100-lab documentation-driven curriculum** for building enterprise networks from scratch. No pre-baked configs are provided. You read the business scenario and technical requirements, plan addressing, build the topology in your preferred simulator, and verify your own work.

The labs are split into a **core CCNA track** (50 labs) and **advanced ENCOR-aligned projects** (50 labs).

### Core CCNA Track (Labs 01–50)

| Phase | Folder | Labs | Focus |
|---|---|---|---|
| Foundations | `01-foundations` | 01–10 | CLI navigation, device hardening, IPv4 subnetting (`192.168.X.0/24`), VLANs (10/20/99), default gateways |
| Switching | `02-switching` | 11–20 | Multi-switch campus designs, 802.1Q trunks, STP root selection, EtherChannel |
| Routing & WAN | `03-routing-wan` | 21–35 | Inter-VLAN routing, WAN point-to-point (`10.255.X.0/30`), OSPF single-area, dual-site convergence |
| Security & Optimisation | `04-security-optimization` | 36–45 | ACL design and placement, SSH hardening, syslog and monitoring, network segmentation |
| Advanced Design | `05-advanced-design` | 46–50 | Multi-site enterprise (`10.X.0.0/24`), route summarisation, dual-ISP failover, template-driven builds |

### Advanced Projects 

Located in [`ccna-in-90-greenfield/ccnain90/advanced-projects/`](./ccna-in-90-greenfield/ccnain90/advanced-projects/). These are larger, scenario-based exercises for learners ready to go beyond CCNA.

| Domain | Folder | Labs | Focus |
|---|---|---|---|
| Architecture | `01-architecture` | 01–08 | Dual-stack IPv4/IPv6, high availability (FHRP, SSO), SD-WAN and SD-Access concepts, QoS |
| Virtualisation | `02-virtualization` | 09–13 | VRF segmentation, GRE and IPsec tunnelling, LISP/VXLAN overlay concepts |
| Infrastructure | `03-infrastructure` | 14–28 | Advanced L2/L3, OSPF/EIGRP/eBGP, wireless architecture, IP services (NTP, NAT/PAT, multicast) |
| Network Assurance | `04-network-assurance` | 29–33 | SPAN/RSPAN/ERSPAN, NetFlow, IP SLA, Cisco DNA Center workflows |
| Security | `05-security` | 34–43 | DHCP snooping, DAI, port security, AAA/802.1X, CoPP, infrastructure hardening |
| Automation | `06-automation` | 44–50 | Python scripting, RESTCONF/NETCONF, JSON/YANG, EEM applets, automation strategy |

### What each greenfield lab contains

Every lab folder provides engineering specifications rather than step-by-step instructions:

- `README.md` - scenario, business constraints, technical requirements, implementation checklist and verification commands.
- `addressing-plan.md` - subnet and gateway assignments following a consistent master blueprint.
- `topology-description.md` - device roles, link types and port-level mapping.
- `failure-testing.md` - structured failure scenarios to inject and recover from.
- `expected-outcomes.md` - success criteria and reflection prompts.

### Simulator support

Unlike the troubleshooting labs which require Packet Tracer `.pkt` files, the greenfield curriculum is **simulator-agnostic**. Build in Cisco Packet Tracer, GNS3, EVE-NG, Cisco Modeling Labs (CML) or physical hardware.

### How to use it

- **Self-study**: work labs in order for a structured 50-day or 90-day CCNA path. Read the README, build the topology using the addressing plan and topology description, then verify using the expected outcomes and failure testing guides.
- **Instructors**: treat each lab folder as a lesson module with built-in answer keys, break/fix exercises and student reflection prompts.
- **Revision**: re-use later-phase labs (30–50) and the advanced projects as capstone scenarios.

See the full curriculum guide in [`ccna-in-90-greenfield/ccnain90/README.md`](./ccna-in-90-greenfield/ccnain90/README.md).

---

## Suggested Learning Paths

**New to networking?** Start with the greenfield foundations (Labs 01–10), then try TechPeak Enterprise as your first troubleshooting lab.

**Preparing for CCNA?** Work through the full greenfield core track (Labs 01–50), then tackle the troubleshooting labs in order of size to build triage discipline.

**Already certified, want practice?** Jump straight into National Bank, Cardinal Capital or Northgate DR for challenging incident simulations, or the advanced projects.

---

If you find this repo helpful, give it a ⭐ - it helps others discover it.

Good luck.
- Olumayowa 