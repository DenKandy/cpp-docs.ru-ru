---
title: "COLUMN_NAME_LENGTH_STATUS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COLUMN_NAME_LENGTH_STATUS
dev_langs: C++
helpviewer_keywords: COLUMN_NAME_LENGTH_STATUS macro
ms.assetid: f73bd592-7ca7-461c-b106-9a8b1adbb01e
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 11f6b7086fb3403402d9a3da47a596c837868d3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="columnnamelengthstatus"></a>COLUMN_NAME_LENGTH_STATUS
Представляет привязку в наборе строк для конкретного столбца в наборе строк. Аналогично [COLUMN_NAME](../../data/oledb/column-name.md), за исключением того, что этот макрос также принимает длину столбца и состояние столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
COLUMN_NAME_LENGTH_STATUS(  
pszName  
,   
data  
,   
length  
,   
status )  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszName`  
 [in] Указатель на имя столбца. Имя должно быть строкой в Юникоде. Это можно сделать, поместив «L» перед именем, например: `L"MyColumn"`.  
  
 `data`  
 [in] Соответствующего члена данных в записи пользователя.  
  
 *length*  
 [in] Переменная может быть привязано к длина столбца.  
  
 *status*  
 [in] Переменная может быть привязано к состояние столбца.  
  
## <a name="remarks"></a>Примечания  
 В разделе [COLUMN_NAME](../../data/oledb/column-name.md) сведения о том, где **COLUMN_NAME_\***  используются макросы.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldbcli.h  
  
## <a name="see-also"></a>См. также  
 [Макросы и глобальные функции для шаблонов потребителей OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_NAME](../../data/oledb/column-name.md)   
 [COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)