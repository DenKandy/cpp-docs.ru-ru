---
title: "Типы компоновки | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "внешняя компоновка, типы компоновки"
  - "внутренняя компоновка, типы компоновки"
  - "компоновка [C++], нет"
  - "компоновка [C++], типы"
  - "без компоновки"
  - "типы [C++], компоновка"
ms.assetid: 41326c7f-4602-4bad-a648-697604858ba0
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Типы компоновки
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Способ совместного использования имен объектов и функций записями преобразования называется компоновкой.  Эти имена могут иметь указанные ниже типы компоновки.  
  
-   Внутренняя компоновка, при которой имена относятся только к программным элементам внутри их собственных записей преобразования; совместно с другими записями преобразования они не используются.  
  
     То же имя в другой записи преобразования может относиться к другому объекту или классу.  Имена с внутренней компоновкой иногда называются локальными для своих записей преобразования.  
  
     Ниже приведен пример объявления имени с внутренней компоновкой.  
  
    ```  
    static int i;   // The static keyword ensures internal linkage.  
    ```  
  
-   Внешняя компоновка, при которой имена могут относиться к программным элементам в любой записи преобразования в программе: элемент программы совместно используется записями преобразования.  
  
     То же имя в другой записи преобразования относится к тому же объекту или классу.  Имена с внешней компоновкой иногда называются глобальными.  
  
     Ниже приведен пример объявления имени с внешней компоновкой.  
  
    ```  
    extern int i;  
    ```  
  
-   Нет компоновки. В этом случае имена относятся к уникальным сущностям.  То же имя в другой области не может относиться к тому же объекту.  Пример — перечисление.  \(Обратите внимание, что передать указатель на объект можно без компоновки.  При этом объект становится доступным в других записях преобразования.\)  
  
## См. также  
 [Программа и компоновка](../cpp/program-and-linkage-cpp.md)