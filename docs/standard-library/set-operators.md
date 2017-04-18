---
title: "Операторы &lt;set&gt; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4256ebc-c449-4688-95db-fced42d20d4d
caps.latest.revision: 8
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 8a527297ac01359a19f4d5951bb25fcff2dceb5d
ms.lasthandoff: 02/24/2017

---
# <a name="ltsetgt-operators"></a>Операторы &lt;set&gt;
||||  
|-|-|-|  
|[operator!= (set)](#operator_neq)|[operator&gt; (set)](#operator_gt_)|[operator&gt;= (set)](#operator_gt__eq)|  
|[operator&lt; (set)](#operator_lt_)|[operator&lt;= (set)](#operator_lt__eq)|[operator== (set)](#operator_eq_eq)|  
|[operator!= (multiset)](#operator_neq_multiset)|[operator&gt; (multiset)](#operator_gt_multiset)|[operator&gt;= (multiset)](#operator_gt__eq_multiset)|  
|[operator&lt; (multiset)](#operator_lt_multiset)|[operator&lt;= (multiset)](#operator_lt__eq_multiset)|[operator== (multiset)](#operator_eq_eq_multiset)|  
  
##  <a name="a-nameoperatorneqa--operator-set"></a><a name="operator_neq"></a> operator!= (set)  
 Проверяет неравенство объекта-множества слева от оператора объекту-множеству справа от оператора.  
  
```
bool operator!=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Параметры  
 `left`  
 Объект типа **set**.  
  
 `right`  
 Объект типа **set**.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если множества не равны; значение **false**, если множества равны.  
  
### <a name="remarks"></a>Примечания  
 Сравнение между объектами set основывается на попарном сравнении их элементов. Два множества равны, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.  
  
### <a name="example"></a>Пример  
  
```cpp  
// set_op_ne.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i );  
   }  
  
   if ( s1 != s2 )  
      cout << "The sets s1 and s2 are not equal." << endl;  
   else  
      cout << "The sets s1 and s2 are equal." << endl;  
  
   if ( s1 != s3 )  
      cout << "The sets s1 and s3 are not equal." << endl;  
   else  
      cout << "The sets s1 and s3 are equal." << endl;  
}  
\* Output:   
The sets s1 and s2 are not equal.  
The sets s1 and s3 are equal.  
*\  
```  
  
##  <a name="a-nameoperatorlta--operatorlt-set"></a><a name="operator_lt_"></a> operator&lt; (set)  
 Проверяет, меньше ли объект-множество слева от оператора, чем объект-множество справа от оператора.  
  
```
bool operator<(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Параметры  
 `left`  
 Объект типа **set**.  
  
 `right`  
 Объект типа **set**.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если множество слева от оператора строго меньше множества справа от оператора; в противном случае — значение **false**.  
  
### <a name="remarks"></a>Примечания  
 Сравнение между объектами-множествами основывается на попарном сравнении элементов этих множеств. Отношение «меньше» между двумя объектами основывается на сравнении первой пары неравных элементов.  
  
### <a name="example"></a>Пример  
  
```cpp  
// set_op_lt.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
   }  
  
   if ( s1 < s2 )  
      cout << "The set s1 is less than the set s2." << endl;  
   else  
      cout << "The set s1 is not less than the set s2." << endl;  
  
   if ( s1 < s3 )  
      cout << "The set s1 is less than the set s3." << endl;  
   else  
      cout << "The set s1 is not less than the set s3." << endl;  
}  
\* Output:   
The set s1 is less than the set s2.  
The set s1 is not less than the set s3.  
*\  
```  
  
##  <a name="a-nameoperatorlteqa--operatorlt-set"></a><a name="operator_lt__eq"></a> operator&lt;= (set)  
 Проверяет, что объект-множество слева от оператора не больше объекта-множества справа от оператора.  
  
```
bool operator!<=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Параметры  
 `left`  
 Объект типа **set**.  
  
 `right`  
 Объект типа **set**.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если множество слева от оператора не больше множества справа от оператора; в противном случае — значение **false**.  
  
### <a name="remarks"></a>Примечания  
 Сравнение между объектами-множествами основывается на попарном сравнении элементов этих множеств. Отношение «меньше или равно» между двумя объектами основывается на сравнении первой пары неравных элементов.  
  
### <a name="example"></a>Пример  
  
```cpp  
// set_op_le.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2, s3, s4;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
      s4.insert ( i );  
   }  
  
   if ( s1 <= s2 )  
      cout << "Set s1 is less than or equal to the set s2." << endl;  
   else  
      cout << "The set s1 is greater than the set s2." << endl;  
  
   if ( s1 <= s3 )  
      cout << "Set s1 is less than or equal to the set s3." << endl;  
   else  
      cout << "The set s1 is greater than the set s3." << endl;  
  
   if ( s1 <= s4 )  
      cout << "Set s1 is less than or equal to the set s4." << endl;  
   else  
      cout << "The set s1 is greater than the set s4." << endl;  
}  
\* Output:   
Set s1 is less than or equal to the set s2.  
The set s1 is greater than the set s3.  
Set s1 is less than or equal to the set s4.  
*\  
```  
  
##  <a name="a-nameoperatoreqeqa--operator-set"></a><a name="operator_eq_eq"></a> operator== (set)  
 Проверяет равенство объекта-множества слева от оператора объекту-множеству справа от оператора.  
  
```
bool operator!==(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Параметры  
 `left`  
 Объект типа **set**.  
  
 `right`  
 Объект типа **set**.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если множество слева от оператора равно множеству справа от оператора; в противном случае — значение **false**.  
  
### <a name="remarks"></a>Примечания  
 Сравнение между объектами-множествами основывается на попарном сравнении элементов этих множеств. Два множества равны, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.  
  
### <a name="example"></a>Пример  
  
```cpp  
// set_op_eq.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i );  
   }  
  
   if ( s1 == s2 )  
      cout << "The sets s1 and s2 are equal." << endl;  
   else  
      cout << "The sets s1 and s2 are not equal." << endl;  
  
   if ( s1 == s3 )  
      cout << "The sets s1 and s3 are equal." << endl;  
   else  
      cout << "The sets s1 and s3 are not equal." << endl;  
}  
\* Output:   
The sets s1 and s2 are not equal.  
The sets s1 and s3 are equal.  
*\  
```  
  
##  <a name="a-nameoperatorgta--operatorgt-set"></a><a name="operator_gt_"></a> operator&gt; (set)  
 Проверяет, больше ли объект-множество слева от оператора, чем объект-множество справа от оператора.  
  
```
bool operator>(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Параметры  
 `left`  
 Объект типа **set**.  
  
 `right`  
 Объект типа **set**.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если множество слева от оператора больше множества справа от оператора; в противном случае — значение **false**.  
  
### <a name="remarks"></a>Примечания  
 Сравнение между объектами-множествами основывается на попарном сравнении элементов этих множеств. Отношение «больше» между двумя объектами основывается на сравнении первой пары неравных элементов.  
  
### <a name="example"></a>Пример  
  
```cpp  
// set_op_gt.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
   }  
  
   if ( s1 > s2 )  
      cout << "The set s1 is greater than the set s2." << endl;  
   else  
      cout << "The set s1 is not greater than the set s2." << endl;  
  
   if ( s1 > s3 )  
      cout << "The set s1 is greater than the set s3." << endl;  
   else  
      cout << "The set s1 is not greater than the set s3." << endl;  
}  
\* Output:   
The set s1 is not greater than the set s2.  
The set s1 is greater than the set s3.  
*\  
```  
  
##  <a name="a-nameoperatorgteqa--operatorgt-set"></a><a name="operator_gt__eq"></a> operator&gt;= (set)  
 Проверяет, что объект-множество слева от оператора не меньше объекта-множества справа от оператора.  
  
```
bool operator!>=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Параметры  
 `left`  
 Объект типа **set**.  
  
 `right`  
 Объект типа **set**.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если множество слева от оператора не меньше множества справа от оператора; в противном случае — значение **false**.  
  
### <a name="remarks"></a>Примечания  
 Сравнение между объектами-множествами основывается на попарном сравнении элементов этих множеств. Отношение «больше или равно» между двумя объектами основывается на сравнении первой пары неравных элементов.  
  
### <a name="example"></a>Пример  
  
```cpp  
// set_op_ge.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   set <int> s1, s2, s3, s4;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
      s4.insert ( i );  
   }  
  
   if ( s1 >= s2 )  
      cout << "Set s1 is greater than or equal to set s2." << endl;  
   else  
      cout << "The set s1 is less than the set s2." << endl;  
  
   if ( s1 >= s3 )  
      cout << "Set s1 is greater than or equal to set s3." << endl;  
   else  
      cout << "The set s1 is less than the set s3." << endl;  
  
   if ( s1 >= s4 )  
      cout << "Set s1 is greater than or equal to set s4." << endl;  
   else  
      cout << "The set s1 is less than the set s4." << endl;  
}  
\* Output:   
The set s1 is less than the set s2.  
Set s1 is greater than or equal to set s3.  
Set s1 is greater than or equal to set s4.  
*\  
```  
  
##  <a name="a-nameoperatorneqmultiseta--operator-multiset"></a><a name="operator_neq_multiset"></a> operator!= (multiset)  
 Проверяет неравенство объекта multiset слева от оператора и объекта multiset справа от оператора.  
  
```
bool operator!=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Параметры  
 `left`  
 Объект типа `multiset`.  
  
 `right`  
 Объект типа `multiset`.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если множества или мультимножества не равны; значение **false**, если множества или мультимножества равны.  
  
### <a name="remarks"></a>Примечания  
 Сравнение между объектами multiset основывается на попарном сравнении их элементов. Два множества или мультимножества равны, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.  
  
### <a name="example"></a>Пример  
  
```cpp  
// multiset_op_ne.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i );  
   }  
  
   if ( s1 != s2 )  
      cout << "The multisets s1 and s2 are not equal." << endl;  
   else  
      cout << "The multisets s1 and s2 are equal." << endl;  
  
   if ( s1 != s3 )  
      cout << "The multisets s1 and s3 are not equal." << endl;  
   else  
      cout << "The multisets s1 and s3 are equal." << endl;  
}  
\* Output:   
The multisets s1 and s2 are not equal.  
The multisets s1 and s3 are equal.  
*\  
```  
  
##  <a name="a-nameoperatorltmultiseta--operatorlt-multiset"></a><a name="operator_lt_multiset"></a> operator&lt; (multiset)  
 Проверяет, меньше ли объект multiset слева от оператора объекта multiset справа от оператора.  
  
```
bool operator<(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Параметры  
 `left`  
 Объект типа `multiset`.  
  
 `right`  
 Объект типа `multiset`.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если мультимножество слева от оператора строго меньше мультимножества справа от оператора; в противном случае — значение **false**.  
  
### <a name="remarks"></a>Примечания  
 Сравнение между объектами multiset основывается на попарном сравнении их элементов. Отношение «меньше» между двумя объектами основывается на сравнении первой пары неравных элементов.  
  
### <a name="example"></a>Пример  
  
```cpp  
// multiset_op_lt.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
   }  
  
   if ( s1 < s2 )  
      cout << "The multiset s1 is less than "  
           << "the multiset s2." << endl;  
   else  
      cout << "The multiset s1 is not less than "  
           << "the multiset s2." << endl;  
  
   if ( s1 < s3 )  
      cout << "The multiset s1 is less than "  
           << "the multiset s3." << endl;  
   else  
      cout << "The multiset s1 is not less than "  
           << "the multiset s3." << endl;  
}  
\* Output:   
The multiset s1 is less than the multiset s2.  
The multiset s1 is not less than the multiset s3.  
*\  
```  
  
##  <a name="a-nameoperatorlteqmultiseta--operatorlt-multiset"></a><a name="operator_lt__eq_multiset"></a> operator&lt;= (multiset)  
 Проверяет, не больше ли объект multiset слева от оператора объекта multiset справа от оператора.  
  
```
bool operator!<=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Параметры  
 `left`  
 Объект типа `multiset`.  
  
 `right`  
 Объект типа `multiset`.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если мультимножество слева от оператора не больше мультимножества справа от оператора; в противном случае — значение **false**.  
  
### <a name="remarks"></a>Примечания  
 Сравнение между объектами multiset основывается на попарном сравнении их элементов. Отношение «меньше или равно» между двумя объектами основывается на сравнении первой пары неравных элементов.  
  
### <a name="example"></a>Пример  
  
```cpp  
// multiset_op_le.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> s1, s2, s3, s4;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
      s4.insert ( i );  
   }  
  
   if ( s1 <= s2 )  
      cout << "The multiset s1 is less than "  
           << "or equal to the multiset s2." << endl;  
   else  
      cout << "The multiset s1 is greater than "  
           << "the multiset s2." << endl;  
  
   if ( s1 <= s3 )  
      cout << "The multiset s1 is less than "  
           << "or equal to the multiset s3." << endl;  
   else  
      cout << "The multiset s1 is greater than "  
           << "the multiset s3." << endl;  
  
   if ( s1 <= s4 )  
      cout << "The multiset s1 is less than "  
           << "or equal to the multiset s4." << endl;  
   else  
      cout << "The multiset s1 is greater than "  
           << "the multiset s4." << endl;  
}  
\* Output:   
The multiset s1 is less than or equal to the multiset s2.  
The multiset s1 is greater than the multiset s3.  
The multiset s1 is less than or equal to the multiset s4.  
*\  
```  
  
##  <a name="a-nameoperatoreqeqmultiseta--operator-multiset"></a><a name="operator_eq_eq_multiset"></a> operator== (multiset)  
 Проверяет, равен ли объект multiset слева от оператора объекту multiset справа от оператора.  
  
```
bool operator!==(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Параметры  
 `left`  
 Объект типа `multiset`.  
  
 `right`  
 Объект типа `multiset`.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если мультимножество слева от оператора равно мультимножеству справа от оператора; в противном случае — значение **false**.  
  
### <a name="remarks"></a>Примечания  
 Сравнение между объектами multiset основывается на попарном сравнении их элементов. Два множества или мультимножества равны, если они содержат одинаковое количество элементов, а их соответствующие элементы имеют одинаковые значения. В противном случае они не равны.  
  
### <a name="example"></a>Пример  
  
```cpp  
// multiset_op_eq.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i );  
   }  
  
   if ( s1 == s2 )  
      cout << "The multisets s1 and s2 are equal." << endl;  
   else  
      cout << "The multisets s1 and s2 are not equal." << endl;  
  
   if ( s1 == s3 )  
      cout << "The multisets s1 and s3 are equal." << endl;  
   else  
      cout << "The multisets s1 and s3 are not equal." << endl;  
}  
\* Output:   
The multisets s1 and s2 are not equal.  
The multisets s1 and s3 are equal.  
*\  
```  
  
##  <a name="a-nameoperatorgtmultiseta--operatorgt-multiset"></a><a name="operator_gt_multiset"></a> operator&gt; (multiset)  
 Проверяет, больше ли объект multiset слева от оператора объекта multiset справа от оператора.  
  
```
bool operator>(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Параметры  
 `left`  
 Объект типа `multiset`.  
  
 `right`  
 Объект типа `multiset`.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если мультимножество слева от оператора больше мультимножества справа от оператора; в противном случае — значение **false**.  
  
### <a name="remarks"></a>Примечания  
 Сравнение между объектами multiset основывается на попарном сравнении их элементов. Отношение «больше» между двумя объектами основывается на сравнении первой пары неравных элементов.  
  
### <a name="example"></a>Пример  
  
```cpp  
// multiset_op_gt.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> s1, s2, s3;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
   }  
  
   if ( s1 > s2 )  
      cout << "The multiset s1 is greater than "  
           << "the multiset s2." << endl;  
   else  
      cout << "The multiset s1 is not greater "  
           << "than the multiset s2." << endl;  
  
   if ( s1 > s3 )  
      cout << "The multiset s1 is greater than "  
           << "the multiset s3." << endl;  
   else  
      cout << "The multiset s1 is not greater than "  
           << "the multiset s3." << endl;  
}  
\* Output:   
The multiset s1 is not greater than the multiset s2.  
The multiset s1 is greater than the multiset s3.  
*\  
```  
  
##  <a name="a-nameoperatorgteqmultiseta--operatorgt-multiset"></a><a name="operator_gt__eq_multiset"></a> operator&gt;= (multiset)  
 Проверяет, не меньше ли объект multiset слева от оператора объекта multiset справа от оператора.  
  
```
bool operator!>=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>Параметры  
 `left`  
 Объект типа `multiset`.  
  
 `right`  
 Объект типа `multiset`.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если мультимножество слева от оператора не меньше мультимножества справа от оператора; в противном случае — значение **false**.  
  
### <a name="remarks"></a>Примечания  
 Сравнение между объектами multiset основывается на попарном сравнении их элементов. Отношение «больше или равно» между двумя объектами основывается на сравнении первой пары неравных элементов.  
  
### <a name="example"></a>Пример  
  
```cpp  
// multiset_op_ge.cpp  
// compile with: /EHsc  
#include <set>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   multiset <int> s1, s2, s3, s4;  
   int i;  
  
   for ( i = 0 ; i < 3 ; i++ )  
   {  
      s1.insert ( i );  
      s2.insert ( i * i );  
      s3.insert ( i - 1 );  
      s4.insert ( i );  
   }  
  
   if ( s1 >= s2 )  
      cout << "The multiset s1 is greater than "  
           << "or equal to the multiset s2." << endl;  
   else  
      cout << "The multiset s1 is less than "  
           << "the multiset s2." << endl;  
  
   if ( s1 >= s3 )  
      cout << "The multiset s1 is greater than "  
           << "or equal to the multiset s3." << endl;  
   else  
      cout << "The multiset s1 is less than "  
           << "the multiset s3." << endl;  
  
   if ( s1 >= s4 )  
      cout << "The multiset s1 is greater than "  
           << "or equal to the multiset s4." << endl;  
   else  
      cout << "The multiset s1 is less than "  
           << "the multiset s4." << endl;  
}  
\* Output:   
The multiset s1 is less than the multiset s2.  
The multiset s1 is greater than or equal to the multiset s3.  
The multiset s1 is greater than or equal to the multiset s4.  
*\  
```  
  
## <a name="see-also"></a>См. также  
 [\<set>](../standard-library/set.md)



