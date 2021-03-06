---
title: "Серверы: Реализация окон фрейма на месте | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7e26cbb0099f897c65ab3e39338f3c36e77112e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="servers-implementing-in-place-frame-windows"></a>Серверы. Реализация окон фрейма на месте
В этой статье объясняется, что необходимо сделать для реализации окна фрейма на месте в приложении сервера визуального редактирования, если мастер приложений не используется для создания приложения сервера. Вместо следующие процедуры, описанной в этой статье, можно использовать существующий класс окна фрейма на месте из мастера создания приложений приложения или образца, входящие в состав Visual C++.  
  
#### <a name="to-declare-an-in-place-frame-window-class"></a>Чтобы объявить класс окна фрейма на месте  
  
1.  Создайте производный класс окна фрейма на месте из `COleIPFrameWnd`.  
  
    -   Используйте `DECLARE_DYNCREATE` макрос в файл заголовка класса.  
  
    -   Используйте `IMPLEMENT_DYNCREATE` макрос в файле реализации (CPP) класса. Это позволяет объектов этого класса, создаваемого платформой.  
  
2.  Объявите `COleResizeBar` члена в классе фреймового окна. Это необходимо, если требуется поддержка изменения размера на месте в серверных приложениях.  
  
     Объявите `OnCreate` обработчик сообщений (с помощью **свойства** окна) и вызвать **создать** для вашей `COleResizeBar` элемент, если она определена.  
  
3.  Если у вас есть панель инструментов, объявите `CToolBar` члена в классе фреймового окна.  
  
     Переопределить `OnCreateControlBars` функции-члена для создания панели инструментов, когда сервер активен на месте. Пример:  
  
     [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]  
  
     В описании этот код, следующий шаг 5.  
  
4.  Включите файл заголовка для этого класса окна фрейма на месте в основной CPP-файле.  
  
5.  В `InitInstance` класса приложения, вызовите `SetServerInfo` функция объекта шаблона документа для указания ресурсов и окна фрейма на месте для использования в открытых и месте изменения.  
  
 Ряд функция, вызываемая в **Если** инструкция создает панели инструментов из ресурсов указанный сервер server. На этом этапе панели инструментов является частью иерархии контейнера окна. Поскольку эта панель инструментов является производным от `CToolBar`, приложение пройдет сообщения его владельцу окном фрейма приложения-контейнера, если не изменить владельца. Поэтому вызов `SetOwner` необходим. Этот вызов переводит окно, куда должны отправляться команды должно быть окно фрейма на месте на сервере, вызывая сообщений, передаваемых на сервер. Это позволяет серверу реагировать на операции на панели инструментов, он предоставляет.  
  
 Идентификатор для инструментов растрового изображения должно быть таким же, как другие ресурсы на месте, определенные в серверное приложение. В разделе [меню и ресурсы: Добавление серверов](../mfc/menus-and-resources-server-additions.md) подробные сведения.  
  
 Дополнительные сведения см. в разделе [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md), [COleResizeBar](../mfc/reference/coleresizebar-class.md), и [CDocTemplate::SetServerInfo](../mfc/reference/cdoctemplate-class.md#setserverinfo) в *Справочник по библиотеке классов*.  
  
## <a name="see-also"></a>См. также  
 [Серверы](../mfc/servers.md)   
 [Серверы: Реализация сервера](../mfc/servers-implementing-a-server.md)   
 [Серверы: Реализация документов сервера](../mfc/servers-implementing-server-documents.md)   
 [Серверы. Элементы сервера](../mfc/servers-server-items.md)

