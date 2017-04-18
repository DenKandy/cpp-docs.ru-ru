---
title: "Элементы управления ActiveX в MFC. Лицензирование элемента управления ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COleObjectFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleObjectFactory - класс, элементы управления лицензированием"
  - "GetLicenseKey - метод"
  - "лицензирование элементов управления ActiveX"
  - "MFC ActiveX - элементы управления, лицензирование"
  - "VerifyLicenseKey - метод"
  - "VerifyUserLicense - метод"
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Элементы управления ActiveX в MFC. Лицензирование элемента управления ActiveX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Поддержка лицензирования, необязательная функция элементов управления ActiveX, позволяет элементу управления, который может использовать распределенные или элемент управления. \(Для дополнительного обсуждения проблем лицензирования вопросы лицензирования, см. в разделе [Обновление существующего элемента управления ActiveX](../Topic/Upgrading%20an%20Existing%20ActiveX%20Control.md)\).  
  
 В этой статье рассматриваются в следующих разделах:  
  
-   [Общие сведения о лицензировании элементов управления ActiveX](#_core_overview_of_activex_control_licensing)  
  
-   [Создание лицензированный элемент управления](#_core_creating_a_licensed_control)  
  
-   [Поддержка лицензирования](#_core_licensing_support)  
  
-   [Лицензирование настраивать элемент управления ActiveX](#_core_customizing_the_licensing_of_an_activex_control)  
  
 Элементы управления ActiveX, реализующие лицензирование позволяют разработчик элемента управления, чтобы определить, как другие пользователи смогут использовать элемент управления ActiveX.  Предоставить покупателя элементов управления с элементом управления и файлом РАСШИРЕНИЕ, с соглашением, что покупатель может быть распределен элемента управления, но не файлом РАСШИРЕНИЕ с приложением, которое использует элемент управления.  Это запрещает пользователям этого приложения из новых применений записи, использующих элементы управления, без предварительного лицензирования элемент управления пользователя.  
  
##  <a name="_core_overview_of_activex_control_licensing"></a> Общие сведения о лицензировании элементов управления ActiveX  
 Для обеспечения поддержки лицензирования для элементов управления ActiveX класс [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) предоставляет реализацию для нескольких функций в интерфейсе **IClassFactory2** : **IClassFactory2::RequestLicKey**, **IClassFactory2::GetLicInfo** и **IClassFactory2::CreateInstanceLic**.  Когда разработчик приложения выполняет запрос создание экземпляра элемента управления, к `GetLicInfo` вызывается, чтобы убедиться, что файл существует РАСШИРЕНИЕ элемента управления.  Если элемент управления лицензирован, экземпляр элемента управления можно создать и вносится в контейнере.  После того, как разработчик завершил вызов выполняется построение приложения контейнера, другой функции, это время в `RequestLicKey`.  Эта функция возвращает лицензионный ключ \(простая символьная строка\) в приложение\-контейнеру.  Возвращает ключ затем внедряется в приложении.  
  
 На рисунке ниже показана проверка на использование элементов управления ActiveX, который будет использоваться в процессе разработки приложения.  Как упоминалось ранее, разработчик приложения должен иметь правильный файл РАСШИРЕНИЕ, установленным на компьютере разработки для создания экземпляра элемента управления.  
  
 ![Лицензированный элемент управления ActiveX, проверяемый на этапе разработки](../mfc/media/vc374d1.png "vc374D1")  
Проверка лицензированного элемента управления ActiveX во время разработки  
  
 Следующий процесс, показанный на следующем рисунке, возникает, когда пользователь запускает приложение контейнера.  
  
 Когда приложение запущено, экземпляр элемента управления обычно должен быть создан.  Контейнер выполнить путем обращения к `CreateInstanceLic`, передав встроенный лицензионный ключ в качестве параметра.  Сравнение строк затем выполняется между внедренным лицензионным ключом и копией элементом управления собственного лицензионного ключа.  Если совпадение успешно, то экземпляр элемента управления будет создан и приложение продолжает выполняться обычным способом.  Обратите внимание, что файл РАСШИРЕНИЕ не должны присутствовать на компьютере пользователя элемента управления.  
  
 ![Лицензированный элемент управления ActiveX, проверяемый на этапе выполнения](../mfc/media/vc374d2.png "vc374D2")  
Проверка лицензированного элемента управления ActiveX во время выполнения  
  
 Лицензирование элемента управления состоит из 2 основных компонентов: определенный код в библиотеку DLL реализации элемента управления и файла лицензий.  Код состоит из 2 \(или 3\) по возможности вызова функции и символьной строки, с именем «строка» лицензии, содержащие сведения об авторских правах.  Эти вызовы и строка лицензии содержатся в файле реализации элемента управления \(CPP\).  Файл лицензии, созданный мастером элемента управления ActiveX, текстовый файл с выпиской информацию об авторских правах.  Он называется использовать имя проекта с расширением РАСШИРЕНИЕ, например SAMPLE.LIC.  Лицензированный элемент управления должен быть сопровожен файл лицензии, если необходимо использовать во время разработки.  
  
##  <a name="_core_creating_a_licensed_control"></a> Создание лицензированный элемент управления  
 При использовании мастера элементов управления ActiveX для создания элемента управления, платформа легко включить поддержку лицензирования.  При указании, что элемент управления должен иметь времени выполнения лицензию мастера элементов управления ActiveX, добавьте код в класс элемента управления в лицензированию поддержки.  Код состоит из функций, использующих файл ключа и лицензии для проверки лицензии.  Эти функции также можно изменить, чтобы настраивать лицензирование элемента управления.  Дополнительные сведения о настройке лицензии см. в подразделе [Лицензирование настраивать элемент управления ActiveX](#_core_customizing_the_licensing_of_an_activex_control) далее в данном разделе.  
  
#### Добавление поддержки лицензирования с помощью мастера элементов управления ActiveX при создании проекта элемента управления  
  
1.  Использование инструкций в [Создание элемента управления ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md).  Страница **Параметры приложения** мастера элементов управления ActiveX содержит параметр создания элемента управления с времени выполнения лицензией.  
  
 Мастер элементов управления ActiveX теперь создает оболочку элемента управления ActiveX, которая содержит базовую поддержку лицензирования.  Подробное описание кода лицензирования см. в следующем разделе.  
  
##  <a name="_core_licensing_support"></a> Поддержка лицензирования  
 При использовании мастера элементов управления ActiveX для добавления поддержки лицензирования в элемент управления ActiveX, мастера элементов управления ActiveX добавьте код, который объявляет и реализует возможность лицензирования добавляется к заголовку и файлы реализации элемента управления.  Этот код функции\-члена состоит из `VerifyUserLicense` и функции\-члена `GetLicenseKey`, переопределяют реализации по умолчанию, обнаруженные в [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md).  Эти функции возвращают и проверяют лицензия элемента управления.  
  
> [!NOTE]
>  Третий функцию\-член, `VerifyLicenseKey` не создается с помощью мастера элементов управления ActiveX, но может быть переопределен, чтобы настраивать расширение функциональности проверки лицензионного ключа.  
  
 Эти функции\-члены:  
  
-   [VerifyUserLicense](../Topic/COleObjectFactory::VerifyUserLicense.md)  
  
     Проверяет, что элемент управления позволяет потребление времени разработки, система проверить наличие файла лицензий элемента управления.  Эта функция вызывается платформой в процессе обработки **IClassFactory2::GetLicInfo** и **IClassFactory::CreateInstanceLic**.  
  
-   [GetLicenseKey](../Topic/COleObjectFactory::GetLicenseKey.md)  
  
     Запросы уникальный ключ из библиотеки DLL элемента управления.  Этот ключ внедряется в контейнерном приложении и используется позднее, вместе с `VerifyLicenseKey`, для создания экземпляра элемента управления.  Эта функция вызывается платформой в процессе обработки **IClassFactory2::RequestLicKey**.  
  
-   [VerifyLicenseKey](../Topic/COleObjectFactory::VerifyLicenseKey.md)  
  
     Проверяет, что вложенный ключ и уникальный ключ элемента управления одинаковы.  Это позволяет контейнер для создания экземпляра элемента управления для его использования.  Эта функция вызывается платформой в процессе обработки **IClassFactory2::CreateInstanceLic** и может быть переопределена для обеспечения проверки настроенной лицензионного ключа.  Реализация по умолчанию выполняет сравнение строк.  Дополнительные сведения см. в разделе [Лицензирование настраивать элемент управления ActiveX](#_core_customizing_the_licensing_of_an_activex_control) далее в данном разделе.  
  
###  <a name="_core_header_file_modifications"></a> Изменения файла заголовка  
 Мастер элементов управления ActiveX задает следующий код в файле заголовка элемента управления.  В этом примере объявляются 2 функции\-члена объекта `factory``CSampleCtrl`, один, проверка существования файла элемента управления РАСШИРЕНИЕ, а второй извлекает лицензионный ключ, используемых в приложении, содержащую элемент управления.  
  
 [!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_1.h)]  
  
###  <a name="_core_implementation_file_modifications"></a> Изменения файла реализации  
 Мастер элементов управления ActiveX устанавливает следующие 2 выписки в файле реализации элемента управления для объявления имени файла лицензии и строку лицензии.  
  
 [!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_2.cpp)]  
  
> [!NOTE]
>  При изменении **szLicString** в любом случае необходимо также изменить первая линия в файле элемента управления РАСШИРЕНИЕ или лицензирование не работает корректно.  
  
 Мастер элементов управления ActiveX задает следующий код в файле реализации элемента управления для определения функции `VerifyUserLicense` и `GetLicenseKey` классов элементов управления:  
  
 [!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_3.cpp)]  
  
 И, наконец, **Мастер элементов управления ActiveX** изменяет файл проекта .IDL элемента управления.  Ключевое слово **licensed** добавляется к объявлению компонентного класса элемента управления, как показано в следующем примере:  
  
 [!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_4.idl)]  
  
##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> Лицензирование настраивать элемент управления ActiveX  
 Поскольку `VerifyUserLicense`, `GetLicenseKey` и `VerifyLicenseKey` является виртуальным функции\-члена класса фабрики элемента управления, можно настраивать расширение функциональности лицензирования элемента управления.  
  
 Например, можно задать несколько уровней лицензирования для элемента управления путем переопределения функции\-члены `VerifyUserLicense` или `VerifyLicenseKey`.  Внутри этой функции можно настроить, свойства или методы предоставляются пользователю в соответствии с уровнем лицензии, обнаружен.  
  
 Можно также добавить код в функции `VerifyLicenseKey`, предоставляет числом метод для уведомления пользователя о создание элемента управления завершается ошибкой.  Например, в функции\-члене `VerifyLicenseKey` можно открыть окно сообщения о том, что элемент управления не удалось инициализировать и почему.  
  
> [!NOTE]
>  Другой способ проверки лицензии настраивать элемент управления ActiveX для базы данных регистрации для определенного раздела реестра, вместо вызова `AfxVerifyLicFile`.  Пример реализации по умолчанию см. в разделе [Изменения файла реализации](#_core_implementation_file_modifications) статьи.  
  
 Для дополнительного обсуждения проблем лицензирования вопросы лицензирования см. в разделе [Обновление существующего элемента управления ActiveX](../Topic/Upgrading%20an%20Existing%20ActiveX%20Control.md).  
  
## См. также  
 [Элементы управления ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [мастер элементов управления MFC ActiveX](../mfc/reference/mfc-activex-control-wizard.md)