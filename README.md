## Synopsis

`keepasswd` is designed to join together your KeePass database and password management. keepasswd has an initial goal to support changing SSH passwords, with an eventual goal of a pluggable interface to allow changing items like Windows, database or web passwords.


## Code Example

    keepasswd --account user2@localhost --config ./config

`keepasswd` will attempt to connect to localhost as user2 using the password in the KeePass database, generate a new password, change the user's password, and save it back to the KeePass database if the operation was successful.

## KeePass Entry Example

    Title: user@www1
    URL: ssh://user@172.30.25.9
    User: user
    Server: server
    Password: userpassword

`keepasswd` pulls from the URL portion of the entry to connect.  

On the command line you could specify the title, `--account user@www1`, but the script would connect to user@172.30.25.9 .


## Motivation

The creation of this was motivated by the frustration of changing passwords on multiple systems.

## Installation

For RPM-based systems, you'll need perl,expect,perl-File-KeePass,perl-Config-Tiny, IPC::Run as well as the sshchpwd.exp available at:
https://github.com/jsmoriss/sshchpwd

Then git clone the project and set up a configure file for the KeePass database you want to use.

The config file supports the following settings:

The following config file setting is required:

    password=	password to the KeePass DB 
The following config file settings must be specified either in the config file or as command line arguments:  

    dbfile=		full path to the kdb file
    account=	entry title to search for
    group=		default group to search
    openssl=	full path to openssl executable
    sshchpwd=	full path to the sshchpwd script you plan to use
    sshverifypwd=	full path to the sshverifypwd script you plan to use

The following config file settings are optional, but can be specified on the CLI as well:  

    dbkey=		full path to the key file


## Usage

The three main actions are to change (default), verifyonly (via the --verifyonly flag), and rotate-expired (not yet implemented)

An example to rotate a password, with the settings for password, dbfile, group, openssl, sshchpwd, sshverifypwd in the config file:

    keepasswd --account user2@localhost --config ./config

An example that's mostly CLI based, with only the password in the dbfile:

    keepasswd --verifyonly --account user2@localhost --dbfile ./db.kdb --dbkey ./db.key --group cust1 --openssl `which openssl` --sshchpwd ./sshchpasswd.exp --sshverifypwd ./sshverifypwd.exp --config ./keepasswd.config

An example that only verifies:

    keepasswd --verifyonly --account someuser@remote --config ~/keepasswd.config

CLI options will take precedence over the config file options.

## Contributors

Submit bugs or feature requests to the github project page!

## License

The MIT License (MIT)

Copyright (C) 2016 Jodie Cunningham

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
