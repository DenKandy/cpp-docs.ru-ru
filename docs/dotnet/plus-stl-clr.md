---
title: "plus (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::plus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "plus - функция [STL/CLR]"
ms.assetid: 7ec8228a-72c7-4e47-9e63-23525d4a5416
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# plus (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Описание класса шаблона функтором, при вызове возвращает первый и второй аргумент.  Он используется определяется объект функции с точки зрения его типа аргумента.  
  
## Синтаксис  
  
```  
template<typename Arg>  
    ref class plus  
    { // wrap operator()  
public:  
    typedef Arg first_argument_type;  
    typedef Arg second_argument_type;  
    typedef Arg result_type;  
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<  
        first_argument_type, second_argument_type, result_type>  
        delegate_type;  
  
    plus();  
    plus(plus<Arg>% right);  
  
    result_type operator()(first_argument_type left,  
        second_argument_type right);  
    operator delegate_type^();  
    };  
```  
  
#### Параметры  
 Аргумент  
 Тип аргументов и возвращаемого значения.  
  
## Функции\-члены  
  
|Определение типа|Описание|  
|----------------------|--------------|  
|delegate\_type|Тип универсального метод\-делегата.|  
|first\_argument\_type|Тип первого аргумента функтором.|  
|result\_type|Тип результата функтором.|  
|second\_argument\_type|Тип второго аргумента функтором.|  
  
|Член|Описание|  
|----------|--------------|  
|добавочный|Построение функтором.|  
  
|Оператор|Описание|  
|--------------|--------------|  
|operator\(\)|Вычисляет нужную функцию.|  
|delegate\_type^ оператора|Возвращает функтором делегату.|  
  
## Заметки  
 Описание класса шаблона функтором 2 — аргумента.  Он определяет оператор `operator()` члена, что, когда объект вызывается как функция возвращается первый и второй аргумент.  
  
 Можно также передать объект в качестве аргумента функции, тип которого `delegate_type^` и он будет преобразован соответствующим образом.  
  
## Пример  
  
```  
// cliext_plus.cpp   
// compile with: /clr   
#include <cliext/algorithm>   
#include <cliext/functional>   
#include <cliext/vector>   
  
typedef cliext::vector<int> Myvector;   
int main()   
    {   
    Myvector c1;   
    c1.push_back(4);   
    c1.push_back(3);   
    Myvector c2;   
    c2.push_back(2);   
    c2.push_back(1);   
    Myvector c3(2, 0);   
  
// display initial contents " 4 3" and " 2 1"   
    for each (int elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (int elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// transform and display   
    cliext::transform(c1.begin(), c1.begin() + 2,   
        c2.begin(), c3.begin(), cliext::plus<int>());   
    for each (int elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **4 3**  
 **2 1**  
 **6 4**   
## Требования  
 **Заголовок:**\<cliext\/functional\>  
  
 **Пространство имен:** cliext  
  
## См. также  
 [minus](../dotnet/minus-stl-clr.md)