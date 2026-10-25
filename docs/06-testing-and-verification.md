# VoIP Testing and Verification

## 1. Verify Asterisk

```bash
sudo systemctl is-active asterisk
```

Expected result:

```text
active
```

## 2. Verify SIP Transport

```bash
sudo asterisk -rx "pjsip show transports"
```

Confirm that the UDP transport is available.

## 3. Verify SIP Contacts

```bash
sudo asterisk -rx "pjsip show contacts"
```

Confirm that the expected SIP clients are registered.

## 4. Verify Dialplan

```bash
sudo asterisk -rx "dialplan show internal"
```

Expected extensions:

* 101
* 102
* 103

## 5. Call Testing Matrix

| Test | Caller         | Receiver       | Status            |
| ---- | -------------- | -------------- | ----------------- |
| 1    | 101 — Zoiper   | 102 — MicroSIP | PASS              |
| 2    | 102 — MicroSIP | 101 — Zoiper   | PASS|
| 3    | 101            | 103            | Pending           |
| 4    | 103            | 101            | Pending           |
| 5    | 102            | 103            | Pending           |
| 6    | 103            | 102            | Pending           |

## 6. Audio Verification

For every successful call:

1. Confirm that the receiver rings.
2. Answer the call.
3. Confirm that audio travels from caller to receiver.
4. Confirm that audio travels in the reverse direction.
5. End the call.
6. Review Asterisk CLI output if the call fails.

A successful SIP call setup does not automatically prove that two-way RTP audio works correctly.

## 7. Record Results

Update the testing matrix only after performing each test. Record the result, the problem encountered, and the solution if a test fails.
