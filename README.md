# Mission 3

## Part 1

[Link to video](https://drive.google.com/file/d/1sPaQd_R8uSC6GYf8ppHQ7qA81oRz7Gor/view?usp=sharing)

## Part 2

[Link to video](https://drive.google.com/file/d/1Ey9h68Xeqx9RxqakasZH9Dgh0J_eFJT8/view?usp=sharing)

## Part3

1. получить список юзернеймов пользователей
```
SELECT username FROM users;
```
2. получить кол-во отправленных сообщений каждым пользователем:
    username - number of sent messages
```
SELECT 
  u.username, 
  COUNT(m.id) AS "number of sent messages"
FROM users u
LEFT JOIN messages m ON u.id = m.from
GROUP BY u.username
ORDER BY "number of sent messages" DESC;
```
3. Получить пользователя с самым большим кол-вом полученных сообщений и само количество
    username - number of received messages
```
SELECT 
  u.username, 
  COUNT(m.id) AS "number of received messages"
FROM users u
LEFT JOIN messages m ON u.id = m.to
GROUP BY u.username
ORDER BY "number of received messages" DESC
LIMIT 1;
```
4. Получить среднее кол-во сообщений, отправленное каждым пользователем
```
SELECT 
  AVG(sent_count) AS "average messages per user"
FROM (
  SELECT 
    u.id, 
    COUNT(m.id) AS sent_count
  FROM users u
  LEFT JOIN messages m ON u.id = m.from
  GROUP BY u.id
) AS user_sent_counts;
```
