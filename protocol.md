## Protocol
All commands are case insensitive.
#### DSET server
Command to set default server

* Arguments
    * POP3 server to be used as a default server for all incoming connections
* Restrictions
    * Server must be a valid address
* Possible responses
    * +OK
    * -ERR message
* Examples
```
...
C: DSET mail.google.com
S: +OK
...
C: DSET
S: -ERR usage: DSET defaultServer
```
#### USET user server
Command to set the POP3 server to use for a specific user.
* Arguments
    * User to modify
    * POP3 server to set for given user
* Restrictions
    * Server must be a valid address.
* Possible responses
    * +OK
    * -ERR message
* Examples
```
...
C: USET johndoe mail.example.com
S: +OK
...
C: USET example
S: -ERR usage: USET defaultServer
...
C: USET
S: -ERR usage: USET defaultServer
```
#### UDEL user
Command to remove a server exception for a given user and return that user to the default server.
* Arguments
    * User to remove exception
* Restrictions
    * None
* Possible responses
    * +OK
    * -ERR message
* Examples
```
...
C: UDEL johndoe
S: +OK
...
C: UDEL
S: -ERR usage: UDEL defaultServer
```
#### LSET
Command to toggle l33t mode in subject.
* Arguments
    * true or false
* Restrictions
    * None
* Possible responses
    * +OK
    * -ERR message
* Examples
```
...
C: LSET true
S: +OK
...
C: LSET false
S: +OK
...
C: LSET
S: -ERR usage: LSET true or false
```
#### ISET
Command to toggle image rotation.
* Arguments
    * true or false
* Restrictions
    * None
* Possible responses
    * +OK
    * -ERR message
* Examples
```
...
C: ISET true
S: +OK
...
C: ISET false
S: +OK
...
C: ISET
S: -ERR usage: ISET true or false
```
#### CGET
Command to print current loaded configuration.
* Arguments
    * None
* Restrictions
    * None
* Possible responses
    * +OK
    * -ERR message
* Examples
```
...
C: CGET
S: +OK
CONF defaultServer example.com
CONF imageFlip true
CONF leetMode false
CONF serverExceptions none
...
C: CGET
S: +OK
CONF defaultServer example.com
CONF imageFlip true
CONF leetMode true
CONF serverExceptions johndoe@example.com,janedoe@megaserver.net
...
```
#### STAT
Command to print current stats.
* Arguments
    * None
* Restrictions
    * None
* Possible responses
    * +OK
    * -ERR message
* Examples
```
...
C: STAT
S: +OK
STAT input_bytes 432323
STAT output_bytes 412312
STAT leet_letters 423
STAT roated_images 2
...
```
#### HELP
Prints available commands, their information and usage
* Arguments
    * None
* Restrictions
    * None
* Possible responses
    * +OK
    * -ERR message
* Examples
```
...
C: HELP
S: OK
HELP
  Show this help
UDEL username
  Delete server override for given user
STAT
  Display proxy statistics
LSET true or false
  Enable or disable l33t mail title mode
USET username domain
  Add server override for given user
ISET true or false
  Enable or disable image flip
CGET
  Show current configuration parameters
DSET defaultServer
  Set default POP3 server
...
```
