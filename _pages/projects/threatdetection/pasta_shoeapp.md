---
title: 🕵️‍♀️ PASTA Threat Modeling for a Sneaker App
permalink: /pasta_shoeapp
parent: Threat Detection & Analysis
---
# PASTA Threat Modeling for a Sneaker App
{: .no_toc }

{: .note }
OWASP Top 10, PASTA Framework, Threat Modeling, App Security Assessment, Risk Mitigation, Threat Analysis, Vulnerability Analysis
{: .fs-3 }

#### Contents
{: .no_toc }
- TOC
{:toc}

## Scenario
I am part of the growing security team at a company for sneaker enthusiasts and collectors. The business is preparing to launch a mobile app that makes it easy for their customers to buy and sell shoes. I am performing a threat model of the application using the PASTA framework.

## Goals & Objectives
Go through each of the seven stages of the framework to identify security requirements for the new sneaker company app.

## Results
### Threat Model
<table>
    <tr>
        <th>Stages</th>
        <th>Information</th>
    </tr>
    <tr>
        <td>1. Define business and security objectives</td>
        <td>User data is being collected and stored through the app. They want users to feel that data is being protected and kept private. Interaction between buyers and sellers should be easy with zero friction. Proper payment handling is important to avoid legal issues, so compliance with PCI DSS is critical.</td>
    </tr>
    <tr>
        <td>2. Define the technical scope</td>
        <td>Technologies used by the app:
            <ul>
                <li>API - the app is built by combining several third-party software components</li>
                <li>PKI - the app uses AES and RSA encryption algorithms to encrypt sensitive user data and to facilitate key exchange</li>
                <li>SHA256 - used to protect user passwords</li>
                <li>SQL - used to query sneaker inventory and seller information from a database</li>
            </ul>
            I prioritize SQL over other technologies because SQL injection attacks are common attack methods that threat actors use to compromise and exfiltrate sensitive data from databases. This prioritization coincides with the company's concern with data privacy.</td>
    </tr>
    <tr>
        <td>3. Decompose application</td>
        <td><a href="assets/images/dataflow_lg.png" target="_blank">Dataflow diagram</a><sup>1</sup></td>
    </tr>
    <tr>
        <td>4. Threat analysis</td>
        <td>Threats can include:
            <ul>
                <li>Malware installation by an internal threat actor from the development team</li>
                <li>DDoS attack could be carried out on the database</li>
                <li>API injection attacks</li>
                <li>Pass-the-hash attack can occur if an threat actor executes a successful SQL injection attack that targets hashed passwords</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td>5. Vulnerability analysis</td>
        <td>Vulnerabilities can include:
            <ul>
                <li>Lack of prepared statements and input validation to prevent injection attacks</li>
                <li>Using untrustworthy CAs to receive digital certificates from and not using a hierarchal trust model to establish a properly validated trust chain</li>
                <li>Lack of MFA to prevent unauthorized account access as a result of path-the-hash attacks</li>
                <li>Lack of code signing to help detect code tampering and prevent malware installation</li>
            </ul></td>
    </tr>
    <tr>
        <td>6. Attack modeling</td>
        <td><a href="assets/images/attacktree.png" target="_blank">Attack tree</a><sup>1</sup></td>
    </tr>
    <tr>
        <td>7. Risk analysis and impact</td>
        <td>Security controls that can reduce risk:
            <ul>
                <li>Prepared statements and input validation to prevent injection attacks</li>
                <li>NGFW and IDS/IPS to help mitigate the impact DDoS attacks</li>
                <li>MFA to improve access controls</li>
                <li>Code signing to help detect tampering with the app’s source code by internal or external threats</li>
            </ul></td>
    </tr>
</table>

----

<sup>1</sup> For the sake of brevity, the data diagram and attack tree have been truncated. In real-world scenarios, these diagrams are much more detailed and complex. 

---

<a href="#top" id="back-to-top">Back to top</a>