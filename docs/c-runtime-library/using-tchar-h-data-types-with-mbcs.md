---
title: "Использование типов данных TCHAR.H с _MBCS | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_mbcs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_MBCS - тип данных"
  - "MBCS - тип данных"
  - "типы данных TCHAR.H"
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Использование типов данных TCHAR.H с _MBCS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Блок, относящийся только к системам Майкрософт**  
  
 Как показано в таблице универсальных текстовых сопоставлений \(см. раздел [Универсальные текстовые сопоставления](../c-runtime-library/generic-text-mappings.md)\), когда константа манифеста `_MBCS` определена, заданные универсальные текстовые процедуры сопоставляются с одним из данных типов процедур:  
  
-   SBCS\-версии процедур, которые обрабатывают многобайтовые байты, знаки и строки соответствующим образом.  В этом случае ожидается, что строковые аргументы будут иметь тип `char*`.  Например, функция `_tprintf` сопоставляется с функцией `printf`; строковые аргументы `printf` имеют тип `char*`.  При использовании универсального строкового типа данных `_TCHAR` типы формальных и фактических параметров функции `printf` совпадают, потому что `_TCHAR*` сопоставляется с `char*`.  
  
-   MBCS\-версии процедур.  В этом случае ожидается, что строковые аргументы будут иметь тип `unsigned char*`.  Например, функция `_tcsrev`  сопоставляется с функцией `_mbsrev`, которая ожидает и возвращает строку типа `unsigned char*`.  Еще раз, при использовании универсального строкового типа данных `_TCHAR`  существует вероятность конфликта типов, потому что `_TCHAR`  сопоставляется с типом `char`.  
  
 Есть три способа предотвратить конфликт типов \(при конфликте типов компилятор C выдает предупреждение, а компилятор C\+\+ — сообщение об ошибке\):  
  
-   Использовать поведение по умолчанию.  Файл TCHAR.H содержит прототипы универсальных текстовых процедур, реализованных в библиотеках времени выполнения, как показано в следующем примере.  
  
    ```  
    char *_tcsrev(char *);  
    ```  
  
     В этом случае прототип функции `_tcsrev` сопоставляется с функцией `_mbsrev` через преобразователь в LIBC.LIB.  Тип входного параметра и результата функции `_mbsrev` изменяется с `_TCHAR *` \(такой, как `char *`\) на `unsigned char *`.  Данный метод гарантирует совпадение типов при использовании `_TCHAR`, но он является сравнительно медленным из\-за дополнительного вызова функции.  
  
-   Использовать подстановку функций путем включения в код следующей инструкции препроцессора.  
  
    ```  
    #define _USE_INLINING  
    ```  
  
     При этом подходе вызывается встроенный преобразователь функции, реализованный в файле TCHAR.H, который непосредственно сопоставляет универсальную текстовую процедуру с соответствующей MBCS\-процедурой.  Следующий фрагмент кода из TCHAR.H иллюстрирует вышесказанное.  
  
    ```  
    __inline char *_tcsrev(char *_s1)  
    {return (char *)_mbsrev((unsigned char *)_s1);}  
    ```  
  
     По возможности рекомендуется использовать именно подставляемые функции, потому что они гарантируют соответствие типов и не замедляют код.  
  
-   Использовать "прямое сопоставление" путем включения в код следующей инструкции препроцессора.  
  
    ```  
    #define _MB_MAP_DIRECT  
    ```  
  
     Данный подход является быстрой альтернативой, если нет возможности использовать поведение по умолчанию или подставляемые функции.  При этом универсальная текстовая процедура сопоставляется через макрос непосредственно на MBCS\-версию процедуры, как в следующем фрагменте из TCHAR.H.  
  
    ```  
    #define _tcschr _mbschr  
    ```  
  
 При использовании этого подхода необходимо следить, чтобы для строковых входных параметров и выходного значения использовались соответствующие типы данных.  Можно воспользоваться явным приведением типов, чтобы гарантировать соответствие типов, либо универсальным строковым типом данных `_TXCHAR`.  Тип `_TXCHAR` сопоставляется с типом `char` в SBCS\-коде, но в MBCS\-коде он сопоставляется с типом `unsigned char`.  Дополнительные сведения об универсальных текстовых макросах см. в разделе [Универсальные текстовые сопоставления](../c-runtime-library/generic-text-mappings.md).  
  
 **Завершение блока, относящегося только к системам Майкрософт**  
  
## См. также  
 [Интернационализация](../c-runtime-library/internationalization.md)   
 [Процедуры среды выполнения по категориям](../c-runtime-library/run-time-routines-by-category.md)