---
title: "Ошибка компилятора C2130 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2130
dev_langs:
- C++
helpviewer_keywords:
- C2130
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
caps.latest.revision: 10
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
ms.openlocfilehash: 0e6bcfc51ac27b060205d6191b5189e6d7071238
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2130"></a>Ошибка компилятора C2130
\#строки требуется строка, содержащая имя файла, найден «токен»  
  
 Дополнительный токен имени файла после [#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` должно быть строкой.  
  
 При компиляции следующего примера возникнет ошибка C2130:  
  
```  
// C2130.cpp  
int main() {  
   #line 1000 test   // C2130  
   #line 1000 "test"   // OK  
}  
```