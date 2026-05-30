# Домашнее задание к занятию 5. «Практическое применение Docker» - Студент группы FOPS-42 Власов Владимир

### Инструкция к выполнению

1. Для выполнения заданий обязательно ознакомьтесь с [инструкцией](https://github.com/netology-code/devops-materials/blob/master/cloudwork.MD) по экономии облачных ресурсов. Это нужно, чтобы не расходовать средства, полученные в результате использования промокода.
3. **Своё решение к задачам оформите в вашем GitHub репозитории.**
4. В личном кабинете отправьте на проверку ссылку на .md-файл в вашем репозитории.
5. Сопроводите ответ необходимыми скриншотами.

---
## Примечание: Ознакомьтесь со схемой виртуального стенда [по ссылке](https://github.com/netology-code/shvirtd-example-python/blob/main/schema.pdf)

---

## Задача 0
1. Убедитесь что у вас НЕ(!) установлен ```docker-compose```, для этого получите следующую ошибку от команды ```docker-compose --version```
```
Command 'docker-compose' not found, but can be installed with:

sudo snap install docker          # version 24.0.5, or
sudo apt  install docker-compose  # version 1.25.0-1

See 'snap info docker' for additional versions.
```
В случае наличия установленного в системе ```docker-compose``` - удалите его.  
2. Убедитесь что у вас УСТАНОВЛЕН ```docker compose```(без тире) версии не менее v2.24.X, для это выполните команду ```docker compose version```  
###  **Своё решение к задачам оформите в вашем GitHub репозитории!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!**

## Ответ на вопрос 1 в задаче 0:


1. Убедимся что у меня НЕ(!) установлен ```docker-compose``` путем ввода команды ```docker-compose --version```
   
![d1](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d1.png)


## Ответ на вопрос 2 в задаче 0:

2. Произведем установку docker командой ```sudo snap install docker``` и проверим версию командой ```docker compose version```:
   

![d2](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d2.png)


## Задача 1
1. Сделайте в своем GitHub пространстве fork [репозитория](https://github.com/netology-code/shvirtd-example-python).

2. Создайте файл ```Dockerfile.python``` на основе существующего `Dockerfile`:
   - Используйте базовый образ ```python:3.12-slim```
   - Обязательно используйте конструкцию ```COPY . .``` в Dockerfile
   - Создайте `.dockerignore` файл для исключения ненужных файлов
   - Используйте ```CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "5000"]``` для запуска
   - Протестируйте корректность сборки
2.1 Используйте multistage сборку вместо single stage.
3. (Необязательная часть, *) Изучите инструкцию в проекте и запустите web-приложение без использования docker, с помощью venv. (Mysql БД можно запустить в docker run).
4. (Необязательная часть, *) Изучите код приложения и добавьте управление названием таблицы через ENV переменную.
---
### ВНИМАНИЕ!
!!! В процессе последующего выполнения ДЗ НЕ изменяйте содержимое файлов в fork-репозитории! Ваша задача ДОБАВИТЬ 5 файлов: ```Dockerfile.python```, ```compose.yaml```, ```.gitignore```, ```.dockerignore```,```bash-скрипт```. Если вам понадобилось внести иные изменения в проект - вы что-то делаете неверно!
---

## Ответ на вопрос 1 в задаче 1:

1. Сделал в своем GitHub пространстве fork [репозитория](https://github.com/netology-code/shvirtd-example-python)
   
![d3](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d3.png)

## Ответ на вопрос 2 в задаче 1:

Сделал локальный fork [репозитория](https://github.com/wlasoff/shvirtd-example-python)

![d4](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d4.png)

Создал файл ```Dockerfile.python``` на основе существующего `Dockerfile`:

![d5](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d5.png)

Соберем docker контейнер:

![d6](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d6.png)

Протестируем корректность сборки:

![d7](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d7.png)

## Ответ на вопрос 2.1 в задаче 1:

Пеерпишем файл ```Dockerfile.python```:

![d8](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d8.png)

Пересоберем docker контейнер не забыв удалить предыдущую сборку и протестируем ее:

![d9](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d9.png)

Создадим файл `.dockerignore`:

![d10](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d10.png)

## Задача 2 (*)
1. Создайте в yandex cloud container registry с именем "test" с помощью "yc tool" . [Инструкция](https://cloud.yandex.ru/ru/docs/container-registry/quickstart/?from=int-console-help)
2. Настройте аутентификацию вашего локального docker в yandex container registry.
3. Соберите и залейте в него образ с python приложением из задания №1.
4. Просканируйте образ на уязвимости.
5. В качестве ответа приложите отчет сканирования.

## Задача 3
1. Изучите файл "proxy.yaml"
2. Создайте в репозитории с проектом файл ```compose.yaml```. С помощью директивы "include" подключите к нему файл "proxy.yaml".
3. Опишите в файле ```compose.yaml``` следующие сервисы: 

- ```web```. Образ приложения должен ИЛИ собираться при запуске compose из файла ```Dockerfile.python``` ИЛИ скачиваться из yandex cloud container registry(из задание №2 со *). Контейнер должен работать в bridge-сети с названием ```backend``` и иметь фиксированный ipv4-адрес ```172.20.0.5```. Сервис должен всегда перезапускаться в случае ошибок.
Передайте необходимые ENV-переменные для подключения к Mysql базе данных по сетевому имени сервиса ```web``` 

- ```db```. image=mysql:8. Контейнер должен работать в bridge-сети с названием ```backend``` и иметь фиксированный ipv4-адрес ```172.20.0.10```. Явно перезапуск сервиса в случае ошибок. Передайте необходимые ENV-переменные для создания: пароля root пользователя, создания базы данных, пользователя и пароля для web-приложения.Обязательно используйте уже существующий .env file для назначения секретных ENV-переменных!

2. Запустите проект локально с помощью docker compose , добейтесь его стабильной работы: команда ```curl -L http://127.0.0.1:8090``` должна возвращать в качестве ответа время и локальный IP-адрес. Если сервисы не стартуют воспользуйтесь командами: ```docker ps -a ``` и ```docker logs <container_name>``` . Если вместо IP-адреса вы получаете информационную ошибку --убедитесь, что вы шлете запрос на порт ```8090```, а не 5000.

5. Подключитесь к БД mysql с помощью команды ```docker exec -ti <имя_контейнера> mysql -uroot -p<пароль root-пользователя>```(обратите внимание что между ключем -u и логином root нет пробела. это важно!!! тоже самое с паролем) . Введите последовательно команды (не забываем в конце символ ; ): ```show databases; use <имя вашей базы данных(по-умолчанию virtd, как это указано в .env)>; show tables; SELECT * from requests LIMIT 10;```. Примечание: таблица в БД создается после первого поступившего запроса к приложению.

6. Остановите проект. В качестве ответа приложите скриншот sql-запроса.

## Ответ на вопрос 1 в задаче 3:

Изучил файл "proxy.yaml".
   
![d11](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d11.png)

## Ответ на вопрос 2 и 3 в задаче 3:

Создал в репозитории файл ```compose.yaml``` согласно условий задачи:
   
![d12](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d12.png)

## Ответ на вопрос 4 в задаче 3:

Запустил проект локально с помощью docker compose в стабильном режиме работы:
   
![d13](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d13.png)

![d14](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d14.png)

Получили в результате ответ:

![d15](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d15.png)

Проверим в браузере:

![d15_](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d15_.png)

## Ответ на вопрос 5 в задаче 3:

Подключимся к БД mysql:
   
![d16](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d16.png)

Вводим команды и получаем:

![d17](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d17.png)

## Ответ на вопрос 6 в задаче 3:

Остановим проект:
   
![d18](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d18.png)

Больше запросы делать не можем:

![d19](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/d19.png)

## Задача 4
1. Запустите в Yandex Cloud ВМ (вам хватит 2 Гб Ram).
2. Подключитесь к Вм по ssh и установите docker.
3. Напишите bash-скрипт, который скачает ваш fork-репозиторий в каталог /opt и запустит проект целиком.
4. Зайдите на сайт проверки http подключений, например(или аналогичный): ```https://check-host.net/check-http``` и запустите проверку вашего сервиса ```http://<внешний_IP-адрес_вашей_ВМ>:8090```. Таким образом трафик будет направлен в ingress-proxy. Трафик должен пройти через цепочки: Пользователь → Internet → Nginx → HAProxy → FastAPI(запись в БД) → HAProxy → Nginx → Internet → Пользователь
5. (Необязательная часть) Дополнительно настройте remote ssh context к вашему серверу. Отобразите список контекстов и результат удаленного выполнения ```docker ps -a```
6. Повторите SQL-запрос на сервере и приложите скриншот и ссылку на fork.

## Ответ на вопрос 1 в задаче 4:

Создал виртуальную машину в Yandex Cloud:

![v1](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/v1.png)

## Ответ на вопрос 2 в задаче 4:

Подключимся к виртуальной машине в Yandex Cloud:

![v2](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/v2.png)

## Ответ на вопрос 3 в задаче 4:

Написал bash-скрипт, который скачает мой репозиторий https://github.com/wlasoff/shvirtd-example-python в каталог /opt и запустит проект целиком:

![v3](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/v3.png)

Запускаем скрипт:

![v4](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/v4.png)

Проверяем работу нашего Docker контейнера на виртуальной машине в Yandex Cloud:

![v5](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/v5.png)

## Ответ на вопрос 4 в задаче 4:

Проверяем работу нашего Docker контейнера в браузере:

![v6](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/v6.png)


## Ответ на вопрос 5 в задаче 4:

![v_](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/v_.png)


## Ответ на вопрос 6 в задаче 4:


![v7](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/v7.png)


## Задача 5 (*)
1. Напишите и задеплойте на вашу облачную ВМ bash скрипт, который произведет резервное копирование БД mysql в директорию "/opt/backup" с помощью запуска в сети "backend" контейнера из образа ```schnitzler/mysqldump``` при помощи ```docker run ...``` команды. Подсказка: "документация образа."
2. Протестируйте ручной запуск
3. Настройте выполнение скрипта раз в 1 минуту через cron, crontab или systemctl timer. Придумайте способ не светить логин/пароль в git!!
4. Предоставьте скрипт, cron-task и скриншот с несколькими резервными копиями в "/opt/backup"

## Задача 6
Скачайте docker образ ```hashicorp/terraform:latest``` и скопируйте бинарный файл ```/bin/terraform``` на свою локальную машину, используя dive и docker save.
Предоставьте скриншоты  действий .

## Решение задачи 6:

Скачиваю образ:
   
![t1](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/t1.png)

Сохраняю образ в tar-архив:

![t2](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/t2.png)

Создаю папку и распаковываю туда структуру слоев

![t3](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/t3.png)

Анализирую извлеченный образ с помощью dive изучая слои образа (вкладка Layers). Ищем слой, в котором появляется файл /bin/terraform:

![t4](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/t4.png)

К сожалению в архиве нет нужного слоя:

![t4_](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/t4_.png)

Извлечем бинарный файл c помощью docker save с проверкой результата:

![t5](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/t5.png)

## Задача 6.1
Добейтесь аналогичного результата, используя docker cp.  
Предоставьте скриншоты  действий .

## Решение задачи 6.1:

Создаем контейнер без запуска:
   
![t6](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/t6.png)

Копируем бинарный файл:
   
![t7](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/t7.png)

Выполним проверку:
![t8](https://github.com/wlasoff/netology-devops-home-docker-in-practice/blob/main/img/t8.png)

## Задача 6.2 (**)
Предложите способ извлечь файл из контейнера, используя только команду docker build и любой Dockerfile.  
Предоставьте скриншоты  действий .

## Задача 7 (***)
Запустите ваше python-приложение с помощью runC, не используя docker или containerd.  
Предоставьте скриншоты  действий .

