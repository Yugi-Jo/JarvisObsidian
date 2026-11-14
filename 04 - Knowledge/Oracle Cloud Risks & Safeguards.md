# Oracle Cloud — what can take the instance away, and what actually protects it

Researched 14 Nov 2026 after Joel started worrying about losing the agent to an Oracle
reclaim. Everything below was read from primary sources (Oracle docs, the Free Tier
FAQ, the Oracle Cloud Services Agreement and the Universal Credits Service
Descriptions contract PDF) or from dated community reports that are labelled as such.
The guard that acts on this: [[Environment & Access#Keeping the instance (Oracle idle
reclamation)]] and skill `oracle-free-tier-guard`.

## The one rule everyone quotes

> Idle Always Free compute instances may be reclaimed by Oracle. Oracle will deem
> virtual machine and bare metal compute instances as idle if, during a 7-day period,
> the following are true: CPU utilization for the 95th percentile is less than 20%;
> Network utilization is less than 20%; Memory utilization is less than 20% *(applies
> to A1 shapes only)*.

It is an **AND** over three metrics, so holding one above the line defeats the whole
test. The page says **nothing** about notice, a warning email, a grace period, what
state the instance is left in, or what happens to the boot volume. Documented warning
emails exist only for **Free Trial / credit expiry**, not for idle reclamation. Treat
"you'll get an email first" as untrue.

## The things that are worse than idle reclamation

1. **The allowance can be cut, and was.** The Always Free Ampere A1 allowance went from
   4 OCPU / 24 GB to **2 OCPU / 12 GB**, applied silently as a documentation edit on
   **15 June 2026** with enforcement deleting over-limit instances from **18 August
   2026**. Oracle sent "Action Required" emails only *after* the change. Coverage:
   InfoQ, heise. Oracle has never announced the reduction in its own primary sources —
   the old 4/24 figure is still visible in the Internet Archive for the same page.
2. **Contract terms let Oracle end it.** The Universal Credits Service Descriptions
   (effective 10 Sept 2021, p.21) say Oracle may end, on **14 days' notice**, either
   your right to use an Always Free service **or the account itself** if you have not
   used it in the preceding **90 days** — and that Oracle may "in its sole discretion
   remove or modify an Always Free Cloud Service ... at any time". Always Free is
   **excluded from the SLA, the Cloud Service Continuity Policy and the Oracle Cloud
   Support Policy**.
3. **Whole-account suspension or termination.** Documented triggers: crypto mining
   (CSA §1.3(d)), any Acceptable Use Policy breach, false or unverifiable account or
   payment information or a refused card (CSA §9.3(d)), multiple free accounts (one per
   person; sign-up blocks duplicates), a material breach not cured in 30 days (CSA
   §9.4), and mere suspicion — §9.3 lets Oracle suspend when it *believes* a trigger
   applies, with notice only "when reasonably practicable". Separately the FAQ says
   accounts idle 30+ days may be treated as abandoned, while another page says an
   account stays active if used within 60 days. The two are not reconciled.
4. **There is no realistic appeal.** Always-Free-only customers are **not eligible for
   Oracle Support** and cannot raise a service request; the only channel is the
   Oracle-hosted community forum, and community reports say reinstatement requests are
   denied with a final decision. During suspension you typically cannot even sign in to
   the console to download anything.

## What actually happened to people (dated, from r/oraclecloud, HN and Oracle's forum)

- **Idle reclamation** is the most commonly reported cause. Boot volume usually
  survived — but "out of host capacity" for A1 very often then blocks re-provisioning,
  so the service stays down. One reported case: a working Node/Mongo backend reclaimed
  after a quiet week, and the tenancy silently showed the halved 2/12 quota when
  rebuilding.
- **The August 2026 quota enforcement** — a mass event, backed by Oracle's own email.
  Powering the instance off did not protect it: one 4/24 instance was terminated having
  been off all August.
- **AUP bans** — a VPN gateway to a home lab, and accounts using an automated script to
  grab an A1 instance, both terminated with no warning and no successful appeal. One of
  those users: *"the worst part is losing all the data"*.
- **Unexplained terminations**, including on paying accounts, sometimes with audit logs
  showing no actor at all. Rare relative to the above, but real.
- **Counter-evidence matters**: plenty of people report multi-year, trouble-free
  Always Free use, and one HN commenter reported 631 days of uptime. The scary cases
  mostly trace to an identifiable trigger — idle, over-limits, or running something
  that looks like abuse — rather than random deletion.

## Verdict on the popular advice

**Upgrading to Pay As You Go is widely reported to stop idle reclamation** and to have
kept grandfathered 4/24 shapes, and Oracle staff emails quoted by InfoQ say the halved
limit applies only to free accounts. But **Oracle nowhere documents that PAYG exempts an
instance from idle reclamation** — the FAQ only says PAYG gets "different capacity
limits" and that Always Free resources stay free after upgrading. Strongly reported, not
documented. Do not present it as a guarantee.

## What actually protects you, ranked

1. **A complete, encrypted copy off Oracle entirely** — different company, different
   account. This is the only thing that survives losing the whole tenancy. Oracle's own
   terms put backup responsibility on the customer (Hosting & Delivery Policies §1.1)
   and disclaim liability for data loss (CSA §7.1).
2. **OCI boot volume backups** — free (5 backups, 200 GB combined, home region only),
   and a restore can build a new instance. Protects the filesystem, but **it lives in
   the same tenancy**, so it does nothing against account loss. Needs the console or API
   keys; there is no Oracle API access configured on the box.
3. **PAYG upgrade while staying inside the limits** — see the caveat above; needs Joel's
   decision and a valid card, plus a budget alert.
4. **Decouple access from the host** — already done: everything is reached over
   Tailscale by machine name, so a replacement host can take over the name.
5. **A standby host** — the second Always Free shape is only usable by shrinking this
   one, so a genuinely independent standby means another provider. GCP's e2-micro is the
   only other no-expiry always-free VM (weak: ~1 GB RAM, US regions).
6. **An off-box heartbeat** — everything currently watching the server runs *on* the
   server, so a dead box goes quiet rather than shouting. An external pinger (free tier
   of any uptime service) is the missing piece; needs a third-party account.
7. **The idle guard** — cheap and it works, but it is the *smallest* risk of the set,
   and synthetic load is a documented AUP grey area. The passive memory hold is the
   defensible half; the CPU burn was dropped for exactly this reason.

## Traps worth remembering

- **Every OCI-native protection dies with the tenancy.** Boot volume backups, block
  volumes, snapshots: same account, same fate. A recovery copy has to leave the vendor.
- **Don't put the recovery copy and the thing it recovers in one identity** — a single
  GitHub account holding both the code and the backup is one password change away from
  losing both. Hence the Drive copy.
- **Boot volumes persist independently of the instance** and are deleted only manually —
  so a block volume or boot volume surviving an *instance* loss is expected. Surviving
  an *account* loss is not.
- **A1 is Arm/aarch64** and Always Free only exists in the home region
  (`uk-london-1` here), and custom images are region-scoped.
- **Never casually terminate a grandfathered shape** — it cannot be recreated at the old
  size. (Not currently an issue: this instance is already at the new 2 OCPU / 12 GB.)
- **`gomon` reports `MemoryUtilization` here on a 10s sample**, so the memory dimension
  is genuinely measured by Oracle — which is what makes a memory hold a valid play.
