---
title: "Вкладки и вкладку управления атрибутами | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d10db5f1282c726b30536be35b348d50c8bb4a14
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="tabs-and-tab-control-attributes"></a>Вкладки и атрибуты элемента управления "Вкладка"
У вас есть много возможностей управления внешним видом и поведением вкладок, составляющих набор вкладок ([CTabCtrl](../mfc/reference/ctabctrl-class.md)). Каждая вкладка может содержать метку, значок, состояние элемента и 32-разрядное значение, определенное приложением связанные с ним. Для каждой вкладки можно отображать значок, метку или оба.  
  
 Кроме того, каждый элемент вкладка может иметь три возможных состояний: активная, ненажатое или выделяются. Это состояние может устанавливаться только путем изменения существующего элемента вкладки. Чтобы изменить существующий элемент вкладки, получить его с помощью вызова [GetItem](../mfc/reference/ctabctrl-class.md#getitem), изменить `TCITEM` структуры (в частности **dwState** и **dwStateMask** члены данных ) и затем возвращают измененной `TCITEM` структуры с помощью вызова [SetItem](../mfc/reference/ctabctrl-class.md#setitem). Если необходимо снять состояния элементов из всех элементов вкладки в `CTabCtrl` объекта, вызовите [DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall). Эта функция сбрасывает состояние все вкладки или все элементы, кроме того, выбранного в данный момент.  
  
 В следующем коде очищает состояние элементов вкладки и затем изменяет состояние третий элемент:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]  
  
 Дополнительные сведения об атрибутах на вкладке см. в разделе [вкладки и атрибуты вкладку](http://msdn.microsoft.com/library/windows/desktop/bb760550) в Windows SDK. Дополнительные сведения о добавлении вкладок элемента управления tab см. в разделе [Добавление вкладок в элемент управления вкладки](../mfc/adding-tabs-to-a-tab-control.md) далее в этом разделе.  
  
## <a name="see-also"></a>См. также  
 [Использование CTabCtrl](../mfc/using-ctabctrl.md)   
 [Элементы управления](../mfc/controls-mfc.md)

