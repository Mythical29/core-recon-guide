# core-recon-guide

A working reference of OSINT, recon, and threat-intel tools — organized by what you're starting with, not by category buzzwords. these are tools i've actually run,no gimmicks 

## contents
1. [emails, usernames, and account lookup](#1-emails-usernames-and-account-lookup)
2. [images, media, and visual lookup](#2-images-media-and-visual-lookup)
3. [domains, infrastructure, and public footprint](#3-domains-infrastructure-and-public-footprint)
4. [phone numbers](#4-phone-numbers)
5. [social media and people search](#5-social-media-and-people-search)
6. [geolocation and chronolocation](#6-geolocation-and-chronolocation)
7. [breach and dark web monitoring](#7-breach-and-dark-web-monitoring)
8. [malware and file analysis](#8-malware-and-file-analysis)
9. [archives and historical data](#9-archives-and-historical-data)
10. [frameworks and meta-tools](#10-frameworks-and-meta-tools)
11. [a note on use](#a-note-on-use)

---

## 1. Emails, usernames, and account lookup
when you only have an email or a username, these are the first tools i check.

* **[Epieos](https://epieos.com/)** — reverse email lookup. good for google-linked public info and connected account clues.
* **[GHunt](https://github.com/mxrch/ghunt)** — reverse google account lookup. useful when the email belongs to a google account.
* **[holehe](https://github.com/megadose/holehe)** — reverse email registration check. shows where an email may already be registered.
* **[Sherlock](https://github.com/sherlock-project/sherlock)** — reverse username lookup. checks where a handle appears online.
* **[Maigret](https://github.com/soxoj/maigret)** — reverse username lookup. broader than sherlock in many cases.
* **[theHarvester](https://github.com/laramies/theHarvester)** — email and domain footprint lookup. good for finding public emails, names, and subdomains.
* **[Have I Been Pwned](https://haveibeenpwned.com/)** — breach exposure check for an email address.
* **[Intelligence X (intelx.io)](https://intelx.io/)** — search engine for leaked data, breach dumps, and historical web/account records tied to an email or username.
* **[OSINT Industries](https://osint.industries/)** — reverse email/phone lookup that pulls linked accounts across dozens of platforms in one pass.

## 2. Images, media, and visual lookup
when you only have a picture, these are the main tools.

* **[Google Lens](https://lens.google/)** — reverse image lookup. best for broad general search.
* **[Yandex Images](https://yandex.com/images/)** — reverse image lookup. strong for finding similar visual matches.
* **[TinEye](https://tineye.com/)** — reverse image lookup. good for exact copies and old image traces.
* **[Bing Visual Search](https://www.bing.com/visualsearch)** — reverse image lookup. another solid backup.
* **[ExifTool](https://exiftool.org/)** — metadata lookup for images, pdfs, audio, and video.
* **[InVID WeVerify](https://www.invid-project.eu/tools-and-services/invid-weverify/)** — video and image verification tool.
* **[Photo Forensics](https://fotoforensics.com/)** — basic image manipulation check.

## 3. Domains, infrastructure, and public footprint
when you have a domain, ip, or org name, these help map the outside.

* **[SpiderFoot](https://github.com/smicallef/spiderfoot)** — passive recon and footprint mapping.
* **[OWASP Amass](https://owasp.org/www-project-amass/)** — subdomain and attack-surface discovery.
* **[DNSDumpster](https://dnsdumpster.com/)** — quick dns and subdomain overview.
* **[Shodan](https://www.shodan.io/)** — search for exposed services and devices.
* **[urlscan.io](https://urlscan.io/)** — website and link analysis.
* **[crt.sh](https://crt.sh/)** — certificate transparency search for subdomains.
* **[SecurityTrails](https://securitytrails.com/)** — dns history and domain intelligence.

## 4. Phone numbers
when all you've got is a number.

* **[PhoneInfoga](https://github.com/sundowndev/phoneinfoga)** — open-source, pulls carrier info, line type, and social/public footprint from a number.
* **[NumLookup](https://www.numlookup.com/)** — free reverse phone lookup, decent for quick caller-ID style results.
* **[Truecaller](https://www.truecaller.com/)** — crowd-sourced caller ID. especially strong in regions (like india) with heavy adoption.
* **[Twilio Lookup](https://www.twilio.com/docs/lookup)** — api-based, returns carrier, line type (mobile/landline/voip), and porting history.

## 5. Social media and people search
broader identity work once you've got a name, handle, or partial match.

* **[Social Analyzer](https://github.com/qeeqbox/social-analyzer)** — automated profile detection across 1000+ sites with confidence scoring, not just a yes/no hit.
* **[WhatsMyName](https://github.com/WebBreacher/WhatsMyName)** — username enumeration, complements sherlock/maigret with a different site list.
* **[NameChk](https://namechk.com/)** — checks username availability across platforms — useful as the inverse of enumeration (tells you where a handle is *not* taken, which narrows things too).
* **[FastPeopleSearch](https://www.fastpeoplesearch.com/)** — free people-search aggregator, decent for cross-referencing US names/addresses/relatives.

## 6. Geolocation and chronolocation
matching a photo to a place, and a place to a time.

* **[SunCalc](https://www.suncalc.org/)** — sun position and shadow-angle analysis. pairs a date + coordinates with the lighting in an image to narrow down time of day.
* **[Wikimapia](https://wikimapia.org/)** — crowd-tagged landmarks, good for matching distinctive buildings that Google Maps doesn't label well.
* **[Overpass Turbo](https://overpass-turbo.eu/)** — queries raw OpenStreetMap data directly. useful for matching infrastructure (bridge shapes, rail layouts, road patterns) instead of relying on satellite imagery alone.
* **[Wigle.net](https://wigle.net/)** — searchable database of wifi networks and cell towers by SSID/BSSID — niche, but genuinely underrated for narrowing a location from network names.
* **[PeakFinder](https://www.peakfinder.org/)** — matches mountain/skyline silhouettes to a real location. underused outside outdoor/hiking contexts but works well for terrain-based geolocation.
* **[Google Earth Pro (3D)](https://www.google.com/earth/about/versions/)** — skyline and building-angle matching against a real 3D model of the area.

## 7. Breach and dark web monitoring
tracking exposed credentials and leaked data.

* **[DeHashed](https://dehashed.com/)** — freemium breach search engine, broader index than HIBP, searchable by email, username, IP, name, or phone.
* **[LeakCheck](https://leakcheck.io/)** — breach database lookup with a usable free tier.
* **[breach.house](https://breach.house/)** — community-tracked aggregator of disclosed breaches.
* **[databreach.com](https://databreach.com/)** — breach disclosure tracking and news.
* **[Ahmia](https://ahmia.fi/)** — search engine indexing .onion sites that opt in to being searchable. the safer entry point if you need to reference dark web content without manually browsing onion directories.

## 8. Malware and file analysis
sandboxing suspicious files without touching them locally — used directly in the Dynamic Threat Intel section of my portfolio.

* **[Triage (tria.ge)](https://tria.ge/)** — interactive sandbox, free community tier, signup doesn't require a business email. what i used for the AgentTesla writeup.
* **[ANY.RUN](https://any.run/)** — interactive sandbox with live VM detonation and a public task feed. free tier currently requires a business email or Discord-channel verification for personal accounts.
* **[Hybrid Analysis](https://www.hybrid-analysis.com/)** — free sandbox (Falcon Sandbox backend), strong on IOC and YARA-rule output.
* **[VirusTotal](https://www.virustotal.com/)** — multi-engine AV/URL scanning, also correlates IOCs across previously submitted samples.
* **[MalwareBazaar](https://bazaar.abuse.ch/)** — public malware sample repository, browsable by family/signature. the actual source for the AgentTesla sample in my sandbox writeup.
* **[MITRE ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/)** — not a sandbox, but maps observed sandbox behavior to formal adversary tactics/techniques — useful for writing up findings properly instead of just listing IOCs.

## 9. Archives and historical data
recovering deleted or changed content.

* **[Wayback Machine](https://web.archive.org/)** — historical snapshots of websites, deleted-page recovery.
* **[archive.today](https://archive.ph/)** — manual on-demand archiving, useful for capturing a page before it changes or disappears.
* **[CachedView](https://cachedview.nl/)** — quick aggregator pulling cached versions across multiple cache sources at once.

## 10. Frameworks and meta-tools
the directories and orchestration layers that tie everything above together.

* **[OSINT Framework](https://osintframework.com/)** — visual directory of OSINT tools by category. good as a starting map when you don't know what you're looking for yet.
* **[IntelTechniques](https://inteltechniques.com/tools/)** — Michael Bazzell's toolset and methodology, especially strong for search-engine dorking and people search.
* **[Maltego](https://www.maltego.com/)** — entity correlation and link-analysis across multi-variable datasets. used throughout the CTF writeups in my portfolio.
* **[SpiderFoot](https://github.com/smicallef/spiderfoot)** — also functions as an orchestrator running 200+ modules automatically once you give it a single starting point (email, domain, IP, etc).

---

## a note on use

everything above is meant for lawful, consent-based investigation: checking your own exposure, authorized engagements, journalism, research, or CTF/training exercises. a fair number of these tools — breach lookups, facial/image search, phone and people lookups — can just as easily be misused for stalking or harassment. that's not what this list is for. if you wouldn't be comfortable explaining why you ran a lookup to the person it's about, don't run it.
