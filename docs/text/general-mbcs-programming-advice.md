---
title: "Советы по программированию многобайтовой Кодировки Общие | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b379c163963a9ae0dd0c59c7d0fc809fee4f46d0
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="general-mbcs-programming-advice"></a>Общие советы по программированию многобайтовой кодировки
Используйте следующие рекомендации:  
  
-   Для обеспечения гибкости, использовать макросы во время выполнения, такие как `_tcschr` и `_tcscpy` по возможности. Дополнительные сведения см. в разделе [универсальные текстовые сопоставления в файле Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   Использование среды выполнения C `_getmbcp` для получения дополнительных сведений о текущей кодовой странице.  
  
-   Не используйте повторно строковые ресурсы. В зависимости от целевого языка заданную строку может иметь разные значения, при переводе. Например главное меню «Файл» в приложении может по-разному преобразовать из строки «Файл» в диалоговом окне. Если необходимо использовать более одной строки с тем же именем, используйте различные строковые идентификаторы для каждого.  
  
-   Может потребоваться узнать, работает ли приложение в многобайтовую операционной системы. Чтобы сделать это, необходимо установите флаг при запуске программы; не полагайтесь на API.  
  
-   При разработке диалоговым окнам, оставляйте около 30% дополнительного места в конце статического текстового элемента управления для преобразования многобайтовой Кодировки.  
  
-   Будьте внимательны при Выбор шрифтов для вашего приложения, так как некоторые шрифты доступны не во всех системах.  
  
-   При выборе шрифт для диалоговых окон, используйте [MS Shell Dlg](http://msdn.microsoft.com/library/windows/desktop/dd374112) вместо MS Sans Serif или Helvetica. MS Shell Dlg заменяется нужный шрифт в системе перед созданием диалоговым окном. MS Shell Dlg гарантирует, что любые изменения в операционную систему для работы с данным шрифтом автоматически становятся доступными. (MFC заменяет MS Shell Dlg DEFAULT_GUI_FONT или системного шрифта в Windows 95, Windows 98 и Windows NT 4, так как эти системы неправильно обрабатывает MS Shell Dlg.)  
  
-   При разработке приложения, решите, какие строки могут быть локализованы. В случае неясностей предполагается, что все строки будут переведены. Таким образом не следует смешивать строки, которые могут быть локализованы теми, которые невозможно.  
  
## <a name="see-also"></a>См. также  
 [Советы по программированию многобайтовой Кодировки](../text/mbcs-programming-tips.md)   
 [Увеличение и уменьшение значений указателей](../text/incrementing-and-decrementing-pointers.md)