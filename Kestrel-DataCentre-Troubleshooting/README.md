# Kestrel Data Centre: Migration Weekend

## The story

Kestrel Cloud Services runs its customer platform from a single enterprise data centre. It is built in tiers: web servers, application servers, databases, a cache, storage and backup, and a small infrastructure block with DNS, DHCP and logging. Two core switches connect everything to two edge routers and two internet providers. A campus office, a partner extranet and an out-of-band operations network all connect into the core.

Over the weekend a rushed hardware refresh touched server ports, aggregation switches, routing and access rules. On Monday morning the platform is limping. One web node cannot see the app tier. A database server is offline. Campus staff get no addresses. The partner cannot reach the web portal. The data centre has lost the internet. Some rules that keep the database and backup networks private have quietly disappeared, and others now block more than they should.

You are the on-call network engineer. The service owner wants a status every fifteen minutes. You have the console and the tickets.

Work out what is broken, prove why, fix it properly and leave the data centre ready for Monday's load.

## What you receive

| File | Purpose |
|---|---|
| `Kestrel-Troubleshooting-Student.pkt` | The data centre, campus, partner and operations networks for Cisco Packet Tracer 9.0.1 |
| `WORKBOOK.md` | The 20 tickets, discussion questions and a fix log template |

Console and enable password on every device: `Lab#2026`. Username `netadmin`. Domain `kestrel.lab`.

## What the network looks like

- **Data centre:** two core switches, two edge routers (each with NAT to its own provider), and two server pods. Pod A holds the web and application tiers, pod B holds the database, storage/backup and infrastructure servers. Each pod has a pair of aggregation switches with HSRP gateways and an EtherChannel between them, and dual-homed access switches.
- **Campus:** a multilayer switch behind two campus routers, with user (DHCP) and engineering networks.
- **Partner:** a partner router and a partner PC behind an access policy.
- **Out of band:** an operations router and an operations PC.
- Addresses: data centre `10.10.x.0/24`, campus `10.20.x.0/24`, partner `10.30.1.0/24`, operations `10.40.1.0/24`. OSPF runs across the data centre, campus, partner and operations links.

## What is expected of you

1. **Work the tickets in a sensible order.** Start with what affects the most users. Some faults hide behind others.
2. **Prove the cause before you change anything,** and keep the `show` output.
3. **Fix the root cause.** No workarounds such as extra static routes or removing ACLs.
4. **Change as little as possible.**
5. **Verify after every fix** and confirm nothing else broke.
6. **Save your work** with `write memory`.
7. **Document as you go:** symptom, device, commands, root cause, fix, verification.
8. **Be patient.** Allow up to five minutes for spanning-tree, EtherChannel and OSPF to settle, and renew DHCP after a fix.
9. **Finish with an end-to-end check:** campus to web tier, app tier to database, operations to every tier, and the simulated internet (198.51.100.1).

Some blocks are deliberate policy: the web tier must not reach the database or backup networks, the app tier must not reach backup, campus users must not reach the database or backup networks, the database tier must not initiate to the campus, the partner may reach only the web tier, and management is allowed only from the management networks. Do not "fix" those.

## Tips from the shift handover

- Start at the bottom: link, VLAN, IP and gateway, then routing, then policy.
- Compare one server with another. They are built from the same template.
- Test what should be blocked as well as what should work.
- Read console messages; they often name the problem.
- Do not guess. Run another `show` command.

Good luck. The load builds at 09:00.
