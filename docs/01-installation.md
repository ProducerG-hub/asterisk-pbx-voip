# Ubuntu Server and Asterisk Installation

## 1. Environment

The PBX server runs Ubuntu Server 24.04.5 LTS inside VMware.

The virtual machine has SSH enabled to allow remote administration from the Windows host.

## 2. Update the Operating System

After installing Ubuntu Server, update the package index:

```bash
sudo apt update
```

Upgrade installed packages:

```bash
sudo apt upgrade -y
```

Reboot if required:

```bash
sudo reboot
```

## 3. Install SSH Server

Install OpenSSH Server if it was not selected during installation:

```bash
sudo apt install openssh-server -y
```

Enable and start the service:

```bash
sudo systemctl enable --now ssh
```

Check its status:

```bash
sudo systemctl status ssh
```

## 4. Install Asterisk

Install Asterisk from the Ubuntu package repositories:

```bash
sudo apt install asterisk -y
```

Enable and start Asterisk:

```bash
sudo systemctl enable --now asterisk
```

Check the service:

```bash
sudo systemctl status asterisk
```

Verify the installed version:

```bash
asterisk -V
```

The laboratory installation uses Asterisk 20.6.0.

## 5. Access the Asterisk CLI

Connect to the Asterisk command-line interface:

```bash
sudo asterisk -rvvv
```

Exit the CLI:

```text
exit
```

## 6. Verify PJSIP Modules

Run:

```bash
sudo asterisk -rx "module show like res_pjsip"
```

This checks whether the PJSIP components are loaded.

## 7. Configuration Directory

Asterisk configuration files are stored in:

```text
/etc/asterisk/
```

Important files include:

```text
/etc/asterisk/pjsip.conf
/etc/asterisk/extensions.conf
```

## 8. Back Up Configuration Files

Before making changes, create backups:

```bash
sudo cp /etc/asterisk/pjsip.conf \
/etc/asterisk/pjsip.conf.backup
```

```bash
sudo cp /etc/asterisk/extensions.conf \
/etc/asterisk/extensions.conf.backup
```

These backups are stored locally on the server and may help incase of any mistake occured in configurations.
