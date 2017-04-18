---
title: "&lt;memory&gt; | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::<memory>
- std.<memory>
- <memory>
- std::<memory>
dev_langs:
- C++
helpviewer_keywords:
- memory header
ms.assetid: ef8e38da-7c9d-4037-9ad1-20c99febf5dc
caps.latest.revision: 22
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
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: ca10c4b759f9dafbfe4ffd3d6ac4a4b8c0d5b1dc
ms.lasthandoff: 02/24/2017

---
# <a name="ltmemorygt"></a>&lt;memory&gt;
Определяет класс, оператор и несколько шаблонов, позволяющих выделять и освобождать объекты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
#include <memory>  
  
```  
  
## <a name="members"></a>Члены  
  
### <a name="functions"></a>Функции  
  
|||  
|-|-|  
|[addressof](../standard-library/memory-functions.md#addressof)|Получает истинный адрес объекта.|  
|[align](../standard-library/memory-functions.md#align)|Возвращает указатель на диапазон заданного размера на основе указанного выравнивания и начального адреса.|  
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|Создает `shared_ptr` для объектов, выделенных и созданных для заданного типа с указанным распределителем.|  
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|Постоянное приведение к `shared_ptr`.|  
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|Сообщает сборщику мусора, что символы, начинающиеся с указанного адреса и попадающие в блок указанного размера, не содержат трассируемых указателей.|  
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|Уведомляет сборщик мусора, что указанный адрес относится к выделенной памяти и является доступным.|  
|[default_delete](../standard-library/memory-functions.md#default_delete)|Удаляет объекты, выделенные с помощью `operator new`. Подходит для использования с `unique_ptr`.|  
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|Динамическое приведение к `shared_ptr`.|  
|[get_deleter](../standard-library/memory-functions.md#get_deleter_function)|Получение метода удаления из `shared_ptr`.|  
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|Возвращает тип безопасности указателя, подразумеваемый любым сборщиком мусора.|  
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|Выделяет временное хранилище для последовательности элементов, которая не превышает заданное число элементов.|  
|[make_shared](../standard-library/memory-functions.md#make_shared)|Создает и возвращает `shared_ptr`, указывающий на объект, для которого выделена память, созданный из нуля или нескольких аргументов с помощью распределителя по умолчанию.|  
|[make_unique](../standard-library/memory-functions.md#make_unique)|Создает и возвращает [unique_ptr](../standard-library/unique-ptr-class.md), указывающий на выделенный объект, созданный из нуля или нескольких аргументов.|  
|[owner_less](../standard-library/memory-functions.md#owner_less)|Разрешает смешанные сравнения общих и слабых указателей на основе собственности.|  
|[pointer_safety](../standard-library/memory-enums.md#pointer_safety_enumeration)|Перечисление всех возможных возвращаемых значений для `get_pointer_safety`.|  
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|Отменяет выделение временной памяти, выделенной с помощью функции шаблона `get_temporary_buffer`.|  
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|Статическое приведение к `shared_ptr`.|  
|[swap](../standard-library/memory-functions.md#swap)|Обмен двух объектов `shared_ptr` или `weak_ptr`.|  
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|Сообщает сборщику мусора, что символы в блоке памяти, определенном указателем на базовый адрес и размером блока, теперь могут содержать трассируемые указатели.|  
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|Уведомляет `garbage_collector`, что указанная область памяти является недоступной.|  
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|Копирует объекты из указанного входного диапазона в неинициализированный конечный диапазон.|  
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|Создает копию заданного числа элементов из итератора ввода. Копии помещаются в прямой итератор.|  
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|Копирует объекты с указанным значением в неинициализированный конечный диапазон.|  
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|Копирует объекты с указанным значением в указанное число элементов в неинициализированном конечном диапазоне.|  
  
### <a name="operators"></a>Операторы  
  
|||  
|-|-|  
|[оператор!=](../standard-library/memory-operators.md#operator_neq)|Проверяет на неравенство между объектами распределителя указанного класса.|  
|[оператор==](../standard-library/memory-operators.md#operator_eq_eq)|Проверяет на равенство объекты распределителя указанного класса.|  
|[оператор>=](../standard-library/memory-operators.md#operator_gt__eq)|Проверяет, является ли один объект распределителя больше или равным второму объекту распределителя указанного класса.|  
|[оператор<](../standard-library/memory-operators.md#operator_lt_)|Проверяет, является ли один объект распределителя меньше или равным второму объекту распределителя указанного класса.|  
|[оператор\<=](../standard-library/memory-operators.md#operator_lt__eq)|Проверяет, является ли один объект меньше или равным второму объекту указанного класса.|  
|[оператор>](../standard-library/memory-operators.md#operator_gt_)|Проверяет, является ли один объект больше второго объекта указанного класса.|  
|[оператор<<](../standard-library/memory-operators.md#operator_lt__lt_)|Вставляет `shared_ptr`.|  
  
### <a name="classes"></a>Классы  
  
|||  
|-|-|  
|[allocator](../standard-library/allocator-class.md)|Класс шаблона описывает объект, который управляет выделением и освобождением памяти для массивов объектов типа **тип**.|  
|[allocator_traits](../standard-library/allocator-traits-class.md)|Описывает объект, определяющий все сведения, необходимые контейнеру с распределителем.|  
|[auto_ptr](../standard-library/auto-ptr-class.md)|Класс шаблона описывает объект, в котором хранится указатель на объект типа **Type \***, для которого выделена память, гарантирующий, что объект, на который он указывает, удаляется при удалении элемента auto_ptr, в который он входит.|  
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|Сообщает о необрабатываемом исключении weak_ptr.|  
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|Помогает сформировать `shared_ptr`.|  
|[pointer_traits](../standard-library/pointer-traits-struct.md)|Предоставляет данные, необходимые объекту класса шаблонов `allocator_traits` для описания распределителя с типом указателя `Ptr`.|  
|[raw_storage_iterator](../standard-library/raw-storage-iterator-class.md)|Класс-адаптер, который предоставляется, чтобы алгоритмы могли сохранять свои результаты в неинициализированной памяти.|  
|[shared_ptr](../standard-library/shared-ptr-class.md)|Помещает объект с динамическим выделением памяти в оболочку интеллектуального указателя с подсчитанными ссылками.|  
|[unique_ptr](../standard-library/unique-ptr-class.md)|Хранит указатель на собственный объект. Указатель не принадлежит никаким другим `unique_ptr`. `unique_ptr` удаляется при удалении владельца.|  
|[weak_ptr](../standard-library/weak-ptr-class.md)|Создает оболочку слабо связанного указателя.|  
  
### <a name="specializations"></a>Специализации  
  
|||  
|-|-|  
|[allocator\<void>](../standard-library/allocator-void-class.md)|Специализация распределителя класса шаблона для типа void, определяющая только типы членов, имеющие смысл в данном специализированном контексте.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)   
 [Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



