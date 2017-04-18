---
title: "Ошибка компилятора C3618 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3618"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3618"
ms.assetid: cacc105d-4389-4cb8-ae6c-41a3622e9a86
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Ошибка компилятора C3618
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"функция": нельзя определять методы, помеченные атрибутом DllImport  
  
 Метод, помеченный атрибутом <xref:System.Runtime.InteropServices.DllImportAttribute>, определяется в указанной библиотеке DLL.  
  
## Пример  
 Следующий пример приводит к возникновению ошибки C3618:  
  
```  
// C3618.cpp  
// compile with: /clr /c  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[ DllImport("user32.dll", EntryPoint="MessageBox", CharSet=CharSet::Ansi) ]  // CHANGED   
void Func();   
  
void Func() {}   // C3618, remove this function definition to resolve  
```