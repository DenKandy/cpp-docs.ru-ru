---
title: "Объявления перечислений C | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "#define - директива, альтернатива для"
  - "объявления, перечисления"
  - "объявление перечислений"
  - "define - директива (#define), альтернатива для"
  - "перечислители, объявление"
  - "именованные константы, объявления перечислений"
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Объявления перечислений C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Перечисление состоит из набора именованных целочисленных констант.  Объявление типа перечисления предоставляет имя тега перечисления \(необязательно\) и определяет набор именованных целочисленных идентификаторов \(называемых "набор перечисления", "константы перечислителя", "перечислители" или "члены"\).  Переменная с типом перечисления хранит одно из значений набора перечисления, определенных этим типом.  
  
 Переменные типа `enum` можно использовать в выражениях индексации и в качестве операндов всех арифметических операторов и операторов отношения.  Перечисления являются альтернативой директиве препроцессора `#define` с тем преимуществом, что можно создать значения, подчиняющиеся обычным правилам области.  
  
 В ANSI C выражения, определяющие значение константы перечислителя, всегда имеют тип `int`. Таким образом, хранилище, связанное с переменной перечисления, является хранилищем, необходимым для одного значения `int`.  Константу перечисления или значение перечисляемого типа можно использовать как целочисленное выражение в любом месте, допустимом в языке C.  
  
## Синтаксис  
 *спецификатор\-перечисления*:  
 **перечисление**  *идентификатор*  необ **{** *список\-перечислителей* **}**  
  
 **enum**  *идентификатор*  
  
 Необязательный параметр *идентификатор* именует тип перечисления, определенный параметром *список\-перечислителей*.  Этот идентификатор часто называется тегом перечисления, определенным списком.  Описатель типа  
  
```  
  
enum identifier { enumerator-list }  
```  
  
 объявляет *идентификатор*, чтобы тег перечисления, определенный параметром *список\-перечислителей*, был нетерминальным.  *список\-перечислителей* определяет содержимое перечислителя. Подробное описание параметра *список\-перечислителей* представлено ниже.  
  
 Если объявление тега является видимым, последующие объявления, в которых используется тег, но опускается *список\-перечислителей*, определяют ранее объявленный перечисляемый тип.  Тег должен ссылаться на определенный тип перечисления, и этот тип перечисления должен находиться в текущей области.  Поскольку тип перечисления определен в другом месте, *список\-перечислителей* не отображается в этом объявлении.  В объявлениях типов, производных от перечислений, и объявлениях `typedef` для типов перечислений тег перечисления может использоваться до определения типа перечисления.  
  
## Синтаксис  
 *список\-перечислителей*:  
 *перечислитель*  
  
 *список\-перечислителей* **,**  `enumerator`  
  
 `enumerator`:  
 *константа\-перечисления*  
  
 *константа\-перечисления*  **\=**  *константное\-выражение*  
  
 *константа\-перечисления*:  
 *identifier*  
  
 Каждый параметр *константа\-перечисления* в области *список\-перечислителей* именует значение набора перечисления.  По умолчанию первый параметр *константа\-перечисления* связан со значением 0.  Следующий параметр *константа\-перечисления* в списке связан со значением \(*константа\-перечисления* \+ 1\), если его явно не связать с другим значением.  Имя параметра *константа\-перечисления* эквивалентно его значению.  
  
 Выражение *константа\-перечисления \= константное\-выражение* можно использовать для переопределения последовательности значений по умолчанию.  Таким образом, если *константа\-перечисления \= константное\-выражение* отображается в области *список\-перечислителей*, параметр *константа\-перечисления* связывается со значением, предоставленным выражением *константное выражение*.  Выражение *константное\-выражение* должно иметь тип `int` и может быть отрицательным.  
  
 К членам набора перечисления применяются следующие правила.  
  
-   Набор перечисления может содержать повторяющиеся постоянные значения.  Например, значение 0 можно связать с двумя разными идентификаторами, такими как `null` и `zero`, в одном и том же наборе.  
  
-   Идентификаторы в списке перечисления должны отличаться от других идентификаторов в той же области с той же видимостью, включая обычные имена переменных и идентификаторы в других списках перечисления.  
  
-   К тегам перечисления применяются обычные правила области.  Они должны отличаться от всех тегов перечислений, структур или объединений с такой же видимостью.  
  
## Примеры  
 В следующих примерах показаны объявления перечисления.  
  
```  
enum DAY            /* Defines an enumeration type    */  
{  
    saturday,       /* Names day and declares a       */  
    sunday = 0,     /* variable named workday with    */   
    monday,         /* that type                      */  
    tuesday,  
    wednesday,      /* wednesday is associated with 3 */  
    thursday,  
    friday  
} workday;  
```  
  
 Значение 0 связано с `saturday` по умолчанию.  Для идентификатора `sunday` явно задано значение 0.  Оставшимся идентификаторам по умолчанию присваиваются значения от 1 до 5.  
  
 В этом примере значение из набора `DAY` присваивается переменной `today`.  
  
```  
enum DAY today = wednesday;  
```  
  
 Обратите внимание, что имя константы перечисления используется для присвоения значения.  Поскольку тип перечисления `DAY` был объявлен ранее, необходим только тег перечисления `DAY`.  
  
 Чтобы явно присвоить целочисленное значение переменной перечисляемого типа данных, используйте следующее приведение типа.  
  
```  
workday = ( enum DAY ) ( day_value - 1 );  
```  
  
 Это приведение рекомендовано к использованию в С, но не является обязательным.  
  
```  
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */  
{  
    false,     /* false = 0, true = 1 */  
    true   
};   
  
enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */  
```  
  
 Это объявление также можно указать как  
  
```  
enum BOOLEAN { false, true } end_flag, match_flag;\  
```  
  
 или как  
  
```  
enum BOOLEAN { false, true } end_flag;  
enum BOOLEAN match_flag;  
```  
  
 Пример, в котором используются эти переменные, может выглядеть следующим образом.  
  
```  
if ( match_flag == false )  
    {  
     .  
     .   /* statement */   
     .  
    }  
    end_flag = true;  
```  
  
 Также можно объявить неименованные типы данных перечислителя.  Имя типа данных опускается, но можно объявлять переменные.  Переменная `response` является переменной определенного типа.  
  
```  
enum { yes, no } response;  
```  
  
## См. также  
 [Перечисления](../cpp/enumerations-cpp.md)