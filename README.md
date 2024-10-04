<h1>Apply the PASTA threat model framework</h1>

In this activity, you will practice using the Process of Attack Simulation and Threat Analysis (PASTA) threat model framework. You will determine whether a new shopping app is safe to launch.

Threat modeling is an important part of secure software development. Security teams typically perform threat models to identify vulnerabilities before malicious actors do. PASTA is a commonly used framework for assessing the risk profile of new applications.

<h2>Scenario</h2>

You’re part of the growing security team at a company for sneaker enthusiasts and collectors. The business is preparing to launch a mobile app that makes it easy for their customers to buy and sell shoes. 

You are performing a threat model of the application using the PASTA framework. You will go through each of the seven stages of the framework to identify security requirements for the new sneaker company app.

<h2>Part 1 - Access the resources</h2>

<img src="https://i.imgur.com/BH0ywBY.png" height="80%" width="80%"/>

<img src="https://i.imgur.com/k3TX3Jw.png" height="80%" width="80%"/>

<h2>Part 2 - Complete the PASTA stages</h2>

<h3>Step 1: Identify the mobile app's business objectives</h3>

The main goal of Stage I of the PASTA framework is to understand why the application was developed and what it is expected to do.

Note: Stage I typically requires gathering input from many individuals at a business.

First, review the following description of why the sneaker company decided to develop this new app:

Description: Our application should seamlessly connect sellers and shoppers. It should be easy for users to sign-up, log in, and manage their accounts. Data privacy is a big concern for us. We want users to feel confident that we’re being responsible with their information.

Buyers should be able to directly message sellers with questions. They should also have the ability to rate sellers to encourage good service. Sales should be clear and quick to process. Users should have several payment options for a smooth checkout process. Proper payment handling is really important because we want to avoid legal issues.

Transaction Processing: Yes, the app will process transactions, as buyers will be purchasing shoes from sellers. This requires secure payment handling and clear sales processing, making secure payment gateways and encryption essential.

Back-end Processing: The app will involve substantial back-end processing, including managing user accounts, handling transactions, and facilitating messaging between buyers and sellers. This will likely involve secure database management and real-time updates.

Industry Regulations: The app needs to consider payment industry regulations (such as PCI DSS compliance) for secure payment handling. Additionally, data privacy regulations like GDPR or CCPA may apply, as user data privacy is a significant concern for the business.

<h3>Step 2: Evalute the apps components</h3>

In Stage II, the technological scope of the project is defined. Normally, the application development team is involved in this stage because they have the most knowledge about the code base and application logic. Your responsibility as a security professional would be to evaluate the application's architecture for security risks.

For example, the app will be exchanging and storing a lot of user data. These are some of the technologies that it uses:

- Application programming interface (API): An API is a set of rules that define how software components interact with each other. In application development, third-party APIs are commonly used to add functionality without having to program it from scratch.

- Public key infrastructure (PKI): PKI is an encryption framework that secures the exchange of online information. The mobile app uses a combination of symmetric and asymmetric encryption algorithms: AES and RSA. AES encryption is used to encrypt sensitive data, such as credit card information. RSA encryption is used to exchange keys between the app and a user's device.

- SHA-256: SHA-256 is a commonly used hash function that takes an input of any length and produces a digest of 256 bits. The sneaker app will use SHA-256 to protect sensitive user data, like passwords and credit card numbers.

- Structured query language (SQL): SQL is a programming language used to create, interact with, and request information from a database. For example, the mobile app uses SQL to store information about the sneakers that are for sale, as well as the sellers who are selling them. It also  uses SQL to access that data during a purchase.

I would prioritize evaluating the API first because APIs are a common attack surface, especially if they handle sensitive user data or interact with third-party services. Improper API security can lead to data breaches, unauthorized access, or leakage of private information, making it critical to ensure secure authentication, data validation, and communication.

<h3>Step 3: Review a data flow diagram</h3>

During Stage III of PASTA, the objective is to analyze how the application is handling information. Here, each process is broken down.

For example, one of the app's processes might be to allow buyers to search the database for shoes that are for sale. 

Open the PASTA data flow diagram resource. Review the diagram and consider how the technologies you evaluated relate to protecting user data in this process.

Note: Software developers usually have detailed data flow diagrams available for security teams to use and verify that information is being processed securely.

<h3>Step 4: Use an attacker mindset to analyze potential threats</h3>

Stage IV is about identifying potential threats to the application. This includes threats to the technologies you listed in Stage II. It also concerns the processes of your data flow diagram from Stage III.

For example, the apps authentication system could be attacked with a virus. Authentication could also be attacked if a threat actor social engineers an employee.

In the Stage IV row of the PASTA worksheet, list 2 types of threats that are risks to the information being handled by the sneaker company's app. 

Pro tip: Internal system logs that you will use as a security analyst are good sources of threat intel

1. Internal Threats:

- Insider Threats: Employees with legitimate access to sensitive data, such as user credentials or payment information, may misuse their access or inadvertently expose data, potentially leading to data leaks or breaches.
  
- Misconfiguration of Security Controls: Improper configuration of encryption protocols (PKI, SHA-256) or database (SQL) settings by internal staff can leave sensitive data vulnerable to unauthorized access or attacks.

2. External Threats:

- API Exploitation: External attackers could exploit vulnerabilities in the API to gain unauthorized access to user data, perform privilege escalation, or manipulate data flow.

- Man-in-the-Middle (MitM) Attacks: Attackers may intercept and manipulate communications between the app and its users during key exchanges (RSA encryption) or transactions, compromising data confidentiality and integrity.

<h3>Step 5: List vulnerabilities that can be exploited by those threats</h3>

Stage V of PASTA is the vulnerability analysis. Here, you need to consider the attack surface of the technologies listed in Stage II.

For example, the app will use a payment system. The form used to collect credit card information might be vulnerable if it fails to encrypt data.

In Stage V of the PASTA worksheet, list 2 types of vulnerabilities that could be exploited.

Pro tip: Resources like the CVE® list and OWASP are useful for finding common software vulnerabilities.

1. Codebase Vulnerabilities:

- Insecure API Endpoints: If the API lacks proper authentication, authorization, or input validation, attackers could exploit this to access sensitive data, manipulate transactions, or perform unauthorized actions.

2. Database Vulnerabilities:

- SQL Injection: If the app's SQL queries are not properly sanitized, attackers could exploit SQL injection vulnerabilities to access or manipulate the database, steal sensitive user information, or corrupt the data (e.g., product listings or user accounts).

<h3>Step 6: Map assests, threats, and vulnerabilities to an attack tree</h3>

In Stage VI of PASTA, the information gathered in the previous two steps are used to build an attack tree.

Open the PASTA attack tree resource. Review the diagram and consider how threat actors can potentially exploit these attack vectors.

Note: Applications like this normally have large, complex attack trees with many branches.

<h3>Step 7: Identify new security controls that can reduce risk</h3>

PASTA threat modeling is commonly used to reduce the likelihood of security risks. In Stage VII, the final goal is to implement defenses and safeguards that mitigate threats.

In Stage VII of the PASTA worksheet, list 4 security controls that you have learned about that can reduce the chances of a security incident, like a data breach.

- API Security Controls: Implement OAuth 2.0 or JWT for secure API authentication and authorization, along with rate limiting and input validation to prevent unauthorized access and manipulation.

- Database Security: Use parameterized queries and input validation to prevent SQL injection attacks, and enable database encryption for sensitive data fields.

- Encryption for Data Protection: Apply end-to-end encryption (e.g., AES) for sensitive data such as payment information, both in transit and at rest, ensuring data remains secure throughout its lifecycle.

- Multi-Factor Authentication (MFA): Implement MFA for user accounts and administrative access to prevent account takeovers from compromised credentials, adding an extra layer of security.

