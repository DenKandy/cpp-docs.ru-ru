---
title: "Ошибка компилятора C3624 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3624
dev_langs:
- C++
helpviewer_keywords:
- C3624
ms.assetid: eaac6a4f-eb11-4e4d-ab12-124ba995c5cf
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: b7862590432e2aaa5c41126abb1ebd92ebeb05a3
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3624"></a>Ошибка компилятора C3624
«Тип»: использование этого типа необходима ссылка на сборку «сборка»  
  
 Сборка (ссылка), необходимые для компиляции кода не указан; передать сборку с [#using](../../preprocessor/hash-using-directive-cpp.md) директивы.  
  
## <a name="example"></a>Пример  
Следующий пример приводит к возникновению ошибки C3624:  
  
```  
// C3624.cpp  
// compile with: /clr /c  
#using <System.Windows.Forms.dll>  
  
// Uncomment the following 2 lines to resolve.  
// #using <System.dll>  
// #using <System.Drawing.dll>  
  
using namespace System;  
  
public ref class MyForm : public Windows::Forms::Form {};   // C3624  
```  
