# The Magic World of Searchable Symmetric Encryption

*In the last couple of years, cloud and web services have become more and more popular. Since Snowden we know for sure that intelligence agencies have access to the data storage of an service provider, either by (forced) cooperation, or espionage. Thus, to protect our privacy we have to encrypted our data before hand it over to our service provider (data holder). But this approach contradicts the very idea of a web service where the data holder have to process our data in one way or an other. Therefore, we need new cryptographic techniques to enable the data holder to perform operation on encrypted data. One of the most important operations for cloud storage or database based web/cloud services is the search operation. In this talk we focus on the very familiar cloud storage scenario. Because in this scenario, It is obvious, that the user (data owner) do not want to perform the search by himself. This should be a service offered by the data holder. We will present different practical approaches to achieve searchable ciphertext, namely one with an index and one with cleverly encrypted words. Note that no PhD is required to attend this talk ;-)*

Tobias Mueller, Christian Forler

- https://events.ccc.de/congress/2015/Fahrplan/events/7333.html
- https://media.ccc.de/v/32c3-7333-the_magic_world_of_searchable_symmetric_encryption


## Talk notes

*Missed the beginning of the talk.*

- ...
- ...
- ...
- Hash functions with partially extractable/calculable bit masks.
- Searching.
    - Client `DetEnc()`, sends to server.
    - Hashes are mappable to words.
    - One example shows hashes versus word frequency clouds; hashes can be used to match words.
    - Uses padding to 32 bytes per word.
        - King James Bible.
            - Plain-text 4.3MB.
            - Cipher-text 25MB.
            - Time to encrypt 0.211 seconds.
            - Search 0.181 seconds (worst case).
            - High frequency words get results faster (God 0.003 seconds).
- Index-based search.
    - Index with hashes on client.
    - Encrypted on server.
    - Index has to be downloaded to client?
    - Client creates search index hash and index key hash, based on searched word.
    - The combination is used for an index lookup.
- Side channel leakage.
    - The size of the returned index list provides a hint about result frequency, the size has to be masked.
    - Use an incremental search:
        - Lookup index 0 first.
        - If it exists, lookup index 1 as well.
        - Repeat until no result.
    - King James Bible.
        - Plain 4.3MB
        - Cipher-text 4.3MB.
        - Index size 0.125MB.
        - Time to encrypt 0.108 seconds.
        - Search in constant time -- around 0.001 seconds.
    - This scheme is susceptible to statistical analysis.
- Outlook and conclusions.
    - Shown schemes allow clients to perform server-side operations on encrypted data.
    - Deterministic search token -> statistical analysis.
    - Full He... Encryption (FHE) is not yet a practical option.
    - The shown schemes have been implemented as POC; call for libraries.
- Conclusions of presented schemes.
    - Deterministic encryption.
        - Fast setup.
        - Insecure search.
    - Keyword (Song, Wagner, Perrig (SWP)).
        - Search is O(n).
     - Index (Cash et al.).
         - Search is O(1)
         - Index maintenance is needed (for updates etcetera).
    - Slightly different features.
    - More schemes exists!
    - Searching on encrypted data is practical.


---

Part of [Recap](https://github.com/joelpurra/recap)

