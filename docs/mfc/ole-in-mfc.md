---
title: "OLE в MFC | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 38b2f6c936ff314f56e4b1868837729ad00efce4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="ole-in-mfc"></a>OLE в MFC
В этой статье рассматривается основы программирования OLE с помощью MFC. MFC предоставляет удобный способ создавать программы, использующие OLE:  
  
-   Для использования OLE визуального редактирования (Активация на месте).  
  
-   Для работы в качестве OLE-контейнеры и серверы.  
  
-   Для реализации функциональности перетаскивания и вставки.  
  
-   Для работы с данными даты и времени.  
  
-   Чтобы управлять данные состояния MFC модулей, включая экспортировать точки входа функции DLL точки входа интерфейса OLE/COM и точки входа процедуры окна.  
  
 Можно также использовать [автоматизации](../mfc/automation.md) или [удаленной автоматизации](../mfc/remote-automation.md) работы другой программы из программы.  
  
> [!NOTE]
>  Термин, который обозначает OLE перетаскивание технологии, связанные с связь и внедрение, включая OLE-контейнеры, OLE-серверы, OLE-элементы, активация на месте (или визуального редактирования), средства отслеживания и слияние меню. Термин Active применяется к модели объектов компонентов (COM) и объекты на основе COM такими как элементы управления ActiveX. Теперь называется автоматизации OLE-автоматизации.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Поддержка OLE](../mfc/ole-background.md)  
 Описание OLE и приводятся общие сведения о том, как он работает.  
  
 [Активация](../mfc/activation-cpp.md)  
 В этом разделе описывается роль активации редактирования OLE-элементы.  
  
 [Контейнеры](../mfc/containers.md)  
 Ссылки на использование контейнеров в OLE.  
  
 [Объекты и источники данных](../mfc/data-objects-and-data-sources-ole.md)  
 Содержит ссылки на разделы, посвященные использование `COleDataObject` и `COleDataSource` классы.  
  
 [Перетаскивание](../mfc/drag-and-drop-ole.md)  
 Объясняется использование, копирование и вставка с OLE.  
  
 [Меню и ресурсы OLE](../mfc/menus-and-resources-ole.md)  
 Описание использования меню и ресурсы в приложениях MFC OLE документа.  
  
 [Регистрация](../mfc/registration.md)  
 Описание установки сервера и инициализации.  
  
 [Серверы](../mfc/servers.md)  
 Описывает создание OLE элементы (или компоненты) для использования приложением-контейнером.  
  
 [Средства отслеживания](../mfc/trackers.md)  
 Предоставляет сведения о `CRectTracker` класс, который предоставляет графический интерфейс, чтобы пользователи могли взаимодействовать с клиента OLE-элементы.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Точки подключения](../mfc/connection-points.md)  
 Содержит описание реализации точек подключения (прежнее название — точки подключения OLE) с использованием классов MFC `CCmdTarget` и `CConnectionPoint`.  
  
 [Компоненты COM контейнера и сервера](../mfc/containers-advanced-features.md)  
 Описаны шаги, необходимые для включения необязательные дополнительные компоненты в существующие приложения контейнера.  
  
 [Модель COM](http://msdn.microsoft.com/library/windows/desktop/ms694363)  
 Описывает использование OLE без использования MFC.  
  
## <a name="see-also"></a>См. также  
 [Основные понятия](../mfc/mfc-concepts.md)

