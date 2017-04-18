---
title: "CRowset::MoveLast | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CRowset<TAccessor>::MoveLast"
  - "CRowset<TAccessor>::MoveLast"
  - "ATL.CRowset.MoveLast"
  - "ATL::CRowset::MoveLast"
  - "CRowset<TAccessor>.MoveLast"
  - "MoveLast"
  - "CRowset::MoveLast"
  - "ATL.CRowset<TAccessor>.MoveLast"
  - "CRowset.MoveLast"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MoveLast - метод"
ms.assetid: 81063578-ae9d-467b-8c88-81d8fc66e020
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# CRowset::MoveLast
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Перемещение курсора к последней строке.  
  
## Синтаксис  
  
```  
  
HRESULT MoveLast( ) throw( );  
  
```  
  
## Возвращаемое значение  
 Стандартное `HRESULT`.  
  
## Заметки  
 Вызывает метод [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx), чтобы переместить расположение следующ\- выборки на последней позиции и извлекает последняя строка.  
  
 Этот метод требуется набор **DBPROP\_CANSCROLLBACKWARDS** в `VARIANT_TRUE` до вызова метода **Открыть** на таблице или команда, содержащий набор строк. \(Для повышения производительности, необходимо также задать значение **DBPROP\_QUICKRESTART**`VARIANT_TRUE`\).  
  
## Требования  
 **Заголовок:** atldbcli.h  
  
## См. также  
 [Класс CRowset](../Topic/CRowset%20Class.md)   
 [CRowset::MoveNext](../../data/oledb/crowset-movenext.md)   
 [IRowset::RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx)   
 [CRowset::MovePrev](../../data/oledb/crowset-moveprev.md)