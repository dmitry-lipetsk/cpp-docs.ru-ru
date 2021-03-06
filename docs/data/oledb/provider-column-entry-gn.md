---
title: "PROVIDER_COLUMN_ENTRY_GN | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROVIDER_COLUMN_ENTRY_GN
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_GN macro
ms.assetid: be77ba85-634c-4e28-832f-d2fa40413254
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 203f339dc031f4a21f16181043b051c4eaa5ec35
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="providercolumnentrygn"></a>PROVIDER_COLUMN_ENTRY_GN
Представляет отдельного столбца, поддерживаемых поставщиком.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
PROVIDER_COLUMN_ENTRY_GN (name  
, ordinal, flags, colSize, dbtype, precision, scale, guid )  
```  
  
#### <a name="parameters"></a>Параметры  
 *name*  
 [in] Имя столбца.  
  
 `ordinal`  
 [in] Номер столбца. Если столбец является столбцом закладки, номер столбца не должно быть 0.  
  
 `flags`  
 [in] Указывает, как данные возвращаются. В разделе `dwFlags` описание в [структуры DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 *colSize*  
 [in] Размер столбца.  
  
 `dbtype`  
 [in] Указывает тип данных значения. В разделе **wType** описание в [структуры DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 *precision*  
 [in] Указывающее точность для использования при получении данных, если *dbType* — `DBTYPE_NUMERIC` или **DBTYPE_DECIMAL**. В разделе **bPrecision** описание в [структуры DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 `scale`  
 [in] Указывает шкалу для использования при получении данных, если тип dbType `DBTYPE_NUMERIC` или **DBTYPE_DECIMAL**. В разделе **bScale** описание в [структуры DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 `guid`  
 GUID набора строк схемы. В разделе [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) в *Справочник программиста OLE DB* список наборов строк схемы и их идентификаторы GUID.  
  
## <a name="remarks"></a>Примечания  
 Позволяет указать размер столбца, тип данных, точность, масштаб и GUID набора строк схемы.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldb.h  
  
## <a name="see-also"></a>См. также  
 [Макросы для шаблонов поставщика OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Шаблоны поставщика OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Архитектура шаблона поставщика OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Создание поставщика OLE DB](../../data/oledb/creating-an-ole-db-provider.md)