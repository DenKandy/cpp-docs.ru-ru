---
title: "Сокеты Windows. Сокеты потоков | Microsoft Docs"
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
  - "сокеты [C++], сокеты потока"
  - "сокеты потока [C++]"
  - "Сокеты Windows [C++], сокеты потока"
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Сокеты Windows. Сокеты потоков
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

В этом разделе описываются сокеты потока, один из 2 типов, доступных сокета Windows. Другой тип \( [сокет датаграмм](../mfc/windows-sockets-datagram-sockets.md)\).  
  
 Сокеты потока обеспечивают для потока данных, рекордных границ: поток байтов, которые могут быть двунаправленный \(приложению о: он может и отправки и получения через сокет\).  Потоки можно положиться на, чтобы доставлять последовательного, unduplicated данные. \(«Последовательного» означает, что пакеты доставлены в отправленном порядке. «Unduplicated» означает, что при получении указанный пакет только один раз\). Отправку данных сообщений потока гарантировано и поток хорошо подходит для обработки больших объемов данных.  
  
 Транспортный уровень сети может прекращать или группирования данных в пакеты разумного размера.  Класс `CSocket` обрабатывает упаковка и распаковывать автоматически.  
  
 Потоки основаны на точные подключений: запросы сокета a подключение к сокету B; сокет б принимает или отклоняет запрос подключения.  
  
 Телефона вызов обеспечивает хорошую аналогию для потока.  В обычных условиях, принимающая сторона слышит сообщает, что в порядке их получает его, без дублирования или потери.  Сокеты соответствующие потока, например для реализаций, например протокол FTP \(FTP\), который облегчает передачи ASCII или двоичные файлы произвольного размера.  
  
 Сокеты потока предпочтительны к сокетам датаграмм, когда данные должны гарантировать, что приехали и при большой размер данных.  Сокеты потока Дополнительные сведения о см. в спецификации Windows SSL.  Спецификация доступна в [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
 С помощью сокетов потока может быть главн приложениям конструированным для использования сокета датаграмм для широковещательной передачи ко всем получение сокетам в сети, поскольку  
  
-   Широковещательная модель и проблемы потока сети \(или «шторма»\).  
  
-   Модель клиент\-сервера принята далее более эффективным.  
  
-   Передача достоверных данных предоставляет потока модели, где модель датаграммы не требуется.  
  
-   Конечная модель использует возможности взаимодействия между юникод и приложениями сокета ANSI, класс CArchive одалживает в класс CSocket.  
  
    > [!NOTE]
    >  При использовании класса `CSocket`, необходимо использовать поток.  Утверждение MFC завершается неудачей, если указать тип сокета как **SOCK\_DGRAM**.  
  
## См. также  
 [Сокеты Windows в MFC](../mfc/windows-sockets-in-mfc.md)   
 [Сокеты Windows. Фон](../mfc/windows-sockets-background.md)