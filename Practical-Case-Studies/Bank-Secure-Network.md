# Practical Case Study: Bank Secure Network

## 1. Overview

This case study connects the concepts in these course notes to one practical project I completed: the **Bank Secure Network**, a segmented banking network designed and simulated in **Cisco Packet Tracer**.

The scenario is a small bank branch where administrative users, employees, ATMs and core banking servers share one physical network. The project separates them into VLANs, routes between them through a single Cisco 2911 router (router-on-a-stick), and uses ACLs to restrict specific traffic flows.

It is an **educational simulation and personal portfolio project**. It is not a production banking network and does not represent professional experience.

The full implementation is in the original project repository, linked at the end of this case study.

## 2. Security Objectives

A flat network lets every device reach every other device, so one compromised or misconfigured device can expose the rest. The project separates four groups so that each can be controlled independently:

| Network | Why it is separated |
|---|---|
| Admin | Administrative systems are the most sensitive endpoints; access to them from other segments should be restricted. |
| Employee | General staff workstations need access to services but not to administrative systems. |
| ATM | ATMs have different trust and access requirements from staff workstations. |
| Server | Banking and network services are placed in their own segment so they can be reached through a controlled routing point. |

## 3. Network Segmentation

Each VLAN has its own `/24` subnet (mask `255.255.255.0`), with the `.1` address as its default gateway on the router.

| VLAN | Name | Network | Gateway |
|:---:|---|---|---|
| 10 | ADMIN | `192.168.10.0/24` | `192.168.10.1` |
| 20 | EMPLOYEE | `192.168.20.0/24` | `192.168.20.1` |
| 30 | ATM | `192.168.30.0/24` | `192.168.30.1` |
| 40 | SERVER | `192.168.40.0/24` | `192.168.40.1` |

The Server VLAN hosts the Banking Server (`192.168.40.10`) and the DNS/DHCP Server (`192.168.40.20`).

VLANs separate Layer 2 broadcast domains. Traffic between VLANs is routed through the router, so segmentation alone does not block inter-VLAN communication; the router is where that traffic can be filtered.

## 4. Access Control

Two named extended ACLs on the router restrict specific flows. Both are applied **inbound** on the router subinterfaces for their VLANs.

| ACL | Applied on | Intent | Rules |
|---|---|---|---|
| `EMPLOYEE-SECURITY` | `GigabitEthernet0/1.20` (VLAN 20) | Keep Employee devices out of the Admin network | Deny IPv4 from `192.168.20.0/24` to `192.168.10.0/24`, then `permit ip any any` |
| `ATM-SECURITY` | `GigabitEthernet0/1.30` (VLAN 30) | Keep ATMs out of the Admin and Employee networks | Deny IPv4 from `192.168.30.0/24` to `192.168.10.0/24` and to `192.168.20.0/24`, then `permit ip any any` |

Because each ACL ends with `permit ip any any`, they block **only** the listed flows. Other IPv4 traffic from those VLANs, including traffic toward the Server VLAN, is permitted. They are stateless IPv4 packet filters, not a comprehensive security policy.

## 5. Validation and Evidence

This table follows the original project's documented evidence. It separates tested results from configured-only behavior.

| Check | Result | Status |
|---|---|---|
| Employee PC → Admin host `192.168.10.10` (ping) | Failed; four destination-host-unreachable messages from `192.168.20.1`, zero ping replies | **Verified** (blocked as intended) |
| `EMPLOYEE-SECURITY` deny-rule counter | Increased from 4 to 8 during repeated blocked tests | **Verified** |
| Employee PC → Banking Server `192.168.40.10` (ping) | Succeeded with 0% packet loss; confirms ICMP reachability only | **Verified** |
| ATM → Admin and ATM → Employee restrictions | Deny rules are configured; no dedicated connectivity test documented | **Not verified** |
| ATM → Banking Server | Permitted by the final ACL rule; no test documented | **Not verified** |
| DHCP lease assignment, DNS resolution, HTTP/HTTPS and FTP access | Configuration is documented; no end-to-end results documented | **Not verified** |

The inbound assignment of `EMPLOYEE-SECURITY` together with the increasing deny counter supports the conclusion that the Employee-to-Admin restriction worked during the test. A successful ping shows ICMP reachability only; it does not show that the banking web service works.

## 6. Security Lessons

- **VLAN segmentation:** grouping devices by role creates boundaries and separate broadcast domains, but routed traffic still crosses them unless something restricts it.
- **Least privilege (partial):** the ACLs apply least-privilege thinking to specific flows, such as ATMs toward Admin and Employee networks. They are not a full least-privilege policy, because `permit ip any any` allows everything not explicitly denied.
- **ACL enforcement:** rule order and placement matter. The deny rules come before the permit-all rule, and applying the ACLs inbound on the source VLAN's subinterface filters traffic as it enters the router.
- **Controlled connectivity:** all inter-VLAN traffic passes through one routing point, which gives a single place to apply and review access rules.
- **Validation:** a configured rule is not a tested rule. Recording which behaviors were tested, and which were not, keeps the documentation honest and shows where further testing is needed.

## 7. Limitations and Next Steps

**Limitations**

- This is a Cisco Packet Tracer simulation for learning, not a production or regulatory-compliant banking environment.
- ACLs are stateless packet filters. They do not inspect payloads, authenticate users or encrypt traffic.
- Other IPv4 traffic from the Employee and ATM VLANs is permitted by the final rule of each ACL.
- ACL coverage confirmed in the documentation is limited to the Employee and ATM subinterfaces.

**Untested areas and next steps**

- Run dedicated tests for the ATM-to-Admin and ATM-to-Employee deny rules.
- Test ATM-to-Banking-Server connectivity.
- Record end-to-end evidence for DHCP, DNS, HTTP/HTTPS and FTP.
- Replace `permit ip any any` with more granular rules (specific hosts, protocols and ports).
- Add logging of ACL matches and denied traffic.

## 8. Explore the Full Project

For the complete Cisco Packet Tracer implementation, network configuration, ACL documentation and available test evidence, visit the [Bank Secure Network repository](https://github.com/andyydz/bank-secure-network).
