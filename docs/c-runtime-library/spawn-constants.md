---
title: "Константы spawn | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _P_NOWAIT
- _P_OVERLAY
- _P_WAIT
- _P_DETACH
- _P_NOWAITO
dev_langs:
- C++
helpviewer_keywords:
- _P_OVERLAY constant
- P_DETACH constant
- P_OVERLAY constant
- P_NOWAIT constant
- _P_DETACH constant
- _P_NOWAIT constant
- _P_NOWAITO constant
- P_NOWAITO constant
- spawn constants
- P_WAIT constant
- _P_WAIT constant
ms.assetid: e0533e88-d362-46fc-b53c-5f193226d879
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 891080cb7740285aba2ac7d9f2542b5604c210bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="spawn-constants"></a>Константы spawn
## <a name="syntax"></a>Синтаксис  
  
```  
#include <process.h>  
```  
  
## <a name="remarks"></a>Примечания  
 Аргумент `mode` определяет действие, предпринимаемое процессом перед операцией инициализации и в течение нее. Для `mode` возможны следующие значения:  
  
|Константа|Значение|  
|--------------|-------------|  
|`_P_OVERLAY`|Перекрывает вызывающий процесс новым процессом, уничтожая вызывающий процесс (тот же эффект, что и у вызовов функции `_exec`).|  
|`_P_WAIT`|Приостанавливает вызывающий поток до тех пор, пока не будет завершено выполнение нового процесса (синхронная функция `_spawn`).|  
|`_P_NOWAIT`, `_P_NOWAITO`|Продолжает выполнять вызывающий процесс параллельно с новым процессом (асинхронная функция `_spawn`).|  
|`_P_DETACH`|Продолжает выполнять вызывающий процесс; новый процесс выполняется в фоновом режиме без доступа к консоли или клавиатуре. Вызовы функции `_cwait` для нового процесса будут завершаться с ошибкой. Это асинхронная функция `_spawn`.|  
  
## <a name="see-also"></a>См. также  
 [Функции _spawn, _wspawn](../c-runtime-library/spawn-wspawn-functions.md)   
 [Глобальные константы](../c-runtime-library/global-constants.md)