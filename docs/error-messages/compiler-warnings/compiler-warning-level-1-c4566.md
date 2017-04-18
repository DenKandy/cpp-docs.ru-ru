---
title: "Предупреждение компилятора (уровень 1) C4566 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4566"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4566"
ms.assetid: 65f40730-e86f-447c-b37b-16caadcfe311
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Предупреждение компилятора (уровень 1) C4566
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

символ, представленный универсальным именем символа "знак", невозможно представить в текущей кодовой странице \(страница\)  
  
 Не все символы Юникод могут быть представлены на текущей кодовой странице ANSI.  
  
 Строки обычных символов \(однoбайтовые символы\) преобразуются в многобайтовые символы, в то время как двухбайтовые строки \(двухбайтовые символы\) не подлежат преобразованию.  
  
 Следующий пример приводит к возникновению ошибки C4566:  
  
```  
// C4566.cpp  
// compile with: /W1  
int main() {  
   char c1 = '\u03a0';   // C4566  
   char c2 = '\u0642';   // C4566  
  
   wchar_t c3 = L'\u03a0';   // OK  
   wchar_t c4 = L'\u0642';   // OK  
}  
```