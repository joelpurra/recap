# Breaking Honeypots for Fun and Profit

*We will detect, bypass, and abuse honeypot technologies and solutions, turning them against the defender. We will also release a global map of honeypot deployments, honeypot detection vulnerabilities, and supporting code.*

- https://events.ccc.de/congress/2015/Fahrplan/events/7277.html
- https://media.ccc.de/v/32c3-7277-breaking_honeypots_for_fun_and_profit


## Talk notes

DeanSysman, Gadi Evron, Itamar Sher

- Cyber Deception.
  - Find out what the bad guys are doing by tricking them.
  - Attacks s attackers detection.
  - Attackers have to search the target network for flaws.
  - Observe, orient, decieve, attack (OODA).
  - Considered in planning an intelligence operation.
  - Requires a decoy.
  - The decoy normally is receiving no traffic.
  - If there's traffic, it means it's an attacker.
  - Low interaction honeypots useful for malware and scanning detection.
    - Limited by definition, as it's an emulation of another service to lure the attacker.
  - High interaction honeypots are higly instrumented real services.
- Fingerprinting.
  - Can be a vulnerability.
- Low interaction honeypots.
   - Scripting of default protocol behavior.
   - Monitoring built into it.
- High interaction honeypots.
  - It's the actual network services/machines.
  - Needs to be monitored.
  - Difficult to properly implement.
- Shodan.
  - "Honeypot or not?" service.
- "Artillery" project.
  - A combination of a honeypot, monitoring tool, and alerting system.
  - On github.
  - Sends lots of random data to the attacker.
  - No real deception.
  - Detection is trivial.
  - Can be used to block any IP internally in a network by spoofind source IP.
- "BearTrap" project.
  - Implements some services.
  - Sends a default banner with status code 220.
  - Easily detected.
  - Waits for a user command, then returns status code 530.
  - Can also be tricket into blocking a spoofed source IP.
- "honeyd" project.
  - Configurable platform for honeypots.
  - Default script detectable; has to be replaced.
    - Spoofs IIS web server by default -- easily fingerprinted.
    - Doesn't implement `DELE` command for FTP.
    - Some SSH stuff detectable.
- "Nova"
  - Detectable.
    - Default windows config has no NetBIOS-service.
    - ...
  - Looking at _all_ services can fingerprint the honeypot.
- "Kippo"
  - Many commands aren't implemented.
  - `wget` is implemented.
  - Can be used for DDoS, port scan.
  - Can be detected.
    - Detecting can be achieved in the SSH connection.
    - `uname` is always the same.
      - Searching for the string gives lots of sysadmin questions in forums; "this machine on my network is weird".
- "Dionaea"
  - Written with the goal to get a copy of the malware used in attacks.
  - Can be detected.
    - Portscan shows MS SQL server with "honeypot" in the name.
    - HTTPS certificate is issued to a dionaea domain.
  - Developers are aware of detection problems, but can't fix all of them with reasonable work.
  - Attackers risk losing resources.
- "Glstopf"
  - Emulates thousands of known web security holes.
  - Can be detected.
    - Default web site front page needs to be customized.
    - Implements directory traversal security hole. Returns default `/etc/shadow`.
    - Directory traversal can be used to list `/proc/` -- if it's emulated you can see it. If it's a real machine, you can read out memory contents.
- "KFSensor"
  - Commercial Windows honeypot/IDS.
  - Gives audio feedback for attacks.
    - Default configuration gives lots of feedback for `broadcast requests`.
  - Can be detected.
    - Hosting a default web page.
    - Limits conncetions to 40 before blacklisting.
- World honeypot deployment.
  - Using zmap daily scan of port 443.
  - Looking through HTTPS certificate domain results for dinoeae domain name.
    - Taiwan, US, Japan the largest number of servers.
    - Largest hosts are in a Taiwanese ISP, a US university, Taiwanese university.
    - Random organizations around the world also deploys dioneae.
- Lessons learned.
  - Detection flaws are easy to find.
  - Should deploy the service.
  - Should deploy the whole service.
  - Should make the set of services make sense for the specifik machine.
  - Should make the service exploitable to unknown exploits.
  - ...
  - ...

EOT?

