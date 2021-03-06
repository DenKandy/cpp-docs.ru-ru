---
title: "_swab | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _swab
- stdlib/_swab
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _swab
- stdlib/_swab
dev_langs:
- C++
helpviewer_keywords:
- _swab function
- swapping bytes
- swab function
- bytes, swapping
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 01f23047436b7ff8cee16b42cc6ae0d8c2a9fd78
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="swab"></a>_swab
Меняет местами байты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void _swab(  
   char *src,  
   char *dest,  
   int n   
);  
```  
  
## <a name="parameters"></a>Параметры  
 `src`  
 Данные, которые следует скопировать и поменять местами.  
  
 `dest`  
 Место хранения для переставленных местами данных.  
  
 `n`  
 Число байтов, которые следует скопировать и поменять местами.  
  
## <a name="return-value"></a>Возвращаемое значение
 Функция `swab` не возвращает значение. Функция задает для `errno` значение `EINVAL`, если указатель `src` или `dest` имеет значение NULL или параметр `n` меньше нуля, и вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md).  
  
 Дополнительные сведения об этих и других кодах возврата см. в разделе [_doserrno, errno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).
 
## <a name="remarks"></a>Примечания  
 Если `n` является четным числом, функция `_swab` копирует `n` байт из `src`, меняет местами все соседние пары байтов и сохраняет результат в `dest`. Если `n` является нечетным числом, `_swab` копирует и меняет местами первые `n-1` байт из `src`, последний байт не копируется. Функция `_swab` обычно используется для подготовки двоичных данных для передачи на компьютер, который использует другой порядок байтов.  
  
## <a name="requirements"></a>Требования  
|Подпрограмма|Обязательный заголовок|  
|-------------|---------------------|  
|`_swab`|C: \<stdlib.h> C++: \<cstdlib> или \<stdlib.h>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md) во введении.  
  
## <a name="example"></a>Пример  
```C 
// crt_swab.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";  
char to[] =   "...........................";  
  
int main()  
{  
    printf("Before: %s  %d bytes\n        %s\n\n", from, sizeof(from), to);  
    _swab(from, to, sizeof(from));  
    printf("After:  %s\n        %s\n\n", from, to);  
}  
```  
  
```Output  
Before: BADCFEHGJILKNMPORQTSVUXWZY  27 bytes  
        ...........................  
  
After:  BADCFEHGJILKNMPORQTSVUXWZY  
        ABCDEFGHIJKLMNOPQRSTUVWXYZ.  
```  
  
## <a name="see-also"></a>См. также  
 [Манипуляция буфером](../../c-runtime-library/buffer-manipulation.md)