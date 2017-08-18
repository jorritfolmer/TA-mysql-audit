# MySQL query audit add-on for Splunk

[![Travis CI build status](https://travis-ci.org/jorritfolmer/TA-mysql-audit.svg?branch=master)](https://travis-ci.org/jorritfolmer/TA-mysql-audit)

This CIM compliant add-on provides field extractions, aliases and tags for
MySQL query audit logging in both "NEW" and "OLD" XML format.

## Install the MySQL query audit add-on

### Single instance Splunk deployments

1. In Splunk, click on "Manage Apps"
2. Click "Browse more apps", search for "MySQL query audit" and install the add-on

### Distributed Splunk deployments

| Instance type | Supported | Required | Description
|---------------|-----------|----------|------------
| Search head   | Yes       | Yes      | Install this add-on on your search head(s) where CIM compliance of MySQL query audit logging is required
| Indexer       | Yes       | Conditional | Install this add-on on your indexer(s) if you are using Universal Forwarder to collect the audit data. If you are using Heavy Forwarders, installation on indexers is not required.
| Universal Forwarder | Yes | No       | This add-on is not meant to be installed on Universal Forwarders
| Heavy Forwarder     | Yes | Yes | Install this add-on if you use a heavy forwarder to monitor MySQL query audit logging. In that case, this add-on doesn't have to be installed on indexers.

The following table lists support for distributed deployment roles in a Splunk deployment:

| Deployment role | Supported | Description
|-----------------|-----------|-------------
| Search head deployer | Yes  | Install this add-on on your search head deployer to enable CIM compliance of MySQL query audit logging on a Search Head Cluster
| Cluster Master       | Yes  | Install this add-on on your Cluster Master to ensure correct parsing operations on all cluster peers
| Deployment Server    | Yes  | Install this add-on on your Deployment Server to deploy it to search heads and indexers, if you are not using a clustered deployment

## Configure inputs for the MySQL query audit add-on

To collect the MySQL query audit logging, install a Universal Forwarder on your MySQL server(s). Refer to [Install the universal forwarder software](http://docs.splunk.com/Documentation/Forwarder/latest/Forwarder/Installtheuniversalforwardersoftware) in the Splunk documentation for further details.

Then, create an inputs.conf to collect and send the data to the Splunk Platform:

```
[monitor://<MYSQL_AUDIT_LOG_PATH>/audit.log]
index = mysql
sourcetype = mysql:audit:xml
disabled = 0
```

## Enable MySQL audit logging

Refer to the MySQL documentation for help with installing the Audit Log plugin on your MySQL server(s). To enable audit logging in XML format you have to install the audit_log plugin and configure the proper auditing format to use:

1. Install the audit plugin: `install plugin audit_log soname 'audit_log.so';`
2. Set the audit log format: `set global audit_log_format=NEW`

This will create the audit log file: `/var/lib/mysql/audit.log`

## Support

This is an MIT licensed open source project without warranty of any kind. No
support is provided. A public repository and issue tracker are available at
[https://github.com/jorritfolmer/TA-mysql-audit](https://github.com/jorritfolmer/TA-mysql-audit)

