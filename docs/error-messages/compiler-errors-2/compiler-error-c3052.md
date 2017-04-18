---
title: "Ошибка компилятора C3052 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3052
dev_langs:
- C++
helpviewer_keywords:
- C3052
ms.assetid: 87480c42-1ceb-4775-8d20-88c54a7bb6a6
caps.latest.revision: 7
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
ms.openlocfilehash: 65c77919d980d574c0dacb27e9fc33f94d80391f
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3052"></a>Ошибка компилятора C3052
"переменная": переменная не встречается в предложении совместного использования данных под предложением default(none)  
  
 Если [default(none)](../../parallel/openmp/reference/default-openmp.md) — используется, все переменные, используемые в структурированном блоке должна быть указана явно как [общего](../../parallel/openmp/reference/shared-openmp.md) или [частного](../../parallel/openmp/reference/private-openmp.md).  
  
 Следующий пример приводит к возникновению ошибки C3052:  
  
```  
// C3052.cpp  
// compile with: /openmp /c  
int main() {  
   int n1 = 1;  
  
   #pragma omp parallel default(none) // shared(n1) private(n1)  
   {  
      n1 = 0;   // C3052 use either a shared or private clause  
   }  
}  
```