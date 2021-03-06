---
title: "TN024: Сообщения, определенные MFC и ресурсы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17aadfd089d6917cd8cded239287034026ff7ad3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024. Сообщения и ресурсы, определенные MFC
> [!NOTE]
>  Следующее техническое примечание не было обновлено, поскольку сначала оно было включено в электронную документацию. В результате некоторые процедуры и разделы могут быть устаревшими или неверными. Для получения последних сведений рекомендуется выполнить поиск интересующей темы в алфавитном указателе документации в Интернете.  
  
 Эта заметка Описывает внутренние сообщения Windows и форматов файлов ресурсов, используемые MFC. Эта информация объясняет реализацию платформы и будет использовать при отладке приложения. Для активно несмотря на то, что эти сведения не официально поддерживается, вы можете использовать некоторые из этих сведений для более сложные реализации.  
  
 Эта заметка содержит сведения о закрытой реализации MFC; все содержимое могут измениться в будущем. Закрытые сообщения MFC Windows имеют значение в области только одно приложение, но изменится в будущем накопить системных сообщений.  
  
 Закрытые сообщения диапазона MFC Windows и типы ресурсов находятся в диапазоне зарезервированных «система» выделить операционной системой Microsoft Windows. Используются в настоящее время не все числа в диапазонах и в будущем, можно использовать новый числа в диапазоне. В настоящее время используется номера может быть изменен.  
  
 MFC Windows закрытого сообщения находятся в диапазоне от 0x360 -> 0x37F.  
  
 Типы находятся в диапазоне от 0xF0 MFC закрытого ресурса -> 0xFF.  
  
 **Сообщения Windows закрытого MFC**  
  
 Эти сообщения Windows используются вместо виртуальных функций C++, где не требуется относительно слабой связи между объектами окон и когда виртуальной функции C++ может не подойти.  
  
 Эти конфиденциальных сообщений Windows и связанных параметров структуры объявляются в частный заголовок MFC "AFXPRIV. H ". Предупреждение о том, что код, содержащий этот заголовок может полагаться на непредсказуемому поведению и скорее всего, будет нарушит в будущих версий MFC.  
  
 В редких случаях необходимо, чтобы для обработки одного из этих сообщений, следует использовать `ON_MESSAGE` сообщение макрос сопоставления и обработки сообщения в формате универсального LRESULT/WPARAM и LPARAM.  
  
 **WM_QUERYAFXWNDPROC**  
  
 Это сообщение отправляется в окно создаваемого. Это число отправляется очень ранней стадии процесса создания как метод определения того, если WndProc **AfxWndProc. AfxWndProc** возвращает 1.  
  
|||  
|-|-|  
|wParam|Не используется|  
|lParam|Не используется|  
|returns|1, если обрабатываемых **AfxWndProc**|  
  
 **WM_SIZEPARENT**  
  
 Это сообщение отправляется по окно фрейма его непосредственные дочерние элементы при изменении размера (**CFrameWnd::OnSize** вызовы `CFrameWnd::RecalcLayout` какие вызовы `CWnd::RepositionBars`) для изменения положения панели элементов управления вокруг боковой стороне главного окна. **AFX_SIZEPARENTPARAMS** структура содержит текущий прямоугольник для клиента родительский и HDWP, (который может быть равно NULL) с помощью которой вызывается `DeferWindowPos` чтобы свести к минимуму перерисовка.  
  
|||  
|-|-|  
|wParam|Не используется|  
|lParam|Адрес **AFX_SIZEPARENTPARAMS** структуры|  
|returns|Не используется (0)|  
  
 Пропуск сообщения указывает, что окно не участвуют в макете.  
  
 **WM_SETMESSAGESTRING**  
  
 Это сообщение отправляется в фрейм окна служит для обновления строки сообщения в строке состояния. Идентификатор строки или LPCSTR может быть задан (но не оба).  
  
|||  
|-|-|  
|wParam|Строка идентификатора (или 0)|  
|lParam|LPCSTR для строки (или значение NULL)|  
|returns|Не используется (0)|  
  
 **WM_IDLEUPDATECMDUI**  
  
 Это сообщение отправляется в время простоя для реализации обновления время простоя обработчиков команды обновления пользовательского интерфейса. Если окно (обычно панель элементов управления) обрабатывает сообщение, он создает `CCmdUI` (или объект производного класса) и вызовите **CCmdUI::DoUpdate** для каждого из элементов «» в окне. В свою очередь проверит наличие `ON_UPDATE_COMMAND_UI` обработчик для объектов в цепочке обработчика команд.  
  
|||  
|-|-|  
|wParam|BOOL bDisableIfNoHandler|  
|lParam|Не используется (0)|  
|returns|Не используется (0)|  
  
 *bDisableIfNoHandler* имеет ненулевое значение, чтобы отключить этот объект пользовательского интерфейса, если нет ни `ON_UPDATE_COMMAND_UI` ни `ON_COMMAND` обработчика.  
  
 **WM_EXITHELPMODE**  
  
 Это сообщение отправляется на `CFrameWnd` режим, чтобы выйти из контекстной справки. Получение этого сообщения завершает цикл, запущенную **CFrameWnd::OnContextHelp.**  
  
|||  
|-|-|  
|wParam|Не используется (0)|  
|lParam|Не используется (0)|  
|returns|Не используется|  
  
 **WM_INITIALUPDATE**  
  
 Это сообщение отправляется с помощью шаблона документа все потомки окна фрейма безопасно для них сделать их начальное обновление. Он преобразуется в вызов `CView::OnInitialUpdate` , но может использоваться в других `CWnd`-производных классов для других одноразовой обновления.  
  
|||  
|-|-|  
|wParam|Не используется (0)|  
|lParam|Не используется (0)|  
|returns|Не используется (0)|  
  
 **WM_RECALCPARENT**  
  
 Это сообщение отправляется с помощью представления своему родительскому окну (полученных с помощью `GetParent`) для принудительного повторного вычисления макета (обычно вызывает родительский `RecalcLayout`). Используется в приложения сервера OLE, где это необходимо для кадра к увеличению размера по мере роста общий размер этого представления.  
  
 Если родительское окно обрабатывает это сообщение следует возвращают значение TRUE и заполнение RECT, переданный lParam новый размер клиентской области. Это используется в `CScrollView` правильно обрабатывала полосы прокрутки (установить затем за пределами окна при их добавлении) объект сервера при активации на месте.  
  
|||  
|-|-|  
|wParam|Не используется (0)|  
|lParam|LPRECT rectClient может иметь значение NULL|  
|returns|Значение TRUE, если новый клиентского прямоугольника, значение FALSE в противном случае возвращается|  
  
 **WM_SIZECHILD**  
  
 Это сообщение отправляется по `COleResizeBar` для окна-владельца (через `GetOwner`) при изменении пользователем размера полосу изменения размера с маркерами изменения размера. `COleIPFrameWnd`При попытке изменить положение окна фрейма, как пользователь запросил реагирует на данное сообщение.  
  
 Указывает новый прямоугольник, в клиентских координатах относительно окна фрейма, который содержит полосу изменения размера по lParam.  
  
|||  
|-|-|  
|wParam|Не используется (0)|  
|lParam|LPRECT rectNew|  
|returns|Не используется (0)|  
  
 **WM_DISABLEMODAL**  
  
 Это сообщение отправляется на все всплывающие окна, принадлежащие окно фрейма, который становится неактивным. Окна фрейма использует результат для определения ли отключить всплывающего окна.  
  
 Это можно использовать для выполнения специальной обработки в всплывающем окне фрейма переходит в модальное состояние или запретить получение отключены некоторые всплывающие окна. Всплывающие подсказки использовать это сообщение для уничтожения сами при окна фрейма в модальное состояние, например.  
  
|||  
|-|-|  
|wParam|Не используется (0)|  
|lParam|Не используется (0)|  
|returns|Ненулевое значение для **не** отключать окно, значение 0 указывает, будут отключены окна|  
  
 **WM_FLOATSTATUS**  
  
 Это сообщение отправляется на все всплывающие окна, принадлежащие окно фрейма при активации или деактивации, еще одно окно фрейма верхнего уровня кадр. Это значение используется реализация **MFS_SYNCACTIVE** в `CMiniFrameWnd`, чтобы синхронизировать активации этих всплывающих окон с активацией окна рамки верхнего уровня.  
  
|||  
|-|-|  
|wParam|Является одним из следующих значений:<br /><br /> **FS_SHOW**<br /><br /> **FS_HIDE**<br /><br /> **FS_ACTIVATE**<br /><br /> **FS_DEACTIVATE**<br /><br /> **FS_ENABLEFS_DISABLE**<br /><br /> **FS_SYNCACTIVE**|  
|lParam|Не используется (0)|  
  
 Возвращаемое значение должно быть ненулевым Если **FS_SYNCACTIVE** — набор и синхронизирует окно с родительского фрейма для ее активации. `CMiniFrameWnd`возвращает ненулевое значение, если стиль имеет значение **MFS_SYNCACTIVE.**  
  
 Дополнительные сведения см. в разделе реализации `CMiniFrameWnd`.  
  
## <a name="wmactivatetoplevel"></a>WM_ACTIVATETOPLEVEL  
 Это сообщение отправляется в окно верхнего уровня, при активации или деактивации окна в его «верхнего уровня группы». Окно — часть группы верхнего уровня, если это окно верхнего уровня (нет родительского или владелец), или он принадлежит такое окно. Это сообщение аналогично с помощью **WM_ACTIVATEAPP,** , но работает в ситуациях, где windows, принадлежащих разные процессы смешиваются в одном окне иерархии (обычно в приложениях OLE).  
  
## <a name="wmcommandhelp-wmhelphittest-wmexithelpmode"></a>WM_EXITHELPMODE WM_COMMANDHELP WM_HELPHITTEST,  
 Эти сообщения используются в реализации контекстной справки. Обратитесь к [Технические заметки 28](../mfc/tn028-context-sensitive-help-support.md) для получения дополнительной информации.  
  
## <a name="mfc-private-resource-formats"></a>Форматы ресурсов частного MFC  
 В настоящее время MFC определяет два формата закрытого ресурса: **RT_TOOLBAR** и **RT_DLGINIT**.  
  
## <a name="rttoolbar-resource-format"></a>Формат ресурса RT_TOOLBAR  
 Панели инструментов по умолчанию, предоставляемые мастером приложений на основе **RT_TOOLBAR** настраиваемого ресурса, который появился в версии MFC 4.0. Вы можете изменить этот ресурс, с помощью панели инструментов редактора.  
  
## <a name="rtdlginit-resource-format"></a>Формат ресурса RT_DLGINIT  
 Один формат закрытого ресурса MFC используется для хранения диалоговое окно Дополнительные сведения об инициализации. Включает в себя начальной строки, хранящиеся в поле со списком. Формат этого ресурса не позволяет изменить вручную, но обрабатывается Visual C++.  
  
 Visual C++ и это **RT_DLGINIT** ресурсов не должны использовать связанные компоненты MFC, так как имеются альтернативу API с помощью сведений, ресурс. С помощью Visual C++ позволяет легко для записи, поддерживать и перевести приложение в долгосрочной перспективе.  
  
 Базовая структура **RT_DLGINIT** ресурс является следующим образом:  
  
```  
+---------------+    \  
| Control ID    |   UINT             |  
+---------------+    |  
| Message #     |   UINT             |  
+---------------+    |  
|length of data |   DWORD            |  
+---------------+    |   Repeated  
|   Data        |   Variable Length  |   for each control  
|   ...         |   and Format       |   and message  
+---------------+    /  
|     0         |   BYTE  
+---------------+  
```  
  
 Повторяющиеся раздел содержит идентификатор элемента управления для отправки сообщения, сообщения # отправки (обычного сообщения Windows) и переменной длины данных. В форме отправляется сообщение Windows.  
  
```  
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```  
  
 Это очень общий формат, что все сообщения Windows и содержимое данных. Редактор ресурсов Visual C++ и MFC поддерживают только ограниченное подмножество сообщений Windows: CB_ADDSTRING для начальной список выбора для поля со списком (данных представляет собой текстовую строку).  
  
## <a name="see-also"></a>См. также  
 [Технические примечания по номеру](../mfc/technical-notes-by-number.md)   
 [Технические примечания по категории](../mfc/technical-notes-by-category.md)

