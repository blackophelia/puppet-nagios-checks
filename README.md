# Puppet Nagios Checks

Spot to put my puppet nagios checks.  Available for use 'as-is'.

## checks/check_puppet_nodes.py

Checks the status of a puppet environment, providing a summary or detailed version of the current state.

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
  -W, --warn-failed     Failed nodes won't trigger critical state.
  -C, --crit-failed     Failed nodes will trigger critical state. Default.
```

Sample output from `summary` mode:
```
CRITICAL:: Total nodes=23, Changed=14, Failed=2, Noop=0, Unchanged=7, Unreported=0, Unresponsive=0,
```


Sample output from `detailed` mode:
```
CRITICAL:: Total nodes=23, Changed=2 host-01 host-02, Failed=1 test-host-01, Noop=0, Unchanged=20 dev-host-01 prod-host-01 dev-host-02 dev-host-03 prod-host-02..., Unreported=0, Unresponsive=0,
```

## checks/check_pe_license.sh

Checks the status of  a PE 2015.x, PE 2016.x installation and licensing.  Designed to run locally on the puppetmaster as an NRPE Nagios check.

Usage:
```
  Script to check PE license status, for number of nodes remaining under license and number of days before expiry.
  Assumes that the host on which this script is run is the puppetmaster.  Designed to run as an NRPE check, from nagios.

  usage: ./check_pe_license.sh [-h] [-w num] [-c num] [-W num] [-C num]

    -h            Usage.
    -w            Number of nodes remaining before a warning alert is triggered.  Default is 15.
    -c            Number of nodes remaining before a critical alert is triggered.  Default is 5.
    -W            Number of days before license expiry before a warning alert is triggered.  Default is 15.
    -C            Number of days before license expiry before a critical alert is triggered.  Default is 5.

  Returns standard Nagios return codes:
  - 0 for success
  - 1 for warning
  - 2 for critical
  - 3 for unknown
```

Sample output:
```
OK: Puppet Enterprise License:: Nodes used 8/150. License expires in 167 days, on 2016-12-13.
```

