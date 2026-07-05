# Mock-Global-Multisite-Network-Design

## Project Overview (essentially the TLdr)
This repository contains the logical design multi-site corporate network infrastructure. The architecture simulates a corporate Headquarters (HQ) and a remote Branch office connected via a simulated WAN boundary.

## Let's talk about the components that I used:

I went with a pretty standard setup for this lab. I made this a global build because I work globally for my current job. 

**Cisco 3560 Multi-Layer Switches (Core)**: I decided to use these because (in this instance) layer 3 switches are superior to layer 2 switches. They have built-in "brains" that allow me to handle all the traffic moving between my internal VLANs right on the switches at lightning speed. It also lets me run HSRP, which is just a fancy way of saying that if one core switch dies, the other one instantly takes over without users losing internet. It just adds some redundancy to ease the minds of the plant/site/office etc. <br><br>
**Cisco 2911 Router (Edge)**:  Since the 3560 switches are doing all the heavy lifting for the internal traffic, this router can just sit at the door and do edge work. I use it strictly to talk to the branch office via OSPF, translate internal IPs to the internet using NAT, and block bad traffic using ACL security rules.<br><br>
**Cisco 2911 Router (Branch Edge)**: The one is just the gatekeeper for the remote office. It handles the local branch users and routes their traffic back to Headquarters over the WAN link.

## Resources I used:
 
https://www.skendric.com/seminar/

## 30-Day Build Timeline
(last edited July 5th 2026)<br>
This is how I structured the build. I could have done it quicker but I wanted to do my best work and kinda take my time (because there is not time limit or deadline)

### Week 1: Layer 2 Infrastructure & STP Optimization
**Day 1: Topology Mapping & Physical Placement**
  - Mapped out physical devices and connections in Cisco Packet Tracer.
  - Establish redundancy throughout the core to prevent downtime in the event a cable gets unplugged, ports fail, cables break etc.
  - The infrastrucure is free from SPOF to maintain uptime.
