![onboardingrules01](https://github.com/NallaTeja/MOP-PAS/assets/145950340/9e64e5f2-d0a4-4783-b163-c24f805c5ada)

## Log Management
### 1. Automate Log Clearing with Cron Job
**Objective:** Set up a cron job to automatically clear aging logs on the target server.
**Steps:**
1. **Login to the Target Server**
    ```bash
    ssh user@target_server
    ```
2. **Switch to Root User**
    ```bash
    sudo su -
    ```
3. **Edit the Cron Job Configuration**
    ```bash
    crontab -e
    ```
4. **Add Cron Jobs**
    ```cron
    0 3 * * * find /var/opt/CARK/logs/components/old -type f -mtime +60 -exec rm -f {} \;
    0 3 * * * find /var/opt/CARK/logs/components/ -type f -mtime +60 -exec rm -f {} \;
    0 3 * * * find /var/opt/CARK/logs/old -type f -mtime +60 -exec rm -f {} \;
    ```

### 2. Manually Clear Aging Logs
**Objective:** Manually clear aging logs on the target server.
**Steps:**
1. **Login to the Target Server**
    ```bash
    ssh user@target_server
    ```
2. **Switch to Root User**
    ```bash
    sudo su -
    ```
3. **Check Disk Usage**
    ```bash
    df -h
    ```
4. **Navigate to Logs Directory**
    ```bash
    cd /var/opt/CARK/logs/
    ```
5. **Check Disk Space Occupied by Logs**
    ```bash
    du -sh*
    ```
6. **Clear Aging Logs**
    ```bash
    find /var/opt/CARK/logs/components/old -type f -mtime +60 -exec rm -f {} \;
    find /var/opt/CARK/logs/components/old -type f -mtime +60 -exec rm -f {} \;
    find /var/opt/CARK/logs/components/old -type f -mtime +60 -exec rm -f {} \;
    ```
