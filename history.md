# 1. Prerequisites

## Install JDK and Maven
```sh
admin@gw-mac sb-mvn-rest-api % /usr/libexec/java_home               
/Library/Java/JavaVirtualMachines/temurin-17.jdk/Contents/Home
admin@gw-mac sb-mvn-rest-api % echo $JAVA_HOME
/Library/Java/JavaVirtualMachines/temurin-17.jdk/Contents/Home
admin@gw-mac sb-mvn-rest-api % 
admin@gw-mac sb-mvn-rest-api % java -version
openjdk version "17.0.4.1" 2022-08-12
OpenJDK Runtime Environment Temurin-17.0.4.1+1 (build 17.0.4.1+1)
OpenJDK 64-Bit Server VM Temurin-17.0.4.1+1 (build 17.0.4.1+1, mixed mode)
admin@gw-mac sb-mvn-rest-api % mvn -v       
Apache Maven 3.8.6 (84538c9988a25aec085021c365c560670ad80f63)
Maven home: /opt/homebrew/Cellar/maven/3.8.6/libexec
Java version: 18.0.2.1, vendor: Homebrew, runtime: /opt/homebrew/Cellar/openjdk/18.0.2.1/libexec/openjdk.jdk/Contents/Home
Default locale: en_JP, platform encoding: UTF-8
OS name: "mac os x", version: "12.5.1", arch: "aarch64", family: "mac"
admin@gw-mac sb-mvn-rest-api % 
admin@gw-mac sb-mvn-rest-api % /usr/libexec/java_home               
/Library/Java/JavaVirtualMachines/temurin-17.jdk/Contents/Home
admin@gw-mac sb-mvn-rest-api % echo $JAVA_HOME
/Library/Java/JavaVirtualMachines/temurin-17.jdk/Contents/Home
admin@gw-mac sb-mvn-rest-api % 
admin@gw-mac sb-mvn-rest-api % brew info maven
==> maven: stable 3.8.6 (bottled)
Java-based project management
https://maven.apache.org/
Conflicts with:
  mvnvm (because also installs a 'mvn' executable)
/opt/homebrew/Cellar/maven/3.8.6 (78 files, 9.7MB) *
  Poured from bottle on 2022-08-31 at 10:25:13
From: https://github.com/Homebrew/homebrew-core/blob/HEAD/Formula/maven.rb
License: Apache-2.0
==> Dependencies
Required: openjdk ✔
==> Analytics
install: 61,489 (30 days), 215,979 (90 days), 802,742 (365 days)
install-on-request: 61,371 (30 days), 215,335 (90 days), 798,990 (365 days)
build-error: 0 (30 days)
admin@gw-mac sb-mvn-rest-api % 
```

## Install mysql
```sh
admin@gw-mac sb-mvn-rest-api % brew install mysql
Warning: mysql 8.0.30 is already installed and up-to-date.
To reinstall 8.0.30, run:
  brew reinstall mysql
admin@gw-mac sb-mvn-rest-api % mysql --version
mysql  Ver 8.0.30 for macos12.4 on arm64 (Homebrew)
admin@gw-mac sb-mvn-rest-api % brew services start mysql
==> Tapping homebrew/services
Cloning into '/opt/homebrew/Library/Taps/homebrew/homebrew-services'...
remote: Enumerating objects: 2090, done.
remote: Total 2090 (delta 0), reused 0 (delta 0), pack-reused 2090
Receiving objects: 100% (2090/2090), 584.66 KiB | 3.56 MiB/s, done.
Resolving deltas: 100% (927/927), done.
Tapped 1 command (45 files, 739.2KB).
==> Successfully started `mysql` (label: homebrew.mxcl.mysql)
admin@gw-mac sb-mvn-rest-api % brew services      
Name          Status  User  File
mysql         started admin ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
postgresql@14 none          
admin@gw-mac sb-mvn-rest-api % 
admin@gw-mac sb-mvn-rest-api % brew info mysql
==> mysql: stable 8.0.30 (bottled)
Open source relational database management system
https://dev.mysql.com/doc/refman/8.0/en/
Conflicts with:
  mariadb (because mysql, mariadb, and percona install the same binaries)
  percona-server (because mysql, mariadb, and percona install the same binaries)
/opt/homebrew/Cellar/mysql/8.0.30 (312 files, 296.4MB) *
  Poured from bottle on 2022-08-31 at 07:36:11
From: https://github.com/Homebrew/homebrew-core/blob/HEAD/Formula/mysql.rb
License: GPL-2.0-only with Universal-FOSS-exception-1.0
==> Dependencies
Build: cmake ✘, pkg-config ✘
Required: icu4c ✔, libevent ✔, libfido2 ✔, lz4 ✔, openssl@1.1 ✔, protobuf ✔, zlib ✔, zstd ✔
==> Caveats
We've installed your MySQL database without a root password. To secure it run:
    mysql_secure_installation

MySQL is configured to only allow connections from localhost by default

To connect run:
    mysql -uroot

To restart mysql after an upgrade:
  brew services restart mysql
Or, if you don't want/need a background service you can just run:
  /opt/homebrew/opt/mysql/bin/mysqld_safe --datadir=/opt/homebrew/var/mysql
==> Analytics
install: 98,811 (30 days), 276,206 (90 days), 1,062,558 (365 days)
install-on-request: 98,592 (30 days), 275,561 (90 days), 1,059,252 (365 days)
build-error: 277 (30 days)
admin@gw-mac sb-mvn-rest-api % 
admin@gw-mac sb-mvn-rest-api % mysql_secure_installation

Securing the MySQL server deployment.

Connecting to MySQL using a blank password.

VALIDATE PASSWORD COMPONENT can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD component?

Press y|Y for Yes, any other key for No: 
Please set the password for root here.

New password: P@ssword!@#$%

Re-enter new password: P@ssword!@#$%
By default, a MySQL installation has an anonymous user,
allowing anyone to log into MySQL without having to have
a user account created for them. This is intended only for
testing, and to make the installation go a bit smoother.
You should remove them before moving into a production
environment.

Remove anonymous users? (Press y|Y for Yes, any other key for No) : 

 ... skipping.


Normally, root should only be allowed to connect from
'localhost'. This ensures that someone cannot guess at
the root password from the network.

Disallow root login remotely? (Press y|Y for Yes, any other key for No) : 

 ... skipping.
By default, MySQL comes with a database named 'test' that
anyone can access. This is also intended only for testing,
and should be removed before moving into a production
environment.


Remove test database and access to it? (Press y|Y for Yes, any other key for No) : 

 ... skipping.
Reloading the privilege tables will ensure that all changes
made so far will take effect immediately.

Reload privilege tables now? (Press y|Y for Yes, any other key for No) : 

 ... skipping.
All done! 
admin@gw-mac sb-mvn-rest-api % mysql --user=root --password
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 16
Server version: 8.0.30 Homebrew

Copyright (c) 2000, 2022, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
mysql> 
mysql> exit
Bye
admin@gw-mac sb-mvn-rest-api % 
```

# 2. Create and import Spring Boot project
```sh
admin@gw-mac sb-mvn-rest-api % ls -la employee
total 80
drwxr-xr-x@ 13 admin  staff    416 Aug 31 10:33 .
drwxr-xr-x   6 admin  staff    192 Aug 31 08:07 ..
-rw-r--r--   1 admin  staff   1967 Aug 31 10:14 .classpath
-rw-r--r--@  1 admin  staff    395 Aug 30 23:01 .gitignore
drwxr-xr-x@  3 admin  staff     96 Aug 30 23:01 .mvn
-rw-r--r--   1 admin  staff    832 Aug 31 10:14 .project
drwxr-xr-x   5 admin  staff    160 Aug 31 08:05 .settings
-rw-r--r--@  1 admin  staff   1124 Aug 30 23:01 HELP.md
-rwxr-xr-x@  1 admin  staff  10284 Aug 30 23:01 mvnw
-rw-r--r--@  1 admin  staff   6734 Aug 30 23:01 mvnw.cmd
-rw-r--r--@  1 admin  staff   1503 Aug 30 23:01 pom.xml
drwxr-xr-x@  4 admin  staff    128 Aug 30 23:01 src
drwxr-xr-x   4 admin  staff    128 Aug 31 08:05 target
admin@gw-mac sb-mvn-rest-api % 
```

# 3. Add sub-packages to the project
```sh
admin@gw-mac sb-mvn-rest-api % mkdir employee/src/main/java/com/example/employee/controller
admin@gw-mac sb-mvn-rest-api % mkdir employee/src/main/java/com/example/employee/service
admin@gw-mac sb-mvn-rest-api % mkdir employee/src/main/java/com/example/employee/model
admin@gw-mac sb-mvn-rest-api % mkdir employee/src/main/java/com/example/employee/repository
admin@gw-mac sb-mvn-rest-api % 
admin@gw-mac sb-mvn-rest-api % touch employee/src/main/java/com/example/employee/controller/test.java
admin@gw-mac sb-mvn-rest-api % touch employee/src/main/java/com/example/employee/model/test.java
admin@gw-mac sb-mvn-rest-api % touch employee/src/main/java/com/example/employee/repository/test.java 
admin@gw-mac sb-mvn-rest-api % touch employee/src/main/java/com/example/employee/service/test.java
```

# 4. Create table and configure MySQL details in Spring Boot
```sh
admin@gw-mac sb-mvn-rest-api % mysql --user=root --password
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 16
Server version: 8.0.30 Homebrew

Copyright (c) 2000, 2022, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 

mysql> SHOW databases;
+--------------------+
| Database           |
+--------------------+
| employee-schema    |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.01 sec)

mysql> use employee-schema;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> 
mysql> 
mysql> CREATE TABLE `employee-schema`.`employees` (`emp_id` int AUTO_INCREMENT,`first_name` varchar(255),`last_name` varchar(255),`email_id` varchar(255), PRIMARY KEY (emp_id));
Query OK, 0 rows affected (0.01 sec)

mysql> 
mysql> SHOW tables;
+---------------------------+
| Tables_in_employee-schema |
+---------------------------+
| employees                 |
+---------------------------+
1 row in set (0.00 sec)

mysql> 
mysql> exit
Bye
admin@gw-mac sb-mvn-rest-api % 
```


# 5. Create the model class

```sh
admin@gw-mac sb-mvn-rest-api % touch employee/src/main/java/com/example/employee/model/Employee.java
admin@gw-mac sb-mvn-rest-api % ls -l employee/src/main/java/com/example/employee/model/Employee.java
-rw-r--r--  1 admin  staff  64 Aug 31 13:30 employee/src/main/java/com/example/employee/model/Employee.java
admin@gw-mac sb-mvn-rest-api % 
```


# 6. Create the repository class
```sh
admin@gw-mac sb-mvn-rest-api % touch employee/src/main/java/com/example/employee/repository/EmployeeRepository.java
admin@gw-mac sb-mvn-rest-api % ls -l employee/src/main/java/com/example/employee/repository/EmployeeRepository.java
-rw-r--r--  1 admin  staff  0 Aug 31 14:44 employee/src/main/java/com/example/employee/repository/EmployeeRepository.java
admin@gw-mac sb-mvn-rest-api % 
```

# 7. Create the service class
```sh
admin@gw-mac sb-mvn-rest-api % touch employee/src/main/java/com/example/employee/service/EmployeeService.java      
admin@gw-mac sb-mvn-rest-api % ls -l employee/src/main/java/com/example/employee/service/EmployeeService.java
-rw-r--r--  1 admin  staff  0 Aug 31 15:23 employee/src/main/java/com/example/employee/service/EmployeeService.java
admin@gw-mac sb-mvn-rest-api % 
```

# 8. Create the controller class
```sh
admin@gw-mac sb-mvn-rest-api % touch employee/src/main/java/com/example/employee/controller/EmployeeController.java
admin@gw-mac sb-mvn-rest-api % ls -l employee/src/main/java/com/example/employee/controller/EmployeeController.java
-rw-r--r--  1 admin  staff  0 Aug 31 15:37 employee/src/main/java/com/example/employee/controller/EmployeeController.java
admin@gw-mac sb-mvn-rest-api % 
```

# 10. Run the application
```sh
admin@gw-mac employee % mvn compile
[INFO] Scanning for projects...
[INFO] 
[INFO] ------------------------< com.example:employee >------------------------
[INFO] Building employee 0.0.1-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
...
...
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.473 s
[INFO] Finished at: 2022-08-31T17:25:32+09:00
[INFO] ------------------------------------------------------------------------
admin@gw-mac employee % 
admin@gw-mac employee % mvn spring-boot:run
[INFO] Scanning for projects...
[INFO] 
[INFO] ------------------------< com.example:employee >------------------------
[INFO] Building employee 0.0.1-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
...
...
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  25.103 s
[INFO] Finished at: 2022-08-31T17:28:47+09:00
[INFO] ------------------------------------------------------------------------
admin@gw-mac employee % 
admin@gw-mac employee % mvn package                                  
[INFO] Scanning for projects...
[INFO] 
[INFO] ------------------------< com.example:employee >------------------------
[INFO] Building employee 0.0.1-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
...
...
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  3.590 s
[INFO] Finished at: 2022-08-31T17:27:09+09:00
[INFO] ------------------------------------------------------------------------
admin@gw-mac employee % 
admin@gw-mac employee % java -jar target/employee-0.0.1-SNAPSHOT.jar
...
...
^C2022-08-31 17:30:14.463  INFO 7885 --- [ionShutdownHook] j.LocalContainerEntityManagerFactoryBean : Closing JPA EntityManagerFactory for persistence unit 'default'
2022-08-31 17:30:14.464  INFO 7885 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown initiated...
2022-08-31 17:30:14.467  INFO 7885 --- [ionShutdownHook] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Shutdown completed.
admin@gw-mac employee % 
```