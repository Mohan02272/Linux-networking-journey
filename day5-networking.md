## Network Security

# Table of Contents
Introduction to Network Security
Objectives of Network Security
CIA Triad
Types of Cyber Attacks
Malware Attacks
Phishing Attacks
Denial of Service Attacks
Man-in-the-Middle Attacks
Password Attacks
Spoofing Attacks
Sniffing and Packet Capture
SQL Injection
Social Engineering
VPN Concepts
VPN Protocols
Encryption Basics
Symmetric Encryption
Asymmetric Encryption
Hashing
Digital Signatures
SSL/TLS
Authentication Concepts


# Introduction to Network Security

Network Security is the process of protecting computer networks, devices, systems, applications, and data from unauthorized access, attacks, damage, or theft.

Modern organizations heavily depend on network infrastructure for:

Communication
Cloud computing
Databases
Business operations
Financial transactions
Remote work
Web applications

Without proper security, attackers can:

Steal sensitive information
Disrupt services
Damage systems
Encrypt files using ransomware
Gain unauthorized access

Network security is one of the most important areas in:

System Administration
DevOps
Cloud Engineering
Ethical Hacking
Cybersecurity
2. Objectives of Network Security

The main objectives are:

Protect systems
Protect data
Prevent unauthorized access
Detect attacks
Maintain service availability
Ensure secure communication
3. CIA Triad

The CIA Triad is the foundation of information security.

Component	Meaning
Confidentiality	Prevent unauthorized access to data
Integrity	Prevent unauthorized modification
Availability	Ensure systems remain accessible
Confidentiality

Confidentiality ensures only authorized users can access information.

Examples:

Banking credentials
Medical records
Company secrets

Protection methods:

Encryption
VPN
Authentication
Access control
Integrity

Integrity ensures data is not modified illegally.

Examples:

Financial transaction data
Database records
Configuration files

Protection methods:

Hashing
Checksums
Digital signatures
Availability

Availability ensures services remain operational.

Threats:

DDoS attacks
Hardware failure
Ransomware
Power outages

Protection methods:

Redundancy
Load balancing
Backup systems
Firewalls
4. Types of Cyber Attacks

Cyber attacks target networks, applications, systems, or users.

Major Attack Categories
Attack Type	Purpose
Malware	Damage systems or steal data
Phishing	Steal credentials
DoS/DDoS	Disrupt services
MITM	Intercept communication
Password attacks	Crack passwords
Spoofing	Fake identities
Sniffing	Capture traffic
SQL Injection	Attack databases
Social Engineering	Manipulate humans
5. Malware Attacks

Malware means malicious software.

Its purpose is to:

Damage systems
Spy on users
Steal data
Encrypt files
Create backdoors
Types of Malware
Malware	Description
Virus	Infects files and programs
Worm	Self-replicating malware
Trojan	Fake legitimate software
Spyware	Steals information secretly
Ransomware	Encrypts files for ransom
Rootkit	Hides attacker presence
Virus

A virus attaches itself to files or programs.

Characteristics:

Requires user action
Spreads through infected files
Damages systems
Worm

A worm spreads automatically through networks.

Characteristics:

Self-replicating
Fast spreading
No user interaction needed

Trojan

A Trojan disguises itself as legitimate software.

Example:

Fake cracked software
Fake software installers
Ransomware

Ransomware encrypts user files and demands payment.

Effects:

File loss
Business disruption
Financial damage

Protection:

Regular backups
Updates
Email security
Endpoint protection
6. Phishing Attacks

Phishing tricks users into revealing sensitive information.

Targets:

Passwords
OTPs
Credit card details
Banking information
Types of Phishing
Type	Description
Email phishing	Fake emails
Spear phishing	Targeted attacks
Whaling	Targets executives
Smishing	SMS phishing
Vishing	Voice phishing
Prevention
Verify URLs carefully
Avoid suspicious attachments
Use MFA
Conduct security awareness training
7. Denial of Service Attacks

A DoS attack attempts to make services unavailable.

DoS Attack

Single attacker floods a system with requests.

DDoS Attack

Multiple systems attack simultaneously.

Usually uses botnets.

Effects:

Server overload
Website downtime
Service interruption

Protection:

Firewalls
Load balancers
CDN services
Rate limiting
8. Man-in-the-Middle Attacks

In a MITM attack, the attacker intercepts communication between two parties.

Example

User ↔ Attacker ↔ Website

The attacker can:

Read traffic
Modify data
Steal credentials
Protection
HTTPS
VPN
Encryption
Certificate validation
9. Password Attacks

Attackers try to obtain passwords using different methods.

Brute Force Attack

Attempts every possible password combination.

Dictionary Attack

Uses common password lists.

Credential Stuffing

Uses leaked passwords from other websites.

Protection
Strong passwords
MFA
Password managers
Account lockout policies
10. Spoofing Attacks

Spoofing means pretending to be another device or user.

Types of Spoofing
Type	Description
IP Spoofing	Fake IP address
MAC Spoofing	Fake MAC address
DNS Spoofing	Fake DNS response
Email Spoofing	Fake email sender
11. Sniffing and Packet Capture

Sniffing means capturing network traffic.

Passive Sniffing

Only monitors traffic.

Active Sniffing

Manipulates traffic while capturing.

Protection
Encryption
VPN
HTTPS
Switched networks
12. SQL Injection

SQL Injection targets databases through vulnerable web applications.

Example

Unsafe SQL query:

SELECT * FROM users WHERE username='admin';

Attackers inject malicious SQL code.

Effects
Database theft
Data modification
Administrative access
Prevention
Parameterized queries
Input validation
Web Application Firewall (WAF)
13. Social Engineering

Social engineering manipulates humans instead of systems.

Examples:

Fake technical support
Urgent scam calls
Fake login pages

Humans are often the weakest security layer.

14. VPN Concepts

VPN stands for Virtual Private Network.

A VPN creates an encrypted tunnel between a user and a remote network.

VPN Goals
Goal	Purpose
Privacy	Hide internet activity
Encryption	Secure communication
Remote Access	Secure company access
Security	Protect data over public networks
How VPN Works
User connects to VPN server
Authentication occurs
Encrypted tunnel is established
Data travels securely
15. VPN Protocols
Protocol	Description
PPTP	Old and insecure
L2TP/IPsec	Better security
OpenVPN	Secure and popular
WireGuard	Modern and fast
IPsec	Enterprise standard
OpenVPN

Features:

SSL/TLS based
Cross-platform
Highly secure
WireGuard

Features:

Lightweight
High performance
Modern cryptography
16. Encryption Basics

Encryption converts readable data into unreadable form.

Terms
Term	Meaning
Plaintext	Original readable data
Ciphertext	Encrypted data
Key	Secret used for encryption
Encryption Process

Plaintext + Key → Ciphertext

Decryption Process

Ciphertext + Key → Plaintext

17. Symmetric Encryption

Uses the same key for encryption and decryption.

Advantages
Fast
Efficient
Disadvantages
Key sharing problem
Algorithms
Algorithm	Status
AES	Modern standard
DES	Old and insecure
3DES	Improved DES
AES

Advanced Encryption Standard is widely used in:

VPNs
HTTPS
Banking systems
Wi-Fi security
18. Asymmetric Encryption

Uses two keys.

Key	Purpose
Public Key	Encryption
Private Key	Decryption
Advantages
Secure key exchange
Supports digital signatures
Disadvantages
Slower than symmetric encryption
Algorithms
Algorithm	Usage
RSA	Common
ECC	Modern efficient encryption
DSA	Digital signatures
19. Hashing

Hashing is a one-way mathematical process.

Unlike encryption, hashing cannot be reversed.

Characteristics
One-way
Fixed output size
Used for integrity verification
Common Hash Algorithms
Algorithm	Status
MD5	Broken
SHA1	Weak
SHA256	Secure
Password Storage

Passwords should be hashed, not encrypted.

20. Digital Signatures

Digital signatures ensure:

Authenticity
Integrity
Non-repudiation
Process
Sender hashes data
Hash encrypted using private key
Receiver verifies using public key
Usage
HTTPS certificates
Software signing
Secure email
21. SSL/TLS

TLS secures internet communication.

Used in:

HTTPS
APIs
Email security
VPNs
HTTPS

HTTPS = HTTP + TLS

Provides encrypted web communication.

TLS Handshake

During handshake:

Client connects
Certificate exchanged
Keys generated
Secure session established
22. Authentication Concepts

Authentication verifies user identity.

Example:

Username and password
Fingerprint
OTP
