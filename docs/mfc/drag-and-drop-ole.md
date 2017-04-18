---
title: "Перетаскивание (OLE) | Microsoft Docs"
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
  - "перетаскивание [C++]"
  - "перетаскивание [C++], о перетаскивании OLE"
  - "поддержка перетаскивания диспетчера файлов"
  - "OLE - приложения, перетаскивание"
  - "перетаскивание OLE"
  - "приложения сервера OLE, перетаскивание"
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Перетаскивание (OLE)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Функция перетаскивания OLE в основном ярлык для скопировать и вставить данные.  При использовании обмена, чтобы скопировать и вставить данные, несколько шагов необходимы.  Необходимо выделить данные, выберите пункт **Вырезать** или **Копировать** в меню **Изменить**, переход в конечный файл, окна или приложения, установите курсор в нужное место и нажмите кнопку **Вставить** в меню **Изменить**.  
  
 Перетаскивание OLE отличается от механизма перетаскивания файлового менеджера, который может обрабатывать только имена файлов и специально предназначенному для передачи имена файлов в приложения.  Перетаскивание OLE гораздо более общее.  Он позволяет перетаскиваним к любым данным, которые могут быть помещены в буфер обмена.  
  
 При использовании перетаскиванием OLE, удаляется из шага 2 процесса.  Необходимо выделить данные из окна источника \(«источника перетаскивания»\), перетащите его в нужное место назначения \(«целевому объекту перетаскивания»\), и удалите его с отпущена кнопка мыши.  Операция исключается необходимость в меню и быстрее, чем скопировать и вставить последовательность.  Единственное требование заключается в том, что и источник и целевой объект перетаскивания размещения должны быть открыты и по крайней мере частично отображаются на экране.  
  
 С помощью перетаскивания OLE, данные можно перемещать из одного места в другое в документе, между различными документами или между приложениями.  Его можно реализовать в контейнере или или серверном приложении, и любое приложение может быть источником размещения, целевым объектом перетаскивания, или и того, и другого.  Если приложение имеет и, размещение\- источника и целевого объекта поддержки перетаскивания, позволяет перетаскивания между дочерними окнами, или в одно окно.  Эта функция может сделать приложение гораздо проще использовать.  
  
 Если требуется использовать только перетаскивание OLE возможности см. в разделе [Перетаскивания: Настраивать](../Topic/Drag%20and%20Drop:%20Customizing.md).  С помощью методов проверки, описанных в этой статье, чтобы сделать источники размещения приложений не OLE.  Статья [Перетаскивания: Реализация целевой объект перетаскивания](../mfc/drag-and-drop-implementing-a-drop-target.md) описываются способы реализации поддержки целевого объекта и перетаскивания для приложений OLE и без OLE.  Также будет полезно просмотреть примеры MFC OLE [OCLIENT](../top/visual-cpp-samples.md) и [HIERSVR](../top/visual-cpp-samples.md).  
  
 Если не имеются семейство [Объекты данных и источники данных OLE \(\)](../mfc/data-objects-and-data-sources-ole.md) статей, может потребоваться ее сейчас.  Эти статьи описаны основные принципы передачи данных, а также реализовать его в приложениях.  
  
 Дополнительные сведения о перетаскивания см. в разделе:  
  
-   [Перетаскивания: Реализация источнику перетаскивания](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [Перетаскивания: Реализация целевой объект перетаскивания](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [Перетаскивания: Настраивать](../Topic/Drag%20and%20Drop:%20Customizing.md)  
  
## См. также  
 [OLE](../mfc/ole-in-mfc.md)   
 [Объекты и источники данных \(OLE\)](../mfc/data-objects-and-data-sources-ole.md)