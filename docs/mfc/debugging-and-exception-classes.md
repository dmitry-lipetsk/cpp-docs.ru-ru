---
title: "Классы исключений для отладки и | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.debug
dev_langs: C++
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 622e6d04a567668ebfd2c737c5cdde1c2ea09b35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="debugging-and-exception-classes"></a>Классы для отладки и работы с исключениями
Эти классы обеспечивают поддержку для отладки динамическое выделение памяти и для передачи информации об исключении из функции, где исключения функции где перехватывается.  
  
 Используйте классы [CDumpContext](../mfc/reference/cdumpcontext-class.md) и [CMemoryState](../mfc/reference/cmemorystate-structure.md) во время разработки в целях отладки, как описано в [отладки приложения MFC](/visualstudio/debugger/mfc-debugging-techniques). Используйте [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) определение класса любого объекта во время выполнения, как описано в статье [доступ к сведениям о классе во время выполнения](../mfc/accessing-run-time-class-information.md). Платформа использует `CRuntimeClass` для динамического создания объектов определенного класса.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о классе](../mfc/class-library-overview.md)

