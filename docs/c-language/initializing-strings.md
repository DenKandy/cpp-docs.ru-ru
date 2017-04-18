---
title: "Инициализация строк | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "массив знаков, инициализация"
  - "инициализация массивов, строки"
  - "строки [C++], инициализация"
ms.assetid: 0ab8079d-d0d3-48f9-afd1-36a7bb439b29
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Инициализация строк
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Массив символов \(или расширенных символов\) можно инициализировать со строковым литералом \(или расширенным строковым литералом\).  Например:  
  
```  
char code[ ] = "abc";  
```  
  
 Этот код инициализирует символьный массив `code` с четырьмя элементами.  Четвертым элементом является символ null, которым завершаются все строковые литералы.  
  
 Длина списка идентификаторов может быть равна количеству инициализируемых идентификаторов.  Если указанный размер массива меньше длины строки, то лишние символы игнорируются.  Например, следующее объявление инициализирует символьный массив `code` с тремя элементами:  
  
```  
char code[3] = "abcd";  
```  
  
 Массиву `code` присваиваются только первые три символа инициализатора.  Символ `d` и символ null, завершающий строки, отбрасываются.  Обратите внимание, что при этом будет создана незавершенная строка \(т. е. строка без значения 0, которым обозначается ее конец\) и сгенерировано диагностическое сообщение, указывающее на это состояние.  
  
 Объявление  
  
```  
char s[] = "abc", t[3] = "abc";  
```  
  
 идентично объявлению  
  
```  
char s[]  = {'a', 'b', 'c', '\0'},   
     t[3] = {'a', 'b', 'c' };  
```  
  
 Если строка короче указанного размера массива, то остальные элементы массива инициализируются как равные 0.  
  
 **Блок, относящийся только к системам Microsoft**  
  
 В Microsoft C строковые литералы могут иметь длину до 2048 байт.  
  
 **Завершение блока, относящегося только к системам Microsoft**  
  
## См. также  
 [Инициализация](../c-language/initialization.md)