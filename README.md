# Домашнее задание к занятию «Базы данных»

### Инструкция по выполнению домашнего задания

1. Сделайте fork [репозитория c шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и ваши фамилию и имя;
   - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
   - для корректного добавления скриншотов воспользуйтесь инструкцией [«Как вставить скриншот в шаблон с решением»](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md);
   - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в [инструкции по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md).
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.

Желаем успехов в выполнении домашнего задания.

---
### Легенда

Заказчик передал вам [файл в формате Excel](https://github.com/netology-code/sdb-homeworks/blob/main/resources/hw-12-1.xlsx), в котором сформирован отчёт. 

На основе этого отчёта нужно выполнить следующие задания.

### Задание 1

Опишите не менее семи таблиц, из которых состоит база данных:

- какие данные хранятся в этих таблицах;
- какой тип данных у столбцов в этих таблицах, если данные хранятся в PostgreSQL.

Приведите решение к следующему виду:

Сотрудники (

- идентификатор, первичный ключ, serial,
- фамилия varchar(50),
- ...
- идентификатор структурного подразделения, внешний ключ, integer).


Сотрудники (
- идентификатор, первичный ключ
- ФИО, VARCHAR (255)
- оклад, DECIMAL/NUMERIC
- дата найма, DATE
- Идентификатор должности (идентификатор)
- идентификатор региона (идентификатор)
- идентификатор города (идентификатор)
- идентификатор филиала (идентификатор)
- идентификатор типа подразделения (идентификатор)
- идентификатор структурного подразделения (идентификатор)
- идентификатор проекта (идентификатор)
)

Должности у нас повторяются в разных офисах, поэтому привязываться тут не к чему:

Должности (
- идентификатор, первичный ключ
- должность, VARCHAR (100)
)

Регион (
- Идентификатор, первичный ключ)
- Регион (VARCHAR30
)

Город (
- Идентификатор, первичный ключ
- Идентификатор региона (идентификатор)
- Город (VARCHAR 30)
) 

Филиалы (
- идентификатор, первичный ключ
- Идентификатор города (идентификатор)
- Адрес филиала (VARCHAR 255)
)

Тип подразделения (
- идентификатор, первичный ключ
- Идентификатор филиала (идентификатор)
- Тип подразделения (VARCHAR 30)
)

Структурное подразделение (
- идентификатор, первичный ключ
- Идентификатор типа подразделения (идентификатор)
- Структурное подразделение (VARCHAR 100)
)

Кажется что сотрудники работающие над одним проектом вполне могут работать в разных регионах, поэтому привязки тут будут лишними:

Проект (
- идентификатор, первичный ключ
- проект (VARCHAR 50)
)


## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.


### Задание 2*

Перечислите, какие, на ваш взгляд, в этой денормализованной таблице встречаются функциональные зависимости и какие правила вывода нужно применить, чтобы нормализовать данные.
1. Разбить ФИО на 3 столбца
2. В столбце "оклад" убрать FLOAT (тк все равно не используется)
3. В столбце "должность" добавить столбец с грейдом и сделать его возможно пустым (NULL, ведущий, страший)
