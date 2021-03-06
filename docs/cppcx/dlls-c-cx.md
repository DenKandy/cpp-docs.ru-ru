---
title: "Библиотеки DLL (C + +/ CX) | Документы Microsoft"
ms.custom: 
ms.date: 02/06/2018
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 16b7ed16ec128f1fbf67d1b62e974ccd7ea5213b
ms.sourcegitcommit: a5a69d2dc3513261e9e28320e4e067aaf40d2ef2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2018
---
# <a name="dlls-ccx"></a>Библиотеки DLL (C++/CX)

Чтобы создать стандартную библиотеку DLL Win32 или компонент среды выполнения Windows, библиотеки DLL, которая может использоваться приложениями универсальной платформы Windows (UWP), можно использовать Visual Studio. Стандартная библиотека DLL, созданная с помощью версии Visual Studio или компилятор Visual C++, который раньше, чем Visual Studio 2012 не может правильно загружен в приложении UWP и не может передавать тест проверки приложения в Microsoft Store.

## <a name="windows-runtime-component-dlls"></a>DLL компонентов среды выполнения Windows

Почти во всех случаях, когда требуется создать DLL-ФАЙЛ для использования в приложении UWP, создайте его как компонента среды выполнения Windows с помощью шаблона проекта с тем же именем. Можно создать проект компонента среды выполнения Windows для библиотек DLL, содержащих открытые или закрытые типы среды выполнения Windows. Компонент среды выполнения Windows может осуществляться из приложений, написанных на любом языке, совместимом с среды выполнения Windows. По умолчанию в параметрах компилятора для компонента среды выполнения Windows в project используется **/zw** переключения. WINMD-файл должен иметь одно имя с корневым пространством имен. Например, экземпляр класса с именем A.B.C.MyClass может быть создан, только если он определен в файле метаданных с именем A.winmd, A.B.winmd или A.B.C.winmd. Имя DLL-файла не обязательно должно соответствовать имени WINMD-файла.

Дополнительные сведения см. в разделе [создание компонентов среды выполнения Windows в C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>Для ссылки на двоичный файл проекта компонента среды выполнения Windows сторонних разработчиков

1. Откройте контекстное меню для проекта, в котором будет использоваться библиотека DLL, и выберите пункт **Свойства**. На странице **Общие свойства** нажмите кнопку **Добавить новую ссылку** .

1. Компонент среды выполнения Windows состоит из DLL-файла и winmd-файл, содержащий метаданные. Обычно эти файлы расположены в одной и той же папке. В левой области диалогового окна **Добавление ссылки** нажмите кнопку **Обзор** и перейдите к расположению DLL-файла и его WINMD-файла. Дополнительные сведения см. в разделе [пакетов SDK расширений](/visualstudio/extensibility/creating-a-software-development-kit#ExtensionSDKs).

## <a name="standard-dlls"></a>Стандартные библиотеки DLL

Можно создать стандартную библиотеку DLL для кода C++, который не использовать или создавать открытые типы среды выполнения Windows и использовать его в приложении UWP. Используйте тип проекта библиотеки динамической компоновки (DLL), если нужно перенести существующую библиотеку DLL для компиляции в этой версии Visual Studio без конвертирования кода в проект компонента среды выполнения Windows. При выполнении следующих действий библиотека DLL будет развернута вместе с исполняемым файлом приложения в APPX-пакете.

### <a name="to-create-a-standard-dll-in-visual-studio"></a>Создание стандартной библиотеки DLL в Visual Studio

1. В строке меню выберите **файл**, **New**, **проекта**, а затем выберите **библиотеки динамических ссылок (DLL)** шаблона.

1. Введите имя проекта и нажмите кнопку **ОК** .

1. Добавьте код. Не забудьте добавить выражение `__declspec(dllexport)` для функций, которые планируется экспортировать, например `__declspec(dllexport) Add(int I, in j);`

1. Добавить `#include winapifamily.h` включить этот файл заголовка из Windows SDK для приложений UWP, и задайте макрос `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>Указание ссылки на проект стандартной библиотеки DLL из того же решения

1. Откройте контекстное меню для проекта, в котором будет использоваться библиотека DLL, и выберите пункт **Свойства**. На странице **Общие свойства** нажмите кнопку **Добавить новую ссылку** .

1. В левой области выберите **Решение**и установите соответствующий флажок в правой области.

1. В файлах исходного кода добавьте оператор `#include` для файла заголовков библиотеки DLL.

### <a name="to-reference-a-standard-dll-binary"></a>Указание ссылки на двоичный файл стандартной библиотеки DLL

1. Скопируйте DLL-файл, LIB-файл и файл заголовков в нужное расположение, например в папку текущего проекта.

1. Откройте контекстное меню для проекта, в котором будет использоваться библиотека DLL, и выберите пункт **Свойства**. На странице **Свойства конфигурации**&gt; **Компоновщик**&gt; **Ввод** добавьте LIB-файл в качестве зависимости.

1. В файлах исходного кода добавьте оператор `#include` для файла заголовков библиотеки DLL.

### <a name="to-migrate-an-existing-win32-dll-for-uwp-app-compatibility"></a>Чтобы перенести существующую библиотеку DLL Win32 для обеспечения совместимости приложений UWP

1. Создайте проект типа DLL (универсальные приложения Windows) и Добавление существующего исходного кода.

1. Добавить `#include winapifamily.h` включить этот файл заголовка из Windows SDK для приложений UWP, и задайте макрос `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

1. В файлах исходного кода добавьте оператор `#include` для файла заголовков библиотеки DLL.
