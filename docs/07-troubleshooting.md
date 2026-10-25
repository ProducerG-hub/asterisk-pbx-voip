# Asterisk VoIP Troubleshooting

## Problem 1: SIP Transport Was Not Available

### Symptom

The command:

```text
pjsip show transports
```

returned:

```text
No objects found.
```

### Investigation

The UDP transport configuration was present in `pjsip.conf`, but the transport was not available after a PJSIP reload.

### Resolution

Restarted Asterisk:

```bash
sudo systemctl restart asterisk
```

Then verified:

```bash
sudo asterisk -rx "pjsip show transports"
```

The UDP transport became available.

### Lesson

Some transport configuration changes may require a complete Asterisk restart in this environment.

---

## Problem 2: Windows and Ubuntu Were on Different Subnets

### Symptom

The Ubuntu virtual machine initially used a VMware NAT address from a different subnet than the Windows host.

### Resolution

Changed the VMware network adapter from NAT to Bridged.

Verified the resulting network address and connectivity.

### Lesson

The network mode must be appropriate for the intended SIP client connectivity.

---

## Problem 3: Extension 103 Authentication Configuration

### Symptom

Extension 103 initially referenced the authentication object for extension 102.

### Resolution

Corrected the endpoint to reference its own authentication object:

```ini
auth=103-auth
```

The authentication object must also use:

```ini
username=103
```

### Lesson

Each endpoint should reference the correct authentication object and AOR.

---

## Useful Diagnostic Commands

Check service status:

```bash
sudo systemctl status asterisk
```

Check UDP port 5060:

```bash
sudo ss -lunp | grep 5060
```

Check endpoints:

```bash
sudo asterisk -rx "pjsip show endpoints"
```

Check contacts:

```bash
sudo asterisk -rx "pjsip show contacts"
```

Check transport:

```bash
sudo asterisk -rx "pjsip show transports"
```

Check dialplan:

```bash
sudo asterisk -rx "dialplan show internal"
```

Open Asterisk CLI:

```bash
sudo asterisk -rvvv
```

Enable PJSIP logging in the CLI:

```text
pjsip set logger on
```
