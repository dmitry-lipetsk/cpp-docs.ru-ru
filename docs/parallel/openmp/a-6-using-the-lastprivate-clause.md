---
title: "С помощью lastprivate предложение A.6 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1744787e1dfb90fa9af93db5dba4eecd600b4334
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6   Использование предложения lastprivate
Иногда для правильного выполнения зависит от значения, последней итерации цикла присваивается переменной. Такие программы необходимо перечислить все переменные, такие как аргументы для `lastprivate` предложение ([раздел 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) на стр.), чтобы значения переменных совпадают при последовательного выполнения цикла.  
  
```  
#pragma omp parallel  
{  
   #pragma omp for lastprivate(i)  
      for (i=0; i<n-1; i++)  
         a[i] = b[i] + b[i+1];  
}  
a[i]=b[i];  
```  
  
 В предыдущем примере значение `i` в конце параллельной области будут равны `n-1`, как в случае последовательного.