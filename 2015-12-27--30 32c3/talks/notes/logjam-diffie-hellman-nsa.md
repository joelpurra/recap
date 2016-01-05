# Logjam: Diffie-Hellman, discrete logs, the NSA, and you

*Earlier this year, we discovered that Diffie-Hellman key exchange – cornerstone of modern cryptography – is less secure in practice than the security community believed. In this talk, we’ll explain how the NSA is likely exploiting this weakness to allow it to decrypt connections to at least 20% of HTTPS websites, 25% of SSH servers, and 66% of IPsec VPNs.*

J. Alex Halderman, Nadia Heninger

- https://events.ccc.de/congress/2015/Fahrplan/events/7288.html
- https://media.ccc.de/v/32c3-7288-logjam_diffie-hellman_discrete_logs_the_nsa_and_you


## Talk notes

- At 31c3 it was shown:
    - NSA documents show most crypto is broken, but not all.
    - Cloud services are broken.
    - Which ones are not broken?
- Steps to break.
    - Attack implementations.
    - Attack crypto algorithms.
- RSA.
    - Created in 1977, still not broken.
    - Cryptanalysis still hard; number field sieve best/fastest one so far.
        - 512 bit < 1 year. Can be done in 4 hours for $75 on Amazon.
        - 768 bit < 1000 core years. First time publicly in 2009?
        - 1024 ~ 1.000.000 core years. In range for a large government.
        - 2048: minimum recommended key size today.
- Diffie-Hellman.
    - Public key crypto key exchange.
    - Initial paper did everything right.
    - Can be used for perfect forward secrecy.
- DH cryptanalysis
    - PFS might not be the solution.
    - Discrete log analysis, using number field sieve discrete log -- almost the same as for RSA.
    - Time
        - 512 bit ~ 10 core years.
        - 768 bit ~ 35000 core years.
        - 1024 bit ~ 45000000 core years.
        - 2048 minimum recommended.
    - Many connections may use the same prime key parameter `p`.
    - This can be used to break many connections at the same time.
        - 512 bit ~ 10 minutes.
        - 768 bit ~ 2 days.
        - 1024 bit ~ 30 core days.
    - The teachers of cryptography are excusing themselves for not noticing that other cryptographers had pointed this out before.
- Exploiting DH.
    - Logjam attack.
    - Trick browsers to use old crypto; negotiate cipher suites from the 1990s cryptowars.
    - Legal export limitations are 512 bits for both RSA and DH.
    - FREAK attack.
        - Force RSA export 512 bit.
        - 9.6% of Top 1M Alexa HTTPS sites.
        - 512 bit factorization.
    - Logjam attack.
        - Use DH export 512 bit.
        - 8.4% of Top 1M Alexa HTTPS sites.
        - Discrete log factorization (?).
        - Active downgrade attack.
            - Protocol flaw: the server doesn't sign the chosen cipher suite.
            - Replaces client's hello's `DHE` with `DHE_EXPORT` key exchange in flight.
            - Replaces server's hello-reply's `DHE_EXPORT` with `DHE`.
            - Bit lengths aren't checked/verified at this point?
            - The `Auth_kmc` and Auth_kms` messages are exchanged in flight, after breaking the 512 bit key.
            - Internet-wide scanning.
                - 97% of `DHE_EXPORT` hosts use one of 3 512 bit primes.
                    - 80% apache 2.2
                    - 13% mod_ssl 2.3.0
            - With pre-computation for these 3 512 bit primes, after 1 week pre-computation, median individual logjam (breakage) time is 70 seconds.
            - Logjam can break 8% of Top 1M Alexa sites.
            - IE, Chrome, Firefox: 1024 bits minimum; Safari 768 bits.
            - TLS 1.3 draft includes anti-downgrade flag in client random.
- Mass surveillance.
    - Governments can exploit 1024 bit discrete log DH for passive (offline?) breakage.
    - With custom hardware, DH 1024 bit pre-compute times can be lowered a lot.
        - 80x speedup gives ~$100M cost for pre-computing 1 single 1024 bit key per year.
    - in 2012, NSA were said to have made a breakthrough in breaking public key crypto.
    - $100M investments are within NSA's reach; Snowden documents shows it.
    - A single 1024 bit precomputed prime would break
        - 66% of VPN servers.
        - 26% of SSH servers.
        - 18% of Top 1M Alexa HTTPS sites.
    - Slides show that NSA can break VPNs.
        - At least IKE internet key exchange for IPsec VPN.
        - The target is getting the pre-shared key, then collect traffic.
        - System architecture details are shown in NSA VPN orchestration slides.
        - IKE is similar to discrete log breaking.
    - The same kind of attack can break HTTPS, SSH, IMAP, SMTP etcetera.

EOT?


---

Part of [Recap](https://github.com/joelpurra/recap)

