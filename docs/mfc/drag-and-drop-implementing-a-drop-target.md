---
title: "Перетаскивание: реализация конечного расположения сброса | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE drag and drop [MFC], implementing drop targets
- OLE drag and drop [MFC], drop target
- drag and drop [MFC], drop target
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9fc73eb6627e63b8013180b7608633a9ee424c92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="drag-and-drop-implementing-a-drop-target"></a>Перетаскивание. Реализация конечного расположения сброса
В этой статье описано, как сделать приложение конечного расположения сброса. Реализация конечного расположения сброса занимает немного сложнее, чем реализация источника перетаскивания, но по-прежнему относительно просто. Эти методы также применяются к приложениям отличных от OLE.  
  
#### <a name="to-implement-a-drop-target"></a>Для реализации объекта-приемника  
  
1.  Добавьте переменную-член для каждого представления в приложении, которое вы хотите быть конечного расположения сброса. Эта переменная-член должен иметь тип `COleDropTarget` или класс, производный от него.  
  
2.  Из функции класс представления, который обрабатывает `WM_CREATE` сообщений (обычно `OnCreate`), для обращения к новой переменной члена `Register` функции-члена. `Revoke`вызывается автоматически для вас при уничтожении представления.  
  
3.  Переопределите следующие функции. Если необходимо такое же поведение во всем приложении Переопределите эти функции в классе представления. Если требуется изменить поведение в отдельных случаях необходимо включить при удалении отличных`CView` windows, переопределение этих функций в вашей `COleDropTarget`-производного класса.  
  
    |Переопределение|Чтобы разрешить|  
    |--------------|--------------|  
    |`OnDragEnter`|Удаление действий в окне. Вызывается, когда курсор в первый раз входит окна.|  
    |`OnDragLeave`|Специальное поведение, когда операция перетаскивания выходит за пределы указанного окна.|  
    |`OnDragOver`|Удаление действий в окне. Вызывается, когда курсор перемещается на экране.|  
    |`OnDrop`|Обработка данных в процессе удаления в указанном окне.|  
    |`OnScrollBy`|Особое поведение для прокрутки при необходимости в окне целевых.|  
  
 В разделе MAINVIEW. CPP файл, который является частью образца MFC OLE [OCLIENT](../visual-cpp-samples.md) пример о работе этих функций.  
  
 Дополнительные сведения:  
  
-   [Реализация источника перетаскивания](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [Создание и уничтожение объектов данных OLE и источников данных](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Управление объектов OLE и источников данных](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## <a name="see-also"></a>См. также  
 [Перетаскивание (OLE)](../mfc/drag-and-drop-ole.md)   
 [Класс COleDropTarget](../mfc/reference/coledroptarget-class.md)
