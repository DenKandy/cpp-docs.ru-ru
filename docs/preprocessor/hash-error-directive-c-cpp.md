---
title: "#Ошибка директивы (C/C++) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#error'
dev_langs:
- C++
helpviewer_keywords:
- '#error directive'
- preprocessor, directives
- error directive (#error directive)
ms.assetid: d550a802-ff19-4347-9597-688935d23b2b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e449da64b5221ccddee34dd850a987b28a2f39df
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="error-directive-cc"></a>Директива #error (C/C++)
Директива `#error` создает заданное пользователем сообщение об ошибке во время компиляции, а затем завершает компиляцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
#errortoken-string  
```  
  
## <a name="remarks"></a>Примечания  
 Эта директива выдает сообщение об ошибке включает *строке токена* параметра. Параметр `token-string` не подлежит расширению макроса. Эта директива наиболее полезна в ходе предварительной обработки и позволяет уведомлять разработчика о противоречиях в программе или о нарушении ограничений. В следующем примере демонстрируется обработка ошибки во время предварительной обработки.  
  
```  
#if !defined(__cplusplus)  
#error C++ compiler required.  
#endif  
```  
  
## <a name="see-also"></a>См. также  
 [Директивы препроцессора](../preprocessor/preprocessor-directives.md)