---
title: "Ограничения библиотек DLL, загружаемых с задержкой | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- constraints [C++], delayed loading of DLLs
- delayed loading of DLLs, constraints
- DLLs [C++], constraints
ms.assetid: 0097ff65-550f-4a4e-8ac3-39bf6404f926
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cd3f641a3ac03705ff7f3765d995d5c40bccda7d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="constraints-of-delay-loading-dlls"></a>Ограничения библиотек DLL, загружаемых с задержкой
Существует ряд ограничений, связанных с отложенной загрузкой файлов импорта.  
  
-   Файлы импорта данных не поддерживаются. Существует обходной путь, заключающийся в явном импорте данных с помощью методов `LoadLibrary` (или `GetModuleHandle` после того, как вспомогательная функция отложенной загрузки загрузила библиотеку DLL) и `GetProcAddress`.  
  
-   Отложенная загрузка Kernel32.dll не поддерживается. Эта библиотека DLL необходима для того, чтобы вспомогательные подпрограммы отложенной загрузки могли выполнить отложенную загрузку.  
  
-   [Привязка](../../build/reference/binding-imports.md) записи переадресованных точек не поддерживается.  
  
-   Отложенная загрузка библиотеки DLL может изменить поведение процесса, если в точке входа библиотеки DLL, загружаемой с задержкой, осуществляется инициализация процессов. Другой случай — это статическая память TLS (локальная память потока), объявляемая с помощью [__declspec(thread)](../../cpp/thread.md), она не работает, если библиотека DLL загружается с помощью `LoadLibrary`. Тем не менее, как в статических библиотеках DLL, так и в библиотеках DLL, загружаемых с задержкой, доступна для использования динамическая память TLS, реализуемая с помощью функций `TlsAlloc`, `TlsFree`, `TlsGetValue` и `TlsSetValue`.  
  
-   Статические (глобальные) указатели импортируемых функций потребуется инициализировать заново после первого вызова соответствующих функций. Причина в том, что при первом вызове указатель функции указывает на преобразователь.  
  
-   В настоящее время не существует способа отложить загрузку отдельных подпрограмм в библиотеке DLL при использовании нормального механизма импорта.  
  
-   Пользовательские соглашения о вызовах (например использование условных кодов в архитектурах x86) не поддерживаются. Кроме того, регистры с плавающей запятой не сохраняются ни на одной платформе. Если пользовательская вспомогательная подпрограмма или обработчик используют типы данных с плавающей запятой, то в них потребуется выполнить полное сохранение и восстановление состояния регистров с плавающей запятой на компьютерах, где в соглашениях о вызовах для передачи параметров с плавающей запятой используются регистры. Следует осторожно подходить к отложенной загрузке библиотеки DLL времени выполнения (CRT), если в программе вызываются функции CRT, принимающие параметры с плавающей запятой через стек арифметического сопроцессора (NDP) во вспомогательной функции.  
  
## <a name="see-also"></a>См. также  
 [Поддержка компоновщика для DLLs, загружаемых с задержкой](../../build/reference/linker-support-for-delay-loaded-dlls.md)   
 [Функции LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175.aspx)   
 [Функция GetModuleHandle](http://msdn.microsoft.com/library/windows/desktop/ms683199.aspx)   
 [Функция GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx)   
 [Функция TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801.aspx)   
 [Функция TlsFree](http://msdn.microsoft.com/library/windows/desktop/ms686804.aspx)   
 [Функция TlsGetValue](http://msdn.microsoft.com/library/windows/desktop/ms686812.aspx)   
 [Функция TlsSetValue](http://msdn.microsoft.com/library/windows/desktop/ms686818.aspx)