---
title: "Класс remove_reference | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- remove_reference
- std::remove_reference
- type_traits/std::remove_reference
dev_langs:
- C++
helpviewer_keywords:
- remove_reference class
- remove_reference
ms.assetid: 294e1965-3ae3-46ee-bc42-4fdf60c24717
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: 873efb477296b9f6765eb9a85d9ac62f63405382
ms.lasthandoff: 02/24/2017

---
# <a name="removereference-class"></a>Класс remove_reference
Делает из типа не ссылочный тип.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template <class T>  
struct remove_reference;  
 
template <class T>  
using remove_reference_t = typename remove_reference<T>::type;  
```  
  
#### <a name="parameters"></a>Параметры  
 `T`  
 Тип для изменения.  
  
## <a name="remarks"></a>Примечания  
 Экземпляр `remove_reference<T>` содержит измененный тип, т. е. `T1`, если `T` имеет форму `T1&`; в противном случае — `T`.  
  
## <a name="example"></a>Пример  
  
```cpp  
#include <type_traits>   
#include <iostream>   
  
int main()   
    {   
    int *p = (std::remove_reference_t<int&> *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "remove_reference_t<int&> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
remove_reference_t<int&> == int  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<type_traits>  
  
 **Пространство имен:** std  
  
## <a name="see-also"></a>См. также  
 [<type_traits>](../standard-library/type-traits.md)   
 [Класс add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)
