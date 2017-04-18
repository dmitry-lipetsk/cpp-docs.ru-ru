---
title: "Серверы автоматизации | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Серверы автоматизации"
  - "компоненты COM, Серверы автоматизации"
  - "съемы подготовки к отправке, Серверы автоматизации"
  - "серверы, автоматизация"
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Серверы автоматизации
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Автоматизация дает возможность приложения для управления объектами, реализованные в другом приложении или предоставление объектов и их можно управлять.  Сервер автоматизации приложение, которое предоставляет программируемых объектов \(называемые объектами Автоматизации\) другим приложениям требуется \( [Клиенты автоматизации](../mfc/automation-clients.md)\).  Серверы автоматизации иногда называются компонентами Автоматизации.  
  
 Предоставление объектов автоматизации позволяет клиентам автоматизации некоторые процедуры прямой доступ к объектам и функция сервер делает доступным.  Предоставление объекты таким способом полезна при приложения предоставляют функции, которые используются для других приложений.  Например, текстовый процессор может предоставлять его возможности необходимые таким образом, чтобы другие программы могли использовать его.  Предоставление объектов таким образом позволяют поставщикам повысить функциональность своих приложений с помощью готовой функции других приложений.  
  
 Эти объекты автоматизации имеют свойства и методы их как внешний интерфейс.  Свойства называются атрибутами объектов автоматизации.  Свойства и элементы данных класса C\+\+.  Методы функции, работающие на объекты автоматизации.  Методы функции как открытые члены класса C\+\+.  
  
> [!NOTE]
>  Хотя свойства как элементы данных C\+\+, они недоступны напрямую.  Чтобы предоставить доступ прозрачный настройте внутреннюю переменную в объекте автоматизации с парой, чтобы получить или задать функции\-члены доступ к ним.  
  
 , Для публикации приложений через общий интерфейс, чёткий, автоматизацию делает возможной его построение приложения в одном общем языке программирования, например Microsoft Visual Basic, а не в разнообразных, специфичных для приложения языков макроса.  
  
##  <a name="_core_support_for_automation_servers"></a> Поддержка сервера автоматизации  
 Visual C\+\+ и платформы MFC предоставляют широкие возможности для сервера автоматизации.  Они обрабатывают большую часть нагрузки, входящих в это сервер автоматизации, можно сделать усилий для функций приложения.  
  
 Механизм платформы главным образом для поддержки автоматизации схема подготовки к сообщению, набор макросов, развернуть в объявления и вызывает необходимые для предоставления методы и свойства для OLE.  Обычная схема подготовки к отправке выглядит следующим образом:  
  
 [!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/CPP/automation-servers_1.cpp)]  
  
 Окно свойств и представление классов помогают в поддерживаемом схемах подготовки к сообщению.  При добавлении новых метод или свойство в класс, Visual C\+\+ добавляет соответствующие `DISP_FUNCTION` или макрос `DISP_PROPERTY` с параметрами, указывающее имя класса, внешние и внутренние имена методов или свойств и типы данных.  
  
 Диалоговое окно **Добавление класса** также упрощает объявление классов автоматизации и управление их свойств и операций.  При использовании диалогового окна " добавление класса для добавления класса в проект, необходимо указать его базовый класс.  Если базовый класс позволяет автоматизации, элементы управления для отображения диалогового окна " добавление класса используется, чтобы определить, следует ли новый класс поддержке автоматизации, ли он «OLE создаваемыми» \(то есть ли объекты класса можно создать в запросе клиента модели COM\) и внешнее имя для клиента модели COM для использования.  
  
 Откроется диалоговое окно **Добавление класса** затем создает объявление класса, включая соответствующие макросов OLE для функций, определенной пользователем.  Он также добавляет каркас код для реализации функции\-члены класса.  
  
 Мастер приложений MFC упрощает шагов, необходимых для получения приложение сервера автоматизации с земли.  Если вы выбираете проект флажок **Автоматизация** на странице **Дополнительные параметры**, мастер приложений MFC добавляет в функции `InitInstance` приложения вызовы, необходимые для зарегистрированного объекты автоматизации и запускать приложение в качестве сервера автоматизации.  
  
### Выберите действие.  
  
-   [Дополнительные сведения о клиентах автоматизации](../mfc/automation-clients.md)  
  
-   [Дополнительные сведения о классе CCmdTarget](../Topic/CCmdTarget%20Class.md)  
  
-   [Дополнительные сведения о классе COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)  
  
## См. также  
 [автоматизация](../mfc/automation.md)   
 [мастер приложений MFC](../Topic/MFC%20Application%20Wizard.md)