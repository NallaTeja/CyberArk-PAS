# Download Java
Link to download Java
https://www.atlassian.com/software/jira/service-management/download-archives

# Install Java
Jave setup 8.0.4110.9 version intallation form site.
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/6d153822-092e-4f97-9a62-ffc77b744a38)
Accept licence
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/87298896-556d-4083-874f-d6102c5b5ecc)
Destination Folder
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/6bfddc21-fb99-4475-b9ad-399e4ca586b6)
Successfully installed JAVA
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/addb698b-c143-4e04-92ac-afdc691c29c3)

# Install Jira
Install Jira Service Desk 5.16.0
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/2a4d3842-acd9-44d0-a831-d98cb28f56ea)
Upradaing Jira (Express Install)
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/d99e33bd-5885-4371-b4aa-064a7867378b)
Installation Summary
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/a96b4d19-e8c8-4f83-bd33-064c300e2a80)
Successfully installed Jira
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e188542a-4626-49d3-b118-1a261076f593)
Launch browser
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/043f14e3-af0e-4291-80f0-69d954bc489f)

# Configure Jira
Access the web interface 
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/1773b5fa-0151-401f-81c3-daf1faa2ce7f)
http://localhost:8080/secure/SetupMode!default.jspa
Set up the database connection (default: embeded database)select "I'll set it up myself"
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/d6e1bff5-010d-4d82-b380-ccbe828a3bb6)
Database setup
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/daee457f-5bf4-4049-bc0c-99a2d4384b52)
- Database type: PostgreSQL (compatible with CyberArk and Jira)
- Hostname: `192.168.5.131` localhost (if the database is on the same server as Jira) or the hostname/IP address of your database server
- Port: `5432` (default port for PostgreSQL)
- Database name: `jira_db`
- Username: administrator
- Password: Tej@143

Test connection before going to next 
# install Postgresql (based up on windows OS version download the version)
Download link
https://www.enterprisedb.com/downloads/postgres-postgresql-downloads
Setup -PostgreSQL
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/1e7c608c-d246-4fe4-b050-9bfdf12df58f)
Installation Directory
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/dae5ffe7-48fd-4480-9a55-dfec5725c697)
Select components
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/58216d6d-dc69-4ecb-8e17-53313cbbd54f)
Data Directory
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/66ca9b44-f841-46ba-95ae-b6aaf21f3a20)
Password: `Tej@143`
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e53b5158-d1c8-4b71-8237-8d669a6132f7)
Port: 5432
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/1edc492c-6907-46e2-9cb9-ff1c794c72c0)
Advanced Options
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/167163d4-0831-4340-af66-8fa532acd68b)
Pre Installation summary
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/02b6c298-7deb-40cd-af61-8e6b29fe337f)
Ready to Install
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/1b94e7d9-530c-4c74-a30b-43cf250a329a)
Successfully installed postgreSQL
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/e5ac6e9c-8295-4430-9738-e2ad21f5b940)

# Stack Bulder 4.2.1
![image](https://github.com/NallaTeja/CyberArk-PAS/assets/145950340/d2425383-b2c2-4025-9fea-1ed7a9ce5131)

Select the applications you would like to install.
1. Add-ons, tools and utilities
   > pgAgent (64 bit) for postgreSQL 12 v4.2.2.-1
    Useful for scheduling and automating database tasks. This can be beneficial for maintenance and running scheduled queries or jobs related to your integration
2. Database Drivers
   > pgJDBC v42.7.2-1
   Required for Java applications to connect to PostgreSQL, which is essential if Jira is using JDBC for database connectivity.
   > psqlODBC (64 bit) v13.02.0000-1
   Useful for applications that connect to PostgreSQL using ODBC, providing flexibility in connection methods.
3. Database Server
   > PostgreSQL (Installed)
4. Registration-required and trial products
   > Migration toolkit v55.7.0-1
    Useful if you need to migrate data from another database system
   > PEM SQL Profiler Plugin for PostgresSQL 12 (64bit) v8.2.0-1
   Helpful for performance monitoring and optimization.
5. Web Development
   > PEM-HTTPD v2.4.59-1
Provides a web server interface for managing PostgreSQL. Useful for web-based database management and monitoring.









