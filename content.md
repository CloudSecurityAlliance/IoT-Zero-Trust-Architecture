Introduction
This paper recommends an approach for adapting zero-trust (ZT) principles to Internet of Things (IoT) devices. This includes a recommended device security profile and a recommended set of network services that can be used to enable ZT at the edge. Suggested requirements are identified within this document to support tailoring of the recommended approach within organizations.  
Scope
Edge devices that interface with enterprise networks and cloud systems are within scope for this edge ZT approach. Many types of edge devices can take advantage of this approach. Some examples include medical devices, smart meters, robotics and industrial control devices. 
Intended Audience
Developers of edge/ IoT devices, system integrators and network architects may find this information useful. 
Zero Trust Concepts
ZT is a security model that requires strict verification of anything and everyone interacting with the network. This model assumes that any device or user requesting access to the network or cloud is a threat (Haughey, C). ZT is realized as a framework of technologies, policies and processes. 
ZT Principles
The National Security Agency (NSA) released “Embracing a Zero Trust Security Model”. This document identifies three core ZT principles that apply to both users and devices. These principles include: 
Never Trust, Always Verify
Assume Breach
Verify Explicitly
ZT Principles should be applied to edge devices. Devices communication with the network should be authorized per transaction. Device security posture should also be verified explicitly and continuously with action taken to restrict authorizations for a device that is potentially compromised or known vulnerable. 
ZT Edge Data Flows
ZT edge architecture requires that devices first authenticate to a network / resource using single packet authorization. Once authenticated and authorized, the appropriate IP-address/port is opened to allow data flow. 

The ability to open the correct port for an IP-address is policy driven. Organizations must have an understanding of the allowable communications/data flows within their systems in order to support this. 
ZTE 1: Map transactions flows to and from devices, applications and users in order to create associated ZTE authorization policy. 
Single Packet Authorization
For Zero Trust, authentication and authorization is  a must to ensure the security of the network. However, the unique characteristics of IoT networks result in an urgent need for simple and reliable authorization/authentication methods. 
The single packet will be the first thing sent to the network, and it will contain sequences for verification and request details, including access port, traffic information. If the network receives anything else, it could consider it as a possible attack. Also, once the single packet is verified, the authentication is completed, and the specific port will be open to the IP address which sent the single packet. This firewall and security policies will be configured, and a connection via traditional network protocols can be established. After a connection is established, all configuration is removed, and the port/service is hidden from all other devices. Without a  single packet, all services and ports are hidden to devices outside of the network. Furthermore, since the network does not respond to the single packet sender, it can mitigate DDOS attacks as all traffic is ignored and filtered before the single packet is verified and authenticated. Single packet authentication is based on RFC 4226, which is an HMAC based one-time password algorithm.
ZTE 2: Perform Single Packet Authorization (SPA) for all device communications with the network
ZTE 3: Upon successful SPA transaction from a device, open the applicable IP-address/port combination to allow device communication into the network. 
ZT Policy Management and Enforcement
One of the primary requirements for a ZTA implementation is that authentication occurs for each transaction. 

                                      
Figure ?? - Onboarding (IdP Scenario)
ZTE 4: Integrate Authorization Infrastructure with ZT capabilities to support SPA. 
Software Defined Networking for ZTE
Software-Defined Networking (SDN) is a networking approach that decouples hardware from the logical data and control planes. This allows for dynamic reconfiguration of data flows and routes within the network. SDN is an enabling technology for IoT ZTA. SDN controllers are used for network policy and application distribution. These controllers can be integrated with network security tools to automate responses to threats , and vulnerability data. Automation can take the form of policy updates, and re-routing traffic within the data plane. 
SDN is preferred because automation of policy reconfiguration can be achieved. When integrated with various capabilities such as threat intelligence and vulnerability management, this provides a powerful feature that results in constant evaluation of the trust profile of a device and removal of a device’s ability to authenticate to the network when needed, in an efficient manner. 
An example use case associated with dynamic policy reconfiguration using SDN is the identification of an edge device that is vulnerable to a newly identified threat. The device for example may include an embedded library with a newly discovered vulnerability. The SDN can then automatically quarantine the device by rerouting traffic to a honeypot for example. Alternatively, the device can be blacklisted and not able to successfully authenticate to the network anymore. 
Network Micro-Segmentation
Unlike traditional networks, under the Zero Trust principles, the network should be separated into segments. This could be done based on several different categorizing methods such as functionalities, features, tasks, departments, etc... Also, physical/software gateways should be implemented between segments. This would increase the difficulties for adversaries to infect the entire network even if there are breaches and vulnerabilities in various small segments. Through micro-segmentation, policy designers and security engineers can easily control, identify, and minimize destructions caused by breaches and adversaries. Micro-Segmentation should leverage a unique network subnetting schema for blast radius control and data planes should be deployed in these schemas based on the tagging.
ZTE 5: Establish architecture/plan for network micro-segmentation based on applicable categories to your organization. 
Least Privilege Access
For a group of users (assets, nodes, devices, etc.), the privilege or level of accessibility is determined by the lowest privilege among the users defined in the same group. This group could be defined within micro-segmentation or labels that combine assets, devices, and users on the network. Least privilege can minimize the risk of vulnerabilities to assets, devices, or users that have low privilege, which may be affected by the  security measures they’ve taken, the strength of firewalls, and frequency of communication with untrusted users.  A better analogy would be the barrel effect, in which the shortest wood strip determines the capacity of a barrel. Similarly, to take the safest approach, we can assume the asset, device, or user with the least privilege is either the easiest to be compromised or has  the greatest attack surface for adversaries.
ZTE 6: Define and enforce least-privilege restrictions on all device and user interactions and data flows. 
Asset Visibility and Management
Asset Visibility is a crucial part of achieving Zero Trust as we want to make sure devices connected to our network are authorized. Ensuring that we know information regarding the assets, devices, and users connected will provide us with guidelines that can be set to protect the network. 
ZTE 7: Encourage device manufacturers to provide software/ hardware bill of materials (SBOM/HBOM) with products to determine if new vulnerabilities affect product libraries. 
Device Monitoring
Logging and information sharing are critical to securing a zero-trust  network. This is because the network is segmented into various parts, so communication and cooperation between departments and teams are  crucial to secure the network. Furthermore, it is important for different parts of the network to know and understand breaches and vulnerabilities within the network, so immediate patches and updates can be done to prevent further damage done by the adversary. Furthermore, logging allows us to track deeper into the abnormal behaviors caused by attacks or possible infections. This could be used as a reference to reinforce our security policies and can be considered when designing new security policies and parameters. 
Monitoring can detect abnormal behaviors, and allocate extra resources to investigate abnormal behaviors. Also, continuous monitoring can provide evidence and trace for attacks, and can be used as a source to identify and prevent future attacks. Furthermore, the logged (monitored) information should be shared across the network. This could help remove attacks detected by other departments and lower the risks of unidentified attacks. Through the exchange of information, we can also rearrange security policy design and remedy tasks to agents who are connected to that network segment.
ZTE 8: Implement robust security monitoring capabilities for devices that connect to the network.


 Trusted Device Onboarding
The device onboarding process is one of the most critical processes for a successful IoT ZTA implementation. Device credentials must be securely generated and managed. These credentials represent the identity of the device. Without assurances that the identity of a device cannot be easily forged, the rest of the processes in place within the ZTA framework cannot be assured. Trusted device onboarding assumes that the IoT device is  developed with a strong cryptographic root of trust (RoT). The RoT securely stores the cryptographic keys and trust anchors for the device and performs several additional security functions, as detailed in this paper. 

ZTE 9: Implement and enforce a trusted device onboarding process to provision credentials to edge devices after procurement. 

