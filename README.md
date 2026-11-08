# Unmanaged Linux VPS Hosting: What Does It Really Cost, What Happens at Renewal, and Where Does Support Stop? (Verified Price Table and Plan-Sizing Rules)

Unmanaged Linux VPS hosting starts at $4.99/month for 1 vCPU, 1 GB RAM and 30 GB of SSD on a published monthly price list; 2 cores with 4 GB RAM and NVMe storage starts around $11/month. Those are list prices rather than first-term teasers, so they give you a realistic floor for budgeting.

Two things decide whether you still like the deal in month thirteen. The renewal price is one. The other is where the host's support obligation ends, because on an unmanaged plan that line sits much closer to the hardware than most buyers expect.

SpinServers sells VPS plans alongside a much larger dedicated-server business, and its tier names, stock and pricing shift with promotions, so the price table below uses figures I could confirm on other providers' published pages. The SpinServers links take you to its current VPS list. Everything else here applies to any unmanaged Linux VPS you buy, including theirs: the responsibility split, the renewal math, the backup and firewall defaults, and the sizing rules.

> **Quick pick:** for a single small site, a script stack or a test box, 2 vCPU / 4 GB RAM / 60–80 GB NVMe is the sensible floor, and list prices for that shape run about $11–$19/month. Skip 1 GB plans unless the box only does DNS, WireGuard or monitoring. 👉 [Check SpinServers' current unmanaged Linux VPS tiers and pricing](https://bit.ly/Spinservers)

## What unmanaged Linux VPS plans actually cost right now

These are list prices from providers that publish their full tables, collected as monthly figures. Treat them as the market's shape rather than a ranking: a 2-core plan with 4 GB and NVMe costs roughly the same at several hosts, and the spread widens as you climb.

| Provider | vCPU | RAM | Storage | Price (monthly list) |
| --- | --- | --- | --- | --- |
| Hostwinds | 1 | 1 GB | 30 GB SSD | $4.99/mo |
| Hostwinds | 1 | 2 GB | 50 GB SSD | $9.99/mo |
| Hostwinds | 2 | 4 GB | 75 GB SSD | $18.99/mo |
| Hostwinds | 4 | 8 GB | 150 GB SSD | $38.99/mo |
| Hostwinds | 8 | 32 GB | 400 GB SSD | $124.99/mo |
| blastvps (Ryzen 9 3900X) | 2 | 4 GB | 40 GB NVMe | $10.99/mo |
| blastvps (Ryzen 9 3900X) | 3 | 6 GB | 60 GB NVMe | $19.99/mo |
| blastvps (Ryzen 9 3900X) | 6 | 12 GB | 100 GB NVMe | $39.99/mo |

A few details sit outside the table and matter. Hostwinds puts a 1 Gbps port, snapshots and custom ISO support on every unmanaged tier. blastvps runs KVM on Ryzen 9 3900X cores with unlimited bandwidth and offers an out-of-band VNC console alongside SSH, which is the thing you want when a firewall rule locks you out of your own box.

## Where the responsibility line falls on an unmanaged plan

Unmanaged means you own the operating system and everything above it. The split is usually stated plainly somewhere on the host's site, and it's worth reading before you buy rather than after.

The clearest version I found is hosting.com's: "You manage everything above the operating system: OS choice and updates, security patching, your software, and your own backups unless you add ours. We manage everything below it: the physical hardware, power, network, and data centre." InMotion Hosting words the same boundary from the customer's side: "You handle everything above the hardware: operating system updates and security patching, software installation and configuration, firewall rules, backups, and troubleshooting your applications."

Hostwinds draws the line even tighter. Its unmanaged guarantee is that the VPS "can start up and is 'functional' with the power, networking, and connection between your server and Hostwinds," followed by the sentence "Hostwinds will supply no other assistance or support." InMotion's support scope is similarly narrow: "24/7 human support for your hardware, network, and data center only."

Translated into tickets you might actually open:

- Nginx won't start after an update, MySQL is eating RAM, or you broke sudoers. Yours, on every unmanaged plan above.
- The node loses network, the host's uplink drops, or the physical disk fails. Theirs.
- Your data is gone because you had no backups. Yours, unless you bought a backup add-on.
- A DDoS flood saturates your port. Depends on the provider. InMotion includes Always On DDoS protection at the edge on self-managed plans; smaller hosts often don't.

That's what the lower price buys: the hardware, the power and the network, and nothing above the OS. If you're fine with that trade, 👉 [see what SpinServers currently lists for unmanaged Linux VPS](https://bit.ly/Spinservers) and compare the specs against the sizing rules further down.

## The renewal price is the number that decides your second year

Monthly list prices make comparison easy, and they're also where budget hosts hide the gap. InMotion publishes both numbers for its self-managed VPS: plans start at $13.99/month on a 24-month term and renew at $26.99/month, with higher tiers running $21.99 to $44.99/month on the first term and renewing between $56.99 and $121.99/month. On the entry plan, year two costs roughly twice what year one did.

Do the arithmetic before you commit to a long term. A $13.99 plan on a 24-month term is $335.76 for the first two years; the same plan at $26.99 renewal is $647.76 for the following two. If you're keeping the server for years, the renewal rate is your real budget line, not the headline.

Hostwinds and blastvps both display monthly prices with no separate renewal figure in their tables, which usually means the listed rate is the ongoing rate. Confirm it before checkout anyway. Promotional pricing and "locked for life" language are different things, and only one of them survives your second invoice.

## Defaults that catch people: backups, firewalls, snapshots, panels

Backups are the most common gap. hosting.com's managed-versus-unmanaged table lists backups as optional on unmanaged and daily-included on managed. InMotion puts backups in the customer's column outright. Hostwinds does include automated nightly backups to object storage on its unmanaged plans, with configurable run times and retention, plus whole-server or single-file restore. If backups aren't mentioned on the plan page you're reading, assume they don't exist and price out your own.

Firewall placement is subtler. Hostwinds implements its firewall outside the server's operating system, and the stated reason is that a standard Linux software firewall "can be disabled maliciously or accidentally." A host-level firewall keeps filtering even after someone with root runs the wrong iptables command. On most budget VPS plans, your only firewall is the one you configure inside the OS, which means a bad rule can lock you out until you use the provider's console.

Snapshots are not backups. They're fast and useful before an upgrade, and Hostwinds and InMotion both offer them, but they typically live on the same infrastructure as the server.

One more gotcha worth knowing if you plan to run containers: InMotion's Docker-ready configuration, which ships Docker Engine and Compose with raised process and container limits, is only available on the self-managed plans without a control panel. Want cPanel? You lose the pre-built Docker image. Want Docker pre-installed? Install cPanel yourself afterwards, and license it yourself.

## How much VPS you need, by workload

Most buyers overbuy on RAM and underbuy on storage. This table maps common jobs to specs that list prices support.

| What you're running | vCPU | RAM | Storage |
| --- | --- | --- | --- |
| DNS resolver, WireGuard endpoint, uptime monitor | 1 | 1 GB | 20–30 GB |
| Static site or cached WordPress with a CDN in front | 1–2 | 2 GB | 40–50 GB |
| App server with a small MySQL or Postgres on the same box | 2 | 4 GB | 60–80 GB |
| Docker Compose stack: app, database, reverse proxy, Redis | 4 | 8 GB | 100–150 GB |
| CI runner or several containers under real load | 8 | 16–32 GB | 200 GB+ |

Two practical notes. Compiling anything (Go binaries, Node modules, kernel modules) is where a 1-core box hurts, not where a static site hurts. And a database sharing a box with your app will eventually want its own RAM, at which point the jump from 4 GB to 8 GB is cheaper than the outage.

## Who shouldn't buy unmanaged at all

If you want to keep using cPanel and expect the host to patch the OS, unmanaged is the wrong product. hosting.com says so directly, recommending a managed VPS for anyone upgrading from shared hosting who wants to keep an intuitive control panel. InMotion's comparison puts managed plans with businesses that have no server administrator, and self-managed with developers and teams that have sysadmin experience.

Also skip unmanaged if you can't recover a server from a serial or VNC console. Every host eventually has a customer who broke networking at 1 a.m.; on an unmanaged plan, that customer fixes it.

Before you order, check the current specs against your workload rather than the marketing tier names: 👉 [compare SpinServers' live VPS configurations](https://bit.ly/Spinservers).

## FAQ

**Is "self-managed" the same as "unmanaged"?**
Yes. InMotion labels the same product "Self-Managed VPS" and describes it in the page copy as "unmanaged VPS hosting." If a provider uses either term, expect root access and no OS-level support.

**Is a cloud VPS different from a VPS?**
Usually not. InMotion states that the terms overlap and most products marketed as cloud VPS are virtual private servers; its own VPS plans run on high-availability clusters with fixed monthly pricing rather than hourly metering. When you compare "cloud" against "VPS," compare the actual resources, the billing model and the support scope.

**Can I install Docker?**
On any plan with full root access and a supported kernel, yes. Pre-built Docker images are rarer; InMotion's requires choosing a plan without a control panel.

**Can I add cPanel later?**
You can install and license it yourself on most unmanaged plans. hosting.com offers cPanel licences across its tiers and runs them on AlmaLinux. Check that the plan has enough RAM, since cPanel plus a mail stack on 2 GB is unpleasant.

**Who fixes it when something breaks?**
The host handles hardware, power, network and the data centre. You handle the OS, the packages, the application, the firewall rules and the data. Hostwinds' guarantee stops at the server starting up and being reachable; InMotion's 24/7 support covers hardware, network and data centre only.

**How many IPs and how much bandwidth do I get?**
It varies enough that you should read the plan line. Hostwinds includes 1 TB of transfer on its $4.99 tier and scales to 9 TB on the largest; blastvps advertises unlimited bandwidth on all four tiers; InMotion includes multiple dedicated IPs on higher plans. If you're serving video or running a mail server, the IP count and the transfer cap matter more than the CPU.

## Picking a tier without overpaying

Match the plan to the job and stop there. A DNS resolver, VPN endpoint or uptime probe runs fine on 1 vCPU and 1 GB, and that's the $5/month class. A single cached site or a small API needs 2 GB and one or two cores. Anything running a database plus an application server should start at 2 vCPU and 4 GB, and a container stack with four services wants 4 vCPU and 8 GB before it wants more disk.

Three things to confirm before you pay: the renewal price in writing, whether backups are included or billed separately, and which data centre your plan lands in relative to your users. If any of those answers is missing from the plan page, ask support before checkout rather than after.

When you're ready to compare the current tiers, 👉 [start from SpinServers' unmanaged Linux VPS listings](https://bit.ly/Spinservers) and check the specs against the table above.
