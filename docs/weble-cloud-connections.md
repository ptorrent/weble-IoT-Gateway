# Connections
## VNC

The VNC protocol is the simplest and first protocol supported by Guacamole. Although generally not as fast as RDP, many VNC servers are adequate, and VNC over Guacamole tends to be faster than VNC by itself due to decreased bandwidth usage.

VNC support for Guacamole is provided by the libguac-client-vnc library, which will be installed as part of guacamole-server if the required dependencies are present during the build.

### Network parameters

With the exception of reverse-mode VNC connections, VNC works by making outbound network connections to a particular host which runs one or more VNC servers. Each VNC server is associated with a display number, from which the appropriate port number is derived.

hostname
The hostname or IP address of the VNC server Guacamole should connect to.

port
The port the VNC server is listening on, usually 5900 or 5900 + display number. For example, if your VNC server is serving display number 1 (sometimes written as :1), your port number here would be 5901.

autoretry
The number of times to retry connecting before giving up and returning an error. In the case of a reverse connection, this is the number of times the connection process is allowed to time out.

## RDP
