---
title: "Класс ICommandPropertiesImpl | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
dev_langs:
- C++
helpviewer_keywords:
- ICommandPropertiesImpl class
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4fbcdd2647337b8e265d3d79e6c02c1698e54e33
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="icommandpropertiesimpl-class"></a>Класс ICommandPropertiesImpl
Предоставляет реализацию [ICommandProperties](https://msdn.microsoft.com/en-us/library/ms723044.aspx) интерфейса.  
  
## <a name="syntax"></a>Синтаксис

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ICommandPropertiesImpl   
   : public ICommandProperties, public CUtlProps<PropClass>  
```  
  
#### <a name="parameters"></a>Параметры  
 `T`  
 Класс, производный от  
  
 `PropClass`  
 Класс свойств.  
  
## <a name="members"></a>Участники  
  
### <a name="interface-methods"></a>Методы интерфейса  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/icommandpropertiesimpl-getproperties.md)|Возвращает список свойств в группе свойств набора строк, в настоящее время запрос для набора строк.|  
|[SetProperties](../../data/oledb/icommandpropertiesimpl-setproperties.md)|Задает свойства в группе свойств набора строк.|  
  
## <a name="remarks"></a>Примечания  
 Это обязательная для команды. Реализация обеспечивается статическую функцию, определяемую [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) макрос.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldb.h  
  
## <a name="see-also"></a>См. также  
 [Шаблоны поставщика OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Архитектура шаблона поставщика OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)