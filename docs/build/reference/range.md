---
title: "— ДИАПАЗОН | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /RANGE
dev_langs:
- C++
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1ccca814a388a458513773247f79cecf87fcdeae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="range"></a>Параметр /RANGE
Изменяет вывод свойства dumpbin при совместном использовании с другими параметрами dumpbin, например/RAWDATA или/DISASM.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
/RANGE:vaMin[,vaMax]  
```  
  
## <a name="flags"></a>Флаги  
 **vaMin**  
 Виртуальный адрес, с которого начинается операция dumpbin.  
  
 **vaMax** (необязательно)  
 Виртуальный адрес, по которому операция dumpbin для завершения. Если не указан, программа dumpbin переместится в конец файла.  
  
## <a name="remarks"></a>Примечания  
 Чтобы просмотреть виртуальные адреса образа, используйте файл отображения образа (RVA + базовый адрес), **/DISASM** или **/Headers** параметр программы dumpbin, или Дизассемблированный код в отладчике Visual Studio.  
  
## <a name="example"></a>Пример  
 В этом примере **/диапазон** используется для изменения способа отображения **/DISASM** параметр. В этом примере начальное значение выражается как десятичное число, и конечное значение указывается в виде шестнадцатеричного числа.  
  
```  
dumpbin /disasm /range:4219334,0x004061CD t.exe  
```  
  
## <a name="see-also"></a>См. также  
 [Параметры DUMPBIN](../../build/reference/dumpbin-options.md)