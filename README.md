# my-osint-toolkit / the stuff that actually works

Most OSINT repositories on GitHub are a massive graveyard of 400 broken links to tools that got shut down in 2018. I got tired of bookmarking garbage, so I scraped the actual high-utility stuff from the Bellingcat guides, OSINT Framework, and my own notes. 

Keep it simple. Zero bloat.

***

## 1. emails & usernames 

When you have a target email, your goal is to see where it lives without tipping the guy off. 

* **[Epieos](https://epieos.com/)** — Put an email in here. It queries Google server-side. It pulls their Google ID, their Google Maps review history, calendar settings, and their public Google account photo. The target gets zero notification that you just looked them up. 
* **[Holehe](https://github.com/megadose/holehe)** — CLI python tool. You run `holehe target@email.com` and it checks that email against ~120 sites (Twitter, Instagram, Imgur, etc) using their "Forgot Password" functions. It drops the connection right before sending the actual recovery email, so it's completely silent. 
* **[IntelX](https://intelx.io/)** — Sinks an email or domain into deep-web archives. If the target's email was caught in a 2017 LinkedIn breach or a random Pastebin dump, it spits out the raw plaintext file. 

## 2. mapping infrastructure

* **[SpiderFoot](https://github.com/smicallef/spiderfoot)** — The heavy hitter. Give it a domain or an IP, set it strictly to **Passive Mode**, and go make a coffee. It cross-references a hundred different open APIs to draw a giant map of their subdomains, whois history, and associated netblocks. *(Keep it passive—active mode touches their live server and leaves your IP in their logs).*
* **[DNSDumpster](https://dnsdumpster.com/)** — Free web tool. Spits out a visual map of a domain's DNS routing (MX records, host servers) in 4 seconds. Good for a quick glance before you fire up heavier scripts.
* **[Shodan](https://www.shodan.io/)** — Google searches websites; Shodan searches open ports. You use this to find the stuff the sysadmin forgot to put behind a login screen (open webcams, unpatched RDP ports, raw elasticsearch databases). 

## 3. sketchy files & links

Never double-click a random `.pdf` or `.exe` on your bare host machine just to see what it is. 

* **[VirusTotal](https://www.virustotal.com/)** — The baseline. Upload a file/URL and it checks the hash against 70+ antivirus engines. Don't just look at the red/green score; check the **Relations** tab to see what external IP addresses the file tries to call home to once it executes.
* **[Hybrid Analysis](https://www.hybrid-analysis.com/)** — If VirusTotal just gives you a generic "Malicious" tag, drop it here. It drops the file into a live virtual machine, takes actual desktop screenshots of what the malware did, and hands you the `.pcap` network traffic file.
* **[IPQualityScore](https://www.ipqualityscore.com/)** — Underrated. Normal IP checkers just tell you "This IP is in Chicago." IPQS does deep behavioral checks to tell you *"This is a residential proxy being used by a botnet in Chicago."* Great for checking if an IP hitting your site is a real human or a scraper.

## 4. hashes & cracking

When you actually get your hands on a dump of password hashes, your local machine has to do the math.

* **[John The Ripper](https://github.com/openwall/john)** — `john --wordlist=rockyou.txt hashes.txt`. Uses your CPU. It's smart enough to auto-detect what kind of hash you just fed it (MD5, SHA1, etc). Best for quick offline jobs.
* **[Hashcat](https://hashcat.net/hashcat/)** — The one you use when John isn't fast enough. It offloads the math to your Graphics Card (GPU) to brute-force millions of combos a second. 

#### the wordlists:
* **`rockyou.txt`** — The classic. Originating from a 2009 breach, it’s a `.txt` file of 14 million real passwords. Because human psychology never changes, running a basic attack with RockYou still cracks roughly 30% of legacy user dumps today. 
* **[SecLists](https://github.com/danielmiessler/SecLists)** — Go star this repo right now. It’s the master archive. It doesn't just hold passwords; it holds wordlists for web-directory fuzzing, common default router logins, and SQL injection payloads.

## 5. preservation (bellingcat style)

If you find something juicy, gather it instantly. If the target realizes they are being looked at, they will delete the post 10 minutes later.

* **[Archive.today](https://archive.ph/)** — Paste a URL in here immediately. It takes an immutable, server-side snapshot of the page. Even if the guy deletes his website tomorrow, you have the proof. Bonus: viewing an `archive.ph` link prevents the target's site from running IP-loggers on your browser.
* **[SunCalc](https://www.suncalc.org/)** — Classic geo-location trick. If you have an outdoor photo of a target and you know roughly what city they are in, match the angle of the physical shadows in the picture to the SunCalc interface to figure out the exact hour and minute the photo was snapped.

***

**quick opsec note:** Passive recon is just looking at public billboards; it's legal. Active scanning (firing nmap at some company's live server without written permission) is how you get a polite knock on the door from a guy in a windbreaker. Know the difference.
