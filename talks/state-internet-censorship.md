# The state of Internet Censorship

*The techniques to control access to the Internet, and the ability to bring transparency to those processes are both continuing to evolve. We’ll give an update on the landscape of online information controls, and our ability to measure them.*

Will Scott, andz@torproject.org

- https://events.ccc.de/congress/2015/Fahrplan/events/7143.html
- https://media.ccc.de/v/32c3-7143-the_state_of_internet_censorship


## Talk notes

- China's great cannon; DDOS with javascript.
  - Injects a small piece of javascript into HTML.
  - Major Chinese websites infected.
  - Floods targets with traffic from visitor's browsers.
  - Targeted western sites.
- China cracks down on individual developers.
- ...
- Blackberry leaves user data in Pakistan.
- South Korea's "Smart Sheriff" application adds security holes.
- North Korea is using a Squid proxy.
- Gambling online censorship.
  - Over-blocking and "mistaken" blocking.
  - Many EU countries restrict online gambling.
  - Some allow domestic online gambling only.
  - Greek ISPs blocks domain kind of "at will", to follow the law of the Gaming Commission.
    - Some ISP does DPI.
    - HTTP 403 status.
    - Blocking pages.
    - Redirecting to the Gaming Commission website.
    - This has spilled over to other kinds of "illegal content", blocked using the same system with 403 results.
- UK
  - Government pressured ISPs to implement filters.
  - Each ISP decides what/how to block.
    - Dentists, bars, random pages have been blocked.
    - 21013 sites blocked by strict filters (opt-in).
    - 11395 sites blocked by default filters (installed by default, can opt-out).
- Saudi Arabia
  - Uses "WireFilter" hardware/software, marketed as a "worry-free internet experience".
- Iraq
  - On 2015-06-27, internet traffic was blocked.
    - Coincides with high school exams.
    - Only lasted a few hours.
- ???
  - Uses squidproxy.
- Iran
  - 2015-10-20 Users complained that Telegram was blocked.
  - 2015-10-25 The government explained it was because of "disturbances"; term previously used for throttling for censorship.
- US
  - Politicians wants to close down stuff online, because of terrorists.
  - ISIS the main target.
  - Twitter, Facebook etcetera block ISIS stuff.
  - What is being deleted is not known, as private companies perform the censorship.
- Seeing censorship.
  - Some groups/organizations classify research reports by textual markup/analysis.
    - Used as basis of several reports.
    - Often world maps of censorship, journalist safety etcetera.
  - OpenNet Initiative measures censorship, but doesn't publish data as it could be used to find those who measure.
  - `ooni` is an open measurement platform.
    - Send multiple requests, over the open internet and for example Tor.
      - Used can detect differences between the local and global/non-local internet.
      - Differences can be seen as censorship.
    - Raspberry Pi image available, to increase number of endpoints.
  - ICLabs does work.
  - RIPE has an atlas of network coverage.
- Centralized measurements
  - Lots of Tor users spike in Bangladesh during Facebook blocking.
  - Google measures and publishes network outages, but data is non-public.
  - "Herdict". Helps spots web blockages.
  - "Greatfire" measures censorship in China.
- Mobile interference.
  - "Netalyzer" measures ports.
  - "Asia chats" from Net[...] Labs measures blocked words in chat programs.
  - "MeasurementKit"; like "ooni" but for mobile.
- Some software do non-server, non-mitm connectivity analysis with some TCP tricks.
- `zmap` is useful.
- "Satellite" measures ip4 usage for websites.
- New HTTP status code 451 being pushed as a standard in IETF.
  - Used to indicate "legal censorship".
  - What's legal depends on local laws.
  - Can be seen as approving of or giving legitimacy to censorship.
- Human rights protocol considerations research group.
  - Expose the relation between technical protocols and human rights.
- Open technology fund.
  - Lots of money, but from the US government.
  - Seeks alternative funding.
- What about harder-to-detect censorship?
  - Current censorship is easy to detect.
  - Throttling instead of blocking.
  - Platform self-censorship (Twitter?)
  - ISP-level censorship.
  - Social impacts. Do people notice/care/change their ways?
- Some do not like the research being done on their networks.
  - Threatening emails from network admins.
  - Informed consent?
  - US Homeland Security's the Menlo Report discusses ethics in internet measurement.
- What you can do:
  - `pip install ooniprobe`
  - `ooni`/Sattelite
  - Pluggable transports for SOCKS/Tor.
  - Be an advocate in your home area.

