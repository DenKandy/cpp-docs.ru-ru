---
title: "_tell, _telli64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_telli64"
  - "_tell"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "tell"
  - "telli64"
  - "_telli64"
  - "_tell"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tell - функция"
  - "_telli64 - функция"
  - "указатели файлов [C++]"
  - "указатели файлов [C++], получение"
  - "tell - функция"
  - "telli64 - функция"
ms.assetid: 1500e8f9-8fec-4253-9eec-ec66125dfc9b
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _tell, _telli64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Получает позицию указателя файла.  
  
## Синтаксис  
  
```  
long _tell(  
   int handle  
);  
__int64 _telli64(  
   int handle   
);  
```  
  
#### Параметры  
 `handle`  
 Дескриптор файла, ссылающийся на открытый файл.  
  
## Возвращаемое значение  
 Текущая позиция указателя файла.  Для устройств, которые не поддерживают поиск, возвращаемое значение не определено.  
  
 Возвращаемое значение –1L указывает на ошибку.  Если параметр `handle` является недопустимым дескриптором файла, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md).  Если продолжение выполнения разрешено, эти функции устанавливают для `errno` значение `EBADF` и возвращают \-1L.  
  
 См. раздел [\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr](../Topic/errno,%20_doserrno,%20_sys_errlist,%20and%20_sys_nerr.md) для дополнительных сведений по этим и другим кодам возврата.  
  
## Заметки  
 Функция `_tell` получает текущее положение указателя файла \(при его наличии\), связанного с аргументом `handle`.  Позиция представлена в виде количества байт от начала файла.  Для функции `_telli64` это значение выражено в виде 64\-разрядного целого числа.  
  
## Требования  
  
|Подпрограмма|Обязательный заголовок|  
|------------------|----------------------------|  
|`_tell`, `_telli64`|\<io.h\>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md) во введении.  
  
## Пример  
  
```  
// crt_tell.c  
// This program uses _tell to tell the  
// file pointer position after a file read.  
//  
  
#include <io.h>  
#include <stdio.h>  
#include <fcntl.h>  
#include <share.h>  
#include <string.h>  
  
int main( void )  
{  
   int  fh;  
   char buffer[500];  
  
   if ( _sopen_s( &fh, "crt_tell.txt", _O_RDONLY, _SH_DENYNO, 0) )  
   {  
      char buff[50];  
      _strerror_s( buff, sizeof(buff), NULL );  
      printf( buff );  
      exit( -1 );  
   }  
  
   if( _read( fh, buffer, 500 ) > 0 )  
      printf( "Current file position is: %d\n", _tell( fh ) );  
   _close( fh );  
}  
```  
  
## Входные данные: crt\_tell.txt  
  
```  
Line one.  
Line two.  
```  
  
### Output  
  
```  
Current file position is: 20  
```  
  
## См. также  
 [Низкоуровневый ввод\-вывод](../../c-runtime-library/low-level-i-o.md)   
 [ftell, \_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)   
 [\_lseek, \_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)