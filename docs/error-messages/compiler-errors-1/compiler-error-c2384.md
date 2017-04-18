---
title: "Compiler Error C2384 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2384"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2384"
ms.assetid: 8145f7ad-31b1-406d-ac43-0d557feab635
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# Compiler Error C2384
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

member: невозможно применить \_\_declspec\(thread\) к члену управляемого класса или класса WinRT  
  
 Модификатор [thread](../../cpp/thread.md) `__declspec` нельзя применять к членам управляемого класса или класса среды выполнения Windows.  
  
 Локальное хранилище статического потока в управляемом коде может использоваться только для статически загружаемых библиотек DLL \(библиотека  загружается статически при запуске процесса\).  Среда выполнения Windows не поддерживает локальное хранилище потока.  
  
 Следующая строка вызывает ошибку C2384. Также показано, как устранить ее в коде C\+\+\/CLI:  
  
```  
// C2384.cpp  
// compile with: /clr /c  
public ref class B {  
public:  
   __declspec( thread ) static int tls_i = 1;   // C2384  
  
   // OK - declare with attribute instead  
   [System::ThreadStaticAttribute]  
   static int tls_j;  
};  
```