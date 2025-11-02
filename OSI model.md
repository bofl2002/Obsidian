[[Teknologi]]

**

## [OSI & TCP/IP models](https://study-ccna.com/osi-tcp-ip-models/)

Begge modeller beskriver, hvordan data transmitteres gennem netværk, men med forskellige tilgange:

OSI-modellen (7 lag) – Open Systems interconnection (Reference Model)

Lag 7 - Applikationslaget (Application Layer) - Netværks applikationer (Chrome &Google)

- Netværkstjenester til applikationer
    
- Protocols: HTTP, FTP, SMTP, DNS...
    

Lag 6 - Præsentationslaget (Presentation Layer) - Translation, data compression, encryption/decryption)

- Datakryptering, komprimering, formatering)
    
- Formater: SSL/TLS, JPEG, ASCII, MPEG...
    
- Compression og kryptering
    

Lag 5 - Sessionslaget (Session Layer) - APIs, Netbios, Authenticating/Authorisation, session management

- Etablerer og administrerer forbindelser mellem sender og modtager.
    
- Synkronisering af sessioner via sequence numbers
    
- Protocols: NetBIOS, SOCKS, NFS (network file system), RPC
    

Lag 4 - Transportlaget (Transport Layer) - Segmentation, flow control, error control

- Pålidelig dataoverførsel, fejlkontrol
    
- Transportprotokol: TCP, UDP
    
- Fra packets til segments
    
- Process separation via port numre
    
-   
    

Lag 3 - Netværkslaget (Network Layer)

- Routing og logiske adresser
    
- Eksempler: IPV4/IPV6, ICMP, IPsec, OSPF
    

Lag 2 - Datalinklaget (Data Link Layer) - Media access control

- Frame-dannelse, fejlregistrering
    
- Eksempler: Ethernet, Wi-Fi, PPP (Point to Point Protocol)
    
- Fysisk adresse: MAC adresser
    
- Flow control (Synchronizing Sending and receiving af frames)
    
- Protokoller: Ethernet, frame-relay, token ring, FDDI (Fiber distributed data interface)
    
- Devices: Brigdes, Layer 2 switches
    

Lag 1 - Det fysiske lag (Physical Layer)

- Fysisk transmission af bits (Frames)
    
- Eksempler: Kabler, radiofrekvenser, lysdioder
    
- Typer af kommunikation (Simplex (oneway), Halfduplex (two way,  kun en vej ad gangen), Fullduplex (two way på same tid)
    
- Devices på fysisk lag: Hubs, Netværkskort, repeaters
    

TCP/IP-modellen (4 lag) – TCP Transmission Control Protocol (Implementation model)

Lag 4 - Applikationslaget

- Kombinerer OSI lag 5, 6 og 7
    
- HTTP, FTP, SMTP, DNS
    

Lag 3 - Transportlaget

- TCP (pålidelig) og UDP (hurtig)
    
- Portnumre, fejlkontrol
    

Lag 2 - Internet Laget

- IP-adressering og routing
    
- IPv4, IPv6, ICMP
    

Lag 1 - Netværksadgangslaget

- Kombinerer OSI lag 1 og 2
    
- Ethernet, Wi-Fi, fysiske forbindelser
    

Sammenligning

OSI-modellen:

- Teoretisk referencemodel
    
- Mere detaljeret (7 lag)
    
- Udviklet af ISO
    
- Bruges til undervisning og forståelse
    

TCP/IP-modellen:

- Praktisk implementering
    
- Enklere (4 lag)
    
- Grundlag for internettet
    
- Udviklet af DARPA/US Department of Defense
    

Hukommelsesstøtte (OSI): "All People Seem To Need Data Processing" (Application, Presentation, Session, Transport, Network, Data Link, Physical)

**

# PDU (Protocol Data Unit) i OSI-modellen

**PDU** står for **Protocol Data Unit** og refererer til den dataenhed, der overføres mellem lag i OSI-modellen. Hver PDU har et specifikt navn afhængigt af hvilket lag den befinder sig på.

## PDU'er på de forskellige lag:

|**OSI-lag**|**PDU-navn**|**Beskrivelse**|
|---|---|---|
|**7. Application**|Data|Rå applikationsdata|
|**6. Presentation**|Data|Formateret/krypteret data|
|**5. Session**|Data|Data med sessionsstyring|
|**4. Transport**|**Segment** (TCP) eller **Datagram** (UDP)|Data opdelt i segmenter med port-info|
|**3. Network**|**Packet**|Segment med IP-adresser tilføjet|
|**2. Data Link**|**Frame**|Packet med MAC-adresser og error-checking|
|**1. Physical**|**Bits**|Rå binær data (0'er og 1'er)|

## Hvordan det fungerer:

**Encapsulation (nedadgående):** Når data sendes ned gennem lagene, tilføjer hvert lag sin egen header (og nogle gange trailer) til PDU'en:

- Application/Presentation/Session → **Data**
- Transport tilføjer header → **Segment/Datagram**
- Network tilføjer header → **Packet**
- Data Link tilføjer header og trailer → **Frame**
- Physical konverterer til → **Bits**

**Decapsulation (opadgående):** Når data modtages, fjerner hvert lag sin header og sender dataen op til næste lag.

## Vigtigt at huske:

- **Segment/Datagram** = Transport lag (lag 4)
- **Packet** = Network lag (lag 3)
- **Frame** = Data Link lag (lag 2)
- **Bits** = Physical lag (lag 1)