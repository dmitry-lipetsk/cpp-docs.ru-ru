---
title: "omp_unset_lock | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_unset_lock
dev_langs: C++
helpviewer_keywords: omp_unset_lock OpenMP function
ms.assetid: 68fcb728-040b-4bad-979e-aaecb9097a4e
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5dae4888176807ba2d3a3356d71c55eb82f2a55c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="ompunsetlock"></a>omp_unset_lock
Освобождает блокировку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void omp_unset_lock(  
   omp_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>Примечания  
 где  
  
 `lock`  
 Переменная типа [omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) , инициализированный с [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md), принадлежащие потоком и выполняется в функции.  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения см. в разделе [3.2.4 функции omp_unset_lock и omp_unset_nest_lock](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).  
  
## <a name="example"></a>Пример  
 В разделе [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) пример использования `omp_unset_lock`.  
  
## <a name="see-also"></a>См. также  
 [Функции](../../../parallel/openmp/reference/openmp-functions.md)