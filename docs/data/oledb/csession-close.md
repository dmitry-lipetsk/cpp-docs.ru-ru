---
title: "CSession::Close | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSession::Close
- ATL.CSession.Close
- CSession.Close
- ATL::CSession::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: dc36c4c0-e588-4c0b-91d1-fc7dc5c8e7f4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e48ee830cbe2a154a039767bd11805f10dbfabc1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="csessionclose"></a>CSession::Close
Закрывает сеанс, который был открыт, [CSession::Open](../../data/oledb/csession-open.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
void Close() throw();  
  
```  
  
## <a name="remarks"></a>Примечания  
 Выпуски **m_spOpenRowset** указателя.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldbcli.h  
  
## <a name="see-also"></a>См. также  
 [Класс CSession](../../data/oledb/csession-class.md)