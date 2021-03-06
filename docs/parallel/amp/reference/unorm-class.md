---
title: "Класс unorm | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
dev_langs:
- C++
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cfd4ed2b4aad398e1206d0e3b786742841aa189b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/23/2018
---
# <a name="unorm-class"></a>Класс unorm
Представляет число unorm. Каждый элемент является типом с плавающей запятой в диапазоне [0, 0f, 1, 0f].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
class unorm;  
```  
  
## <a name="members"></a>Участники  
  
### <a name="public-constructors"></a>Открытые конструкторы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[Конструктор unorm](#ctor)|Перегружен. Конструктор по умолчанию. Инициализируйте 0, 0f.|  
  
### <a name="public-operators"></a>Открытые операторы  
  
|Имя|Описание:|  
|----------|-----------------|  
|unorm::operator--||  
|unorm::operator число с плавающей запятой|Оператор преобразования. Преобразуйте unorm число с плавающей запятой.|  
|unorm::operator * =||  
|unorm::operator / =||  
|unorm::operator ++||  
|unorm::operator +=||  
|unorm::operator =||  
|unorm::operator-=||  
  
## <a name="inheritance-hierarchy"></a>Иерархия наследования  
 `unorm`  
  
## <a name="requirements"></a>Требования  
 **Header:** amp_short_vectors.h  
  
 **Namespace:** Concurrency::graphics  
  
##  <a name="ctor"></a> unorm 

 Конструктор по умолчанию. Инициализируйте 0, 0f.  
  
```  
unorm(
    void) restrict(amp,
    cpu);

 
explicit unorm(
    float _V) restrict(amp,
    cpu);

 
explicit unorm(
    unsigned int _V) restrict(amp,
    cpu);

 
explicit unorm(
    int _V) restrict(amp,
    cpu);

 
explicit unorm(
    double _V) restrict(amp,
    cpu);

 
unorm(
    const unorm& _Other) restrict(amp,
    cpu);

 
inline explicit unorm(
    const norm& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Параметры  
 `_V`  
 Значение, используемое для инициализации.  
  
 `_Other`  
 Норма объект, используемый для инициализации.  
  
## <a name="see-also"></a>См. также  
 [Пространство имен Concurrency::graphics](concurrency-graphics-namespace.md)
