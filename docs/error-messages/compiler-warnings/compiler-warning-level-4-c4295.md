---
title: "Предупреждение (уровень 4) C4295 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4295
dev_langs:
- C++
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
caps.latest.revision: 5
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
ms.openlocfilehash: 8afa9526c2a16c6a4062fd17480bd1d04bf51911
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-4-c4295"></a>Предупреждение компилятора (уровень 4) C4295
**'**   
 ***Массив* ": массив слишком мал, чтобы включить конечный символ null**  
  
 Массив был инициализирован, но последний знак в массиве не является пустым; доступ к массиву может привести к непредсказуемым результатам.  
  
 Следующий пример приводит к возникновению ошибки C4295:  
  
```  
// C4295.c  
// compile with: /W4  
  
int main() {  
   char a[3] = "abc";   // C4295  
}  
```