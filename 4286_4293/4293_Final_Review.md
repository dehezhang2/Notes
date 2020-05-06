# CS4293 Final Review

## Question

* In chapter 7, TCP connection Spoofing, why it cannot be prevent by IPSec?
* In chapter 7, what is the difference between the Bot net and normal DDoS

## Chapter 7: Network Protocol Security and Defenses

### Networks: IP and TCP

* IP
  * Vulnerability: IP and TCP headers are not protected well, easy to override using raw packets
    * No encryption and for confidentiality (Eavesdropping)
    * No source authentication (spoof source address)
    * No integrity checking ( content forgeries, redirections, and man-in-the-middle
      attacks)
    * No bandwidth constraints (DoS)
  * Countermeasure: IPSec (AH (integrity) , ESP (integrity + confidentiality) headers), Tunnel Mode
* TCP
  * Vulnerability:
    * packets pass by untrusted hosts => eavesdropping. packet sniffing 
    * TCP state can be easy to guess  (guess the sequence number)
      * Attack: After victim setting up a TCP connection with server, an attacker pretends to be the victim by changing the IP address of his packet
    * DoS vulnerabilities: DDoS
      * Attacker can send Reset packet to close connection
      * TCP allows a large window of sequence number, which makes it easier to guess the sequence number
    * Optimistic ACK Attack
      * Takes advantage of the TCP congestion control
      * It begins with a client sending out ACKs for data segments it hasn’t yet received
      * makes the servers TCP stack believe that there is a large amount of bandwidth available and thus increase cwnd
      * This leads to the attacker providing more optimistic ACKs, and eventually bandwidth use beyond what the server has available
      * This can also be played out across multiple servers, with enough congestion that a certain section of the network is no longer reachable
      * no practical solutions to this problem
  * Countermeasure: 
    * SSL protocol => packet sniffing (confidentiality)
    * Random initial TCP sequence numbers (should be unpredictable) => TCP states and DoS

### Routing Vulnerabilities

* ARP (address resolution protocol): IP address => ethernet address
  - Used to find the physical connected neighbors in the network
* OSPF: used for routing **within** an anonymous system (e.g. CityU network)
* BGP: routing between the anonymous systems
  * Protocol
    * Different router learns information from each other
  * Vulnerability: BGP packets are un-authenticated
    - Attacker cause entire Internet to send traffic for a victim IP to attacker’s address => DoS
    - In the interdomain routing, one point failure will be populated to all the network
  * Countermeasure: S-BGP (raise the bar of fake advertisement)
    - **IPsec**: secure point-to-point router communication
    - **PKI**: authorization frame for all S-BGP entities
    - Attestations: **digitally-signed** authorizations
      - Address: authorization to advertise specified address blocks
      - Route: Validation of UPDATEs based on a new path attribute, using PKI certificates and attestations

### Domain Name System

* DNS query:
  * Protocol
    * Client send request to local DNS resolver (e.g. CityU resolver), and local DNS resolver sends query to the higher level resolver
    * Sometimes, DNS responses and negative queries(nonexistent sites e.g. misspelling) are cached for a quicker response. The data cached also has TTL(time to live)
  * Packet: application level protocol using UDP/IP
    * UDP header, IP header
    * DNS header including query ID (16 bit random value, link response to query)
  * Vulnerability: No protocol widely used to protect DNS request packet
    * Interception of requests or compromise of DNS server can result in incorrect or malicious response 
    * DNS poison attack
      * Attacker can keep sending (guessing the QID) bad mapping from domain name and IP address to a local DNS resolver. It will get a probability to success.
  * Countermeasure: 
    * authenticated requests/responses => provided by DNSsec ... but few use
      * Provides origin authentication and integrity
      * New Resource Records, PKI
    * Increase Query ID size: 
      * randomize src port, add another 11 bits to guess => turn to several hours to attack
      * ask every query twice => raise the bar for attack, but DNS system cannot handle the load

### DoS and DDoS

* Definition: A transient or persistent set of actions by a third party preventing authorized users from access to or use of a resource or service => need not be launched by malicious third party, for malicious party it is called DoS **attack**
* Mode of attack
  * Consumption of resources
    * types
      * Network connectivity
      * bandwidth consumption
    * Vulnerability (Effort Amplification(放大)): Once your it takes less effort for attacker than the server for a message, it is vulnerable to DoS attack. e.g.:
      - ping of death => attacker construct data frames that appear to be fragments of the same application layer data. The sum of the sizes of the data frames is greater than the limit, which will cause buffer overflow. 
      - Smurf Attack: Send request to gateway with echo function and set the echo back IP address to victim’s address
      - TCP SYN Flooding: Server allocate memory for the coming TCP handshake. Attacker send the request that spoofing the clients, server save the request state and run out of resource.  
  * Disruption or deletion of configuration information
    * An improperly configured computer may not perform well or may not operate at all
    * Vulnerability: An intruder may be able to alter or destroy configuration information that prevents you from using your computer or network (BGP example)
  * Disruption of physical resources
    * cutting cables, power cuts for wired network
    * physical jammers for wireless network (exist for a number of frequencies and protocols)
* Countermeasure
  * Monitoring
  * Right limiting: don’t want to many request from the same user
* DDoS: use multiple attackers on a network
  * Master program installed on one computer, which communicates to a number of agent programs installed on compromised computers. Agents initiate attack simultaneously
  * Can be injected to legitimate softwares and uploaded to network
* Bot Networks
  * Infection Mechanisms: web download, mail attachments, scan/exploit
  * Command and Control (C&C): Centralized, P2P, unstructured
  * Communication Protocols: IRC, HTTP, P2P, proprietary
  * Payload/Actions: Spam, DDoS, Keyloggers, Clickfraud
  * Counter measure: 
    * Building one could be a one man job
    * Easier to disable than to destroy (the attacked system can solve the problem but cannot destroy the bot net)