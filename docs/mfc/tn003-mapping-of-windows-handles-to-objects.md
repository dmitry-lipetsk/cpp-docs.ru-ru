---
title: "TN003. Сопоставление дескрипторов Windows с объектами | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mapping"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "схемы дескрипторов"
  - "сопоставления, дескрипторы Windows для объектов"
  - "TN003"
  - "дескрипторы Windows для объектов [C++]"
ms.assetid: fbea9f38-992c-4091-8dbc-f29e288617d6
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# TN003. Сопоставление дескрипторов Windows с объектами
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Эта заметка описаны процедуры MFC, поддерживающие дескрипторы объекта Windows сопоставления к объектам C C\+\+.  
  
## Проблема  
 Объекты Windows обычно представлены различными объектами [HANDLE](http://msdn.microsoft.com/library/windows/desktop/aa383751) объекта Windows использованих программы\-оболочек классов MFC обрабатывает с объектами C C\+\+.  Функции обертывания дескриптора библиотеки классов MFC позволяют найти объект C\+\+, который создает экземпляр объекта Windows, который имеет указанный дескриптор.  Однако иногда объект не является владельцем объекта оболочки C\+\+ и в этих случаях система создает временный объект для использования в качестве программа\-оболочка C C\+\+.  
  
 Объекты Windows, сопоставления дескрипторов использования следующим образом:  
  
-   HWND \([CWnd](../Topic/CWnd%20Class.md) и `CWnd`\- производные классы\)  
  
-   HDC \([CDC](../Topic/CDC%20Class.md) и `CDC`\- производные классы\)  
  
-   HMENU \([CMenu](../mfc/reference/cmenu-class.md)\)  
  
-   HPEN \([CGdiObject](../mfc/reference/cgdiobject-class.md)\)  
  
-   HBRUSH \(`CGdiObject`\)  
  
-   HFONT \(`CGdiObject`\)  
  
-   HBITMAP \(`CGdiObject`\)  
  
-   HPALETTE \(`CGdiObject`\)  
  
-   HRGN \(`CGdiObject`\)  
  
-   HIMAGELIST \([CImageList](../Topic/CImageList%20Class.md)\)  
  
-   СОКЕТ \([CSocket](../mfc/reference/csocket-class.md)\)  
  
 Данные дескриптор любого из этих объектов, можно найти объект MFC, дескриптор экземпляра, вызвав статический метод `FromHandle`.  Например, для вызова HWND `hWnd`, следующая линия возвращает указатель на `CWnd`, который создает экземпляры `hWnd`:  
  
```  
CWnd::FromHandle(hWnd)  
```  
  
 Если `hWnd` не имеет определенный объект оболочки, временное `CWnd` создается для создания `hWnd`.  Это позволяет получить допустимый объект C\+\+ из любого дескриптора.  
  
 После импорта объект оболочки можно извлекать его дескриптор из переменной открытые члены класс\-оболочки.  В случае `CWnd`, `m_hWnd` содержит HWND для этого объекта.  
  
## Вложение дескрипторы к объектам MFC  
 Данные вновь созданный объект дескриптор\- программы\-оболочки и дескриптор объекта Windows можно связать 2 путем вызова функции `Attach`, как в следующем примере:  
  
```  
CWnd myWnd;  
myWnd.Attach(hWnd);  
```  
  
 Это делает запись в постоянном сопоставлении сопоставляет `myWnd` и `hWnd`.  Вызов `CWnd::FromHandle(hWnd)` теперь возвращает указатель на `myWnd`.  При `myWnd` будет удалено, деструктор автоматически разрушит `hWnd` путем вызова функции [DestroyWindow](http://msdn.microsoft.com/library/windows/desktop/ms632682) Windows.  Если это не хотите, `hWnd` необходимо окончательно удалить из `myWnd` до `myWnd` уничтожается \(обычно и область, в которой задано `myWnd` \).  Метод `Detach` делает это.  
  
```  
myWnd.Detach();  
```  
  
## Дополнительные сведения о временных объектов  
 Временные объекты создаются при дают `FromHandle` дескриптор, который еще не содержит объект оболочки.  Эти временные объекты окончательно удаляются из их обработки и удаляются функциями `DeleteTempMap`.  По умолчанию [CWinThread::OnIdle](../Topic/CWinThread::OnIdle.md) автоматически вызывает `DeleteTempMap` для каждого класса, который поддерживает временные сопоставления дескрипторов.  Это означает, что нельзя приведено указатель на временный объект будет допустимым за точкой выхода из функции, полученного указателя.  
  
## Объекты и несколько потоков оболочки  
 И временные и постоянные объекты поддерживаются на уровне потока.  То есть один поток не может получать доступ к объектам программы\-оболочки C\+\+ другого потока, независимо от того, является ли он является временным или постоянным.  
  
 Чтобы передать эти объекты от одного потока к другому, всегда отправлять их как собственный тип `HANDLE`.  Передача объекта оболочки C\+\+ от одного потока к другому часто будет вызывать непредвиденные результаты.  
  
## См. также  
 [Технические примечания по номеру](../mfc/technical-notes-by-number.md)   
 [Технические примечания по категории](../mfc/technical-notes-by-category.md)