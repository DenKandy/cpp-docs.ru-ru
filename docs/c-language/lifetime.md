---
title: "Время жизни | Microsoft Docs"
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
  - "автоматический класс хранения"
  - "автоматический класс хранения, длительность"
  - "динамическое выделение памяти"
  - "функции [C++], время существования"
  - "глобальные переменные, время существования"
  - "время существования"
  - "локальные переменные, время существования"
  - "выделение памяти, dynamic"
  - "выделение памяти, динамическое выделение"
  - "спецификаторы классов хранения, продолжительность хранения"
  - "классы хранения, время существования"
  - "продолжительность хранения"
  - "переменные, автоматическая"
  - "переменные, время существования"
ms.assetid: ff0b42cb-3f0f-49a3-a94f-d1d825d8ddfe
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Время жизни
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

"Время жизни" представляет собой период во время выполнения программы, в течение которого существует переменная или функция.  Время жизни идентификатора определяется длительностью его хранения.  
  
 Идентификатор, объявленный со *спецификатором\-класса\-хранения* **static** имеет статическую длительность хранения.  Идентификаторы со статической длительностью хранения \(также называемые "глобальными"\) имеют выделенную память и определенное значение в течение всего времени выполнения программы.  Выделение памяти и инициализация хранящегося значения идентификатора производятся только один раз перед началом работы программы.  Идентификатор, объявленный с внешней или внутренней компоновкой, также имеет статическую длительность хранения \(см. раздел [Компоновка](../c-language/linkage.md)\).  
  
 Идентификатор, объявленный без спецификатора класса хранения **static**, имеет автоматическую длительность хранения, если он объявлен внутри функции.  Идентификатор с автоматической длительностью хранения \("локальный идентификатор"\) имеет выделенную память и определенное значение только внутри блока, в котором он определен или объявлен.  Автоматическому идентификатору выделяется новая память при каждом входе программы в соответствующий блок; при выходе программы из этого блока память \(и значение\) идентификатора освобождается.  Идентификаторы, объявленные в функции без компоновки, также имеют автоматическую длительность хранения.  
  
 Следующие правила определяют, имеет ли идентификатор глобальное \(статическое\) или локальное \(автоматическое\) время жизни:  
  
-   Все функции имеют статическое время жизни.  Поэтому они существуют в течение всего времени выполнения программы.  Идентификаторы, объявленные на внешнем уровне \(т. е., вне всех блоков в программе на одном уровне определений функций\), всегда имеют глобальное \(статическое\) время жизни.  
  
-   Если локальная переменная имеет инициализатор, эта переменная инициализирует при каждом создании \(если она не объявлена как **static**\).  Параметры функции также имеют локальное время жизни.  Для идентификатора можно определить глобальное время существования в пределах блока, включив в его объявление спецификатор класса хранения **static**.  Если переменная объявлена как **static**, она сохраняет свое значение от одного входа в блок до следующего.  
  
 Хотя идентификатор с глобальным временем жизни существует в течение всего времени выполнения исходной программы \(например, внешне объявленная переменная или локальная переменная, объявленная с ключевым словом **static**\), он может быть видимым не во всех частях программы.  Сведения о видимости см. в разделе [Область действия и видимость](../c-language/scope-and-visibility.md); в разделе [Классы хранения](../c-language/c-storage-classes.md) рассматривается нетерминальный *спецификатор\-класса\-хранения*.  
  
 Память может выделяться по мере необходимости \(динамически\), если создается с помощью специальных библиотечных процедур, таких как `malloc`.  Поскольку динамическое выделение памяти использует библиотечные процедуры, оно не считается составной частью языка.  См. описание функции [malloc](../c-runtime-library/reference/malloc.md) в *Справочнике по библиотеке времени выполнения*.  
  
## См. также  
 [Время жизни, область, видимость и компоновка](../Topic/Lifetime,%20Scope,%20Visibility,%20and%20Linkage.md)