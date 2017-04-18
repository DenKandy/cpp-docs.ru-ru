---
title: "Класс raw_storage_iterator | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::raw_storage_iterator
- raw_storage_iterator
- std.raw_storage_iterator
- memory/std::raw_storage_iterator
dev_langs:
- C++
helpviewer_keywords:
- raw_storage_iterator class
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: a7aef3b83378d36ff5db1ec14c401112818c8de1
ms.lasthandoff: 02/24/2017

---
# <a name="rawstorageiterator-class"></a>Класс raw_storage_iterator
Класс-адаптер, который предоставляется, чтобы алгоритмы могли сохранять свои результаты в неинициализированной памяти.  
  
## <a name="syntax"></a>Синтаксис  
  
```
template <class OutputIterator, class Type>  
class raw_storage_iterator
```  
  
#### <a name="parameters"></a>Параметры  
 `OutputIterator`  
 Указывает выходной итератор сохраняемого объекта.  
  
 *Тип*  
 Тип объекта, для которого выполняется выделение памяти.  
  
## <a name="remarks"></a>Примечания  
 Класс описывает итератор вывода, который создает объекты типа **Type** в формируемой им последовательности. Объект класса `raw_storage_iterator`\< **ForwardIterator**, **Type**> получает доступ к хранилищу с помощью объекта прямого итератора класса **ForwardIterator**, который указывается при создании объекта. Для объекта first класса **ForwardIterator** выражение **&\*first** должно обозначать несконструированное хранилище для следующего объекта (типа **Type**) в создаваемой последовательности.  
  
 Этот класс адаптера используется, когда необходимо разделить выделение памяти и создание объектов. `raw_storage_iterator` можно использовать для копирования объектов в неинициализированное хранилище, например в память, выделенную с помощью функции `malloc`.  
  
## <a name="members"></a>Участники  
  
### <a name="constructors"></a>Конструкторы  
  
|||  
|-|-|  
|[raw_storage_iterator](#raw_storage_iterator__raw_storage_iterator)|Создает итератор необработанного хранилища с указанным базовым выходным итератором.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[element_type](#raw_storage_iterator__element_type)|Предоставляет тип, описывающий элемент, в котором будет сохранен итератор необработанного хранилища.|  
|[iter_type](#raw_storage_iterator__iter_type)|Предоставляет тип, который описывает итератор, базовый для итератора необработанного хранилища.|  
  
### <a name="operators"></a>Операторы  
  
|||  
|-|-|  
|[оператор*](#raw_storage_iterator__operator_star)|Оператор разыменования, используемый для реализации выражения итератора вывода * `ii` = `x`.|  
|[оператор=](#raw_storage_iterator__operator_eq)|Оператор присваивания, используемый для реализации выражения итератора необработанного хранилища * `i` = `x` для сохранения в памяти.|  
|[оператор++](#raw_storage_iterator__operator_add_add)|Преинкрементный и постинкрементный операторы для итераторов необработанного хранилища.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<memory>  
  
 **Пространство имен:** std  
  
##  <a name="a-namerawstorageiteratorelementtypea--rawstorageiteratorelementtype"></a><a name="raw_storage_iterator__element_type"></a>  raw_storage_iterator::element_type  
 Предоставляет тип, описывающий элемент, в котором будет сохранен итератор необработанного хранилища.  
  
```
typedef Type element_type;
```  
  
### <a name="remarks"></a>Примечания  
 Тип является синонимом параметра-шаблона **Type** класса raw_storage_iterator.  
  
##  <a name="a-namerawstorageiteratoritertypea--rawstorageiteratoritertype"></a><a name="raw_storage_iterator__iter_type"></a>  raw_storage_iterator::iter_type  
 Предоставляет тип, который описывает итератор, базовый для итератора необработанного хранилища.  
  
```
typedef ForwardIterator iter_type;
```  
  
### <a name="remarks"></a>Примечания  
 Тип является синонимом для параметра-шаблона **ForwardIterator**.  
  
##  <a name="a-namerawstorageiteratoroperatorstara--rawstorageiteratoroperator"></a><a name="raw_storage_iterator__operator_star"></a>  raw_storage_iterator::operator*  
 Оператор разыменования, используемый для реализации выражения итератора необработанного хранилища \* *ii* = *x*.  
  
```
raw_storage_iterator<ForwardIterator, Type>& operator*();
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Ссылка на итератор необработанного хранилища  
  
### <a name="remarks"></a>Примечания  
 Требования для состояния **ForwardIterator**, которые должен выполнить итератор необработанного хранилища, требуют только действительность выражения \* *ii* = *t*, и он не должен ничего сообщать об **operator** или `operator=` самих по себе. Возвращает операторы-члены в этой реализации **\*this**, так что [operator=](#raw_storage_iterator__operator_eq)(**constType**&) может выполнить фактическое сохранение в выражении, таком как \* *ptr* = `val`.  
  
### <a name="example"></a>Пример  
  
```cpp  
// raw_storage_iterator_op_deref.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iterator>  
#include <memory>  
#include <list>  
using namespace std;  
  
class Int   
{  
public:  
   Int(int i)   
   {  
      cout << "Constructing " << i << endl;   
      x = i;  
      bIsConstructed = true;  
   };  
  
   Int &operator=(int i)   
   {  
      if (!bIsConstructed)  
         cout << "Not constructed.\n";  
      cout << "Copying " << i << endl;    
      x = i;   
      return *this;  
   };  
  
   int x;  
  
private:  
   bool bIsConstructed;  
};  
  
int main( void)   
{  
   Int *pInt = ( Int* ) malloc( sizeof( Int ) );  
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;  
 *pInt = 5;  
   raw_storage_iterator< Int*, Int > it( pInt );  
 *it = 5;  
}  
\* Output:   
Not constructed.  
Copying 5  
Constructing 5  
*\  
```  
  
##  <a name="a-namerawstorageiteratoroperatoreqa--rawstorageiteratoroperator"></a><a name="raw_storage_iterator__operator_eq"></a>  raw_storage_iterator::operator=  
 Оператор присваивания, используемый для реализации выражения итератора необработанного хранилища \* *i* = *x* для сохранения в памяти.  
  
```
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```  
  
### <a name="parameters"></a>Параметры  
 `val`  
 Значение объекта типа **Type** для вставки в память.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Оператор вставляет `val` в память и возвращает ссылку на итератор необработанного хранилища.  
  
### <a name="remarks"></a>Примечания  
 Требования для состояния **ForwardIterator**, которые должен выполнить итератор необработанного хранилища, требуют только действительность выражения \* *ii* = *t*, и он не должен ничего сообщать об **operator** или `operator=` самих по себе. Эти операторы-члены возвращают **\*this**.  
  
 Оператор присваивания создает следующий объект в выходной последовательности, используя сначала значение сохраненного итератора путем вычисления расположения нового выражения **new** ((`void` \*)&\* **first**) **Type**(`val`).  
  
### <a name="example"></a>Пример  
  
```cpp  
// raw_storage_iterator_op_assign.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iterator>  
#include <memory>  
#include <list>  
using namespace std;  
  
class Int   
{  
public:  
   Int( int i )   
   {  
      cout << "Constructing " << i << endl;   
      x = i;  
      bIsConstructed = true;  
   };  
   Int &operator=( int i )   
   {  
      if ( !bIsConstructed )  
         cout << "Not constructed.\n";  
      cout << "Copying " << i << endl; x = i;  
      return *this;  
   };  
   int x;  
private:  
   bool bIsConstructed;  
};  
  
int main( void )  
{  
   Int *pInt = ( Int* )malloc( sizeof( Int ) );  
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;  
  
 *pInt = 5;  
  
   raw_storage_iterator<Int*, Int> it( pInt );  
 *it = 5;  
}  
\* Output:   
Not constructed.  
Copying 5  
Constructing 5  
*\  
```  
  
##  <a name="a-namerawstorageiteratoroperatoraddadda--rawstorageiteratoroperator"></a><a name="raw_storage_iterator__operator_add_add"></a>  raw_storage_iterator::operator++  
 Преинкрементный и постинкрементный операторы для итераторов необработанного хранилища.  
  
```
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Итератор необработанного хранилища или ссылка такой итератор.  
  
### <a name="remarks"></a>Примечания  
 Первый оператор в конечном итоге пытается извлечь и сохранить объект типа **CharType** из соответствующего входного потока. Второй оператор создает копию объекта, выполняет приращение объекта, а затем возвращает копию.  
  
 Первый оператор preincrement увеличивает сохраненный объект-итератор вывода, а затем возвращает **\*this**.  
  
 Второй оператор postincrement создает копию **\*this**, увеличивает сохраненный объект-итератор вывода, а затем возвращает копию.  
  
 Конструктор сохраняет **first** как объект-итератор вывода.  
  
### <a name="example"></a>Пример  
  
```cpp  
// raw_storage_iterator_op_incr.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <iterator>  
#include <memory>  
#include <list>  
using namespace std;  
  
int main( void )  
{  
   int *pInt = new int[5];  
   std::raw_storage_iterator<int*,int> it( pInt );  
   for ( int i = 0; i < 5; i++, it++ ) {  
 *it = 2 * i;  
};  
  
   for ( int i = 0; i < 5; i++ ) cout << "array " << i << " = " << pInt[i] << endl;;  
  
   delete[] pInt;  
}  
\* Output:   
array 0 = 0  
array 1 = 2  
array 2 = 4  
array 3 = 6  
array 4 = 8  
*\  
```  
  
##  <a name="a-namerawstorageiteratorrawstorageiteratora--rawstorageiteratorrawstorageiterator"></a><a name="raw_storage_iterator__raw_storage_iterator"></a>  raw_storage_iterator::raw_storage_iterator  
 Создает итератор необработанного хранилища с указанным базовым выходным итератором.  
  
```
explicit raw_storage_iterator(ForwardIterator first);
```  
  
### <a name="parameters"></a>Параметры  
 `first`  
 Прямой итератор, который лежит в основе создаваемого объекта `raw_storage_iterator`.  
  
### <a name="example"></a>Пример  
  
```cpp  
// raw_storage_iterator_ctor.cpp  
// compile with: /EHsc /W3  
#include <iostream>  
#include <iterator>  
#include <memory>  
#include <list>  
using namespace std;  
  
class Int  
{  
public:  
   Int(int i)  
   {  
      cout << "Constructing " << i << endl;  
      x = i;  
      bIsConstructed = true;  
   };  
   Int &operator=( int i )  
   {  
      if (!bIsConstructed)  
         cout << "Error! I'm not constructed!\n";  
      cout << "Copying " << i << endl;  x = i; return *this;  
   };  
   int x;  
   bool bIsConstructed;  
};  
  
int main( void )  
{  
   std::list<int> l;  
   l.push_back( 1 );  
   l.push_back( 2 );  
   l.push_back( 3 );  
   l.push_back( 4 );  
  
   Int *pInt = (Int*)malloc(sizeof(Int)*l.size( ));  
   memset (pInt, 0, sizeof(Int)*l.size( ));  
   // Hack: make sure bIsConstructed is false  
  
   std::copy( l.begin( ), l.end( ), pInt );  // C4996  
   for (unsigned int i = 0; i < l.size( ); i++)  
      cout << "array " << i << " = " << pInt[i].x << endl;;  
  
   memset (pInt, 0, sizeof(Int)*l.size( ));  
   // hack: make sure bIsConstructed is false  
  
   std::copy( l.begin( ), l.end( ),  
      std::raw_storage_iterator<Int*,Int>(pInt));  // C4996  
   for (unsigned int i = 0; i < l.size( ); i++ )  
      cout << "array " << i << " = " << pInt[i].x << endl;  
  
   free(pInt);  
}  
\* Output:   
Error! I'm not constructed!  
Copying 1  
Error! I'm not constructed!  
Copying 2  
Error! I'm not constructed!  
Copying 3  
Error! I'm not constructed!  
Copying 4  
array 0 = 1  
array 1 = 2  
array 2 = 3  
array 3 = 4  
Constructing 1  
Constructing 2  
Constructing 3  
Constructing 4  
array 0 = 1  
array 1 = 2  
array 2 = 3  
array 3 = 4  
*\  
```  
  
## <a name="see-also"></a>См. также  
 [Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



