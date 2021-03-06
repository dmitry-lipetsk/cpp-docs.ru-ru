---
title: "MFC и ATL | Документы Microsoft"
ms.custom: 
ms.date: 01/24/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 31b1a3a8-4154-4c4a-af10-fafc23ecdc5c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1b863b002f6ab8362ed51e8cb16747de53eeb1b8
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="mfc-and-atl"></a>MFC и ATL
Классы Microsoft Foundation Classes (MFC) предоставляют объектно-ориентированную оболочку C++ для Win32 для быстрого создания классических приложений в машинном коде. Active Template Library (ATL) — это библиотека оболочки, которая упрощает разработку COM и широко используется для создания элементов управления ActiveX.  
  
Программы MFC или ATL можно создавать в выпуске Visual Studio Community или более поздней версии. Выпуски Express не поддерживают MFC и ATL. 

В Visual Studio 2015 Visual C++ — это необязательный компонент, а компоненты MFC и ATL являются необязательными компонентами в составе Visual C++. Если эти компоненты не выбраны, при установке Visual Studio будет предложено установить их при первой попытке создать или открыть проект MFC или ATL.  

В Visual Studio 2017 г. и более поздних версиях MFC и ATL являются необязательными компонентами в **разработки настольных приложений с помощью C++** рабочей нагрузки в программе установщик Visual Studio. Можно установить поддержку ATL без использования MFC или объединить поддержка MFC и ATL (MFC зависит от библиотеки ATL). Дополнительные сведения о рабочих нагрузок и компонентах см. в разделе [установить Visual Studio 2017 г.](/visualstudio/install/install-visual-studio).
  
## <a name="related-articles"></a>Связанные статьи  
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Приложения MFC для рабочего стола](../mfc/mfc-desktop-applications.md)|Классы Microsoft Foundation Classes предоставляют тонкую объектно-ориентированную оболочку для Win32, которая позволяет быстро создавать приложения с графическим пользовательским интерфейсом на языке C++.|  
|[Компоненты ATL COM Desktop](../atl/atl-com-desktop-components.md)|Библиотека ATL предоставляет шаблоны классов и другие конструкции, упрощающие создание COM-объектов на C++.|  
|[ATL и MFC общие классы](../atl-mfc-shared/atl-mfc-shared-classes.md)|Ссылки на [CStringT Class](../atl-mfc-shared/reference/cstringt-class.md) и другие общие классы MFC и ATL.|  
|[Работа с файлами ресурсов](../windows/working-with-resource-files.md)|Редактор ресурсов позволяет изменять ресурсы пользовательского интерфейса, такие как строки, изображения и диалоговые окна.|  
|[Visual C++](../visual-cpp-in-visual-studio.md)|Родительский раздел для всего контента, посвященного C++, в библиотеке MSDN.|