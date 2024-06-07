# mysql command line tool.
# Index
- [mysql command line tool.](#mysql-command-line-tool.)
- [Kali MariaDB Installation and Setup.](#kali-mariadb-installation-and-setup.)
# mysql command line tool.
The mysql utility is used to authenticate to and interact with a MySQL/MariaDB database. The `-u` flag is used to supply the username and the `-p` flag for the password. 
> The -p flag should be passed empty, so we are prompted to enter the password and do not pass it directly on the command line since it could be stored in cleartext in the bash_history file.
The default MySQL/MariaDB port is (3306), but it can be configured to another port. It is specified using an uppercase `P`, unlike the lowercase `p` used for passwords.<br />
`-u` **->** Username.<br />
`-p` **->** Password.<br />
`-h` **->** Host. <br />
`-P` **->** Port.<br />
<img src="https://github.com/alejandro-pentest/Hacking-Web/assets/161533623/9286e439-9d67-4de1-bae9-196331f6b5d2" width="700">

When we do not specify a host, it will default connect to the localhost server.

We can view which privileges we have using the `SHOW GRANTS` command. (in this case we have full privs cause we are logged as root).

![2](https://github.com/alejandro-pentest/Hacking-Web/assets/161533623/774fa9c3-649a-45dd-a1cd-7dd4f6787a76)<br />

<br />`SHOW DATABASES` **->** Will display all the databases that this db is containing.<br />
![3](https://github.com/alejandro-pentest/Hacking-Web/assets/161533623/689df40f-11dd-4bd6-91a7-eca2ae8a3124)<br />
<br /> After seen which databases does this database contains, we can select or "use" one of them `use <DBName>;`.<br />
![7](https://github.com/alejandro-pentest/Hacking-Web/assets/161533623/254c36e4-d829-4e3e-90e2-80fceb29c247)<br />
<br /> Once this database is selected we can list all the tables from the database `SHOW TABLES;`<br />
![4](https://github.com/alejandro-pentest/Hacking-Web/assets/161533623/04e59813-fd27-41c5-aadb-df454a5ff8f8)<br />
<br />Now is the time to finally see what secrets this database contains. We can use `describe <table>;` to retrieve all the information we can extract.<br />
![5](https://github.com/alejandro-pentest/Hacking-Web/assets/161533623/813cbcd5-5f1b-4af5-902c-6105ec7d8ba3)<br />
<br /> If we want to extract all the data from the table we can use `select * FROM TABLE;`.
![6](https://github.com/alejandro-pentest/Hacking-Web/assets/161533623/17fd836d-a020-439e-b3c5-df11d838beba)

----------------------

## Kali MariaDB Installation and Setup.
It's possible that we find out that we can connect to remote DB, but we cannot connect to our own database. That's probably because we have the mysql-client ready to use, but we have not installed or 
set up mysql-server. If this is our case we can see the next alert ```ERROR 2002 (HY000): Can't connect to local server through socket '/run/mysqld/mysqld.sock' (2)```.
Next, we will see how to install, set up, and connect to our own local database in Kali Linux OS.




```mysql
apt-get -y install mariadb-server
```
![10](https://github.com/alejandro-pentest/Hacking-Web/assets/161533623/b73e5513-9f3a-402e-81fd-df89d2fd302f)


```bash
service mysql start
```
![8](https://github.com/alejandro-pentest/Hacking-Web/assets/161533623/db97fe20-b419-48cb-abf7-2d543a28045a)


```bash
mysql_secure_installation
```
<img src="https://github.com/alejandro-pentest/Hacking-Web/assets/161533623/7c585bbe-6ab4-4f72-bda0-a531d35d67d3" width="500">


We can finally try to connect.
![16](https://github.com/alejandro-pentest/Hacking-Web/assets/161533623/8ef7bc9d-daea-4de1-8e15-6564953f9924)





