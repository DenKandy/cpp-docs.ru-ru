---
title: "Неустранимая ошибка ML A1011 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A1011
dev_langs:
- C++
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e3a614bc56c76b220eeeb73ce2cc7e90a9ca9b8e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="ml-fatal-error-a1011"></a>Неустранимая ошибка ML A1011
**Директива должна быть в блоке управления**  
  
 Код на языке ассемблера найти директиву высокого уровня, где не ожидалось только одно. Найдена одна из следующих директив:  
  
-   [. ELSE](../../assembler/masm/dot-else.md) без [. ЕСЛИ](../../assembler/masm/dot-if.md)  
  
-   [. ENDIF](../../assembler/masm/dot-endif.md) без [. ЕСЛИ](../../assembler/masm/dot-if.md)  
  
-   [. ENDW](../../assembler/masm/dot-endw.md) без [. WHILE](../../assembler/masm/dot-while.md)  
  
-   [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md) без [. ПОВТОРИТЕ ЭТИ ДЕЙСТВИЯ](../../assembler/masm/dot-repeat.md)  
  
-   [. ПРОДОЛЖИТЬ](../../assembler/masm/dot-continue.md) без [. ХОТЯ](../../assembler/masm/dot-while.md) или [. ПОВТОРИТЕ ЭТИ ДЕЙСТВИЯ](../../assembler/masm/dot-repeat.md)  
  
-   [. ПРЕРВАТЬ](../../assembler/masm/dot-break.md) без [. ХОТЯ](../../assembler/masm/dot-while.md) или [. ПОВТОРИТЕ ЭТИ ДЕЙСТВИЯ](../../assembler/masm/dot-repeat.md)  
  
-   [. ELSE](../../assembler/masm/dot-else.md) следующие `.ELSE`  
  
## <a name="see-also"></a>См. также  
 [Сообщения об ошибках ML](../../assembler/masm/ml-error-messages.md)