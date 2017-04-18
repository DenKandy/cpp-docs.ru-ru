---
title: "Контейнеры. Составные файлы | Microsoft Docs"
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
  - "режимы доступа для файлов [C++]"
  - "составные документы"
  - "составные файлы"
  - "контейнеры [C++], составные файлы"
  - "документы [C++], составное"
  - "документы [C++], OLE"
  - "файлы [C++], составное"
  - "OLE - контейнеры, составные файлы"
  - "OLE-документы, составные файлы"
  - "производительность [C++], составные файлы"
  - "составные файлы стандартизированной файловой структуры"
ms.assetid: 8b83cb3e-76c8-4bbe-ba16-737092b36f49
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Контейнеры. Составные файлы
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

В этой статье описывается компоненты и реализации составных файлов и преимуществ и недостатков использования составных файлов в приложениях OLE.  
  
 Составные файлы целая часть OLE.  Они используются для упрощения хранилище передачи данных и документа OLE.  Составные файлы реализация активной, состоящей из модели хранения.  Последовательные интерфейсов существуют этой поддержки сериализации в хранилище, поток или объект файла.  Составные файлы поддерживаются в библиотеки Microsoft Foundation Class классами `COleStreamFile` и `COleDocument`.  
  
> [!NOTE]
>  С помощью составного файл не означает, что данные берутся из OLE документа или составного документа.  Составные файлы только один из способов хранения составных документов, OLE документы и другие данные.  
  
##  <a name="_core_components_of_a_compound_file"></a> Компоненты составного файла  
 Реализация OLE составных файлов используется 3 типа объектов: объекты потока хранилища, объекты и объекты `ILockBytes`.  Эти объекты аналогичны компоненты стандартной файловой системы следующими способами:  
  
-   Объекты потока, как файлы, сохранять данные любого типа.  
  
-   Объекты хранения данных, как и каталоги, могут содержать другие объекты и хранилища потока.  
  
-   объекты **LockBytes** — это интерфейс между объектами хранилища и физическим оборудованием.  Они определяют, как фактические байты записываются в любое запоминающее устройство объект **LockBytes** доступа, например жесткий диск или глобальной области памяти.  Дополнительные сведения о объекты **LockBytes** и интерфейс `ILockBytes` см. в *справочнике программиста OLE*.  
  
##  <a name="_core_advantages_and_disadvantages_of_compound_files"></a> Преимущества и недостатки составных файлов  
 Составные файлы обеспечивают преимущества не доступные с прежними методами хранилища файлов.  В их число входят следующие элементы управления.  
  
-   Последовательный доступ к файлу.  
  
-   Режимы доступа к файлу.  
  
-   Стандартизация структуры файлов.  
  
 Потенциальные недостатки составных файлов — крупноразмерных и проблем производительности, относящиеся к хранения на дисках неповоротливых — считаться решая, будут ли их использования в приложении.  
  
###  <a name="_core_incremental_access_to_files"></a> Последовательный доступ к файлам  
 Последовательный доступ к файлам автоматическое преимущество использования составных файлов.  Поскольку составной файл можно просматривать как «файловая система» в файле, типы отдельного объекта, например поток или хранилище можно получать доступ без необходимости загрузки всего файла.  Это может значительно сократить время приложению необходим доступ к новые объекты для редактирования пользователем.  Последовательный обновления, основанный на одном концепции, предоставляет аналогичные преимущества.  Сохранить весь файл, а не только для сохранения изменений в один объект OLE, сохраняет только поток или объект хранилища изменянные пользователем.  
  
###  <a name="_core_file_access_modes"></a> Режимы доступа к файлам  
 Возможность определить, когда изменения объектов в составном файле фиксируются на диск другим преимуществом использования составных файлов.  Режим, в котором осуществляется доступ, либо транзакционных или управляющие файлы, определяет, когда изменения фиксируются.  
  
-   Режима транзакций использует операции двухфазной фиксации для внесения изменений объектов в составном файле, тем самым хранение и старые и новые копии документа, до тех пор, пока пользователь не завершит выбор либо сохранить или отменить изменения.  
  
-   Непосредственное управление включает изменения в документ, как они выполняются без возможности отменить их позже.  
  
 Дополнительные сведения о режимах доступа см. в *справочнике программиста OLE*.  
  
###  <a name="_core_standardization"></a> Стандартизация  
 Структура унифицированная составных файлов позволяет различным приложениям OLE сканировать составные файлы, созданные приложением OLE без статьи приложения, фактически создал XML\-файл.  
  
###  <a name="_core_size_and_performance_considerations"></a> Размер и производительности.  
 Так как структуры хранения этих файлов и возможности сохранения данных последовательно, файлы с помощью этот формат имеют тенденцию превышать другие файлы с помощью неструктурированного хранилища или «неструктурированного файла».  Если приложение часто загружает и сохраняет файлы, применение составных файлов может привести к увеличить размер файла гораздо быстрее, чем файлы noncompound.  Поскольку составные файлы могут получить большими, так и для файлов, хранящихся в нагружало из дискет также может быть трогнуто, и в более медленном доступе к файлам.  
  
 Это делается путем, влияющие на производительность фрагментация составного файла.  Размер файла составного определяется различием между первым и последними участками диска, используемыми файлом.  Разделенный файл может содержать множество областей свободного пространства, не содержащих данных, но считается высчитывая размер.  Во время существования этих файлов, эти области создаются вставкой или удалением объектов хранилища.  
  
##  <a name="_core_using_compound_files_format_for_your_data"></a> Использование составных формат файла для данных.  
 После успешного создания приложения, имеет класс документа, производном от `COleDocument`, убедитесь, свои вызовы конструктора `EnableCompoundFile` основного документа.  Когда мастер приложений создает приложения OLE\-контейнер, а этот вызов автоматически.  
  
 В *справочнике программиста OLE* см. в разделах [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034), [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) и [ILockBytes](http://msdn.microsoft.com/library/windows/desktop/aa379238).  
  
## См. также  
 [Контейнеры](../mfc/containers.md)   
 [Контейнеры. Проблемы пользовательского интерфейса](../mfc/containers-user-interface-issues.md)   
 [COleStreamFile Class](../Topic/COleStreamFile%20Class.md)   
 [COleDocument Class](../mfc/reference/coledocument-class.md)