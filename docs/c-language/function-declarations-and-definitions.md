---
title: "Объявления и определения функций | Microsoft Docs"
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
  - "объявление функций"
  - "объявление функций, определения функций"
  - "внешние объявления"
  - "внешняя компоновка, объявления функций"
  - "определения функций, объявления функций"
  - "прототипы функции, основы"
  - "внутренние объявления"
  - "локальные объявления"
ms.assetid: 43fd98eb-7441-4473-a5d9-fc88c75577f7
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Объявления и определения функций
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Прототипы функций устанавливают имя функции, тип возвращаемого ею значения, а также тип и число ее формальных параметров.  Определение функции содержит тело функции.  
  
## Примечания  
 Объявления функции и переменных могут находиться внутри или вне определения функции.  Считается, что любое объявление, сделанное внутри определения функции, находится на "внутреннем", или "локальном", уровне, а  объявление, расположенное вне всех определений функций, находится на внешнем, глобальном уровне или на уровне области видимости файла.  Определения переменных, подобно объявлениям, могут находиться на внутреннем \(в определении функции\) или внешнем \(вне всех определений функций\) уровне.  Определения функций всегда находятся на внешнем уровне.  Подробнее определения функций рассматриваются в разделе [Определения функций](../c-language/c-function-definitions.md).  Прототипы функций описаны в разделе [Прототипы функций](../c-language/function-prototypes.md).  
  
## См. также  
 [Файлы с исходным кодом и исходные программы](../c-language/source-files-and-source-programs.md)