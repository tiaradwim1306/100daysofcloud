
# AWS Backup,DRS,AWS DataSync,MGN : Course on Udemmy by Stepahane Mareek

## Cloud Research
### AWS Backup
- Fully-managed service to centrally manage and automate backups across AWS services
- On-demand and scheduled backups
- Supports PITR (Point-in-time Recovery)
- Retention Periods, Lifecycle Management, Backup Policies, …
- Cross-Region Backup
- Cross-Account Backup (using AWS Organizations)

### Disaster Recovery Strategies
- Backup and Restore
- Pilot Light
- Warm standby
- Multi-Site / Hot-Site

### AWS Elastic Disaster Recovery (DRS)
- Used to be named “CloudEndure Disaster Recovery”
- Quickly and easily recover your physical, virtual, and cloud-based servers into AWS
- Example: protect your most critical databases (including Oracle, MySQL, and SQL Server), enterprise apps (SAP), protect your data from ransomware attacks, …
- Continuous block-level replication for your servers

### AWS DataSync
- Move large amount of data from on-premises to AWS
- Can synchronize to: Amazon S3 (any storage classes – including Glacier), Amazon EFS, Amazon FSx for Windows
- Replication tasks can be scheduled hourly, daily, weekly
- The replication tasks are incremental after the first full load

### AWS Application Discovery Service
- Plan migration projects by gathering information about on-premises data centers
- Server utilization data and dependency mapping are important for migrations
- Resulting data can be viewed within AWS Migration Hub

There are two types of migration you can do :
- Agentless Discovery (AWS Agentless Discovery Connector)
	- VM inventory, configuration, and performance history such as CPU, memory, and disk usage
- Agent-based Discovery (AWS Application Discovery Agent)
	- System configuration, system performance, running processes, and details of the network connections between systems

### AWS Application Migration Service (MGN)
- The “AWS evolution” of CloudEndure Migration, replacing AWS Server Migration Service (SMS)
- Lift-and-shift (rehost) solution which simplify migrating applications to AWS
- Converts your physical, virtual, and cloud-based servers to run natively on AWS
- Supports wide range of platforms, Operating Systems, and databases
- Minimal downtime, reduced costs

## Social Proof

[Twitter](https://twitter.com/tiaradwim1306/status/1629684741502033920)
