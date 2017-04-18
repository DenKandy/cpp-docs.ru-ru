---
title: "Класс moneypunct_byname | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.moneypunct_byname"
  - "std::moneypunct_byname"
  - "xlocmon/std::moneypunct_byname"
  - "moneypunct_byname"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "moneypunct_byname - класс"
ms.assetid: e8a544d2-6aee-420d-b513-deb385c9b416
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# Класс moneypunct_byname
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Производный класс шаблона, который описывает объект, который можно использовать как аспект `moneypunct` данного языкового стандарта, содержащие поля ввода форматирования монетное или монетные поля.  
  
## Синтаксис  
  
```  
template<class CharType, bool Intl = false>  
class moneypunct_byname : public moneypunct<CharType, Intl>  
{  
public:  
    explicit moneypunct_byname(  
        const char *_Locname,  
        size_t _Refs = 0  
    );  
    explicit moneypunct_byname(  
        const string& _Locname,  
        size_t _Refs = 0  
    );   
protected:  
    virtual ~moneypunct_byname();  
};  
```  
  
## Заметки  
 Его расширение функциональности именованным определяется языковым стандартом `_Locname`.  Каждый конструктор инициализирует его базовый объект с помощью [moneypunct](../Topic/moneypunct::moneypunct.md)\<CharType, Intl\>\(`_Refs`\).  
  
## Требования  
 **Заголовок:**\<locale\>  
  
 **Пространство имен:** std  
  
## См. также  
 [Потокобезопасность в стандартной библиотеке C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)