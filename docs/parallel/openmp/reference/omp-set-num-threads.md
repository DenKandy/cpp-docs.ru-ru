---
title: "omp_set_num_threads | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_set_num_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_set_num_threads OpenMP function
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce4768c60480e20a48dd3b41d608216259c81530
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="ompsetnumthreads"></a>omp_set_num_threads
Задает число потоков в последующих параллельных регионах, если иное не переопределено [num_threads](../../../parallel/openmp/reference/num-threads.md) предложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void omp_set_num_threads(  
   int num_threads  
);  
```  
  
## <a name="remarks"></a>Примечания  
 где  
  
 `num_threads`  
 Число потоков в параллельной области.  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения см. в разделе [3.1.1 функция omp_set_num_threads](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).  
  
## <a name="example"></a>Пример  
 В разделе [omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md) пример использования `omp_set_num_threads`.  
  
## <a name="see-also"></a>См. также  
 [Функции](../../../parallel/openmp/reference/openmp-functions.md)