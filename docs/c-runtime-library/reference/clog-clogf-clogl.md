---
title: "clog, clogf, clogl | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- clog
- clogf
- clogl
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clog
- clogf
- clogl
- complex/clog
- complex/clogf
- complex/clogl
dev_langs:
- C++
helpviewer_keywords:
- clog function
- clogf function
- clogl function
ms.assetid: 870b9b0b-6618-46f3-bfcf-da595cbd5e18
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 045eaee50f988e5712fd23845bd91db68c75ba65
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="clog-clogf-clogl"></a>clog, clogf, clogl
Извлекает натуральный логарифм комплексного числа, ветви которого заканчиваются в отрицательной части реальной оси.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
_Dcomplex clog(   
   _Dcomplex z   
);  
_Fcomplex clog(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex clog(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex clogf(   
   _Fcomplex z   
);  
_Lcomplex clogl(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `z`  
 Основание логарифма.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Натуральный логарифм числа `z`. Результат unbounded вдоль оси реальные и в интервале [-iπ, + iπ] мнимой оси.  
  
 Возможны следующие возвращаемые значения:  
  
|параметр z|Возвращаемое значение|  
|-----------------|------------------|  
|Положительное число|Десятичный логарифм z|  
|Нуль|- ∞|  
|Отрицательное число|NaN|  
|NaN|NaN|  
|+ ∞|+ ∞|  
  
## <a name="remarks"></a>Примечания  
 Поскольку C++ допускает перегрузку, можно вызывать перегрузки `clog`, которые принимают и возвращают значения `_Fcomplex` и `_Lcomplex`. В программе на языке C `clog` всегда принимает и возвращает значение `_Dcomplex` .  
  
## <a name="requirements"></a>Требования  
  
|Подпрограмма|Заголовок C|Заголовок C++|  
|-------------|--------------|------------------|  
|`clog`,               `clogf`, `clogl`|\<complex.h>|\<ccomplex>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md) во введении.  
  
## <a name="see-also"></a>См. также  
 [Алфавитный указатель функций](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cexp, cexpf, cexpl](../../c-runtime-library/reference/cexp-cexpf-cexpl.md)   
 [cpow, cpowf, cpowl](../../c-runtime-library/reference/cpow-cpowf-cpowl.md)   
 [clog10, clog10f, clog10l](../../c-runtime-library/reference/clog10-clog10f-clog10l.md)