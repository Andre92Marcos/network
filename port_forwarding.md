# Port Forwarding

## Local port forwarding

	ssh -L local_port:remote_host:remote_port

	Let's say that we have a remote host running an application on port 4444, that only accepts local connections. We can port forward to our localhost by doing this in our localhost
	ssh <user>@<ip_remote_host> -L 4444:127.0.0.1:4444

	The -L command tells the SSH client to request the SSH server to forward all the data we send via the port 4444 to localhost:4444

## Remote port forwarding

	ssh -R remote_port:local_host:local_port


## Socat

We can use socat for this

	socat TCP4-LISTEN:5001,fork TCP4:localhost:5000

This sends all incoming traffic in port 5001 to 5000
Can be used with the previous ssh command


## Port forwarding with SOCKS5

We can use ssh -D 1080 to use a dynamic socks5 port.

Then if we connect to the port (for instance using foxy proxy on port 1080) we can access to the ports on the remote server.

In the command line we can use proxychains (need to check config /etc/proxychains.conf)

## Tool for windows and Linux

	chisel: https://github.com/Andre92Marcos/tools/tree/master/chisel

