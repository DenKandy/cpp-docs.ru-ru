---
title: "umask | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "umask"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "umask"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "umask - функция"
ms.assetid: d2f697fc-08d5-4b70-9dd5-df3f5bb8b754
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# umask
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Не рекомендуется использовать эту функцию POSIX.  Вместо неё используйте соответствующую стандарту ISO C\+\+ [\_umask](../../c-runtime-library/reference/umask.md) или [\_umask\_s](../Topic/_umask_s.md) с улучшенной безопасностью.