---
title: "Предупреждение компилятора (уровень 1) C4272 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4272"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4272"
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Предупреждение компилятора (уровень 1) C4272
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"функция" : помечена как \_\_declspec\(dllimport\); необходимо указать машинное соглашение о вызове при импорте функции.  
  
 Экспорт функции, помеченной соглашением о вызове [\_\_clrcall](../../cpp/clrcall.md), приводит к ошибке. Компилятор выдаст это предупреждение при попытке импорта функции, отмеченной как `__clrcall`.  
  
 Следующий пример приводит к возникновению ошибки C4272:  
  
```  
// C4272.cpp  
// compile with: /c /W1 /clr  
__declspec(dllimport) void __clrcall Test();   // C4272  
__declspec(dllimport) void Test2();   // OK  
```