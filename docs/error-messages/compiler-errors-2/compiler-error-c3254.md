---
title: "Ошибка компилятора C3254 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3254"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3254"
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Ошибка компилятора C3254
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"явное переопределение" : класс содержит явное переопределение "переопределение", но не является наследником интерфейса, содержащего объявление функции  
  
 При [явном переопределении](../../cpp/explicit-overrides-cpp.md) метода класс, содержащий это переопределение, должен явно или неявно наследовать от типа, который содержит переопределяемую функцию.  
  
 Следующий пример приводит к возникновению ошибки C3254:  
  
```  
// C3254.cpp  
__interface I  
{  
   void f();  
};  
  
__interface I1 : I  
{  
};  
  
struct A /* : I1 */  
{  
   void I1::f()  
   {   // C3254, uncomment : I1 to resolve this C3254  
   }  
};  
  
int main()  
{  
}  
```