---
title: "Прямая связь клиента микрослужбу и шаблон шлюза API"
description: "Архитектура Микрослужбами .NET для приложений .NET в контейнерах | Прямая связь клиента микрослужбу и шаблон шлюза API"
keywords: "Docker, Микрослужбами, ASP.NET, контейнера, API шлюза"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c8227ec47888c7cf361f34c4c85a09c0666f886e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2017
---
# <a name="direct-client-to-microservice-communication-versus-the-api-gateway-pattern"></a>Прямая связь клиента микрослужбу и шаблон шлюза API

В архитектуре микрослужбами каждого микрослужбу предоставляет набор (обычно) fine‑grained конечных точек. Этот факт может повлиять на взаимодействие client‑to‑microservice, как описано в этом разделе.

## <a name="direct-client-to-microservice-communication"></a>Прямая связь клиента микрослужбу

Возможные подходом является использование архитектуры прямой обмен данными клиента микрослужбы. При таком подходе клиентские приложения могут выполнять запросы непосредственно к некоторым микрослужбами, как показано на рисунке 4-12.

![](./media/image12.png)

**Рис. 4-12**. С помощью прямой обмен данными клиента микрослужбу архитектуры

При использовании этого подхода. Каждый микрослужбу имеет общедоступную конечную точку, иногда с разных портов TCP для каждого микрослужбы. Пример URL-адреса для конкретной службы может быть следующий URL-адрес в Azure.

<http://eshoponcontainers.westus.cloudapp.Azure.com:88 />

В рабочей среде, в зависимости от кластера, что URL-адреса будут сопоставлены с подсистемой балансировки нагрузки в кластере, который в свою очередь распределяет запросы по микрослужбами. В производственной среде, можно создать контроллер доставки приложений (ADC) как [шлюза приложения Azure](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) между вашей микрослужбами и Интернетом. Это действует как прозрачный уровня, которые не только выполняет балансировку нагрузки, но также обеспечивает защиту служб, предлагая завершение запросов SSL. Это повышает нагрузку на узлах за счет разгрузки SSL процессор завершения других маршрутизации обязанностей и для шлюза приложения Azure. В любом случае подсистемы балансировки нагрузки и Соединитель Active Directory являются прозрачными из приложения логической архитектуры точки зрения.

Архитектура прямого взаимодействия клиента микрослужбу может быть достаточно для небольших микрослужбу-приложения, особенно в том случае, если клиентское приложение находится в серверном веб-приложения, как приложение ASP.NET MVC. Однако при построении больших и сложных микрослужбу приложений на основе (например, при обработке десятки микрослужбу типов), и особенно в том случае, если клиентские приложения являются удаленного мобильных приложений или SPA веб-приложений, этот подход сталкивается несколько проблем.

При разработке большого приложения, основанного на микрослужбами, ответьте на следующие вопросы:

-   *Как клиентские приложения свести к минимуму число запросов к серверной части и уменьшить частый обмен данными на нескольких микрослужбами?*

Взаимодействие с несколькими микрослужбами для создания одного пользовательского интерфейса экрана увеличивает количество обращений через Интернет. Это увеличивает задержку и сложности на стороне пользовательского интерфейса. В идеальном случае ответы эффективно рассчитано на стороне сервера — это сокращает задержки, так как несколько фрагментов данных вернитесь в параллельном режиме и пользовательский Интерфейс можно показать данные, как только будет готов к работе.

-   *Порядок обработки перекрестными проблемы, такие как авторизация, преобразования данных и диспетчеризации динамический запрос?*

Реализация перекрестными проблемы безопасности и как безопасности и авторизации на каждом микрослужбу может потребовать значительных разработки приложения. Возможный подход является эти службы в узел Docker или внутри кластера, чтобы предотвратить прямой доступ к ним извне и реализовать их беспокойство перекрестными в централизованном расположении, например шлюз API.

-   *Как клиентские приложения могут взаимодействовать со службами, которые используют протоколы Интернета понятное?*

Протоколы, используемые на стороне сервера (например, AMQP или двоичные протоколы) обычно не поддерживается в клиентских приложениях. Таким образом запросы требуется выполнить через протоколы, например HTTP или HTTPS, а затем преобразуется в другие протоколы. Объект *в середине* подход может помочь в этой ситуации.

-   *Как можно формировать оболочки, особенно сделанные для мобильных приложений*

API-Интерфейс несколько микрослужбами не следует также спроектировать для удовлетворения потребностей различных клиентских приложений. Например потребностей мобильного приложения может отличаться от потребности веб-приложения. Для мобильных приложений может потребоваться еще больше оптимизировать, чтобы данные ответов может быть более эффективным. Это может сделать, статистическая обработка данных из нескольких микрослужбами и возвращение одного набора данных и иногда решать любые данные в ответ, который не требуется, мобильное приложение. И, конечно, вы сжатие этих данных. Опять же оболочка или API-Интерфейс между микрослужбами и мобильные приложения может оказаться удобным для этого сценария.

## <a name="using-an-api-gateway"></a>С помощью API-интерфейса шлюза

При проектировании и создание больших или сложных микрослужбу-приложениям с несколько клиентских приложений, может быть хорошим подходом, которые следует учитывать [шлюза API](http://microservices.io/patterns/apigateway.html). Это служба, предоставляющая единую точку входа для определенных групп микрослужбами. Это похоже на [шаблон Facade](https://en.wikipedia.org/wiki/Facade_pattern) от object‑oriented проектирования, но в этом случае он является частью распределенных систем. Шаблон шлюза API также иногда называют «внутренняя для внешнего интерфейса» [(BFF)](http://samnewman.io/patterns/architectural/bff/) так, как построить при думать о потребностях клиентского приложения.

На рисунке 4-13 показано, как пользовательские API шлюз может быть загружено в архитектуру на основе микрослужбу.
Важно обратить внимание, что в эту схему, используемого одну пользовательскую службу шлюза API с несколькими и различных клиентских приложений. На многих различных требований из клиентских приложений, факт может быть важные риска, так как службы шлюза API будет растет и развития основе. Со временем будет перегруженными из-за этих различных потребностей и эффективно может быть довольно аналогично монолитные приложения или объединенный службы. Именно поэтому сильно рекомендуется разбить шлюза API в несколько служб или несколько небольших API шлюзов, по одной на каждый тип форм фактор для экземпляра.

![](./media/image13.png)

**Рис. 4-13**. С помощью API-интерфейса шлюза реализован как пользовательскую службу веб-API

В этом примере API шлюза будет реализован в виде пользовательских веб-API службы, запущенной как контейнер.

Как уже упоминалось, необходимо реализовать несколько шлюзов API, чтобы у вас есть другой оболочкой для удовлетворения потребностей каждого клиентского приложения. Каждый шлюз API может предоставить другой API, предназначенная для каждого клиентского приложения, возможно даже, на основе форм-фактор клиента путем реализации какие расположенных под вызывает несколько внутренних микрослужбами кода отдельный адаптер.

Поскольку пользовательские API шлюза обычно агрегации данных, необходимо Будьте внимательны с ним. Обычно не рекомендуется иметь один шлюз API статистическая обработка всех внутренних микрослужбами приложения. В этом случае он выступает в качестве монолитные инвентаризации программного обеспечения или orchestrator и приводит к нарушению автономность микрослужбу, связывая микрослужбами. Таким образом шлюзы API должны быть выделены на основе границы и не act как инвентаризации программного обеспечения для всего приложения.

Иногда детальные шлюза API можно также микрослужбу сам по себе и даже настроить домен или название организации и связанные данные. Наличие границы шлюза API для обрабатываемых бизнеса или домена поможет получить лучше.

Можно особенно полезна для более сложных составных приложений пользовательского интерфейса на основании микрослужбами, гранулярности на уровне API шлюза, поскольку концепция детально шлюза API как композиции службу пользовательского интерфейса. Мы обсудим это позже в [создания составного пользовательского интерфейса, основанного на микрослужбами](#creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices).

Таким образом, для многих приложений среднего и большого размера с использованием пользовательского API шлюза обычно является хорошим решением, но как один монолитные инвентаризации программного обеспечения или уникальный центра пользовательские API шлюза.

Другой подход заключается в использовании продукта как [управления API Azure](https://azure.microsoft.com/services/api-management/) как показано на рисунке 4-14. Такой подход не только позволяет решить потребности API шлюза, но предоставляет функции, например сбор аналитики собственные интерфейсы API. При использовании решения управления API шлюз API является только компонентом в рамках этого полному решению управления API.

![](./media/image14.png)

**Рис. 4-14**. С помощью управления Azure API API шлюза

В этом случае при использование продукта, например управление API Azure, тот факт, что может потребоваться один шлюз API не так рискованно, поскольку такого рода шлюзы API «узкий», то есть не реализовать пользовательский код C#, который могут включать в сторону монолитные компонент. 

Этот тип продукта более действует как обратного прокси-сервера для передачи данных входящих событий, где можно также фильтровать API из внутренней микрослужбами и применять проверку подлинности для опубликованных интерфейсов API в этом одного уровня.

Аналитики, доступных из справочной системы управления API получить представление о том, как используются собственные интерфейсы API и как они выполняются. Это делается, позволяя просматривать рядом с отчетами в режиме реального времени и выявления трендов, которые может повлиять на ваш бизнес. Кроме того может иметь журналы действий запроса и ответа для дальнейшего анализа сети и вне сети.

Службы управления API Azure можно защитить собственные интерфейсы API, с помощью ключа, маркер и фильтрация IP-адресов. Эти возможности позволяют обеспечить гибкую и тонкого квоты и пределы скорости, изменять форму и поведение собственные интерфейсы API, с помощью политик и позволяют повысить производительность благодаря кэширование ответов.

В этом руководстве и ссылка пример приложения (eShopOnContainers) архитектура проще и собственной разработки контейнерного архитектуры ограничение чтобы сосредоточить внимание на обычные контейнеры без использования продуктов PaaS как API управления Azure. Однако для больших микрослужбу-приложений, развернутых в Microsoft Azure, мы рекомендуем просмотреть и адаптировать API управления Azure как основа для шлюзов API.

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Недостатки шаблона API шлюза

-   Наиболее важные недостаток заключается в том, что при реализации API шлюза с внутренней микрослужбами взаимозависимость этого уровня. Объединение следующим образом, может возникнуть серьезные проблемы для вашего приложения. Vaster Клеменса архитектор в группе Azure Service Bus, ссылается на этой потенциальной сложности, как «новый ESB» в его «[обмена сообщениями и Микрослужбами](https://www.youtube.com/watch?v=rXi5CLjIQ9k)» в GOTO 2016 сеанс.

-   С помощью микрослужбами API шлюза создает дополнительные возможных узких мест.

-   Шлюз API могут вызвать увеличения времени ответа из-за дополнительных сетевых вызовов. Тем не менее этот дополнительный вызов обычно имеет меньше влияния, чем ошибки возникают интерфейс, который отправляет которых слишком много прямого вызова внутренней микрослужбами.

-   Если не масштабировать должным образом, шлюз API может стать узким местом.

-   Шлюз API требует затраты на разработку и обслуживание будущих, если он включает пользовательской логики и статистической обработки данных. Разработчикам необходимо обновить шлюз API для предоставления конечных точек каждой микрослужбы. Кроме того изменения реализации в внутренней микрослужбами может привести к изменения кода на уровне API шлюза. Тем не менее если шлюз API просто применяет безопасности, ведение журнала и управление версиями (как при использовании API управления Azure), эти затраты на разработку могут не действовать.

-   Если шлюз API, разработанном одну группу, может быть узким местом разработки. Это еще одна причина, почему лучше иметь несколько Контролируемая влечет API шлюзов, которые отвечать на разные клиентские запросы. Может также внутренне разделять API шлюза на несколько областей или уровни, которые принадлежат другой команды, работающие на внутренние микрослужбами.

## <a name="additional-resources"></a>Дополнительные ресурсы

-   **Чарльз Ричардсон. Шаблон: API шлюза и внутреннем сервере для переднего плана**
    [*http://microservices.io/patterns/apigateway.html*](http://microservices.io/patterns/apigateway.html)

-   **Управление Azure API**
    [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

-   **UDI Dahan. Сервисноориентированные композиции**\
    [*http://udidahan.com/2014/07/30/Service-Oriented-Composition-WITH-Video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

-   **Clemens Vasters. Обмен сообщениями и Микрослужбами на GOTO 2016** (видео) [ *https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)


>[!div class="step-by-step"]
[Предыдущие] (определить микрослужбу домена модели boundaries.md) [Далее] (связи в микрослужбу architecture.md)
