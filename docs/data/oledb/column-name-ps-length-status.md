---
title: "COLUMN_NAME_PS_LENGTH_STATUS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- COLUMN_NAME_PS_LENGTH_STATUS
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_NAME_PS_LENGTH_STATUS macro
ms.assetid: a1a2e2ca-f0ae-4896-8aa3-67a96c270b05
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fbaad78bfcbd33d0f4c4c99f8848fc6c6bab01be
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="columnnamepslengthstatus"></a>COLUMN_NAME_PS_LENGTH_STATUS
Представляет привязку в наборе строк для конкретного столбца в наборе строк. Аналогично [COLUMN_NAME](../../data/oledb/column-name.md), за исключением того, что этот макрос также принимает точность, масштаб, длину столбца и состояние столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszName`  
 [in] Указатель на имя столбца. Имя должно быть строкой в Юникоде. Это можно сделать, поместив «L» перед именем, например: `L"MyColumn"`.  
  
 `nPrecision`  
 [in] Максимальная точность столбца, который требуется выполнить привязку.  
  
 `nScale`  
 [in] Масштаб столбца, необходимо выполнить привязку.  
  
 `data`  
 [in] Соответствующего члена данных в записи пользователя.  
  
 *length*  
 [in] Переменная может быть привязано к длина столбца.  
  
 *status*  
 [in] Переменная может быть привязано к состояние столбца.  
  
## <a name="remarks"></a>Примечания  
 В разделе [COLUMN_NAME](../../data/oledb/column-name.md) сведения о том, где **COLUMN_NAME_\***  используются макросы.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldbcli.h  
  
## <a name="see-also"></a>См. также  
 [Макросы и глобальные функции для шаблонов потребителей OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_NAME](../../data/oledb/column-name.md)   
 [COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)