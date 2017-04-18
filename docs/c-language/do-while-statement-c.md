---
title: "Оператор do-while (C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "do"
  - "while"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "do-while - ключевое слово [C]"
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Оператор do-while (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Оператор `do-while` позволяет повторять выполнение оператора или составного оператора до тех пор, пока указанное выражение не станет ложным.  
  
## Синтаксис  
 *оператор\-итерации*:  
 **do**  *оператор*  **while \(**  *выражение*  **\) ;**  
  
 *Выражение* в операторе `do-while` вычисляется после выполнения тела цикла.  Поэтому тело цикла всегда выполняется по крайней мере один раз.  
  
 *Выражение* должно иметь арифметический тип или тип указателя.  Выполнение происходит следующим образом:  
  
1.  Выполняется тело оператора.  
  
2.  Затем вычисляется значение *выражения*.  Если значение *выражения* ложно, выполнение оператора `do-while` завершается и управление передается следующему оператору программы.  Если значение *выражения* истинно \(не равно нулю\), процесс повторяется с шага 1.  
  
 Выполнение оператора `do-while` может также прерываться, если в теле оператора выполняется оператор **break**, `goto` или `return`.  
  
 Ниже приводится пример оператора `do-while`.  
  
```  
do   
{  
    y = f( x );  
    x--;  
} while ( x > 0 );  
```  
  
 В этом операторе `do-while` два оператора `y = f( x );` и `x--;` выполняются независимо от начального значения переменной `x`.  Затем вычисляется выражение `x > 0`.  Если `x` больше 0, тело оператора выполняется еще раз и снова вычисляется выражение `x > 0`.  Тело оператора многократно выполняется, пока значение переменной `x` остается больше 0.  Выполнение оператора `do-while` завершается, когда значение переменной `x` становится равным 0 или отрицательным.  Тело цикла выполняется по крайней мере один раз.  
  
## См. также  
 [Выражение do\-while \(C\+\+\)](../cpp/do-while-statement-cpp.md)