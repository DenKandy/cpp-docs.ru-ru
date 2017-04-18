---
title: "Структура equal_to | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::equal_to"
  - "equal_to"
  - "xfunctional/std::equal_to"
  - "std.equal_to"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "equal_to - функция"
  - "equal_to - структура"
ms.assetid: 8e4f2b50-b2db-48e3-b4cc-6cc03362c2a6
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# Структура equal_to
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Бинарный предикат, выполняет операцию равенства \(`operator==`\) на основе своих аргументов.  
  
## Синтаксис  
  
```  
template<class Type = void>  
   struct equal_to : public binary_function<Type, Type, bool>   
   {  
      bool operator()(  
         const Type& Left,   
         const Type& Right  
      ) const;  
   };  
  
// specialized transparent functor for operator==  
template<>  
   struct equal_to<void>  
   {  
      template<class Type1, class Type2>  
      auto operator()(Type1&& Left, Type2&& Right) const  
         -> decltype(std::forward<Type1>(Left)  
            == std::forward<Type2>(Right));  
   };  
  
```  
  
#### Параметры  
 `Type`, `Type1`, `Type2`  
 Любой тип, поддерживающий `operator==`, принимающую операнды определение или возвращаемого типа.  
  
 `Left`  
 Левый операнд операции равенства.  Неспециализированный шаблон принимает аргумент ссылки значения типа `Type`.  Представляет шаблон повышает препровождение аргументов ссылки rvalue возвращаемого значения и типа `Type1`.  
  
 `Right`  
 Правый операнд операции равенства.  Неспециализированный шаблон принимает аргумент ссылки значения типа `Type`.  Представляет шаблон повышает препровождение аргументов ссылки rvalue возвращаемого значения и типа `Type2`.  
  
## Возвращаемое значение  
 Результат `Left``==``Right`.  Представляет шаблон повышает препровождение результата, который имеет тип, который возвращается `operator==`.  
  
## Заметки  
 Объекты типа `Type` должны быть равенство\-соответствующими.  Для этого необходимо, чтобы `operator==`, указанное для набора объектов удовлетворяет математически свойства отношения эквивалентности.  Все встроенные числовые типы указателей и удовлетворяют этим требованиям.  
  
## Пример  
  
```  
// functional_equal_to.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   vector <double> v1, v2, v3 ( 6 );  
   vector <double>::iterator Iter1, Iter2, Iter3;  
  
   int i;  
   for ( i = 0 ; i <= 5 ; i+=2 )  
   {  
      v1.push_back( 2.0 *i );  
      v1.push_back( 2.0 * i + 1.0 );  
   }  
  
   int j;  
   for ( j = 0 ; j <= 5 ; j+=2 )  
   {  
      v2.push_back( - 2.0 * j );  
      v2.push_back( 2.0 * j + 1.0 );  
   }  
  
   cout << "The vector v1 = ( " ;  
   for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )  
      cout << *Iter1 << " ";  
   cout << ")" << endl;  
  
   cout << "The vector v2 = ( " ;  
   for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )  
      cout << *Iter2 << " ";  
   cout << ")" << endl;  
  
   // Testing for the element-wise equality between v1 & v2  
   transform ( v1.begin( ),  v1.end( ), v2.begin( ), v3.begin ( ),   
      equal_to<double>( ) );  
  
   cout << "The result of the element-wise equal_to comparison\n"  
      << "between v1 & v2 is: ( " ;  
   for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )  
      cout << *Iter3 << " ";  
   cout << ")" << endl;  
}  
```  
  
  **Вектор v1 \= \(0 1 4 5 8 9\)**  
**Вектор v2 \= \(\-0 1 \-4 5 \-8 9\)**  
**Результат — мудрого сравнения equal\_to**  
**между v1 & v2 выглядит следующим образом: \(1 1 0 1 0 1\)**