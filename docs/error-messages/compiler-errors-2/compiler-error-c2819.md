---
title: "Ошибка компилятора C2819 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2819"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2819"
ms.assetid: fcc7762d-cb82-4bb1-a715-0d82da832edf
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Ошибка компилятора C2819
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

тип «тип» не имеет перегруженный элемент оператор «\-\>»  
  
 Необходимо определить `operator->()`, чтобы использовать данную операцию над указателями.  
  
 Следующий пример приводит к возникновению ошибки C2819:  
  
```  
// C2819.cpp  
// compile with: /c  
class A {  
   public:  
      int i;  
};  
  
class B {};  
  
void C(B j) {  
   j->i;   // C2819  
}  
  
class D {  
   A* pA;  
  
   public:  
      A* operator->() {  
         return pA;  
      }  
};  
  
void F(D j) {  
   j->i;  
}  
```  
  
 Ошибка C2819 также может возникнуть при использовании [Семантика стека C\+\+ для ссылочных типов](../../dotnet/cpp-stack-semantics-for-reference-types.md).  Следующий пример приводит к возникновению ошибки C2819:  
  
```  
// C2819_b.cpp  
// compile with: /clr  
ref struct R {  
   void Test() {}  
};  
  
int main() {  
   R r;  
   r->Test();   // C2819  
   r.Test();   // OK  
}  
```