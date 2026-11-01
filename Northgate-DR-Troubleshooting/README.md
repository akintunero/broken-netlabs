# Northgate Hosting: The Failover That Wasn't

## The story

Northgate Hosting runs customer web, database, authentication, DNS and backup services from a primary data centre in London, with a disaster-recovery data centre in Manchester and an operations office that manages both. Over the weekend the team reorganised both data centres, tightened the rules between tiers and rehearsed a failover.

It is 03:20 on Monday and the failover rehearsal has left a mess. A web server cannot reach its database. A database port is dead. Office users are not getting addresses. Replication to the DR site is failing, and the DR site has lost its internet and, in places, its own gateways. Some of the controls that keep users away from the databases have also quietly disappeared.

You are the engineer on call. The platform lead is unreachable. You have the console and the tickets.

Work out what is broken, prove why, fix it properly and leave both data centres ready for the next real failover.

## What you receive

| File | Purpose |
|---|---|
| `Northgate-Troubleshooting-Student.pkt` | The two data centres and the office for Cisco Packet Tracer 9.0.1 |
| `WORKBOOK.md` | The 20 tickets, discussion questions and a fix log template |

Console and enable password on every device: `Lab#2026`. Username `netadmin`. Domain `northgate.lab`.

## What the network looks like

- **Primary data centre (London):** two HSRP core switches and four access switches for the web, database, authentication/DNS/DHCP/syslog and backup tiers. An edge router with NAT to a simulated ISP, and two WAN routers.
- **DR data centre (Manchester):** two routers, two HSRP cores and four access switches mirroring the primary tiers.
- **Operations office:** two routers, two HSRP cores and two access switches for office users (DHCP) and operations staff.
- Addresses follow `10.<site>.<vlan>.0/24` (primary 1, DR 2, office 3). OSPF runs everywhere. Replication between the sites must work in both directions.

## What is expected of you

1. **Work the tickets in a sensible order.** Start with what affects the most services. Some faults hide behind others.
2. **Prove the cause before you change anything,** and keep the `show` output.
3. **Fix the root cause.** No workarounds such as extra static routes or removing ACLs.
4. **Change as little as possible.**
5. **Verify after every fix** and confirm nothing else broke.
6. **Save your work** with `write memory`.
7. **Document as you go:** symptom, device, commands, root cause, fix, verification.
8. **Be patient.** Allow up to five minutes for spanning-tree, EtherChannel and routing to settle, and renew DHCP after a fix.
9. **Finish with an end-to-end check** across both data centres, the office and the simulated internet (198.51.100.1).

Some blocks are deliberate policy: office users must not reach the database or backup networks, the web tier must not reach the backup network, office users must not use the DR site directly (operations may), and management is allowed only from the management VLANs. Do not "fix" those.

## Tips from the shift handover

- Start at the bottom: link, VLAN, IP and gateway, then routing, then policy.
- Compare the primary and DR sites. They are meant to mirror each other.
- Test what should be blocked as well as what should work.
- Read console messages; they often name the problem.
- Do not guess. Run another `show` command.

Good luck. The next failover will not be a rehearsal.
