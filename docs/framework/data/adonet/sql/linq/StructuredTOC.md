# [LINQ to SQL](index.md)
## [Начало работы](getting-started.md)
### [Возможности LINQ to SQL](what-you-can-do-with-linq-to-sql.md)
### [Типичные действия по использованию LINQ to SQL](typical-steps-for-using-linq-to-sql.md)
### [Загрузка образцов баз данных](downloading-sample-databases.md)
### [Обучение с помощью пошаговых руководств](learning-by-walkthroughs.md)
#### [Пошаговое руководство. Простая модель объектов и простой запрос (Visual Basic) (LINQ to SQL).](walkthrough-simple-object-model-and-query-visual-basic.md)
#### [Пошаговое руководство. Выполнение запросов со связями (Visual Basic)](walkthrough-querying-across-relationships-visual-basic.md)
#### [Пошаговое руководство. Обработка данных (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)
#### [Пошаговое руководство. Применение только хранимых процедур (Visual Basic)](walkthrough-using-only-stored-procedures-visual-basic.md)
#### [Пошаговое руководство. Простая модель объектов и простой запрос (C#)](walkthrough-simple-object-model-and-query-csharp.md)
#### [Пошаговое руководство. Запросы по связям (C#)](walkthrough-querying-across-relationships-csharp.md)
#### [Пошаговое руководство. Обработка данных (C#)](walkthrough-manipulating-data-csharp.md)
#### [Пошаговое руководство. Использование только хранимых процедур (C#)](walkthrough-using-only-stored-procedures-csharp.md)
## [Руководство по программированию](programming-guide.md)
### [Создание модели объектов](creating-the-object-model.md)
#### [Как создать модель объектов на языке Visual Basic или C#](how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
#### [Как сформировать модель объектов в виде внешнего файла](how-to-generate-the-object-model-as-an-external-file.md)
#### [Как создать настраиваемый код путем изменения DBML-файла](how-to-generate-customized-code-by-modifying-a-dbml-file.md)
#### [Как проверить DBML-файлы и внешние файлы сопоставлений](how-to-validate-dbml-and-external-mapping-files.md)
#### [Как обеспечить сериализацию сущностей](how-to-make-entities-serializable.md)
#### [Как настроить классы сущностей с помощью редактора кода](how-to-customize-entity-classes-by-using-the-code-editor.md)
##### [Как указывать имена баз данных](how-to-specify-database-names.md)
##### [Как представить таблицы в виде классов](how-to-represent-tables-as-classes.md)
##### [Как представить столбцы в виде членов класса](how-to-represent-columns-as-class-members.md)
##### [Как представить первичные ключи](how-to-represent-primary-keys.md)
##### [Как сопоставить связи базы данных](how-to-map-database-relationships.md)
##### [Как представить столбцы как сформированные базой данных](how-to-represent-columns-as-database-generated.md)
##### [Как представить столбцы как столбцы отметки времени или версии](how-to-represent-columns-as-timestamp-or-version-columns.md)
##### [Как задавать типы данных базы данных](how-to-specify-database-data-types.md)
##### [Как представить вычисляемые столбцы](how-to-represent-computed-columns.md)
##### [Как указать поля закрытого хранения](how-to-specify-private-storage-fields.md)
##### [Как представлять столбцы, допускающие значения NULL](how-to-represent-columns-as-allowing-null-values.md)
##### [Как сопоставить иерархии наследования](how-to-map-inheritance-hierarchies.md)
##### [Как задать проверку наличия конфликтов параллелизма](how-to-specify-concurrency-conflict-checking.md)
### [Взаимодействие с базой данных](communicating-with-the-database.md)
#### [Как соединиться с базой данных](how-to-connect-to-a-database.md)
#### [Как напрямую выполнять команды SQL](how-to-directly-execute-sql-commands.md)
#### [Как повторно использовать соединение между командой ADO.NET и DataContext](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
### [Выполнение запросов к базе данных](querying-the-database.md)
#### [Как выполнять запросы о сведениях](how-to-query-for-information.md)
#### [Как получать данные в режиме только для чтения](how-to-retrieve-information-as-read-only.md)
#### [Как управлять объемом получаемых взаимосвязанных данных](how-to-control-how-much-related-data-is-retrieved.md)
#### [Как отфильтровать взаимосвязанные данные](how-to-filter-related-data.md)
#### [Как отключить отложенную загрузку](how-to-turn-off-deferred-loading.md)
#### [Как напрямую выполнять SQL-запросы](how-to-directly-execute-sql-queries.md)
#### [Как сохранять и повторно использовать запросы](how-to-store-and-reuse-queries.md)
#### [Как обрабатывать составные ключи в запросах](how-to-handle-composite-keys-in-queries.md)
#### [Как извлечь несколько объектов одновременно](how-to-retrieve-many-objects-at-once.md)
#### [Как отфильтровать данные на уровне DataContext](how-to-filter-at-the-datacontext-level.md)
#### [Примеры запросов](query-examples.md)
##### [Агрегатные запросы](aggregate-queries.md)
###### [Возврат среднего значения из числовой последовательности ](return-the-average-value-from-a-numeric-sequence.md)
###### [Подсчет числа элементов в последовательности](count-the-number-of-elements-in-a-sequence.md)
###### [Нахождение наибольшего значения в числовой последовательности](find-the-maximum-value-in-a-numeric-sequence.md)
###### [Нахождение наименьшего значения в числовой последовательности](find-the-minimum-value-in-a-numeric-sequence.md)
###### [Вычисление суммы значений числовой последовательности](compute-the-sum-of-values-in-a-numeric-sequence.md)
##### [Возвращение первого элемента последовательности](return-the-first-element-in-a-sequence.md)
##### [Возвращение или пропуск элементов последовательности](return-or-skip-elements-in-a-sequence.md)
##### [Сортировка элементов в последовательности](sort-elements-in-a-sequence.md)
##### [Группирование элементов в последовательности](group-elements-in-a-sequence.md)
##### [Удаление повторяющихся элементов из последовательности](eliminate-duplicate-elements-from-a-sequence.md)
##### [Как определить, выполняется условие для одного или для всех элементов последовательности](determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)
##### [Объединение двух последовательностей](concatenate-two-sequences.md)
##### [Возвращение различий в наборах двух последовательностей](return-the-set-difference-between-two-sequences.md)
##### [Возвращение набора пересечения двух последовательностей](return-the-set-intersection-of-two-sequences.md)
##### [Возвращение объединения наборов двух последовательностей](return-the-set-union-of-two-sequences.md)
##### [Преобразование последовательности в массив](convert-a-sequence-to-an-array.md)
##### [Преобразование последовательности в список общего вида](convert-a-sequence-to-a-generic-list.md)
##### [Преобразование последовательности в общий интерфейс IEnumerable](convert-a-type-to-a-generic-ienumerable.md)
##### [Формирование соединений и запросов с перекрестными произведениями](formulate-joins-and-cross-product-queries.md)
##### [Формирование проекций](formulate-projections.md)
### [Внесение и отправка изменений данных ](making-and-submitting-data-changes.md)
#### [Как вставлять строки в базу данных](how-to-insert-rows-into-the-database.md)
#### [Как обновлять строки в базе данных](how-to-update-rows-in-the-database.md)
#### [Как удалять строки из базы данных](how-to-delete-rows-from-the-database.md)
#### [Как отправить изменения в базу данных](how-to-submit-changes-to-the-database.md)
#### [Как объединить в пакеты отправку данных с помощью транзакций](how-to-bracket-data-submissions-by-using-transactions.md)
#### [Как динамически создать базу данных](how-to-dynamically-create-a-database.md)
#### [Как управлять конфликтами изменений](how-to-manage-change-conflicts.md)
##### [Как обнаруживать и разрешать конфликты отправки](how-to-detect-and-resolve-conflicting-submissions.md)
##### [Как указать, когда возникают исключения параллелизма](how-to-specify-when-concurrency-exceptions-are-thrown.md)
##### [Как указать, для каких элементов тестируется возникновение конфликтов параллелизма](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
##### [Как получить сведения о конфликтах сущностей](how-to-retrieve-entity-conflict-information.md)
##### [Как получить сведения о конфликтах элементов](how-to-retrieve-member-conflict-information.md)
##### [Как разрешать конфликты параллелизма путем сохранения значений базы данных](how-to-resolve-conflicts-by-retaining-database-values.md)
##### [Как разрешать конфликты параллелизма методом перезаписи значений базы данных](how-to-resolve-conflicts-by-overwriting-database-values.md)
##### [Как разрешать конфликты путем слияния значений базы данных](how-to-resolve-conflicts-by-merging-with-database-values.md)
### [Поддержка отладки](debugging-support.md)
#### [Как отобразить сформированный код SQL](how-to-display-generated-sql.md)
#### [Как отобразить набор изменений](how-to-display-a-changeset.md)
#### [Как отображать команды LINQ to SQL](how-to-display-linq-to-sql-commands.md)
#### [Устранение неполадок](troubleshooting.md)
### [Дополнительные сведения](background-information.md)
#### [ADO.NET и LINQ to SQL](ado-net-and-linq-to-sql.md)
#### [Анализ исходного кода LINQ to SQL](analyzing-linq-to-sql-source-code.md)
#### [Настройка операций вставки, обновления и удаления](customizing-insert-update-and-delete-operations.md)
##### [Настройка операций. Общие сведения](customizing-operations-overview.md)
##### [Операции вставки, обновления и удаления](insert-update-and-delete-operations.md)
##### [Обязанности разработчика при переопределении поведения по умолчанию](responsibilities-of-the-developer-in-overriding-default-behavior.md)
##### [Добавление бизнес-логики с помощью разделяемых методов](adding-business-logic-by-using-partial-methods.md)
#### [Привязка данных](data-binding.md)
#### [Поддержка наследования](inheritance-support.md)
#### [Локальные вызовы методов](local-method-calls.md)
#### [Многоуровневые и удаленные приложения с LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md)
##### [N-уровневое использование LINQ to SQL с ASP.NET](linq-to-sql-n-tier-with-aspnet.md)
##### [Технология LINQ to SQL в многоуровневых приложениях с веб-службами](linq-to-sql-n-tier-with-web-services.md)
##### [LINQ to SQL и тесно связанные клиент-серверные приложения](linq-to-sql-with-tightly-coupled-client-server-applications.md)
##### [Реализация многоуровневой бизнес-логики](implementing-business-logic-linq-to-sql.md)
##### [Получение данных и операции CUD в многоуровневых приложениях (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md)
#### [Идентификация объекта](object-identity.md)
#### [Модель объектов LINQ to SQL](the-linq-to-sql-object-model.md)
#### [Состояния объектов и отслеживание изменений](object-states-and-change-tracking.md)
#### [Оптимистичный параллелизм. Общие сведения](optimistic-concurrency-overview.md)
#### [Основные понятия о запросах](query-concepts.md)
##### [Запросы LINQ to SQL](linq-to-sql-queries.md)
##### [Выполнение запросов в связях](querying-across-relationships.md)
##### [Сравнение удаленного и локального выполнения](remote-vs-local-execution.md)
##### [Сравнение отложенной и немедленной загрузки](deferred-versus-immediate-loading.md)
#### [Получение объектов из кэша идентификации](retrieving-objects-from-the-identity-cache.md)
#### [Безопасность в LINQ to SQL](security-in-linq-to-sql.md)
#### [Сериализация](serialization.md)
#### [Хранимые процедуры](stored-procedures.md)
##### [Как использовать хранимые процедуры для возвращения](how-to-return-rowsets.md)
##### [Как использовать хранимые процедуры, принимающие параметры](how-to-use-stored-procedures-that-take-parameters.md)
##### [Как использовать хранимые процедуры, сопоставленные с несколькими результирующими формами](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)
##### [Как использовать хранимые процедуры, сопоставленные с последовательными результирующими формами](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)
##### [Настройка операций с помощью хранимых процедур](customizing-operations-by-using-stored-procedures.md)
##### [Настройка операций с использованием только хранимых процедур](customizing-operations-by-using-stored-procedures-exclusively.md)
#### [Поддержка транзакций](transaction-support.md)
#### [Несоответствия типов SQL-CLR](sql-clr-type-mismatches.md)
#### [Сопоставления пользовательских типов SQL-CLR ](sql-clr-custom-type-mappings.md)
#### [Определяемые пользователем функции](user-defined-functions.md)
##### [Как применять определяемые пользователем скалярные функции](how-to-use-scalar-valued-user-defined-functions.md)
##### [Как применять определяемые пользователем возвращающие табличное значение функции](how-to-use-table-valued-user-defined-functions.md)
##### [Как вызывать встроенные определяемые пользователем функции](how-to-call-user-defined-functions-inline.md)
## [Ссылки](reference.md)
### [Типы данных и функции](data-types-and-functions.md)
#### [Сопоставление типов SQL и CLR](sql-clr-type-mapping.md)
#### [Основные типы данных](basic-data-types.md)
#### [Логические типы данных](boolean-data-types.md)
#### [Семантика NULL](null-semantics.md)
#### [Числовые операторы и операторы сравнения](numeric-and-comparison-operators.md)
#### [Операторы последовательности](sequence-operators.md)
#### [Методы System.Convert](system-convert-methods.md)
#### [Методы System.DateTime](system-datetime-methods.md)
#### [Методы System.Math](system-math-methods.md)
#### [Методы System.Object ](system-object-methods.md)
#### [Методы System.String](system-string-methods.md)
#### [Методы System.TimeSpan](system-timespan-methods.md)
#### [Неподдерживаемые функции](unsupported-functionality.md)
#### [Методы System.DateTimeOffset](system-datetimeoffset-methods.md)
### [Сопоставление на основе атрибутов](attribute-based-mapping.md)
### [Создание кода в LINQ to SQL](code-generation-in-linq-to-sql.md)
### [Внешние сопоставления](external-mapping.md)
### [Часто задаваемые вопросы](frequently-asked-questions.md)
### [SQL Server Compact и LINQ to SQL](sql-server-compact-and-linq-to-sql.md)
### [Преобразование стандартных операторов запросов](standard-query-operator-translation.md)
## [Образцы](samples.md)