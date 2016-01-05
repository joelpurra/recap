# goto fail;

*Legend has it, the first iteration of the Secure Sockets Layer (SSL) protocol was broken in ten minutes by Phillip Hallam-Baker and Alan Schiffman during a presentation by Marc Andreesen at MIT in 1994. In the following two decades the protocol has been improved and the implementations have been strengthened, but not without a steady stream of implementation vulnerabilities and protocol design errors. From the ciphersuite rollback attack to LogJam, SSL/TLS has seen a diverse set of problems. In this talk we’ll discuss the pitfalls in designing and implementing a cryptographic protocol and lessons learned from TLS up to version 1.2.*

Nick Sullivan

- https://events.ccc.de/congress/2015/Fahrplan/events/7438.html
- https://media.ccc.de/v/32c3-7438-goto_fail


## Talk notes

- SSL started with Netscape 1.1, around 1993-1944.
- Wasn't used that much to start with.
- It has evolved over time.
- Public-key cryptography.
- Authenticated with the public key infrastructure; x509.
- PKI and SSL has had:
    - Implementation bugs.
    - Intentional flaws.
    - ...
- Phases
    - Phase 1
        - Get the certificate.
    - Phase 2
        - Use RSA or DH.
- Implementation problems.
    - GNU TLS 2005-2014.
    - Apple's implementation up to 2014.
    - Netscape/Firefox NSS' ASN-1 based implementations up to 2014.
    - Machine-local proxies.
        - Adds certificates to your local trusted store.
        - Superfish, up to entire countries who wants to use it.
    - Dual EC DRBG.
        - Backdoored crypto.
    - Heartbleed (2014).
        - Another dumb bug.
- Protocol bugs.
    - SSL 1-3
    - TLS 1, 1.1, 1.2, 1.3 upcoming
    - Compression oracles (CRIME & BREACH)
        - HTTP uses cookies; cookies can be guessed.
        - Injecting javascript can make repeated requests.
        - TLS compression adds some holes.
        - Repeated requests with slightly modified/guessed/guessable data can reveal the key.
        - The number of returned packets tell you if you made the right or wrong guess.
    - Padding oracles.
        - Cipher block chaining, instead of plain CBC.
    - MAC-then-encrypt.
        - Signing with a HMAC done before encryption.
        - Padding is added after the message, but not signed.
        - Unauthenticated padding data leaves room to modify data.
            - Guess the key by modifying the padding values.
            - The right key can be figured out with working XOR backwards.
            - The error codes returned reveals which part contains an error; in the padding or HMAC.
            - If it's in the HMAC, you have guessed the padding value's XOR.
            - Can also be done with timing side-channel (padding fail fast, HMAC fails slow).
            - Fix is to always compute the HMAC for the entire message.
    - Lucky 13.
        - More timing side-channel stuff, inside of the HMAC computation.
- Downgrade attack.
    - Drop or modify packages to use a weaker crypto.
    - POODLE.
        - Padding oracle and downgrade attack.
        - "Downgrade dance" in browsers.
    - TLS POODLE.
        - Padding oracle, downgrade attack, implementation attack.
- Lots of SSL/TLS breakage from 2012 or so and onwards.
- Protocol usage.
    - Most modern clients support TLS 1.2.
- Lessons learned.
    - If an attacker can identify *one* bit, it's over.
    - Many side-channels.
    - Trusting unauthenticated data is bad.
    - Don't MAC-then-encrypt -- use AEAD.
    - X.509 and ASN-1 are hard to implement correctly.
    - If old/insecure ciphers are supported, there will be a way to do a downgrade attack.
- New vulnerability: CurveSwap.
    - Attack ECC where curve selection isn't done right.
    - Choose a small curve.
    - Solve DLP.
    - sect163k
        - About the same level as RSA 1024 bit.
        - 4.3% client support.
        - 0.13% Alexa Top 100.000.
        - No publicly broken 160 bit ECC keys yet, but it's also a binary curve which may be weak.

EOT?

