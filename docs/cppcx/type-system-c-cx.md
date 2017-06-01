---
title: "Система типов (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
caps.latest.revision: 28
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 28
---
# Система типов (C++/CX)
С помощью архитектуры [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] можно использовать [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)], Visual Basic, Visual C\# и JavaScript для написания приложений и компонентов, которые напрямую обращаются к API Windows и взаимодействуют с другими приложениями и компонентами [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]. Приложения [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)], созданные на языке C\+\+, компилируются в машинный код, который выполняется непосредственно в ЦП. Приложения [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)], написанные на языке C\# или Visual Basic, компилируются в код на языке MSIL и выполняются в среде CLR. Приложения [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)], написанные на языке JavaScript, выполняются в среде выполнения. Сами компоненты операционной системы [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] пишутся на языке C\+\+ и выполняются как машинный код. Все эти компоненты и приложения [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] напрямую взаимодействуют через двоичный интерфейс приложений \(ABI\) [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].  
  
 Чтобы обеспечить поддержку [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] в новейшей идиоме C\+\+, корпорация Майкрософт создала [!INCLUDE[cppwrt](../cppcx/includes/cppwrt-md.md)] \([!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]\).[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] предоставляет встроенные базовые типы и реализации основных типов [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)], которые позволяют приложениям и компонентам C\+\+ взаимодействовать через интерфейс ABI с приложениями, написанными на других языках. Можно использовать любой тип [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] или создавать классы, структуры, интерфейсы и другие пользовательские типы, которые могут быть использованы другими приложениями и компонентами [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]. Приложение [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)], написанное на [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)], также может использовать обычные классы и структуры C\+\+, если доступ к ним не является открытым.  
  
 Подробное рассмотрение проекции языка C\+\+\/CX и принципов его работы приведено в следующих записях блогов:  
  
1.  [C\+\+\/CX: часть 0 из \[n\]. Введение](http://blogs.msdn.com/b/vcblog/archive/2012/08/29/cxxcxpart00anintroduction.aspx)  
  
2.  [C\+\+\/CX: часть 0 из \[n\]. Введение](http://blogs.msdn.com/b/vcblog/archive/2012/08/29/cxxcxpart00anintroduction.aspx)  
  
3.  [C\+\+\/CX: часть 2 из \[n\]. Типы с крышками](http://blogs.msdn.com/b/vcblog/archive/2012/09/17/cxxcxpart02typesthatwearhats.aspx)  
  
4.  [C\+\+\/CX: часть 3 из \[n\]. В разработке](http://blogs.msdn.com/b/vcblog/archive/2012/10/05/cxxcxpart03underconstruction.aspx)  
  
5.  [C\+\+\/CX: часть 4 из \[n\]. Статические функции\-члены](http://blogs.msdn.com/b/vcblog/archive/2012/10/19/cxxcxpart04staticmemberfunctions.aspx)  
  
## Файлы метаданных Windows \(WINMD\-файлы\)  
 При компилировании приложения [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)], написанного на языке C\+\+, компилятор создает исполняемый файл в машинном коде, а также создает отдельный файл метаданных Windows \(WINMD\), содержащий описания открытых типов [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)], которые включают классы, структуры, перечисления, интерфейсы, параметризованные интерфейсы и делегаты. Формат метаданных напоминает формат, используемый в сборках .NET Framework.  В компоненте C\+\+ WINMD\-файл содержит только метаданные; исполняемый код находится в отдельном файле. Тот же подход реализован для компонентов [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)], поставляемых вместе с Windows. Имя WINMD\-файла должно соответствовать корневому пространству имен в исходном коде или являться его префиксом. \(Для языков платформы .NET Framework WINMD\-файл содержит код и метаданные точно так же, как сборка .NET Framework.\)  
  
 Метаданные в WINMD\-файле представляют опубликованную область кода. Опубликованные типы являются видимыми для других приложений [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)], независимо от языка, на котором они написаны. Поэтому метаданные, или опубликованный код, могут содержать только типы, определенные системой типов [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]. Языковые конструкции, относящиеся к C\+\+, такие как обычные классы, массивы, шаблоны или контейнеры STL, не могут публиковаться в метаданных, поскольку клиентское приложение JavaScript или C\# не будет знать, что с ними делать.  
  
 Видимость типа или метода в метаданных зависит от применяемых к ним модификаторов доступа. Чтобы быть видимым, тип должен быть объявлен в пространстве имен как открытый тип. Класс ссылки, не являющийся открытым, можно использовать в коде как внутренний вспомогательный тип; он просто не отображается в метаданных. Даже в открытом классе ссылки не все члены будут обязательно видимыми. В следующей таблице перечислены отношения между спецификаторами доступа C\+\+ в открытом классе ссылки и видимостью метаданных [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]:  
  
|||  
|-|-|  
|**Опубликован в метаданных**|**Не опубликован в метаданных**|  
|public|private|  
|protected|internal|  
|public protected|private protected|  
  
 Для просмотра WINMD\-файлов можно использовать **обозреватель объектов**. Компоненты [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)], включенные в Windows, содержатся в файле Windows.winmd. Файл default.winmd содержит базовые типы, используемые в [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)], а файл platform.winmd содержит дополнительные типы из пространства имен Platform. По умолчанию эти три WINMD\-файла включены в каждый проекте C\+\+ для приложений [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)].  
  
> [!TIP]
>  Типы из [Пространство имен Platform::Collections](../cppcx/platform-collections-namespace.md) не отображаются в WINMD\-файле, поскольку они не являются открытыми. Они являются закрытыми особыми реализациями интерфейсов C\+\+, которые определены в `Windows::Foundation::Collections`. Приложение [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] написанные на языке JavaScript или C\#, не знает, что такое [Класс Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md), но этот класс может использовать интерфейс `Windows::Foundation::Collections::IVector`. Типы `Platform::Collections` определены в файле collection.h.  
  
## Система типов [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] в [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]  
 В следующих разделах описываются основные функции системы типов [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] и объясняется, как они поддерживаются в [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)].  
  
### Пространства имен  
 Все типы [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] должен быть объявлены в пространстве имен; сам интерфейс API Windows упорядочен по пространствам имен. WINMD\-файл должен иметь одно имя с корневым пространством имен. Например, экземпляр класса с именем A.B.C.MyClass может быть создан, только если он определен в файле метаданных с именем A.winmd, A.B.winmd или A.B.C.winmd. Имя DLL\-файла не обязательно должно соответствовать имени WINMD\-файла.  
  
 Сам интерфейс API Windows был переработан как хорошо организованная библиотека классов, упорядоченная по пространствам имен.  Все компоненты [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] объявляются в пространствах имен Windows.\*.  
  
 Дополнительные сведения см. в разделе [Пространства имен и видимость типов](../cppcx/namespaces-and-type-visibility-c-cx.md).  
  
### Базовые типы  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] определяет следующие базовые типы: UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, single, double, Char16, Boolean и String.[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] поддерживает базовые числовые типы в своем пространстве имен по умолчанию, например uint16, uint32, uint64, int16, int32, int64, float32, float64 и char16. Типы Boolean и String также определены в пространстве имен Platform.  
  
 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] также определяет тип uint8, эквивалентный типу `unsigned char`, который не поддерживается в [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] и не может использоваться в открытых интерфейсах API.  
  
 Фундаментальный тип можно сделать поддерживающим значение NULL, если поместить его в интерфейс [Platform::IBox](../cppcx/platform-ibox-interface.md). Дополнительные сведения см. в разделе [Классы и структуры значений](../cppcx/value-classes-and-structs-c-cx.md).  
  
 Дополнительные сведения о фундаментальных типах см. в разделе [Фундаментальные типы](../cppcx/fundamental-types-c-cx.md).  
  
### Строки  
 Строка [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] — это неизменяемая последовательность 16\-битовых символов ЮНИКОДА. Строка [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] проецируется как класс `Platform::String^`. Этот класс предоставляет методы для создания, обработки строк, а также для их преобразования в тип `wchar_t` и из этого типа.  
  
 Дополнительные сведения см. в разделе [Строки](../cppcx/strings-c-cx.md).  
  
### Массивы  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] поддерживает одномерные массивы любого типа. Массивы массивов не поддерживаются.  В [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] массивы [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] проецируются в качестве [Platform::Array \- класс](../cppcx/platform-array-class.md).  
  
 Дополнительные сведения см. в разделе [Классы Array и WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
### Классы и структуры ссылки  
 Класс [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] проецируется в [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] как класс или структура ссылки, поскольку они копируются по ссылке. Управление памятью для классов и структур ссылки прозрачно осуществляется посредством подсчета ссылок. Когда последняя ссылка на объект выходит из области, объект ликвидируется. Класс или структура ссылки:  
  
-   может содержать такие члены, как конструкторы, методы, свойства и события. Эти члены могут иметь модификаторы доступа public, private, protected или internal;  
  
-   могут содержать определения закрытых вложенных перечислений, структур или классов;  
  
-   могут напрямую наследовать от одного базового класса и реализовать любое число интерфейсов. Все классы ссылок неявно преобразуются в [Класс Platform::Object](../cppcx/platform-object-class.md) и могут переопределять его виртуальные методы, например [Object::ToString](../cppcx/object-tostring-method-c-cx.md).  
  
 Класс ссылки, имеющий открытый конструктор, необходимо объявить как запечатанный, чтобы запретить его дальнейшее наследование.  
  
 Дополнительные сведения см. в разделе [Классы и структуры ссылки](../cppcx/ref-classes-and-structs-c-cx.md).  
  
### Классы и структуры значения  
 Класс значения или структура значения представляет базовую структуру данных и содержит только поля, которые могут быть классами значений, структурами значений или типом `Platform::String^`.  Структуры и классы значения копируются по значению.  
  
 Структура значений может допускать значение NULL, если ее заключить в интерфейс IBox.  
  
 Дополнительные сведения см. в разделе [Классы и структуры значений](../cppcx/value-classes-and-structs-c-cx.md).  
  
### Разделяемые классы  
 Функция разделяемого класса позволяет определять один класс на несколько файлов. Она используется в основном для того, чтобы позволить средствам создания кода, таким как редактор XAML, изменить один файл, не внося корректив в редактируемый пользователем файл.  
  
 Дополнительные сведения см. в разделе [Разделяемые классы](../cppcx/partial-classes-c-cx.md).  
  
### Свойства  
 Свойство — это открытый элемент данных любого типа [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)], который реализуется в виде пары методов get и set. Клиентский код обращается к свойству, как если бы он был открытым полем. Свойство, для которого не требуется пользовательский код get или set, называется *тривиальным свойством*; его можно объявлять без явного указания методов get и set.  
  
 Дополнительные сведения см. в разделе [Свойства](../cppcx/properties-c-cx.md).  
  
### Коллекции [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] в [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)]  
 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] определяет набор интерфейсов для типов коллекций, которые каждый язык реализует собственным способом.[!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] предоставляет реализации в [Класс Platform::Collections::Vector](../cppcx/platform-collections-vector-class.md), [Класс Platform::Collections::Map](../cppcx/platform-collections-map-class.md) и других связанных конкретных типах коллекций, которые совместимы со своими аналогами из библиотеки стандартных шаблонов \(STL\).  
  
 Дополнительные сведения см. в разделе [Коллекции](../cppcx/collections-c-cx.md).  
  
### Классы ссылки шаблонов  
 Для закрытых и внутренних классов ссылок можно создавать шаблоны и задавать параметры.  
  
 Дополнительные сведения см. в разделе [Классы ссылки шаблонов](../cppcx/template-ref-classes-c-cx.md).  
  
### Интерфейсы  
 Интерфейс [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] определяет набор открытых свойств, методов и событий, которые должны реализовывать класс или структура ссылки, если они наследуют от интерфейса.  
  
 Дополнительные сведения см. в разделе [Интерфейсы](../cppcx/interfaces-c-cx.md).  
  
### Перечисления  
 Класс перечисления в [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] напоминает перечисление C\+\+ с областью видимости. Базовым типом является int32, если не применяется атрибут \[Flags\] — в этом случае базовым типом становится uint32.  
  
 Дополнительные сведения см. в разделе [Перечислимые типы](../cppcx/enums-c-cx.md).  
  
### Делегаты  
 Делегат в [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] аналогичен к объекту std::function в C\+\+. Это особый тип класса ссылки, который используется для вызова предоставляемых клиентом функций с совместимыми сигнатурами.  Делегаты наиболее часто используются в [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] в качестве типа события.  
  
 Дополнительные сведения см. в разделе [Делегаты](../cppcx/delegates-c-cx.md).  
  
### Исключения  
 В C \+\+\/CX можно перехватить пользовательские типы исключений, типы [std::exception](~/standard-library/exception-class.md) и [Platform::Exception](../cppcx/platform-exception-class.md).  
  
 Дополнительные сведения см. в разделе [Исключения](../cppcx/exceptions-c-cx.md).  
  
### События  
 Событие — открытый член класса или структуры ссылки, тип которого является типом делегата. Событие может вызываться — или инициироваться — только классом\-владельцем. Однако клиентский код может предоставить свои собственные функции, которые называются обработчиками событий и вызываются при инициировании события классом\-владельцем.  
  
 Дополнительные сведения см. в разделе [События](../cppcx/events-c-cx.md).  
  
### Приведение  
 C \+\+\/CX поддерживает стандартные операторы приведения типа [static\_cast](../cpp/static-cast-operator.md), [dynamic\_cast](../cpp/dynamic-cast-operator.md) и [reinterpret\_cast](../cpp/reinterpret-cast-operator.md), а также оператор [safe\_cast](~/windows/safe-cast-cpp-component-extensions.md), относящийся к C \+\+\/CX.  
  
 Дополнительные сведения см. в разделе [Приведение](../cppcx/casting-c-cx.md).  
  
### Упаковка  
 Упакованная переменная — это тип значения, упакованный в ссылочный тип в ситуациях, где требуется ссылочная семантика.  
  
 Дополнительные сведения см. в разделе [Упаковка](../cppcx/boxing-c-cx.md).  
  
### Атрибуты  
 Атрибут — это значение метаданных, которое можно применить к любому типу или члену типа [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]. Атрибуты можно проверять во время выполнения.[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] определяет набор общих атрибутов в пространстве имен `Windows::Foundation::Metadata`. Пользовательские атрибуты открытых интерфейсов не поддерживаются [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] в данном выпуске.  
  
## Включение API в список нерекомендуемых  
 Описывает, как пометить открытые API в качестве нерекомендуемых, с помощью тех же атрибутов, которые используются в системных типах [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)].  
  
 Дополнительные сведения см. в разделе [Перевод типов и членов в разряд нерекомендуемых](../cppcx/deprecating-types-and-members-c-cx.md).  
  
## См. также  
 [Справочник по языку C\+\+](../cppcx/visual-c-language-reference-c-cx.md)