# MySQL audit add-on for Splunk

This CIM compliant add-on provides field extractions, aliases and tags for
MySQL query audit logging in both "NEW" and "OLD" XML format.

## Installation

For distributed environments, this add-on needs to be deployed on the search head(s) as well as on the indexer(s).

## Configuration

Deploy an inputs.conf file on the MySQL server to audit:

```
[monitor:///var/lib/mysql/audit.log]
index = mysql
sourcetype = mysql:audit:xml
disabled = 0
```

## Enable MySQL audit logging

On the MySQL prompt:

1. Install the audit plugin: `install plugin audit_log soname 'audit_log.so';`
2. Set the audit log format: `set global audit_log_format=NEW`

This will create the audit log file: `/var/lib/mysql/audit.log`

## Support

This is an MIT licensed open source project without warranty of any kind. No
support is provided. A public repository and issue tracker are available at
[https://github.com/jorritfolmer/TA-mysql-audit](https://github.com/jorritfolmer/TA-mysql-audit)

