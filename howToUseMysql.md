#Mysql
[http://dev.mysql.com/doc/refman/5.7/en/creating-database.html]()

##base cmd
mysql -u root -h localhost -p

use test;

show tables;

##how to backup 
mysqldump -u root -p test > test.sql;