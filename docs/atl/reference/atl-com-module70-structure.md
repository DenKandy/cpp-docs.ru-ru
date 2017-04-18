---
title: "Структура _ATL_COM_MODULE70 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4e393abb2a904a0f5e101efe3d78d0645664397b
ms.openlocfilehash: 503c2a29cf0e70020b012911c51b056f00562374
ms.lasthandoff: 02/24/2017

---
# <a name="atlcommodule70-structure"></a>Структура _ATL_COM_MODULE70
Используемый код, связанный с COM в ATL.  
  
## <a name="syntax"></a>Синтаксис  
  
```
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```  
  
## <a name="members"></a>Члены  
 `cbSize`  
 Размер структуры, используемые для управления версиями.  
  
 `m_hInstTypeLib`  
 Экземпляр дескриптора в библиотеку типов для этого модуля.  
  
 **m_ppAutoObjMapFirst**  
 Адрес элемента массива, указывающее начало записи сопоставления объектов для этого модуля.  
  
 **m_ppAutoObjMapLast**  
 Адрес элемента массива, указывая на конец записей сопоставлений объект для этого модуля.  
  
 `m_csObjMap`  
 Критический раздел сериализации доступа к операции сопоставления объекта. Используется внутренними механизмами ATL.  
  
## <a name="remarks"></a>Примечания  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) определяется как typedef для `_ATL_COM_MODULE70`.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atlbase.h  
  
## <a name="see-also"></a>См. также  
 [Структуры](../../atl/reference/atl-structures.md)





