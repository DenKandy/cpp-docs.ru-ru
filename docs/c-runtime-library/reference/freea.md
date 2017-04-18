---
title: "_freea | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _freea
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
apitype: DLLExport
f1_keywords:
- freea
- _freea
dev_langs:
- C++
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: b8310730b9b1c700402cc8d6d35eea3abc893dfe
ms.lasthandoff: 02/24/2017

---
# <a name="freea"></a>_freea
Освобождает блок памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void _freea(   
   void *memblock   
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `memblock`  
 Ранее выделенный блок памяти, который требуется освободить.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Отсутствует.  
  
## <a name="remarks"></a>Примечания  
 Функция `_freea` освобождает блок памяти (`memblock`), который был выделен ранее вызовом функции [_malloca](../../c-runtime-library/reference/malloca.md). Функция `_freea` проверяет, была ли память выделена в стеке или в куче. Если она была выделена в стеке, функция `_freea` не выполняет никаких действий. Если память выделена в куче, число освобожденных байтов эквивалентно количеству байтов, запрошенному при выделении блока. Если `memblock` имеет значение `NULL`, указатель не обрабатывается и функция `_freea` немедленно возвращает управление. Попытка освободить недопустимый указатель (указатель на блок памяти, который не был выделен функцией `_malloca`) может повлиять на последующие запросы выделения памяти и вызвать ошибки.  
  
 Если память выделена в куче, функция _`freea` выполняет внутренний вызов функции `free`. Информация о том, выделена ли память в куче или в стеке, определяется меткой, которая устанавливается в памяти по адресу, непосредственно предшествующему выделенному блоку памяти.  
  
 В случае возникновения ошибки при освобождении памяти для `errno` задаются сведения о характере сбоя, полученные от операционной системы. Дополнительные сведения см. в разделе [errno, _doserrno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 После освобождения блока памяти функция [_heapmin](../../c-runtime-library/reference/heapmin.md) минимизирует объем свободной памяти в куче путем объединения неиспользуемых областей и возврата их операционной системе. Освобожденная память, которая не возвращена операционной системе, возвращается в пул свободной памяти и снова доступна для выделения.  
  
 Вызов `_freea` должен сопровождать все вызовы `_malloca`. Повторный вызов функции `_freea` для того же блока памяти приведет к ошибке. Если приложение связано с отладочной версией библиотеки времени выполнения C, в особенности в том случае, если функции [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md) включены посредством определения `_CRTDBG_MAP_ALLOC`, найти пропущенные или повторные вызовы функции `_freea` будет проще. Дополнительные сведения об управлении кучей в процессе отладки см. в разделе [Куча отладки CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
 Функция `_freea` помечена как `__declspec(noalias)`; это означает, что функция гарантировано не изменяет глобальные переменные. Дополнительные сведения см. в разделе [noalias](../../cpp/noalias.md).  
  
## <a name="requirements"></a>Требования  
  
|Функция|Обязательный заголовок|  
|--------------|---------------------|  
|`_freea`|\<stdlib.h> и \<malloc.h>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md) во введении.  
  
## <a name="example"></a>Пример  
 См. пример для функции [_malloca](../../c-runtime-library/reference/malloca.md).  
  
## <a name="net-framework-equivalent"></a>Эквивалент .NET Framework  
 Неприменимо. Для вызова стандартной функции C используйте `PInvoke`. Дополнительные сведения см. в разделе [Примеры вызова неуправляемого кода](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>См. также  
 [Выделение памяти](../../c-runtime-library/memory-allocation.md)   
 [_malloca](../../c-runtime-library/reference/malloca.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_free_dbg](../../c-runtime-library/reference/free-dbg.md)   
 [_heapmin](../../c-runtime-library/reference/heapmin.md)