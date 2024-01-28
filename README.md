# azure-database-migration531 - README

## Achievements in Milestone

In this milestone, we have successfully accomplished the following tasks:

1. **Virtual Machine Setup**

   - We provisioned a virtual machine (VM) on the Azure cloud platform to host our application and database.
   - The VM is configured with the necessary resources (CPU, RAM, storage) based on our project requirements.
   - We ensured that the VM is running on the windows 10x64 operating system for our application.

2. **SQL Server Installation**

   - We installed Microsoft SQL Server on the virtual machine to serve as our database management system.
   - The SQL Server version used is SQL Server 2022 to leverage the latest features and security enhancements.

3. **Production Database Creation**
   - We created the production database by restoring it from a backup file.
   - The backup file corresponds to the renowned Microsoft SQL Server database known as AdventureWorks.
   - AdventureWorks is an illustrative and comprehensive sample database that emulates a fictional manufacturing company's operations. It encompasses various tables, views, stored procedures, and data, offering a rich and diverse dataset.
   - By restoring the AdventureWorks database from the provided backup file, we've replicated an authentic production database scenario.

## Virtual Machine Setup Details

- **Cloud Platform**: Azure
- **VM Specifications**: vCPUs: 2, RAM: 8GiB, STORAGE: 127GiB - premium SSD LRS
- **Operating System**: Image plan: win10-22h2-pro-g2, Windows-10-pro-x64
- **Network Configuration**: Security Type: Trustesd launch, Describe any networking configurations, such as public/private IP addresses, firewall rules, and network security groups.

## SQL Server Installation Details

- **SQL Server Version**: Microsoft SQL Server 2022 (RTM) - 16.0.1000.6 (X64)
- **Installation Method**: Downloaded from microsoft.com installer
- **Configuration Settings**: Loaded with basic settings.
- **SQL Server Management Tools**: SQL Server Management Studio

## Production Database Details

- **Database Name**: Provide the name of the production database.
- **Schema Design**: Describe the data schema, including tables, columns, and relationships.
- **Security Measures**: Detail the security measures implemented, such as user roles, access control, and encryption.
- **Backup and Maintenance**: Explain the backup strategy and any maintenance plans in place to ensure database reliability and disaster recovery.

## Next Steps
