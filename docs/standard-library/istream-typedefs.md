---
title: "Определения типов &lt;istream&gt; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: e3607735f989b61f373eb689b8fe3b2dee656f7b
ms.lasthandoff: 02/24/2017

---
# <a name="ltistreamgt-typedefs"></a>Определения типов &lt;istream&gt;
||||  
|-|-|-|  
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|  
|[wistream](#wistream)|  
  
##  <a name="a-nameiostreama--iostream"></a><a name="iostream"></a>  iostream  
 Тип `basic_iostream`, специализированный для `char`.  
  
```  
typedef basic_iostream<char, char_traits<char>> iostream;  
```  
  
### <a name="remarks"></a>Примечания  
 Этот тип является синонимом класса шаблона [basic_iostream](../standard-library/basic-iostream-class.md), специализированного для элементов типа `char` с признаками символов по умолчанию.  
  
##  <a name="a-nameistreama--istream"></a><a name="istream"></a>  istream  
 Тип `basic_istream`, специализированный для `char`.  
  
```  
typedef basic_istream<char, char_traits<char>> istream;  
```  
  
### <a name="remarks"></a>Примечания  
 Этот тип является синонимом класса шаблона [basic_istream](../standard-library/basic-istream-class.md), специализированного для элементов типа `char` с признаками символов по умолчанию.  
  
##  <a name="a-namewiostreama--wiostream"></a><a name="wiostream"></a>  wiostream  
 Тип `basic_iostream`, специализированный для `wchar_t`.  
  
```  
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;  
```  
  
### <a name="remarks"></a>Примечания  
 Этот тип является синонимом класса шаблона [basic_iostream](../standard-library/basic-iostream-class.md), специализированного для элементов типа `wchar_t` с признаками символов по умолчанию.  
  
##  <a name="a-namewistreama--wistream"></a><a name="wistream"></a>  wistream  
 Тип `basic_istream`, специализированный для `wchar_t`.  
  
```  
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;  
```  
  
### <a name="remarks"></a>Примечания  
 Этот тип является синонимом класса шаблона [basic_istream](../standard-library/basic-istream-class.md), специализированного для элементов типа `wchar_t` с признаками символов по умолчанию.  
  
## <a name="see-also"></a>См. также  
 [\<istream>](../standard-library/istream.md)

