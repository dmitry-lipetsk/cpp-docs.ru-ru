---
title: "CDynamicParameterAccessor::GetParamName | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicParameterAccessor::GetParamName
- ATL.CDynamicParameterAccessor.GetParamName
- GetParamName
- CDynamicParameterAccessor.GetParamName
- ATL::CDynamicParameterAccessor::GetParamName
dev_langs:
- C++
helpviewer_keywords:
- GetParamName method
ms.assetid: 707c08ed-d3d0-4ce8-b23e-20b07202a3e2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1b41b9f2daca1b6f4d911bfc64e675079bdee0e5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicparameteraccessorgetparamname"></a>CDynamicParameterAccessor::GetParamName
Возвращает имя указанного параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
      LPOLESTR GetParamName(DBORDINAL nParam) const throw();  
```  
  
#### <a name="parameters"></a>Параметры  
 `nParam`  
 [in] Номер параметра (начиная с 1). Параметр 0 зарезервирован для возвращаемых значений. Параметр с номером — это индекс параметра, в зависимости от порядка в SQL или хранимой процедуры. В разделе [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) в качестве примера.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Имя указанного параметра.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldbcli.h  
  
## <a name="see-also"></a>См. также  
 [Класс CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)