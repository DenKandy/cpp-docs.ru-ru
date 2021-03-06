---
title: "CEnumerator::GetMoniker | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
dev_langs:
- C++
helpviewer_keywords:
- GetMoniker method
ms.assetid: 69a5cf2d-4a94-41dc-812d-bc1661d516d2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6049dfc14bb6ebe46f173ec07e536102acdebb3c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="cenumeratorgetmoniker"></a>CEnumerator::GetMoniker
Выполняет синтаксический анализ отображаемое имя для извлечения строки, который может быть преобразован в специальное имя компонента.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();  


HRESULT GetMoniker(LPMONIKER* ppMoniker,   
   LPCTSTR lpszDisplayName) const throw();  
```  
  
#### <a name="parameters"></a>Параметры  
 *ppMoniker*  
 [out] Моникер, извлеченными из отображаемое имя ([CEnumeratorAccessor::m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) текущей строки.  
  
 *lpszDisplayName*  
 [in] Отображаемое имя для синтаксического анализа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Стандартный `HRESULT`.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldbcli.h  
  
## <a name="see-also"></a>См. также  
 [Класс CEnumerator](../../data/oledb/cenumerator-class.md)