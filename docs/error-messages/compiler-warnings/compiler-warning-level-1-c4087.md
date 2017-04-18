---
title: "Предупреждение (уровень 1) C4087 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4087
dev_langs:
- C++
helpviewer_keywords:
- C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
caps.latest.revision: 6
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
ms.openlocfilehash: 8c1ef0f7bc9badfc8ddd5f2cf0420568d4f524fb
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4087"></a>Предупреждение компилятора (уровень 1) C4087
"функция": объявлена со списком параметров void  
  
 Объявление функции не имеет формальных параметров, но вызов функции содержит фактические параметры. Лишние параметры передаются в соответствии с соглашением о вызовах функции.  
  
 Это предупреждение для компилятора C.  
  
## <a name="example"></a>Пример  
  
```  
// C4087.c  
// compile with: /W1  
int f1( void ) {  
}  
  
int main() {  
   f1( 10 );   // C4087  
}  
```