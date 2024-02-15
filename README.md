# azure-database-migration531 - README

## Achievements in Milestone 1 & 2: Set Up Enviroment and Production Enviroment

In this milestone, we were given the task of setting up the enviroment and production enviroment, we have successfully accomplished the following tasks:

1. **Azure Account and Git Repo**

   - We are using GitHub to track changes and progress.
   - We will be using the Azure suite, an account has been created with access to relevant services.
   - Git Repository: https://github.com/alamdave/azure-database-migration531
   - Inclusion of README.md.

2. **Virtual Machine Setup**

   - We provisioned a virtual machine (VM) on the Azure cloud platform to host our application and database.
   - The VM is configured with the necessary resources (CPU, RAM, storage) based on our project requirements.
   - We ensured that the VM is running on the windows 10x64 operating system for our application.

3. **SQL Server Installation**

   - We installed Microsoft SQL Server on the virtual machine to serve as our database management system.
   - The SQL Server version used is SQL Server 2022 to leverage the latest features and security enhancements.

4. **Production Database Creation**
   - We created the production database by restoring it from a backup file.
   - The backup file corresponds to the renowned Microsoft SQL Server database known as AdventureWorks.
   - AdventureWorks is an illustrative and comprehensive sample database that emulates a fictional manufacturing company's operations. It encompasses various tables, views, stored procedures, and data, offering a rich and diverse dataset.
   - By restoring the AdventureWorks database from the provided backup file, we've replicated an authentic production database scenario.

## Virtual Machine Setup Details

- **Cloud Platform**: Azure
- **VM Specifications**: vCPUs: 2, RAM: 8GiB, STORAGE: 127GiB - premium SSD LRS
- **Operating System**: Image plan: win10-22h2-pro-g2, Windows-10-pro-x64
- **Network Configuration**: Security Type: Trusted launch

## SQL Server Installation Details

- **SQL Server Version**: Microsoft SQL Server 2022 (RTM) - 16.0.1000.6 (X64)
- **Installation Method**: Downloaded from microsoft.com installer
- **Configuration Settings**: Loaded with basic settings.
- **SQL Server Management Tools**: SQL Server Management Studio

## Production Database Details

- **Database Name**: av-sql-db_restored-01-02-2024
- **Server Name**: UK South
- **Security Measures**: SSL login, Entra-ID, Transparent Data Encryption.
- **Backup and Maintenance**: Automated backup strategy, Geo-differenciated failover group for disaster recovery.

## Achievements in Milestone 3: Migrate to Azure SQL Database

In this milestone, we will outline how I successfully achieved the migration of our on-premise database to Azure SQL Database. Here are the key accomplishments:

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

## Achievements in Milestone 4: Data Backup and Restoration

In this milestone, we will outline the meticulous backup and restoration journey we have undertaken to ensure the safety and integrity of our data. This process includes:

1. **Full Backup of Production Database**

   - We initiated a full backup of our production database hosted on the Windows VM.
   - This backup serves as a duplicate of our database, providing a safety net in case of unforeseen issues.
   - The resultant backup file has been securely stored in a designated location on our computer.

2. **Azure Blob Storage Configuration**

   - We configured an Azure Blob Storage account, which acts as a secure online repository for our database backups.
   - The previously created database backup file has been uploaded to the Blob Storage container.
   - This step adds an extra layer of backup protection by maintaining a redundant copy stored remotely.

3. **Development Environment Setup**

   - To facilitate controlled experimentation, similar to a sandbox in software development, we provisioned a new Windows VM that replicates our development setup.
   - SQL Server has been installed on this VM to mimic the necessary database infrastructure.
   - The database backup from Step 1 was successfully restored onto this new "sandbox" environment, allowing us to experiment without impacting production data.

4. **Automated Backups in SSMS**

   - On our development Windows VM, we utilized SQL Server Management Studio (SSMS) to establish a Management Task that automates regular backups of our development database.
   - A weekly backup schedule has been configured to ensure consistent protection for our evolving work and simplify recovery for the development environment if needed.

By following this meticulous backup process, utilizing secure Azure Blob Storage, seamlessly restoring data onto our development environment, and executing automated backups via Maintenance Plans in SSMS, we have established a robust data backup and restoration strategy. Our data remains secure and recoverable, even in challenging circumstances.

## Achievements in Milestone 5: Disaster Recovery Simulation

In this documentation, we outline the deliberate removal of critical data from our production database to simulate a scenario where data integrity is compromised, as well as the subsequent recovery process. This process includes:

1. **Simulating Data Loss**

   - Deliberately removed critical data from our production database to replicate a scenario where data integrity is compromised.
   - Detailed documentation of the simulated data loss has been meticulously recorded for reference.
   - Simulation of data loss and recovery:

     ```
     DELETE TOP(1000)
     FROM [av-sql-db].[Production].[BillOfMaterials];

     UPDATE TOP (100) [av-sql-db].[Production].[BillOfMaterials]
     SET EndDate = NULL;
     ```

2. **Confirming Simulation Success**

   - After completing the simulation, we confirmed its success by examining the Azure SQL Database using the connection already established in Azure Data Studio.
   - This step ensured that the simulated data loss was accurately reflected in the database.

3. **Database Restoration from Backup**

   - We utilized Azure SQL Database Backup to restore the production database to a point just before the simulated data loss occurred.
   - Validation of the restoration's success was performed by examining the restored data through the connection in Azure Data Studio.
   - It's important to note that the restored database now functions as our production database, as the previous production database lacked critical data.

4. **Cleanup**

   - After successfully restoring the production database from a backup, we deleted the database that had suffered data loss in the Azure portal.

By following this process, including simulating data loss, confirming the simulation's success, and recovering the database from a backup, we have established a robust data recovery strategy. Our data integrity is ensured, and we are well-prepared to handle unforeseen data loss scenarios with confidence.

## Achievements in Milestone 6: Geo Replication and Failover

In this documentation, we describe our experience with setting up geo-replication, orchestrating a planned failover, and performing a failback for our production Azure SQL Database. This process includes:

1. **Setting Up Geo-Replication**

   - We initiated the setup of geo-replication for our production Azure SQL Database.
   - This involved creating a synchronized replica of our primary database on a separate SQL server located in a different geographical region from our primary database server.
   - The geographical separation bolsters redundancy and resilience, minimizing shared risks.

## Failover Server

- **Database Name**: av-sql-failover
- **Server**: West-Europe

2. **Simulating Planned Failover**

   - To simulate real-world challenges and test the failover strategy, we orchestrated a planned failover to the secondary region.
   - This act transitioned operations to the secondary copy, and we evaluated the availability and data consistency of the failover database.
   - The failover process allowed us to ensure that our systems can maintain operations in the event of a primary region outage.

3. **Performing Failback**

   - Following the failover testing, we performed a failback to the primary region.
   - This demonstrated the cyclical nature of our failover strategy, ensuring that our systems could seamlessly return to the primary region once it became available again.

By going through these steps, including setting up geo-replication, orchestrating a planned failover, and performing a failback, we have enhanced the resilience and availability of our database system. This experience has provided valuable insights into our disaster recovery capabilities and preparedness.

## Achievements in Milestone 7: Microsoft Entra Directory Integration

In this documentation, we describe the process of enabling Microsoft Entra ID authentication for our Azure SQL production database and integrating it with our database users. This process includes:

1. **Enabling Microsoft Entra ID Authentication**

   - We initiated the integration of Microsoft Entra ID as a trusted identity provider for our SQL Server that hosts the Azure SQL production database.
   - This allows users to authenticate using their Microsoft Entra credentials, enhancing security and user convenience.
   - Ensure that you can establish a connection to the production database using Microsoft Entra credentials within Azure Data Studio.

2. **Designating a Microsoft Entra Admin**

   - We chose a Microsoft Entra admin with privileged permissions within our Azure SQL Database environment.
   - This admin has the authority over user management and access control, ensuring proper governance.

3. **Creating a DB Reader User**

   - We generated a new user account in Microsoft Entra ID "db_reader_alam@aicoreusers.onmicrosoft.com", which serves as our DB Reader user.
   - In Azure Data Studio, we connected to the production database using the Microsoft Entra admin credentials.
   - We assigned the `db_datareader` role to the previously created DB Reader User, providing them with read-only privileges. I used the following code to apply these permissions:

     ```
     CREATE USER [db_reader_alam@aicoreusers.onmicrosoft.com] FROM EXTERNAL PROVIDER;
     ALTER ROLE db_datareader ADD MEMBER [db_reader_alam@aicoreusers.onmicrosoft.com];
     ```

4. **Testing Permissions**

   - We reconnected to our production database using Azure Data Studio and the credentials of the new DB Reader AD user.
   - We thoroughly tested the permissions of the user to ensure that the correct role had been assigned, and the user could access the database with read-only privileges.

5. **Documentation and UML Diagram**

   - We have updated this README file on GitHub to capture our journey of integrating Microsoft Entra ID.
   - Our documentation includes details of the configuration process, role definitions, and the creation of both admin and reader accounts.
   - Additionally, we have added a UML diagram to illustrate the architecture we have built.

By following these steps, we have successfully integrated Microsoft Entra ID authentication into our Azure SQL Database environment, enhancing security and user management. The documentation and UML diagram provide a comprehensive overview of our project experience.
