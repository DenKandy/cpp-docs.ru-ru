---
title: "Класс CBookmark | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b5c0f5f7a2af7c5b744fcad31ae6901988e92b9e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="cbookmark-class"></a>Класс CBookmark
Содержит значения закладки в свой буфер.  
  
## <a name="syntax"></a>Синтаксис

```cpp
template < DBLENGTH nSize = 0 >  
class CBookmark : public CBookmarkBase
  
template <>  
class CBookmark< 0 > : public CBookmarkBase  
```  
  
#### <a name="parameters"></a>Параметры  
 `nSize`  
 Размер буфера закладки в байтах. Когда `nSize` равен нулю, буфера закладки создается динамически во время выполнения.  
  
## <a name="members"></a>Участники  
  
### <a name="methods"></a>Методы  
  
|||  
|-|-|  
|[CBookmark](../../data/oledb/cbookmark-class.md)|Конструктор|  
|[GetBuffer](../../data/oledb/cbookmark-getbuffer.md)|Извлекает указатель на буфер.|  
|[GetSize](../../data/oledb/cbookmark-getsize.md)|Получает размер буфера в байтах.|  
|[SetBookmark](../../data/oledb/cbookmark-setbookmark.md)|Задает значение закладки.|  
  
### <a name="operators"></a>Операторы  
  
|||  
|-|-|  
|[оператор =](../../data/oledb/cbookmark-operator-equal.md)|Назначает один `CBookmark` класса в другой.|  
  
## <a name="remarks"></a>Примечания  
 **CBookmark\<0 >** является специализацией шаблона `CBookmark`; буфера создается динамически во время выполнения.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldbcli.h  
  
## <a name="see-also"></a>См. также  
 [Шаблоны потребителя OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Ссылка на шаблоны объекта-получателя OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)