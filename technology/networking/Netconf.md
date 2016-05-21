#  Network 

https://www.youtube.com/watch?v=9pbzLcN9QGw

# NetConf

## Design
* People spend lots of time in CLI
* Netconf protocol + Yang lang
* Comes from IETF - Standard
* protocol to manipulate configuration
* not designed to replace SNMP
* Big distinction between config and state data

## feature
* can do conf change validations
* can do transactions
* filter config data
* partial dumps
* stream playback notifications
* can define own commands
* fundamental programming features for any automation
* two-phase commits
* distributed transactions
  * connect and lock to R1, R2, R3
  * edit candidate db and commit w/ timeout
  * do assurance checks during timeout
  * confirm commit, copy to startup and release locks
  * If anything happens, then cancel client, and then box will revert to previous state
  
  
## model
* Layer:  Conent -> Operations -> RPC -> Transport Protocol
* NETCONF: Config data -> get/get-config -> rpc -> ssh, tls, etc.
* Three conceptual databases
  * candidate - (optional) working copy for manipulating config data with no impact
  * running - represents complete and active config
  * startup (optional) - loaded by device when boots
* common ops
  * get, get-config, edit-config, copy-config, delete-config, discard-changes, lock, unlock, commit, cancel-commit, get-schema, rpc, close-session, kill-session
* can extend with "ping", "reboot"
* Code example: https://youtu.be/9pbzLcN9QGw?t=865
* Code Bindings: Ruby, Go, Python, Perl, Java
* Could build entire systems on it

## YANG
* Data modeling for Networking
* human readable
* Example: https://youtu.be/9pbzLcN9QGw?t=1187
* reusable types and groupings
* full and formal contract language
* Can ask network element:  "What do you support?"  "IP"


## Other
* RFC 6244
* OpenFlow? Netconf is protocol that acts with semantics, but acts above the driver layer.  https://youtu.be/9pbzLcN9QGw?t=1470
* $PROTO? Netconf provides transport binding, and data modeling, If you use REST, then you have to invent yourself.
* Open Daylight is based upon YANG
