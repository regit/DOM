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

Go into the source directory and run: ::

 ./dom -f /usr/local/var/log/suricata/eve.json

Full options are available via '-h' option: ::

 usage: dom [-h] [-f FILE] [-s IPSET] [-v] [-l LOG] [-m MOTIF] [-i] [-D]
 
 Deny On Monitoring
 
 optional arguments:
   -h, --help            show this help message and exit
   -f FILE, --file FILE  JSON file to monitor
   -s IPSET, --ipset IPSET
                         Set IPSET for blacklist
   -v, --verbose         Show verbose output, use multiple times increase
                         verbosity
   -l LOG, --log LOG     File to log output to (default to stdout)
   -m MOTIF, --motif MOTIF
                         String to look for in event
   -i, --invert          Invert match: trigger action if not found
   -D, --daemon          Run as unix daemon

If you know that regular client are using a software client (like OpenSSH) then
you can use motif and invert options to trigger an action on all client not using
this software: ::

 ./dom -f /usr/local/var/log/suricata/eve.json -i -m OpenSSH
