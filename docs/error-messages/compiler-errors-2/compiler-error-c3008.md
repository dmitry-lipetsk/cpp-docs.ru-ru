---
title: "Ошибка компилятора C3008 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3008
dev_langs: C++
helpviewer_keywords: C3008
ms.assetid: 04d93201-28e5-4be0-945c-aad616376f4b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 75adf08e05a6b192c5bb785224eac770425a72a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3008"></a>Ошибка компилятора C3008
"аргумент": в аргументе директивы OpenMP "директива" отсутствует закрывающая скобка ")"  
  
 Директива OpenMP, которая принимает аргумент, не содержит закрывающую скобку.  
  
 При компиляции следующего примера возникнет ошибка C3008:  
  
```  
// C3008.c  
// compile with: /openmp  
int main()  
{  
   int x, y, z;  
   #pragma omp parallel shared(x   // C3008  
   // Try the following line instead:  
   #pragma omp parallel shared(x)  
   {  
   }  
}  
```