# Решение

1. Переходим на сайт [Apache Kafka](https://kafka.apache.org/downloads) и скачиваем последнию версию. Скачав архив выполняем следующие шаги:
    - Распаковываем скачанный архив 
    ```shell
    tar -xzf kafka kafka_2.13-3.4.0.tgz
    ```
    - Перемещаем папку в удобное для нас место (я используя папку */home/Application/*)
    ```shell
    mv kafka_2.13-3.4.0 ../Application/
    ```
 ![Консоль](/task-01/images/image1.png)

 2. Запускаем сервер **ZooKeeper**
 ```shell
 ./zookeeper-server-start.sh ../config/zookeeper.properties
 ```
 ![Запуск ZooKeeper](/task-01/images/image2.png)

 3. Запуск брокера **Kafka**
 ```shell
 ./kafka-server-start.sh ../config/server.properties
 ```
 ![Запуск брокера Kafka](/task-01/images/image3.png)

 4. Создаем топик **test**
 ```shell
 ./kafka-topics.sh --create --bootstrap-server localhost:9092 --topic test
 ```
 ![Создание топика](/task-01/images/image4.png)

 5. Подключаемся к топику producer-а, что бы отправить сообщения
 ```shell
 ./kafka-console-producer.sh --bootstrap-server localhost:9092 --topic test
 ```

 6. Подключаем к топик **test** consumer-а, чтобы прочитать сообщения
 ```shell
 ./kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test --from-beginning
 ```
 ![Получение и отправка сообщений](/task-01/images/image5.png)