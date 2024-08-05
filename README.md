# Honeypot

# Honeypot Project: Enhancing Cybersecurity with the Cowrie Framework

## Introduction

In today's digital landscape, cyber threats are increasingly sophisticated and prevalent, posing significant risks to organizations of all sizes. As attackers employ more advanced techniques to breach defenses, understanding their behavior and methodologies becomes crucial for developing effective countermeasures. One innovative approach to gaining this understanding is the deployment of honeypots—decoy systems designed to attract and monitor cyber attackers.

## HONEYPOT

![Untitled](Honeypot%20d47b75953cee4b0f84939540b9e2f7e4/Untitled.png)

A honeypot serves as a trap for malicious actors, presenting itself as a vulnerable target while being isolated and meticulously monitored. This setup allows security professionals to observe attackers in action, gather intelligence on their tactics, techniques, and procedures (TTPs), and improve defensive strategies accordingly.

In this project, we will deploy a honeypot using the Cowrie framework. Cowrie is a versatile tool that simulates a network environment to lure attackers and log their activities in detail. By setting up Cowrie, we aim to gain valuable insights into the current threat landscape, analyze attack patterns, and enhance our cybersecurity posture.

## PURPOSE

In this project, we will set up a honeypot using the Cowrie framework. Cowrie is an excellent tool for simulating a network environment that attracts and logs interactions with potential attackers. The primary purpose of deploying Cowrie is to identify and analyze attacks. By observing the behavior and methods employed by attackers, we can gather valuable insights into their tactics, techniques, and procedures. This information can then be used to enhance security measures and better defend against future attacks.

## OVERVIEW

This project aims to deploy a honeypot using the Cowrie framework. Cowrie is a powerful tool designed to simulate a vulnerable network environment to attract and monitor cyber attackers. The primary goal is to collect and analyze data on the behaviors and techniques employed by attackers when they interact with the honeypot. This information is invaluable for understanding potential security threats and improving defensive strategies.

## PREREQUISITES

1. ***DigitalOcean Account***: A DigitalOcean account is essential for setting up the virtual machine where the honeypot will be deployed.
2. **Linux Basics**: Basic knowledge of Linux commands and operations is necessary for managing the server and performing configurations.
3. **SSH and Terminal Skills**: Understanding SSH and how to use a terminal is crucial, as these tools will be used to remotely access and configure the server.
4. **Stable Internet Connection**: A reliable internet connection is required to ensure consistent access to the server and to download necessary packages and updates.
5. **Docker Basics**: Familiarity with Docker is beneficial, as it simplifies the deployment and management of the Cowrie honeypot within a containerized environment.

## **USES OF A HONEYPOT**

1. **Intrusion Detection**: Honeypots detect unauthorized access and activities by attracting attackers, making it easier to identify potential threats.
2. **Behavioral Analysis**: They allow security experts to observe and study the tactics, techniques, and procedures (TTPs) of attackers in a controlled environment.
3. **Vulnerability Identification**: Honeypots can help identify vulnerabilities in a network by observing how attackers exploit these weaknesses.
4. **Incident Response**: By providing early warning signs of an attack, honeypots enable quicker incident response and mitigation.
5. **Deception and Diversion**: They divert attackers away from critical systems, reducing the risk of actual damage to production environments.
6. **Threat Intelligence Gathering**: Honeypots collect valuable data on new attack vectors and malware, contributing to broader threat intelligence efforts.
7. **Training and Research**: They are used in cybersecurity training to simulate attack scenarios and for research purposes to develop new defensive strategies.

## HOW HONEYPOT WORKS

- **Simulation**: Honeypots simulate vulnerable systems or services that appear attractive to attackers.
- **Deployment**: They are deployed within a network to mimic real assets, such as servers or applications.
- **Attracting Attackers**: By appearing vulnerable, honeypots attract and engage malicious actors who attempt to exploit perceived weaknesses.
- **Monitoring**: Activities within the honeypot, such as login attempts or file access, are monitored and logged.
- **Analysis**: Data collected includes attacker techniques, tools used, and payloads deployed.
- **Security Insights**: Insights gained help in understanding emerging threats and improving overall cybersecurity defenses.

## **WHAT IS COWRIE**

Cowrie is a medium to high interaction SSH and Telnet honeypot designed to log brute force attacks and the shell interaction performed by the attacker. In medium interaction mode (shell) it emulates a UNIX system in Python, in high interaction mode (proxy) it functions as an SSH and telnet proxy to observe attacker behavior to another system.

### Features

- *Choose to run as an emulated shell (default):* Fake filesystem with the ability to add/remove files. A full fake filesystem resembling a Debian 5.0 installation is included of adding fake file contents so the attacker can cat files such as /etc/passwd. Only minimal file contents are included. Saved files downloaded with wget/curl or uploaded with SFTP and SCP for later inspection
- *Or proxy SSH and telnet to another system*Run as a pure telnet and SSH proxy with monitoring Or let Cowrie manage a pool of QEMU emulated servers to provide the systems to login to

**For both settings:**

- Session logs are stored in an UML Compatible format for easy replay with the bin/playlog utility.
- SFTP and SCP support for file upload
- Support for SSH exec commands
- Logging of direct-tcp connection attempts (SSH proxying)
- Forward SMTP connections to SMTP Honeypot (e.g. [mailoney](https://github.com/awhitehatter/mailoney))
- JSON logging for easy processing in log management solutions

## REQUIREMENTS

Software required to run locally:

- Python 3.9+
- python-virtualenv
- Docker

```sql
appdirs==1.4.4
attrs==23.2.0
bcrypt==4.1.3
configparser==7.0.0
cryptography==42.0.8
packaging==24.0
pyasn1_modules==0.4.0
pyparsing==3.1.2
python-dateutil==2.9.0.post0
service_identity==24.1.0
tftpy==0.8.2
treq==23.11.0
twisted==24.3.0
```

## Setup Guide for [Cowrie](https://github.com/cowrie/cowrie) Honeypot

1. **Create a Droplet on DigitalOcean**:
- Log in to your DigitalOcean account.
- Navigate to the "Droplets" section and create a new Droplet with Ubuntu or another preferred Linux distribution.
- Choose the appropriate plan and region, then create the Droplet.

![Untitled](Honeypot%20d47b75953cee4b0f84939540b9e2f7e4/Untitled%201.png)

1. First, set up the server, connect to it, and update and upgrade it according to the requirements.

![Untitled](Honeypot%20d47b75953cee4b0f84939540b9e2f7e4/Untitled.jpeg)

![Untitled](Honeypot%20d47b75953cee4b0f84939540b9e2f7e4/Untitled%201.jpeg)

1. Now, clone the Cowrie GitHub repository. 

![Untitled](Honeypot%20d47b75953cee4b0f84939540b9e2f7e4/Untitled%202.jpeg)

1. Now, install Docker, Docker container and Snap to run the honeypot on the server without interruptions.
- To install Docker and snap we use the command

```sql
sudo snap install docker         # version 24.0.5, or
sudo apt  install docker.io      # version 24.0.5-0ubuntu1~22.04.1
sudo apt  install podman-docker  # version 3.4.4+ds1-1ubuntu1.22.04.2
```

![Untitled](Honeypot%20d47b75953cee4b0f84939540b9e2f7e4/Untitled%203.jpeg)

- to install the the docker container we use the command

```sql

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

![Untitled](Honeypot%20d47b75953cee4b0f84939540b9e2f7e4/Untitled%204.jpeg)

1. Now the setup for the honeypot is complete. To access and run the honeypot, use the command.

```sql
$ docker run -p 2222:2222 cowrie/cowrie:latest
$ ssh -p 2222 root@localhost
```

- This command will start the Honeypot setup and run it on the server.
- Also it will pull up the resources and then

![Untitled](Honeypot%20d47b75953cee4b0f84939540b9e2f7e4/Untitled%202.png)

![Untitled](Honeypot%20d47b75953cee4b0f84939540b9e2f7e4/Untitled%203.png)

1. With this setup, we can effectively observe and understand hackers' behavior and processes, allowing us to implement necessary security updates.
2. The attacker can connect to the honeypot and access the decoy file. The interface will look like this:

![Untitled](Honeypot%20d47b75953cee4b0f84939540b9e2f7e4/Untitled%205.jpeg)

1. In our system, we get the interface as shown below:

![Untitled](Honeypot%20d47b75953cee4b0f84939540b9e2f7e4/Untitled%206.jpeg)

## References

- DigitalOcean Documentation: [https://docs.digitalocean.com/](https://docs.digitalocean.com/)
- Cowrie GitHub Repository: [https://github.com/cowrie/cowrie](https://github.com/cowrie/cowrie)
- "Honeypots: Concepts, Approaches, and Challenges" - Research Paper: [https://hal.science/hal-03324407/document](https://hal.science/hal-03324407/document)

**Appendix:**

For additional information or troubleshooting tips, please refer to the following resources:

- Cowrie Documentation: [https://cowrie.readthedocs.io/en/latest/](https://cowrie.readthedocs.io/en/latest/)
- DigitalOcean Community Tutorials: [https://www.digitalocean.com/community](https://www.digitalocean.com/community)
- [Demo Link](https://drive.google.com/file/d/14gqBcVR4NN3gIYhQ4eFaiBXhD2QWJpqc/view?usp=drive_link)