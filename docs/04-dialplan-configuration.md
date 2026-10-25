# Internal extension dialplan

#

## This is the relevant custom context from:

## /etc/asterisk/extensions.conf

[internal]

exten => 101,1,Dial(PJSIP/101,20)
exten => 102,1,Dial(PJSIP/102,20)
exten => 103,1,Dial(PJSIP/103,20)

This means enables asterisk to direct the particular call to an intended extension and the call may ring for 20 seconds

## NB: The file may contain default configurations so review it before replacing