---
title: "Ошибка компилятора C3059 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3059
dev_langs: C++
helpviewer_keywords: C3059
ms.assetid: 57220324-8286-4cab-a1ab-45385eb1eae0
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a596a1b570b7966a02ee6d102209918c260f4c3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3059"></a>Ошибка компилятора C3059
var: символ threadprivate нельзя использовать в предложении "предложение"  
  
 Символ [threadprivate](../../parallel/openmp/reference/threadprivate.md) использовался в предложении.  
  
 В следующем примере возникает ошибка C3059:  
  
```  
// C3059.cpp  
// compile with: /openmp  
#include "omp.h"  
int x, y;  
#pragma omp threadprivate(x, y)  
  
int main() {  
   #pragma omp parallel private(x, y)   // C3059  
   {  
      x = y;  
   }  
}  
```  
  
 Возможное решение  
  
```  
// C3059b.cpp  
// compile with: /openmp  
#include "omp.h"  
int x = 0, y = 0;  
  
int main() {  
   #pragma omp parallel firstprivate(y) private(x)  
   {  
      x = y;  
   }  
}  
```