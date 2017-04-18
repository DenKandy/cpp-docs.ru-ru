---
title: "Ошибка компилятора C2460 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2460"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2460"
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Ошибка компилятора C2460
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"идентификатор1" : использует "идентификатор2", который определяется  
  
 Класс или структура \(`identifier2`\) объявлены как член самого себя \(`identifier1`\).  Рекурсивные определения классов и структур недопустимы.  
  
 Следующий пример приводит к возникновению ошибки C2460:  
  
```  
// C2460.cpp  
class C {  
   C aC;    // C2460  
};  
```  
  
 Вместо этого в классе необходимо использовать ссылку на указатель.  
  
```  
// C2460.cpp  
class C {  
   C * aC;    // OK  
};  
```