---
title: "Предупреждение (уровень 1) C4440 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4440
dev_langs:
- C++
helpviewer_keywords:
- C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
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
ms.openlocfilehash: 39205d805299df753f6b3af3733195bb6078567f
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4440"></a>Предупреждение компилятора (уровень 1) C4440
вызов переопределения соглашение «calling_convention1» в «соглашение о вызове&2;» игнорируется  
  
 Попытка изменения соглашения о вызовах был пропущен.  
  
 Следующий пример приводит к возникновению ошибки C4440:  
  
```  
// C4440.cpp  
// compile with: /W1 /LD /clr  
typedef void __clrcall F();  
typedef F __cdecl *PFV;   // C4440  
```