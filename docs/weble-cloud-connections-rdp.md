# RDP

## Authentication and security

RDP provides authentication through the use of a username, password, and optional domain. All RDP connections are encrypted.

Most RDP servers will provide a graphical login if the username, password, and domain parameters are omitted. One notable exception to this is Network Level Authentication, or NLA, which performs all authentication outside of a desktop session, and thus in the absence of a graphical interface.

Servers that require NLA can be handled by Guacamole in one of two ways. The first is to provide the username and password within the connection configuration, either via static values or by passing through the Guacamole credentials with parameter tokens and LDAP authentication. Alternatively, if credentials are not configured within the connection configuration, Guacamole will attempt to prompt the user for the credentials interactively, if the versions of both guacd and Guacamole Client in use support it. If either component does not support prompting and the credentials are not configured, NLA-based connections will fail.

### username
The username to use to authenticate, if any. This parameter is optional.

### password
The password to use when attempting authentication, if any. This parameter is optional.

### domain
The domain to use when attempting authentication, if any. This parameter is optional.

### security
The security mode to use for the RDP connection. This mode dictates how data will be encrypted and what type of authentication will be performed, if any. By default, a security mode is selected based on a negotiation process which determines what both the client and the server support.

Possible values are:

#### any
Automatically select the security mode based on the security protocols supported by both the client and the server. This is the default.

#### nla
Network Level Authentication, sometimes also referred to as “hybrid” or CredSSP (the protocol that drives NLA). This mode uses TLS encryption and requires the username and password to be given in advance. Unlike RDP mode, the authentication step is performed before the remote desktop session actually starts, avoiding the need for the Windows server to allocate significant resources for users that may not be authorized.

If the versions of guacd and Guacamole Client in use support prompting and the username, password, and domain are not specified, the user will be interactively prompted to enter credentials to complete NLA and continue the connection. Otherwise, when prompting is not supported and credentials are not provided, NLA connections will fail.

#### nla-ext
Extended Network Level Authentication. This mode is identical to NLA except that an additional “Early User Authorization Result” is required to be sent from the server to the client immediately after the NLA handshake is completed.

#### tls
RDP authentication and encryption implemented via TLS (Transport Layer Security). Also referred to as RDSTLS, the TLS security mode is primarily used in load balanced configurations where the initial RDP server may redirect the connection to a different RDP server.

#### vmconnect
Automatically select the security mode based on the security protocols supported by both the client and the server, limiting that negotiation to only the protocols known to be supported by Hyper-V / VMConnect.

#### rdp
Legacy RDP encryption. This mode is generally only used for older Windows servers or in cases where a standard Windows login screen is desired. Newer versions of Windows have this mode disabled by default and will only accept NLA unless explicitly configured otherwise.

#### ignore-cert
If set to “true”, the certificate returned by the server will be ignored, even if that certificate cannot be validated. This is useful if you universally trust the server and your connection to the server, and you know that the server’s certificate cannot be validated (for example, if it is self-signed).

#### disable-auth
If set to “true”, authentication will be disabled. Note that this refers to authentication that takes place while connecting. Any authentication enforced by the server over the remote desktop session (such as a login dialog) will still take place. By default, authentication is enabled and only used when requested by the server.

If you are using NLA, authentication must be enabled by definition.

## Session settings

### server-layout

The server-side keyboard layout. This is the layout of the RDP server and has nothing to do with the keyboard layout in use on the client. The Remote services client is independent of keyboard layout. The RDP protocol, however, is not independent of keyboard layout, and Remote services needs to know the keyboard layout of the server in order to send the proper keys when a user is typing.

Possible values are generally in the format LANGUAGE-REGION-VARIANT, where LANGUAGE is the standard two-letter language code for the primary language associated with the layout, REGION is a standard representation of the location that the keyboard is used (the two-letter country code, when possible), and VARIANT is the specific keyboard layout variant (such as “qwerty”, “qwertz”, or “azerty”):

### Keyboard layout

Brazilian (Portuguese) pt-br-qwerty
English (UK) en-gb-qwerty
English (US) en-us-qwerty
French fr-fr-azerty
French (Belgian) fr-be-azerty
French (Swiss) fr-ch-qwertz
German de-de-qwertz
German (Swiss) de-ch-qwertz
Hungarian hu-hu-qwertz
Italian it-it-qwerty
Japanese ja-jp-qwerty
Norwegian no-no-qwerty
Spanish es-es-qwerty
Spanish (Latin American) es-latam-qwerty
Swedish sv-se-qwerty
Turkish-Q tr-tr-qwerty

If you server’s keyboard layout is not yet supported, and it is not possible to set your server to use a supported layout, the failsafe layout may be used to force Unicode events to be used for all input, however beware that doing so may prevent keyboard shortcuts from working as expected. timezone

### enable-drive

File transfer is disabled by default, but with file transfer enabled, RDP users can transfer files to and from a virtual drive which persists on the Remote services server. Enable file transfer support by setting this parameter to “true”.
Files will be stored in the directory specified by the “drive-path” parameter, which is required if file transfer is enabled.

### disable-download

If set to true downloads from the remote server to client (browser) will be disabled. This includes both downloads done via the hidden Remote services menu, as well as using the special “Download” folder presented to the remote server. The default is false, which means that downloads will be allowed.
If file transfer is not enabled, this parameter is ignored.

### disable-upload

If set to true, uploads from the client (browser) to the remote server location will be disabled. The default is false, which means uploads will be allowed if file transfer is enabled.
If file transfer is not enabled, this parameter is ignored.

### drive-name

The name of the filesystem used when passed through to the RDP session. This is the name that users will see in their Computer/My Computer area along with client name (for example, “Remote services on Remote services RDP”), and is also the name of the share when accessing the special \tsclient network location.
If file transfer is not enabled, this parameter is ignored.
