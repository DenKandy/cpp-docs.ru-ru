---
title: "putenv | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "putenv"
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
  - "api-ms-win-crt-environment-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "putenv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "putenv - функция"
ms.assetid: 1dc49ef3-6b12-484c-8e60-7048bcc999f1
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# putenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Не рекомендуется использовать эту функцию POSIX.  Вместо неё используйте ISO C\+\+ совместимую [\_putenv](../../c-runtime-library/reference/putenv-wputenv.md) или [\_putenv\_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md) с улучшенной безопасностью.  
  
> [!IMPORTANT]
>  Этот API невозможно использовать в приложениях, запускаемых в среде выполнения Windows.  Дополнительные сведения см. в статье [Функции CRT, которые не поддерживаются с ключом \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).