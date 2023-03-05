---
title: Computer Security Lecture
tags:
- UNNC
- Computer Security
- Lecture
categories:
- Computer Security
- Lecture
---

<!-- toc -->

## Lecture 01
### Security
- **`Security`**: 
  - People have protected their property and privacy for generations
  - Security is about the protection of assets
  - |Terms|Definations|
    |:----:|:------|
    |Reliability | **Accidental** failures |
    |Usability   | Operating mistakes  |
    |Security    | **Intentional** failures|
  - Legal system defines boundaries of acceptable behaviour
- **Goal**
  - A secure system is one which does not exist
  - It is **NOT** about achieving complete security
  - It is about minimising risk to systems
- **`Attack`**
  - An attack is a sequence of steps. It may start innocuosly, gathering information needed to move on to gain privileges on one machine, from there jump to anthor machine, until the final target is reached.
- **`Attacker`**
- **`Security Management`**
  - Management responsible for assets
- **`Security Policy`**
  - State what should be protected 
  - And how this should be achieved
- **`Measure Security`**
  - Product Security
  - System Security
  - Cost of an Attack
  - Cost of Assets

### Risk & Threat
- **`Risk`**
  - Possibility of an incident or attack to cause damage to your enterprise
  - $$Risk = Assets * Vulnerabilities * Threat$$
- **`Risk Analysis`**
  - All information assets
  - IT infrastructure
  - Perform during development
  - Types
    -`Quantitative Risk Analysis`
        - probability theory based on mathematical theory
        - quality of results depends on quality of inputs
        - - not always feasible
    - `Qualitative Risk Analysis`
      - more applicable
      - scaling based on judgements of security experts
- **`Assets`**
  - Software
  - Hardware
  - Data Information
  - Reputation
- **`Vulnerabilities`**
  - Weaknesses of a system that could be accidentally or intentionally exploited to damage assets
    - Badly configured accounts
    - Programs with known flaws
    - Weak access control
    - Weak firewall configuration
    - Can be rated according to impact 
- **`Threats`**
  - Actions by adversaries who try to exploit vulnerabilities to damage assets
- **`Countermeasures`**
  - Risk analysis generates recommended countermeasures
  - Up to date/continuous risk analysis not always possible

## Lecture 02
### Computer Security
- **`Computer Security`**
  - The property of a computer system such that reliance can justifiably be placed in the service it delivers
  - Concerned with the measures we can take to deal with intentional actions by parties behaving in some unwelcome fashion
  - `Confidentiality`: prevention of unauthorised disclosure of information
  - `Integrity`: prevention of unauthorised modification of information
  - `Availability`: prevention of unauthorised withholding of information or resources
- **`Confidentiality`**
  - The prevention of unauthorised users reading sensitive (private, secret) information
  - `Privacy`: protection of personal data
  - `Secrecy`: protection of data of an organisation
- **`Integrity`**
  - _Informally_ > Making sure everything is as it is supposed to be.
  - _Formally_ > Integrity deals with the prevention of unauthorised writing.
  - The prevention of unauthorised modification of data, and the assurance that data remains unmodified
  - Data Integrity
    > “The state that exists when computerised data is the same as that in the source documents and has not been exposed to accidental or malicious alteration or destruction.” [Orange Book]
- **`Authenticity`**
  - $$Authenticity = Integrity + Freshness$$
- **`Availability`**
  - The property of being accessible and useable upon demand by an authorised entity.
  - The prevention of authorised access to resources or the delaying of timecritical operations.
  - Users should be held responsible for their actions
  - System should identify and authenticate users
- **`Non-Repudiation`**
  - Non-repudiation provides un-forgeable evidence
  - Evidence verifiable by a third party
  - Nonrepudiation of
    - origin > sender identification
    - delivery > delivery confirmation
  
### Reliability
- **`Reliability`**
  - against (accidental) failures
  - `Safety`: impact of system failures on their environment
  - `Security` is an aspect of reliability, and vice versa
  - `Dependability`
    > The property of a computer system such that reliance can justifiably be placed in the service it delivers

### Fundamental Dilemma
- **`Fundamental Dilemma`**
  - Trade-off between security and ease of use
  - conflict between security and ease of use:
    - Security mechanisms need increased computational resources 
    - Security interferes with working patterns of users
    - Managing security is work – thus better (G)UI wins

### Data & Information
- Security is about controlling access to information and resources
- **`Data`**
  - Means to represent information
- **`Information`**
  - (subjective) interpretation of data 
- **`Inference`**
  - Focusing on data can still leave information vulnerable

### Security Design
- **`Fundamental Design Principles`**
  - Focus of Control
  - Complexity vs. Assurance 
  - Centralised or Decentralised Controls 
  - Layered Security
- **`Focus of Control`**
  - `1st Design Decision`
    - In a given application, should the protection mechanisms in a computer system focus on:
      - Data: Permitted manipulation of data
      - Operations: Permitted invocations
      - Users: Permissions for specific users
  - `2nd Design Decision`
    - Do you prefer simplicity- and higher assurance- to a feature-rich security environment?
  - `3rd Design Decision`
    - Should the tasks of defining and enforcing security be given to a central entity or should they be left to individual components in a system?
    - `Central entity`: could mean a bottleneck
    - `Distributed solution`: more efficient but harder to manage
  - `4th Design Decision`
    - How can you prevent an attacker getting access to a layer below the protection mechanism?
    - A good security layer built upon an insecure layer is useless
- **`Onion Model`** 
    - ```mermaid
        graph TD;
        subgraph Applications
            subgraph Services
                subgraph OS
                    subgraph Kernel
                        subgraph Hardware
                        end
                    end
                end
            end
        end
        ```
    - Each layer protects a boundary, and relies on the security of the layers below
    - `Security perimeter`: parts of a system that can be used to disable the protection mechanism lying within

## Lecture 03
### Usernames and Passwords
- **`Identification`**: Who you are
- **`Authentication`**: Verify that identity
- **`TOCTTOU`**: Time of check to time of use
  - Repeated authentication
  - At the start and during a session
- **`Password`**: Passwords are digital keys
  - One-way hash function
- **`Password cracking`**:
  - Offline: You have a copy of the password hash locally
    - Offline password cracking is simply a case of trying lots of possible passwords, and seeing if we have a hash collision with a password list
    - Brute Force approach
    - **`Dictionary Attacks`**: 
      - Using a dictionary of common words and passwords
      - Apply small variations to this list, trying them all
      - Combine words from two different lists
  - Online: You do not have the hash, and are instead attempting to gain access to an actual login terminal
- **`Password Salting`**: We can improve security by prepending a random "salt" to a password before hashing
  - Cracking multiple passwords is slower – a hit is for a single user, not all users with that password
  - Prevents rainbow table attacks – we can’t pre-compute that many password combinations
  - Salting has no effect on the speed of cracking a single password
