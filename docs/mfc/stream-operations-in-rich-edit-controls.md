---
title: "Поток операций в элементы управления Rich Edit | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CRichEditCtrl class [MFC], stream operations
- CRichEditCtrl class [MFC], stream storage
- rich edit controls [MFC], stream operations
- storage, stream in CRichEditCtrl
- stream operations in CRichEditCtrl
- stream storage and CRichEditCtrl
ms.assetid: 110b4684-1e76-4ca6-9ef0-5bc8b2d93c78
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c1a73790124adbc1ff8a89290bf4e1d7a4fa6824
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="stream-operations-in-rich-edit-controls"></a>Потоковые операции с использованием элементов управления "Rich Edit"
Потоки можно использовать для передачи данных в таблицу или из элемента управления rich edit ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)). Поток определяется [EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) структуру, которая задает функцию обратного вызова, определяемые приложением и буфер.  
  
 Для чтения данных в форматированного редактирования (т. е. поток данных в), используйте [StreamIn](../mfc/reference/cricheditctrl-class.md#streamin) функции-члена. Элемент управления несколько раз вызывает функцию обратного вызова, определяемые приложением, которая передает часть данных в буфер каждый раз.  
  
 Чтобы сохранить содержимое форматированного ввода элемента управления (то есть поток данных out), можно использовать [StreamOut](../mfc/reference/cricheditctrl-class.md#streamout) функции-члена. Элемент управления многократно выполняет запись в буфер и затем вызывает функцию обратного вызова, определяемые приложением. Для каждого вызова функции обратного вызова сохраняет содержимое буфера.  
  
## <a name="see-also"></a>См. также  
 [Использование CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Элементы управления](../mfc/controls-mfc.md)

