---
title: "Предупреждение (уровень 1) C4928 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4928
dev_langs:
- C++
helpviewer_keywords:
- C4928
ms.assetid: 77235d7f-9360-45cb-8348-d148c605c4a3
caps.latest.revision: 7
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
ms.openlocfilehash: 019a54b9911bd749e067a3a6989a8f79513f7181
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4928"></a>Предупреждение компилятора (уровень 1) C4928
недопустимая инициализация копии; неявно применено несколько пользовательских преобразований  
  
 Найден более чем одной подпрограммы определенного пользователем преобразования. При компиляции кода выполняется во всех этих процедурах.  
  
 Это предупреждение отключено по умолчанию. В разделе [компилятора предупреждения, — это отключение по умолчанию](../../preprocessor/compiler-warnings-that-are-off-by-default.md) подробнее.  
  
 Следующий пример приводит к возникновению ошибки C4928:  
  
```  
// C4928.cpp  
// compile with: /W1  
#pragma warning(default: 4928)  
  
struct I  
{  
};  
  
struct I1 : I  
{  
};  
  
struct I2 : I  
{  
};  
  
template <class T>  
struct Ptr  
{  
   operator T*()  
   {  
      return 0;  
   }  
  
   Ptr()  
   {  
   }  
  
   Ptr(I*)  
   {  
   }  
};  
  
int main()  
{  
   Ptr<I1> p1;  
   Ptr<I2> p2 = p1;   // C4928  
   // try one of the following two lines to resolve this error  
   // Ptr<I2> p2(p1);  
   // Ptr<I2> p2 = (I1*) p1;  
}  
```