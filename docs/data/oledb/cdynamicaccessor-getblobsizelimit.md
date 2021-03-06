---
title: CDynamicAccessor::GetBlobSizeLimit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDynamicAccessor::GetBlobSizeLimit
- CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor::GetBlobSizeLimit
- GetBlobSizeLimit
- ATL.CDynamicAccessor.GetBlobSizeLimit
dev_langs:
- C++
helpviewer_keywords:
- GetBlobSizeLimit method
ms.assetid: 7131e7c4-6e05-42f3-9d87-110301b672f2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 69eeae3d25f8db631e78971c8dcbb5befa63fb45
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicaccessorgetblobsizelimit"></a>CDynamicAccessor::GetBlobSizeLimit
Получает максимальный размер большого двоичного ОБЪЕКТА в байтах.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
const DBLENGTH GetBlobSizeLimit() const;  
  
```  
  
## <a name="remarks"></a>Примечания  
 Возвращает значение обработка большого двоичного ОБЪЕКТА `nBlobSize` задается [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md).  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldbcli.h  
  
## <a name="see-also"></a>См. также  
 [Класс CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)