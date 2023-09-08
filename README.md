# Пояснительная записка по выполнению Дипломной работы профессии «Тестировщик ПО»
[Задание](https://github.com/netology-code/qa-diploma)

## Документы
* [План автоматизации](https://github.com/BOYKO-QA-60/QA-60_Diplom_BSS/blob/main/documents/Plan.md)
* [Отчёт по итогам тестирования](в разработке)
* [Отчёт об автоматизации](в разработке)

## Описание приложения
Приложение представляет собой веб-сервис, который предлагает купить тур по определённой цене двумя способами:
Обычная оплата по дебетовой карте.
Уникальная технология: выдача кредита по данным банковской карты.

Само приложение не обрабатывает данные по картам, а пересылает их банковским сервисам:

* сервису платежей, далее Payment Gate;

* кредитному сервису, далее Credit Gate.
  
Приложение в собственной СУБД должно сохранять информацию о том, успешно ли был совершён платёж и каким способом. Данные карт при этом сохранять не допускается.

## Инструкция по запуску тестов

1. Клонировать проект на личную машину (компьютер) при помощи терминала Git Bash, введите команду:   
    `git clone git@github.com:BOYKO-QA-60/QA-60_Diplom_BSS.git`


2. Для запуска контейнеров Docker, воспользуемся альтернативным путем:
   
a) Открыть программу `PutTy`. 

b) Подключиться к `виртуальной машине LINUX (НЕТОЛОГИИ)`, введите:

 * ip-машины:`185.119.57.9` , 
 * `Логин` и `Пароль` – предоставленный руководителем.
   
c) После подключения к виртуальной машине, необходимо выполнить следящее: 

 * клонировать проект на `виртуальную машину LINUX (НЕТОЛОГИИ)`, введите команду:
   
`git clone https://github.com/BOYKO-QA-60/QA-60_Diplom_BSS.git`
   
 * Далее, команду:
    `cd  QA-60_Diplom_BSS`,
   таким образом мы указали папку(место),где расположен файл docker-compose и где будет сохранена информация и построенных контейнеров. 

d) Запустить контейнеры командой:
   `docker-compose up --build`


3. Открыть клонированный проект на личной машине в `IntelliJ IDEA`
   

4. Для запуска сервиса с указанием пути к базе данных использовать следующие команды:
   
* для mysql:
   `java "-Dspring.datasource.url=jdbc:mysql://185.119.57.9:9999/app" -jar aqa-shop.jar`
  
* для postgresql:
   `java "-Dspring.datasource.url=jdbc:postgresql://185.119.57.9:9999/app" -jar aqa-shop.jar`
  

5. Sut открывается по адресу `http://localhost:8080/`
  

6. Запуск тестов стоит выполнить с параметрами, указав путь к базе данных в командной строке:
   
  * для mysql:
     `./gradlew clean test "-Ddb.url=jdbc:mysql://185.119.57.9:9999/app"`
    
  * для postgresql:
     `./gradlew clean test "-Ddb.url=jdbc:postgresql://185.119.57.9:9999/app"`
    

7. Для формирования отчета (Allure), после выполнения тестов выполнить команду:
    `./gradlew allureReport`


8. Сформировать Gradle-репорт можно командой:
   `./gradlew clean build`
 

9. После завершения тестирования завершить работу приложения (CTRL+C) и остановить контейнеры командой:
    `docker-compose down`
