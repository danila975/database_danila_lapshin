# задание 2


## удаление из таблицы

test=# delete from users where name = 'данила';

DELETE 1


## обновление таблицы

test=# update users set email = 'dmitry@gmail.com' where name = 'дима';

UPDATE 1


## структура двух таблиц, кроме users

test=# select * from messages;

 message_id |        message_text        | user_name | chat_name 
------------+----------------------------+-----------+-----------
          1 | привет                     | дима      | vk
          2 | как дела                   | мария     | почта
          3 | пока                       | дима      | vk
          4 | можешь меня встретить      | мария     | почта
          5 | думаю тебе будет интересно | вася      | telegramm
(5 строк)

test=# select * from chats;

 chat_id | chat_name 
---------+-----------
       1 | telegramm
       2 | vk
       3 | почта
(3 строки)


## использование where, group by и join

test=# select user_id, user_name, lastname, chat_id, message_id, message_text from messages inner join users on messages.user_name = users.name inner join chats on messages.chat_name = chats.chat_name where name = 'дима' group by user_id, user_name, chat_id, message_id;
 user_id | user_name | lastname | chat_id | message_id | message_text 
---------+-----------+----------+---------+------------+--------------
       2 | дима      | иванов   |       2 |          1 | привет
       2 | дима      | иванов   |       2 |          3 | пока
(2 строки)


## пытался вывести chat_name, не понял почему не получилось

test=# select user_id, user_name, lastname, chat_name, message_id, message_text from messages inner join users on messages.user_name = users.name inner join chats on messages.chat_name = chats.chat_name where name = 'дима' group by user_id, user_name, chat_name, message_id;
ОШИБКА:  неоднозначная ссылка на столбец "chat_name"
