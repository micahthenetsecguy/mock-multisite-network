# Mock-Global-Multisite-Network-Design

## Project Overview (essentially the TLdr)
This repository contains the logical design multi-site corporate network infrastructure. The architecture simulates a corporate Headquarters (HQ) and a remote Branch office connected via a simulated WAN boundary.

## Branches (locations that I service in real-life)
Austin, Texas (where I live) - HQ
New York - Branch
London - Branch
Hyderabad - Branch
Seoul - Branch

## Let's talk about the components that I used and my reasoning (apologies, it is a lot):

**Cisco ISR 4321 Edge Routers**: To me these routers work for branch offices. Of course, this selection is pretty dependent on the traffic <br><br>
**Cisco ISR 4431**: I was going to use the 4321 routers for all offices, but after doing some research, I realized that they would choke as the spine for the network. They only max out around 50 to 100 Mbps, which is totally fine for a single branch office with a few users, but if I tried to force all four international offices in New York, London, Hyderabad, and Seoul to tunnel back into one at the Austin HQ, it would become a massive bottleneck. Plus, once I start adding the zone-based firewall rules, NAT configurations, and all the OSPF routing processes onto them, the CPU would just lock up. So, to keep it realistic, I decided to upgrade the Austin HQ routers to the ISR 4431 model so the core actually has enough bandwidth to handle the global traffic.<br><br>
**Cisco Catalyst 3650-24PS Multi-Layer Switches**: I decided to use these because (in this instance) layer 3 switches are superior to layer 2 switches. They have built-in "brains" that allow me to handle all the traffic moving between my internal VLANs right on the switches at lightning speed. It also lets me run HSRP, which is just a fancy way of saying that if one core switch dies, the other one instantly takes over without users losing internet. It just adds some redundancy to ease the minds of the plant/site/office etc.

## Resources I used:
 
https://www.skendric.com/seminar/

## 60-Day Build Timeline
(last edited July 5th 2026)<br>
This is how I structured the build. I could have done it quicker but I wanted to do my best work and kinda take my time (because there is not time limit or deadline)

### Week 1: Layer 2 Infrastructure & STP Optimization
**Day 1: Topology Mapping & Physical Placement**
  - Mapped out physical devices and connections in Cisco Packet Tracer.
  - Establish redundancy throughout the core to prevent downtime in the event a cable gets unplugged, ports fail, cables break etc.
  - The infrastrucure is free from SPOF to maintain uptime.
