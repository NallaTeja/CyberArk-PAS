## Log Management

### 1. Automating Log Clearance with Cron Jobs

**Objective:** Automate the process of clearing aging logs on the target server using cron jobs.

**Procedure:**

1. **Access the Target Server**
    ```bash
    ssh user@target_server
    ```

2. **Switch to the Root User**
    ```bash
    sudo su -
    ```

3. **Modify the Cron Job Configuration**
    ```bash
    crontab -e
    ```

4. **Configure Cron Jobs**
    ```cron
    0 3 * * * find /var/opt/CARK/logs/components/old -type f -mtime +60 -exec rm -f {} \;
    0 3 * * * find /var/opt/CARK/logs/components/ -type f -mtime +60 -exec rm -f {} \;
    0 3 * * * find /var/opt/CARK/logs/old -type f -mtime +60 -exec rm -f {} \;
    ```

### 2. Manual Clearance of Aging Logs

**Objective:** Manually clear aging logs on the target server.

**Procedure:**

1. **Access the Target Server**
    ```bash
    ssh user@target_server
    ```

2. **Switch to the Root User**
    ```bash
    sudo su -
    ```

3. **Check Disk Usage**
    ```bash
    df -h
    ```

4. **Navigate to the Logs Directory**
    ```bash
    cd /var/opt/CARK/logs/
    ```

5. **Review Disk Space Occupied by Logs**
    ```bash
    du -sh*
    ```

6. **Clear Aging Logs**
    ```bash
    find /var/opt/CARK/logs/components/old -type f -mtime +60 -exec rm -f {} \;
    find /var/opt/CARK/logs/components/old -type f -mtime +60 -exec rm -f {} \;
    find /var/opt/CARK/logs/components/old -type f -mtime +60 -exec rm -f {} \;
    ```

These revised notes are presented in a professional tone with improved grammar, clearer instructions, and stronger verbs.
