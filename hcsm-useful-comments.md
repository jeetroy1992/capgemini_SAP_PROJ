# ServiceNow Ticket Comment Templates - GCID Network HEC Data


---

## Template 1: Initial Ticket Acknowledgment & Information Gathering

**Title:** Initial Ticket Acknowledgment & Information Gathering

**Description:** Use this when first reviewing a new ticket to acknowledge receipt and request necessary information for troubleshooting.

**Comment:**

```java
Hello Team,

Thank you for submitting this request. We have received your ticket and our team is currently reviewing the details.

To ensure we can provide you with the most efficient resolution, could you please provide the following information:

• Source IP: (Client/Local machine IP from where you are accessing the service)
• Destination IP: (Target service/SAP HANA instance you are trying to reach)
• Destination Port:
• Connection Type: (VPN/MPLS/Cloud Peering)
• Connection Status: (Not working at all/Slow/Intermittent issues)
• Was this connection working previously? If yes, when was the last successful connection?
• System Type (Production/Non-Production):
• Data Center/Location: (Ex. HEC01-ROT)
• Ping, traceroute & telnet results if any (Please include .pcap or .pcapng file if available)

This information will help us perform a thorough analysis and expedite the resolution process.

Thank you for your cooperation.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 2: Missing Pre-Shared Key Information

**Title:** Request for Missing Pre-Shared Key (PSK)

**Description:** Use when PSK is missing from the VPN tunnel configuration request.

**Comment:**

```java
Hello Team,

We are currently reviewing your VPN tunnel configuration request. However, we have identified that the Pre-Shared Key (PSK) information is missing from the submitted details.

To proceed with the VPN tunnel setup, please provide:

• Pre-Shared Key (PSK) - Required for authentication
• Confirm PSK matches on both ends (Customer side and SAP side)
• If this is a new tunnel, please provide a secure PSK meeting complexity requirements (minimum 20 characters, alphanumeric with special characters recommended)

Please note: For security purposes, we recommend sharing the PSK through a secure channel or encrypted method.

Once we receive this information, we will proceed with the configuration immediately.

Thank you for your prompt attention to this matter.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 3: Downtime Request for Policy-Based VPN Changes

**Title:** Downtime Window Request - Policy-Based VPN Modification

**Description:** Use when changes to policy-based VPN will cause connectivity disruption (encryption domain, peer IP, etc.).

**Comment:**

```java
Hello Team,

We have reviewed your request for modification to the VPN configuration (Addition/Removal/Modification of encryption subnet/host/Peer IP/BGP ASN).

Important Note: During this configuration change, there will be a temporary connectivity loss as this is a policy-based VPN tunnel.

To minimize business impact, please provide TWO preferred downtime windows (1-2 hours each) between Monday to Friday when we can perform this activity:

Downtime Window 1:
• Start Time: YYYY-MM-DD HH:MM:SS [Timezone]
• Estimated End: YYYY-MM-DD HH:MM:SS [Timezone]

Downtime Window 2:
• Start Time: YYYY-MM-DD HH:MM:SS [Timezone]
• Estimated End: YYYY-MM-DD HH:MM:SS [Timezone]

Please ensure the timezone is clearly specified (e.g., UTC, EST, CET) and use 24-hour format.

We will coordinate with you to confirm the final maintenance window once we receive your response.

Thank you for your cooperation.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 4: Downtime Request for Route-Based VPN Changes (not applicable for HEC01/HEC02)

**Title:** Downtime Window Request - Route-Based VPN Modification

**Description:** Use for route-based VPN changes where connectivity loss is minimal but downtime window is still recommended.

**Comment:**

```java
Hello Team,

We have reviewed your request for modification to the IKEv2 Route-Based VPN tunnel configuration.

We note that you currently have a route-based VPN with [Peer IP] and have requested changes to the encryption subnets.

Technical Note: Since this is a route-based VPN, the addition/removal of encryption subnets typically should not cause connectivity loss. However, as a best practice and to ensure zero business impact, we recommend scheduling a brief maintenance window.

Please provide TWO preferred downtime windows (1-2 hours each) between Monday to Friday:

Downtime Window 1:
• Start Time: YYYY-MM-DD HH:MM:SS [Timezone]
• Estimated End: YYYY-MM-DD HH:MM:SS [Timezone]

Downtime Window 2:
• Start Time: YYYY-MM-DD HH:MM:SS [Timezone]
• Estimated End: YYYY-MM-DD HH:MM:SS [Timezone]

Please ensure timezone is clearly specified (e.g., UTC, EST, CET) using 24-hour format.

Thank you for your cooperation.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 5: IKEv1 to IKEv2 Migration Request

**Title:** IKEv1 to IKEv2 VPN Migration - Downtime Required

**Description:** Use when migrating VPN tunnels from IKEv1 to IKEv2 protocol.

**Comment:**

```java
Hello Team,

We have received your request to migrate the existing VPN tunnel from IKEv1 to IKEv2 protocol.

Migration Overview:
• Current Configuration: IKEv1 with [Peer IP]
• Target Configuration: IKEv2 with enhanced security parameters
• Expected Impact: Complete VPN tunnel reconfiguration required

Important: This migration requires complete tunnel reconfiguration and will result in connectivity downtime during the transition.

Please provide the following:

1. TWO preferred maintenance windows (2-3 hours each) between Monday to Friday:
   
   Window 1:
   • Start Time: YYYY-MM-DD HH:MM:SS [Timezone]
   • Estimated End: YYYY-MM-DD HH:MM:SS [Timezone]
   
   Window 2:
   • Start Time: YYYY-MM-DD HH:MM:SS [Timezone]
   • Estimated End: YYYY-MM-DD HH:MM:SS [Timezone]

2. Confirm that customer-side devices support IKEv2 protocol
3. New Pre-Shared Key (recommended for enhanced security)
4. Business justification for the migration

We will coordinate the implementation details once we receive your confirmation.

Thank you.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 6: VPN Peer IP Change Request

**Title:** VPN Peer IP Address Change - Downtime Coordination

**Description:** Use when customer requests to change the VPN tunnel peer IP address.

**Comment:**

```java
Hello Team,

We have reviewed your request to modify the VPN peer IP address.

Current Configuration:
• Existing Peer IP: [Current IP]
• Requested New Peer IP: [New IP]

This change requires complete tunnel reconfiguration and will result in temporary service disruption.

To proceed, please provide:

1. Call Booking Details: (Joint customer call with Customer/Provider's network team)
   Window:
   • Start Time: YYYY-MM-DD HH:MM:SS [Timezone]
   • Estimated End: YYYY-MM-DD HH:MM:SS [Timezone]

2. Confirmation of the new peer IP address
3. Reason for the IP change (ISP change, network redesign, etc.)
4. Confirmation that the new peer IP is reachable from our infrastructure
5. Will the Pre-Shared Key remain the same, or do you require a new PSK?

Once confirmed, we will create a Standard Change Request (SRA) and configuration will be prepared prior to the agreed maintenance window and the Peer IP will be changed during the customer call to avoid possible issues post cutover.

Thank you for your cooperation.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 7: Encryption Domain Modification

**Title:** Encryption Domain/Subnet Modification Request

**Description:** Use when adding, removing, or modifying encryption domains/subnets in VPN configuration.

**Comment:**

```java
Hello Team,

We have received your request to modify the encryption domain for the existing VPN tunnel with peer [Peer IP].

Requested Changes:
• Subnets to Add: [List subnets]
• Subnets to Remove: [List subnets]
• Subnets to Modify: [List subnets]

VPN Type: [Policy-Based / Route-Based]

Impact Assessment:
• Policy-Based VPN: Temporary connectivity loss expected during reconfiguration
• Route-Based VPN: Minimal impact, but maintenance window recommended as best practice

Please provide:

1. Business justification for the subnet changes
2. Confirmation that the new subnets are properly configured on your end
3. TWO preferred maintenance windows (1-2 hours each):
   
   Window 1:
   • Start Time: YYYY-MM-DD HH:MM:SS [Timezone]
   • Estimated End: YYYY-MM-DD HH:MM:SS [Timezone]
   
   Window 2:
   • Start Time: YYYY-MM-DD HH:MM:SS [Timezone]
   • Estimated End: YYYY-MM-DD HH:MM:SS [Timezone]

We will prepare the configuration and coordinate with you for implementation.

Thank you.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 8: Successful Implementation Notification

**Title:** Successful Implementation Completed

**Description:** Use after successfully completing configuration changes with SRA/Change Number.

**Comment:**

```java
Hello Team,

We are pleased to inform you that the implementation has been completed successfully.

Implementation Details:
• SRA Change Number: [CHG#######]
• Implementation Date: [Date and Time]
• Configuration Status: Completed

From SAP side, we have completed the entire configuration as per the request. We suggest you verify all the shared information and complete the configuration at your end accordingly.

Note: As per HEC standards, there are no restrictions at the network layer or OS level for classic HEC or VMware servers - traffic is allowed by default. Restrictions are only applicable on Hyperscale environments through NSG or firewall configurations.

Next Steps:
• Please verify connectivity from your end
• Test all required services and applications
• Confirm successful operation

If you require any changes or additional information, please do NOT reopen this ticket. Instead, please open a new service request with the ECS COE team:
https://sap.sharepoint.com/sites/207904/SitePages/Organization.aspx

Thank you for your patience and cooperation.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 9: VPN Tunnel Status - Confirmed UP and Active

**Title:** VPN Tunnel Status Verification - Active and Operational

**Description:** Use when confirming VPN tunnel is up and operational from network side.

**Comment:**

```java
Hello Team,

We have completed our investigation and verification of the VPN tunnel connectivity.

Status Update:
• VPN Tunnel Status: UP and ACTIVE
• Peer IP: [Peer IP Address]
• All configured encryption subnets: ALLOWED and OPERATIONAL
• Phase 1 (IKE): Established
• Phase 2 (IPSec): Active

Network Analysis:
Upon running debug diagnostics, we observe that packets are being sent successfully from our end to establish and maintain the connection. However, we are not receiving return traffic from your side.

Findings:
• No network-level blocking from SAP infrastructure
• All ports are open as per configuration
• No additional work required from the network team

Recommendation:
The issue appears to be on the customer/application side. We recommend:
• Verify firewall rules on your end
• Check server-level configurations
• Engage your server management team for further investigation
• Verify application-level connectivity

This ticket will remain open for 24 hours for your review. If no additional network-related work is identified, we will close the ticket as no further action is needed from our side.

For server or application-level issues, please engage your respective teams.

Thank you.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 10: Request for Troubleshooting Call

**Title:** Request to Schedule Troubleshooting Call

**Description:** Use when complex issues require live troubleshooting session with customer and vendors.

**Comment:**

```java
Hello Team,

Based on the complexity of the current issue, we recommend scheduling a live troubleshooting call to expedite resolution.

To arrange a troubleshooting session, please schedule a call via the CND portal using the link below:

Portal Links:
• https://sap.sharepoint.com/sites/100553/HECOperations/default.aspx
• https://outlook.office365.com/owa/calendar/testing4@sap.onmicrosoft.com/bookings/?skipRedirect=1

Call Requirements:
Please ensure the following participants are available during the scheduled call:
• Customer Network Team representative
• Device Vendor Specialist/TAC/SME (if applicable)
• SAP Network Operations team (we will join)

Preferred Schedule:
• Monday to Friday (business hours preferred)
• Duration: 1-2 hours
• Please provide your timezone preference

Note: If the booking links are not working or you are unable to book a slot, please contact TSM/PC3/CDM via email at: gcshelp@sap.com for assistance with call scheduling.

During the call, we can perform live diagnostics, configuration verification, and real-time troubleshooting with all stakeholders present.

Please confirm your preferred time slots and we will coordinate accordingly.

Thank you for your cooperation.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 11: Cutover Schedule Request - VPN to Cloud Peering Migration

**Title:** Migration Cutover Schedule - VPN to Cloud Peering

**Description:** Use when planning migration from VPN to cloud peering (Azure/AWS/GCP).

**Comment:**

```java
Hello Team,

We have received your request to migrate from the existing VPN connectivity to Cloud Peering setup.

Migration Overview:
• Current Setup: IPSec VPN Tunnel
• Target Setup: Cloud Peering (Azure ExpressRoute/AWS Direct Connect/GCP Interconnect)
• Migration Type: [Cutover/Parallel Run/Phased]

To ensure a smooth transition with minimal business impact, we need to plan the migration carefully.

Please provide the following information:

1. Preferred Migration Strategy:
   • Complete cutover (VPN to Cloud Peering switch)
   • Parallel run (both active during transition)
   • Phased migration (subnet by subnet)

2. Cutover Windows (please provide THREE options):
   
   Window 1:
   • Date: YYYY-MM-DD
   • Start Time: HH:MM:SS [Timezone]
   • End Time: HH:MM:SS [Timezone]
   
   Window 2:
   • Date: YYYY-MM-DD
   • Start Time: HH:MM:SS [Timezone]
   • End Time: HH:MM:SS [Timezone]
   
   Window 3:
   • Date: YYYY-MM-DD
   • Start Time: HH:MM:SS [Timezone]
   • End Time: HH:MM:SS [Timezone]

3. Cloud Peering Details:
   • Cloud Provider: [Azure/AWS/GCP]
   • Circuit/Connection ID:
   • Bandwidth requirement:
   • Peering Location:

4. Rollback Plan:
   • In case of issues, should we keep VPN active as fallback?
   • Rollback decision criteria?

5. Business Justification and approval for the migration

We will prepare a detailed migration plan once we receive this information.

Thank you.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 12: No Customer Response - Pending Closure

**Title:** Pending Ticket Closure - Awaiting Customer Response

**Description:** Use when no response received from customer and ticket is pending closure.

**Comment:**

```java
Hello Team,

We have not received any response or update from your end regarding this ticket.

Previous Request Summary:
• Initial contact date: [Date]
• Information requested: [Brief summary]
• Last follow-up: [Date]
• Current status: Awaiting customer response

As we have not heard back from you and there are no reported issues from your end, we will proceed to close this ticket within the next 48 hours.

Important Notes:
• If you require any changes or additional information, please do NOT reopen this ticket
• For new requests, modifications, or additional information, please open a new service request with the ECS COE team

New Service Request Portal:
https://sap.sharepoint.com/sites/207904/SitePages/Organization.aspx

If you have any urgent concerns regarding this ticket, please respond immediately to prevent automatic closure.

Thank you for your understanding.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 13: Ticket Closure - No Further Action Required

**Title:** Ticket Resolution and Closure

**Description:** Use when closing ticket after successful resolution or no further action required.

**Comment:**

```java
Hello Team,

Based on our investigation and the current status, we are closing this ticket as resolved/completed.

Resolution Summary:
• Issue/Request: [Brief description]
• Action Taken: [Summary of actions]
• Current Status: [Resolved/Completed/No action required]
• Closure Date: [Date]

There have been no further reports or issues from your end, and all requested work has been completed from the network operations team.

Important Information:
• Please do NOT reopen this ticket for new requests or modifications
• If you require any changes, modifications, or additional information in the future, please open a new service request

New Service Request Portal:
https://sap.sharepoint.com/sites/207904/SitePages/Organization.aspx

If you experience any issues related to this ticket within the next 24 hours, please respond immediately.

Thank you for your cooperation throughout this process.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 14: BGP Configuration Request

**Title:** BGP Configuration and ASN Details Request

**Description:** Use when BGP routing configuration is required for VPN or cloud peering.

**Comment:**

```java
Hello Team,

We have received your request for BGP configuration. To proceed with the setup, we require additional information.

Note: To support high availability and automatic failover/failback, we always configure two independent route-based VPN tunnels. In the SAP private cloud,BGP support is mandatory for redundant vpn.

Current Request Summary:
• Connection Type: [VPN Route-Based/Cloud Peering/MPLS]
• Peer IP: [If applicable]

Required BGP Information:

1. BGP ASN Details:
   • Customer BGP ASN (Private/Public):
   • SAP Side BGP ASN: [Will be provided by SAP]

2. IP Addressing (We need two BGP subnets (/30 preferably) for both primary & secondary EDGE/WAN routers):

BGP subnet1: (Ex: 169.254.1.0/30)
   • BGP Peering IP (Customer side): (Ex: 169.254.1.1)
   • BGP Peering IP (SAP side): (Ex: 169.254.1.2)
BGP subnet2: (Ex: 169.254.2.0/30)
   • BGP Peering IP (Customer side): (Ex: 169.254.2.1)
   • BGP Peering IP (SAP side): (Ex: 169.254.2.2)

3. Route Advertisement:
   • Prefixes to be advertised from customer side:
   • Prefixes expected from SAP side:
   • Any route filtering requirements:

4. BGP Parameters:
   • BGP authentication (MD5) required? If yes, provide password securely
   • Preferred BGP timers (Keepalive/Hold time):
   • Maximum prefix limit:

5. Redundancy:
   • Primary BGP peer:
   • Secondary BGP peer (if applicable):

Please note: During BGP configuration, there may be brief connectivity interruptions. Please provide a preferred maintenance window:
• Date: YYYY-MM-DD
• Time: HH:MM:SS to HH:MM:SS [Timezone]

Once we receive this information, we will proceed with the BGP configuration.

Thank you.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 15: ACL / Firewall Rule Request

**Title:** ACL/Firewall Configuration Request - Hyperscale Environment

**Description:** Use for ACL/firewall rule requests.

**Comment:**

```java
Hello Team,

We have reviewed your request regarding network connectivity in the Hyperscale environment.

Important Information - HEC Network Security Standards:

Customer Connectivity:
  - We only enable routing
  - We do not have any firewalls/ACL in the customer connectivity at network level
  - We do not restrict traffic at port(Ex. TCP 22) or individual IPs (Ex. 10.10.10.10) 
  - No restrictions at network layer or OS level
  - All traffic is allowed by default as long as the network is reachable


For Hyperscale NSG Configuration, please provide:

1. Source Information:
   • Source IP addresses/ranges:
   • Source ports:

2. Destination Information:
   • Destination IP addresses/ranges:
   • Destination ports:
   • Protocol (TCP/UDP/ICMP/Any):

3. Rule Direction:
   • Inbound
   • Outbound
   • Both

4. Priority and Action:
   • Action (Allow/Deny):

5. Business Justification:
   • Purpose of the rule:
   • Applications/Services affected:

Please provide a maintenance window if changes might impact existing connectivity:
• Date: YYYY-MM-DD
• Time: HH:MM:SS to HH:MM:SS [Timezone]

Thank you.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 16: Set Up SAP Cloud Peering Connection

**Title:** Set Up SAP Cloud Peering Connection  

**Delivery Instructions:**  
SAP Cloud Peering is the SAP Cloud Service that connects customers to a specific SAP datacenter using interconnect ecosystem providers without touching the public internet. It is similar to direct connectivity options offered by public cloud providers such as AWS Direct Connect, Azure ExpressRoute, and GCP Interconnect.

**Additional Attributes:**  

- **SAP HEC Datacenter:** HEC01 (ASN 65200)  
- **Interconnect Provider:** Equinix ECX / Megaport MCR
- **SAP Cloud Peering Bandwidth:** 200M  
- **BGP Peering Network 1:** 93.122.121.8/30  
  - **BGP Peering IP SAP Network 1:** 93.122.121.10  
  - **BGP Peering IP Customer Network 1:** 93.122.121.9  
- **BGP Peering Network 2:** 93.122.121.12/30  
  - **BGP Peering IP SAP Network 2:** 93.122.121.14  
  - **BGP Peering IP Customer Network 2:** 93.122.121.13  
- **BGP Peering Customer Side ASN:** 65300  
- **BGP MD5 Secret (optional, recommended):** find-me-if-you-can!
- **Customer ID:** ABC

**Comment:**

```java
Hello Team,

We are initiating the setup for SAP Cloud Peering connectivity as per your request.

Connection Details:
• SAP HEC Datacenter: HEC01 (ASN 65200)
• Interconnect Provider: Equinix ECX
• Bandwidth: 200M

BGP Peering Configuration:
• BGP Peering Network 1: 93.122.121.8/30
  - SAP IP: 93.122.121.10
  - Customer IP: 93.122.121.9
• BGP Peering Network 2: 93.122.121.12/30
  - SAP IP: 93.122.121.14
  - Customer IP: 93.122.121.13
• Customer ASN: 65300
• BGP MD5 Secret: xxxxxx (recommended)

Implementation Schedule:
• Scheduled Start: 09 December 2025 11:05:00 UTC
• Estimated End: 16 December 2025 11:05:00 UTC

Next Steps:
1. Please confirm all provided details and readiness on your side.
2. Ensure your interconnect provider (Equinix ECX) is prepared for the scheduled implementation.
3. Confirm BGP configuration and MD5 secret on your equipment.
4. Provide any additional requirements or changes before the scheduled start.

Once confirmed, we will coordinate with all parties and proceed with the implementation.

Thank you.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 17: Cloud Peering Configuration Request

**Title:** Cloud Peering Setup Request (ExpressRoute/Direct Connect/Interconnect)

**Description:** Use for Azure ExpressRoute, AWS Direct Connect, or GCP Interconnect setup.

**Comment:**

```java
Hello Team,

We have received your request for Cloud Peering connectivity setup.

Cloud Provider: [Azure/AWS/GCP]
Peering Type: [Azure ExpressRoute/AWS Direct Connect/GCP Cloud Interconnect]

To proceed with the configuration, please provide the following information:

1. Cloud Connection Details:
   • Circuit/Connection ID:
   • Service Key/Authorization Key:
   • Peering Location:
   • Bandwidth:

2. For Azure ExpressRoute:
   • Subscription ID:
   • Resource Group:
   • ExpressRoute Circuit Name:
   • Service Key:
   • Private Peering ASN:
   • Microsoft Peering ASN (if required):
   • VLAN ID for Private Peering:

3. For AWS Direct Connect:
   • AWS Account ID:
   • Direct Connect ID:
   • BGP ASN:
   • Virtual Interface ID:
   • VLAN ID:
   • BGP Authentication Key (if required):

4. For GCP Cloud Interconnect:
   • GCP Project ID:
   • Interconnect Attachment Name:
   • Cloud Router Name:
   • BGP Peer ASN:
   • VLAN Attachment ID:

5. IP Addressing:
   • Primary link - Customer side IP:
   • Primary link - SAP side IP:
   • Secondary link - Customer side IP (if applicable):
   • Secondary link - SAP side IP (if applicable):
   • Subnet mask:

6. Route Advertisement:
   • Prefixes to be advertised to SAP:
   • Expected prefixes from SAP side:

7. Implementation Window:
   Please provide preferred implementation date and time:
   • Date: YYYY-MM-DD
   • Time: HH:MM:SS to HH:MM:SS [Timezone]

Please ensure all prerequisites are completed on the cloud provider side before the scheduled implementation.

Thank you.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 18: Connectivity Troubleshooting - Debug Results

**Title:** Connectivity Troubleshooting - Debug Analysis Results

**Description:** Use when providing debug analysis results for connectivity issues.

**Comment:**

```java
Hello Team,

We have completed comprehensive debugging and analysis of the reported connectivity issue.

Issue Summary:
• Reported Issue: [Brief description]
• Affected Connection: [VPN/MPLS/Cloud Peering]
• Source: [IP/Subnet]
• Destination: [IP/Subnet/Service]

Debug Analysis Results:

1. VPN Tunnel Status:
   • Phase 1 (IKE): [UP/DOWN]
   • Phase 2 (IPSec): [UP/DOWN]
   • Encryption Status: [Active/Inactive]
   • Last Status Change: [Date and Time]

2. Traffic Flow Analysis:
   • Outbound packets from SAP: [Being sent/Not sent]
   • Inbound return traffic: [Received/Not received]
   • Packet loss percentage: [X%]
   • Latency: [X ms]

3. Configuration Verification:
   • Encryption domains: [Correctly configured/Mismatch detected]
   • Routing: [Proper routes in place/Route missing]
   • ACLs/Firewall rules: [Configured correctly/Issues found]

4. Debug Output Summary:
   We observe that packets are being sent from our infrastructure attempting to establish/maintain the connection. However, we are not seeing return traffic from your end.

Findings:
• Network layer: No blocking from SAP infrastructure
• All required ports: Open and accessible
• VPN tunnel: [Status]
• All configured subnets: Allowed in encryption domain

Conclusion:
From the network connectivity perspective, all configurations are correct and active. The issue appears to be:
• [Application-level configuration]
• [Server-side firewall rules]
• [Customer-side network configuration]
• [Other - specify]

Recommendations:
1. Verify firewall rules on your end allow the required traffic
2. Check server/application level configurations
3. Engage server management team for OS-level investigation
4. Verify that the service/application is running and listening on the specified port

Next Steps:
This ticket will remain open for 24 hours for your review and testing. If no additional network-related work is identified from our side, the ticket will be closed.

For server or application-level issues, please engage your respective support teams.

Thank you.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 19: Escalation to Vendor TAC/SME

**Title:** Escalation Request - Vendor TAC/SME Engagement Required

**Description:** Use when issue requires vendor TAC or subject matter expert involvement.

**Comment:**

```java
Hello Team,

Based on our detailed analysis and troubleshooting efforts, we have determined that this issue requires specialized expertise from the device vendor's Technical Assistance Center (TAC) or Subject Matter Expert (SME).

Issue Summary:
• Problem Description: [Detailed description]
• Affected Device/Service: [Device model/Service]
• Severity: [P1/P2/P3/P4]
• Business Impact: [Description]

Troubleshooting Performed:
1. [Action taken 1]
2. [Action taken 2]
3. [Action taken 3]
4. [Additional diagnostics performed]

Current Status:
• Configuration: Verified and correct
• Connectivity: [Status]
• Logs/Debugs: Available and indicate [findings]

Reason for Escalation:
[Specific technical reason requiring vendor involvement - e.g., potential software bug, advanced feature configuration, hardware issue, etc.]

Required Actions:

1. Please engage your Device Vendor Specialist/TAC/SME with the following information:
   • Device make and model:
   • Software/firmware version:
   • Issue description and symptoms:
   • Configuration files (sanitized):
   • Debug outputs/logs:

2. We recommend scheduling a joint troubleshooting call via the CND portal:
   • https://sap.sharepoint.com/sites/100553/HECOperations/default.aspx
   
   Required participants:
   • Customer Network Team
   • Device Vendor TAC/SME
   • SAP Network Operations Team

3. Please provide your preferred time for the joint troubleshooting session:
   • Date: YYYY-MM-DD
   • Time: HH:MM:SS to HH:MM:SS [Timezone]

We will continue to support this issue and work collaboratively with the vendor TAC to reach resolution.

For call scheduling assistance: gcshelp@sap.com

Thank you for your cooperation.

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

---

## Template 20: P1 Incident - Critical Business Impact

**Title:** P1 Critical Incident - Immediate Attention Required

**Description:** Use for Priority 1 incidents with critical business impact requiring immediate response.

**Comment:**

```java
Hello Team,

This ticket has been classified as a Priority 1 (P1) Critical Incident due to significant business impact.

Incident Classification:
• Priority: P1 - Critical
• Impact: [Production down/Complete service outage/Critical business function unavailable]
• Affected Systems: [System/Service details]
• Number of Users Affected: [Estimate]
• Business Impact: [Revenue impact/SLA breach/Critical deadline at risk]

Current Status:
• Incident Start Time: [YYYY-MM-DD HH:MM:SS Timezone]
• Detection Time: [YYYY-MM-DD HH:MM:SS Timezone]
• Current State: [Investigation/Troubleshooting/Escalated]

Immediate Actions Taken:
1. [Action 1]
2. [Action 2]
3. [Action 3]

Our P1 Response:
• Dedicated engineer assigned to this incident
• Continuous monitoring until resolution
• Regular status updates every [30/60] minutes
• Full engagement of SAP Network Operations team

Requirements for Expedited Resolution:

1. Business Justification (Required for P1):
   • Detailed impact statement:
   • Financial/operational consequences:
   • Affected business processes:
   • SLA/contractual obligations at risk:

2. Immediate Availability:
   • Customer technical contact (24/7 reachable):
   • Phone number:
   • Email:
   • Backup contact:

3. For immediate troubleshooting call:
   • We are available NOW for emergency troubleshooting
   • Please contact: [Emergency contact number]
   • Or join scheduled emergency call via CND portal

4. Decision Makers:
   • Please have authorized decision makers available for:
   - Emergency change approvals
   - Rollback decisions
   - Configuration modifications

Additional Support:
• ECS MIM (Major Incident Management) can be engaged if needed
• Vendor TAC emergency support can be requested
• Management escalation available if required

Next Update:
We will provide the next status update within [30/60] minutes or immediately upon any significant development.

This incident has our highest priority and full attention until resolved.

For immediate contact: [Phone number / Emergency contact details]

Best regards,  
[Your Name]  
PlusOne Network Team  
External On behalf of SAP
```

## Template 21: SR Closure Note (Activity Complete)

**Title:** SR Closure Note (Activity Complete)

**Description:** Use for closing the SCTASK after fulfilling the customer request.

**Comment:**

```java
Hi Team,

We are proceeding with the closure of the request as it has already been fulfilled and haven't received any feedback.
Please open a new ticket if you need any further assistance from SAP side.

Thank you for your support!!

Best regards
<Name>
PlusOne Network Team
External On behalf of SAP
```

## Template 22: VPN: PBVPN to RBVPN Conversion - Request for Customer Call & Downtime

**Title:** Policy-based to Route-based VPN Conversion - Request for Customer Call & Downtime

**Description:** Used for PBVPN to RBVPN customer call request

**Comment:**

```
Hello Team,

To proceed with the migration from 1x Policy-Based VPN to 2x Route-Based VPN with BGP tunnels, we kindly request you to schedule a call via the CND booking portal using the link below:

Portal Link:
   • https://sap.sharepoint.com/sites/100553/HECOperations/default.aspx
   • https://outlook.office365.com/owa/calendar/testing4@sap.onmicrosoft.com/bookings/?skipRedirect=1

Call Requirements:

Please ensure the following participants are available during the scheduled session:
   • Customer or Provider Network Team
   • SAP Network Operations Team (we will join the call)

Preferred Schedule:

   • Monday to Friday (business hours preferred)
   • Duration: 1–2 hours

Note: If the booking link is not working or you are unable to reserve a slot, please reach out to your SAP ECS representatives (TSM/PC3/CDM) or contact us via email at gcshelp@sap.com
for assistance with scheduling.

During the call, we will:
   • Perform the migration from Policy-Based to Route-Based VPN
   • Establish BGP tunnels
   • Shift the traffic from old to new VPN tunnels
   • Conduct end-to-end testing
   • Provide real-time troubleshooting in case of any issues

Kindly confirm your preferred time slot, and we will coordinate accordingly.

Thank you for your cooperation.

Best regards,
[Your Name]
PlusOne Network Team
External – On behalf of SAP
```
---

## Template 23: No Action Required | Requesting for Ticket Redirection

**Title:** No Action Required - Requesting OSD for Ticket Redirection

**Description:** Requesting OSD for Ticket Redirection

**Comment:**

```
Hello Team,

Thank you for sharing the details.

Based on our checks, we can see that one port is already open, while the others to the same destination from the HEC servers are not.
From our analysis, this does not appear to be a network-level issue, as there are no firewalls or ACLs configured on the SAP side that would block this traffic.

@OSD Team – Could you please route this ticket to the MCD SM team, as we do not observe any issue from the SAP HEC network perspective.

Please let us know if you have any questions. Thank you for your cooperation!!

Best regards
[Your Name]
PlusOne Network Team
External – On behalf of SAP
```
---

**End of Templates**

*Note: Remember to customize these templates with actual values, names, contact information, and specific details relevant to each ticket. Always review and adjust the tone and content based on the specific customer relationship and situation.*

*Note: 

Hello Team

BGP cannot be established over a Policy‑based VPN/Multi-SA VTI and mixing policy‑based on one side with Route‑Based+BGP on the other will not meet the redundancy design we’re targeting in the same HEC datacenter.

We cannot build two separate VPN tunnels with the same subnet/traffic selectors within the same SAP HEC datacenter.
To achieve dual tunnels/HA without selector conflicts, HEC requires IKEv2 route‑based with BGP with two endpoints on both sides.
BGP requires a route‑based (VTI/tunnel‑interface) construct. A policy‑based/Multi-SA VTI peer will not bring up BGP adjacencies reliably.

To proceed with a primary/secondary design within the same HEC DC, RNB must change from policy‑based to route‑based with BGP.
We (SAP HEC) can support either policy‑based or route‑based (static/BGP) on our side, but dual tunnels with identical selectors in the same DC is only achievable with route‑based+BGP on both ends.

:::::::::::::::::::::::::::::::::::::::::::::Alternatives (if RNB cannot move to BGP yet):::::::::::::::::::::::::::::::::::::::::::::

Single policy‑based tunnel only (no secondary in the same HEC DC).
Route‑based on both sides with static routing (no BGP) — still limited by the “no duplicate selectors” rule for two tunnels in the same DC, so you would not get two parallel tunnels for the same prefixes.*


