# Practical Case Studies

This folder connects the network-defense concepts in these course notes to practical projects I have completed. Each case study explains what was built, which security concepts it demonstrates, and what has and has not been verified.

These are educational simulations and personal portfolio projects, not production deployments or professional experience.

## Case Studies

| Case Study | Focus | Tools |
|---|---|---|
| [Bank Secure Network](Bank-Secure-Network.md) | VLAN segmentation, router-on-a-stick inter-VLAN routing, and ACL-based restrictions in a simulated bank network | Cisco Packet Tracer |

## Bank Secure Network at a Glance

A segmented banking network with four VLANs (ADMIN, EMPLOYEE, ATM and SERVER) routed through one Cisco 2911 router. Two ACLs restrict Employee and ATM traffic toward the Admin network (and ATM traffic toward the Employee network).

| Area | Status |
|---|---|
| VLAN segmentation and router-on-a-stick routing | Implemented |
| Employee-to-Admin restriction | Verified (blocked ping, deny counter increase) |
| Employee-to-Banking-Server ICMP reachability | Verified (ICMP only) |
| ATM restrictions | Configured, not independently verified |
| DHCP, DNS, HTTP/HTTPS and FTP end to end | Not verified |

The ACLs end with `permit ip any any`, so they block only the specific flows they list. See the case study for details and limitations.

## Full Project

For the complete Cisco Packet Tracer implementation, network configuration, ACL documentation and available test evidence, visit the [Bank Secure Network repository](https://github.com/andyydz/bank-secure-network).
