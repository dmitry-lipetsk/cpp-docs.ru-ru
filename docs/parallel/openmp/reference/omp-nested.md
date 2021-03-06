---
title: "OMP_NESTED | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_NESTED
dev_langs: C++
helpviewer_keywords: OMP_NESTED OpenMP environment variable
ms.assetid: c43f5287-a548-40d0-bd54-0c6b2b9f9a53
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d90d43727227593cccbd3d885f71f5cabaf10429
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="ompnested"></a>OMP_NESTED
Указывает, будет ли вложенный параллелизм, если не включена или отключена с вложенной параллелизма `omp_set_nested`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
set OMP_NESTED[=TRUE | =FALSE]  
```  
  
## <a name="remarks"></a>Примечания  
 `OMP_NESTED` Переменной среды может быть переопределено [omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md) функции.  
  
 Значение по умолчанию в Visual C++ реализации стандартной OpenMP — `OMP_DYNAMIC=FALSE`.  
  
 Дополнительные сведения см. в разделе [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).  
  
## <a name="example"></a>Пример  
 Следующая команда задает `OMP_NESTED` переменной среды в значение TRUE:  
  
```  
set OMP_NESTED=TRUE  
```  
  
 Следующая команда отображает текущее значение параметра `OMP_NESTED` переменной среды:  
  
```  
set OMP_NESTED  
```  
  
## <a name="see-also"></a>См. также  
 [Переменные среды](../../../parallel/openmp/reference/openmp-environment-variables.md)