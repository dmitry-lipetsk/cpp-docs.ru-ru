---
title: "Реализация точки подключения (Visual C++) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Implement Connection Point Wizard [C++]
- connection points [C++], implementing
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ab065c78d8ea5d2de105abdc2fa651e05f9d1875
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-a-connection-point-visual-c"></a>Реализация точки подключения (Visual C++)
Чтобы реализовать точку подключения с помощью мастера реализации точек подключения, необходимо создан проект как COM-приложение ATL или как приложение MFC с поддержкой ATL. Можно использовать [мастер проектов ATL](../atl/reference/atl-project-wizard.md) для создания приложения ATL или [добавить объект ATL в приложение MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) для реализации поддержки ATL в приложении MFC.  
  
> [!NOTE]
>  Сведения о реализации точек подключения для проекта MFC см. в разделе [точки подключения](../mfc/connection-points.md).  
  
 После создания проекта, чтобы реализовать точку соединения, необходимо сначала добавить объект ATL. В разделе [Добавление объекты и элементы управления в проект ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) список мастеров для добавления объектов в проекты ATL.  
  
> [!NOTE]
>  Мастер не поддерживает диалоговые окна ATL, XML-веб-служб, созданных с помощью сервера ATL, объекты производительности и счетчики производительности.  
  
 Доступный для соединения объект (то есть источник) может предоставлять точку подключения для каждого из исходящих интерфейсов. Каждый исходящий интерфейс может быть реализован клиента в объекте (то есть приемника). Дополнительные сведения см. в разделе [точки подключения ATL](../atl/atl-connection-points.md).  
  
### <a name="to-implement-a-connection-point"></a>Реализация точки подключения  
  
1.  В представлении классов щелкните правой кнопкой мыши имя класса объекта ATL.  
  
2.  Нажмите кнопку **добавить** из контекстного меню и нажмите кнопку **добавить точку подключения** для отображения [мастер реализации точек подключения](../ide/implement-connection-point-wizard.md).  
  
3.  Выберите интерфейсы точки подключения для реализации из соответствующих библиотек типов и нажмите кнопку **Готово**.  
  
4.  В представлении классов проверьте классы прокси, создаваемые для каждой точки подключения. Классы отображаются в виде CProxy*InterfaceName*\<T > и являются производными от [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md).  
  
5.  Дважды щелкните класс точки подключения для отображения определения класса точки подключения.  
  
    -   При реализации точки подключения для интерфейса собственного проекта, появится следующее определение:  
  
        ```  
        template< class T >  
        class CProxyInterfaceName :  
           public IConnectionPointImpl< T, &IID_InterfaceName >  
        {  
        public:  
        };  
        ```  
  
         Если вы реализуете локальный интерфейс, методы и свойства отображаются в теле класса.  
  
    -   При реализации точки подключения для другого интерфейса, определение включает в себя методы интерфейса, перед каждым указывается `Fire_`.  
  
## <a name="see-also"></a>См. также  
 [Добавление функциональных возможностей с помощью мастеров кода](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Добавление точек подключения к объектам](../atl/adding-connection-points-to-an-object.md)