notracking
==========

Pull the latest blocklists from https://github.com/notracking/hosts-blocklists,
verify them, and install them.

Usage
-----

Clone this repository to a directory on your system:

    git clone git://github.com/bahamas10/notracking.git
    cd notracking

Run the `update` command, this will:

1. pull the latest `hostnames.txt` and `domains.txt` files to a temporary file
in the current directory
2. Validate them using the `validate` script (ensure the lines are well formed
and the IPs are only `::` or `0.0.0.0`)
3. Move them from their temporary file to `hostnames.txt` and `domains.txt` respectively
4. Optionally run a command after this is done given as arguments

Example:

     # ./update svcadm -v restart dnsmasq
     Sun Jul  8 11:43:19  2018
     pulling latest domains list (https://raw.githubusercontent.com/notracking/hosts-blocklists/master/domains.txt)
     validating domains list (domains.txt.tmp)
     installing domains list: /home/dave/dev/notracking/domains.txt
     pulling latest hostnames list (https://raw.githubusercontent.com/notracking/hosts-blocklists/master/hostnames.txt)
     validating hostnames list (hostnames.txt.tmp)
     installing hostnames list: /home/dave/dev/notracking/hostnames.txt
     running: svcadm -v restart dnsmasq
     Action restart set for svc:/pkgsrc/dnsmasq:default.
     finished running - code: 0
     done.  took 2 seconds


Any arguments to `./update` will be run after the files are updated and put in
place - this is optional.

Dependencies
------------

[Node.JS](https://nodejs.org/en/) must be installed for the `validate` script to work.

License
--------

MIT License
