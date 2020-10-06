## О компании
[GroupPrice.ru](https://groupprice.ru "GroupPrice.ru") – маркетплейс товаров, складская логистика реализована по кросс-докинг модели (минимальные складские запасы), загрузка товаров и синхронизация складских остатков происходит через [YML формат](http://https://yandex.ru/support/partnermarket/export/yml.html "YML формат").

Компании 9 лет. ~ 1.5 млн. посетителей в месяц, https://www.similarweb.com/website/groupprice.ru

## Технологический стек
- RoR 6
- Ruby 2.7
- Dry-rb
- Slim, SCSS
- Webpacker, Stimulus, ES6
- Rspec
- PostgreSQL
- rubocop, eslint, slim-lint, stylelint, prettier

## Ключевая информация по организации работы

- В команде 4 разработчика
- Официальное трудоустройство по ТК РФ (зарплата белая)
- Гибкий график работы, но с 12 до 18 по мск нужно быть онлайн
- Офис в Твери. Но все кто в ИТ-отделе работают удаленно
- Для управления проектами используем свою тикет систему, которая тесно интегрируется с бизнес процессами, и отражает коммуникационные связи организации, интеграция с Gitlab
- Переписка и чаты в Telegram
- Есть годовой бюджет на покупку книг, курсов, билетов на конференции на весь ИТ-отдел. Неиспользованные средства в конце года сгорают
- Собираемся на RubyRussia, вместе работаем одну неделю

## Работа над задачей
Задача создается во внутренней тикет системе, из которой можно сразу создать Merge Request в Gitlab, случайным образом для задачи выбираются 2 проверяющих (1 Сеньёр и 1 Мидл/Junior), проверяющие автоматически добавляются к MR и получают уведомления о коммитах в Gitlab, в нем и проходит ревью кода.

## OpenSource
### Собственные репозитории (в том числе поддерживаемые форки)
- https://github.com/corp-gp/rails_string_enum
- https://github.com/corp-gp/activerecord-clean-db-structure
- https://github.com/corp-gp/lintbot
### MR
https://github.com/corp-gp/delayed_job

https://github.com/corp-gp/mini_sql
 - [@xronos-i-am - Fix symbol param encoder](https://github.com/discourse/mini_sql/pull/9)
 - [@ermolaev - add query_array](https://github.com/discourse/mini_sql/pull/10)
 - [@ermolaev - add query_decorator](https://github.com/discourse/mini_sql/pull/13)
 - [@ermolaev - empty array encoding compatibility with Sequel and ActiveRecord](https://github.com/discourse/mini_sql/pull/14)
 - [@ermolaev - improve test_query_decorator](https://github.com/discourse/mini_sql/pull/16)
 - [@ermolaev - remove double checked empty params](https://github.com/discourse/mini_sql/pull/18)

https://github.com/corp-gp/pronto-reek
 - [@ermolaev - markdown message with link](https://github.com/prontolabs/pronto-reek/pull/25)

https://github.com/corp-gp/pronto-brakeman
 - [@ermolaev - markdown message with link](https://github.com/prontolabs/pronto-brakeman/pull/22)

https://github.com/zaru/webpush
- [@xronos-i-am - Fix authorization header](https://github.com/zaru/webpush/pull/72)

## Работа с базой данных
Для коммуницирования с Postgresql используются:
### ActiveRecord:
- написания бизнес логики (в сервис объектах), удобно - построчное обновление с логированием всех изменений сущности, связи между объектами
- простые операции типа find, destroy, update_all

### [mini_sql](https://github.com/corp-gp/mini_sql)
- быстрая компиляция запроса в sql (builder от 3х быстрее ActiveRecord)
- быстрая сериализация данных из бд, экономия памяти, быстрее как создание объектов из строки, так и вызов методов у инстанса (быстрее ActiveRecord от 7х, если используются временные столбцы `timestamp`, преимущество 10x раз)
- ручной контроль prepared statements
- переиспользуется соединение с бд от ActiveRecord


## Frontend
Вся логика отображения храниться на сервере, пишется на slim шаблонизаторе, за счет использования `mini_sql` удается минимизировать время работы ruby кода, 90% всех действий это выборка объектов из бд и вызовов их методов

Логика на JS минимальна, используется минималестичный фреймворк https://stimulusjs.org, js пишеться на es6, без jquery, и спользуются нативные методы и полифилы для них
