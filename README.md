# Auditd Wazuh integration
## On Linux agent machines, run following commands to enable auditd and load these rules
```
apt update -y
apt install auditd audispd-plugins -y
wget https://raw.githubusercontent.com/0xbad53c/auditd/master/audit.rules -O /etc/audit/rules.d/audit.rules
systemctl enable auditd.service
systemctl start auditd.service
```

## On Wazuh manager instance, run following commands to make wazuh parse correctly
```
wget https://raw.githubusercontent.com/0xbad53c/auditd/master/audit-keys -O /var/ossec/etc/lists/audit-keys
systemctl restart wazuh-manager
```



Original README below.


        ___             ___ __      __
       /   | __  ______/ (_) /_____/ /
      / /| |/ / / / __  / / __/ __  / 
     / ___ / /_/ / /_/ / / /_/ /_/ /  
    /_/  |_\__,_/\__,_/_/\__/\__,_/   

Best Practice Auditd Configuration

## Idea

The idea of this auditd configuration is to provide a basic configuration that

- works out-of-the-box on all major Linux distributions 
- fits most use cases
- produces a reasonable amount of log data
- covers security relevant activity
- is easy to read (different sections, many comments)

## Sources

The configuration is based on the following sources

Gov.uk auditd rules
https://github.com/gds-operations/puppet-auditd/pull/1

CentOS 7 hardening
https://highon.coffee/blog/security-harden-centos-7/#auditd---audit-daemon

Linux audit repo 
https://github.com/linux-audit/audit-userspace/tree/master/rules

Auditd high performance linux auditing
https://linux-audit.com/tuning-auditd-high-performance-linux-auditing/

### Further rules

Not all of these rules have been included. 

For PCI DSS compliance see: 
https://github.com/linux-audit/audit-userspace/blob/master/rules/30-pci-dss-v31.rules

For NISPOM compliance see:
https://github.com/linux-audit/audit-userspace/blob/master/rules/30-nispom.rules

## Video Explanations by IppSec

IppSec captured a video that explains how to detect the exploitation of the OMIGOD vulnerability using auditd. In that video, he walks you through the audit configuration maintained in this repo and exlains how to use it. I highly recommend this video to get a better understanding of what is happening in the config. 

https://www.youtube.com/watch?v=lc1i9h1GyMA

## Contribution

Please contribute your changes as pull requests
