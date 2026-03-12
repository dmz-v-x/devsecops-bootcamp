## Types of Cyber Attacks and How to Protect Against Them

Modern applications, APIs, and infrastructure face many different types of attacks. Attackers exploit weaknesses in authentication, networking, web applications, and third-party dependencies. Understanding these attacks is critical for building secure systems in DevSecOps environments.

This guide explains each attack type from multiple perspectives:

- What the attack is
- How the attack is typically carried out
- How organizations defend against it

---

### 1. Brute Force Attack

A brute force attack is an authentication attack where an attacker attempts to guess credentials by trying many combinations of usernames and passwords until the correct one is found.

These attacks rely on automation and computing power rather than exploiting a specific vulnerability.

#### How Brute Force Attacks Are Carried Out

Attackers typically use automated scripts or tools that repeatedly attempt login requests.

Common approaches include:

Password Guessing  
Attackers attempt common passwords such as:

- password123
- admin
- welcome

Dictionary Attacks  
Attackers use lists of commonly used passwords collected from previous breaches.

Credential Stuffing  
Attackers use username-password combinations leaked from other breaches to try logging into different services.

Automated tools often generate thousands of login attempts per minute.

#### How to Stay Safe from Brute Force Attacks

Several security controls help prevent brute force attacks.

Rate Limiting  
Limit how many login attempts can be made within a time window.

Account Lockout  
Temporarily lock accounts after multiple failed login attempts.

Multi-Factor Authentication (MFA)  
Even if a password is guessed, the attacker cannot log in without a second authentication factor.

Strong Password Policies  
Require long and complex passwords.

CAPTCHA  
Prevent automated login attempts by requiring human verification.

Monitoring and Alerts  
Detect unusual login attempts from unknown IP addresses.

---

### 2. DoS (Denial of Service) Attack

A Denial of Service attack attempts to make a system unavailable to legitimate users by overwhelming it with traffic or requests.

Instead of stealing data, the goal is to disrupt availability.

#### How DoS Attacks Are Carried Out

A single machine sends an extremely large number of requests to a server.

Common techniques include:

Traffic Flooding  
Sending massive numbers of HTTP requests.

Resource Exhaustion  
Consuming CPU, memory, or network resources.

Protocol Exploits  
Exploiting weaknesses in network protocols.

When the server becomes overloaded, it cannot serve legitimate users.

#### How to Stay Safe from DoS Attacks

Protection strategies include:

Traffic Filtering  
Block malicious IP addresses.

Rate Limiting  
Restrict the number of requests per IP address.

Load Balancers  
Distribute traffic across multiple servers.

Auto Scaling  
Automatically increase infrastructure capacity during traffic spikes.

Web Application Firewalls (WAF)  
Filter malicious traffic patterns.

Content Delivery Networks (CDN)  
Absorb traffic spikes using distributed networks.

---

### 3. DDoS (Distributed Denial of Service) Attack

A Distributed Denial of Service attack is similar to a DoS attack but is launched from many machines simultaneously.

These machines are usually part of a botnet — a network of compromised devices controlled by attackers.

#### How DDoS Attacks Are Carried Out

Attackers infect thousands or millions of devices such as:

- computers
- servers
- IoT devices
- routers

These infected systems form a botnet.

The attacker commands the botnet to send traffic to a target simultaneously.

This creates enormous traffic volumes that overwhelm servers or networks.

Common DDoS attack types include:

Volume-Based Attacks  
Overload bandwidth with massive traffic.

Protocol Attacks  
Exploit weaknesses in network protocols.

Application Layer Attacks  
Target specific applications like HTTP APIs.

#### How to Stay Safe from DDoS Attacks

Mitigation techniques include:

DDoS Protection Services  
Cloud providers offer managed protection systems.

Traffic Scrubbing  
Malicious traffic is filtered before reaching servers.

Anycast Networks  
Traffic is distributed across multiple global data centers.

Elastic Infrastructure  
Auto-scaling systems absorb traffic spikes.

Rate Limiting and WAF  
Limit suspicious traffic patterns.

---

### 4. Phishing Attack

Phishing is a social engineering attack that tricks users into revealing sensitive information such as:

- passwords
- credit card numbers
- authentication tokens

Attackers impersonate trusted entities to deceive victims.

#### How Phishing Attacks Are Carried Out

Attackers create messages that appear legitimate.

Common methods include:

Fake Emails  
Emails that look like they come from banks, companies, or colleagues.

Malicious Links  
Victims are directed to fake websites that capture login credentials.

Attachment-Based Attacks  
Emails include malicious files that install malware.

Spear Phishing  
Highly targeted attacks aimed at specific individuals.

Business Email Compromise  
Attackers impersonate executives to request financial transfers.

#### How to Stay Safe from Phishing Attacks

Security practices include:

Security Awareness Training  
Educate employees about phishing tactics.

Email Filtering Systems  
Detect suspicious messages.

Multi-Factor Authentication  
Prevent unauthorized logins even if credentials are stolen.

Domain Monitoring  
Detect look-alike domains used for phishing.

URL Verification  
Encourage users to verify links before clicking.

---

### 5. XSS (Cross-Site Scripting)

Cross-Site Scripting is a web application attack where attackers inject malicious scripts into websites viewed by other users.

The malicious script runs inside the victim's browser.

#### How XSS Attacks Are Carried Out

The attack usually occurs when user input is not properly sanitized.

Example scenarios include:

Comment fields  
Search boxes  
Form inputs  
User profile fields

An attacker inserts malicious JavaScript into an input field.

When other users view the page, their browsers execute the script.

Common consequences include:

- session cookie theft
- account hijacking
- redirecting users to malicious websites

Types of XSS include:

Stored XSS  
Malicious code stored permanently in the database.

Reflected XSS  
Malicious code embedded in URLs or request parameters.

DOM-Based XSS  
Client-side scripts manipulate the DOM insecurely.

#### How to Stay Safe from XSS Attacks

Prevention strategies include:

Input Validation  
Validate and sanitize all user inputs.

Output Encoding  
Encode data before displaying it in HTML.

Content Security Policy (CSP)  
Restrict which scripts browsers can execute.

Use Secure Frameworks  
Modern frameworks automatically escape outputs.

HTTP-Only Cookies  
Prevent JavaScript from accessing session cookies.

---

### 6. CSRF (Cross-Site Request Forgery)

CSRF is an attack that forces authenticated users to perform unintended actions on a web application.

The attacker tricks a user's browser into sending unauthorized requests.

#### How CSRF Attacks Are Carried Out

The attack works when a user is already authenticated to a website.

Example scenario:

1. User logs into a banking website.
2. User visits a malicious website.
3. That site sends a hidden request to the banking site.
4. The browser automatically includes authentication cookies.

The server processes the request as if the legitimate user initiated it.

This can result in actions like:

- transferring money
- changing passwords
- modifying account details

#### How to Stay Safe from CSRF Attacks

Security controls include:

CSRF Tokens  
Unique tokens must be included with requests.

SameSite Cookies  
Restrict cross-site cookie usage.

User Confirmation  
Require password confirmation for sensitive actions.

Double Submit Cookies  
Use token verification techniques.

---

### 7. SSRF (Server-Side Request Forgery)

SSRF occurs when attackers trick a server into making requests to unintended locations.

Instead of the attacker making requests directly, the vulnerable server sends them.

#### How SSRF Attacks Are Carried Out

Many applications allow servers to fetch remote resources.

Example use cases:

- image fetching
- webhook processing
- API integrations

Attackers manipulate inputs that specify URLs.

Instead of external URLs, attackers target internal resources.

Examples include:

- internal APIs
- cloud metadata services
- private network resources

This can expose sensitive information or allow attackers to access internal systems.

#### How to Stay Safe from SSRF Attacks

Defense mechanisms include:

URL Allow Lists  
Allow only approved external domains.

Network Segmentation  
Prevent servers from accessing sensitive internal services.

Metadata Protection  
Block access to cloud metadata endpoints.

Input Validation  
Strictly validate URL inputs.

Firewall Rules  
Restrict outbound network requests.

---

### 8. SQL Injection

SQL Injection is a database attack where attackers manipulate SQL queries by injecting malicious input.

It occurs when user input is directly inserted into database queries without proper validation.

#### How SQL Injection Attacks Are Carried Out

Example scenario:

An application constructs SQL queries like this:

SELECT * FROM users WHERE username = 'input'

If the application does not sanitize input, attackers can manipulate the query.

This allows attackers to:

- bypass authentication
- extract database records
- modify or delete data
- execute administrative database commands

SQL injection is one of the most dangerous web vulnerabilities.

#### How to Stay Safe from SQL Injection

Prevention techniques include:

Prepared Statements  
Use parameterized queries instead of string concatenation.

ORM Frameworks  
Use database abstraction layers that prevent injection.

Input Validation  
Validate user inputs before processing.

Least Privilege Database Access  
Applications should not use highly privileged database accounts.

Database Firewalls  
Monitor and block suspicious queries.

---

### 9. Security Vulnerabilities in Third-Party Libraries

Modern applications rely heavily on open-source libraries and frameworks.

These dependencies may contain vulnerabilities.

If an application includes a vulnerable library, attackers can exploit it even if the application's code is secure.

#### How Third-Party Vulnerabilities Are Exploited

Attackers identify known vulnerabilities in widely used libraries.

Examples include vulnerabilities in:

- web frameworks
- logging libraries
- authentication libraries
- encryption libraries

If organizations do not update dependencies, attackers can exploit these weaknesses.

Supply chain attacks can also occur where attackers insert malicious code into dependencies.

#### How to Stay Safe from Third-Party Library Vulnerabilities

Organizations must actively manage dependencies.

Security practices include:

Dependency Scanning  
Use automated tools to detect vulnerable packages.

Regular Updates  
Keep libraries updated to patched versions.

Minimal Dependencies  
Use only necessary libraries.

Software Bill of Materials (SBOM)  
Maintain visibility into all dependencies used in an application.

Dependency Monitoring Tools  

Examples include:

- Snyk
- Dependabot
- OWASP Dependency Check
- Mend

These tools continuously scan projects for vulnerable packages.

---

### 10. Final Summary

Cyber attacks target many different layers of modern systems.

Common attack categories include:

Authentication Attacks  
Brute force and credential stuffing.

Availability Attacks  
DoS and DDoS attacks.

Social Engineering  
Phishing attacks targeting human behavior.

Web Application Attacks  
XSS, CSRF, SSRF, and SQL injection.

Supply Chain Attacks  
Exploiting vulnerabilities in third-party libraries.

Modern DevSecOps practices address these threats by integrating security controls into development, deployment, and runtime environments.

Security is achieved through:

- secure coding practices
- automated vulnerability scanning
- strong authentication systems
- infrastructure security controls
- continuous monitoring

A multi-layer security approach ensures systems remain resilient even when individual defenses fail.
