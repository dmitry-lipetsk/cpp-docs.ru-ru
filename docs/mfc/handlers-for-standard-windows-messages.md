---
title: "Обработчики для стандартных сообщений Windows | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: afx_msg
dev_langs: C++
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 91df3462297c2a45a8938d815cc3b6a3b8ca6edb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="handlers-for-standard-windows-messages"></a>Обработчики для стандартных сообщений Windows
По умолчанию обработчики для стандартных сообщений Windows (**WM_**) предварительно определены в классе `CWnd`. Библиотека классов сформирует имена для этих обработчиков на имя сообщения. Например, обработчик `WM_PAINT` сообщение объявляется в `CWnd` как:  
  
 `afx_msg void OnPaint();`  
  
 **Afx_msg** ключевое слово предлагает эффект C++ **виртуальных** ключевое слово by отличия от других обработчиков `CWnd` функции-члены. Обратите внимание, что эти функции не фактически виртуальным; Вместо этого они реализуются с помощью схемы сообщений. Схемы сообщений зависят от исключительно на стандартные макросы препроцессора не для всех расширений языка C++. **Afx_msg** ключевое слово разрешается пробелы после предварительной обработки.  
  
 Чтобы переопределить обработчика, определенные в базовом классе, просто определите функцию с же прототип в производном классе, а также записи схемы сообщений для обработчика. Обработчик «переопределяет» любого обработчика с тем же именем, ни в одном из базовых классов ваш класс.  
  
 В некоторых случаях обработчик следует вызывать переопределенный обработчика в базовом классе, базовые классы и Windows могут работать в сообщении. Когда вызывать обработчик базового класса в переопределении зависит от обстоятельств. Иногда необходимо сначала вызвать обработчик базового класса и иногда последним. Иногда вызове обработчика базового класса условно, если вы решили не самостоятельно обрабатывать сообщения. Иногда необходимо вызывать обработчик базового класса, а затем позволяет выполнять собственный код обработчика, в зависимости от значения или состояния, возвращаемого обработчиком базового класса.  
  
> [!CAUTION]
>  Измените аргументы, переданные в обработчик, если требуется передать обработчик базового класса небезопасно. Например, может возникнуть желание изменить `nChar` аргумент `OnChar` обработчика (для преобразования в верхний регистр, например). Такое поведение довольно запутанные, но если необходимо выполнить этот эффект, используйте `CWnd` функции-члена **SendMessage** вместо него.  
  
 Как определить правильный способ переопределить данное сообщение, если окно свойств записывает основу функции обработчика для заданного сообщения — `OnCreate` обработчик `WM_CREATE`, например — эскизы его в виде рекомендуемые переопределить функцию-член. Следующий пример рекомендует обработчик сначала вызывает обработчик базового класса и продолжить работу только при условии, что он не возвращает значение -1.  
  
 [!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]  
  
 По соглашению имена этих обработчиков начинаются с префикса «On». Некоторые из этих обработчиков не принимают аргументов, тогда как другие принимают несколько. Также есть тип возвращаемого значения не `void`. Обработчики по умолчанию для всех **WM_** сообщений описаны в *Справочник по библиотеке MFC* как функции-члены класса `CWnd` , имена которых начинаются с «Далее». В объявлениях функций-членов `CWnd` начинаются с префикса **afx_msg**.  
  
## <a name="see-also"></a>См. также  
 [Объявление функций обработчиков сообщений](../mfc/declaring-message-handler-functions.md)
