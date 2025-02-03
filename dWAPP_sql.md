### 1. Connect to MySQL as Root User
```bash
mysql -u root -p
```

---

### 2. Create Database
#### Create Database
```sql
CREATE DATABASE IF NOT EXISTS bWAPP;
USE bWAPP;
```

#### Create User and Grant Privileges
```sql
CREATE USER 'bwapp_user'@'localhost' IDENTIFIED BY 'bug';
GRANT ALL PRIVILEGES ON bWAPP.* TO 'bwapp_user'@'localhost';
FLUSH PRIVILEGES;
```

---

### 3. Create Tables

#### Users Table
```sql
CREATE TABLE IF NOT EXISTS users (
    id INT(10) NOT NULL AUTO_INCREMENT,
    login VARCHAR(100) DEFAULT NULL,
    password VARCHAR(100) DEFAULT NULL,
    email VARCHAR(100) DEFAULT NULL,
    secret VARCHAR(100) DEFAULT NULL,
    activation_code VARCHAR(100) DEFAULT NULL,
    activated TINYINT(1) DEFAULT '0',
    reset_code VARCHAR(100) DEFAULT NULL,
    admin TINYINT(1) DEFAULT '0',
    PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

#### Blog Table
```sql
CREATE TABLE IF NOT EXISTS blog (
    id INT(10) NOT NULL AUTO_INCREMENT,
    owner VARCHAR(100) DEFAULT NULL,
    entry VARCHAR(500) DEFAULT NULL,
    date DATETIME DEFAULT NULL,
    PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

#### Visitors Table
```sql
CREATE TABLE IF NOT EXISTS visitors (
    id INT(10) NOT NULL AUTO_INCREMENT,
    ip_address VARCHAR(50) DEFAULT NULL,
    user_agent VARCHAR(500) DEFAULT NULL,
    date DATETIME DEFAULT NULL,
    PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

#### Movies Table
```sql
CREATE TABLE IF NOT EXISTS movies (
    id INT(10) NOT NULL AUTO_INCREMENT,
    title VARCHAR(100) DEFAULT NULL,
    release_year VARCHAR(100) DEFAULT NULL,
    genre VARCHAR(100) DEFAULT NULL,
    main_character VARCHAR(100) DEFAULT NULL,
    imdb VARCHAR(100) DEFAULT NULL,
    tickets_stock INT(10) DEFAULT NULL,
    PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

#### Heroes Table
```sql
CREATE TABLE IF NOT EXISTS heroes (
    id INT(10) NOT NULL AUTO_INCREMENT,
    login VARCHAR(100) DEFAULT NULL,
    password VARCHAR(100) DEFAULT NULL,
    secret VARCHAR(100) DEFAULT NULL,
    PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

---

### 4. Insert Initial Data

#### Insert Users Data
```sql
INSERT INTO users (login, password, email, secret, admin) VALUES
('A.I.M.', '6885858486f31043e5839c735d99457f045affd0', 'bwapp-aim@mailinator.com', 'A.I.M. or Authentication Is Missing', 1),
('bee', '6885858486f31043e5839c735d99457f045affd0', 'bwapp-bee@mailinator.com', 'Any bugs?', 1);
```

#### Insert Movies Data
```sql
INSERT INTO movies (title, release_year, genre, main_character, imdb, tickets_stock) VALUES
('G.I. Joe: Retaliation', '2013', 'action', 'Cobra Commander', 'tt1583421', 100),
('Iron Man', '2008', 'action', 'Tony Stark', 'tt0371746', 53),
('Man of Steel', '2013', 'action', 'Clark Kent', 'tt0770828', 78),
('Terminator Salvation', '2009', 'sci-fi', 'John Connor', 'tt0438488', 100),
('The Amazing Spider-Man', '2012', 'action', 'Peter Parker', 'tt0948470', 13),
('The Cabin in the Woods', '2011', 'horror', 'Some zombies', 'tt1259521', 666),
('The Dark Knight Rises', '2012', 'action', 'Bruce Wayne', 'tt1345836', 3),
('The Fast and the Furious', '2001', 'action', 'Brian O\'Connor', 'tt0232500', 40),
('The Incredible Hulk', '2008', 'action', 'Bruce Banner', 'tt0800080', 23),
('World War Z', '2013', 'horror', 'Gerry Lane', 'tt0816711', 0);
```

#### Insert Heroes Data
```sql
INSERT INTO heroes (login, password, secret) VALUES
('neo', 'trinity', 'Oh why didn\'t I took that BLACK pill?'),
('alice', 'loveZombies', 'There\'s a cure!'),
('thor', 'Asgard', 'Oh, no... this is Earth... isn\'t it?'),
('wolverine', 'Log@N', 'What\'s a Magneto?'),
('johnny', 'm3ph1st0ph3l3s', 'I\'m the Ghost Rider!'),
('seline', 'm00n', 'It wasn\'t the Lycans. It was you.');
```

---

### 5. Verify Installation

#### Show Tables
```sql
SHOW TABLES;
```

#### Select All from Users
```sql
SELECT * FROM users;
```

#### Count Movies
```sql
SELECT COUNT(*) FROM movies;
```

---
