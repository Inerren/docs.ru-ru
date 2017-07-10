---
title: "Транспорт: TCP-взаимодействие WSE 3.0 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5f7c3708-acad-4eb3-acb9-d232c77d1486
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# Транспорт: TCP-взаимодействие WSE 3.0
В примере транспорта взаимодействия TCP WSE 3.0 демонстрируется реализация дуплексного сеанса TCP в виде пользовательского транспорта [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].Также демонстрируется использование расширяемости уровня канала для создания интерфейса по сети с существующими развернутыми системами.Следующие шаги показывают, как построить этот пользовательский транспорт [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
1.  Начиная с сокета TCP, создайте клиентские и серверные реализации интерфейса <xref:System.ServiceModel.Channels.IDuplexSessionChannel>, использующие кадрирование DIME для разграничения границ сообщений.  
  
2.  Создайте фабрику каналов, которая подключается к службе TCP WSE и передает кадрированные сообщения через клиентские интерфейсы <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.  
  
3.  Создайте прослушиватель канала для приема входящих подключений TCP и создания соответствующих каналов.  
  
4.  Убедитесь, что все исключения, связанные с сетью, нормализованы в соответствующий класс, унаследованный от <xref:System.ServiceModel.CommunicationException>.  
  
5.  Добавьте элемент привязки, добавляющий пользовательский транспорт в стек каналов.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Добавление элемента привязки](#AddingABindingElement).  
  
## Создание IDuplexSessionChannel  
 Первый этап создания транспорта взаимодействия TCP WSE 3.0 — это реализация интерфейса <xref:System.ServiceModel.Channels.IDuplexSessionChannel> на основе класса <xref:System.Net.Sockets.Socket>.`WseTcpDuplexSessionChannel` является производным от <xref:System.ServiceModel.Channels.ChannelBase>.Логика передачи сообщения состоит из двух основных частей: \(1\) кодирование сообщения в байты и \(2\) кадрирование этих байтов и передача их по сети.  
  
 `ArraySegment<byte> encodedBytes = EncodeMessage(message);`  
  
 `WriteData(encodedBytes);`  
  
 Кроме того, устанавливается блокировка, чтобы вызовы Send\(\) сохраняли гарантию порядка IDuplexSessionChannel и чтобы вызовы соответствующего сокета были правильно синхронизированы.  
  
 `WseTcpDuplexSessionChannel` использует <xref:System.ServiceModel.Channels.MessageEncoder> для преобразования <xref:System.ServiceModel.Channels.Message> в массив byte\[\] и из него.Так как это транспорт, канал `WseTcpDuplexSessionChannel` также отвечает за использование удаленного адреса, с которым был настроен канал.`EncodeMessage` инкапсулирует логику для этого преобразования.  
  
 `this.RemoteAddress.ApplyTo(message);`  
  
 `return encoder.WriteMessage(message, maxBufferSize, bufferManager);`  
  
 После того как сообщение <xref:System.ServiceModel.Channels.Message> закодировано в байты, оно должно быть передано по сети.Для этого требуется система определения границ сообщения.В качестве протокола кадрирования WSE 3.0 использует версию [DIME](http://go.microsoft.com/fwlink/?LinkId=94999).`WriteData` инкапсулирует логику кадрирования для заключения массива byte \[\] в набор записей DIME.  
  
 Логика приема сообщений очень похожа.Основная сложность заключается в учете ситуаций, когда операция чтения сокета может вернуть меньше байтов, чем было запрошено.Чтобы принять сообщение, `WseTcpDuplexSessionChannel` считывает байты из сети, декодирует кадрирование DIME, затем использует <xref:System.ServiceModel.Channels.MessageEncoder> для преобразования массива byte\[\] в сообщение <xref:System.ServiceModel.Channels.Message>.  
  
 Базовый класс `WseTcpDuplexSessionChannel` предполагает, что он получает подключенный сокет.Базовый класс обрабатывает завершение работы сокета.Существуют три места, взаимодействующих с закрытием сокета:  
  
-   OnAbort — закрыть сокет некорректно \(жесткое закрытие\).  
  
-   On\[Begin\]Close — закрыть сокет корректно \(мягкое закрытие\).  
  
-   session.CloseOutputSession \-\- завершить работу исходящего потока данных \(закрытие наполовину\).  
  
## Фабрика каналов  
 Следующий этап создания транспорта TCP — реализация <xref:System.ServiceModel.Channels.IChannelFactory> для каналов клиентов.  
  
-   `WseTcpChannelFactory` наследует от <xref:System.ServiceModel.Channels.ChannelFactoryBase>\<IDuplexSessionChannel\>.Это фабрика, которая переопределяет `OnCreateChannel` для создания каналов клиентов.  
  
 `protected override IDuplexSessionChannel OnCreateChannel(EndpointAddress remoteAddress, Uri via)`  
  
 `{`  
  
 `return new ClientWseTcpDuplexSessionChannel(encoderFactory, bufferManager, remoteAddress, via, this);`  
  
 `}`  
  
-   `ClientWseTcpDuplexSessionChannel` добавляет логику в базовый класс `WseTcpDuplexSessionChannel`для подключения к серверу TCP в момент времени `channel.Open` time.Сначала имя узла разрешается в IP\-адрес, как показано в следующем коде.  
  
 `hostEntry = Dns.GetHostEntry(Via.Host);`  
  
-   Затем имя узла подключается в цикле к первому доступному IP\-адресу, как показано в следующем коде.  
  
 `IPAddress address = hostEntry.AddressList[i];`  
  
 `socket = new Socket(address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `socket.Connect(new IPEndPoint(address, port));`  
  
-   Как часть контракта канала, все специфичные для домена расширения заключаются в оболочку, как `SocketException` в <xref:System.ServiceModel.CommunicationException>.  
  
## Прослушиватель канала  
 Следующий этап создания транспорта TCP — реализация <xref:System.ServiceModel.Channels.IChannelListener> для приема каналов сервера.  
  
-   `WseTcpChannelListener` наследует от <xref:System.ServiceModel.Channels.ChannelListenerBase>\<IDuplexSessionChannel\> и переопределяет методы On\[Begin\]Open и On\[Begin\]Close для управления временем существования его прослушивающих сокетов.В OnOpen создается сокет для прослушивания по IP\_ANY.Более сложные реализации могут создавать второй сокет для прослушивания также и по IPv6.Они могут также допускать задание IP\-адреса в имени узла.  
  
 `IPEndPoint localEndpoint = new IPEndPoint(IPAddress.Any, uri.Port);`  
  
 `this.listenSocket = new Socket(localEndpoint.AddressFamily, SocketType.Stream, ProtocolType.Tcp);`  
  
 `this.listenSocket.Bind(localEndpoint);`  
  
 `this.listenSocket.Listen(10);`  
  
 Когда принимается новый сокет, инициализируется новый канал сервера с этим сокетом.Все операции ввода и вывода уже реализованы в базовом классе, поэтому этот канал отвечает за инициализацию сокета.  
  
## Добавление элемента привязки  
 Теперь, когда фабрики и каналы построены, они должны быть предоставлены среде выполнения ServiceModel через привязку.Привязка — это коллекция элементов привязки, представляющая стек связи для адреса службы.Каждый элемент стека представлен элементом привязки.  
  
 В этом примере в качестве элемента привязки выступает элемент `WseTcpTransportBindingElement`, являющийся производным элемента <xref:System.ServiceModel.Channels.TransportBindingElement>.Он поддерживает <xref:System.ServiceModel.Channels.IDuplexSessionChannel> и переопределяет следующие методы создания фабрик, связанных с нашей привязкой.  
  
 `public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelFactory<TChannel>)(object)new WseTcpChannelFactory(this, context);`  
  
 `}`  
  
 `public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)`  
  
 `{`  
  
 `return (IChannelListener<TChannel>)(object)new WseTcpChannelListener(this, context);`  
  
 `}`  
  
 Он также содержит члены для клонирования элемента `BindingElement` и возврата схемы \(wse.tcp\).  
  
## Тестовая консоль WSE TCP  
 Тестовый код для использования этого образца транспорта находится в файле TestCode.cs.Ниже показано, как выполнить построение и запуск образца `TcpSyncStockService`.  
  
 Тестовый код создает пользовательскую привязку, которая использует MTOM для кодирования и `WseTcpTransport` для транспорта.Он также настраивает AddressingVersion для соответствия WSE 3.0, как показано в следующем примере кода.  
  
 `CustomBinding binding = new CustomBinding();`  
  
 `MtomMessageEncodingBindingElement mtomBindingElement = new MtomMessageEncodingBindingElement();`  
  
 `mtomBindingElement.MessageVersion = MessageVersion.Soap11WSAddressingAugust2004;`  
  
 `binding.Elements.Add(mtomBindingElement);`  
  
 `binding.Elements.Add(new WseTcpTransportBindingElement());`  
  
 Он состоит из двух тестов — один тест настраивает типизированного клиента с помощью кода, созданного из WSE 3.0 WSDL.Второй тест использует [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] в качестве как клиента, так и сервера, передавая сообщения непосредственно по интерфейсам API канала.  
  
 При выполнении этого образца ожидаются следующие выходные данные.  
  
 Клиент:  
  
```  
Calling soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Symbol: FABRIKAM  
        Name: Fabrikam, Inc.  
        Last Price: 120  
  
Symbol: CONTOSO  
        Name: Contoso Corp.  
        Last Price: 50.07  
Press enter.  
  
Received Action: http://SayHello  
Received Body: to you.  
Hello to you.  
Press enter.  
  
Received Action: http://NotHello  
Received Body: to me.  
Press enter.  
```  
  
 Сервер:  
  
```  
Listening for messages at soap://stockservice.contoso.com/wse/samples/2003/06/TcpSyncStockService  
  
Press any key to exit when done...  
  
Request received.  
Symbols:  
        FABRIKAM  
        CONTOSO  
```  
  
#### Настройка, построение и выполнение образца  
  
1.  Для выполнения этого примера необходимо, чтобы были установлены WSE 3.0 и пример WSE `TcpSyncStockService`.[WSE 3.0 можно загрузить с MSDN](http://go.microsoft.com/fwlink/?LinkId=95000).  
  
> [!NOTE]
>  Так как WSE 3.0 не поддерживается в [!INCLUDE[lserver](../../../../includes/lserver-md.md)], пример `TcpSyncStockService` невозможно установить или выполнить в этой операционной системе.  
  
1.  После установки примера `TcpSyncStockService` выполните следующие операции.  
  
    1.  Откройте `TcpSyncStockService` в Visual Studio \(Обратите внимание, что пример TcpSyncStockService устанавливается с WSE 3.0.Он не является частью кода данного примера.\).  
  
    2.  Установите проект StockService в качестве проекта для запуска.  
  
    3.  Откройте файл StockService.cs в проекте StockService и закомментируйте атрибут \[Policy\] класса `StockService`.Таким образом в примере отключается безопасность.Хотя [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] может взаимодействовать с безопасными конечными точками WSE 3.0, безопасность отключается, чтобы сфокусировать данный пример на пользовательском транспорте TCP.  
  
    4.  Нажмите клавишу F5, чтобы запустить `TcpSyncStockService`.Служба запускается в новом окне консоли.  
  
    5.  Откройте пример транспорта TCP в Visual Studio.  
  
    6.  Обновите переменную "hostname" в файле TestCode.cs, чтобы она соответствовала имени компьютера, на котором запущена служба `TcpSyncStockService`.  
  
    7.  Нажмите клавишу F5, чтобы запустить пример транспорта TCP.  
  
    8.  Тестовый клиент транспорта TCP запускается в новой консоли.Клиент запрашивает у службы цены акций и отображает результаты в своем окне консоли.  
  
## См. также