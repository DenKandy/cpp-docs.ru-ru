---
title: "Клиенты автоматизации | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Клиенты автоматизации"
  - "клиенты"
  - "клиенты, автоматизация"
  - "библиотеки типов, Клиенты автоматизации"
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Клиенты автоматизации
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Автоматизация дает возможность приложения для управления объектами, реализованные в другом приложении или предоставление объектов и их можно управлять.  Клиент автоматизации, приложение может управлять, объектов, принадлежащих к другому приложению.  Приложение, которое предоставляет объекты вызывается сервером автоматизации.  Клиент обрабатывать объекты серверного приложения через свойства и функции этих объектов.  
  
### Типы клиентов автоматизации  
 2 Типа клиентов автоматизации.  
  
-   Клиенты, которые динамически во время выполнения \(\) получить информацию о свойствах и операциях сервера.  
  
-   Клиенты, которые обладают статическими \(предоставленными сведениями во время компиляции\), который определяет свойства и операций сервера.  
  
 Клиенты первого типа получают сведения о методах и свойствах сервера можно с помощью механизма `IDispatch` OLE системы.  Хотя он достаточный для динамических клиентов, `IDispatch` сложно для статических клиентов, где, управляемыми объекты должны быть известны во время компиляции.  Для статических ограниченных клиентов классы Microsoft Foundation предоставляет класс [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md).  
  
 Статические ограниченные клиенты используют прокси\-класс, статически связана с клиентским приложением.  Этот класс предоставляет типобезопасную инкапсуляцию C\+\+ свойств операций серверного приложения.  
  
 Класс `COleDispatchDriver` предоставляет основной поддержку на стороне клиента автоматизации.  С помощью диалогового окна `Add New Item` создается класс, производный от `COleDispatchDriver`.  
  
 Затем следует определить файл библиотеки типов, свойства и функции объекта серверного приложения.  Диалоговое окно " добавление элемента " считывает этот файл и создает `COleDispatchDriver`\- производный класс, с функции\-членами, приложение может вызывать, чтобы получить объекты серверного приложения в C\+\+ в типобезопасном способом.  Дополнительные функциональные возможности, наследованную от `COleDispatchDriver` упрощает процесс вызова правильный сервер автоматизации.  
  
### Обработка событий в клиенте автоматизации  
 Если требуется обрабатывать события в клиенте автоматизации, необходимо добавить интерфейс приемника.  MFC предоставляет поддержку мастера для добавления приемника интерфейсы для элементов управления ActiveX, но не для других серверов поддержку модели COM.  Дополнительные сведения о добавлении интерфейса приемника в клиенте MFC для интерфейсов источника описанных серверами COM см. в разделе HOWTO: Создайте интерфейс приемника в клиенте модели COM на основе MFC \(181845 КБ\) в [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;181845](http://support.microsoft.com/default.aspx?scid=kb;en-us;181845).  
  
## См. также  
 [Клиенты автоматизации. Использование библиотек типов](../Topic/Automation%20Clients:%20Using%20Type%20Libraries.md)   
 [автоматизация](../mfc/automation.md)   
 [мастер приложений MFC](../Topic/MFC%20Application%20Wizard.md)