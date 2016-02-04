Zimbra ownCloud Zimlet
==========

If you find Zimbra ownCloud Zimlet useful and want to support its continued development, you can make donations via:
- PayPal: info@barrydegraaff.tk
- Bank transfer: IBAN NL55ABNA0623226413 ; BIC ABNANL2A

Demo video: https://www.youtube.com/watch?v=gfVLE22kJ6o

User manual : http://barrydegraaff.github.io/owncloud/

Integrating ownCloud in Zimbra Collaboration Suite, currently tested on:
- Windows: Internet Explorer 11, Microsoft Edge, Google Chrome, Firefox
- Linux: Google Chrome, Firefox

This Zimlet is designed for Zimbra version 8.6.

This Zimlet is not available for use in Zimbra Desktop.

Bugs and feedback: https://github.com/Zimbra-Community/owncloud-zimlet/issues

========================================================================

### Install prerequisites
  - A running Zimbra server
  - A running ownCloud server

For fresh ownCloud installs I recommend to use the [official repository](https://download.owncloud.org/download/repositories/stable/owncloud/).

### Install the ownCloud Zimlet
The recommended method is to deploy using git.

    # apt-get -y install git
    # git clone https://github.com/btactic/owncloud-zimlet.git
    # cd owncloud-zimlet
    # chmod +rx build.sh
    # su - zimbra
    $ zmzimletctl deploy tk_barrydegraaff_owncloud_zimlet.zip
    $ zmcontrol restart

### Configure your ownCloud Server

Add the following lines in .htaccess of owncloud installation:
NOTE: `example.com` must be the Zimbra domain where the owncloud will be accessed.
```
<IfModule mod_headers.c>
    <IfModule mod_env.c>
        # ownCloud zimlet
        Header always set Access-Control-Allow-Origin "https://example.com"
        Header always set Access-Control-Allow-Headers "Authorization, Content-type, depth"
        Header always set Access-Control-Allow-Methods "MKCOL, PROPFIND, PUT"
    </IfModule>
</IfModule>

<IfModule mod_rewrite.c>
    # ownCloud zimlet
    RewriteCond %{REQUEST_METHOD} OPTIONS
    RewriteRule ^(.*)$ $1 [R=200,L]
</IfModule>
```

If you want to enable link sharing add a php file to you ownCloud installation:

    $ cd public_html/ocs/
    $ wget https://raw.githubusercontent.com/btactic/owncloud-zimlet/btactic/php/zcs.php

IMPORTANT: if this steps are not followed the owncloud zimlet does not work properly. All the installations that users will use must be configured following this steps.





========================================================================

### License

Copyright (C) 2015-2016  Barry de Graaff

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see http://www.gnu.org/licenses/.
