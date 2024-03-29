# План по выполнению дипломной работы по автоматизации тестирования приложения "Путешествие дня"

**Цель дипломной работы:**
Автоматизировать сценарии (позитивные и негативные) покупки тура через Приложение.

**Задачи дипломной работы:**

1. Прописать и реализовать перечень автоматизируемых сценариев;
2. Перечислить используемые инструменты с обоснованием выбора;
3. Описать возможные риски при автоматизации;
4. Спрогнозировать интервальную оценку с учётом рисков в часах;
5. Спрогнозировать план сдачи работы.

## Перечень автоматизируемых сценариев ##
### Валидные данные:
1. Номер карты, цифры 16 шт.
2. Месяц, 01-12, но не раньше текущего.
3. Год, последние 2 цифры года, но не раньше текущего, и не более 5 лет от текущего.
4. Владелец, буквенные символы латинского алфавита.
5. CVC/CVV, любое 3-х  (трехзначное) число.

### Позитивные сценарии:
1. Оплата тура с валидной картой с статусом "APPROVED" :
* Номер карты: 4444 4444 4444 4441. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление всплывающего окна "Операция одобрена Банком", запись со статусом "APPROVED" в базе данных.

2. Кредит за тур с валидной картой с статусом "APPROVED» :
* Номер карты: 4444 4444 4444 4441. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление всплывающего окна "Операция одобрена Банком", запись со статусом "APPROVED" в базе данных.

3. Оплата тура с валидной картой со статусом "DECLINED":
* Номер карты: 4444 4444 4444 4442. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление всплывающего окна "Ошибка! Банк отказал в проведении операции", запись со статусом "DECLINED" в базе данных .

4. Кредит за тур с валидной картой со статусом "DECLINED":
* Номер карты: 4444 4444 4444 4442. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление всплывающего окна "Ошибка! Банк отказал в проведении операции", запись со статусом "DECLINED" в базе данных.

### Негативные сценарии:
1. Оплата тура по несуществующей карте:
* Номер карты: 4444 4444 4444 4440. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление всплывающего окна "Ошибка! Банк отказал в проведении операции", отсутствие записи в базе данных.

2. Кредит за тур по несуществующей карте:
* Номер карты: 4444 4444 4444 4440. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление всплывающего окна "Ошибка! Банк отказал в проведении операции", отсутствие записи в базе данных.

3. Оплата тура по не полностью заполненной карте:
* Номер карты: 4444 4444 4444 444. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверный формат", отсутствие записи в базе данных.

4. Кредит за тур по не полностью заполненной карте:
* Номер карты: 4444 4444 4444 444. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверный формат", отсутствие записи в базе данных.

5. Оплата тура по карте с истекшим сроком действия (месяц):
* Номер карты: 4444 4444 4444 4441, Месяц любой прошлом или текущем году. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверно указан срок действия карты", отсутствие записи в базе данных.

6. Кредит за тур по карте с истекшим сроком действия (месяц):
* Номер карты: 4444 4444 4444 4441, Месяц любой в прошлом или текущем году. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверно указан срок действия карты", отсутствие записи в базе данных.

7. Оплата тура по карте с не валидным месяцем 00:
* Номер карты: 4444 4444 4444 4441, Месяц: 00. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверно указан срок действия карты", отсутствие записи в базе данных.

8. Кредит за тур по карте с не валидным месяцем 00:
* Номер карты: 4444 4444 4444 4441, Месяц: 00. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверно указан срок действия карты", отсутствие записи в базе данных.

9. Оплата тура по карте с незаполненным полем месяц:
* Номер карты: 4444 4444 4444 4441, Месяц не заполнен. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверный формат", отсутствие записи в базе данных.

10. Кредит за тур по карте с незаполненным полем месяц:
* Номер карты: 4444 4444 4444 4441, Месяц не заполнен. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверный формат", отсутствие записи в базе данных.

11. Оплата тура по карте с истекшим сроком действия (год):
* Номер карты: 4444 4444 4444 4441, Год: предыдущий год от текущего. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Истёк срок действия карты", отсутствие записи в базе данных.

12. Кредит за тур по карте с истекшим сроком действия (год):
* Номер карты: 4444 4444 4444 4441, Год: предыдущий год от текущего. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Истёк срок действия карты", отсутствие записи в базе данных.

13. Оплата тура по карте с годом + 6 лет от текущего:
* Номер карты: 4444 4444 4444 4441, Год: + 6 лет, от текущего года. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверно указан срок действия карты", отсутствие записи в базе данных.

14. Кредит за тур по карте с годом + 6 лет от текущего:
* Номер карты: 4444 4444 4444 4441, Год: + 6 лет от текущего года. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверно указан срок действия карты", отсутствие записи в базе данных.

15. Оплата тура по карте с незаполненным полем год :
* Номер карты: 4444 4444 4444 4441, Год: не заполнено. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверно указан срок действия карты", отсутствие записи в базе данных.

16. Кредит за тур по карте с незаполненным полем год :
* Номер карты: 4444 4444 4444 4441, Год: не заполнено. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверно указан срок действия карты", отсутствие записи в базе данных.

17. Оплата тура с вводом цифр в поле Владелец:
* Номер карты: 4444 4444 4444 4441, В поле владелец: ввести цифры. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Поле обязательно для заполнения", отсутствие записи в базе данных.

18. Оплата тура с вводом специальных символов в поле Владелец:
* Номер карты: 4444 4444 4444 4441, В поле владелец: ввести специальные символы. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Поле обязательно для заполнения", отсутствие записи в базе данных.

19. Оплата тура с пустым полем Владелец:
* Номер карты: 4444 4444 4444 4441, Поле владелец оставить пустым. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Поле обязательно для заполнения", отсутствие записи в базе данных.

20. Кредит за тур с вводом цифр в поле Владелец:
* Номер карты: 4444 4444 4444 4441, В поле владелец: ввести цифры. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Поле обязательно для заполнения", отсутствие записи в базе данных.

21. Кредит за тур с вводом специальных символов поле Владелец:
* Номер карты: 4444 4444 4444 4441, В поле владелец: ввести специальные символы. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Поле обязательно для заполнения", отсутствие записи в базе данных.

22. Кредит за тур с пустым полем Владелец:
* Номер карты: 4444 4444 4444 4441, Поле владелец оставить пустым. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Поле обязательно для заполнения", отсутствие записи в базе данных.

23. Оплата тура с вводом одной цифры в поле CVC/CVV :
* Номер карты: 4444 4444 4444 4441, CVC: 0 . Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверный формат", отсутствие записи в базе данных.

24. Оплата тура с вводом двух цифр в поле CVC/CVV :
* Номер карты: 4444 4444 4444 4441, CVC: 11 . Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверный формат", отсутствие записи в базе данных.

25. Оплата тура с пустым значением в поле CVC/CVV :
* Номер карты: 4444 4444 4444 4441, Поле CVC оставить пустым. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверный формат", отсутствие записи в базе данных.

26. Кредит за тур с вводом одной цифры в поле CVC/CVV :
* Номер карты: 4444 4444 4444 4441, CVC: 0 . Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверный формат", отсутствие записи в базе данных.

27. Кредит за тур с вводом двух цифр в поле CVC/CVV :
* Номер карты: 4444 4444 4444 4441, CVC: 11 . Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверный формат", отсутствие записи в базе данных.

28. Кредит за тур с пустым значением в поле CVC/CVV :
* Номер карты: 4444 4444 4444 4441, Поле CVC оставить пустым. Остальные данные валидные. Нажать `ПРОДОЛЖИТЬ`.
  Ожидаемый результат: Появление сообщения об ошибке "Неверный формат", отсутствие записи в базе данных.

29. Оплата тура с незаполненными полями:
* Все поля пустые. Нажать продолжить.
  Ожидаемый результат: Появление сообщения об ошибке "Неверный формат" во всех полях, отсутствие записи в базе данных.

30. Кредит за тур с незаполненными полями:
* Все поля пустые. Нажать продолжить.
  Ожидаемый результат: Появление сообщения об ошибке "Неверный формат" во всех полях, отсутствие записи в базе данных.

## Перечень используемых инструментов

#### IntelliJ IDEA:
Интегрированная среда разработки (IDE) для Java, которую мы используем для разработки и отладки нашего проекта.

#### Gradle:
Gradle является мощной системой автоматизации сборки и управления зависимостями, которая позволяет эффективно управлять проектом и его зависимостями, делая процесс сборки более удобным и надежным.

#### JUnit:
JUnit — это платформа для написания и запуска авто-тестов в Java. Она широко используется в сообществе разработчиков и имеет обширную поддержку. JUnit обладает простым и понятным синтаксисом, а также предоставляет множество возможностей для проверки функциональности кода.

#### Selenide:
Selenide является мощным фреймворком для автоматизированного тестирования веб-приложений. Он обеспечивает простоту и удобство в использовании, предоставляет богатый набор функций для взаимодействия с веб-элементами и обладает хорошей документацией.

#### DockerCompose:
DockerCompose позволяет устанавливать и запускать нужные базы данных и другие сервисы в контейнерах, обеспечивая легкость развертывания тестового окружения. Это значительно упрощает процесс настройки и подготовки окружения для тестирования.

#### Allure:
Allure — это фреймворк для создания красивых и информативных отчетов о прогонах тестов. Он предоставляет детальную информацию о результатах тестирования, что делает процесс отладки и анализа проблем более удобным.

#### PostgreSQL, MySQL системы управления базами данных.:
PostgreSQL и MySQL являются популярными и надежными системами управления базами данных, широко используемыми в веб-разработке. Они обеспечивают хранение и обработку тестовых данных, что позволяет проводить комплексное тестирование функциональности, включая взаимодействие с базой данных.

## Перечень и описание возможных рисков при автоматизации:

1. Из-за отсутствия технического задания и документации трудно понять, как приложение должно работать, что является багом, а что нет.
2. Большие неоправданные затраты
3. Изменение структуры сайта: если сайт будет переработан, локаторы элементов могут измениться, что повлияет на стабильность тестов.
4. Обновления платформы: Новые версии браузеров, операционных систем, могут повлиять на работу тестов.
5. Недоступность сервера: если сервер тестируемого сайта недоступен, то тесты не смогут быть выполнены.

## 4. Интервальная оценка с учётом рисков в часах

- Планирование автоматизации тестирования: 16–18 часов
- Написание авто-тестов: 72–96 часов
- Подготовка отчётных документов по итогам автоматизированного тестирования: 16–18  часов
- Подготовка отчётных документов по итогам автоматизации: 16–18 часов

## 5. План сдачи работ

- Готовность авто-тестов: через 16 календарных дней после утверждения плана тестирования;
- Подготовка отчетов по результатам прогона тестов: через 4 рабочих дня после прогона тестов;
- Подготовка отчета по итогам автоматизации: через 4 рабочих дня после отчетов по прогону тестов.