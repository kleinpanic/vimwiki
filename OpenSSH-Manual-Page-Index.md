# OpenSSH Manual Pages 

## SSH(1) 
ssh - OpenSSH remote login client. 

ssh is a program for logging ito a remote machine and for executing commands on a remote machine. It is intended to provide secure encrypted communications between untrusted hosts over an insecure network. X11 connections, arbitrary TCP ports, ad UNIX-domain sockets can also be forwarded over the same secure channel. 

ssh connects and logs into the specified destination which is specified as either [user@]hostname or a url of the form ssh://[user@]hostname[:port]. The user must provde their indentiy to the remote machine using one of the several methods (see below). 
If a command is specified it will be executed on the remote host instead of a login shell. A complete command line may be spefieid as a commad, or it may have additional arguments. if supplied, the arguments will be appended to the command, seperated by spaces, before it is sent to the server to be executed. 

### Possible Options 
- 4: Force IPv4 address usage on SSH 
- 6: Forces SSH to use IPv6. 
