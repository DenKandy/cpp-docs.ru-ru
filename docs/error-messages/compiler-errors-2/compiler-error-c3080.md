---
title: "Ошибка компилятора ошибка C3080 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3080
dev_langs:
- C++
helpviewer_keywords:
- C3080
ms.assetid: ff62a3f7-9b3b-44bd-b8d9-f3a8e5354560
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: 631a4e1b0b3304d376be8708cf0f9d5ab39dbd9e
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3080"></a>Ошибка компилятора C3080
"функция_метода_завершения": метод завершения не может иметь спецификатор класса хранения  
  
 Дополнительные сведения см. в разделе [деструкторы и методы завершения в Практическое руководство: определение и использование классов и структур (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
## <a name="example"></a>Пример  
 В следующем примере возникает ошибка C3080.  
  
```  
// C3080.cpp  
// compile with: /clr /c  
ref struct rs {  
protected:  
   static !rs(){}   // C3080  
   !rs(){}   // OK  
};  
```