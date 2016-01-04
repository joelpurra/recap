# How the Great Firewall discovers hidden circumvention servers

*Several years ago, the Great Firewall of China was silently upgraded to find and block circumvention servers that employ encryption to defeat deep packet inspection. The system is now used to block protocols such as Tor, SoftEther, and SSH. In this talk, we will give an overview of how this system works, and how it can be circumvented.*

Philip Winter. 2015-12-27 17:00-18:15
https://media.ccc.de/v/32c3-7196-how_the_great_firewall_discovers_hidden_circumvention_servers#video

## Already known

Research usually one-offs, but collected knowledge is large.

- Domains are blocked by pattern, returning bogus dns results (dns poisoning).
  - You get two responses -- one bogus, one correct. It's a race condition.
  - Facebook is an example.
- Keyword scanning in HTTP requests.
  - Sends a `reset` TCP package back; closes the connection.
- Workarounds include using tunnel services.
  - Tor
  - OpenVPN
  - OpenSSH
  - ...
- DPI of encrypted connections.
  - HTTPS? VPN? Tor?
  - Port number? Type of encryption? Handshake parameters? Flow information?
  - They block more than the want to block.
  - China blocked github.com as a test. Then they unblocked it.
- Testing connections.
  - Tor can be detected by looking at cipher list.
  - Can't be sure -- could be something else, perhaps important for economical reasons etcetera.
  - Connect to the Tor server with a Tor client; if it's successful, block it.
  - Seems modular, with modules for other protocols.
  - Research shows that certain connections are followed up; connections to obfs2/obfs3 bridges are.
  - Spreads out re-connections from different GFW computers and ports.
  - 16k unique prober IP addresses; 95% only seen once.
  - IPs seems to come from ISP pools, plus one dedicated scanning machine.
- Custom GFW software.
  - GFW seems to have a custom TCP/IP stack.
    - TCP sequence numbers are correlated with time.
  - Seems to have a custom Tor client.
    - Uses an uncommon "hello" and cipher suite.
  - The probes leak internal state, showing a central system.
    - A centralized entity might control different proxy servers around the Chinese network.
    - Could also be controlled through switches at ISPs.
    - There seeems to be probe/blocking system downtime once every 25h.
    - In 2012, systems were probed in batches.
    - In 2015, scanning is done in realtime -- around 500ms delay after user's connect to a Tor bridge.
- Probed or blocked protocols.
  - SSH is now unblocked -- not in 2011?
  - VPN, sometimes OpenVPN, SoftEther.
  - Vanilla Tor, obfs2, obfs3.
  - AppSpot, which hosted GoAgent?
  - TLS.
- Tor probes don't use reference implementations.
  - Probe fingerprinting possible.
  - Leaking state through internal obfs3 padding values; they're supposed to be large random values, but sometimes are exactly the same.
- Trolling the GFW.
  - Filling up their blocklist by connecting to random IP/port addresses with Tor from inside China.
  - When a probe connects, don't return `ACK` and don't close the socket.
  - GFW used to blindly block ip addresses; connect to important addresses to have them blocked.
    - Windows update servers.
    - DNS root servers.
    - Google infrastructure.
    - GFW soon started verifying addresses.
  - Send broken or obduscated TCP streams, to break DPI reassembly.
- Tor's pluggable transports.
  - Uses SOCKS5.
  - Scrambles traffic to Turn tor into "something else".
  - API available for C, Go, Python.
  - ScrambleSuit, obfs4 work from within China. Uses shared secrets.
  - "meek" tunnels traffic over CDNs (Amazon, Azure, Google).

EOF
