---
title: "Ограничения компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf668ddfa1c2d7e62ca10963827056f9661b83f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-limits"></a>Ограничения компилятора
Стандарт языка C++ рекомендует ограничения для различных языковых конструкций. Ниже приведен список случаев, когда компилятор Visual C++ не реализует рекомендуемые ограничения. Первое число является ограничением, установленным в стандарте ISO C++ 11 (INCITS/ISO/IEC 14882-2011[2012], приложение B), а второе — ограничением, реализуемым Visual C++:  
  
-   Число уровней вложения составных операторов, структур управления итерациями и выделение управляющие структуры - стандарт языка C++: 256, компилятор Visual C++: зависит от сочетания вложенных операторов, но обычно от 100 до 110.  
  
-   Параметры в одном определении макроса - стандарт языка C++: 256, компилятор Visual C++: 127.  
  
-   Аргументы в одном вызове макроса - стандарт языка C++: 256, компилятор Visual C++: 127.  
  
-   Символов в строку литерала или расширенных строкового литерала (после объединения) - стандарт C++: 65536, компилятор Visual C++: 65535 однобайтовых символов, включая `null` признак конца и 32767 двухбайтовых символов, включая `null` признака конца.  
  
-   Уровней вложенных классов, структуры или объединения определениях в одном `struct-declaration-list` -стандарт C++: 256, компилятор Visual C++: 16.  
  
-   Инициализаторы членов в определении конструктора - стандарт языка C++: 6144, компилятор Visual C++: минимум 6144.  
  
-   Один идентификатор - стандарту C++ квалификаций области: 256, компилятор Visual C++: 127.  
  
-   Вложенные `extern` спецификации - стандарт языка C++: 1024, компилятор Visual C++: 9 (не считая неявную `extern` спецификации в глобальной области или 10 число неявный `extern` спецификации в глобальной области...  
  
-   Аргументы шаблона в объявлении шаблона - стандарт языка C++: 1024, компилятор Visual C++: 2046.  
  
## <a name="see-also"></a>См. также  
 [Нестандартное поведение](../cpp/nonstandard-behavior.md)