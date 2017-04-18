---
title: "Ошибка компилятора C3743 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3743
dev_langs:
- C++
helpviewer_keywords:
- C3743
ms.assetid: 7ca9a76e-7b60-46d1-ab8b-18600cf1a306
caps.latest.revision: 8
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 1a7f7e7b561e20f962aef4757d1248f1b7d3c6f5
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3743"></a>Ошибка компилятора C3743
когда параметр "layout_dependent" для event_receiver имеет значение true, установка и удаление обработчика допускаются только для всего интерфейса  
  
 [__Unhook](../../cpp/unhook.md) функции зависит от числа параметров, принимаемых на значение, передаваемое в `layout_dependent` параметр в [event_receiver](../../windows/event-receiver.md) класса.  
  
 Следующий пример приводит к возникновению ошибки C3743:  
  
```  
// C3743.cpp  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
[module(name="xx")];  
[object] __interface I { HRESULT f(); };  
  
[event_receiver(com, layout_dependent=true), coclass]  
struct R : I {  
        HRESULT f() {  
      return 0;  
   }  
        R() {  
   }  
  
   R(I* a) {  
      __hook(I, a, &R::f);   // C3743  
      // The following line resolves the error.  
      // __hook(I, a);  
   }  
};  
```