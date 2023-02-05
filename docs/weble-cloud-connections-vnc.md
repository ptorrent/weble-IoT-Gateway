# Connections
## VNC

The VNC protocol is the simplest and first protocol supported by Guacamole. Although generally not as fast as RDP, many VNC servers are adequate, and VNC over Guacamole tends to be faster than VNC by itself due to decreased bandwidth usage.

VNC support for Guacamole is provided by the libguac-client-vnc library, which will be installed as part of guacamole-server if the required dependencies are present during the build.

### Network parameters

With the exception of reverse-mode VNC connections, VNC works by making outbound network connections to a particular host which runs one or more VNC servers. Each VNC server is associated with a display number, from which the appropriate port number is derived.

#### hostname
The hostname or IP address of the VNC server Guacamole should connect to.

#### port
The port the VNC server is listening on, usually 5900 or 5900 + display number. For example, if your VNC server is serving display number 1 (sometimes written as :1), your port number here would be 5901.

#### autoretry
The number of times to retry connecting before giving up and returning an error. In the case of a reverse connection, this is the number of times the connection process is allowed to time out.

### Authentication

The VNC standard defines only password based authentication. Other authentication mechanisms exist, but are non-standard or proprietary. Guacamole currently supports both standard password-only based authentication, as well as username and password authentication.

#### username
The username to use when attempting authentication, if any. This parameter is optional.

#### password
The password to use when attempting authentication, if any. This parameter is optional.

### Display settings

VNC servers do not allow the client to request particular display sizes, so you are at the mercy of your VNC server with respect to display width and height. However, to reduce bandwidth usage, you may request that the VNC server reduce its color depth. Guacamole will automatically detect 256-color images, but this can be guaranteed for absolutely all graphics sent over the connection by forcing the color depth to 8-bit. Color depth is otherwise dictated by the VNC server.

If you are noticing problems with your VNC display, such as the lack of a mouse cursor, the presence of multiple mouse cursors, or strange colors (such as blue colors appearing more like orange or red), these are typically the result of bugs or limitations within the VNC server, and additional parameters are available to work around such issues.

#### color-depth
The color depth to request, in bits-per-pixel. This parameter is optional. If specified, this must be either 8, 16, 24, or 32. Regardless of what value is chosen here, if a particular update uses less than 256 colors, Guacamole will always send that update as a 256-color PNG.

#### swap-red-blue
If the colors of your display appear wrong (blues appear orange or red, etc.), it may be that your VNC server is sending image data incorrectly, and the red and blue components of each color are swapped. If this is the case, set this parameter to “true” to work around the problem. This parameter is optional.

#### cursor
If set to “remote”, the mouse pointer will be rendered remotely, and the local position of the mouse pointer will be indicated by a small dot. A remote mouse cursor will feel slower than a local cursor, but may be necessary if the VNC server does not support sending the cursor image to the client.

#### encodings
A space-delimited list of VNC encodings to use. The format of this parameter is dictated by libvncclient and thus doesn’t really follow the form of other Guacamole parameters. This parameter is optional, and libguac-client-vnc will use any supported encoding by default.

Beware that this parameter is intended to be replaced with individual, encoding-specific parameters in a future release.

#### read-only
Whether this connection should be read-only. If set to “true”, no input will be accepted on the connection at all. Users will only see the desktop and whatever other users using that same desktop are doing. This parameter is optional.

#### force-lossless
Whether this connection should only use lossless compression for graphical updates. If set to “true”, lossy compression will not be used. This parameter is optional. By default, lossy compression will be used when heuristics determine that it would likely outperform lossless compression.
