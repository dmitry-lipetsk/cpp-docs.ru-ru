---
title: "Класс CNoMultipleResults | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CNoMultipleResults
- ATL.CNoMultipleResults
- ATL::CNoMultipleResults
dev_langs:
- C++
helpviewer_keywords:
- CNoMultipleResults class
ms.assetid: 343e77c4-b319-476e-b592-901ab9b2f34e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e936978c2904c378b3a652343b7b299f56b4acf4
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="cnomultipleresults-class"></a>Класс CNoMultipleResults
Используется в качестве аргумента шаблона (*тип TMultiple*) для [CCommand](../../data/oledb/ccommand-class.md) для создания оптимизированного команды, который обрабатывает один результирующий набор.  
  
## <a name="syntax"></a>Синтаксис

```cpp
class CNoMultipleResults  
```  
  
## <a name="remarks"></a>Примечания  
 Команда для обработки нескольких результирующих наборов, используйте [CMultipleResults](../../data/oledb/cmultipleresults-class.md) вместо него.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldbcli.h  
  
## <a name="see-also"></a>См. также  
 [Шаблоны потребителя OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Ссылка на шаблоны объекта-получателя OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)