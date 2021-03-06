---
title: "Операторы C | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ternary operators
- operators [C]
- symbols, operators
- binary operators
- associativity of operators
- binary data, binary expressions
ms.assetid: 13bc4c8e-2dc9-4b23-9f3a-25064e8777ed
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3d4acb0acec44d695bd4c03ffa102a0ac42971b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="c-operators"></a>Операторы в C
Операторы C являются подмножеством [ встроенных операторов C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md).  
  
 Существуют три типа операторов. Унарное выражение состоит либо из унарного оператора, который стоит перед операндом, либо из ключевого слова `sizeof`, за которым следует выражение. Выражением может быть либо имя переменной, либо выражение приведения типа. В последнем случае выражение должно быть заключено в круглые скобки. Бинарное выражение состоит из 2 операндов, соединенных бинарным оператором. Троичное выражение состоит из 3 операндов, соединенных оператором условного выражения.  
  
 В языке C имеются следующие унарные операторы:  
  
|Символ|name|  
|------------|----------|  
|**- ~ !**|Операторы отрицания и дополнения|  
|**\* &**|Операторы косвенного обращения и взятия адреса|  
|`sizeof`|Оператор определения размера|  
|**+**|Оператор унарного сложения|  
|**++ --**|Унарные операторы инкремента и декремента|  
  
 Бинарные операторы имеют левую ассоциативность, т. е. выполняются слева направо. В языке C имеются следующие бинарные операторы:  
  
|Символ|name|  
|------------|----------|  
|**\* / %**|Мультипликативные операторы|  
|**+ -**|Аддитивные операторы|  
|**<\< >>**|Операторы сдвига|  
|**\<   >   \<=   >=   ==   !=**|Операторы отношения|  
|**&   &#124; ^**|Побитовые операторы|  
|**&&   &#124;&#124;**|Логические операторы|  
|**,**|Оператор последовательного вычисления|  
  
 Базовый оператор (**:>**), поддерживающийся предыдущими версиями компилятора Microsoft C для 16-разрядных систем, описывается в [кратком обзоре синтаксиса языка C](../c-language/c-language-syntax-summary.md).  
  
 Оператор условного выражения имеет более низкий приоритет, чем бинарные выражения, и отличается от них тем, что имеет правую ассоциативность.  
  
 К выражениям с операторами также относятся выражения присваивания, в которых используются унарные или бинарные операторы присваивания. Унарные операторы присваивания — это операторы инкремента и декремента (`++` и **--** соответственно). Бинарные операторы присваивания — это оператор простого присваивания (**=**) и составные операторы присваивания. Все составные операторы присваивания состоят из другого бинарного оператора и оператора простого присваивания.  
  
## <a name="see-also"></a>См. также  
 [Выражения и присваивания](../c-language/expressions-and-assignments.md)