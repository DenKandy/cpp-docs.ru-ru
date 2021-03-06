---
title: "Встраиваемые функции | Документация Майкрософт"
ms.custom: 
ms.date: 10/16/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- fast code
- inline functions, __inline keyword
- functions [C++], inline functions
ms.assetid: 00f4b2ff-8ad0-4165-9f4c-2ef157d03f31
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8b5adadc990bed67abe739a4d73b2973b26ca207
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="inline-functions"></a>Встраиваемые функции

**Блок, относящийся только к системам Microsoft**

Ключевое слово `__inline` указывает компилятору заменить код в определении функции для каждого экземпляра вызова функции. Однако подстановка выполняется только по решению компилятора. Например, компилятор не подставляет функцию, если ее адрес был получен или если она слишком велика для подстановки.

Для того чтобы функция считалась кандидатом для подстановки, для нее должно использоваться определение функции в новом стиле.

Используйте следующую форму для определения встраиваемой функции:

> **__inline** *type*<sub>opt</sub> *function-definition*

С помощью встраиваемых функций можно создавать более быстрый код, который иногда может быть меньше, чем при использовании соответствующего вызова функции. Это вызвано следующими причинами:

- Они сокращают время, необходимое для выполнения вызовов функций.

- Подставляемые функции небольшого размера, например длиной 3 строки или менее, создают меньше кода, чем соответствующий вызов функции, потому что компилятор не генерирует код для обработки аргументов и возвращаемого значения.

- Для функций, которые создаются как подставляемые, выполняется оптимизация кода, которая недоступна для обычных функций, поскольку компилятор не выполняет межпроцедурные оптимизации.

Функции, в которых используется ключевое слово `__inline`, не следует путать со встраиваемым кодом на языке ассемблера. Дополнительные сведения см. в статье о [встроенном ассемблере](../c-language/inline-assembler-c.md).

**Завершение блока, относящегося только к системам Майкрософт**  

## <a name="see-also"></a>См. также

[inline, __inline, \__forceinline](../cpp/inline-functions-cpp.md)

