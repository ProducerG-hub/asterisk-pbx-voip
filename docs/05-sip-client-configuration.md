# Loading and Verifying PJSIP Configuration

## 1. Edit PJSIP Configuration

```bash
sudo nano /etc/asterisk/pjsip.conf
```

Save changes in nano:

* Ctrl+O to write the file.
* Enter to confirm the filename.
* Ctrl+X to exit.

## 2. Restart Asterisk When Transport Settings Change

In this laboratory, reloading PJSIP did not activate the new UDP transport. A full restart resolved the issue.

```bash
sudo systemctl restart asterisk
```

Check the service:

```bash
sudo systemctl status asterisk
```

Note: Restarting Asterisk can interrupt active calls. Do not do this on a production system without planning for the interruption.

## 3. Verify SIP Transport

```bash
sudo asterisk -rx "pjsip show transports"
```

Expected configuration includes a UDP transport bound to port 5060.

## 4. Verify Endpoints

```bash
sudo asterisk -rx "pjsip show endpoints"
```

Inspect an individual endpoint:

```bash
sudo asterisk -rx "pjsip show endpoint 101"
```

Repeat for extensions 102 and 103.

## 5. Verify Registered Contacts

```bash
sudo asterisk -rx "pjsip show contacts"
```

A registered client should appear as a contact.

## 6. Enable SIP Logging

Open the Asterisk CLI:

```bash
sudo asterisk -rvvv
```

Enable SIP message logging:

```text
pjsip set logger on
```

Disable logging when finished:

```text
pjsip set logger off
```

Avoid sharing logs publicly without reviewing them for IP addresses, account names, or other sensitive information.

## Extension 101 - On Zoiper (you can use any soft call software)

| Setting       | Value                                 |
| ------------- | ------------------------------------- |
| Application   | Zoiper                                |
| Username      | 101                                   |
| Password      | Password configured for extension 101 |
| Domain / Host | `192.168.1.135`                       |
| Port          | `5060`                                |
| Transport     | UDP                                   |

## Extension 102 - On MicroSIP

| Setting      | Value                                 |
| ------------ | ------------------------------------- |
| Application  | MicroSIP                              |
| SIP Server   | `192.168.1.135`                       |
| SIP Proxy    | `192.168.1.135:5060`                  |
| Username     | 102                                   |
| Login        | 102                                   |
| Password     | Password configured for extension 102 |
| Domain       | `192.168.1.135`                       |
| Display Name | 102                                   |
| Transport    | UDP                                   |
