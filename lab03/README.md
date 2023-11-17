SEG 4105
Anurag Taak
300073742

## Overview

Hotel-Palace is a comprehensive hotel-management program designed to facilitate and manage the operation of a chain of hotel branches. The program serves multiple purposes, both for hotel personnel and visitors, to enhance the overall experience of booking rooms at a variety of hotels across North America. The purpose of the application is to stand as a tool that benefits both corporations and guests by serving as a central hub for ultimate and efficient service.

## Problem 

Currently there is a lack of security within the web application. At present, there passwords and user data is stored as plain text and is plainly visible by accessing the database. This leaves the company especially vulnerable to cyber attacks and having info about their clients leaked. 

This is a large concern as data privacy and security of high value to our customers and something which our competitors already provide their clients. 

## Appetite
There are currently only 4-5 developers available to create a viable product to help resolve this problem. Thus the primary focus for increasing security will be user passwords. The other fields within the database will remain stored in their original data formats. 

## Time budget
6 weeks

## Solution

To tackle the problem, we can use a combination of salting and hashing techniques. Upon user registeration, rather than directly storing the password in the database, we will store a salted and hashed version of the password. When a user successfully signs up the system will generate a random unique value called a "salt" specifically for that user. The salt will then be combined with the user entered password before being hashed. 

We can use a modern cryptographic has function like bcrypt, Argon2, or scrypt. The output is then a fixed-length string of characters which is what will be stored in the database. Typically the string is in the form of a hex or base64 encoded value. 

When the user tries to sign in again in the future, rather than comparing the passwords directly, we will re-salt and re-hash the newly entered password and compare it to the one stored within the database. If they match, the user will be granted access, and if not access will be denied. 


## Breadboarding:
![image](https://github.com/Zoom1120/seg4105_playground/blob/main/Deliverable%201/Assets/bb.jpg)
 
## No-goes (nice-to-haves)

* Network Security and Firewalls
    * Using a firewall to restrict access to the PostgreSQL database server, allowing only trusted IPs or networks to connect.

* Secure Backup and Recovery
    *Protect database backups by encrypting them and storing them in a secure location.
    *Implement secure recovery procedures to ensure that data can be restored in case of a disaster.

* Compliance with Regulations:
    *The organization is not subject to specific data protection regulations (e.g., GDPR, HIPAA)

## Rabbit Holes

* Secure Application Development:
    *Ensure that your applications follow secure coding practices, such as parameterized queries and input validation, to prevent SQL injection attacks.

* Regular Security Audits:
    *Conduct regular security audits and vulnerability assessments to identify and remediate potential security issues.

* Use of Security Extensions:
    *Consider using security extensions like pgAudit for advanced auditing capabilities or additional security features.
    *None of the Previous 3 Options will be persued due to a lack of time in the 6 week-cycle and the team-hours required to complete these tasks.