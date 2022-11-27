Install the Mysql driver using

go get github.com/go-sql-driver/mysql

Connect to mysql server

mysql -u root

Set password for root

ALTER user 'root'@'localhost' IDENTIFIED BY 'password';
flush privileges;

create database test;
use test;
create table test(id INT NOT NULL);

