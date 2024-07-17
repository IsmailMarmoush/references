# Security

## Introductions

* https://www.digitalocean.com/community/tutorials/7-security-measures-to-protect-your-servers

## Knowledge highlights

* CIA - Confidentiality, Integrity, Availability
    * Confidentiality
        * Encryption
        * MFA
    * Integrity
        * Ensure while storage, processing, transit
        * Types: Physical and logical
    * Availability
        * Ensure authorized users have access to their data
        * Non-Malicious (hardware & network failure, software downtime)
        * Malicious e.g (D)DOS
* Confidential Information
    * PII
    * CCI Company confidential information
        * Information to run a company
        * E.g IP, designs, procedures, plans
    * Customer confidential information
        * Information supplied by customer or partner
        * E.g PII, CreditCard, purchase history
    * PHI Protected health information
        * Personal medical records
        * PII, Medical history, prescription list
* PII, PCI, SPI
    * PCI includes PII
    * SPI (Sensitive personal information) information that might not be identifiable but could cause harm if made
      public
* Data -> Information -> Insights
* HIPA health insurance portability and accountability act
* GDPR general data protection regulation
* Digital Rights Management, or DRM, is code added directly to files that helps prevent digital assets from being copied
  or pirated, but some tools can remove DRM code.
* The Digital Millennium Copyright Act, or DMCA, makes it illegal to bypass copy protections or to develop technology
  that helps bypass copy protections.
* Data threats
    * Data leaks (accidental exposure through sec vulnerability)
    * Data breach (Intentional data leak)
    * Data dump (dump data in dark web for monetary gain)
    * Dumpster diving of companies literal trash to find any data
* Software Threats
    * Theft (unauthorized copy)
    * Exploits (usage of vulnerabilities to get into system)
    * Malware
* Malware types
    * Program Viruses (bits of code insert themselves into another program)
    * Macro viruses (affect microsoft office files via macros they use to automate tasks)
    * Stealth viruses (copy themselves to avoid scans)
    * Polymorphic viruses 97% of malware (change their characteristics to get around cyber sec defenses)
    * Worms are viruses that start themselves after identifying system weakneses
    * Spyware collects data, credentials, records aud/vid
    * Adware: software coded in online ads which records personal data, website visits
    * Ransomware
* Threat types
    * Snooping
        * Eavesdropping (packet sniffing)
        * MIM (form of eavesdropping)
            * Physical (public wifi, honeypot wifi)
            * Logical (fake links, maleware infected websites)
        * Replay (form of MIM)
            * Uses token
        * XSS
            * Types:
                * Reflected: (common) link with malicious code in legitimate url
                * Persistent: (not as common) malicious code embedded in unvalidated comments
            * Prevention
                * Validate input
                * Sanitize data
                * Set cookie rules
                * WAF, web application firewall
        * SQLi
            * How
                * `Username'` then syntax error
            * Parameterize queries
            * Store procedures
            * Use an allowlist
            * escape user input
        * Botnets
            * large collection of compromised malware infected computers
        * DOS
            * Buffer overflow
                * more traffic than expected
            * ICMP
                * Diagnostic pings sent to every computer on network to cause network crash
            * Syn flood
                * Rapid series of incomplete connection requests until server crashes
        * DDOS uses botnet
        * Phishing
            * WIFI impersonation aka Evil twin
        * Social engineering
            * Relies on
                * Sense of fear or urgency
                * Human error
            * Types:
                * Shoulder surfing
                    * Sit in strategic view to see credentials or put usb stick
                    * In Cafes, public places,
                * Baiting
                    * Uses physical lure, e.g leaving usb stick on floor
                    * Logical lure: online ad, or free.
                * Pretexting
                    * Attacker pretends to be someone with authority
                * Phishing
                    * Attacker send email or text to create sense of emergency
                    * Bank account was compromised use this link to reset
                    * Spear phishing: target specific individual
                    * Whaling: high level execs
                    * Vishing: over the phone
        * Identity theft: stealing personal info
        * Identify fraud: using stolen identity to commit fraud
* Password cracking
    * Brute force submit as many passwords as possible
    * Dictionary attack use words pulled from dictionaries or newspapers
    * Rainbow attacks use words from an original password hash
* AAA
    * Access control
    * Authentication
    * Authorization
* Accounting
    * Logs
    * Tracking
    * Cookies
    * Browsing history
* Non-repudiation
    * When you can't deny being in a specific location
    * Video, biometrics, signature, receipt
* Default passwords:
    * Disable built-in accounts
    * change all default passwords
    * Use strong passwords
    * Check documentation for default, backdoor and hidden accounts
* Firewalls
    * Stateful inspection, also known as dynamic filtering, monitors the state of active network connections. It relies
      on patterns to analyze and monitor traffic for potential threats.
    * A proxy firewall serves as a go-between for the requesting system and the internet. Information is first sent to
      the proxy service before it is forwarded to its destination.
* VPN
    * Site to site VPN
    * Host to site VPN
    * Host to host VPN
* IPsec (Internet protocol security)
    * IPsec suite protocols:
        * Authentication header (AH)
        * Encapsulating security payload (ESP)
            * Encrypts data, authenticates data and senders
    * Tunnel mode (common in site to site VPN)
    * Transport mode (common in host to site vpn)
    * IPsec suites:
        * Security association: which types of hashing and ecnryption used
        * Internet key exchange: secure exchange of cryptographic keys
        * Anti-replay protection (network standard to stop hackers from reusing data)

## Tools

* File Integrity Monitoring (FIM)

## Security Architect

* Business Context diagrams provide a high-level line of business view. They show the relationship between different
  entities in a system.
* System Context diagrams decompose the business context diagram further to determine how the entities might look in a
  system.
* Architecture Overview diagrams decompose the system context diagrams to determine how the smallest components will
  look and connect with other components.
* LifeCycle: Risk Analysis -> Policy -> Arch -> Impl -> Admin -> Audit&Assess

### NIST/Cybersecurity Framework: Identify -> Protect -> Detect -> Respond -> Recover

[NIST Cyber framework](https://www.nist.gov/cyberframework/getting-started/quick-start-guide)

**Identify**
The identify function focuses on understanding the organization's assets, business environment, risk management
strategy, and governance structure. This involves identifying all critical assets and data, assessing the
potential impact of a cyber-attack on these assets, and determining the organization's risk tolerance level.

This function also includes developing incident response plans, establishing policies and procedures for managing
cybersecurity risks, and conducting regular assessments to identify any changes in the organization's risk profile.

**Protect**
The protect function involves implementing measures to safeguard the organization's assets and ensure their continued
availability, integrity, and confidentiality. This includes physical security controls, access controls, data at rest
and in transit protection, employee training programs, and vulnerability management processes.

This function also focuses on supply chain risk management by ensuring that third-party vendors and partners have
appropriate security measures to protect the organization's data and assets.

**Detect**
The detect function focuses on identifying cybersecurity events and incidents as they occur. This includes implementing
monitoring systems, establishing threat intelligence capabilities, and conducting routine assessments of the
organization's security posture.

Quickly detecting and responding to cyber-attacks is essential in minimizing their impact on an organization's
operations and reputation. Therefore, this function also includes developing incident response plans and conducting
regular exercises to test their effectiveness.

**Respond**
The respond function focuses on taking appropriate action in response to a cybersecurity event or incident. This may
involve containment of the incident, eradicating the threat, and recovering impacted systems or data. It also includes
notifying relevant stakeholders, such as customers or regulatory authorities, and implementing additional security
measures to prevent similar incidents from occurring in the future.

**Recover**
The final function, recover, focuses on restoring operational capabilities and services after a cybersecurity event or
incident has occurred. This includes conducting post-incident reviews, implementing changes to policies and procedures,
and updating risk management strategies based on lessons learned.

### PAM

Priviliged access management

Admin, Authn, Authz, audit(UBA, UEBA user entity behavioral analytics)

### Endpoint security

* Inventory - HW/SW (what we have)
* Security policy (latest versions for x software)
* Patching
* Encryption
* Remote wipe
* Location tracking
* Antivirus
* Disposal of devices

### BYOD (bring your own device)

* Consent - monitor, usage, wipe
* Software - version, required apps, prohibited apps
* Hardware - types of desktops/laptops (e.g mac)
* Servicees - Auth

### Network security

* Firewalls
* Segmentation
* VPN
* SASE

#### Firwall

* Packet filter
* Stateful pkt inspection
* Proxy
* NET Addr translation (NAT)

#### Segmentation

Demilitarized Zone (DMZ)
The DMZ typically hosts systems that provide services to users in external networks such as the Internet. These include
Web Servers, which deliver web pages to users who request them via browsers. An Email Server might also be in the DMZ to
manage incoming and outgoing mail. Furthermore, a DNS Server, which translates domain names into IP addresses, can be
found in the DMZ to aid in resolving external requests. Additionally, FTP Servers for file transfers and VPN Servers for
remote network access are often placed in the DMZ. By isolating these servers in the DMZ, organizations seek to limit
potential damage from external threats, as these are the systems that primarily interact with the internet and are thus
more exposed.

#### VPN

|                 |           |   |
|-----------------|-----------|---|
| 1. APP          | SSH       |   |
| 2. Presentation |           |   |
| 3. Session      |           |   |
| 4. Transport    | TLS/SSL   |   |
| 5. Network      | IPSEC     |   |
| 6. Data link    | PPTP/L2TP |   |
| 7. Physical     |           |   |

Moving from Broad based, to app based vpn

#### SASE Secure Access Service Edge

Netsec = Firewall, Secure GW, DLP (data loss prevention)
WAN = Software defined wan
Cloud = Scale + elastic + agile
ID = Authn + Authz

### App Security

* Owasp coding practices checklist
* Owasp top 10 mistakes

### Security testing

* SAST (static application security testing): whilte box, source code
    * https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/stable-en/
* DAST (Dynamic application security testing): blackbox, running app

### Threat Modeling

Threat modeling is a systematic process used in secure coding that involves identifying, understanding, and addressing
potential security threats in a software system. It is generally performed at the early stages of development and
throughout the software life cycle:

The process starts by creating a detailed overview of the system — mapping out the data flow, identifying potential
vulnerabilities, and defining key areas that threats could target.
The next step is identifying and categorizing potential threats using STRIDE (Spoofing, Tampering, Repudiation,
Information Disclosure, Denial of Service, and Elevation of Privilege).
Each threat is then analyzed to understand its potential impact and likelihood of occurrence.
Appropriate mitigation strategies are then designed and implemented to address each identified threat.
Regular reviews and updates are carried out as the system evolves and new threats emerge.
Threat modeling allows for proactive identification and mitigation of potential security risks. It helps prioritize
security measures based on the severity and likelihood of threats, significantly reducing the risk of security breaches.

### Data security ecosystem

* Governance plan to analyze what should be done. It needs a data security policy to identify the key and sensitive
  areas:
  Classification criteria to identify key issues and label them (confidential, unclassified, top secret, and so on)
  Catalog to locate the data, especially the sensitive information
  Resilience plan to plan for recovery in case of data breach
* Discovery to find sensitive data
  Databases that contain structured data
  Files, emails, and spreadsheets that contain unstructured data
* Protection of data
  Encryption that requires data scrambling (for data in databases or in the network)
  Managing the keys and creating them at random
  Access control, which is a part of identity and access management
  Backup to cope with a disaster recovery scenario
* Complying with industry regulations
  Looking for general protection guiding bodies (GDPR Europe and HIPAA US)
  Reporting when non-complying with these bodies
  Retaining records in accordance with the law
* Security comprises detection
  Monitor the systems and analyze how data is used and by whom
  UBA (User Behavior Analytics) to monitor users and how they perceive data
  Alerts that go to consoles and seek immediate action
* Response to security breach
  Investigating cases
  Dynamic playbook for situation handling
  Automation and Orchestration of the cases
* Data Loss Protection (DLP) is a technology that helps to discover the data issues that are flowing across networks.

### Five areas that can remove the cost of data breach:

Artificial intelligence
DevSecOps
Incident Response (IR)
Cryptography
Employee training

### S = P+D+R (prevention, detection, response)

Detection

* Monitor
* Analyze
* Report
* Hunt

SIEM(security and information event management system)

* Came from Logging or Network
* data collected into DB top level

XDR (extended detection and response)

* It came from Endpoint detection and response
* Federated search on the low level

* Collect,
* Correlate,
* Rules policies (if _ & _ then )
* Anomalies (UBA)
* Trends (reports)

Reconnaissance: The attacker will spend time figuring out what your weak points or vulnerabilities are

Mean Time to Identify (MTTI): Time for the organization to identify that there has been an attack. That is in the order
of 200 days.

Mean Time to Contain (MTTC): This is the time taken to fix and recover after the attack is identified.

It is important to detect an attack as soon as possible. This is done with threat hunting.

Threat hunting is a proactive initiative for an organization. This is where a cybersecurity analyst with experience and
a good instinct can help with a hypothesis based on which we can determine the tools to detect threats or possible
attacks, which results in early detection.

SOAR Security orchestration automation and response system
Dynamic playbook ( A tree of flexible actions)

### SANS Incident Response Scenario

Let's consider a hypothetical scenario where an e-commerce company identifies a sudden and unexpected downtime of its
website. Under the SANS Incident Response Framework, the company will follow these steps:

Step 1: Preparation
The organization had established an incident response team with clear roles and responsibilities. They had also set up a
system for logging and monitoring web traffic to detect anomalies.

Step 2: Identification
The company's monitoring systems alerted the IT department about the website's sudden downtime. Upon further
investigation, they discovered a Distributed Denial of Service (DDoS) attack was the cause of the disruption.

Step 3: Containment
The IT team immediately implemented its DDoS mitigation strategy, which involved rerouting traffic through a network of
global servers to distribute the load. The affected server was temporarily taken offline to prevent further damage.

Step 4: Eradication
While traffic was being rerouted, the team worked on eradicating the cause of the attack, blocking the offending IP
addresses, and patching any vulnerabilities that may have been exploited during the attack.

Step 5: Recovery
The affected server was returned online after neutralizing the threat. A comprehensive review was made to ensure the
website's functionality and security were restored before resuming normal operations.

Step 6: Lessons Learned
Post-incident, the company conducted a thorough analysis to understand how the attack happened. They used these insights
to improve their security measures. Employees were provided additional training on cybersecurity best practices, and an
enhanced DDoS mitigation strategy was developed to prevent future attacks.

### Security roles

* Information security and assurance
    * Security policies
    * User access controls
    * Conducting regular audits
    * Ensuring compliance with policies
* Security operations
    * Maintaining and monitoring security infrastructure
    * Carrying out incident response activities
    * Collaborating with other IT teams to manage security incidents effectively
* Cryptography
    * Cryptographic attacks
    * Algorithms
    * Public key infrastructure
* Risk management
    * Threat assessment
    * Risk assessment
    * Risk analysis
* Threat management
    * Threat actors and attributes
    * Threat investigation, detection, and response
    * Indicators of compromise
* Vulnerability management
    * Penetration testing
    * Vulnerability assessment
    * Vulnerability scanning
* Authentication
    * Identity and access management controls
    * Identity and access services
    * Account management
* Digital forensics
    * Chain of custody
    * Data acquisition
    * Data recovery and preservation 