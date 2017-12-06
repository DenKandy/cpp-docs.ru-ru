---
title: "Изменение размера изображения (редактор изображений для значков) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.image.editing
dev_langs: C++
helpviewer_keywords:
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6c6e8d5e4704f9dda9399d67de5b3d0f93d283a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/24/2017
---
# <a name="resizing-an-image-image-editor-for-icons"></a>Изменение размера изображения (редактор изображений для значков)
Поведение редактора изображения при изменении размера изображения зависит ли [выбранного](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) всего изображения или только его фрагмент.  
  
 Если выделена только часть изображения, редактор изображений может уменьшить выделенную область, удалив строки или столбцы точек и заполнив освободившуюся область с текущим цветом фона или его растягивает выделение путем дублирования строк или столбцов пикселей.  
  
 Если выделено все изображение, редактор изображений либо сжимает и растянуть изображение, или обрезает и расширяет его.  
  
 Существует два механизма изменить размеры изображения: маркеры изменения размера и [окно свойств](/visualstudio/ide/reference/properties-window). Можно перетаскивать маркеры изменения размера, чтобы изменить размер всех или части изображения. Маркеры изменения размера, которые можно перетащить сплошная. Нельзя перетащить маркеры, которые являются пустыми. Можно использовать в окне свойств изменение размера всего изображения не выделенной области.  
  
 ![Маркеры точечного рисунка](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")  
Маркеры изменения размера  
  
> [!NOTE]
>  Если у вас есть параметр плитку сетки в [параметры сетки-диалоговое окно](../windows/grid-settings-dialog-box-image-editor-for-icons.md), затем изменить ее размер позволяет выполнить привязку к следующей строке сетки плитки. Если только Точечная сетка выбран (по умолчанию), маркер может перемещаться доступным точкам.  
  
-   [Изменение размера всего изображения](../windows/resizing-an-entire-image-image-editor-for-icons.md)  
  
-   [Обрезание или расширение всего изображения](cropping-or-extending-an-entire-image-image-editor-for-icons.md)  
  
-   [Растяжение всего изображения и](../windows/shrinking-or-stretching-an-entire-image-image-editor-for-icons.md)  
  
-   [Растяжение и сжатие фрагмента изображения](../windows/shrinking-or-stretching-part-of-an-image-image-editor-for-icons.md)  
  
 Сведения о добавлении ресурсов в управляемые проекты см. в разделе [ресурсы в классических приложениях](https://msdn.microsoft.com/library/f45fce5x.aspx) в *руководства разработчика .NET Framework.* Сведения о вручную добавлять файлы ресурсов в управляемые проекты, осуществлять доступ к ресурсам, отображать статические ресурсы и присваивать строки ресурсов свойствам см. в разделе [Создание файлов ресурсов для приложений рабочего стола](https://msdn.microsoft.com/library/xbx3z216.aspx). Сведения о глобализации и локализации ресурсов в управляемых приложениях см. в разделе [Globalizing и локализация приложений .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
## <a name="requirements"></a>Требования  
 Нет  
  
## <a name="see-also"></a>См. также  
 [Сочетания клавиш](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Редактирование графических ресурсов](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Редактор изображений для значков](../windows/image-editor-for-icons.md)
