# azure-database-migration531 - README

## Achievements in Milestone 1 & 2

In this milestone, we were given the task of setting up the enviroment and production enviroment, we have successfully accomplished the following tasks:

1. **Azure Account and Git Repo**

   - We are using GitHub to track changes and progress.
   - We will be using the Azure suite, an account has been created with access to relevant services.
   - Git Repository: https://github.com/alamdave/azure-database-migration531
   - Inclusion of README.md.

1. **Virtual Machine Setup**

   - We provisioned a virtual machine (VM) on the Azure cloud platform to host our application and database.
   - The VM is configured with the necessary resources (CPU, RAM, storage) based on our project requirements.
   - We ensured that the VM is running on the windows 10x64 operating system for our application.

1. **SQL Server Installation**

   - We installed Microsoft SQL Server on the virtual machine to serve as our database management system.
   - The SQL Server version used is SQL Server 2022 to leverage the latest features and security enhancements.

1. **Production Database Creation**
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

## Achievements in Milestone 3

In this milestone, we have successfully achieved the migration of our on-premise database to Azure SQL Database. Here are the key accomplishments:

1. **Azure SQL Database Configuration**

   - We created an Azure SQL Database to serve as the target for migrating our on-premise database.
   - The SQL Server associated with the Azure SQL Database uses SQL login as the chosen authentication method.
   - Firewall rules have been configured, including the addition of our IP address, to ensure secure access to the Azure SQL Database.

2. **Azure Data Studio Integration**

   - Azure Data Studio has been installed and configured on our production Windows VM.
   - We established connections to both the existing on-premise database and the newly created Azure SQL Database using Azure Data Studio.

3. **Schema Migration**

   - We installed the SQL Server Schema Compare extension within Azure Data Studio.
   - Leveraging this extension, we compared and migrated the schema from the on-premise database to the Azure SQL Database.

4. **Data Migration**

   - We installed the Azure SQL Migration extension within Azure Data Studio to facilitate the smooth transfer of data from the on-premise database to the Azure SQL Database.

5. **Validation**

   - We carried out a comprehensive validation process to ensure the success of the database migration.
   - This included thorough inspections of data, schema, and configurations, ensuring that the migration adheres to principles of data integrity.

## Azure SQL Database Configuration Details

- **Database Name**: av-server-sql
- **Authentication Method**: SQL login.
- **Firewall Rules**: Rule name: windows-vm-alamdave Start IPv4: 20.77.14.195 End IPv4: 20.77.14.195
- **Azure Data Migration service Name**: Data-Migration-service-aicore

## Azure Data Studio Configuration

- **Tool Installation**: Azure Data Studio has been installed and configured on the production Windows VM.
