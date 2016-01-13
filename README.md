## Synopsis

`keepasswd` is designed to join together your KeePass database and password management. keepasswd has an initial goal to support changing SSH passwords, with an eventual goal of a pluggable interface to allow changing items like Windows, database or web passwords.


## Code Example

    keepasswd --account user2@localhost --config ./config

`keepass` will attempt to connect to localhost as user2 using the password in the KeePass database, generate a new password, change the user's password, and save it back to the KeePass database if the operation was successful.

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

For RPM-based systems, you'll need perl,perl-File-KeePass,perl-Config-Tiny, IPC::Run as well as the sshchpasswd.exp available at:
https://github.com/jsmoriss/sshchpwd

Then git clone the project and set up a configure file for the KeePass database you want to use.

The config file supports the following options:  
	password=	password to the KeePass DB [required]  
	dbfile=		full path to the kdb file [optional]  
	dbkey=		full path to the key file for the kdb [optional]  
	sshchpasswd=	full path to the sshchpasswd script you plan to use [required for ssh]  
	group=		default group to search [optional]  

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
