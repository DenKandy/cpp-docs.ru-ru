---
title: "Приведение целочисленных значений в значения с плавающей запятой | Microsoft Docs"
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
  - "целые числа, приведение к значениям с плавающей запятой"
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Приведение целочисленных значений в значения с плавающей запятой
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.2.1.3** Направление усечение при преобразовании целого числа в число с плавающей запятой, которое не может точно представить исходное значение  
  
 Если целое число приводится к значению с плавающей запятой, которое точно не может представить это значение, это значение округляется \(в большую или меньшую сторону\) до ближайшего подходящего значения.  
  
 Например, приведение числа типа **unsigned long** \(точность — 32 бита\) к числу типа **float** \(мантисса которого имеет точность 23 бита\) округляет число до ближайшего четного 256.  Значения **long** от 4 294 966 913 до 4 294 967 167 округляются до значения типа **float** 4 294 967 040.  
  
## См. также  
 [Вычисления с плавающей запятой](../c-language/floating-point-math.md)