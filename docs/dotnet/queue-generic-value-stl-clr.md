---
title: "Queue::generic_value (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::queue::generic_value
dev_langs:
- C++
helpviewer_keywords:
- generic_value member [STL/CLR]
ms.assetid: 5efd9812-6b4d-4e59-b8e8-c4975ae61667
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d4e3dbf57b9dd3535a430066cfd4c0eeda26ef92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="queuegenericvalue-stlclr"></a>queue::generic_value (STL/CLR)
Тип элемента для использования с универсальный интерфейс для контейнера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef GValue generic_value;  
```  
  
## <a name="remarks"></a>Примечания  
 Тип описывает объект типа `GValue` , описывающий значение хранимого элемента для использования с универсальный интерфейс для класса контейнера шаблона. (`GValue` либо `value_type` или `value_type^` Если `value_type` является типом ссылки.)  
  
## <a name="example"></a>Пример  
  
```  
// cliext_queue_generic_value.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get interface to container   
    Myqueue::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1->get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display in order using generic_value   
    for (; !gc1->empty(); gc1->pop())   
        {   
        Myqueue::generic_value elem = gc1->front();   
  
        System::Console::Write(" {0}", elem);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a b c  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext/очереди >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 [очереди (STL/CLR)](../dotnet/queue-stl-clr.md)   
 [Queue::generic_container (STL/CLR)](../dotnet/queue-generic-container-stl-clr.md)   
 [queue::value_type (STL/CLR)](../dotnet/queue-value-type-stl-clr.md)