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
