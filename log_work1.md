# работа 1

## создание пользователя
postgres=# create user test1 with login password '123';
CREATE ROLE

## создание базы данных
postgres=# create database test;
CREATE DATABASE

## смена владельца базы данных на созданного пользователя
postgres=# alter database test owner to test1;
ALTER DATABASE

## подключение к базе данных
postgres=# \q
postgres@danilalapsin:~$ psql test
psql (15.6 (Debian 15.6-0+deb12u1))
Введите "help", чтобы получить справку.

## создание таблицы
test=# CREATE TABLE USERS (USER_ID SERIAL PRIMARY KEY, EMAIL VARCHAR(255), NAME VARCHAR(100), LASTNAME VARCHAR(100));
CREATE TABLE

## добавление данных в таблицу
test=# INSERT INTO USERS (EMAIL, NAME, LASTNAME) VALUES ('GMAIL', 'DANILA', 'LAPSIN');
INSERT 0 1

## вывод таблицы
test=# SELECT * FROM USERS;
 user_id | email |  name  | lastname 
---------+-------+--------+----------
       1 | GMAIL | DANILA | LAPSIN
(1 строка)

test=# 

## попытка войти под именем созданного пользователя
postgres@danilalapsin:~$ psql test test1
psql: ошибка: подключиться к серверу через сокет "/var/run/postgresql/.s.PGSQL.5432" не удалось: ВАЖНО:  пользователь "test1" не прошёл проверку подлинности (Peer)
postgres@danilalapsin:~$ psql -U test1 -d test -W
Пароль: 
psql: ошибка: подключиться к серверу через сокет "/var/run/postgresql/.s.PGSQL.5432" не удалось: ВАЖНО:  пользователь "test1" не прошёл проверку подлинности (Peer)
postgres@danilalapsin:~$ 

## удаление всего
postgres@danilalapsin:~$ psql test
psql (15.6 (Debian 15.6-0+deb12u1))
Введите "help", чтобы получить справку.

test=# drop table users;
DROP TABLE
test=# 

postgres@danilalapsin:~$ psql
psql (15.6 (Debian 15.6-0+deb12u1))
Введите "help", чтобы получить справку.

postgres=# drop database test;
DROP DATABASE
postgres=# drop user test1;
DROP ROLE
