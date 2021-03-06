---
title: "Вложение активного документа | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 16c0311c3eedc13cbc47214b44fc8810dee3eecd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="active-document-containment"></a>Вложение активного документа
Вложение активного документа — это технология, которая предоставляет один кадр, в котором для работы с документами, чтобы вам создать и использовать несколько кадров приложения для каждого типа документа. Он отличается от основные технологии OLE, в том, что технологии OLE с внедренными объектами внутри составного документа, в котором может быть активна только одним элементом содержания. С вложение активного документа активировать всего документа (то есть всего приложения, включая связанные меню, панелей инструментов и т. д) в контексте одного кадра.  
  
 Технология вложения активного документа было разработано для Microsoft Office, чтобы реализовать Office Binder. Тем не менее технология обладает достаточной гибкостью для поддержки контейнеры активных документов, кроме Office Binder и может поддерживать серверы документа, отличные от приложений Office и совместимыми с Microsoft Office.  
  
 Приложение, которое содержит активные документы вызывается [контейнер активного документа](../mfc/active-document-containers.md). Примерами таких контейнеров являются Microsoft Office Binder или Microsoft Internet Explorer.  
  
 Вложение активного документа реализуется как набор расширений OLE документы, технологии составных документов OLE. Все модули, дополнительные интерфейсы, позволяющие объекта встраиваемая, на месте для представления всего документа вместо одну часть встроенного содержимого. С помощью OLE-документы, вложения активного документа использует контейнер, содержащий места на экране для активных документов и серверов, которые предоставляют возможности интерфейса и обработка данных пользователя для самих активных документов.  
  
 [Сервера активных документов](../mfc/active-document-servers.md) является приложения (например, Word, Excel или PowerPoint), поддерживающий один или несколько классов активного документа, где каждый объект сам поддерживает интерфейсы расширения, которые позволяют объект активации в подходящего контейнера.  
  
 [Активного документа](../mfc/active-documents.md) (предоставляется с сервера активных документов, таких как Microsoft Word или Excel) является фактически обычных, полномасштабных документ, который внедряется в виде объекта в другой контейнер активного документа. В отличие от внедренных объектов активные документы имеют полный контроль над ними страницы и полный интерфейс приложения (со всеми его базовой команды и инструменты) доступно для пользователей, чтобы изменить их.  
  
 Активный документ наилучшим образом воспринимает ее отличия от стандартных внедренного объекта OLE. Внедренный объект — это то, отображается на странице документа, который является его владельцем соглашению OLE и документов осуществляется с OLE-контейнер. Контейнер хранит данные внедренного объекта с оставшейся частью документа. Тем не менее внедренные объекты ограничены, так как они не управляют страницы, на котором они появляются.  
  
 Пользователи приложения контейнера активного документа можно создать активные документы (разделах Office Binder) (если эти приложения могут включить активного документа), с помощью приложений, но пользователи могут управлять итоговый проект как одной сущности, который может быть уникальное имя, сохранить, печати и т. д. Таким же образом пользователь Интернет-браузер может рассматривать всей сети, а также локальной файловой системы, в качестве хранилища сущности одного документа возможность просматривать документы в этом хранилище из одного места.  
  
## <a name="sample-programs"></a>Примеры программ  
  
-   [MFCBIND](../visual-cpp-samples.md) образце показана реализация приложения с контейнером активных документов.  
  
## <a name="see-also"></a>См. также  
 [MFC COM](../mfc/mfc-com.md)

