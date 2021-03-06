---
title: "Вопросы проектирования архитектуры OLE DB | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b894ec1cbd227663d46e98e523ffe8c1c5d84475
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/03/2018
---
# <a name="ole-db-architectural-design-issues"></a>Вопросы проектирования архитектуры OLE DB
Перед запуском приложения OLE DB необходимо учитывать следующие аспекты:  
  
 **Какой язык программирования будет использоваться для создания вашего приложения OLE DB?**  
 Корпорация Майкрософт предлагает несколько библиотек для выполнения этой задачи: библиотека шаблонов OLE DB, атрибуты OLE DB и необработанные интерфейсы OLE DB в пакете SDK OLE DB. Кроме того существуют мастеры, помогающие при написании программы. Эти реализации описаны в [шаблонов OLE DB, атрибуты и другие реализации](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md).  
  
 **Необходимо указать собственный поставщик?**  
 Большинство разработчиков не требуется написание собственного поставщика. Корпорация Майкрософт предоставляет несколько поставщиков. При каждом создании подключение данных (например, при добавлении объекта-получателя к проекту, используя мастер потребителя ATL OLE DB), **свойства связи данных** диалоговое окно содержит список всех доступных поставщиков, зарегистрированных в системе. Если один из этих поставщиков подходит для данных хранилища и данные доступа приложения, проще всего будет используйте одну из следующих. Если хранилище данных не соответствует ни одной из этих категорий, необходимо создать собственный поставщик. Сведения о создании поставщиков см. в разделе [шаблоны поставщика OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md).  
  
 **Какой уровень поддержки требуется вашему получателю?**  
 Некоторым пользователям может быть очень простой; а другие могут быть очень сложными. Функциональность объектов OLE DB определяется свойствами. При использовании мастера потребителя ATL OLE DB для создания объекта-получателя или баз данных поставщика мастера для создания поставщика устанавливает соответствующий объект свойства, представляющие стандартный набор функциональности. Тем не менее, если созданный мастером классы поставщика или получателя не поддерживают все, что нужно сделать, необходимо ссылаться интерфейсов для этих классов в [библиотека шаблонов OLE DB](../../data/oledb/ole-db-templates.md). Эти интерфейсы преобразуют необработанные интерфейсы OLE DB, предоставляя дополнительную реализацию упрощает их использование для вас.  
  
 Например, если вы хотите обновить данные в наборе строк, но вы забыли указать это при создании получателя с помощью мастера, можно указать функциональные возможности после их проведения, задав **DBPROP_IRowsetChange** и  **DBPROP_UPDATABILITY** свойства в объекте command. Затем, при создании набора строк, он имеет `IRowsetChange` интерфейса.  
  
 **У вас есть старого кода с помощью другой технологии доступа к данным (ADO, ODBC или DAO)?**  
 Анализ возможных комбинаций технологий (например, использование компонентов ADO с компонентами OLE DB и миграция кода ODBC в OLE DB), охватывают все ситуации выходит за рамки документации по Visual C++. Однако во многих статьях, в которых рассматриваются различные сценарии доступны на следующих веб-сайтах корпорации Майкрософт:  
  
-   [Центр справки и поддержки Майкрософт](http://go.microsoft.com/fwlink/p/?linkid=148218)  
  
-   [Обзор технических статей для доступа к данным Microsoft](http://go.microsoft.com/fwlink/p/?linkid=148217)  
  
-   [Центр решений Visual Studio](http://go.microsoft.com/fwlink/p/?linkid=148215)  
  
-   [Поиск Microsoft.com](http://search.microsoft.com/)  
  
 При выполнении поиска введите комбинацию ключевых слов для оптимально подходит для вашего сценария; Например: Если вы используете объекты ADO с поставщиком OLE DB, попробуйте поиска логических с **ADO и «OLE DB»**. Если вы хотите перенести старого кода DAO для ODBC, выберите «все слова» и укажите строки, например **перенос DAO**.  
  
## <a name="see-also"></a>См. также  
 [Программирование объектов OLE DB](../../data/oledb/ole-db-programming.md)   
 [Общие сведения о программировании OLE DB](../../data/oledb/ole-db-programming-overview.md)