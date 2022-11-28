# check_linux_ethernet_bond
nagios check for health status of ethernet bonding interface

# Requirements
perl, SSH key pair auth

# Configuration
Add a section similar to the following to the services.cfg file on the nagios server.
```
define service{
        use                             generic-service
        host_name                       linux01.example.com
        service_description             NIC bond0
        check_command                   check_by_ssh!"/usr/local/nagios/libexec/check_linux_ethernet_bond --bond=bond0"
        }
        
 define service{
        use                             generic-service
        host_name                       linux01.example.com
        service_description             NIC bond1
        check_command                   check_by_ssh!"/usr/local/nagios/libexec/check_linux_ethernet_bond --bond=bond1"
        }

```

# Output
You will see output similar to the following:
```
NIC bond OK - mode:active-backup bond0_status:up  eno1_status:up eno1_speed:10000 Mbps eno1_link_failure_count:0 eno2_status:up eno2_speed:10000 Mbps eno2_link_failure_count:0
```
```
NIC bond OK - mode:LACP bond1_status:up  ens1f0_status:up ens1f0_speed:25000 Mbps ens1f0_link_failure_count:0 ens1f1_status:up ens1f1_speed:25000 Mbps ens1f1_link_failure_count:0
```
