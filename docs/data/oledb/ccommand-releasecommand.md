---
title: "CCommand::ReleaseCommand | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CCommand.ReleaseCommand
- ReleaseCommand
- CCommand::ReleaseCommand
dev_langs:
- C++
helpviewer_keywords:
- ReleaseCommand method
ms.assetid: 3b58230c-13d5-45c5-b43e-bb013ecc3019
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ae8035d25247fc640961f4ce7b5df62467fdf58
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="ccommandreleasecommand"></a>CCommand::ReleaseCommand
Освобождает доступа к параметру, затем освобождает саму команду.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
void CCommandBase::ReleaseCommand() throw();  
  
```  
  
## <a name="remarks"></a>Примечания  
 `ReleaseCommand` используется в сочетании с **закрыть**. В разделе [закрыть](../../data/oledb/ccommand-close.md) сведения об использовании.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldbcli.h  
  
## <a name="see-also"></a>См. также  
 [CCommand-класс](../../data/oledb/ccommand-class.md)   
 [CCommand::Close](../../data/oledb/ccommand-close.md)