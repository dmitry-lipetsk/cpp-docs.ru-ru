---
title: "PROPERTY_INFO_ENTRY | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROPERTY_INFO_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- PROPERTY_INFO_ENTRY macro
ms.assetid: f7bd23d6-52b4-4d6a-aa9a-1fca9834c8dc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d660a969937e3e75784516e3b50fbfe2690f9d3c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="propertyinfoentry"></a>PROPERTY_INFO_ENTRY
Представляет конкретное свойство в наборе свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
PROPERTY_INFO_ENTRY(dwPropID)  
  
```  
  
#### <a name="parameters"></a>Параметры  
 *dwPropID*  
 [входные данные] Значение [DBPROPID](https://msdn.microsoft.com/en-us/library/ms723882.aspx) , которое может использоваться вместе с GUID набора свойств для идентификации свойства.  
  
## <a name="remarks"></a>Примечания  
 Этот макрос задает в качестве значения свойства типа `DWORD` значение по умолчанию, определенное в ATLDB.H. Чтобы задать свойству нужное вам значение, используйте [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Чтобы задать одновременно [VARTYPE](http://msdn.microsoft.com/en-us/317b911b-1805-402d-a9cb-159546bc88b4) и [DBPROPFLAGS](https://msdn.microsoft.com/en-us/library/ms724342.aspx) для свойства, используйте [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
## <a name="example"></a>Пример  
 См. раздел [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldb.h  
  
## <a name="see-also"></a>См. также  
 [Макросы для шаблонов поставщика OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Шаблоны поставщика OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Архитектура шаблона поставщика OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Создание поставщика OLE DB](../../data/oledb/creating-an-ole-db-provider.md)