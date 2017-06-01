---
title: "Компилятора C3200 ошибки через C3299 | Документы Microsoft"
ms.custom: 
ms.date: 04/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3220
- C3221
- C3245
- C3249
- C3250
- C3256
- C3257
- C3258
- C3259
- C3260
- C3261
- C3263
- C3267
- C3281
- C3294
helpviewer_keywords:
- C3220
- C3221
- C3245
- C3249
- C3250
- C3256
- C3257
- C3258
- C3259
- C3260
- C3261
- C3263
- C3267
- C3281
- C3294
dev_langs:
- C++
ms.assetid: 6b3104f6-63bc-4823-b6f3-b8a16be4b87f
caps.latest.revision: 1
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: 1d63e4faaafe9ba208e17857a8ac60723c6c5cf5
ms.contentlocale: ru-ru
ms.lasthandoff: 04/24/2017

---
# <a name="compiler-errors-c3200-through-c3299"></a>Компилятора C3200 ошибки через C3299
Статьи из этой части документации содержат сведения о подразделе ошибок компилятора Visual C++. Информацию можно найти здесь, или можно выбрать номер ошибки в окне **Вывод** Visual Studio и нажать клавишу F1.  
  
> [!NOTE]
>  Не каждый [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] ошибки документируется в MSDN. Во многих случаях диагностическое сообщение предоставляет все информацию, которая доступна. Если вы считаете, что сообщение об ошибке требует дополнительного объяснения, сообщите нам об этом. Используйте форму обратной связи на этой странице или перейти к строке меню в Visual Studio и выберите **справки**, **сообщения об ошибке**, или вы можете отправить отчет предложений или ошибку на [Microsoft Connect](http://connect.microsoft.com/VisualStudio).  
  
 Может оказаться дополнительную помощь для ошибок и предупреждений на открытых форумах MSDN. [Языка Visual C++](http://go.microsoft.com/fwlink/?LinkId=158195) — форум для вопросов и обсуждения о [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] синтаксисом и компилятором языка. [Visual C++ Общие](http://go.microsoft.com/fwlink/?LinkId=158194) — форум для вопросов о [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] , которые не обсуждаются на других форумах. Кроме того, возможно справки об ошибках и предупреждения на [переполнения стека](http://stackoverflow.com/).  
  
|Ошибка|Сообщение|  
|-----------|-------------|  
|[Ошибка компилятора C3200](compiler-error-c3200.md)|"*тип*": недопустимый аргумент шаблона для параметра шаблона "*параметр*", требуется класс-шаблон|  
|[Ошибка компилятора C3201](compiler-error-c3201.md)|список параметров шаблона для шаблона класса "*шаблона*«не совпадает со списком параметров шаблона для параметра шаблона»*параметр*"|  
|[Ошибка компилятора C3202](compiler-error-c3202.md)|"*идентификатор*": недопустимое значение по умолчанию аргумента, требуется класс-шаблон|  
|[Ошибка компилятора C3203](compiler-error-c3203.md)|"*идентификатор*": Шаблон неспециализированного класса или универсальный не может использоваться как аргумент шаблона или универсального шаблона или универсального параметра "*параметр*", требуется действительный тип|  
|[Ошибка компилятора C3204](compiler-error-c3204.md)|"*функция*" не может вызываться из блока catch|  
|[Ошибка компилятора C3205](compiler-error-c3205.md)|список аргументов шаблона для параметра шаблона "*идентификатор*" отсутствует|  
|[Ошибка компилятора C3206](compiler-error-c3206.md)|"*функция*": недопустимый шаблона или универсального аргумента для "*шаблона*", отсутствует список аргументов шаблона или универсальный на шаблон класса или универсальный "*типа*"|  
|[Ошибка компилятора C3207](compiler-error-c3207.md)|"*функция*": недопустимый аргумент шаблона для "*параметр*", требуется класс шаблона|  
|[Ошибка компилятора C3208](compiler-error-c3208.md)|"*функция*": список параметров шаблона для шаблона класса "*шаблона*«не соответствует список параметров шаблона для параметра шаблона»*параметр*"|  
|[Ошибка компилятора C3209](compiler-error-c3209.md)|"*типа*": универсальный класс должен быть классом управляемого WinRT|  
|[Ошибка компилятора C3210](compiler-error-c3210.md)|"*идентификатор*": объявление уровня доступа может применяться только к члену базового класса|  
|[Ошибка компилятора C3211](compiler-error-c3211.md)|"*функция*": явная специализация с синтаксисом частичной специализации, вместо этого используйте <> шаблона|  
|[Ошибка компилятора C3212](compiler-error-c3212.md)|"*функция*": явная специализация члена шаблона должна быть членом явной специализации|  
|[Ошибка компилятора C3213](compiler-error-c3213.md)|базовый класс*класса*«является менее доступным, чем»*derived_class*"|  
|[Ошибка компилятора C3214](compiler-error-c3214.md)|"*аргумент*": недопустимый аргумент типа для универсального параметра "*параметр*«для универсального»*тип*", не соответствует ограничению "*ограничение*"|  
|[Ошибка компилятора C3215](compiler-error-c3215.md)|"*ограничение1*": параметр универсального типа, уже имеющимся ограничением "*ограничение2*"|  
|[Ошибка компилятора C3216](compiler-error-c3216.md)|ограничение должно быть универсальным параметром, а не "*типа*"|  
|[Ошибка компилятора C3217](compiler-error-c3217.md)|"*параметр*": универсальный параметр нельзя ограничить в этом объявлении|  
|[Ошибка компилятора C3218](compiler-error-c3218.md)|"*типа*": не допускается в качестве ограничения типа|  
|[Ошибка компилятора C3219](compiler-error-c3219.md)|"*параметр*": универсальный параметр нельзя ограничить несколькими не интерфейсами: "*типа*"|  
|C3220 ошибки компилятора|"*интерфейс*": интерфейс не может иметь progid|  
|C3221 ошибки компилятора|"*член*": несколько «default» и «case» атрибутов не допускается в качестве элемента|  
|[Ошибка компилятора C3222](compiler-error-c3222.md)|"*функция*": нельзя объявить аргументы по умолчанию для элемента, функции типа managed WinRT или универсальных функций|  
|[Ошибка компилятора C3223](compiler-error-c3223.md)|"*свойство*': 'typeid» нельзя применить к свойству|  
|[Ошибка компилятора C3224](compiler-error-c3224.md)|"*тип*": нет перегруженный универсальный класс не принимает*номер*"аргументов универсального типа|  
|[Ошибка компилятора C3225](compiler-error-c3225.md)|Аргумент универсального типа для "*аргумент*'не может быть»*типа*", он должен быть типом значения или дескриптором ссылочного типа|  
|[Ошибка компилятора C3226](compiler-error-c3226.md)|Объявление шаблона недопустимо внутри универсального объявления|  
|[Ошибка компилятора C3227](compiler-error-c3227.md)|"*тип*": невозможно использовать "*оператор*" для размещения универсального типа|  
|[Ошибка компилятора C3228](compiler-error-c3228.md)|"*функция*": аргумент универсального типа для "*аргумент*'не может быть»*типа*", он должен быть типом значения или тип дескриптора|  
|[Ошибка компилятора C3229](compiler-error-c3229.md)|"*типа*": косвенные обращения к параметру универсального типа не допускаются.|  
|[Ошибка компилятора C3230](compiler-error-c3230.md)|"*функция*": аргумент типа шаблона для "*аргумент*" не может содержать параметр универсального типа: "*типа*"|  
|[Ошибка компилятора C3231](compiler-error-c3231.md)|"*типа*": аргумент типа шаблона нельзя использовать параметр универсального типа|  
|[Ошибка компилятора C3232](compiler-error-c3232.md)|"*параметр*": параметр универсального типа не может использоваться в полном имени|  
|[Ошибка компилятора C3233](compiler-error-c3233.md)|"*типа*": параметр универсального типа уже ограничен|  
|[Ошибка компилятора C3234](compiler-error-c3234.md)|универсальный класс нельзя вывести из параметра универсального типа|  
|[Ошибка компилятора C3235](compiler-error-c3235.md)|"*специализации*": явная или частичная специализация универсального класса не допускается|  
|[Ошибка компилятора C3236](compiler-error-c3236.md)|явное создание экземпляра универсального класса не допускается|  
|[Ошибка компилятора C3237](compiler-error-c3237.md)|"*класс*": универсальный класс не может быть пользовательским атрибутом|  
|[Ошибка компилятора C3238](compiler-error-c3238.md)|"*тип*": тип с таким именем уже был переадресован в сборку "*сборки*"|  
|[Ошибка компилятора C3239](compiler-error-c3239.md)|"*типа*": указатель на внутренний или точечный указатель запрещается средой общеязыковая среда выполнения|  
|[Ошибка компилятора C3240](compiler-error-c3240.md)|"*идентификатор*": должен быть функцией неперегруженным абстрактный член "*типа*"|  
|[Ошибка компилятора C3241](compiler-error-c3241.md)|"*член*": этот метод не был введен "*интерфейс*"|  
|[Ошибка компилятора C3242](compiler-error-c3242.md)|"*функция*": виртуальные функции можно переопределять только явно|  
|[Ошибка компилятора C3243](compiler-error-c3243.md)|ни одна из функций перегрузки не была введена в "*интерфейс*"|  
|[Ошибка компилятора C3244](compiler-error-c3244.md)|"*член*": этот метод был создан "*интерфейс1*«не по»*interface2*"|  
|C3245 ошибки компилятора|"*функция*": использование шаблона переменной требуется список аргументов шаблона|  
|[Ошибка компилятора C3246](compiler-error-c3246.md)|"*класса*": не может наследовать от "*base_class*«как он объявлен как»*наследования*"|  
|[Ошибка компилятора C3247](compiler-error-c3247.md)|"*coclass*": компонентный класс не может наследовать от другого класса coclass*base_class*"|  
|[Ошибка компилятора C3248](compiler-error-c3248.md)|Является устаревшей. "*функция*": функция объявлена как «sealed» не может быть переопределено "*функция*"|  
|C3249 ошибки компилятора|недопустимый оператор или подвыражение для функции "constexpr"|  
|C3250 ошибки компилятора|"*объявление*": не допускается объявление в теле функции «constexpr»|  
|[Ошибка компилятора C3251](compiler-error-c3251.md)|нельзя вызвать метод базового класса для экземпляра типа значения|  
|[Ошибка компилятора C3252](compiler-error-c3252.md)|"*функция*": нельзя уменьшить доступность виртуального метода в типе managed WinRT|  
|[Ошибка компилятора C3253](compiler-error-c3253.md)|"*функция*": ошибка при явном переопределении|  
|[Ошибка компилятора C3254](compiler-error-c3254.md)|"*функция*": класс содержит явное переопределение "*функция*", но не является производным от интерфейса, содержащего объявление функции|  
|[Ошибка компилятора C3255](compiler-error-c3255.md)|"*типа*": не удается динамически выделить этот объект типа значения в собственной куче|  
|C3256 ошибки компилятора|"*функция*": использование переменной не создает константное выражение|  
|Ошибка компилятора C3257|Является устаревшей.|  
|C3258 ошибки компилятора|Является устаревшей.|  
|C3259 ошибки компилятора|в функциях "constexpr" может быть только один оператор return|  
|C3260 ошибки компилятора|"*маркера*": пропускаются непредвиденные токены перед тело лямбда-выражения|  
|C3261 ошибки компилятора|функции, возвращающей массив managed WinRT должны находиться скобки массива в конце объявления: "*идентификатор*(...) []'|  
|[Ошибка компилятора C3262](compiler-error-c3262.md)|Неправильная индексация массива: *номер* размерностей указано для *номер*-измерений "*типа*"|  
|C3263 ошибки компилятора|Является устаревшей.|  
|[Ошибка компилятора C3264](compiler-error-c3264.md)|"*идентификатор*": конструктор класса не может иметь тип возвращаемого значения|  
|[Ошибка компилятора C3265](compiler-error-c3265.md)|нельзя объявлять управляемый "*managed_construct*«в неуправляемый»*unmanaged_construct*"|  
|[Ошибка компилятора C3266](compiler-error-c3266.md)|"*функция*": конструктор класса должен иметь список параметров «void»|  
|Ошибка компилятора C3267|Является устаревшей.|  
|[Ошибка компилятора C3268](compiler-error-c3268.md)|"*функция*": универсальная функция или функция член универсального класса не может иметь переменный список параметров|  
|[Ошибка компилятора C3269](compiler-error-c3269.md)|"*функция*": функция член типа управляемых WinRT не может объявляться с помощью «...»|  
|[Ошибка компилятора C3270](compiler-error-c3270.md)|"*поле*": атрибут FieldOffset может использоваться только в контексте StructLayout(LayoutKind::Explicit)|  
|[Ошибка компилятора C3271](compiler-error-c3271.md)|"*поле*": недопустимое значение "*номер*" для атрибута FieldOffset|  
|[Ошибка компилятора C3272](compiler-error-c3272.md)|"*символ*": символу требуется атрибут FieldOffset, так как он входит структура или класс *type_name* определенным с помощью StructLayout(LayoutKind::Explicit)|  
|[Ошибка компилятора C3273](compiler-error-c3273.md)|"*ключевое слово*": не допускается для блока try C++|  
|[Ошибка компилятора C3274](compiler-error-c3274.md)|Наконец /\_\_finally без соответствующего try|  
|[Ошибка компилятора C3275](compiler-error-c3275.md)|"*идентификатор*": нельзя использовать этот символ без квалификатора|  
|[Ошибка компилятора C3276](compiler-error-c3276.md)|"*ключевое слово*": переходить из finally или\_\_наконец блок не определено поведение при обработке завершения|  
|[Ошибка компилятора C3277](compiler-error-c3277.md)|не удается определить неуправляемый enum "*перечисления*«внутри управляемых»*типа*"|  
|[Ошибка компилятора C3278](compiler-error-c3278.md)|прямой вызов метода интерфейса или чистого метода "*функция*" приведет к сбою во время выполнения|  
|[Ошибка компилятора C3279](compiler-error-c3279.md)|Частичные и явные специализации, а также явные создания экземпляров шаблонов классов, объявленные в пространстве имен CLI, запрещены|  
|[Ошибка компилятора C3280](compiler-error-c3280.md)|"*функция*": функция член управляемого типа нельзя скомпилировать как неуправляемую функцию|  
|Ошибка компилятора ошибка C3281|"*функция*": глобальный оператор не может иметь тип managed WinRT "*типа*" в сигнатуре|  
|[Ошибка компилятора C3282](compiler-error-c3282.md)|списки универсальных параметров могут использоваться только в managed WinRT классы, структуры или функции|  
|[Ошибка компилятора C3283](compiler-error-c3283.md)|"*интерфейс*": интерфейс не может иметь конструктор экземпляров|  
|[Ошибка компилятора C3284](compiler-error-c3284.md)|ограничения для универсального параметра "*параметр*«функции»*декларатор*«должны соответствовать ограничениям для универсального параметра»*параметр*«функции»*декларатор*"|  
|[Ошибка компилятора C3285](compiler-error-c3285.md)|для каждой инструкции не может работать с переменными типа "*типа*"|  
|[Ошибка компилятора C3286](compiler-error-c3286.md)|"*описатель*": переменной итерации не может иметь любой спецификаторов класса хранения|  
|[Ошибка компилятора C3287](compiler-error-c3287.md)|Тип "*типа*" (тип возвращаемого значения GetEnumerator) должен иметь соответствующую общую функцию член MoveNext и открытое свойство Current|  
|[Ошибка компилятора C3288](compiler-error-c3288.md)|"*типа*": недопустимая Отмена типа дескриптора|  
|[Ошибка компилятора C3289](compiler-error-c3289.md)|"*идентификатор*": тривиальное свойство нельзя индексировать|  
|[Ошибка компилятора C3290](compiler-error-c3290.md)|"*типа*": тривиальное свойство не может иметь ссылочный тип|  
|[Ошибка компилятора C3291](compiler-error-c3291.md)|default: не может быть именем тривиального свойства|  
|[Ошибка компилятора C3292](compiler-error-c3292.md)|пространство имен CLI нельзя открыть повторно|  
|[Ошибка компилятора C3293](compiler-error-c3293.md)|"*идентификатор*": используйте «default» для доступа к свойству по умолчанию (индексатору) для класса*класс*"|  
|Ошибка компилятора C3294|Является устаревшей.|  
|[Ошибка компилятора C3295](compiler-error-c3295.md)|"#pragma *описатель*" может использоваться только в глобальной или области видимости пространства имен|  
|[Ошибка компилятора C3296](compiler-error-c3296.md)|"*идентификатор*": свойство с таким именем уже существует.|  
|[Ошибка компилятора C3297](compiler-error-c3297.md)|" *ограничение2*": невозможно использовать " *ограничение1*" как ограничение так как " *ограничение1*" имеет ограничение значения|  
|[Ошибка компилятора C3298](compiler-error-c3298.md)|" *ограничение1*": невозможно использовать " *ограничение2*" как ограничение так как " *ограничение2*" имеет ограничение ссылки и " *ограничение1*" имеет ограничение значения|  
|[Ошибка компилятора C3299](compiler-error-c3299.md)|" *функция*": невозможно указать ограничения, они наследуются от базового метода|  
