---
title: "Оператор try-except (C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__except"
  - "try"
  - "__try"
  - "except"
  - "__except_cpp"
  - "__try_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__except - ключевое слово [C]"
  - "__except - ключевое слово [C], в try-except"
  - "__try - ключевое слово [C]"
  - "структурированная обработка исключений, try-except"
  - "try-catch - ключевое слово [C]"
  - "try-catch - ключевое слово [C], try-except - ключевое слово [C]"
  - "try-except - ключевое слово [C]"
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Оператор try-except (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Блок, относящийся только к системам Microsoft**  
  
 Оператор **try\-except** является расширением Microsoft для языка C, которое позволяет приложениям получать управление программой при возникновении событий, обычно приводящих к прекращению выполнения.  Такие события вызываются исключениями, а механизм, предназначенный для работы с ними, называется структурированной обработкой исключений.  
  
 Исключения могут вызываться аппаратными или программными средствами.  Даже если работа приложения после таких исключений и не может полностью восстановиться, структурированная обработка исключений позволяет отобразить информацию об ошибке и зафиксировать внутреннее состояние приложения, чтобы выполнить диагностику проблемы.  Это особенно полезно для нерегулярно встречающихся неполадок, которые сложно воспроизвести.  
  
## Синтаксис  
 *оператор\-try\-except*:  
 **\_\_try**  *составной\-оператор*  
  
 **\_\_except \(**  *выражение*  **\)**  *составной\-оператор*  
  
 Составной оператор после предложения `__try` представляет собой защищенный раздел.  Составной оператор после предложения `__except` является обработчиком исключения.  Обработчик задает набор действий, выполняемых при возникновении исключения во время выполнения защищенного раздела.  Выполнение происходит следующим образом:  
  
1.  Сначала выполняется защищенный раздел.  
  
2.  Если исключение при этом не возникает, выполнение переходит в инструкцию, стоящую после предложения `__except`.  
  
3.  Если исключение возникло во время выполнения защищенного раздела или в любой процедуре, вызываемой из защищенного раздела, вычисляется выражение `__except` и способ обработки исключения определяется возвращенным значением.  Поддерживается три значения:  
  
     `EXCEPTION_CONTINUE_SEARCH` Исключение не распознано.  Программа переходит к поиску обработчика в стеке \(сначала находятся выражения с оператором **try\-except**, а затем обработчики с наивысшим приоритетом\).  
  
     `EXCEPTION_CONTINUE_EXECUTION` Исключение распознано, но отброшено.  Выполнение продолжается в точке, в которой возникло исключение.  
  
     `EXCEPTION_EXECUTE_HANDLER` Исключение распознано.  Управление передается в обработчик исключений путем выполнения составного оператора `__except`, затем выполнение продолжается с точки, в которой возникло исключение.  
  
 Поскольку выражение `__except` вычисляется как выражение C, оно ограничивается одиночным значением, оператором условного выражения и оператором запятой.  Если требуется более сложная обработка, выражение может вызывать процедуру, которая возвращает одно из этих трех значений.  
  
> [!NOTE]
>  Структурированная обработка исключений поддерживается с исходными файлами C и C\+\+.  Однако она не предназначена специально для C\+\+.  Для того чтобы ваш код лучше переносился, лучше использовать механизм обработки исключений языка C\+\+.  Кроме того, механизм обработки исключений C\+\+ обеспечивает намного более высокую гибкость, поскольку может обрабатывать исключения любого типа.  
  
> [!NOTE]
>  Для программ C\+\+ вместо структурированной обработки исключений следует использовать обработку исключений C\+\+.  Дополнительные сведения см. в разделе [Обработка исключений](../cpp/exception-handling-in-visual-cpp.md) *Справочника по языку С\+\+*.  
  
 Каждая процедура в приложении может иметь свой собственный обработчик исключений.  Выражение `__except` выполняется в области тела `__try`.  Это означает, что оно имеет доступ ко всем локальным переменным, объявленным в этой области.  
  
 Ключевое слово `__leave` можно использовать только в блоке оператора **try\-except**.  Результат использования ключевого слова `__leave` — переход в конец блока **try\-except**.  Выполнение продолжается после окончания обработчика исключений.  Хотя для получения того же результата можно использовать оператор `goto`, он \(оператор `goto`\) приводит к освобождению стека.  Оператор `__leave` более эффективен, поскольку не вызывает освобождение стека.  
  
 Выход из оператора **try\-except** с помощью функции времени выполнения `longjmp` считается ненормальным завершением.  Переход к оператору `__try` недопустим, но допустим выход из него.  Обработчик исключений не вызывается, если процесс удален во время выполнения оператора **try\-except**.  
  
## Пример  
 Ниже приведен пример обработчика исключений и обработчика завершения.  Дополнительные сведения об обработчиках завершения см. в разделе [Оператор try\-finally](../c-language/try-finally-statement-c.md) .  
  
```  
.  
.  
.  
puts("hello");  
__try{  
   puts("in try");  
   __try{  
      puts("in try");  
      RAISE_AN_EXCEPTION();  
   }__finally{  
      puts("in finally");  
   }  
}__except( puts("in filter"), EXCEPTION_EXECUTE_HANDLER ){  
   puts("in except");  
}  
puts("world");  
```  
  
 Ниже показаны выходные данные для этого примера, справа добавлены комментарии:  
  
```  
hello  
in try              /* fall into try                     */  
in try              /* fall into nested try                */  
in filter           /* execute filter; returns 1 so accept  */  
in finally          /* unwind nested finally                */  
in except           /* transfer control to selected handler */  
world               /* flow out of handler                  */  
```  
  
 **Завершение блока, относящегося только к системам Microsoft**  
  
## См. также  
 [Оператор try\-except](../cpp/try-except-statement.md)