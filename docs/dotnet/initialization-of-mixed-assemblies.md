---
title: "Инициализация смешанных сборок | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 843b7a6e10e7814f4f922297b94b3ffe523dc0ad
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="initialization-of-mixed-assemblies"></a>Инициализация смешанных сборок
До Visual Studio 2005, библиотеки DLL, скомпилированные с **/CLR** могут произвольным образом взаимоблокировки при загрузке; эта проблема была вызвана смешанных DLL загрузки или загрузчик блокировки проблему. Почти все недетерминированные ситуации при загрузке смешанных библиотек DLL исключены. Однако остаются несколько определенных случаев, в которых может произойти блокировка загрузчика. Дополнительные сведения об этой проблеме см. в разделе "Проблема при загрузке смешанных библиотек DLL" в [библиотеке MSDN](http://go.microsoft.com/fwlink/?linkid=556).  
  
 Код в [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583) не должен иметь доступа к среде CLR. Это означает, что функция `DllMain` не должна вызывать управляемые функции напрямую или косвенно. В функции `DllMain`запрещается объявлять или реализовывать неуправляемый код. В функции `DllMain`запрещается выполнять сборку мусора или автоматическую загрузку библиотек.  
  
> [!NOTE]
>  В Visual C++ 2003 предоставлен файл _vcclrit.h для упрощения инициализации библиотеки DLL с минимальным риском возникновения взаимоблокировки. Больше нет необходимости использовать файл _vcclrit.h, а если он все же используется, то во время компиляции выдаются предупреждения об устаревшей версии. Рекомендуемая стратегия заключается в удалении зависимостей от этого файла в соответствии с процедурой, описанной в разделе [Removing Deprecated Header File _vcclrit.h](http://msdn.microsoft.com/en-us/7881993e-431d-43e9-8c6d-0d2285a4882d). Менее подходящее решение состоит в подавлении предупреждений с помощью объявления `_CRT_VCCLRIT_NO_DEPRECATE` перед включением файла _vcclrit.h или в простом пропуске предупреждений.  
  
## <a name="causes-of-loader-lock"></a>Причины блокировки загрузчика  
 После введения платформы .NET появились два механизма загрузки исполняемых модулей (EXE или DLL): один для Windows, который используется для неуправляемых модулей, и другой для среды CLR .NET, загружающий сборки .NET. Проблема загрузки смешанных библиотек DLL касается загрузчика ОС Microsoft Windows.  
  
 Если в процесс загружается сборка, содержащая только конструкции .NET, загрузчик CLR сам может выполнить все необходимые задачи загрузки и инициализации. Однако для смешанных сборок, поскольку они могут содержать машинный код и неуправляемые данные, необходимо использовать и загрузчик Windows.  
  
 Загрузчик Windows гарантирует, что никакая часть кода не получит доступ к коду или данным в этой библиотеке DLL перед тем, как она будет инициализирована, и что никакая часть кода не сможет загрузить DLL, если она частично инициализирована. Для этого загрузчик Windows использует глобальный для всего процесса критический раздел (часто называемый "блокировкой загрузчика"), предотвращающий небезопасное обращение во время инициализации модуля. В результате процесс загрузки является уязвимым для многих случаев взаимоблокировки. Для смешанных сборок следующие две ситуации повышают риск взаимоблокировки.  
  
-   Первая ситуация возникает, если пользователи пытаются выполнить функции, скомпилированные в код MSIL, во время блокировки загрузчика (например, в функции `DllMain` или в статических инициализаторах) — это может вызвать взаимоблокировку. Рассмотрим случай, в котором функция MSIL ссылается на тип в еще не загруженной сборке. Среда CLR пытается автоматически загрузить эту сборку, а для этого может потребоваться установить блокировку загрузчика Windows. Поскольку в коде, вызванном ранее, уже происходит блокировка загрузчика, это вызывает взаимоблокировку. Однако выполнение функции MSIL во время блокировки не обязательно приводит к появлению взаимоблокировки, поэтому данную ситуацию трудно диагностировать и исправить. При некоторых обстоятельствах, например если библиотека DLL ссылочного типа и все зависимые от нее модули не содержат неуправляемых конструкций, для загрузки сборки .NET ссылочного типа загрузчик Windows не требуется. Кроме того, требуемая сборка или ее зависимые смешанные неуправляемые модули или модули .NET могли быть загружены другим кодом. Следовательно, взаимоблокировку трудно прогнозировать и вероятность ее возникновения зависит от конфигурации целевого компьютера.  
  
-   Вторая ситуация происходит при загрузке библиотек DLL на платформе .NET Framework версии 1.0 и 1.1, когда среда CLR предполагает, что блокировка загрузчика не используется, и выполняет несколько действий, которые являются недопустимыми во время блокировки загрузчика. Предположение об отсутствии блокировки загрузчика верно только для чистых DLL-библиотек .NET, тогда как смешанные библиотеки DLL выполняют неуправляемые процедуры инициализации, для которых требуется загрузчик Windows и, следовательно, блокировка загрузчика. Как следствие, даже если разработчик не пытается выполнить какие-либо функции MSIL во время инициализации библиотеки DLL, все равно есть небольшая вероятность возникновения взаимоблокировки для платформы .NET Framework версии 1.0 и 1.1.  
  
 Все недетерминированные ситуации при загрузке смешанных библиотек DLL исключены. Этого удалось достигнуть за счет следующих изменений.  
  
-   Среда CLR больше не делает ложных предположений при загрузке смешанных DLL.  
  
-   Неуправляемая и управляемая инициализация выполняются на двух отдельных этапах. Сначала выполняется неуправляемая инициализация (через DllMain), а управляемая инициализация выполняется после с помощью поддерживаемой .NET конструкции *.cctor*. Последняя конструкция полностью прозрачная для пользователей, если только не используется параметр **/Zl** или **/NODEFAULTLIB** . Дополнительные сведения см. в разделах[/NODEFAULTLIB (Ignore Libraries)](../build/reference/nodefaultlib-ignore-libraries.md) и [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md) .  
  
 Блокировка загрузчика все равно может произойти, но теперь эти случаи можно воспроизвести и обнаружить. Если функция DllMain содержит инструкции MSIL, компилятор выдаст предупреждение [Compiler Warning (level 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md). Кроме того, либо библиотека CRT, либо среда CLR попытаются определить случаи выполнения функций MSIL во время блокировки загрузчика и сообщат о них, если такие были. Если библиотека CRT обнаруживает попытку, выдается ошибка во время выполнения C R6033  
  
 В остальной части этого документа описываются другие случаи выполнения MSIL при блокировке загрузчика, решения для устранения проблем в каждой их этих ситуаций и методы отладки.  
  
## <a name="scenarios-and-workarounds"></a>Ситуации и способы решения проблем  
 Существует несколько ситуаций, в которых пользовательский код может выполнять функции MSIL во время блокировки загрузчика. Разработчик должен убедиться, что в реализации пользовательского кода не предпринимаются попытки выполнить инструкции MSIL в ситуациях, описанных ниже. В следующих подразделах описываются все возможные ситуации, а также способы решения распространенных проблем.  
  
-   `DllMain`  
  
-   Статические инициализаторы  
  
-   Пользовательские функции, влияющие на автозагрузку  
  
-   Пользовательские языковые стандарты  
  
### <a name="dllmain"></a>DllMain  
 Функция `DllMain` — это определяемая пользователем точка входа для библиотеки DLL. Если пользователь не указывает иное, функция `DllMain` вызывается каждый раз, когда процесс или поток присоединяется к библиотеке DLL или отсоединяется от нее. Поскольку подобный вызов может произойти во время блокировки загрузчика, запрещается компилировать пользовательские функции `DllMain` в код MSIL. Кроме того, в MSIL нельзя скомпилировать никакую функцию в дереве вызовов с корнем `DllMain` . Для решения этой проблемы блок кода, в котором задается функция `DllMain` , необходимо изменить с помощью директивы #pragma `unmanaged`. То же необходимо сделать для каждой функции, которая вызывается в `DllMain` .  
  
 В случаях, когда эти функции должны вызывать функцию, для которой требуется MSIL-реализация для вызова другого контекста, можно использовать стратегию дупликации, согласно которой создается версия .NET и неуправляемая версия одной функции.  
  
 Кроме того, если функция `DllMain` не требуется или если она не выполняется при блокировке загрузчика, можно удалить пользовательскую реализацию функции `DllMain` , что решит проблему.  
  
 Если DllMain пытается выполнить код MSIL напрямую, выдается [Compiler Warning (level 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) . Однако компилятор не может обнаружить ситуации, в которых DllMain вызывает функцию в другом модуле, который, в свою очередь, пытается выполнить код MSIL.  
  
 Дополнительные сведения об этой ситуации см. в разделе "Трудности при диагностике".  
  
### <a name="initializing-static-objects"></a>Инициализация статических объектов  
 Инициализация статических объектов может вызвать взаимоблокировку, если требуется динамический инициализатор. В простых случаях, например когда статической переменной просто присваивается значение, известное на время компиляции, динамическая инициализация не требуется, поэтому нет риска возникновения взаимоблокировки. Однако для статических переменных, инициализируемых при вызове функции, конструктора или инициализируемых выражениями, значения которых получить во время компиляции невозможно, необходимо выполнять код во время инициализации модуля.  
  
 В коде, приведенном ниже, показаны примеры статических инициализаторов, для которых требуется динамическая инициализация: вызов функции, конструирование объекта и инициализация указателя. (Эти примеры не статические, но предполагается, что определены глобально, что дает тот же результат.)  
  
```  
// dynamic initializer function generated  
int a = init();  
CObject o(arg1, arg2);    
CObject* op = new CObject(arg1, arg2);  
```  
  
 Возможность возникновения взаимоблокировки зависит от того, скомпилирован ли содержащий модуль с использованием параметра **/clr** и будет ли выполняться код MSIL. Так, если статическая переменная скомпилирована без использования параметра **/clr** (или если она расположена в блоке #pragma `unmanaged` ) и для ее инициализации требуется динамический инициализатор, это может привести к выполнению инструкций MSIL и, как следствие, вызвать взаимоблокировку. Это происходит потому, что для модулей, скомпилированных без использования параметра **/clr**, инициализацию статических переменных выполняет функция DllMain. Напротив, статические переменные, скомпилированные с использованием **/clr** , инициализируются конструкцией .cctor после того, как этап неуправляемой инициализации завершен, а блокировка загрузчика отключена.  
  
 Существует несколько способов предотвратить взаимоблокировку, вызванную динамической инициализацией статических переменных (ниже они приблизительно упорядочены по времени, необходимому для решения проблемы).  
  
-   Исходный файл, содержащий статическую переменную, можно скомпилировать с использованием параметра **/clr**.  
  
-   Все функции, вызываемые статической переменной, можно скомпилировать в машинный код с помощью директивы #pragma `unmanaged` .  
  
-   Можно вручную клонируйте код, от которого зависит статическая переменная, создав версию .NET и неуправляемую версию с разными именами. Разработчики могут затем вызвать собственную версию из неуправляемых статических инициализаторов и вызывать версию .NET в других случаях.  
  
### <a name="user-supplied-functions-affecting-startup"></a>Пользовательские функции, влияющие на автозагрузку  
 Существует несколько пользовательских функций, от которых зависит инициализация библиотек при автозагрузке. Например, при глобальной перегрузке операторов C++, таких как `new` и `delete` операторы, пользовательские версии используются повсеместно, включая стандартной библиотеки C++ инициализацию и уничтожение. В результате все предоставленные пользователем версии этих операторов будет вызывать пользователя статические инициализаторы и стандартной библиотеки C++.  
  
 Если они скомпилированы в код MSIL, эти инициализаторы пытаются выполнить инструкции MSIL во время блокировки загрузчика. Перегрузка функции выделения памяти malloc приводит к тем же результатам. Для решения этой проблемы все подобные перегрузки или пользовательские определения необходимо реализовать в машинном коде с помощью директивы #pragma `unmanaged` .  
  
 Дополнительные сведения об этой ситуации см. в разделе "Трудности при диагностике".  
  
### <a name="custom-locales"></a>Пользовательские языковые стандарты  
 Если пользователь применяет глобальный пользовательский языковой стандарт, он используется для инициализации всех будущих потоков ввода-вывода, включая статически инициализируемые потоки. Если объект глобального языкового стандарта скомпилирован в код MSIL, функции элемента этого объекта, скомпилированные в MSIL, могут быть вызваны во время блокировки загрузчика.  
  
 Существует три способа решения этой проблемы.  
  
 Исходные файлы, содержащие все глобальные определения потока ввода-вывода, можно скомпилировать с использованием параметра **/clr** . Это предотвратит выполнение статической инициализации во время блокировки загрузчика.  
  
 Определения функций пользовательского языкового стандарта можно скомпилировать в машинный код с помощью директивы #pragma `unmanaged` .  
  
 Рекомендуется устанавливать пользовательский языковой стандарт как глобальный языковой стандарт только после отключения блокировки загрузчика. Затем следует явно настроить потоки ввода-вывода, созданные во время инициализации с использованием пользовательского языкового стандарта.  
  
## <a name="impediments-to-diagnosis"></a>Трудности при диагностике  
 В некоторых случаях сложно обнаружить источник взаимоблокировки. В следующих подразделах описываются эти случаи и способы решения возникающих проблем.  
  
### <a name="implementation-in-headers"></a>Реализация в заголовках  
 В некоторых случаях реализация функций в файлах заголовка может затруднить диагностику. Для встроенных функций и кода шаблона требуется, чтобы функции были заданы в файле заголовка.  Язык C++ указывает "правило одного определения", которое говорит о том, что все реализации функций с одинаковым именем должны быть семантически эквивалентны. Как следствие, компоновщику C++ не требуются особые предосторожности при слиянии объектных файлов с дублированными реализациями определенной функции.  
  
 До Visual Studio 2005 компоновщик просто выбирает самое большое из этих семантически эквивалентных определений, чтобы использовать упреждающие объявления и различные параметры оптимизации для разных исходных файлов. Это создает проблему для смешанных библиотек DLL.  
  
 Поскольку один и тот же заголовок может быть включен файлами CPP как с включенным, так и с отключенным параметром **/clr** или блок директивы #include может быть размещен в блоке #pragma `unmanaged` , для функций, реализованных в заголовке, возможно одновременное существование версии MSIL и версии в машинном коде. Эти реализации обладают различной семантикой по отношению к инициализации во время блокировки загрузчика, что нарушает правило одного определения. Как следствие, когда компоновщик выбирает самую большую реализацию, он может выбрать MSIL-реализацию функции, даже если она была явно скомпилирована в машинный код в другой части кода с помощью директивы #pragma unmanaged. Для предотвращения вызова MSIL-версии встроенной функции или шаблона во время блокировки загрузчика в каждое определение подобной функции, вызываемой во время блокировки загрузчика, необходимо добавить директиву #pragma `unmanaged` . Если файл заголовка предоставлен сторонним поставщиком, самый простой способ сделать это — поместить директиву #pragma unmanaged в стек и восстановить ее из стека вокруг директивы #include файла заголовка, вызывающего проблему. (См. [управляемые, неуправляемые](../preprocessor/managed-unmanaged.md) в качестве примера.) Однако этот метод не действует для заголовков, содержащих другой код, который напрямую вызывает API-интерфейсы .NET.  
  
 Для удобства пользователей, решающих проблему блокировку загрузчика, компоновщик выбирает реализацию на машинном, а не управляемом коде, если существует две версии реализации.  Это позволяет предотвратить проблемы, описанные выше.  Однако в этой версии существуют два исключения из этого правила из-за двух нерешенных проблем компилятора.  
  
-   Вызов встроенной функции происходит через указатель глобальной статической функции.  Эта ситуация важна, так как виртуальные функции вызываются через указатели глобальной функции.  Например:  
  
```  
#include "definesmyObject.h"  
#include "definesclassC.h"  
  
typedef void (*function_pointer_t)();  
  
function_pointer_t myObject_p = &myObject;  
  
#pragma unmanaged  
void DuringLoaderlock(C & c)  
{  
    // Either of these calls could resolve to a managed implementation,   
    // at link-time, even if a native implementation also exists.  
    c.VirtualMember();  
    myObject_p();  
}  
```  
  
-   В компиляции для платформы Itanium присутствует ошибка в реализации всех указателей функции.  В предыдущем примере, если myObject_p задано локально внутри during_loaderlock(), вызов также может разрешить в управляемую реализацию.  
  
### <a name="diagnosing-in-debug-mode"></a>Диагностика в режиме отладки  
 Вся диагностика проблем блокировки загрузчика должна проходить в отладочных построениях. В сборках выпуска диагностика может не дать результатов, а оптимизация в режиме выпуска может скрыть некоторые вызовы MSIL во время блокировки загрузчика.  
  
## <a name="how-to-debug-loader-lock-issues"></a>Отладка проблем при блокировке загрузчика  
 Диагностика, которую создает среда CLR при вызове функции MSIL, приводит к тому, что CLR приостанавливает выполнение. Это, в свою очередь, приводит к тому, что отладчик смешанного режима Visual C++ также приостанавливает выполнение отлаживаемого кода. Однако при присоединении к процессу невозможно получить управляемый стек вызовов для отлаживаемого кода с помощью смешанного отладчика.  
  
 Чтобы определить конкретную функцию MSIL, вызванную во время блокировки загрузчика, разработчики должны выполнить следующие действия.  
  
1.  Убедитесь, что доступны символы для библиотек mscoree.dll и mscorwks.dll.  
  
     Это можно сделать двумя способами. Первый способ заключается в том, что PDB-файлы для библиотек mscoree.dll и mscorwks.dll можно добавить к пути поиска. Для этого откройте диалоговое окно параметров пути поиска символов. (В меню "Сервис" выберите "Параметры". В левой части диалогового окна "Параметры" раскройте узел "Отладка" и выберите "Символы".) Добавьте путь к PDB-файлам библиотек mscoree.dll и mscorwks.dll в список поиска. Эти файлы устанавливаются в каталог % VSINSTALLDIR%\SDK\v2.0\symbols. Нажмите кнопку ОК.  
  
     Второй способ заключается в том, что PDB-файлы для mscoree.dll и mscorwks.dll можно загрузить с сервера символов Майкрософт. Для настройки сервера символов откройте диалоговое окно параметров пути поиска символов. (В меню "Сервис" выберите "Параметры". В левой части диалогового окна "Параметры" раскройте узел "Отладка" и выберите "Символы".) Добавить следующий путь в список поиска: http://msdl.microsoft.com/download/symbols. Добавьте каталог кэша символов в текстовом поле кэша сервера символов. Нажмите кнопку ОК.  
  
2.  Для отладчика установите режим отладки только машинного кода.  
  
     Для этого откройте сетку "Свойства" для автозагружаемого проекта в решении. В поддереве "Свойства конфигурации" выберите узел "Отладка". В поле "Тип отладчика" выберите пункт "Только машинный код".  
  
3.  Запустите отладчик (F5).  
  
4.  После создания диагностики **/clr** нажмите кнопку "Повторить", а затем нажмите кнопку "Прервать".  
  
5.  Откройте окно "Стек вызовов". (В меню "Отладка" выделите пункт "Окна" и выберите команду "Стек вызовов".) Если функция `DllMain` или статический инициализатор отмечаются зеленой стрелкой. Если функция, вызывающая неполадки, не определена, необходимо выполнить следующие действия, чтобы найти ее.  
  
6.  Откройте окно интерпретации (в меню "Отладка" выделите пункт "Окна", а затем выберите "Интерпретация").  
  
7.  Введите ".load.sos.dll" в окне интерпретации, чтобы загрузить службу отладки SOS.  
  
8.  Введите "!dumpstack" в окне интерпретации, чтобы получить полный текст стека **/clr** .  
  
9. Найдите первый экземпляр (самый близкий ко дну стека) _CorDllMain (если проблему вызывает функция `DllMain` ) или первый экземпляр _VTableBootstrapThunkInitHelperStub или GetTargetForVTableEntry (если проблему вызывает статический инициализатор).  Запись в стеке сразу под этим вызовом является вызовом функции, реализованной в коде MSIL, которая была вызвана во время блокировки загрузчика.  
  
10. Перейдите к строке файла исходного кода, определенной на шаге 9, и исправьте проблему, как описано в разделе "Ситуации".  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание  
 В следующем примере показано, как избежать блокировки загрузчика, переместив код из функции DllMain в конструктор глобального объекта.  
  
 В этом примере используется глобальный управляемый объект, чей конструктор содержит управляемый объект, первоначально располагающийся в DllMain. Во второй части примера присутствует ссылка на сборку, создание экземпляра управляемого объекта для вызова конструктора модуля, который производит инициализацию.  
  
### <a name="code"></a>Код  
  
```  
// initializing_mixed_assemblies.cpp  
// compile with: /clr /LD   
#pragma once  
#include <stdio.h>  
#include <windows.h>  
struct __declspec(dllexport) A {  
   A() {  
      System::Console::WriteLine("Module ctor initializing based on global instance of class.\n");  
   }  
  
   void Test() {  
      printf_s("Test called so linker does not throw away unused object.\n");  
   }  
};  
  
#pragma unmanaged  
// Global instance of object  
A obj;  
  
extern "C"  
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved) {  
   // Remove all managed code from here and put it in constructor of A.  
   return true;  
}  
```  
  
## <a name="example"></a>Пример  
  
### <a name="code"></a>Код  
  
```  
// initializing_mixed_assemblies_2.cpp  
// compile with: /clr initializing_mixed_assemblies.lib  
#include <windows.h>  
using namespace System;  
#include <stdio.h>  
#using "initializing_mixed_assemblies.dll"  
struct __declspec(dllimport) A {  
   void Test();  
};  
  
int main() {  
   A obj;  
   obj.Test();  
}  
```  
  
### <a name="output"></a>Вывод  
  
```  
Module ctor initializing based on global instance of class.  
  
Test called so linker does not throw away unused object.  
```  
  
## <a name="see-also"></a>См. также  
 [Смешанные (собственные и управляемые) сборки](../dotnet/mixed-native-and-managed-assemblies.md)