---
title: "IDBCreateSessionImpl::CreateSession | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
dev_langs:
- C++
helpviewer_keywords:
- CreateSession method
ms.assetid: 035e5ddb-56e6-43b1-874d-89c0e40b103b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 566bcc80c141ee808c8a7f583c1e92fd6b62256e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="idbcreatesessionimplcreatesession"></a>IDBCreateSessionImpl::CreateSession
Создает новый сеанс из объекта источника данных и возвращает запрошенный интерфейс на только что созданного сеанса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
      STDMETHOD(CreateSession)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppDBSession);  
```  
  
#### <a name="parameters"></a>Параметры  
 В разделе [IDBCreateSession::CreateSession](https://msdn.microsoft.com/en-us/library/ms714942.aspx) в *справочника программиста OLE DB*.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldb.h  
  
## <a name="see-also"></a>См. также  
 [Класс IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)