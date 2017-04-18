---
title: "GetRuntimeErrorDesc | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetRuntimeErrorDesc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ConversionError - метод"
  - "GetRuntimeErrorDesc - метод"
  - "RangeError - метод"
  - "ReferenceError - метод"
  - "RegExpError - метод"
  - "SyntaxError - метод"
  - "TypeError - метод"
  - "URIError - метод"
ms.assetid: d56fdd2e-6ad0-4c49-9e98-bcf0105e1b12
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# GetRuntimeErrorDesc
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Возвращает описание типа исключения.  
  
## Синтаксис  
  
```  
  
      function GetRuntimeErrorDesc(   
   strRuntimeErrorName    
);  
```  
  
#### Параметры  
 *strRuntimeErrorName*  
 Имя типа возникшего исключения.  
  
## Возвращаемое значение  
 Описание типа исключения.  
  
## Заметки  
 Возвращает описание типа исключения.  Может быть одним из следующих типов исключения:  
  
|Типы исключения|Описание|  
|---------------------|--------------|  
|ConversionError|Возникает, если производится попытка преобразовать объект во что\-то, во что он не может быть преобразован.|  
|RangeError|Возникает, если функция предоставляется с аргументом, значение которого выходит за его допустимый диапазон.  Например, эта ошибка возникает при попытке конструировать объект `Array` с длиной, представленной не допустимым положительным целым числом.|  
|ReferenceError|Возникает при обнаружении недопустимой ссылки.  Эта ошибка возникает, например, если ожидаемая ссылка равна null.|  
|RegExpError|Возникает, когда возникает ошибка компиляции при наличии регулярного выражения.  Эта ошибка возникает при компиляции регулярного выражения.  Эта ситуация возникает, например, если регулярное выражение объявляется с шаблоном, имеющим недопустимый синтаксис, или с флагами, отличными от *i*, *g*, or *m*, либо если в нем имеется один и тот же флаг, повторяющийся несколько раз.|  
|SyntaxError|Возникает, когда выполняется синтаксический анализ исходного текста, и этот исходный текст не позволяет корректировать синтаксис.  Например, эта ошибка возникает, если функция `eval` вызывается с аргументом, который не является допустимым текстом программы.|  
|TypeError|Возникает, если действительный тип операнда не соответствует предполагаемому типу.  Такая ситуация возникает, например, если вызов функции выполнен на чем\-то, что не является объектом или не поддерживает вызов.|  
|URIError|Возникает, если обнаруживается недопустимый URI.  Например, такая ошибка возникает, если в кодируемой или декодируемой строке обнаруживается недопустимый символ.|  
  
## См. также  
 [Настройка мастеров С\+\+ с помощью общих функций JScript.](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [Функции JScript для мастеров C\+\+](../ide/jscript-functions-for-cpp-wizards.md)   
 [Создание пользовательского мастера](../ide/creating-a-custom-wizard.md)   
 [Разработка мастера](../ide/designing-a-wizard.md)