---
title: "Роль пользователя в работе с представлением записи (доступ к данным MFC) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- record views, customizing default code
- MFC, record views
ms.assetid: 691e89a5-ff21-4ca3-9278-69d4678288bb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 03d64715f3bdfb6028fdb039451d4b4b004a059e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="your-role-in-working-with-a-record-view--mfc-data-access"></a>Роль пользователя в работе с представлением записи (доступ к данным MFC)
Следующая таблица показывает, что обычно необходимо сделать, чтобы работать с представлением записи и что платформа делает за вас.  
  
### <a name="working-with-a-record-view-you-and-the-framework"></a>Работа с представлением записи: разработчик и среда  
  
|Вы|Платформа|  
|---------|-------------------|  
|Используйте редактор диалоговых окон Visual C++ для разработки формы.|Создает ресурс шаблона диалоговых окон с элементами управления.|  
|Используйте [мастер приложений MFC](../mfc/reference/database-support-mfc-application-wizard.md) для создания классов, производных от [CRecordView](../mfc/reference/crecordview-class.md) и [CRecordset](../mfc/reference/crecordset-class.md).|Создает классы за вас.|  
|Сопоставление элементов управления представления записи с элементами данных полей набора записей.|Обеспечивает обмен данных между элементами управления и полями набора записей.|  
||Предоставляет обработчиков команд по умолчанию **переместить первый**, **переместить последний**, **переместить следующий**, и **Переместить предыдущий** команд из меню или панели инструментов кнопки.|  
||Сохраняет изменения в источнике данных|  
|[Дополнительно] Напишите код для заполнения списка или поля со списком или других элементов управления данными из второго набора записей.||  
|[Дополнительно] Написание кода необязательно.||  
|[Дополнительно] Напишите код для добавления и удаления записей.||  
  
 Программирование на основе формы является только одним подходом в работе с базой данных. Сведения о приложениях, использующих другой пользовательский интерфейс или нет пользовательский интерфейс см. в разделе [MFC: использование классов базы данных с документами и представлениями](../data/mfc-using-database-classes-with-documents-and-views.md) и [MFC: использование классов базы данных без документов и представлений](../data/mfc-using-database-classes-without-documents-and-views.md). Альтернативные подходы к отображению записей базы данных в разделе классы [CListView](../mfc/reference/clistview-class.md) и [CTreeView](../mfc/reference/ctreeview-class.md).  
  
## <a name="see-also"></a>См. также  
 [Представления записей (доступ к данным MFC)](../data/record-views-mfc-data-access.md)   
 [Список драйверов ODBC](../data/odbc/odbc-driver-list.md)