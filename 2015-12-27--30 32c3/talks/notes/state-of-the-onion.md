# State of the Onion

*Major changes are underway in the Tor Project, the Tor Network, and the Tor community. We want to tell you details and introduce the growing Tor community to the larger world.*

Roger, Jacob, Mike Perry, Shari Steele, Alison Macrina

- https://events.ccc.de/congress/2015/Fahrplan/events/7307.html
- https://media.ccc.de/v/32c3-7307-state_of_the_onion


## Talk notes

- Unlikely partners.
    - Facebook, and their .onion address.
    - IETF, and the recognition of .onion as a special use domain name.
- Usage incidents.
    - Russia.
        - From 180k to 400k users.
        - Two major drops in users.
    - Bangladesh.
        - Facebook blocked; users moved to Tor.
    - Carnegie Mellon University (CMU) in Pittsburgh.
        - Researchers did badly executed research.
        - De-anonymization of users.
        - When Roger contacted them, they went silent.
        - Was scheduled for a Black Hat talk in 2015, but pulled.
        - Rumored to be connected to FBI.
- Notable.
    - New executive director.
        - Roger was interim executive director.
    - Citizenfour wins an Oscar.
    - Reddit funds Tor.
    - UN Special Rapporteur endorses Tor.
    - Tor offices now in both Boston and Berlin.
        - Economically and organizationally separated.
        - Zwiebelraum.
    - Break into teams.
        - Network, application, metrics, other teams.
- Metrics team.
    - About one person getting paid.
    - About 30 active code bases.
    - Measures things, for example to find bad relays.
        - Looks at new relays every hour.
        - Visualizing historical relay data to find groups.
        - RESTful API for investigation.
        - CollecTor for analysis.
            - 1TB of data.
            - Also basis for Tor Metrics page.
            - Stem (python).
            - Metrics-lib.
            - Zossh.
            - Meetings on IRC.
- Applications team.
    - Browser.
        - New Firefox releases.
        - Need to audit.
        - Stay in lockstep with FF releases to avoid disclosure attack windows.
        - New HTML5 features.
        - Privacy, security, usability.
        - Protects against all pwn2own hacks.
        - Security slider for easy configuration.
        - Displays the Tor circuit in-browser.
        - Trying to convince FF to separate third-parties for increased privacy.
        - Exploit bounties.
    - Tor Messenger.
        - Goal is to minimize Tor and OTR configuration by providing a self-contained app.
        - Mozilla platform.
            - Shared components with Tor Browser.
        - Protocol parses written in javascript.
        - Don't use jabber.ccc.de because of too much centralization.
        - Riccochet.
            - No MITM (self-auth names).
            - Metadata and social graph via correlation only (high false positives).
- Culture.
    - Tor-ified museum in Oldenburg.
    - Tor working on getting out to libraries.
        - Macrina a radical militant librarian.
        - Library Freedom Project, with American Library Association.
        - Also working wit ACLU.
        - Taught 2300 librarians about Tor and other anonymity tools.
        - Running Tor relays (exits?) in a New Hampshire library.
            - Department of Homeland Security reported the library to the local police.
            - Library temporarily shut it the relay down.
            - Got a huge coalition to sign a letter in support of the library. (ACLU, EFF, Reporters Without Borders, lots more)
            - Rally for Tor outside library.
            - Relay back up again, with a stronger community.
- New executive director.
    - Steele, the dream candidate.
    - Crowd funding collected $120k from 3000 donors.
    - thejuicemedia.com


---

Part of [Recap](https://github.com/joelpurra/recap)

