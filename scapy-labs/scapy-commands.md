# Scapy Practical Lab – Commands, Steps, Observations & Results

=====================================================================
1. Command: sudo su
=====================================================================

Step:
- Switched to root user.

Purpose:
- Needed to sniff and send packets.

Observation:
- Terminal changed to root (#).

Results:
- Root access granted.

---------------------------------------------------------------------

=====================================================================
2. Command: scapy
=====================================================================

Step:
- Launched Scapy shell.

Purpose:
- Provides packet crafting environment.

Observation:
- Scapy banner displayed.

Results:
  Example:
    >>> 

Screenshot Reference:
- /scapy-labs/screenshots/01-scapy-start.png

---------------------------------------------------------------------

=====================================================================
3. Command: ls
=====================================================================

Step:
- Listed Scapy layers and functions.

Purpose:
- Shows available protocol layers.

Observation:
- Long list displayed (IP, TCP, UDP, ARP, ICMP…).

Results:
  Example:
    IP     TCP     UDP     ICMP     ARP ...

---------------------------------------------------------------------

=====================================================================
4. Command: ls(IP)
=====================================================================

Step:
- Listed fields of IP layer.

Purpose:
- Shows attributes like ttl, src, dst.

Results:
    version    : BitField  (4 bits)                  = ('4')
    ihl        : BitField  (4 bits)                  = ('None')
    tos        : XByteField                          = ('0')
    len        : ShortField                          = ('None')
    id         : ShortField                          = ('1')
    flags      : FlagsField                          = ('<Flag 0 ()>')
    frag       : BitField  (13 bits)                 = ('0')
---------------------------------------------------------------------

=====================================================================
5. Command: sniff()
=====================================================================

Step:
- Captured packets on default interface.

Purpose:
- Observe real-time network traffic.

Observation:
- Packets captured until Ctrl+C.

Results:
- Sniffed: TCP:0 UDP:6 ICMP:10 Other:5


Screenshot:
- /scapy-labs/screenshots/02-sniff.png

---------------------------------------------------------------------

=====================================================================
6. Command: ping -c 5 www.cisco.com
=====================================================================

Step:
- Generated ICMP traffic.

Purpose:
- Provides data for sniffing.

Results:
- 5 packets transmitted, 5 received, 0% packet loss, time 4009ms.

Screenshot:
- /scapy-labs/screenshots/ping-scan.png

---------------------------------------------------------------------

=====================================================================
7. Commands: a = _, a.summary()
=====================================================================

Step:
- Stored last Scapy output into variable a.

Purpose:
- Allows further analysis.
- Shows one-line description of each packet

Results:
- “a” now contains packet list.
- ICMP 10.0.2.15 > 2.17.168.94 echo-request.

Screenshot:
- /scapy-labs/screenshots/captured-traffic.png

---------------------------------------------------------------------

=====================================================================
8. Commands:ifconfig, sniff(iface="eth0"), a=_, a.summary()
=====================================================================

Step:
- Sniffed packets on eth0 interface.


Purpose:
- The ifconfig command shows network interfaces such as eth0.
- The sniff(iface="eth0") command monitors the  specific network interface.
- The a=_ command stores last Scapy output into variable a.
- The a.summary() command shows one-line description of each packet captured.

Observation:
- Packet list created.

Results:
- Sniffed: TCP:3878 UDP:130 ICMP:0 Other:7>

Screenshot:
- /scapy-labs/screenshots/03-sniffed-packets.png

---------------------------------------------------------------------

====================================================================
9. Command: sniff(iface="eth0", filter="icmp", count=10)
====================================================================

Purpose:
- Capture only ICMP packets.

Results:
- Sniffed: TCP:0 UDP:0 ICMP:0 Other:0

Screenshot:
- /scapy-labs/screenshots/04-icmp-packets.png

---------------------------------------------------------------------

=====================================================================
10. Command: ping -c 10 10.6.6.23
=====================================================================

Purpose:
- Generate traffic for ICMP sniff.

Output:
- 10 packets transmitted, 10 received, 0% packet loss, time 9596ms

Screenshot:
- /scapy-labs/screenshots/collected-packets.png

---------------------------------------------------------------------

=====================================================================
11. Command: wrpcap("capture1.pcap", a)
=====================================================================

Purpose:
- Save packets to pcap file.

Expected Result:
- File created: capture1.pcap

---------------------------------------------------------------------

=====================================================================
12. Command: send(IP(dst="10.0.2.15")/ICMP()/"This is a test")
=====================================================================

Step:
- Sent custom ICMP packet.

Purpose:
- Test packet crafting.

Result:
- Sent 1 packets.

Screenshot:
- /scapy-labs/screenshots/05-custom-icmp-packet.png

---------------------------------------------------------------------

=====================================================================
13. Command: a.nsummary()
=====================================================================

Purpose:
- Numbered summary of packets.

Output:
    0000 Ether / IP / TCP 10.0.2.15:33522 > 34.36.137.203:https PA / Raw
    0001 Ether / IP / TCP 10.0.2.15:33522 > 34.36.137.203:https FPA / Raw
    0002 Ether / IP / TCP 34.36.137.203:https > 10.0.2.15:33522 A / Padding

Screenshot:
- /scapy-labs/screenshots/summary-packets.png

---------------------------------------------------------------------

=====================================================================
14. Command: send(IP(dst="10.6.6.23")/TCP(dport=445, flags="S"))
=====================================================================

Step:
- Sent SYN packet to port 445.

Purpose:
- Test SMB port for activity.

Result:
- Sent 1 packets.

Screenshot:
- /scapy-labs/screenshots/06-syn-packet-capture.png

---------------------------------------------------------------------

# End of Scapy Labs Documentation
