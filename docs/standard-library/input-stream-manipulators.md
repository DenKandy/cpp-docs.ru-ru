---
title: "Манипуляторы входных потоков | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: e1c7e8f5e1075230f008e4cb5f9a6ac843c75502
ms.lasthandoff: 02/24/2017

---
# <a name="input-stream-manipulators"></a>Манипуляторы входных потоков
Многие манипуляторы, например, brokenlink--(../Topic/not%20found:3ddde610-70cc-4cfa-8a89-3e83d1d356a8.md#setprecision) определены для класса `ios` и, поэтому, применяются к потокам ввода. Однако некоторые манипуляторы фактически влияют на объекты потока ввода. Наиболее важными из них являются манипуляторы основания системы счисления `dec`, `oct` и `hex`, которые определяют базу преобразования, используемую с числами из входного потока.  
  
 При извлечении манипулятор `hex` позволяет обрабатывать различные форматы входных данных. Например, c C, 0xc, 0xC, 0Xc и 0XC интерпретируются как десятичное целое число 12. Любой символ, отличный от цифр от 0 до 9, букв от A до F, букв от a до f, x и X, завершает числовое преобразование. Таким образом, последовательность `"124n5"` преобразуется в число 124 с заданными битом [basic_ios::fail](../standard-library/basic-ios-class.md#basic_ios__fail).  
  
## <a name="see-also"></a>См. также  
 [Потоки ввода](../standard-library/input-streams.md)

