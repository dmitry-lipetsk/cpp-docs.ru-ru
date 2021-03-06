---
title: "Общие (OpenMP) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Shared
dev_langs: C++
helpviewer_keywords: shared OpenMP clause
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 26f8618a0340216215c3432576b6adbba3e70f80
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="shared-openmp"></a>shared (OpenMP)
Указывает, что один или несколько переменных должны совместно используются всеми потоками.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
shared(var)  
```  
  
## <a name="remarks"></a>Примечания  
 где  
  
 `var`  
 Один для получения дополнительных переменные для совместного использования. Если указано более одной переменной, разделяйте имена переменных запятыми.  
  
## <a name="remarks"></a>Примечания  
 Другой способ совместного использования переменных потоков — с [copyprivate](../../../parallel/openmp/reference/copyprivate.md) предложения.  
  
 `shared`применяется к следующие директивы:  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [разделы](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Дополнительные сведения см. в разделе [2.7.2.4 общих](../../../parallel/openmp/2-7-2-4-shared.md).  
  
## <a name="example"></a>Пример  
 В разделе [закрытый](../../../parallel/openmp/reference/private-openmp.md) пример использования `shared`.  
  
## <a name="see-also"></a>См. также  
 [Предложения](../../../parallel/openmp/reference/openmp-clauses.md)