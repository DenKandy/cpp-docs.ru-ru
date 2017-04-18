---
title: "Параметр /Ob (расширение встроенных функций) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion"
  - "VC.Project.VCCLCompilerTool.InlineFunctionExpansion"
  - "/ob"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Ob - параметр компилятора [C++]"
  - "/Ob0 - параметр компилятора [C++]"
  - "/Ob1 - параметр компилятора [C++]"
  - "/Ob2 - параметр компилятора [C++]"
  - "любой вид - параметр компилятора [C++]"
  - "отключить - параметр компилятора [C++]"
  - "встроенное выражение, параметр компилятора"
  - "встроенные функции, расширение функции - параметр компилятора [C++]"
  - "Ob - параметр компилятора [C++]"
  - "-Ob - параметр компилятора [C++]"
  - "Ob0 - параметр компилятора [C++]"
  - "-Ob0 - параметр компилятора [C++]"
  - "Ob1 - параметр компилятора C++"
  - "-Ob1 - параметр компилятора C++"
  - "Ob2 - параметр компилятора [C++]"
  - "-Ob2 - параметр компилятора [C++]"
  - "only __inline - параметр компилятора [C++]"
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# Параметр /Ob (расширение встроенных функций)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Управляет подстановкой функций.  
  
## Синтаксис  
  
```  
/Ob{0|1|2}  
```  
  
## Аргументы  
 **0**  
 Отключает подставляемые функции.  По умолчанию подстановка всех функций происходит по решению компилятора и часто обозначается как *автоподстановка*.  
  
 **1**  
 Разрешает подстановку только тех функций, которые помечены как [inline](../../misc/inline-inline-forceinline.md), [\_\_inline](../../misc/inline-inline-forceinline.md) или [\_\_forceinline](../../misc/inline-inline-forceinline.md), а также функций\-членов C\+\+, определенных в объявлении класса.  
  
 **2**  
 Значение по умолчанию.  Разрешает подстановку всех функций, помеченных как `inline`, `__inline` или `__forceinline`, а также любых функций, выбранных компилятором.  
  
 **\/Ob2** вступает в силу, если используется [\/O1, \/O2 \(минимизировать размер, максимизировать скорость\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) или [\/Ox \(полная оптимизация\)](../../build/reference/ox-full-optimization.md).  
  
 Для этого параметра требуется включить оптимизацию с помощью **\/O1**, **\/O2**, **\/Ox** или **\/Og**.  
  
## Заметки  
 Параметры и ключевые слова подстановки компилятор обрабатывает как рекомендации.  Подстановка какой\-либо функции не гарантируется.  Подстановку можно отключить, но вы не сможете выполнить принудительную подстановку определенной функции компилятором, даже если используете ключевое слово `__forceinline`.  
  
 Вы можете использовать директиву `#pragma` [auto\_inline](../../preprocessor/auto-inline.md), чтобы исключить из рассмотрения функции\-кандидаты на подстановку.  Также см. директиву `#pragma` [intrinsic](../../preprocessor/intrinsic.md).  
  
> [!NOTE]
>  Сведения, полученные из теста профилирования, запускают переопределения оптимизаций, которые в противном случае вступят в силу, если указать **\/Ob**, **\/Os** или **\/Ot**.  Дополнительные сведения см. в разделе [Профильная оптимизация](../../build/reference/profile-guided-optimizations.md).  
  
### Установка данного параметра компилятора в среде разработки Visual Studio  
  
1.  Откройте диалоговое окно **Страницы свойств** проекта.  Дополнительные сведения см. в разделе [Работа со свойствами проектов](../../ide/working-with-project-properties.md).  
  
2.  Откройте меню **Свойства конфигурации**, **C\/C\+\+** и выберите **Оптимизация**.  
  
3.  Измените свойство **Подстановка встраиваемой функции**.  
  
### Установка данного параметра компилятора программным способом  
  
-   См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.  
  
## См. также  
 [Параметры \/O \(оптимизация кода\)](../../build/reference/o-options-optimize-code.md)   
 [Параметры компилятора](../../build/reference/compiler-options.md)   
 [Настройка параметров компилятора](../Topic/Setting%20Compiler%20Options.md)