---
title: "Выходные данные классы (контекст устройства) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.output
dev_langs: C++
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: db7080c263ee6e98d458381d59446263490dfd7a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="output-device-context-classes"></a>Классы вывода (контекст устройства)
Эти классы инкапсулируют различных типов устройств контексты, доступные в Windows.  
  
 Большинство следующие классы инкапсулируют дескриптор контекста устройства Windows. Контекст устройства — объект Windows, который содержит сведения о замене атрибутов рисования устройства, такие как экран или принтер. Все вызовы рисования выполняются через объект контекста устройства. Дополнительные классы, производные от `CDC` инкапсулируют функциональность специализированные контекста устройства, включая поддержку метафайлы Windows.  
  
 [CDC](../mfc/reference/cdc-class.md)  
 Базовый класс для контексты устройств. Использовать непосредственно, для доступа к целой отображаемой и доступ к nondisplay контекстах, например принтеры.  
  
 [CPaintDC](../mfc/reference/cpaintdc-class.md)  
 Контекст отображения, используемых в `OnPaint` функции-члены класса windows. Автоматически вызывает `BeginPaint` при использовании конструктора и `EndPaint` при уничтожении объекта.  
  
 [CClientDC](../mfc/reference/cclientdc-class.md)  
 Контекст отображения для клиентской области окна. Используется, например, для рисования в ответ на события мыши немедленно.  
  
 [CWindowDC](../mfc/reference/cwindowdc-class.md)  
 Контекст отображения для всей системы windows, включая клиента и неклиентской области.  
  
 [CMetaFileDC](../mfc/reference/cmetafiledc-class.md)  
 Контекст устройства для метафайлы Windows. Метафайл Windows содержит последовательность команд (GDI) интерфейса графических устройств, которые могут быть воспроизведены в приложении для создания образа. Вызовы к функциям-членам `CMetaFileDC` записаны в метафайл.  
  
## <a name="related-classes"></a>Связанные классы  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 Хранит пары координат (x, y).  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 Содержит расстояние, относительные позиции или пар значений.  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 Содержит координаты прямоугольной области.  
  
 [CRgn](../mfc/reference/crgn-class.md)  
 Инкапсулирует область GDI для манипулирования эллипса, многоугольных или неправильную область в окне. Используется в сочетании с отсечения функции-члены в классе `CDC`.  
  
 [CRectTracker](../mfc/reference/crecttracker-class.md)  
 Отображает и обрабатывает пользовательский интерфейс для изменения размера и перемещения прямоугольной объектов.  
  
 [CColorDialog](../mfc/reference/ccolordialog-class.md)  
 Предоставляет стандартное диалоговое окно для выбора цвета.  
  
 [CFontDialog](../mfc/reference/cfontdialog-class.md)  
 Предоставляет стандартное диалоговое окно для выбора шрифта.  
  
 [CPrintDialog](../mfc/reference/cprintdialog-class.md)  
 Предоставляет стандартное диалоговое окно для печати файла.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о классе](../mfc/class-library-overview.md)

