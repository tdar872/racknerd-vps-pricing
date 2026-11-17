# VPS providers: what should you pay, how much RAM does your workload need, and will the renewal price hold? (RackNerd's full plan list, priced)

RackNerd sells five annual KVM plans, starting at **$21.99/year for a 1 GB instance** and reaching **$119.99/year for 8 GB RAM, 7 vCPU, 150 GB SSD and 20 TB of monthly transfer**. The **4 GB plan at $59.99/year** (3 vCPU, 60 GB SSD, 7 TB) is the tier most people should buy, because it clears the 4 GB floor that self-hosted AI tools and multi-container Docker stacks run into.

RackNerd renews at the price you signed up at instead of repricing you later, which is the detail that makes these annual specials worth a second look. Below: every plan with its specs, the RAM floor each workload needs, the billing-cycle math, and how RackNerd's prices sit against IONOS, Vultr, Hetzner, Hostinger and DigitalOcean.

> **Quick pick:** the 4 GB KVM special, **$59.99/year** — 3 vCPU, 60 GB SSD, 7 TB transfer, full root access, dedicated IPv4. Enough headroom for AnythingLLM, Ollama or LibreChat, which need at least 4 GB. 👉 [Check the 4 GB plan's current price and locations](https://bit.ly/RacKnerd)

## Every RackNerd plan, priced

All five are annual-billed KVM specials. Prices are per year, in USD.

| Plan | vCPU / RAM | SSD | Transfer (1 Gbps port) | Price, billed yearly | Order |
| --- | --- | --- | --- | --- | --- |
| 1 GB special | 1 GB RAM | — | — | **$21.99/yr** | [Order the 1 GB plan](https://bit.ly/RacKnerd) |
| 2 GB special | 2 vCPU / 2 GB | 35 GB | 5 TB | **$35.99/yr** | [Order the 2 GB plan](https://bit.ly/RacKnerd) |
| 4 GB special | 3 vCPU / 4 GB | 60 GB | 7 TB | **$59.99/yr** | [Order the 4 GB plan](https://bit.ly/RacKnerd) |
| 6 GB special | 6 vCPU / 6 GB | 100 GB | 12 TB | **$89.99/yr** | [Order the 6 GB plan](https://bit.ly/RacKnerd) |
| 8 GB special | 7 vCPU / 8 GB | 150 GB | 20 TB | **$119.99/yr** | [Order the 8 GB plan](https://bit.ly/RacKnerd) |

The 1 GB tier's CPU count and disk size aren't broken out on the plan listing I checked; the checkout screen shows both before you pay.

Every one of these plans includes the same platform pieces:

- **KVM virtualization**, so each VM runs its own kernel rather than sharing the host's.
- **Full root SSH access** and a dedicated IPv4 address.
- **ctrl**, RackNerd's control panel: reboot, OS reinstall, an HTML5 VNC console for recovery, firewall rules, root password reset, one-click apps, and upgrades.
- **Linux templates**: CentOS, Rocky Linux, AlmaLinux, Fedora, Debian, Ubuntu. Custom ISO installs go through a support ticket.
- **IPv6 free** in the Los Angeles and France locations (up to 100 addresses, requested by ticket after ordering).
- **Multiple datacenter locations**, listed at checkout. Match the location to where your users are; a box in France is a poor fit for an audience in Singapore.
- **24/7 support** for platform issues. The server itself is unmanaged.

## Pick the tier by RAM, not by CPU

Self-hosted stacks exhaust memory long before they saturate cores. RackNerd publishes the RAM floors for its one-click apps, which makes a decent yardstick even if you install everything by hand: n8n and Coolify are comfortable from 2 GB, AnythingLLM, Ollama and LibreChat want at least 4 GB, and OpenClaw wants 8 GB.

| What you're running | Start at | Why that tier |
| --- | --- | --- |
| A bot, uptime monitor, static site, VPN endpoint or personal proxy | 1 GB ($21.99/yr) | Always-on and light; nothing here needs a second gigabyte |
| A small WordPress site, a Flask or Django app, a personal Git server, n8n, Coolify | 2 GB ($35.99/yr) | 2 GB is where Linux plus a web stack stops swapping |
| Several containers, a small database, a few sites behind a reverse proxy, a local LLM front end | 4 GB ($59.99/yr) | Matches the 4 GB floor for the AI one-click apps and leaves room for everything else |
| Heavier self-hosted stacks, many containers, OpenClaw | 6 GB ($89.99/yr) or 8 GB ($119.99/yr) | The 8 GB tier is the only one that clears OpenClaw's requirement |

Business workloads map onto the same ladder. A small business site with plugins, email and traffic spikes typically starts around 2 vCPU and 4 GB, which lands on the 4 GB plan. Several WordPress sites with staging and caching push toward 4 vCPU and 8 GB, so the 8 GB plan. An ecommerce store wants 4 or more vCPU and at least 8 GB before catalog size, concurrent shoppers and checkout load are factored in.

For a rougher capacity estimate, third-party guidance puts a 1–2 GB server at roughly 5–10 lightweight sites and a 4–8 GB server at 20–50, depending on how heavy each one is. Treat those as estimates rather than guarantees; caching and a reverse proxy move the number a lot.

## The billing cycle decides the real cost, and renewal keeps it there

The same 1 GB tier costs **$17.99 on monthly billing** and **$21.99 for a full year** on the annual special. Twelve months of the monthly plan runs to about ten times the annual price, which is the single largest price lever RackNerd gives you.

That creates an odd choice if you want to test the platform before committing: $17.99 buys you one month, $21.99 buys you twelve. On the 1 GB tier the annual plan is $4 more than a single month, so there's little reason to start monthly unless you genuinely expect to walk away within weeks. RackNerd doesn't publish a 30-day money-back guarantee, so the annual price is money spent rather than money held.

Renewal runs on manual invoices. RackNerd generates the renewal invoice 14 days before expiry and emails it, and nothing is charged automatically unless you opt into auto-recharge yourself. You can also generate a renewal invoice from the client area. The amount is billed at your original purchase price rather than a current list rate, so the $59.99 on a 4 GB plan is what year two and year three cost as long as you keep that plan. Miss the invoice and the service pauses for a few days to a week with your data retained; past that window the VPS is reclaimed.

One caveat on upgrades: moving up a tier reprices the plan at the larger tier's own rate, and the locked-in special price doesn't follow you. The upgrade itself is a tier bump with a restart, roughly a minute of downtime, rather than a rebuild. Confirm the renewal figure in the client area before you rely on it for a multi-year budget.

Running the numbers on the two plans most readers choose, assuming the price holds:

| Plan | Year 1 | Years 1–3 | Effective monthly |
| --- | --- | --- | --- |
| 1 GB special | $21.99 | $65.97 | ~$1.83 |
| 4 GB special | $59.99 | $179.97 | ~$5.00 |
| 8 GB special | $119.99 | $359.97 | ~$10.00 |

👉 [Start with the 1 GB plan at $21.99/year](https://bit.ly/RacKnerd) if you only need an always-on box and want the cheapest entry into a KVM instance with a dedicated IPv4.

## RackNerd is unmanaged, and that decides who should shop elsewhere

RackNerd's VPS specials are unmanaged. You get root access and ctrl handles the day-to-day platform work (power, reinstall, console, firewall, one-click apps, upgrades), but the operating system, web server, database, security patching and troubleshooting are yours. Support covers the platform, not your application stack.

That's fine for a developer running containers or a self-hoster who's comfortable over SSH. It's the wrong purchase for anyone who wants someone else to handle updates and incidents. Every provider defines "managed" differently, so if you do go looking for it, read the support policy and check whether it actually covers the OS, control panel, web server, database, email and applications. Some hosts sell a middle tier (core-managed) that covers only part of that list. Managed VPS costs noticeably more and gives up some control in exchange.

If you can't yet work a command line, a VPS is paying for capability you won't use. Shared hosting with cPanel does that job for less.

👉 [Compare all five RackNerd KVM plans side by side](https://bit.ly/RacKnerd)

## How RackNerd's prices sit against other VPS providers

Entry prices across the market are all over the place, and the spread comes from what's bundled. PCMag puts a typical VPS configuration at roughly **$20–$100/month**, while cheapest-plan roundups quote entry tiers from **$2/month**. Those describe different products: the low figures are small self-managed boxes, the high ones are larger or partially managed configurations.

| Provider | Entry price | What that entry price is |
| --- | --- | --- |
| IONOS | $2–$90/mo | 1–24 GB RAM, 10–640 GB SSD, unlimited traffic to 1 Gbit/s |
| Vultr | $2.50/mo | SSD instances, adjustable resources |
| Netcup | €3.35/mo | 2 vCore, 2 GB RAM, 64 GB SSD |
| Hetzner Cloud | €4.35/mo | NVMe SSD, AMD EPYC, Germany/Finland/US regions |
| Hostinger | $4.99–$19.99/mo for the first 24 months | 4–32 GB RAM, 50–400 GB SSD, self-managed Linux, 30-day refund |
| DigitalOcean | $4/mo | 512 MiB RAM, 1 vCPU, 10 GiB SSD at entry; no refunds |
| Liquid Web | $11–$55/mo billed yearly | 1–16 GB RAM, 60–200 GB SSD, cPanel extra |

On effective monthly cost, RackNerd's 1 GB special at about $1.83/month and 4 GB at about $5.00/month land at or below most entry prices above, and the 4 GB tier brings 60 GB of SSD and 7 TB of transfer with it. The trade-offs are real: you prepay a year, there's no money-back window, and the platform is self-managed. Hostinger's 30-day refund and DigitalOcean's hourly flexibility are worth more than the price gap if you expect to change your mind.

## FAQ

### Is $21.99 the price every year, or an intro rate?

The renewal is billed at your original purchase price rather than a repriced current rate, so the special you sign up for is the rate you keep. Upgrading to a larger tier is the exception: the new plan renews at its own rate.

### KVM or OpenVZ, and does it matter here?

KVM is a bare-metal hypervisor, and every VM gets its own kernel, which means you can run any OS and stay isolated from other tenants. OpenVZ is container-based, shares the host kernel, and is lighter but less flexible. RackNerd's specials are all KVM.

### Can I run Windows?

The published templates are Linux only (CentOS, Rocky, AlmaLinux, Fedora, Debian, Ubuntu), and custom ISO installs are available on request through a support ticket. If Windows is a hard requirement, confirm it with support before ordering.

### Do I need 8 GB for AI tools?

Only for OpenClaw, which wants 8 GB. AnythingLLM, Ollama and LibreChat run at 4 GB, and n8n or Coolify are comfortable from 2 GB. The 4 GB plan covers most of that catalog.

## Before you order

Match the tier to the RAM floor of what you're actually running: a proxy or bot gets the 1 GB at $21.99/year, a Docker stack with a database gets the 4 GB at $59.99/year, and anything touching OpenClaw or a dozen containers gets the 8 GB at $119.99/year.

Then confirm two things at checkout: the datacenter location nearest your users, and the renewal amount on the plan you picked, since upgrades reprice rather than carry your special forward. Add a calendar reminder for the invoice that arrives 14 days before expiry, or turn on auto-recharge so a missed email doesn't cost you the server.

👉 [Order the RackNerd plan that matches your RAM floor](https://bit.ly/RacKnerd)
