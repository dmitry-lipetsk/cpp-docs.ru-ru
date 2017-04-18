---
title: "Использование диалоговой панели с элементом управления главной панели | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WM_EX_TRANSPARENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "диалоговые панели, использование с лентами главной панели"
  - "Элементы управления главной панели, диалоговые панели"
  - "WS_EX_TRANSPARENT - стиль"
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Использование диалоговой панели с элементом управления главной панели
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Как упомянуто в [Элементы управления "Главная панель" и полосы](../mfc/rebar-controls-and-bands.md), каждая полоса может содержать только одно дочернее окно \(или элемент управления\).  Это может быть ограничением, если требуется наличие более чем одно дочернее окно на полосу.  Ошибка удобной создать ресурс диалоговой панели с несколькими элементами управления, а затем добавить полоса главной панели \(с диалоговую панель\) к элементу управления "Главная панель".  
  
 Обычно при необходимости полосу диалоговой панели быть прозрачными, необходимо установить для расширенный стиль **WS\_EX\_TRANSPARENT** для объекта диалоговой панели.  Однако поскольку **WS\_EX\_TRANSPARENT** имеет некоторые проблемы с правильно рисование фон диалоговой панели, потребуется дополнительная работа нижняя для достижения желательного результата.  
  
 Следующая процедура подробно шаги, которые достигл прозрачности без использования расширенных стилей **WS\_EX\_TRANSPARENT**.  
  
### Реализовать прозрачную диалоговую столбец на полосе главной панели  
  
1.  С помощью [Добавьте диалоговое окно класса](../mfc/reference/adding-an-mfc-class.md), добавьте новый класс \(например, `CMyDlgBar`\), реализует этот объект диалоговой панели.  
  
2.  Добавьте обработчик для сообщения `WM_ERASEBKGND`.  
  
3.  В новый обработчик измените существующий код в соответствии с следующим образом:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/CPP/using-a-dialog-bar-with-a-rebar-control_1.cpp)]  
  
4.  Добавьте обработчик для сообщения `WM_MOVE`.  
  
5.  В новый обработчик измените существующий код в соответствии с следующим образом:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/CPP/using-a-dialog-bar-with-a-rebar-control_2.cpp)]  
  
 Новых обработчиков имитируют прозрачность диалоговой панели, переадресовать сообщение `WM_ERASEBKGND` к родительскому окну и реализации обновления каждый раз, когда объект диалоговой панели перемещен.  
  
## См. также  
 [Использование CReBarCtrl](../Topic/Using%20CReBarCtrl.md)   
 [Элементы управления](../mfc/controls-mfc.md)