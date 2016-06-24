# Puppet Nagios Checks

Spot to put my puppet nagios checks.  Available for use 'as-is'.

## checks/check_puppet_nodes.py

Checks the status of a puppet environmnet, providing a summary or detailed version of the current state.

Usage:
```
Usage: check_puppet_nodes.py [options]

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -H HOSTNAME, --hostname=HOSTNAME
                        The PuppetDB hostname (fqdn). eg: dev-
                        puppetmaster-01.serv.abb.ixa.net.au
  -l LOGLEVEL, --loglevel=LOGLEVEL
                        Valid log levels: CRITICAL, ERROR, WARNING, INFO,
                        DEBUG. Defaults to INFO.
  -p PORT, --port=PORT  The PuppetDB port. Defaults to 8080
  -s, --summary         Print summary - just the numbers (not host details)
  -d, --detailed        Print details - inlcudes host details
  -w WARNING_THRESHOLD, --warning=WARNING_THRESHOLD
                        Warning if <num> hosts are failing
  -c CRITICAL_THRESHOLD, --critical=CRITICAL_THRESHOLD
                        Critical if <num> hosts are failing
  -f, --fqdn            Show FQDN for hostname, instead of short hostnames.
                        Default is short hostname.
  -m MAX_HOSTS, --max-hosts=MAX_HOSTS
                        Maximum number of host names to display per state.
                        Default is 5.
```

Sample output from `summary` mode:
```
CRITICAL:: Total nodes=23, Changed=14, Failed=2, Noop=0, Unchanged=7, Unreported=0, Unresponsive=0,
```


Sample output from `detailed` mode:
```
CRITICAL:: Total nodes=23, Changed=2 host-01 host-02, Failed=1 test-host-01, Noop=0, Unchanged=20 dev-host-01 prod-host-01 dev-host-02 dev-host-03 prod-host-02..., Unreported=0, Unresponsive=0,
```
