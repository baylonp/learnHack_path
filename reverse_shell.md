
# What are we doing here?
 
 
So basically, when you want to connect to a remote PC or server or something remote that goes online you can use a **bind shell**. You are the one asking :
_
"Hey , can I connect to you?"_

Most of the times, because of firewall, for example if an attacker wants to connect to a remote server behind a firewall of a company, it does not works. 
The connection gets dropped because the traffic is not legitimate. Also beacuse the server could just expose few ports and there is already traffic through them.

The option an attacker has it to create a **REVERSE SHELL** (thunders + grave and dark voice)



# What the hell is a reverse shell?


The big difference is that now it is not the attacker anymore the one who asks if he can connect. Now is the target PC or target server which says: 

_"Let me connect to you, you ol' dirty bastard"_


Let me explain how it is done. 



First of all is already given that the target has somehow downloaded a malicious file containing a script or something that gets executed. This script makes the target PC on which is executed establish a connection to the attacker. This way there is a higher chance that the firewall will let the connection pass through givent that is outbound traffic.

[ATTACKER]<-------Let me connect to you----[TARGET]

The ATTACKER though has to setup a listener on his machine. This way the TARGET can coonect.
This is done via a listener, a piece of software as **Netcat** that can listen on a specified port.


For what I've been playing with so far, what I did on the ATTACKER machine was just setup netcat to listen on a port. I used this command:

`netcat -lnvp 8000`

I notice other tutorials use `-s SOURCE_IP`, but I don't need it since I got just one interface

Let's go through each flag

`-l` tells netcat to: 
>Listen for an incoming connection rather than initiating a connection to a remote host.

`-n` tells netcat to:
>Do not perform domain name resolution.  If a name cannot be resolved without DNS, an error will be reported.

`-v` tells netcat to be verbose

`-p` let us specify the port to start listening on



