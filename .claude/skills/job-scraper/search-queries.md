# Search Queries for Job Scraper

<!-- Configured via /setup --section search. Re-run that command to update. -->

This profile runs **two tracks**. Track A is the priority; Track B is a backup and should be surfaced separately, not weighted equally with Track A in results or evaluation.

- **Track A (priority):** Fully remote marketing/ops roles at US-based, remote-friendly companies. No location constraint.
- **Track B (backup):** Physical relocation to Australia, New Zealand, or Canada on a working holiday visa (eligible: Australia subclass 462, New Zealand Working Holiday, Canada via IEC/SWAP Recognized Organization). Ireland and South Korea are excluded — not eligible (student/recent-grad requirements).

## Search Sites

**Track A:**
- **linkedin.com/jobs** - filter for remote / work-from-anywhere roles
- **indeed.com** - remote filter
- Company career pages via Google `site:` searches (see target companies below)

**Track B:**
- **seek.com.au** - Australia's largest job board
- **seek.co.nz** - New Zealand's largest job board
- **jobbank.gc.ca** - Canada's official Job Bank
- **linkedin.com/jobs** / **indeed.com** - secondary, filtered by country

## Query Categories

### Track A, Priority 1: Primary Role Titles (Remote)

```
site:linkedin.com/jobs "Marketing Operations Manager" remote
site:linkedin.com/jobs "Digital Marketing Manager" remote
site:linkedin.com/jobs "Growth Marketing Manager" remote
site:linkedin.com/jobs "Performance Marketing Manager" remote
site:indeed.com "Marketing Operations Manager" remote
site:indeed.com "Growth Marketing Manager" remote
site:indeed.com "Performance Marketing Manager" remote
```

### Track A, Priority 2: Key Skills

```
site:linkedin.com/jobs "marketing operations" "Google Ads" remote
site:linkedin.com/jobs "marketing operations" "GA4" OR "Google Analytics" remote
site:linkedin.com/jobs "Salesforce Marketing Cloud" remote
site:linkedin.com/jobs "Meta Ads" "campaign management" remote
site:indeed.com "business operations" "campaign management" remote
```

### Track A, Priority 3: Target Companies

```
site:automattic.com/work-with-us marketing
site:zapier.com/jobs marketing OR operations
site:wikimediafoundation.org/about/jobs marketing
site:xapo.com careers marketing
site:supabase.com careers marketing OR growth
site:linkedin.com/jobs ("Automattic" OR "Zapier" OR "Wikimedia Foundation" OR "Xapo Bank" OR "Supabase") (marketing OR growth OR "marketing operations")
```

### Track A, Priority 4: Broader / Similar Remote-First Companies

Wider net for remote-first and work-from-anywhere employers beyond the named target list.

```
site:linkedin.com/jobs "Marketing Manager" "remote-first" OR "work from anywhere"
site:linkedin.com/jobs "Marketing Automation Manager" OR "Lifecycle Marketing Manager" remote
site:indeed.com "Business Operations Manager" marketing remote
"remote-first company" "marketing operations manager" hiring
```

### Track B, Priority 1: Role Titles by Country

```
site:seek.com.au "Guest Services" OR "Hospitality Associate" OR "Front Office"
site:seek.com.au "Warehouse Associate" OR "Logistics Associate" OR "Picker Packer"
site:seek.com.au "Construction Labourer" OR "General Labourer"
site:seek.co.nz "Guest Services" OR "Hospitality Associate" OR "Front Office"
site:seek.co.nz "Warehouse Associate" OR "Logistics Associate"
site:seek.co.nz "Construction Labourer" OR "General Labourer"
site:jobbank.gc.ca "Guest Services" OR "Hospitality"
site:jobbank.gc.ca "Warehouse Associate" OR "General Labourer"
```

### Track B, Priority 2: Skills / Visa-Friendly Signals

```
site:seek.com.au "customer service" "working holiday"
site:seek.co.nz "customer service" "working holiday"
site:indeed.com "working holiday visa" hospitality Australia
site:indeed.com "working holiday visa" warehouse Canada
site:jobbank.gc.ca "working holiday" OR "IEC"
```

## Location Filter

**Track A:** No commute radius. A posting qualifies if it is explicitly remote or "work from anywhere" and open to candidates outside the employer's HQ time zone. Exclude roles requiring on-site presence or relocation.

**Track B:** Must be physically located in Australia, New Zealand, or Canada. No sub-region priority specified — all cities within these three countries are acceptable. Explicitly exclude Ireland and South Korea (visa ineligible).

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Salary Benchmarking

Not configured. Skip salary lookups until a `salary_data.json` source is loaded.

## Visa & Timing Windows (Track B)

Planned relocation window: after **January 9, 2027**. Flag anything time-sensitive against that date.

- **Canada (IEC / SWAP):** IRCC has not announced a 2027 IEC pool opening date as of this writing. The 2023–2026 seasons all opened in **mid-to-late December**, with first invitations to apply following by **mid-January**. Profiles do **not** carry over between seasons — a new IEC profile must be created once the 2027 pool opens. Watch [canada.ca/iec/pools](https://www.canada.ca/en/immigration-refugees-citizenship/services/work-canada/iec/pools.html) starting December 2026. ([Moving2Canada](https://moving2canada.com/2026/11/iec-2027-opening-date/), [pvtistes.net](https://pvtistes.net/en/working-holiday-canada-2027-iec/))
- **Australia (subclass 462):** No annual ballot/cap applies to most nationalities (the ballot system is specific to China, India, and Vietnam) — applications are otherwise rolling. Official processing time was ~49 days as of September 2026, but the government confirmed a deliberate processing slowdown in August 2026 with no stated end date. Given the uncertainty, apply well before the January 2027 travel window rather than close to it. ([Home Affairs processing times](https://immi.homeaffairs.gov.au/Visa-subsite/Pages/Processing-times/Overview.aspx), [visa delay reporting](https://www.techloy.com/australia-working-holiday-visa-delays-2026/))
- **New Zealand:** No reliable 2026/2027 processing-time data was found in this pass — verify current timing directly on [immigration.govt.nz](https://www.immigration.govt.nz) before relying on a specific window.

Re-check this section closer to application time — visa rules and processing times shift quickly and were not re-verified after this setup pass.

## Adapting Queries

If the user specifies a focus area or track, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape remote marketing" -> Track A Priority 1-3 queries + custom role-specific queries
- "/scrape working holiday" or "/scrape relocation" -> Track B queries only
- Default (no track specified): run Track A first, then Track B, and label results by track in the output.
