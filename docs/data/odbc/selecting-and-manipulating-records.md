---
title: "Выбор и операции с записями | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dec5e0094405cf9d038e53959da97ba079736505
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="selecting-and-manipulating-records"></a>Выбор и операции с записями
Обычно при выборе записи из источника данных при помощи SQL **ВЫБЕРИТЕ** инструкции, получить результирующий набор, который представляет собой набор записей из таблицы или запроса. С классами баз данных можно использовать объект набора записей для выбора и получить доступ к результирующего набора. Это объект класса конкретного приложения, который является производным от класса [CRecordset](../../mfc/reference/crecordset-class.md). При определении класса набора записей источник данных для связи с, таблицы для использования и указываются столбцы таблицы. Мастер приложений MFC или **добавить класс** (как описано в [Добавление потребителя ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) создает класс с подключением к определенному источнику данных. Мастер прописывает [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) функции-члена класса `CRecordset` для получения имени таблицы. Дополнительные сведения об использовании мастеров для создания классов записей см. в разделе [Поддержка баз данных, мастер приложений MFC](../../mfc/reference/database-support-mfc-application-wizard.md) и [Добавление потребителя ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 С помощью [CRecordset](../../mfc/reference/crecordset-class.md) объекта во время выполнения, вы можете:  
  
-   Проверьте поля данных текущей записи.  
  
-   Отфильтровать или отсортировать набор записей.  
  
-   Настройка по умолчанию SQL **ВЫБЕРИТЕ** инструкции.  
  
-   Просмотрите выбранные записи.  
  
-   Добавить, обновить или удалить записи (если источник данных и набор записей являются обновляемыми).  
  
-   Проверка повторных набора записей и обновите данные о его содержимом.  
  
 После завершения работы с объектом набора записей, закройте и удалите его. Дополнительные сведения о наборах см. в разделе [записей (ODBC)](../../data/odbc/recordset-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [ODBC и MFC](../../data/odbc/odbc-and-mfc.md)