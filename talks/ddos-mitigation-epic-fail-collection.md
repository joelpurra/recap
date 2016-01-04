# DDoS mitigation EPIC FAIL collection

*For the past 3 years I have been delivering a custom-tailored DDoS attacks for organizations that wanted to test out their DDoS defense systems.*

dalmoz (Moshe Zioni)

- Running legitimate security company with botnet for DDoSing.
- Everyone gets DDoSed.
- Method.
	- Legitimate botnet.
	- Selling a DDoS testing service.
	- Blue team, onsite with the company, taking notes for the red team.
	- Red team, attacking the company.
- DDoS in the wild.
	- Rely heavily on bandwidth consumption.
	- 53% of attacks are <2Gbps (SANS).
	- Reflection combined with amplification relies on third-party domains (DNS, NTP, etc).
	- Most attacks do not require brains -- which is why bandwidth attacks are common, but not the best.
- Striking harder doesn't require a larger botnet
	- There's more to the web site than the front-end.
	- Overload the backend by triggering the system to do work.
	- Keep it stealthy; they might be using the "magig of sniffing".
		- Mitigated by custom scripts.
	- Think of amplification in a general way.
- Generalized amplifications 4 pillars.
	- Amplification factors.
		- Network -- the usual suspect.
		- CPU - very limited on some mediators and web application servers.
		- Memory - volatile, everything uses it, multi-step operations is prime target.
		- Storage - can be filled up or exhausting I/O buffer.
- Examples based on true stories.
	- Names have been changed.
	- Rated in "facepalms".
	- Examples.
		# "Limiting the rate of incoming packets."
			- Customer had the ISP limit the _incoming_ packet rate to ensure availability.
			- Use reflection.
				- Download a file from the service, which will choke the _outgoing_ packet rate.
				- 1kb request, 200kb file (or larger) -- 200x amplification.
		# "It's OK now, monitoring shows everything is back to normal."
			- Security guy didn't get any reports from anyone even though he hard ordered the attack and was waiting for a call.
			- Monitoring didn't show that the actual site was down.
			- The service was on the same network as the HQ office -- all email, voip etcetera was down. No-one could report it.
		# "Backend servers are not iumportant to protect against DDoS."
			- People are only looking at the frontend.
			- Attacking the backend takes longer to detect -- requires internal knowledge.
			- Mapping the company network is key for an attacker.
				- Databases are often susceptible to DDoS attacks.
				- Provides grounds for intra-amplification.
		# "Buy shiny box, connect all the domains to it."
			- RTFM.
			- The box uses some unknown algorithms to detect probably attacks.
			- Defense mechanism is "draining" out traffic first, and then does magic.
			- Mitigation kicks in 20 seconds after detection, to build a model or something.
			- The company asked to kill the attack they had ordered, because someone internally was angry.
			- They had connected the corporate domain to the same box.
			- Deep internal infrastructure servers got blocked because they were relying on services connected to the box.
			- Monitoring went dark, because it was also connected to the box.
			- Voip went down, so no internal communications.
		# "We don't trust the vendor, we don't give them certificates."
			- Only HTTP goes through the anti-DDoS box.
			- Defense doesn't monitor OSI layer 7? Do HTTPS attacks.
			- SSL re/negotiation.
			- Transmitting via HTTPS, GET/POST/... -- the vendor box can't detect the contents of the attack.
		# "We need Big Data, collect all the logs"
			- ...
		# "Learning mode -- did you do it?"
			- All is learned.
			- Calibration hadn't been done, so box didn't know enough about normal traffic.
			- Attack is considered legitimate traffic.
			- RTFM.
			- Vendor: "next time, buy our service to calibrate the site."
		# "So what CDN is not dynamic? Let's enable it!"
			- If dynamic content is enabled, CDN will reduce/skip cache and make origin requests more often.
			- CDN: "Not in cache? Ask the origin!"
			- Ask multiple CDN locations.
			- Add random query parameters -- always avoids/busts CDN cache.
			- All requests at the origin look like they come from the CDN -- but can't block the CDN.
		# "How to protect your CDN origin server."
			- Bad recommendation: "use a random subdomain for your origin server, such as `fbhjdkoedfjhcb.example.com`, which only the CDN knows".
			- Find other known subdomain, lookup ip, scan /24 or /16 ip range -- good chance your'll find it.
			- WHOIS never forgets -- lookup some whois history websites.
			- DDoS the ip address.
		# "Block 'em!, now them, now them, now them, now them, now them, now them."
			- Mitigation technique was to block the entire ip range of an attacker; /16 of the attacker ip.
			- In Germany there are about 116M IPs.
			- About 1800 class B ranges.
			- Attacked was changed to come from spoofed ip addresses.
			- With 1800 attack request, all of Germany was blocked.
			- After a while, the defender blocked themselves.
- Collected misconception.
	- There's no magic pill to prepare for or fix DDoS.
	- Prepare a plan, not just a mitigation.
