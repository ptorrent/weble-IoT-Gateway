# RDP

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
