---
title: "Использование MFC исходные файлы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- public members
- source files
- MFC, source files
- MFC source files
- comments, MFC
- private member access
- protected member access
- source files, MFC
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 930c205ffd690c190f68766f7a51c83b68ef8d2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="using-the-mfc-source-files"></a>Использование файлов с исходным кодом MFC
Библиотека Microsoft Foundation Class (MFC) предоставляет полный исходный код. Файлы заголовков (.h) находятся в каталоге \atlmfc\include; файлы реализации (.cpp) находятся в каталоге \atlmfc\src\mfc.  
  
 Этот сборник статей объясняется условные обозначения, MFC использует преобразовывать в комментарии различные части каждого класса, что означают эти комментарии и что следует ожидать, что поиск в каждом разделе. Мастеров Visual C++ используйте аналогичные соглашения для классов, которые они создали для вас и, возможно, полезные эти соглашения для собственного кода.  
  
 Возможно, вы знакомы с **открытый**, `protected`, и `private` ключевые слова C++. При просмотре файлы заголовков MFC, вы обнаружите, что каждый класс может иметь несколько каждого из них. Например, открытый член переменные и функции, можно в списке более одного **открытый** ключевое слово. Это происходит потому MFC разделяет переменные-члены и функции в зависимости от их использования не по типу разрешенного доступа. MFC использует `private` минимально; даже те элементы считаются детали реализации обычно защищаются и многократно являются открытыми. Несмотря на то, что доступ к детали реализации не рекомендуется, MFC оставляет решение для вас.  
  
 В исходных файлах MFC и файлы, которые мастер приложений MFC создает вы найдете комментарии подобные внутри объявления класса (обычно в указанном порядке):  
  
 `// Constructors`  
  
 `// Attributes`  
  
 `// Operations`  
  
 `// Overridables`  
  
 `// Implementation`  
  
 В этот сборник статей рассматриваются:  
  
-   [Пример комментариев](../mfc/an-example-of-the-comments.md)  
  
-   [/ / Комментарий реализации](../mfc/decrement-implementation-comment.md)  
  
-   [/ / Комментарий конструкторов](../mfc/decrement-constructors-comment.md)  
  
-   [/ / Комментарий атрибутов](../mfc/decrement-attributes-comment.md)  
  
-   [/ / Комментарий операций](../mfc/decrement-operations-comment.md)  
  
-   [/ / Комментарий Переопределяемости](../mfc/decrement-overridables-comment.md)  
  
## <a name="see-also"></a>См. также  
 [Общие разделы по MFC](../mfc/general-mfc-topics.md)

