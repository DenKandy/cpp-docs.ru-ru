---
title: "оператор&lt;= (&lt;образец контейнера&gt;) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::<=
- std.operator<=
- operator<=
- std.<=
- std::operator<=
- <=
dev_langs:
- C++
helpviewer_keywords:
- operator<=
- operator <=
- <= operator, with specific objects
- <= operator
ms.assetid: 338577dd-dc88-4a2b-9e12-0379c54fc8a2
caps.latest.revision: 9
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
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 160eac8642d463b367ae218cecb9b1ad5984f4a3
ms.lasthandoff: 02/24/2017

---
# <a name="operatorlt-ltsample-containergt"></a>оператор&lt;= (&lt;образец контейнера&gt;)
> [!NOTE]
>  Данный раздел включен в документацию Visual C++ в качестве нефункционального примера контейнеров, используемых в стандартной библиотеке C++. Дополнительные сведения см. в разделе [Контейнеры стандартной библиотеки C++](../standard-library/stl-containers.md).  
  
 Перегружает **оператор<=** для сравнения двух объектов класса шаблона [контейнер](../standard-library/sample-container-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
 
    template <class Ty>  
bool operator<=(
    const Container <Ty>& left,  
    const Container <Ty>& right);
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает **!**(_*Right* < \_*Left*).  
  
## <a name="see-also"></a>См. также  
 [\<образец контейнера>](../standard-library/sample-container.md)

