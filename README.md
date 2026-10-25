# Asterisk VoIP PBX Laboratory

## 1. Project Overview

This project documents the installation, configuration, testing, and troubleshooting of a Voice over Internet Protocol (VoIP) Private Branch Exchange (PBX) using Asterisk on Ubuntu Server.

The purpose of this project is to implement an internal telephone system that allows registered SIP clients to communicate with one another over a local network.

## 2. Objectives

* Install and configure Asterisk PBX.
* Configure SIP extensions using PJSIP.
* Register SIP clients from different devices.
* Establish internal voice calls between extensions.
* Understand SIP registration, call signaling, and RTP audio.
* Document network configuration and troubleshooting procedures.
* Maintain reproducible configurations for future deployment.

## 3. System Environment

| Component             | Configuration             |
| --------------------- | ------------------------- |
| Operating System      | Ubuntu Server 24.04.5 LTS |
| Kernel                | Linux 6.8.0-139-generic   |
| PBX Software          | Asterisk 20.6.0           |
| SIP Configuration     | PJSIP                     |
| SIP Transport         | UDP                       |
| SIP Port              | 5060                      |
| Network Adapter       | VMware Bridged            |
| PBX IP Address        | 192.168.1.135             |
| Configured Extensions | 101, 102, 103             |

## 4. Network Architecture

The laboratory uses a virtualized Ubuntu Server running Asterisk.

* Extension 101: Android/mobile phone running Zoiper.
* Extension 102: Windows computer running MicroSIP.
* Extension 103: Additional SIP extension for testing.
* PBX: Ubuntu Server running Asterisk.

The SIP clients and PBX communicate over the same local network.

## 5. Project Status

* [x] Ubuntu Server installation
* [x] SSH configuration
* [x] Asterisk installation
* [x] PJSIP configuration
* [x] UDP SIP transport configuration
* [x] Internal dialplan configuration
* [x] Extension 101 configuration
* [x] Extension 102 configuration
* [x] Extension 103 configuration
* [x] Extension 101 registration
* [x] Extension 102 registration
* [x] Successful call between extensions 101 and 102
* [ ] Register and test extension 103
* [ ] Test all extension combinations
* [ ] Inspect SIP signaling and RTP audio
* [ ] Complete final testing documentation

## 6. Configuration Files

The `configs/` directory contains sanitized reference configurations for:

* `pjsip.conf`: SIP transport, endpoint, authentication, and address-of-record configuration.
* `extensions.conf`: Internal extension dialplan.

These files are intended for reference and must be reviewed before being deployed to a live server for production purpose.

## 7. Important Security Notes

* Never commit production SIP passwords.
* Never commit private keys, tokens, or other secrets.
* Use strong passwords when deploying outside an isolated laboratory.
* Restrict SIP access using appropriate firewall rules.
* Do not expose SIP services directly to the public internet without appropriate security controls.

## 8. Learning Outcome

This project provides practical experience in Linux server administration, VoIP networking, SIP configuration, PBX management, troubleshooting, and technical documentation.

[Mlue Teachnology](https://www.mluetechnology.me)
