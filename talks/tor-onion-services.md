# Tor onion services: more useful than you think

*We'll update you on what's going on with Tor onion services, aka Tor hidden services.*

Roger, David Goulet, asn

- https://events.ccc.de/congress/2015/Fahrplan/events/7322.html
- https://media.ccc.de/v/32c3-7322-tor_onion_services_more_useful_than_you_think


## Talk notes

- Hidden services
  - The service is reached through 6 hops.
  - Self-auth, end-to-end crypto, NAT punching, limited surface area.
  - Can be used to run, for example, an SSH server behind a fully locked-down firewall.
  - Decentralized; no user/owner lists, nothing stored to hack.
- Numbers.
  - Some 30.000 unique hidden services.
  - Total of about 1gbps Tor traffic -- about 5% of Tor traffic.
- Started as a toy project for Roger Dingeldine.
  - In 2006 a service with leaked documents was set up, and could not be taken down. This set the tone for further hidden services.
  - Wikileaks set up a server in Sweden.
  - GlobaLeaks (2011).
    - More than 30 projects use it.
    - Does politics, convincing governments to set up services.
  - WildLeaks for animal protection.
  - SecureDrop (2013).
    - Works with magazines.
  - Apex Twin release (2014).
    - .onion link got 4000 retweets on twitter.
  - Security concerns.
    - Bitcoin addresses are being rewritten; tricking users to go to malicious bitcoin websites.
  - Facebook is now available through a .onion address.
    - Even has a PKI EV cert.
  - Public websites.
    - Should be available as an onion service.
    - Gives users a choice -- http, https, onion, https onion.
  - Extra perks.
    - Can only get wild-card PKI EV cert for .onion addresses.
    - Could be incorporated into Let's Encrypt to get a .onion domain?
      - Tech and policy details remain.
  - IETF RFC7686
    - .onion special use domain name.
    - Technical endorsement.
- Third party applications for Onion Services.
  - OnionShare: hosts files over Tor.
  - Riccochet: chat service over Tor.
  - Pond: messaging application.
- Services and tools.
  - Riseup.
  - Jabber servers.
  - `apt-get` package repository.
  - DuckDuckGo.
  - GnuPG.
  - The Pirate Bay.
  - Several Alexa Top 500 sites.
- Guidelines for Tor research.
  - Attack only your own traffic.
  - Only collect data that is acceptable/safe to make public.
  - Minimize collected data.
  - Limit data granularity (add noise).
  - Describe benefits and risks; explain why benefits outweigh risks.
  - Consider auxiliary data when accessing the risks; think about any other datasets.
  - Use a test network whenever possible; `chutney`.
  - Tricky edge cases.
    - Don't abuse the protocol when trust has been gained.
  - CMU did research breaking lots of these guidelines; rumored to be connected to FBI.
- Current security problems.
  - Onion identity keys are too short.
  - Relay identity keys can target particular onion services.
  - It's possible to harvest onion addresses.
  - Sybil attacks remain an issue.
  - ...
- Next generation onion services (NGOS).
  - Work started 2013-11-29.
  - Spare time work; recently some funding.
  - HSDir predictability.
    - It's possible to pre-calculate future HSDir for an onion service.
    - Can be abused by pre-creating relays which will then later be responsible for a certain onion service.
    - Fix is to create a new random value each 24 hours
    - The shared randomness is created by the directory services.
    - The random number is used for relay selection.
  - Better crypto.
    - SHA256 instead of SHA1.
  - Bigger onion addresses.
    - From 16 characters to 52 characters.
    - ed25519 public key base32 encoded.
  - Rendezvous single onion services (RSOS).
    - Instead of a total of 6 hops, "known" and "less anonymous" servers/services can choose to use 4 hops.
    - Better for speed and scaling of public services; see debian and facebook.
  - Single onion services (SOS).
    - Not for anonymity.
    - Better for speed and scaling of public services; see debian and facebook.
  - OnionBalance (RSoP).
    - Load balancing for onion services.
    - Shared key, but selects different entry points.
- Takeaways.
  - Onion services aren't only shady stuff -- lots of different types.
  - Still a small fraction of Tor traffic.
  - Technical advantages make onion services harder/better/faster/stronger.
  - Please deploy a .onion address for your website/service.
    - Would be nice to see more larger services.
- Funding campaign underway.

