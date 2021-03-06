---
title: "OMP_NUM_THREADS | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_NUM_THREADS
dev_langs: C++
helpviewer_keywords: OMP_NUM_THREADS OpenMP environment variable
ms.assetid: 4b558124-1387-4c30-a6a5-ff5345a9ced6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a5f6af2ff547ddb95b6d4ef6b9c6d353399c17c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="ompnumthreads"></a>OMP_NUM_THREADS
Задает максимальное число потоков в параллельной области, если иное не переопределено [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) или [num_threads](../../../parallel/openmp/reference/num-threads.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
set OMP_NUM_THREADS[=num]  
```  
  
## <a name="remarks"></a>Примечания  
 где  
  
 `num`  
 Максимальное число потоков в параллельной области, не более 64 реализации в Visual C++.  
  
## <a name="remarks"></a>Примечания  
 **OMP_NUM_THREADS** переменной среды может быть переопределено [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) функции или [num_threads](../../../parallel/openmp/reference/num-threads.md).  
  
 Значение по умолчанию `num` в Visual C++ реализацию стандарта OpenMP — количество виртуальных процессоров, включая ЦП Hyper-Threading.  
  
 Дополнительные сведения см. в разделе [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).  
  
## <a name="example"></a>Пример  
 Следующая команда задает **OMP_NUM_THREADS** переменной среды до 16:  
  
```  
set OMP_NUM_THREADS=16  
```  
  
 Следующая команда отображает текущее значение параметра **OMP_NUM_THREADS** переменной среды:  
  
```  
set OMP_NUM_THREADS  
```  
  
## <a name="see-also"></a>См. также  
 [Переменные среды](../../../parallel/openmp/reference/openmp-environment-variables.md)