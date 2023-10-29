# Домашнее задание к занятию "Очереди RabbitMQ" - Одинцов Игорь

### Задание 1. Установка RabbitMQ
Используя Vagrant или VirtualBox, создайте виртуальную машину и установите RabbitMQ. Добавьте management plug-in и зайдите в веб-интерфейс.
Итогом выполнения домашнего задания будет приложенный скриншот веб-интерфейса RabbitMQ.

### Ответ
![Z1](https://github.com/Bestenar/11.4-RabbitMQ-hw/assets/111271419/3b7f44f4-330d-4efa-82b4-649c9d8c826c)

---

### Задание 2. Отправка и получение сообщений
Используя приложенные скрипты, проведите тестовую отправку и получение сообщения. Для отправки сообщений необходимо запустить скрипт producer.py.

```ruby
$ pip install pika
```
Зайдите в веб-интерфейс, найдите очередь под названием hello и сделайте скриншот. После чего запустите второй скрипт consumer.py и сделайте скриншот результата выполнения скрипта.

*В качестве решения домашнего задания приложите оба скриншота, сделанных на этапе выполнения.*

### Ответ
![Z2 1](https://github.com/Bestenar/11.4-RabbitMQ-hw/assets/111271419/b626befc-d124-4fe7-aa1c-7d17398bf7ef)
![Z2 2](https://github.com/Bestenar/11.4-RabbitMQ-hw/assets/111271419/7f434490-9553-4a5a-b055-4c4b83256db4)

---

### Задание 3. Подготовка HA кластера
Используя Vagrant или VirtualBox, создайте вторую виртуальную машину и установите RabbitMQ. Добавьте в файл hosts название и IP-адрес каждой машины, чтобы машины могли видеть друг друга по имени.

Пример содержимого hosts файла:
```ruby
$ cat /etc/hosts
192.168.0.10 rmq01
192.168.0.11 rmq02
```
После этого ваши машины могут пинговаться по имени.
Затем объедините две машины в кластер и создайте политику ha-all на все очереди.

*В качестве решения домашнего задания приложите скриншоты из веб-интерфейса с информацией о доступных нодах в кластере и включённой политикой.*

Также приложите вывод команды с двух нод:
```ruby
$ rabbitmqctl cluster_status
```
Для закрепления материала снова запустите скрипт producer.py и приложите скриншот выполнения команды на каждой из нод:
```ruby
$ rabbitmqadmin get queue='hello'
```
После чего попробуйте отключить одну из нод, желательно ту, к которой подключались из скрипта, затем поправьте параметры подключения в скрипте consumer.py на вторую ноду и запустите его.

### Ответ
Создание второй машины, настройка hosts файла и объединение в кластер:
![Z3 1](https://github.com/Bestenar/11.4-RabbitMQ-hw/assets/111271419/79c989b0-84e6-405a-a84c-fdf75e978357)
![Z3 2](https://github.com/Bestenar/11.4-RabbitMQ-hw/assets/111271419/31a88444-0a20-4330-970f-2ae948ea58ce)

Вывод команды с двух нод:
```ruby
$ rabbitmqctl cluster_status
```
![Z3 3](https://github.com/Bestenar/11.4-RabbitMQ-hw/assets/111271419/e8cef2a6-3309-4736-967b-e9d433aa7ec7)
![Z3 4](https://github.com/Bestenar/11.4-RabbitMQ-hw/assets/111271419/9ea2aa09-fe19-4312-9646-5bf30da765ca)

Запустите скрипт producer.py на каждой из нод:
```ruby
$ rabbitmqadmin get queue='hello'
```
![Z3 5](https://github.com/Bestenar/11.4-RabbitMQ-hw/assets/111271419/a6e12a0a-2326-4c36-a3a7-8974d70848d4)
![3 6](https://github.com/Bestenar/11.4-RabbitMQ-hw/assets/111271419/c31c3d13-1296-42ff-a354-c57061f54e09)

Попробуйте отключить одну из нод, желательно ту, к которой подключались из скрипта, затем поправьте параметры подключения в скрипте consumer.py на вторую ноду и запустите его.

![Z3 7](https://github.com/Bestenar/11.4-RabbitMQ-hw/assets/111271419/9e34633f-555b-4682-ac46-466b75cfe6ab)

