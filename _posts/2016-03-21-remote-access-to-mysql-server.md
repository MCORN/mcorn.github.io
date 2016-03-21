---
title: Setting up a mySQL server for remote access
updated: 2016-03-21 16:59
---

#### Allow remote connections to mySQL server

* Edit /etc/mysql/my.cnf to change "bind-address=YOUR-SERVER-IP" to the actual IP address instead of 127.0.0.1
* Restart mysql

```
sudo service mysql restart
```

#### Allow remote user access to mySQL database

* Connect to mysql

```
mysql -uroot -p
```

* Create user

```
CREATE USER 'user'@'%' IDENTIFIED BY 'password';
```

* Grant permissions
 
```
GRANT ALL PRIVILEGES ON *.* TO 'user'@'%' WITH GRANT OPTION;
```

* Flush priviledges

```
FLUSH PRIVILEGES;
```