---
title: "Ошибка компилятора C2750 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2750
dev_langs:
- C++
helpviewer_keywords:
- C2750
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96f66115c2e51a7ed49cc20c6b5da94a61cab555
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2750"></a>Ошибка компилятора C2750
«Тип»: нельзя использовать «new» для ссылочного типа; Вместо этого использовать «gcnew»  
  
 Для создания экземпляра типа CLR, которое вызывает экземпляр должен располагаться в куче сбора мусора, необходимо использовать [gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md).  
  
 Следующий пример приводит к возникновению ошибки C2750:  
  
```  
// C2750.cpp  
// compile with: /clr  
ref struct Y1 {};  
  
int main() {  
   Y1 ^ x = new Y1;   // C2750  
  
   // try the following line instead  
   Y1 ^ x2 = gcnew Y1;  
}  
```