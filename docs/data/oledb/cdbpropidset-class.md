---
title: "Класс CDBPropIDSet | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 32048b9f8e6ab528a3a31ed475cfb2725c20918e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="cdbpropidset-class"></a>Класс CDBPropIDSet
Наследует от **DBPROPIDSET** структуры и добавляет конструктор, который инициализирует ключевых полей и [AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md) доступ к методу.  
  
## <a name="syntax"></a>Синтаксис

```cpp
class CDBPropIDSet : public tagDBPROPIDSET  
```  
  
## <a name="members"></a>Участники  
  
### <a name="methods"></a>Методы  
  
|||  
|-|-|  
|[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)|Добавляет свойство идентификатор набора свойств.|  
|[CDBPropIDSet](../../data/oledb/cdbpropidset-cdbpropidset.md)|Конструктор.|  
|[SetGUID](../../data/oledb/cdbpropidset-setguid.md)|Задает идентификатор GUID для свойства идентификатора набора.|  
  
### <a name="operators"></a>Операторы  
  
|||  
|-|-|  
|[оператор =](../../data/oledb/cdbpropidset-operator-equal.md)|Назначает содержимого идентификатор свойства набора в другой.|  
  
## <a name="remarks"></a>Примечания  
 Используйте потребителей OLE DB **DBPROPIDSET** структуры можно передать массив идентификаторов свойств, для которых необходимо получить сведения о свойстве. Свойства, определенные в одном [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) структуры принадлежат набору одно свойство.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldbcli.h  
  
## <a name="see-also"></a>См. также  
 [Шаблоны потребителя OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Ссылка на шаблоны объекта-получателя OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)