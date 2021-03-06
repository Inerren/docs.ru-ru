---
title: "Практическое руководство. Настройка трассировки сети"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- formatting [.NET Framework], network tracing
- network tracing, configuring
- level attribute
- app.config files, network tracing
- configuration files [.NET Framework], network tracing
- protocol-level trace output
- application configuration files, network tracing
- sockets, trace output
ms.assetid: 5ef9fe4b-8d3d-490e-9259-1d014b2181af
caps.latest.revision: "23"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 12f328d58ef568c78d1e2c8a8ff564839cba9f3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-network-tracing"></a>Практическое руководство. Настройка трассировки сети
Файл конфигурации приложения или компьютера содержит параметры, которые определяют формат и содержимое данных трассировки сети. Перед выполнением этой процедуры убедитесь, что трассировка включена. Сведения о том, как включить трассировку сети, см. в разделе [Включение трассировки сети](../../../docs/framework/network-programming/enabling-network-tracing.md).  
  
 Файл конфигурации компьютера (machine.config) хранится в папке %Windir%\Microsoft.NET\Framework в каталоге, в который установлена ОС Windows. В папках %Windir%\Microsoft.NET\Framework для каждой версии платформы .NET Framework, установленной на компьютере (например, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config или C:\Windows\ имеется отдельный файл machine.config Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).  
  
 Эти параметры могут также задаваться в файле конфигурации приложения, который имеет более высокий приоритет, чем в файл конфигурации компьютера.  
  
### <a name="to-configure-network-tracing"></a>Настройка трассировки сети  
  
-   Добавьте следующие строки в соответствующий файл конфигурации. Значения этих параметров описаны в приведенных ниже таблицах.  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="System.Net" tracemode="includehex" maxdatasize="1024">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Cache">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Http">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.Sockets">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
          <source name="System.Net.WebSockets">  
            <listeners>  
              <add name="System.Net"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="System.Net" value="Verbose"/>  
          <add name="System.Net.Cache" value="Verbose"/>  
          <add name="System.Net.Http" value="Verbose"/>  
          <add name="System.Net.Sockets" value="Verbose"/>  
          <add name="System.Net.WebSockets" value="Verbose"/>  
        </switches>  
        <sharedListeners>  
          <add name="System.Net"  
            type="System.Diagnostics.TextWriterTraceListener"  
            initializeData="network.log"  
          />  
        </sharedListeners>  
        <trace autoflush="true"/>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
 При добавлении имени в блок `<switches>` результаты трассировки будут содержать сведения из определенных методов, связанных с указанным именем. Результат описан в следующей таблице.  
  
|Имя|Источник результата|  
|----------|-----------------|  
|`System.Net.Sockets`|Некоторые открытые методы классов <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient> и <xref:System.Net.Dns>|  
|`System.Net`|Некоторые открытые методы классов <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest> и <xref:System.Net.FtpWebResponse>, а также отладочные данные SSL (недопустимые сертификаты, отсутствующие эмитенты и ошибки сертификатов клиентов).|  
|`System.Net.HttpListener`|Некоторые открытые методы классов <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest> и <xref:System.Net.HttpListenerResponse>.|  
|`System.Net.Cache`|Некоторые открытые и закрытые методы в `System.Net.Cache`.|  
|`System.Net.Http`|Некоторые открытые методы классов <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler> и <xref:System.Net.Http.WebRequestHandler>.|  
|`System.Net.WebSockets.WebSocket`|Некоторые открытые методы классов <xref:System.Net.WebSockets.ClientWebSocket> и <xref:System.Net.WebSockets.WebSocket>.|  
  
 Атрибуты, указанные в следующей таблице, задают выходные данные трассировки.  
  
|Имя атрибута|Значение атрибута|  
|--------------------|---------------------|  
|`Value`|Обязательный атрибут элемента <xref:System.String>. Задает уровень детализации результатов. Допустимые значения: `Critical`, `Error`, `Verbose`, `Warning` и `Information`.<br /><br /> Этот атрибут следует установить в элементе \<add name> элемента \<switches>, как показано в примере. Исключение возникает, если этот атрибут задан для элемента \<source>.|  
|`maxdatasize`|Необязательный атрибут элемента <xref:System.Int32>. Задает максимальное число байтов сетевых данных, включенных в трассировку каждой линии. Значение по умолчанию — 1024.<br /><br /> Этот атрибут следует задавать в элементе \<source>, как показано в примере. Исключение возникает, если этот атрибут задан для элемента в элементе \<switches>.|  
|`Tracemode`|Необязательный атрибут элемента <xref:System.String>. Задается `includehex`, чтобы трассировка протоколов отображалась в шестнадцатеричном или текстовом формате. Установите значение `protocolonly`, чтобы отображался только текст. Значение по умолчанию — `includehex`.<br /><br /> Этот атрибут следует задавать в элементе \<switches>, как показано в примере. Исключение возникает, если этот атрибут задан для элемента в элементе \<source>.|  
  
## <a name="see-also"></a>См. также  
 [Интерпретация сетевой трассировки](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [Трассировка сети в .NET Framework](../../../docs/framework/network-programming/network-tracing.md)  
 [Включение трассировки сети](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [Введение. Подготовка к инструментированию и трассировка](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
