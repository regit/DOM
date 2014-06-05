==================
Deny On Monitoring
==================

Introduction
============

DOM is a proof of concept implementing a solution similar to fail2ban. It parses Suricata EVE log file
searching for SSH event. If the client version is based on libssh, it adds the host to a blacklist
by using ipset.

Running DOM
===========

Go into the source directory and run ::

 ./dom -f /usr/local/var/log/suricata/eve.json

Full options are available via '-h' option ::

 usage: dom [-h] [-f FILE] [-s IPSET] [-v] [-l LOG] [-D]
 
 Deny On Monitoring
 
 optional arguments:
   -h, --help            show this help message and exit
   -f FILE, --file FILE  JSON file to monitor
   -s IPSET, --ipset IPSET
                         Set IPSET for blacklist
   -v, --verbose         Show verbose output, use multiple times increase
                         verbosity
   -l LOG, --log LOG     File to log output to (default to stdout)
   -D, --daemon          Run as unix daemon
 
