
### **1. Service Management Commands**

#### **Apache Web Server**
- **Start Apache**:
  ```bash
  sudo systemctl start apache2
  ```
- **Stop Apache**:
  ```bash
  sudo systemctl stop apache2
  ```
- **Restart Apache** (after config changes):
  ```bash
  sudo systemctl restart apache2
  ```
- **Check Apache Status**:
  ```bash
  sudo systemctl status apache2
  ```

#### **MySQL Database**
- **Start MySQL**:
  ```bash
  sudo systemctl start mysql
  ```
- **Stop MySQL**:
  ```bash
  sudo systemctl stop mysql
  ```
- **Restart MySQL**:
  ```bash
  sudo systemctl restart mysql
  ```
- **Check MySQL Status**:
  ```bash
  sudo systemctl status mysql
  ```

---

### **2. Database Management**

#### **Access MySQL Shell**:
```bash
sudo mysql -u bwapp_user -p
# Password: bug (as per your setup)
```

#### **Backup Database**:
```bash
mysqldump -u bwapp_user -p bWAPP > bWAPP_backup.sql
# Enter password when prompted
```

#### **Restore Database**:
```bash
mysql -u bwapp_user -p bWAPP < bWAPP_backup.sql
```

#### **Common SQL Commands**:
- List databases: `SHOW DATABASES;`
- Use bWAPP database: `USE bWAPP;`
- List tables: `SHOW TABLES;`
- View users: `SELECT * FROM users;`

---

### **3. Start/Stop Entire Environment**

#### **Start Everything**:
```bash
sudo systemctl start apache2 mysql
```

#### **Stop Everything**:
```bash
sudo systemctl stop apache2 mysql
```

#### **Auto-Start on Boot** (Optional):
```bash
sudo systemctl enable apache2 mysql
```

---

### **4. File Permissions**
Ensure bWAPP files are accessible:
```bash
sudo chown -R www-data:www-data /var/www/html/bWAPP
sudo chmod -R 755 /var/www/html/bWAPP
```

---

### **5. Automation Scripts**

#### **Start Script** (`start_bwapp.sh`):
```bash
#!/bin/bash
sudo systemctl start apache2 mysql
echo "bWAPP environment started!"
```

#### **Stop Script** (`stop_bwapp.sh`):
```bash
#!/bin/bash
sudo systemctl stop apache2 mysql
echo "bWAPP environment stopped!"
```

**Make scripts executable**:
```bash
chmod +x start_bwapp.sh stop_bwapp.sh
```

---

### **6. Accessing bWAPP**
- **URL**: `http://localhost/bWAPP/bWAPP/login.php`
- **Credentials**:
  - Username: `bee`
  - Password: `bug`

---

### **7. Maintenance Tips**

1. **Regular Backups**:
   ```bash
   # Backup weekly
   mysqldump -u bwapp_user -p bWAPP > /path/to/backups/bWAPP_$(date +\%F).sql
   ```

2. **Update System**:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

3. **Check Logs**:
   - Apache Error Log: `/var/log/apache2/error.log`
   - MySQL Log: `/var/log/mysql/error.log`

4. **Security**:
   - Change default MySQL password (`bug`) if exposing to networks.
   - Use `sudo ufw enable` to activate firewall (allow ports 80/443).

---

### **8. Reset bWAPP Database**
To reset to default state:
```bash
mysql -u bwapp_user -p bWAPP < /var/www/html/bWAPP/bWAPP/admin/reset.sql
```

---

### **9. Key Files & Directories**
- **bWAPP Root**: `/var/www/html/bWAPP/`
- **Database Config**: `/var/www/html/bWAPP/bWAPP/admin/settings.php`
- **Installation Script**: `/var/www/html/bWAPP/bWAPP/install.php`

---

### **10. Best Practices for Learning**
1. **Take Snapshots** (if using VM) before experimenting with vulnerabilities.
2. **Use Burp Suite/ZAP** for testing (configure browser proxy to `127.0.0.1:8080`).
3. **Document Findings**: Record HTTP requests/responses for later analysis.

---
