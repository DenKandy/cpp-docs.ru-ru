---
title: "Ошибка компилятора C2377 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2377
dev_langs:
- C++
helpviewer_keywords:
- C2377
ms.assetid: f7660965-bf4c-4cd9-8307-1bd7016678a1
caps.latest.revision: 8
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
ms.openlocfilehash: 1b5176e81db7cc25d49ff00b0838e661ed6b651a
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2377"></a>Ошибка компилятора C2377
"идентификатор": переопределение; typedef нельзя перегрузить с другим символом  
  
 Идентификатор `typedef` переопределяется.  
  
 В следующем примере возникает ошибка C2377:  
  
```  
// C2377.cpp  
// compile with: /c  
typedef int i;  
int i;   // C2377  
int j;   // OK  
```