---
title: "Ошибка компилятора C3291 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3291
dev_langs:
- C++
helpviewer_keywords:
- C3291
ms.assetid: ed2e9f89-8dbc-4387-bc26-cc955e840858
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
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 231ccf64776c608131878caf9bdbe7e463903f6b
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3291"></a>Ошибка компилятора C3291
default: не может быть именем тривиального свойства  
  
 Тривиальное свойство нельзя назвать `default` В разделе [свойство](../../windows/property-cpp-component-extensions.md) для получения дополнительной информации.  
  
## <a name="example"></a>Пример  
 В следующем примере возникает ошибка C3291.  
  
```  
// C3291.cpp  
// compile with: /clr /c  
ref struct C {  
   property System::String ^ default;   // C3291  
   property System::String ^ Default;   // OK  
};  
```