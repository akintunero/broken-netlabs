# Cardinal Capital Investment Bank: Trading Floor Down

## The story

Cardinal Capital is an investment bank with a London headquarters, a New York office and a data centre that runs the trading engine, the database tier and backups. Over the weekend the network team rebuilt the trading, employee, risk, administration and market-data networks, with resilient paths to the central services and tighter access controls between desks.

It is 06:40 on Monday, twenty minutes before London opens. You are the engineer on call. The trading desks have already raised twenty problems. A trading PC cannot reach the server room. An employee PC is stuck on a dead segment. New York staff are not getting addresses. The market-data feed is silent, and employees can suddenly see risk systems they should never touch.

Every minute of downtime costs money. The architect is unreachable. You have the console and the tickets.

Work out what is broken, prove why, fix it properly and leave the bank in a state you would hand to the next shift.

## What you receive

| File | Purpose |
|---|---|
| `Cardinal-Troubleshooting-Student.pkt` | The bank network for Cisco Packet Tracer 9.0.1 |
| `WORKBOOK.md` | The 20 tickets, discussion questions and a fix log template |

Console and enable password on every device: `Lab#2026`. Username `netadmin`. Domain `cardinal.lab`.

## What the network looks like

- **London HQ:** two HSRP core switches, access switches for trading (two), employee, risk, administration and market data, and a server switch with DHCP/DNS and syslog. Two WAN routers and an edge router with NAT to a simulated ISP.
- **New York:** two routers, two HSRP cores and two access switches.
- **Data centre:** two routers, two HSRP cores and an access switch with the trading engine, database and backup servers.
- Addresses follow `10.<site>.<vlan>.0/24` (London 1, New York 2, data centre 3). Some PCs use DHCP.

## What is expected of you

1. **Work the tickets in a sensible order.** Start with what affects the most users. Some faults hide behind others.
2. **Prove the cause before you change anything,** and keep the `show` output.
3. **Fix the root cause.** No workarounds such as extra static routes or removing ACLs.
4. **Change as little as possible.**
5. **Verify after every fix** and confirm nothing else broke.
6. **Save your work** with `write memory`.
7. **Document as you go:** symptom, device, commands, root cause, fix, verification.
8. **Be patient.** Allow up to five minutes for spanning-tree, EtherChannel and routing to settle, and renew DHCP after a fix.
9. **Finish with an end-to-end check** of London, New York, the data centre and the simulated internet (198.51.100.1).

Some blocks are deliberate policy: trading must not reach employees or administration, employees must not reach trading, risk or market data, market data may only reach trading, risk, the servers and the data-centre engine, New York and employees must not reach the database tier, and management is allowed only from the management VLANs. Do not "fix" those.

## Tips from the shift handover

- Start at the bottom: link, VLAN, IP and gateway, then routing, then policy.
- Compare neighbours. If two similar devices differ, one of them is wrong.
- Test what should be blocked as well as what should work.
- Read console messages; they often name the problem.
- Do not guess. Run another `show` command.

Good luck. The market opens soon.
