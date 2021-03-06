---
title: "Введение в классы окон ATL | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: window classes
ms.assetid: 503efc2c-a269-495d-97cf-3fb300d52f3d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 636fe8aa87b6880f5cda77fb46fc481d99d78a81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="introduction-to-atl-window-classes"></a>Введение в классы окон ATL
Следующие классы ATL предназначены для реализации и управления окнами.  
  
-   [CWindow](../atl/reference/cwindow-class.md) позволяет присоединить дескриптор окна для `CWindow` объекта. Затем вызовите `CWindow` методы для управления окном.  
  
-   [CWindowImpl](../atl/reference/cwindowimpl-class.md) позволяет реализовать новое окно и обработки сообщений со схемой сообщений. Можно создать окно на основе нового класса, суперкласса существующий класс или подкласс Windows существующему окну.  
  
-   [CDialogImpl](../atl/reference/cdialogimpl-class.md) позволяет реализовать модального или немодального диалогового окна и обработать сообщения со схемой сообщений.  
  
-   [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md) — готовых класс, который реализует окно, содержащихся в схеме, в другом классе. С помощью `CContainedWindowT` позволяет централизовать обработки сообщений в одном классе.  
  
-   [CAxDialogImpl](../atl/reference/caxdialogimpl-class.md) позволяет реализовать диалоговое окно (модальные и немодальные), элементы управления ActiveX.  
  
-   [CSimpleDialog](../atl/reference/csimpledialog-class.md) позволяет реализовать модального диалогового окна с базовыми функциями.  
  
-   [CAxWindow](../atl/reference/caxwindow-class.md) позволяет реализовать окна, на котором размещается элемент управления ActiveX.  
  
-   [CAxWindow2T](../atl/reference/caxwindow2t-class.md) позволяет реализовать окна, на котором размещена лицензированный элемент управления ActiveX.  
  
 Наряду с конкретным окном классами библиотека ATL предоставляет несколько классов, предназначенных для упрощения реализации объекта ATL окна. Они приведены ниже:  
  
-   [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) управляет данными нового класса окна.  
  
-   [CWinTraits](../atl/reference/cwintraits-class.md) и [CWinTraitsOR](../atl/reference/cwintraitsor-class.md) предоставляют простой способ стандартизации признаки объект ATL окна.  
  
## <a name="see-also"></a>См. также  
 [Классы окон](../atl/atl-window-classes.md)

