---
title: "Ошибка компилятора C2382 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2382
dev_langs:
- C++
helpviewer_keywords:
- C2382
ms.assetid: 4d4436f9-d0d6-4bd0-b8ec-767b89adfb2f
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 0253c186855f8640b11dcb1a3ead7c27880d2fde
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2382"></a>Ошибка компилятора C2382
"функция": переопределение; разные спецификации исключений  
  
 В разделе [/Za](../../build/reference/za-ze-disable-language-extensions.md), эта ошибка означает, что предпринята попытка перегрузки функции только в [спецификацией исключений](../../cpp/exception-specifications-throw-cpp.md).  
  
 Следующий пример приводит к возникновению ошибки C2382:  
  
```  
// C2382.cpp  
// compile with: /Za /c  
void f1(void) throw(int) {}  
void f1(void) throw(char) {}   // C2382  
void f2(void) throw(char) {}   // OK  
```