---
title: "IRowsetChangeImpl::SetData | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SetData
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
dev_langs:
- C++
helpviewer_keywords:
- SetData method
ms.assetid: 81e1dd0a-0518-440c-8808-cee76e4929c7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cc6757fde591e3108ac02da00793406f0eb28165
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetchangeimplsetdata"></a>IRowsetChangeImpl::SetData
Задает значения данных в одном или нескольких столбцах.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
      STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>Параметры  
 В разделе [IRowsetChange::SetData](https://msdn.microsoft.com/en-us/library/ms721232.aspx) в *справочника программиста OLE DB*.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldb.h  
  
## <a name="see-also"></a>См. также  
 [Класс IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)