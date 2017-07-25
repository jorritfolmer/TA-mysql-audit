# MySQL audit add-on for Splunk

This CIM compliant TA can be used with Splunk Enterprise Security and provides field extractions, aliases and tags for MySQL audit logging in both "NEW" and "OLD" XML format.

## Installation

Install this TA on:
* Splunk (Enterprise Security) search head. 
* Splunk Indexers 

Make sure to name it TA-mysql-audit otherwise ES won't eat it. 

## Configuration

This TA expects MySQL XML audit logging to be sourcetyped `mysql:audit:xml`

