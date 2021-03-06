---
title: "Работа с потоками и маршалинг (C + +/ CX) | Документы Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- C4451
helpviewer_keywords:
- threading issues, C++/CX
- agility, C++/CX
- C++/CX, threading issues
ms.assetid: 83e9ca1d-5107-4194-ae6f-e01bd928c614
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9b1544f18d0d5206e178cf42705d9567fad2423c
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2018
---
# <a name="threading-and-marshaling-ccx"></a>Работа с потоками и маршалинг (C++/CX)
В большинстве случаев экземпляры классов среды выполнения Windows, как и стандартные объекты C++, может осуществляться из любого потока. Такие классы называются "гибкими". Тем не менее небольшое количество классов среды выполнения Windows, поставляемые с Windows не являются гибкими и должны использоваться скорее как COM-объектов, чем стандартные объекты C++. Для работы с негибкими классами не нужно быть специалистом по COM, однако нужно учитывать модель потоков классов и их механизмы маршалинга. В этой статье приведены общие сведения и инструкции по реализации редких сценариев, в которых приходится использовать экземпляры негибких классов.  
  
## <a name="threading-model-and-marshaling-behavior"></a>Модель потоков и механизмы маршалинга  
 Класс среды выполнения Windows может поддерживать одновременный доступ к потокам различными способами, что указывается двумя атрибутами, которые к нему применяются:  
  
-   Атрибут`ThreadingModel` может иметь одно из следующих значений: STA, MTA или Both, которые определены в перечислении `ThreadingModel` .  
  
-   Атрибут`MarshallingBehavior` может иметь одно из следующих значений: Agile, None или Standard, которые определены в перечислении `MarshallingType` .  
  
 Атрибут `ThreadingModel` определяет, где загружается класс при активации: только в контексте потока пользовательского интерфейса (STA), только в контексте фонового потока (MTA) или в контексте потока, создающего объект (Both). Значения атрибутов `MarshallingBehavior` определяют поведение объекта в контекстах различных потоков; в большинстве случаев не требуется подробно разбираться в этих значениях.  Среди классов, предоставляемых API Windows, около 90 процентов имеют значения атрибутов `ThreadingModel`=Both и `MarshallingType`=Agile. Это означает, что они могут обрабатывать низкоуровневые сведения потоков прозрачно и эффективно.   Если создать гибкий класс с помощью ключевого слова `ref new` , его методы можно из основного потока приложения или из одного или нескольких рабочих потоков.  Иначе говоря, гибкий класс можно использовать из любого места в коде, независимо от того, предоставляется ли он Windows или сторонними разработчиками. О потоковой модели класса и его поведении маршалинга можно не беспокоиться.  
  
## <a name="consuming-windows-runtime-components"></a>Использование компонентов среды выполнения Windows  
 При создании приложения универсальной платформы Windows, вы можете работать с гибкой и негибкими компонентами. При работе с негибкими компонентами может возникнуть следующее предупреждение.  
  
### <a name="compiler-warning-when-consuming-non-agile-classes-c4451"></a>Предупреждение компилятора при использовании негибких классов (C4451)  
 По различным причинам некоторые классы не могут быть гибкими. Если вы обращаетесь к экземплярам негибких классов и из потока пользовательского интерфейса, и из фонового потока, необходимо уделить особое внимание тому, чтобы обеспечить правильное поведение во время выполнения. Компилятор Visual C++ выдает предупреждение, если вы создаете экземпляр негибкого класса среды выполнения в приложении в глобальной области или объявляете негибкий тип как член класса в классе ссылки, который сам помечен как гибкий.  
  
 Из негибких классов проще всего работать с теми, у которых `ThreadingModel`=Both и `MarshallingType`=Standard.  Эти классы можно сделать гибкими с помощью вспомогательного класса `Agile<T>` .   В следующем примере показано объявление негибкого объекта типа `Windows::Security::Credentials::UI::CredentialPickerOptions^`и результирующее предупреждение компилятора.  
  
```  
  
ref class MyOptions  
    {  
    public:  
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options  
  
        {  
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()   
            {  
                return _myOptions;  
            }  
        }  
    private:  
        Windows::Security::Credentials::UI::CredentialPickerOptions^ _myOptions;  
    };  
```  
  
 Выдается следующее предупреждение:  
  
> `Warning 1 warning C4451: 'Platform::Agile<T>::_object' : Usage of ref class 'Windows::Security::Credentials::UI::CredentialPickerOptions' inside this context can lead to invalid marshaling of object across contexts. Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead`  
  
 При добавлении ссылки (в области членов или глобальной области) на объект, имеющий поведение маршалинга "Standard", компилятор выдает предупреждение, рекомендующее заключить этот тип в оболочку `Platform::Agile<T>`: `Consider using 'Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions>' instead` Если воспользоваться типом `Agile<T>`, класс можно будет использовать как любой другой гибкий класс. Используйте `Platform::Agile<T>` в следующих ситуациях:  
  
-   Негибкая переменная объявляется в глобальной области.  
  
-   Негибкая переменная объявляется в области класса, и существует возможность того, что код использует указатель в другом подразделении без надлежащего маршалинга.  
  
 Если ни одно из этих условий не выполняется, можно пометить содержащий класс как негибкий. Другими словами, вы должны непосредственно держите негибкие объекты только в негибких классов, а объекты с помощью Platform::Agile\<T > в гибких классах.  
  
 В следующем примере показано, как благодаря `Agile<T>` можно пропустить это предупреждение без последствий.  
  
```  
  
#include <agile.h>  
ref class MyOptions  
    {  
    public:  
        property Windows::Security::Credentials::UI::CredentialPickerOptions^ Options  
  
        {  
            Windows::Security::Credentials::UI::CredentialPickerOptions^ get()   
            {  
                return m_myOptions.Get();  
            }  
        }  
    private:  
        Platform::Agile<Windows::Security::Credentials::UI::CredentialPickerOptions^> m_myOptions;  
  
    };  
  
```  
  
 Обратите внимание, что `Agile` нельзя передавать в качестве возвращаемого значения или параметра в классе ссылки. Метод `Agile<T>::Get()` возвращает дескриптор объекта (^), который можно передать через границу интерфейса ABI в открытом методе или свойстве.  
  
 В Visual C++ при создании ссылки к классу среды выполнения Windows в процессе, имеющий поведение маршалинга «None», компилятор выдает предупреждение C4451, но не предлагает, с помощью `Platform::Agile<T>`.  Компилятор не может ничем помочь помимо этого предупреждения, поэтому вам необходимо самостоятельно обеспечить надлежащую работу класса и убедиться, что код вызывает компоненты однопотокового подразделения (STA) только из потока пользовательского интерфейса, а компоненты многопотокового подразделения (MTA) — только из фонового потока.  
  
## <a name="authoring-agile-windows-runtime-components"></a>Разработка гибких компонентов среды выполнения Windows  
 При определении ссылочного класса в C + +/ CX, он является объектом гибкой разработки по умолчанию — то есть `ThreadingModel`= Both и `MarshallingType`= Agile.  Если используется [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)], можно сделать класс гибким, унаследовав его класса `FtmBase`, использующего `FreeThreadedMarshaller`.  Создавая класс с атрибутами `ThreadingModel`=Both или `ThreadingModel`=MTA, убедитесь, что он является потокобезопасным. Дополнительные сведения см. в разделе [Создание и использование объектов (WRL)](http://msdn.microsoft.com/en-us/d5e42216-e888-4f1f-865a-b5ccd0def73e).  
  
 Потоковую модель и поведение маршалинга класса ссылки можно изменять. Однако если внести изменения, которые делают класс негибким, необходимо четко понимать их последствия.  
  
 В следующем примере показано, как применить `MarshalingBehavior` и `ThreadingModel` атрибуты для класса среды выполнения в библиотеке классов среды выполнения Windows. Если приложение использует библиотеку DLL и в нем активируется объект класса `ref new` с помощью ключевого слова `MySTAClass` , этот объект активируется в однопотоковом подразделении и не поддерживает маршалинг.  
  
```  
using namespace Windows::Foundation::Metadata;  
using namespace Platform;  
  
[Threading(ThreadingModel::STA)]  
[MarshalingBehavior(MarshalingType::None)]   
public ref class MySTAClass  
{  
};  
  
```  
 
 Незапечатанный класс должен иметь атрибуты маршалинга и потоковой модели, чтобы компилятор мог проверить, что производные классы имеют такие же значения этих атрибутов. Если эти параметры не заданы для класса явным образом, компилятор выдает ошибку и не выполняет компиляцию. Любой класс, производный от незапечатанного класса, выдает ошибку компилятора в каждом из следующих случаев:  
  
-   Атрибуты `ThreadingModel` и `MarshallingBehavior` не определены в производном классе.  
  
-   Значения атрибутов `ThreadingModel` и `MarshallingBehavior` в производном классе не соответствуют аналогичным атрибутам базового класса.  
  
 Работа с потоками и маршалинг сведения, которые требуются для компонента среды выполнения Windows сторонних указывается в регистрационных данных манифеста приложения для компонента. Рекомендуется делать все компоненты среды выполнения Windows agile. Это гарантирует, что клиентский код сможет вызывать компонент из любого потока приложения, и улучшает производительность таких вызовов, поскольку они являются прямыми вызовами без маршалирования. Если создать класс таким образом, клиентскому коду не придется применять `Platform::Agile<T>` , чтобы использовать этот класс.  
  
## <a name="see-also"></a>См. также  
 [ThreadingModel](http://msdn.microsoft.com/library/windows/apps/xaml/windows.foundation.metadata.threadingmodel.aspx)   
 [MarshallingBehavior](http://msdn.microsoft.com/library/windows/apps/xaml/windows.foundation.metadata.marshalingbehaviorattribute.aspx)