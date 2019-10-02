## Survey on Smartphone Ad Hoc Networks

**Decentralized Social Networks Sound Great. Too Bad They’ll Never Work**. https://www.wired.com/story/decentralized-social-networks-sound-great-too-bad-theyll-neverą-work/

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

**Supporting Multi-hop Device-to-Device Networks Through WiFi Direct Multi-group Networking.** 2015. https://arxiv.org/pdf/1601.00028.pdf
- WiFi Direct from Android 4.0, MultipeerConnectivity framework from iOS 7.0 (WiFi, WiFi Direct, Bluetooth)
- WiFi Direct
  - devices organized in groups – group owner (GO) + group members (GM)
  - groups are able to support legacy clients (LC) as group members
  - only defines intra-group communication
  - but a device can operate as a member of multiple groups
  - negotiated during construction of the group, then remain fixed
  - 3 group formation cases
    - standard
      1. nodes listen on channels 1, 6, and 11 in the 2.4 GHz band
      2. send intent value during handshake, the device with the highest value becomes GO
      3.  WiFi Protected Setup (WPS) Provision phase
      4. GO assigns IP addresses using Dynamic Host Configuration Protocol (DHCP)
    - persistent
      - faster reconstruction of previous groups
      - negotiation phase -> invitation exchange
      - WPS Provisioning -> reuse stored network credentials      
    - autonomous
      - a node assigns itself the role of GO and creates its own group
  - GO provides basic service set (BSS) functionality
  - multi-group communication
    - to act as a gateway, a device can use MAC virtualization
    - a device can act as a gateway between local D2D network and the Internet
    - 2 scenarios
      - gateway node acs as a client in both groups
      - gateway is GO in one and a client in other group
    - Android
      - WifiP2pManager
      - GO always has the same IP address (192.168.49.1)
      - GM receive an IP address at random from the range (192.168.49.2-254)
      - not possible to create virtual MAC
      - WiFi Direct can operate simultaneously with an infrastructure wireless network
      - connect a device participating in WiFi Direct group to a second group as LC
      - problem: not possible to create a unicast connection to and from the gateway node
      - solutions: 
        - time sharing - gateway switches between more groups
        - hybrid
        - non-stock Android

**Automatic Android-based Wireless Mesh Networks.** 2014. https://pdfs.semanticscholar.org/69db/c9a052c2ce261b82b40845c211fea09ba31c.pdf
- existing solutions
  - [A multilayer application for multi-hop messaging on Android devices](http://anrg.usc.edu/ee579_2012/Group02/index.html)
  - The Serval Project – requires root permissions, WiFi in ad-hoc mode
  - Open Garden – properietary mesh network, WiFi Direct or Bluetooth
- Android limitations
  - a device may not connect to multiple routers
  - WPS confirmation dialog – but a device can be remembered until next reboot
- implementation
  - a device is either a mesh router or a mesh client
  - a client can act as a relay between routers (needs to temporarly disconnect from the original router)
  - a soft AP, send encrypted SSID and PSK (preshared key) in service discovery broadcast (SSID and PSK generated by Android OS)
  - if a client is in range of more routers, it acts as a relay by taking turns between routers
- security – WPA2 compliant – AES-CCMP or TKIP encryption
- mesh router procedure
  - create a soft AP using WiFi Direct with createGroup
  - wait for soft AP to start
  - pack SSID, passphrase, MAC, and connectivity status (?) into a string
  - encrypt the string
  - broadcast the service information with addLocalService
  - start a netsock server
- client procedure
  - listen to NSD (network service discovery) broadcasts
  - stop discovery after a timeout
  - decide which discovered AP is the best (strongest radio signal?)
  - connect to the best AP using WifiManager
- relay procedure
  - connect to all APs in range using round-robin (future work: more sophisticated routing schemes such as demand and event-based relaying)
  - connect to the first AP, receive data, disconnect
  - connect to the next AP and forward any information it knows
  - the mesh router sends messages which are more recent then last client disconnect time
  - repeat
- message structure
  - header
    - UUID – useful for duplicate message checking
    - message type – data/command, point to point/broadcast
    - MAC address list – to construct route data (note: first 2 chars of MAC should be ignored)
  - data
- broadcasting a message  
  - ignore already received messages using circular buffer
  - if the message is new, process, append MAC to the list and send out
- testing
  - challenge to make NSD broadcast continuously visible (sometimes restart was required)
  - distance 35 m, significantly reduced by obstructions

**Testing Nearby Peer-to-Peer Mobile Apps at Large.** https://hal.inria.fr/hal-02059088/document
- introduces PeerFleet – a test framework for reproducible testing of nearby P2P apps
- https://github.com/m3ftah/NearbyTest

**Nearby Threats: Reversing, Analyzing, and Attacking Google’s ‘Nearby Connections’ on Android.** https://www.cs.ox.ac.uk/files/10367/ndss19-paper367.pdf
- Nearby Connections API
  - uses Bluetooth BR (basic rate)/EDR (extended data rate), LE, WiFi
  - automatically uses the best features depending on the type of communication required (BT for short-range low-latency, WiFi for medium-range high-bandwidth)
  - different connection strategies: point to point/star/cluster
  - clients (discoverers) and servers (advertisers)
  - a part of Google Play Services, proprietary
  - *security through obscurity*  
- paper contributions
  - reverse engineering of Nearby Connections API
  - connection manipulation and range extension attacks
  - REARby – a toolkit for reverse engineering and attacking Nearby API (https://github.com/francozappa/REarby)
- library analysis
  - connection request
    - always using Bluetooth
    - discovering and advertising not encrypted
    - Secure Simple Pairing (SSP) – a link key not authenticated and not persistent
  - key exchange protocol
    - custom based based on ECDH
    - 4 packets    
  - optional physical layer switch
- attacks
  - impersonation
  - MITM on Bluetooth
  - MITM on WiFi
  - attacked-induced physical layer switch
  - injection of default route via attacker AP
  - DoS on all victim traffic
  - radio state manipulation


Cocoon: A lightweight opportunistic networking middleware for community-oriented smart mobile applications. 2016. https://ris.utwente.nl/ws/portalfiles/portal/6411441/cocoon-turkes.pdf
- opportunistic networks (oppnets)
  - enable information sharing through occasional P2P connections
  - delay-tolerant communictions under highly-dynamic routing conditions
- two different routing models
  - Opportunistic Beacon Networking (OBN)
    - messages shared over advertisement beacons (encoded in SSID in WiFI, UUID in BLE)
    - without establishing connections
    - highly-opportunistic limited-throughput data dissemination
  - Opportunistic Association Networking (OAN)
    - beacons exploited for the establishment of connection-based networks
    - small-scale high-throughput group communications
  - literature review
    - 


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

### Mesh Networking SDKs & apps
- [HypeLabs](https://hypelabs.io/)
- [Bridgefy](https://www.bridgefy.me/)
- [Signal Offline Messenger](https://play.google.com/store/apps/details?id=com.raxis.signalapp)

### Android Connectivity
- [WiFi Direct](https://developer.android.com/training/connect-devices-wirelessly/wifi-direct) – from Android 4
- [WiFi Aware](https://developer.android.com/guide/topics/connectivity/wifi-aware) - from Android 8
- [Bluetooth](https://developer.android.com/guide/topics/connectivity/bluetooth)
- [Bluetooth Low Energy](https://developer.android.com/guide/topics/connectivity/bluetooth-le) – from Android 4.3
- [Nearby Connections API](https://developers.google.com/nearby/)
  - a part of Google Play Services
  - introduced in 2015, [fully offline 2.0 in 2017](https://android-developers.googleblog.com/2017/07/announcing-nearby-connections-20-fully.html)
  - Nearby engineers: https://stackoverflow.com/users/5623474/xlythe, https://stackoverflow.com/users/7406756/varun-kapoor


Alternative Internet: https://github.com/redecentralize/alternative-internet

## Reading List

Ad Hoc Networks
- Samsung. A mesh network for mobile devices using Bluetooth low energy https://www.researchgate.net/publication/281393663_A_Mesh_Network_for_Mobile_Devices_using_Bluetooth_Low_Energy
- Noise – A chat app for the end of the world. https://github.com/aarmea/noise
  - Adapting epidemic routing for commodity phones in adversarial conditions
- Epidemic Routing for Partially-Connected Ad Hoc Networks. http://issg.cs.duke.edu/epidemic/epidemic.pdf
- Experimentation with MANETs of Smartphones. 2017. https://arxiv.org/pdf/1702.04249.pdf
- A Multilayer Application for Multi-hop messaging on Android devices. http://anrg.usc.edu/ee579_2012/Group02/index.html
- Content-centric Routing in Wi-Fi Direct Multi-group Networks. https://arxiv.org/pdf/1412.0880.pdf
- A Mobile Ad Hoc Network Implementation for Android Smartphones. https://pdfs.semanticscholar.org/50d0/bc5e0e1f69db4c0999d4f79cad01edee434d.pdf
- RightMesh. https://www.rightmesh.io/docs/RightMesh_TWP5.pdf
- https://inthemesh.com/archive/whitepaper-connectivity-of-mesh-networks/
- https://www.eecs.yorku.ca/course_archive/2006-07/F/6590/Misc/jin-final-thesis.pdf
- Android Wireless Issues. http://thaliproject.org/androidWirelessIssues/
- Android BLE Issues. https://github.com/iDevicesInc/SweetBlue/wiki/Android-BLE-Issues
- Profile-Based Ad Hoc Social Networking Using Wi-Fi Direct on the Top of Android. https://www.hindawi.com/journals/misy/2018/9469536/
- Enabling always on service discovery: Wi-Fi Neighbor Awareness Networking (NAN. https://pdfs.semanticscholar.org/e481/45d691155d32db54c840f46b4b0ec28151d6.pdf
- Creating Bluetooth sockets on Android without pairing. https://albertarmea.com/post/bt-auto-connect/
- Trustchain: Native Android implementation. https://github.com/Tribler/tribler/issues/3105

Social Networks
- When Social Networks Meet D2D Communications: A Survey. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6359220/
- A gossip-based distributed social networking system. https://pure.tue.nl/ws/portalfiles/portal/3524712/Metis255949.pdf
- Brewster Kahle. Locking the Web Open: A Call for a Decentralized Web. http://brewster.kahle.org/2015/08/11/locking-the-web-open-a-call-for-a-distributed-web-2/
- Jonathan Warren. Bitmessage: A Peer‐to‐Peer Message Authentication and Delivery System. https://bitmessage.org/bitmessage.pdf
- Scuttlebutt Protocol Guide. https://ssbc.github.io/scuttlebutt-protocol-guide/
- https://secushare.org/
- https://gnunet.org/en/index.html

Streaming
- QUIC
  - http://devsisters.github.io/goquic/
  - https://eng.uber.com/employing-quic-protocol/
  - https://cloudflare-quic.com/
- Spotify – Large Scale, Low Latency, P2P Music-on-Demand Streaming. http://dator8.info/pdf/csc/8.pdf
- Peer-to-Peer Streaming Peer Protocol (PPSPP). https://tools.ietf.org/html/rfc7574

TODO:
- compare range of Bluetooth (~10 m) vs WiFi (~60 m), battery consumption
- explore possibility of multiplatform communication