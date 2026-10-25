# /etc/asterisk/pjsip.conf

#

## Sanitized reference configuration.

## Replace each CHANGE_ME placeholder on the PBX server

## with a strong, unique SIP password before use.

[transport-udp]
type=transport
protocol=udp
bind=0.0.0.0:5060

; =========================
; EXTENSION 101
; =========================

[101]
type=endpoint
context=internal
disallow=all
allow=ulaw
auth=101-auth
aors=101
max_contacts=1

[101-auth]
type=auth
auth_type=userpass
username=101
password=CHANGE_ME_101

[101]
type=aor
max_contacts=1

; =========================
; EXTENSION 102
; =========================

[102]
type=endpoint
context=internal
disallow=all
allow=ulaw
auth=102-auth
aors=102
max_contacts=1

[102-auth]
type=auth
auth_type=userpass
username=102
password=CHANGE_ME_102

[102]
type=aor
max_contacts=1

; =========================
; EXTENSION 103
; =========================

[103]
type=endpoint
context=internal
disallow=all
allow=ulaw
auth=103-auth
aors=103
max_contacts=1

[103-auth]
type=auth
auth_type=userpass
username=103
password=CHANGE_ME_103

[103]
type=aor
max_contacts=1
