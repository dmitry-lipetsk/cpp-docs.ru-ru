---
title: "Стили элемента управления дерева | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
dev_langs: C++
helpviewer_keywords:
- TVS_LINESATROOT [MFC]
- styles [MFC], CTreeCtrl
- styles [MFC], tree control
- TVS_HASLINES
- TVS_SINGLEEXPAND
- CTreeCtrl class [MFC], styles
- TVS_EDITLABELS [MFC]
- TVS_NOTOOLTIPS [MFC]
- TVS_HASBUTTONS [MFC]
- tree controls [MFC], styles
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c141a2b0db673f8d3c5f2c116de5b5d2ec81a8ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-styles"></a>Стили древовидного элемента управления
Дерево элемента управления ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) стили определяют внешний вид элемента управления дерева. Стили начальной задается при создании элемента управления дерева. Можно извлекать и изменение стилей после создания дерева на основе [GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584) и [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) функции Windows, указав **GWL_STYLE** для `nIndex` параметра. Полный список стилей см. в разделе [стили окна элемента управления представления дерева](http://msdn.microsoft.com/library/windows/desktop/bb760013) в Windows SDK.  
  
 **TVS_HASLINES** стиль расширяет графическое представление элемента управления дерева иерархии, рисование линий, которые связывают дочерних элементов с соответствующего родительского элемента. Этот стиль не содержит ссылок на элементы в корне иерархии. Чтобы сделать это, необходимо объединить **TVS_HASLINES** и **TVS_LINESATROOT** стили.  
  
 Пользователю можно развернуть или свернуть список дочерних элементов родительского элемента, дважды щелкнув родительского элемента. Дерево, которое имеет **TVS_SINGLEEXPAND** вызывает стиль элемента выбранного для развертывания и для элемента не выбранные для свертывания. Если указатель мыши одиночного щелчка выбранного элемента и закрыть этот элемент, будет расширен. Если выбранный элемент одним щелкнуть при открытом, будут объединены.  
  
 Дерево, которое имеет **TVS_HASBUTTONS** стиля добавляется кнопка в левой части каждый родительский элемент. Пользователь может щелкнуть кнопку, чтобы развернуть или свернуть дочерние элементы в качестве альтернативы для дважды щелкните родительский элемент. **TVS_HASBUTTONS** не добавляет кнопки элементов в корне иерархии. Чтобы сделать это, необходимо объединить **TVS_HASLINES**, **TVS_LINESATROOT**, и **TVS_HASBUTTONS**.  
  
 **TVS_EDITLABELS** стиль позволяет пользователю изменять метки составляющих элементов управления дерева. Дополнительные сведения об изменении меток см. в разделе [редактирование метки элемента управления дерева](../mfc/tree-control-label-editing.md) далее в этом разделе.  
  
 **TVS_NOTOOLTIPS** стиль отключает функцию tip автоматическое средство представления древовидных структур. Эта функция автоматически отображается всплывающая подсказка, содержащая заголовок элемента указателем мыши, если заголовка не видимую в данный момент.  
  
## <a name="see-also"></a>См. также  
 [Использование CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Элементы управления](../mfc/controls-mfc.md)

