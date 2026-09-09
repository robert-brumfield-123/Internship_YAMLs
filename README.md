# Internship_YAMLs

CloudFormation templates for creating isolated AWS environments used for
hands-on cybersecurity exercises. The labs are designed to give students
practical experience with network reconnaissance, service enumeration, and
basic attack-surface analysis.

> [!WARNING]
> **These templates intentionally create insecure virtual machines.**
> They are designed exclusively for controlled cybersecurity education and
> testing. The systems may contain intentionally vulnerable services,
> weak configurations, and permissive security rules. **Do not deploy these
> templates in a production AWS account or in an environment containing
> sensitive data.**
>
> Use these templates only in an isolated AWS environment that you control.
> Review AWS costs, quotas, networking, and security-group rules before
> deployment. Terminate the resources when the lab is complete.

## Templates

### `nmap_lab.template`

Creates an isolated network containing a Kali Linux attacker machine and
multiple Ubuntu target machines configured with different network services.

The purpose of this lab is to have students use **Nmap** to perform network
reconnaissance, identify open ports and services, and evaluate the different
targets based on their exposed attack surfaces.

Students can use the information gathered during scanning to determine which
target would be the most appropriate candidate for further security testing.

### `metasploitable_lab.template`

Creates an intentionally vulnerable, Metasploitable-like Ubuntu target in
an isolated AWS VPC.

The machine is configured with intentionally exposed services and
vulnerabilities so that students can practice identifying and evaluating
potential attack vectors in a controlled environment.

## Technologies

- AWS EC2
- AWS CloudFormation
- Amazon VPC
- Security Groups
- Kali Linux
- Ubuntu Linux
- Nmap

## Educational Purpose

These templates were developed as part of a cybersecurity course to provide
students with hands-on experience working with cloud-based virtual
infrastructure and network security concepts.

The exercises emphasize:

- Network reconnaissance
- Port and service enumeration
- Attack-surface identification
- Network segmentation
- AWS infrastructure
- Security-group configuration
- Vulnerable system analysis

## Disclaimer

These templates are provided for **educational and authorized security
testing purposes only**.

The author is not responsible for costs, security incidents, data loss, or
other consequences resulting from deployment or modification of these
templates.

Only use these environments against systems that you own or have explicit
authorization to test.

## Architecture

This is a diagram showing the architecture that is created by the nmap_lab.template file.

                     AWS VPC
                  10.80.0.0/16
                         |
              +----------+----------+
              |                     |
       Attacker Subnet        Target Subnet
        10.80.1.0/24          10.80.2.0/24
              |                     |
       Attacker VM            +------+------+------+
       attacker-nmap          |      |      |      |
                            target-1 target-2 target-3 target-4
