## Survey of Decentralized Social Media Platforms

**Decentralized Social Networks Sound Great. Too Bad They’ll Never Work**. https://www.wired.com/story/decentralized-social-networks-sound-great-too-bad-theyll-never-work/

- social networks difficult to bootstrap due to network effect
- cryptographically secure vs. easy to use
- centralized platforms
  - optimize for advertising revenue
  - prioritize attention-grabbing content (keep people entertained rather than informed)
  - echo chambers, filter bubbles problem
  - benefit from economies of scale (cheaper storage, bandwidth)
- should strive for data portability, interoperability and alternatives to ad-based funding

**Paul Brussee. Survey of robust and resilient social media tools on Android.** 2015. https://arxiv.org/pdf/1512.00071.pdf
- Twimight. http://doi.acm.org/10.1145/2079360.2079367
  - Twitter client with a disaster mode
  - a central Twimight Disaster Server
  - project abandoned
- [The Serval Mesh Network](http://developer.servalproject.org/)
  - WiFi mesh network
  - allows calls, text messaging and file sharing
  - users identified with a phone number
  - Mesh Datagram Protocol (MDP)
  - MITM difficult to defeat in a mesh network
  - Voice over Mesh Protocol (VoMP) – can handle packet loss and mid-call re-routing
  - Rhizome – file distribution system
  - source code: https://github.com/servalproject/batphone
  - project abandoned
- [The Psiphon Proxy & VPN Service](https://psiphon.ca)
  - used in more than 40 countries where internet is censored
  - SOCKS, SSH, VPN protocol
  - obfuscation layer on top of SSH to circumvent deep packet inspection (DPI)
  - no effort to hide client's IP (no anonymity)
  - vulnerable to an insider attack => publish only a limited set of proxy servers to a client
  - Psiphon collects and sells metadata of its users
  - active development, 10M+ downloads
- [Orbot](https://guardianproject.info/apps/orbot/)
  - Tor for Android
  - active development, 10M+ downloads
- Tribler
  - search and content based on gossip in communities
    - AllChannelsCommunity
    - SearchCommunity
    - MetadataCommunity
  - exploit geo location of peers to increase transfer speed
  - self-organizing collaborative filtering
  - free-riders penalized if upload bandwidth is scarce
  - increase speed by collaborative downloading
  - Tor-like network – allows multiple circuits at the same time to increase download speed
  - Tribler for Android: https://github.com/Tribler/tribler-android
  - Tribler Play: https://github.com/wtud/tsap
  - Android Tor Tribler Tunneling (AT3): https://github.com/rjagerman/AT3, https://repository.tudelft.nl/islandora/object/uuid%3Ab258a5e8-002c-4631-9291-04be902119f6
  - Shadow Internet: https://repository.tudelft.nl/islandora/object/uuid%3A67becf41-a124-41af-b3d7-c5a0bad0f99d, record a video, share using Tribler or Bluetooth ad hoc network, source code not available?    
  - DroidStealth: https://github.com/droidstealth/droid-stealth, launch using a phone dialer, app icon morphing
  - SelfCompile App

**J. Pouwelse. Media without censorship (CensorFree) scenarios.** https://tools.ietf.org/html/draft-pouwelse-censorfree-scenarios-02
- objective: standardize protocols for microblogging on smartphones with focus on security and censorship resistance
- introduction:
  - 2011 Arab spring - full internet shutdown
  - forced Facebook login at Iranian airport
- goal: Bluetooth transfer
- 20sec scenario – ability to reach 20 million people in 20 seconds
  - adversary: a simplistic attacker
  - direct or NAT-based internet access
  - bootstrap: a list of default bootstrap peers
- kill-switch scenario
  - adversary: advanced attacker – no internet access
  - mobile ad hoc networks (MANET) – self-organized IP routing among wireless devices
  - delay-tolerant networks (DTN) – use store-and-forward primitive
- friend-to-friend scenario
  - friend-to-friend networking to remove requirement for active networking and wifi sensing, 
  - should deliver privacy-by-design
  - adversary: powerful attacker – no internet access, can monitor wireless communication
  - even possession of apps with encryption is dangerous => stealth app 
- should offer capabilities to report spam, mechanisms for fact validation and reputation

**Scalability & Paranoia in a Decentralized Social Network.** 2011. https://secushare.org/2011-FSW-Scalability-Paranoia
- maximize privacy – hide data, relationships, communication
- forward secrecy
- VMs considered unsafe
  - governments can enfore hosters to provide backdoors
  - servers can manage routing and storage while users are offline
- multicasting for scalability
  - web, messaging – one-to-one communication
  - social network – one-to-many, many-to-many
  - XMPP – no encryption, inefficient base64 encoding
  - IRC – application-level multicast tree, all users need to be knows to the entire network
  - Usenet's NNTP
- solutions
  - we need a distributed application-level private multicast backbone
  - GNUnet (based on Freenet, Tor, I2P), Maidsafe, A3, Tonika

## Existing Solutions

### Decentralized Social Networks
- [Mastodon](https://mastodon.social) – a federated social network resembling Twitter
- [Manyverse](https://www.manyver.se/) – Scuttlebutt-based app for Android, sync via Bluetooth, LAN or internet
- [Steemit](https://steemit.com/) – a Reddit-like online community using tokens to encourage contribution
- [Akasha](https://akasha.world/) – decentralized social network based on Ethereum smart contracts and IPFS

### P2P Messaging Systems
- [Bridgefy](https://www.bridgefy.me/) – properietary P2P messaging based on Bluetooth mesh network, [used in Hong Kong protests](https://www.bbc.com/news/technology-49565587), phone number verification, another properietary alternative: [Firechat](https://www.opengarden.com/firechat/)
- [Bitmessage](https://bitmessage.org) – P2P encrypted communication protocol
- [Briar](https://briarproject.org/) – P2P ecrypted messaging app for Android, sync over Bluetooth, WiFi, or Tor

### P2P File-sharing
- [Arbore](https://github.com/MichaelMure/Arbore) – P2P file-sharing app on top of IPFS

Alternative Internet: https://github.com/redecentralize/alternative-internet

TODO:
- A gossip-based distributed social networking system. https://pure.tue.nl/ws/portalfiles/portal/3524712/Metis255949.pdf
- Brewster Kahle. Locking the Web Open: A Call for a Decentralized Web. http://brewster.kahle.org/2015/08/11/locking-the-web-open-a-call-for-a-distributed-web-2/
- Jonathan Warren. Bitmessage: A Peer‐to‐Peer Message Authentication and Delivery System. https://bitmessage.org/bitmessage.pdf
- Scuttlebutt Protocol Guide. https://ssbc.github.io/scuttlebutt-protocol-guide/
- QUIC
  - http://devsisters.github.io/goquic/
  - https://eng.uber.com/employing-quic-protocol/
  - https://cloudflare-quic.com/
- Bridgefy SDK. https://www.bridgefy.me/
- Spotify – Large Scale, Low Latency, P2P Music-on-Demand Streaming. http://dator8.info/pdf/csc/8.pdf
- Peer-to-Peer Streaming Peer Protocol (PPSPP). https://tools.ietf.org/html/rfc7574
- https://secushare.org/
- https://gnunet.org/en/index.html
