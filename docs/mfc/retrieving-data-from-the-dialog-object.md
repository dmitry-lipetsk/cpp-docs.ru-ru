---
title: "Извлечение данных из объекта диалогового окна | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes [MFC], retrieving user data
- dialog box data [MFC]
- data [MFC], retrieving
- GetDlgItemText method [MFC]
- SetDlgItemText method [MFC]
- SetWindowText method [MFC]
- dialog box data [MFC], retrieving
- retrieving data [MFC]
- user input [MFC], retrieving from MFC dialog boxes
- capturing user input [MFC]
- dialog box controls [MFC], initializing values
- DDX (dialog data exchange) [MFC]
- MFC dialog boxes [MFC], retrieving user input
- data retrieval [MFC], dialog boxes
- data [MFC], dialog boxes
- DDX (dialog data exchange) [MFC], about DDX
- DDX (dialog data exchange) [MFC], retrieving data from Dialog object
- GetWindowText method [MFC]
ms.assetid: bdca2b61-6b53-4c2e-b426-8712c7a38ec0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d4b50ae3036a6f262312c7a05c2de093a977a588
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="retrieving-data-from-the-dialog-object"></a>Извлечение данных из объекта диалогового окна
Платформа предоставляет простой способ для инициализации значений элементов управления в диалоговом окне и для извлечения значений из элементов управления. Более сложным вручную подходом является вызов функций, таких как `SetDlgItemText` и `GetDlgItemText` функции-члены класса `CWnd`, применяемых для элемента управления windows. При использовании этих функций, доступе к каждого элемента управления отдельно, чтобы задать или получить его значение вызова таких функций как `SetWindowText` и `GetWindowText`. Платформа framework подхода автоматизирует инициализации и извлечения.  
  
 Обмен данными (диалоговых окон DDX) позволяет упростить обмен данными между элементами управления в диалоговом окне переменных поле и член в объекте диалогового окна. Это exchange работает обоими способами. Для инициализации элементов управления в диалоговом окне, можно задать значения членов данных в объекте диалогового окна, а платформа передачи значения для элементов управления, прежде чем откроется диалоговое окно. Вы можете в любой момент обновить элементы данных диалогового окна с данными, введенные пользователем. В этот момент можно использовать данные с помощью ссылки на переменные члена данных.  
  
 Можно также расположить значения элементов управления диалогового окна проверки автоматически с проверка данных диалогового окна (DDV).  
  
 DDX и DDV рассматриваются более подробно в [обмен данными диалоговых окон и проверка](../mfc/dialog-data-exchange-and-validation.md).  
  
 Для модального диалогового окна, можно получить все данные, введенные пользователем, когда `DoModal` возвращает **IDOK** , но перед диалогового окна объект удаляется. Для немодального диалогового окна, можно получить данные из объекта диалогового окна в любое время путем вызова `UpdateData` с аргументом **TRUE** и последующий доступ к переменные-члены класса диалогового окна. Этой теме рассматривается более подробно в [обмен данными диалоговых окон и проверка](../mfc/dialog-data-exchange-and-validation.md).  
  
## <a name="see-also"></a>См. также  
 [Жизненный цикл диалогового окна](../mfc/life-cycle-of-a-dialog-box.md)

