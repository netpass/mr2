# Mr.2

[中文](README_ZH.md)

[![Build Status](https://travis-ci.org/txthinking/mr2.svg?branch=master)](https://travis-ci.org/txthinking/mr2) [![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](http://www.gnu.org/licenses/gpl-3.0)
[![Donate](https://img.shields.io/badge/Support-Donate-ff69b4.svg)](https://www.txthinking.com/opensource-support.html)
[![Slack](https://img.shields.io/badge/Join-Slack-ff69b4.svg)](https://docs.google.com/forms/d/e/1FAIpQLSdzMwPtDue3QoezXSKfhW88BXp57wkbDXnLaqokJqLeSWP9vQ/viewform)

## What is Mr.2

Mr.2 can help you expose local server to external network. Support both TCP/UDP, of course support HTTP. Keep it **simple**, **stupid**.

### Install via [nami](https://github.com/txthinking/nami)

```
$ nami install github.com/txthinking/mr2
```

or download from [releases](https://github.com/txthinking/mr2/releases)

### Server

    $ mr2 server -l :9999 -p password

    # Only allow partial ports, and set password on each port
    $ mr2 server -l :9999 -P '5678 password' -P '6789 password1'

### Client

    # Local server is 127.0.0.1:1234, expect to expose: server_address:5678
    $ mr2 client -s server_address:port -p password -P 5678 -c 127.0.0.1:1234

    # Local web root is /path/to/www, expect to expose: server_address:5678
    $ mr2 client -s server_address:port -p password -P 5678 --clientDirectory /path/to/www

### Example

#### Access local HTTP server

    $ mr2 client -s server_address:port -p password -P 5678 -c 127.0.0.1:8080

    # then
    Your HTTP server in external network is: server_address:5678

#### SSH into local computer

    $ mr2 client -s server_address:port -p password -P 5678 -c 127.0.0.1:22

    # then
    $ ssh -oPort=5678 user@server_address

#### Access local DNS server

    $ mr2 client -s server_address:port -p password -P 5678 -c 127.0.0.1:53

    # then
    Your DNS server in external network is: server_address:5678

    $ dig github.com @server_address -p 5678

#### Access your local directory via HTTP

    $ mr2 client -s server_address:port -p password -P 5678 --clientDirectory /path/to/www

    # then
    A HTTP server in external network is: server_address:5678

#### Any TCP-based/UDP-based ideas you think of

...

## Contributing

Please read [CONTRIBUTING.md](https://github.com/txthinking/mr2/blob/master/.github/CONTRIBUTING.md) first

## License

Licensed under The GPLv3 License
