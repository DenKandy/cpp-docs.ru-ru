---
title: "/Zo (улучшение оптимизированного процесса отладки) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "-Zo"
  - "/Zo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zo — параметр компилятора [C++]"
  - "Zo — параметр компилятора [C++]"
  - "-Zo — параметр компилятора [C++]"
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# /Zo (улучшение оптимизированного процесса отладки)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Создает расширенные сведения об отладке для оптимизированного кода в неотладочных сборках.  
  
## Синтаксис  
  
```cpp  
/Zo[-]  
```  
  
## Заметки  
 Переключатель компилятора **\/Zo** создает расширенные сведения об отладке для оптимизированного кода.  При оптимизации могут использоваться регистраторы для локальных переменных, изменения в порядке кода, векторизация циклов и вызовы встроенных функций.  Такая оптимизация может скрывать связи между исходным кодом и кодом скомпилированного объекта.  Переключатель **\/Zo** указывает компилятору о необходимости создания дополнительных сведений об отладке для локальных переменных и встроенных функций.  Используйте его для просмотра переменных в окнах **Автоматические**, **Локальные** и **Просмотр** при выполнении пошаговых инструкций по оптимизированному коду в отладчике Visual Studio.  Он также позволяет выполнять трассировки стека для отображения встроенных функций в отладчике WinDBG.  Отладочные сборки с отключенной оптимизацией \([\/Od](../../build/reference/od-disable-debug.md)\) не требуют создания дополнительных сведений об отладке при указании **\/Zo**.  Используйте переключатель **\/Zo** для отладки конфигураций выпуска с включенной оптимизацией.  Дополнительные сведения о переключателях оптимизации см. в разделе [Параметры \/O \(оптимизация кода\)](../../build/reference/o-options-optimize-code.md).  Параметр **\/Zo** включен по умолчанию в Visual Studio 2015 при указании отладочной информации с **\/Zi** или **\/Z7**.  Укажите **\/Zo\-**, чтобы явно отключить этот параметр компилятора.  
  
 Переключатель **\/Zo** доступен в Visual Studio 2013 с обновлением 3 и заменяет не документированный ранее переключатель **\/d2Zi\+**.  
  
### Установка параметра компилятора \/Zo в Visual Studio  
  
1.  Откройте диалоговое окно **Страницы свойств** проекта.  Подробнее: [Открытие свойств страниц проекта](../../misc/how-to-open-project-property-pages.md).  
  
2.  Выберите папку **Свойства конфигурации**, а затем папку **C\/C\+\+**.  
  
3.  Выберите страницу свойств **Командная строка**.  
  
4.  Измените свойство **Дополнительные параметры**, включив параметр `/Zo`, а затем нажмите кнопку **ОК**.  
  
### Установка данного параметра компилятора программным способом  
  
-   См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## См. также  
 [Параметры \/O \(оптимизация кода\)](../../build/reference/o-options-optimize-code.md)   
 [\/Z7, \/Zi, \/ZI \(формат отладочной информации\)](../Topic/-Z7,%20-Zi,%20-ZI%20\(Debug%20Information%20Format\).md)   
 [Изменить и продолжить](../Topic/Edit%20and%20Continue.md)