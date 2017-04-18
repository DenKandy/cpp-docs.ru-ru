---
title: "Класс money_get | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocmon/std::money_get
- money_get
- std.money_get
- std::money_get
dev_langs:
- C++
helpviewer_keywords:
- money_get class
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: f9e122dbeb68fb4ed33d9e652af21c1b9474e3a5
ms.lasthandoff: 02/24/2017

---
# <a name="moneyget-class"></a>Класс money_get
Шаблонный класс описывает объект, который можно использовать как аспект языкового стандарта для управления преобразованиями последовательностей типа `CharType` в денежные значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>  
class money_get : public locale::facet;
```  
  
#### <a name="parameters"></a>Параметры  
 `CharType`  
 Тип, используемый внутри программы для кодирования символов в языковом стандарте.  
  
 `InputIterator`  
 Тип итератора, из которого функции получения считывают своих входные данные.  
  
## <a name="remarks"></a>Примечания  
 Как и в случае любого другого аспекта языкового стандарта, начальное сохраненное значение статического идентификатора объекта равно нулю. Первая попытка получить доступ к сохраненному значению сохранит уникальное положительное значение в **id.**  
  
### <a name="constructors"></a>Конструкторы  
  
|||  
|-|-|  
|[money_get](#money_get__money_get)|Конструктор для объектов типа `money_get`, используемых для извлечения числовых значений из последовательностей, представляющих денежные значения.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#money_get__char_type)|Тип, используемый для описания символа, используемого языковым стандартом.|  
|[iter_type](#money_get__iter_type)|Тип, который описывает итератор ввода.|  
|[string_type](#money_get__string_type)|Тип, описывающий строку, содержащую символы типа `CharType`.|  
  
### <a name="member-functions"></a>Функции-члены  
  
|||  
|-|-|  
|[do_get](#money_get__do_get)|Виртуальная функция, вызываемая для извлечения числового значения из последовательности символов, представляющей денежное значение.|  
|[get](#money_get__get)|Извлекает числовое значение из последовательности символов, представляющей денежное значение.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<locale>  
  
 **Пространство имен:** std  
  
##  <a name="a-namemoneygetchartypea--moneygetchartype"></a><a name="money_get__char_type"></a>  money_get::char_type  
 Тип, используемый для описания символа, используемого языковым стандартом.  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>Примечания  
 Тип является синонимом параметра-шаблона **CharType**.  
  
##  <a name="a-namemoneygetdogeta--moneygetdoget"></a><a name="money_get__do_get"></a>  money_get::do_get  
 Виртуальная функция, которая вызывается для извлечения числового значения из последовательности символов, которая представляет денежное значение.  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const
```  
  
### <a name="parameters"></a>Параметры  
 `first`  
 Входной итератор, адресующий начало последовательности для преобразования.  
  
 `last`  
 Входной итератор, адресующий конец последовательности для преобразования.  
  
 `Intl`  
 Логическое значение, указывающее тип символа валюты, ожидаемого в последовательности: **true** для международного символа, **false** для внутреннего.  
  
 `Iosbase`  
 Флаг формата, который, будучи установленным, указывает, что символ валюты не обязателен; в противном случае он обязателен.  
  
 `State`  
 Устанавливает нужные элементы битовой маски для состояния потока согласно тому, успешно ли выполнились операции.  
  
 `val`  
 Строка, хранящая преобразованную последовательность.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Входной итератор, адресующий первый элемент после денежного поля ввода.  
  
### <a name="remarks"></a>Примечания  
 Первая защищенная виртуальная функция-член пытается сопоставить последовательные элементы, начиная с первого в последовательности [ `first`, `last`), пока не распознает полное, непустое денежное поле ввода. При успешном выполнении она преобразует это поле в последовательность из одной или нескольких десятичных цифр, при необходимости в начале размещается знак минуса ( `–`), чтобы представить сумму, и сохраняет результат в объекте [string_type](#money_get__string_type) `val`. Она возвращает итератор, обозначающий первый элемент после денежного поля ввода. В противном случае функция сохраняет пустую последовательность в `val` и устанавливает `ios_base::failbit` в `State`. Она возвращает итератор, обозначающий первый элемент после любого префикса допустимого денежного поля ввода. В любом случае, если возвращаемое значение равно `last`, функция устанавливает `ios_base::eofbit` в `State`.  
  
 Вторая виртуальная защищенная функция-член ведет себя так же, как первая, за исключением того, что в случае успешного выполнения она преобразует последовательность цифр (при необходимости — со знаком) в значение типа `long double` и сохраняет это значение в `val`.  
  
 Формат денежного поля ввода определяется [аспектом языкового стандарта](../standard-library/locale-class.md#facet_class)**fac**, возвращаемого эффективным вызовом [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**>>( **iosbase**. [getloc](../standard-library/ios-base-class.md#ios_base__getloc)).  
  
 В частности:  
  
- **fac**. [neg_format](../standard-library/moneypunct-class.md#moneypunct__neg_format) определяет порядок, в котором будут расположены компоненты поля.  
  
- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#moneypunct__curr_symbol) определяет последовательность элементов, составляющую символ валюты.  
  
- **fac**. [positive_sign](../standard-library/moneypunct-class.md#moneypunct__positive_sign) определяет последовательность элементов, составляющую положительный знак.  
  
- **fac**. [positive_sign](../standard-library/moneypunct-class.md#moneypunct__negative_sign) определяет последовательность элементов, составляющую отрицательный знак.  
  
- **fac**. [grouping](../standard-library/moneypunct-class.md#moneypunct__grouping) определяет, как группируются цифры слева от любого десятичного разделителя.  
  
- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#moneypunct__thousands_sep) определяет элемент, разделяющий группы цифр слева от любого десятичного разделителя.  
  
- **fac**. [decimal_point](../standard-library/moneypunct-class.md#moneypunct__decimal_point) определяет элемент, который отделяет цифры целой части от цифр дробной части.  
  
- **fac**. [frac_digits](../standard-library/moneypunct-class.md#moneypunct__frac_digits) определяет количество значимых цифр дробной части справа от любого десятичного разделителя. При разборе денежной суммы, в которой больше цифр после запятой, чем требуется `frac_digits`, `do_get` прекращает разбор после как максимум `frac_digits` символов.  
  
 Если строка знака ( **fac**. `negative_sign` или **fac**. `positive_sign`) имеет более одного элемента, сопоставляется только первый элемент, если элемент, равный **money_base::sign** появляется в шаблоне формата ( **fac**. `neg_format`). Любые остающиеся элементы сопоставляются в конце денежного поля ввода. Если ни одна из строк не имеет первого элемента, который соответствует следующему элементу в денежном поле ввода, строка знака считается пустой, а знак — положительным.  
  
 Если **iosbase**. [flags](../standard-library/ios-base-class.md#ios_base__flags) & [showbase](../standard-library/ios-functions.md#showbase) не равно нулю, то строка **fac**. `curr_symbol` должна соответствовать в том месте, где в шаблоне формата возникает элемент, равный **money_base::symbol**. В противном случае, если **money_base::symbol** возникает в конце шаблона формате и если не осталось элементов строки знака для сопоставления, символ валюты не сопоставляется. В противном случае символ валюты при необходимости сопоставляется.  
  
 Если в части значения денежного поля ввода не появляется экземпляров **fac**. `thousands_sep` (если в шаблоне формата есть элемент, равный **money_base::value**), ограничения группировки не применяются. В противном случае применяются любые ограничения группировки, определяемые в **fac**. **grouping**. Обратите внимание, что результирующая последовательность цифр представляет собой целое число, чьи младшие десятичные цифры **fac**. `frac_digits` считаются находящимися справа от десятичного разделителя.  
  
 Произвольный пробел считается соответствующим, если в шаблоне формата появляется элемент, равный **money_base::space**, если он находится не в конце шаблона формата. В противном случае внутренние пробелы не сопоставляются. Элемент *ch* считается пробелом, если [use_facet](../standard-library/locale-functions.md#use_facet) < [ctype](../standard-library/ctype-class.md)\< **CharType**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#ios_base__getloc)). [is](../standard-library/ctype-class.md#ctype__is)( **ctype_base::space**, *ch*) имеет значение **true**.  
  
### <a name="example"></a>Пример  
  См. пример для [get](#money_get__get), который вызывает `do_get`.  
  
##  <a name="a-namemoneygetgeta--moneygetget"></a><a name="money_get__get"></a>  money_get::get  
 Извлекает числовое значение из последовательности символов, представляющей денежное значение.  
  
```
iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const;

iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const;
```  
  
### <a name="parameters"></a>Параметры  
 `first`  
 Входной итератор, адресующий начало последовательности для преобразования.  
  
 `last`  
 Входной итератор, адресующий конец последовательности для преобразования.  
  
 `Intl`  
 Логическое значение, указывающее тип символа валюты, ожидаемого в последовательности: **true** для международного символа, **false** для внутреннего.  
  
 `Iosbase`  
 Флаг формата, который, будучи установленным, указывает, что символ валюты не обязателен; в противном случае он обязателен.  
  
 `State`  
 Устанавливает нужные элементы битовой маски для состояния потока согласно тому, успешно ли выполнились операции.  
  
 `val`  
 Строка, хранящая преобразованную последовательность.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Входной итератор, адресующий первый элемент после денежного поля ввода.  
  
### <a name="remarks"></a>Примечания  
 Обе функции-члены возвращают [do_get](#money_get__do_get)( `first``,` `last``,` `Intl`, `Iosbase`, `State`, `val`).  
  
### <a name="example"></a>Пример  
  
```cpp  
// money_get_get.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
  
int main( )  
{  
   locale loc( "german_germany" );  
  
   basic_stringstream< char > psz;  
   psz << use_facet<moneypunct<char, 1> >(loc).curr_symbol() << "-1.000,56";  
   basic_stringstream< char > psz2;  
   psz2 << "-100056" << use_facet<moneypunct<char, 1> >(loc).curr_symbol();  
  
   ios_base::iostate st = 0;  
   long double fVal;  
  
   psz.flags( psz.flags( )|ios_base::showbase );   
   // Which forced the READING the currency symbol  
   psz.imbue(loc);  
   use_facet < money_get < char > >( loc ).  
      get( basic_istream<char>::_Iter( psz.rdbuf( ) ),     
           basic_istream<char>::_Iter( 0 ), true, psz, st, fVal );  
  
   if ( st & ios_base::failbit )  
      cout << "money_get(" << psz.str( ) << ", intl = 1) FAILED"  
           << endl;  
   else  
      cout << "money_get(" << psz.str( ) << ", intl = 1) = "   
           << fVal/100.0 << endl;  
  
   use_facet < money_get < char > >( loc ).  
      get(basic_istream<char>::_Iter(psz2.rdbuf( )),     
          basic_istream<char>::_Iter(0), false, psz2, st, fVal);  
  
   if ( st & ios_base::failbit )  
      cout << "money_get(" << psz2.str( ) << ", intl = 0) FAILED"   
           << endl;  
   else  
      cout << "money_get(" << psz2.str( ) << ", intl = 0) = "   
           << fVal/100.0 << endl;  
};  
```  
  
##  <a name="a-namemoneygetitertypea--moneygetitertype"></a><a name="money_get__iter_type"></a>  money_get::iter_type  
 Тип, который описывает итератор ввода.  
  
```
typedef InputIterator iter_type;
```  
  
### <a name="remarks"></a>Примечания  
 Этот тип является синонимом для параметра-шаблона **InputIterator**.  
  
##  <a name="a-namemoneygetmoneygeta--moneygetmoneyget"></a><a name="money_get__money_get"></a>  money_get::money_get  
 Конструктор для объектов типа `money_get`, используемых для извлечения числовых значений из последовательностей, представляющих денежные значения.  
  
```
explicit money_get(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>Параметры  
 `_Refs`  
 Целочисленное значение, используемое для указания типа управления памятью для объекта.  
  
### <a name="remarks"></a>Примечания  
 Возможные значения параметра `_Refs` и их важность:  
  
-   0: время существования объекта управляется языковыми стандартами, которые его содержат.  
  
-   1: время существования объекта должно управляться вручную.  
  
-   \> 0: эти значения не определены.  
  
 Прямые примеры привести нельзя, так как деструктор защищен.  
  
 Конструктор инициализирует свой базовый объект через **locale::**[facet](../standard-library/locale-class.md#facet_class)( **_***Refs*).  
  
##  <a name="a-namemoneygetstringtypea--moneygetstringtype"></a><a name="money_get__string_type"></a>  money_get::string_type  
 Тип, который описывает строку, содержащую символы типа **CharType**.  
  
```
typedef basic_string<CharType, Traits, Allocator> string_type;
```  
  
### <a name="remarks"></a>Примечания  
 Тип описывает специализацию класса-шаблона [basic_string](../standard-library/basic-string-class.md).  
  
## <a name="see-also"></a>См. также  
 [\<locale>](../standard-library/locale.md)   
 [Класс facet](../standard-library/locale-class.md#facet_class)   
 [Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



