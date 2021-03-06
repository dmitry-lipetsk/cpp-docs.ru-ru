---
title: "IGetDataSourceImpl::GetDataSource | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
dev_langs:
- C++
helpviewer_keywords:
- GetDataSource method
ms.assetid: b70995d2-b951-452e-a2d4-fb3eb085886e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7a41d6600fc48c530e79a7a2632752e35211becc
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="igetdatasourceimplgetdatasource"></a>IGetDataSourceImpl::GetDataSource
Возвращает указатель интерфейса на объект источника данных, для которого был создан сеанс.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
      STDMETHOD(GetDataSource)(REFIID riid,   
   IUnknown ** ppDataSource);  
```  
  
#### <a name="parameters"></a>Параметры  
 В разделе [IGetDataSource::GetDataSource](https://msdn.microsoft.com/en-us/library/ms725443.aspx) в *справочника программиста OLE DB*.  
  
## <a name="remarks"></a>Примечания  
 Полезно, если необходимо получить доступ к свойствам в объекте источника данных.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldb.h  
  
## <a name="see-also"></a>См. также  
 [Класс IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)