FROM mysql:5.7

ENV MYSQL_ROOT_PASSWORD = root

RUN mysql -h127.0.0.1 -P3306 -uroot -proot

RUN create database testdb;

EXPOSE 3306