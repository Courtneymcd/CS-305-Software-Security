# CS 305 Software Security - Artemis Financial

Courtney McDonald

This repository has my Artemis Financial Vulnerability Assessment Report from Project One for CS 305.

## Who was the client and what did they want?

Artemis Financial is a consulting company that creates individualized financial plans for its clients, covering savings, retirement, investments, and insurance. They wanted to modernize their web application, and since they handle a lot of sensitive financial data, they needed to know where their software was vulnerable and how to make communication between them and their clients secure. For this project I played a developer at Global Rain reviewing their Spring Boot REST API.

## What did I do well, and why is secure coding important?

I think I did well with the manual code review. I went through each class and connected what I found to a CWE, like the hardcoded "root/root" database login in DocData, the endpoints with no authentication, and the deposit method that would take a negative number. After that I ran the OWASP dependency-check plugin, which found 13 vulnerable dependencies and 162 vulnerabilities total. Coding securely is important because one mistake can expose customer data. For a financial company that could mean customers losing money, legal trouble with regulations like GLBA, and losing customers' trust. Good security protects the company as a whole and its reputation.

## What was challenging or helpful?

The dependency-check plugin gave me trouble at first. The version in the pom.xml was too old to work with the current NVD API, so I had to update it to 12.1.0 before it would even run. Once I got the report, there were a lot of CVEs to go through, and some were false positives. Going through them was helpful though because it showed me how to figure out which issues actually matter most.

## How did I increase layers of security, and what would I use in the future?

In Project Two I added a SHA-256 checksum so data could be verified, created a self-signed certificate with Java keytool, and set the app up to run over HTTPS so data is encrypted. In the future I would keep using dependency-check and look up findings in the NVD so I can see how serious they are. I would also use the OWASP Top 10 to help decide which fixes to do first.

## How did I make sure the code was functional and secure?

After refactoring, I ran the application and went to the checksum endpoint using https://localhost to make sure it worked and returned the correct hash. Then I ran the dependency-check again and compared it to the first report to make sure my changes didn't add any new vulnerabilities.

## What resources, tools, or practices will help me later?

The OWASP dependency-check Maven plugin, Java keytool, the NVD, the CWE list, and the OWASP Top 10 are all things I can use again. I also want to keep the habit of doing a manual review first, then running a tool, and testing again after any changes.

## What could I show employers?

I could show this vulnerability assessment report because it shows I can review code for security problems, run and read a dependency scan, and write a plan to fix what I found. I work in aerospace and defense, where security is a big deal, so being able to show I understand this would help me.
