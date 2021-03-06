---
title: "ComPtr::operator =-оператор | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 1a0c2752-f7d8-4819-9443-07b88b69ef02
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 30f04bdfe7b508bf83e34992fefdcb10c58b4655
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="comptroperator-operator"></a>Оператор ComPtr::operator=
Присваивает значение текущему объекту ComPtr.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
WRL_NOTHROW ComPtr& operator=(  
   decltype(__nullptr)  
);  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ T *other  
);  
template <  
   typename U  
>  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr &other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr<U>& other  
);  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr &&other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr<U>&& other  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `U`  
 Класс.  
  
 `other`  
 Указатель, ссылка или rvalue ссылаются на тип или другой объект ComPtr.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Ссылка на текущий объект ComPtr.  
  
## <a name="remarks"></a>Примечания  
 Первая версия этого оператора присваивает пустое значение текущему объекту ComPtr.  
  
 Во второй версии, если присваиваемый указатель интерфейса не совпадает с текущим указателем интерфейса ComPtr, второй указатель интерфейса присваивается текущему объекту ComPtr.  
  
 В третьей версии присваиваемый указатель интерфейса присваивается текущему объекту ComPtr.  
  
 В четвертой версии, если указатель интерфейса присваиваемого значения не совпадает с текущим указателем интерфейса ComPtr, второй указатель интерфейса присваивается текущему объекту ComPtr.  
  
 Пятая версия является оператором копирования; ссылка на объект ComPtr присваивается текущему объекту ComPtr.  
  
 Шестая версия является оператором копирования, использующим семантику перемещения; rvalue ссылается на объект ComPtr, если любой тип приводится статически, а затем присваивается текущему объекту ComPtr.  
  
 Седьмая версия является оператором копирования, использующим семантику перемещения; rvalue ссылается на объект ComPtr типа `U`, который приводится статически, а затем присваивается текущему объекту ComPtr.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** client.h  
  
 **Пространство имен:** Microsoft::WRL  
  
## <a name="see-also"></a>См. также  
 [Класс ComPtr](../windows/comptr-class.md)