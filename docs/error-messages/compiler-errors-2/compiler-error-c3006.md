---
title: "Ошибка компилятора C3006 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3006
dev_langs:
- C++
helpviewer_keywords:
- C3006
ms.assetid: 449082ec-fd45-4c47-8ab3-ba6a719e4dc4
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: ec29d6e1f9ef84026c012f0e124fc1c92c225b65
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3006"></a>Ошибка компилятора C3006
"предложение": в предложении директивы OpenMP "директива" отсутствует необходимый аргумент  
  
 В директиве OpenMP отсутствует ожидаемый аргумент.  
  
 Следующий пример приводит к возникновению ошибки C3006:  
  
```  
// C3006.c  
// compile with: /openmp  
int main()  
{  
   #pragma omp parallel shared   // C3006  
   // Try the following line instead:  
   // #pragma omp parallel shared(x) {}  
  
}  
```