---
title: "Структура common_type | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "chrono/std::common_type"
dev_langs: 
  - "C++"
ms.assetid: 2b42722c-c3dc-4d62-8613-0271e52b6f00
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Структура common_type
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Описывает специализации шаблона класса [common\_type](../standard-library/common-type-class.md) для созданий [длительность](../standard-library/duration-class.md) и [time\_point](../standard-library/time-point-class.md).  
  
## Синтаксис  
  
```  
template<class Rep1, class Period1,  
   class Rep2, class Period2>  
struct common_type  
<chrono::duration<Rep1, Period1>,   
chrono::duration<Rep2, Period2>>;  
  
template<class Clock,  
   class Duration1, class Duration2>  
struct common_type  
<chrono::time_point<Clock, Duration1>,  
chrono::time_point<Clock, Duration2>>;  
```  
  
## Требования  
 **Заголовок:**  chrono  
  
 **Пространство имен:** std  
  
## См. также  
 [Справочные материалы по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)