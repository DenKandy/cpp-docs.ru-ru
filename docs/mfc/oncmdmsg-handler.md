---
title: "Обработчик OnCmdMsg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OnCmdMsg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "маршрутизация команд, OnCmdMsg - обработчик"
  - "обработчики"
  - "обработчики, OnCmdMessage"
  - "сообщения, маршрутизация"
  - "OnCmdMessage - метод"
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Обработчик OnCmdMsg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Для выполнения команд маршрутизации каждый целевой объект команды функции\-члена `OnCmdMsg` следующего конечного команды в последовательности.  Использование `OnCmdMsg` конечных объектов команды задавать ли они могут обрабатывать команду и направить ее в другой конечный объект команды, если они не могут его обработки.  
  
 Каждый класс конечного команды может переопределить функцию\-член `OnCmdMsg`.  Переопределения позволяет каждому классу направить команды к определенной очередной задачей.  Фреймовое окно, например, всегда направляет команды в его текущего дочернему окну или ", как показано в таблице [Маршрут стандартной команды](../mfc/command-routing.md).  
  
 Реализация `CCmdTarget` по умолчанию `OnCmdMsg` используется схема сообщений класса команда\- целевого объекта для поиска функции обработчика для каждого сообщения команды получении — таким же образом, что стандартные сообщения проверяются на.  При обнаружении соответствия, она вызывает обработчик.  Поиск сообщений элементы схемы в [Как платформы .NET Framework найти сопоставления сообщений](../mfc/how-the-framework-searches-message-maps.md).  
  
## См. также  
 [Вызовы к обработчику со стороны платформы](../mfc/how-the-framework-calls-a-handler.md)