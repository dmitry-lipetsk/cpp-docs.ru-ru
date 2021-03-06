---
title: "Клиенты автоматизации | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9cfb6aae5c947d1f36019e548c72b22a3304aa12
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="automation-clients"></a>клиентами автоматизации
Автоматизация позволяет приложения для работы с объектами, реализованными в другом приложении или получить доступ к объектам, поэтому ими можно управлять. Клиента автоматизации — это приложение, можно управлять раскрытых объектов, принадлежащих другим приложением. Приложение, которое предоставляет доступ к объектам называется сервера автоматизации. Клиент управляет объектами сервера приложений с доступа к свойствам этих объектов и функций.  
  
### <a name="types-of-automation-clients"></a>Типы клиентов автоматизации  
 Существует два типа клиентов автоматизации.  
  
-   Клиенты, которые динамически (во время выполнения), получить сведения о свойствах и операций сервера.  
  
-   Клиенты, которые имеются статические данные (предоставляется во время компиляции), указывающая свойства и операции сервера.  
  
 Клиенты первого типа получить сведения о методах и свойствах сервера с помощью запроса к системе OLE `IDispatch` механизм. Несмотря на то, что оно достаточно для динамического клиентов `IDispatch` трудно использовать для статических клиентов, где объектов, управляется должно быть известно во время компиляции. Для клиентов, привязанного к статическим, Microsoft Foundation classes предоставляют [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md) класса.  
  
 Статические привязанного клиенты используют прокси-класса, которое статически связано с клиентским приложением. Этот класс предоставляет типобезопасный C++ инкапсуляция свойства и операции серверного приложения.  
  
 Класс `COleDispatchDriver` обеспечивает основной поддержку на стороне клиента автоматизации. С помощью `Add New Item` диалоговое окно, создайте класс, производный от `COleDispatchDriver`.  
  
 Укажите файл библиотеки типов, описывающая свойства и функции объекта приложения на сервере. В диалоговом окне Добавление элемента читает этот файл и создает `COleDispatchDriver`-производного класса с функциями-членами, приложение может вызвать для доступа к объектам серверного приложения в C++ в строго типизированным образом. Дополнительные функциональные возможности наследуется от `COleDispatchDriver` упрощает процесс вызова на соответствующий сервер автоматизации.  
  
### <a name="handling-events-in-automation-clients"></a>Обработка событий в клиентах автоматизации  
 Если вы хотите обрабатывать события в клиентском приложении автоматизации, необходимо добавить интерфейс приемника. MFC поддерживает мастер добавления приемника интерфейсов для элементов управления ActiveX, но не поддерживает для других серверов COM. Сведения о том, как добавить интерфейс приемника в клиентском приложении MFC для интерфейсов источника, описываемого COM-серверов см. в разделе Практическое руководство: Создание интерфейса приемника в клиент COM MFC-Based (181845 КБ) в [http://support.microsoft.com/default.aspxscid=kb;en-us; 181845](http://support.microsoft.com/default.aspxscid=kb;en-us;181845).  
  
## <a name="see-also"></a>См. также  
 [Клиенты автоматизации: Использование библиотек типов](../mfc/automation-clients-using-type-libraries.md)   
 [Автоматизация](../mfc/automation.md)   
 [Мастер приложений MFC](../mfc/reference/mfc-application-wizard.md)

