---
title: "BLOB_NAME | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BLOB_NAME
dev_langs:
- C++
helpviewer_keywords:
- BLOB_NAME macro
ms.assetid: 757acd0d-946d-447d-937e-94ecd700ba38
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 488c2f9cc2570ea5b512d0cf245902793d408dc5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="blobname"></a>BLOB_NAME
При использовании `BEGIN_COLUMN_MAP` и `END_COLUMN_MAP` для привязки больших двоичных объектов ([больших двоичных ОБЪЕКТОВ](https://msdn.microsoft.com/en-us/library/ms711511.aspx)). Аналогично [BLOB_ENTRY](../../data/oledb/blob-entry.md), за исключением того, что этот макрос принимает имя столбца, а не как число столбцов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
BLOB_NAME(pszName, IID, flags, data )  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszName`  
 [in] Указатель на имя столбца. Имя должно быть строкой в Юникоде. Это можно сделать, поместив «L» перед именем, например: `L"MyColumn"`.  
  
 *IID*  
 [in] Интерфейс GUID, таких как **IDD_ISequentialStream**, который применяется для получения большого двоичного ОБЪЕКТА.  
  
 `flags`  
 [in] Режим хранения помечается как определяются моделью структурированного хранения OLE (например, **STGM_READ**).  
  
 `data`  
 [in] Соответствующего члена данных в записи пользователя.  
  
## <a name="example"></a>Пример  
 В разделе [способ получения большого двоичного ОБЪЕКТА?](../../data/oledb/retrieving-a-blob.md).  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldbcli.h  
  
## <a name="see-also"></a>См. также  
 [Макросы и глобальные функции для шаблонов потребителей OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)   
 [BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)