---
title: "Ошибка компилятора C2824 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2824
dev_langs: C++
helpviewer_keywords: C2824
ms.assetid: 5bd865f7-e0af-404e-80fe-e2b798b44a59
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eeea8950fd524eae4fbb06dc3254ba9010c4c1d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2824"></a>Ошибка компилятора C2824
Тип возвращаемого значения для «operator new» должен быть "void *"  
  
 Не на основе указателей, при перегрузке оператора `new` должен возвращать `void *`.  
  
 Следующий пример приводит к возникновению ошибки C2824:  
  
```  
// C2824.cpp  
// compile with: /c  
class   A {  
   A* operator new(size_t i, char *m);   // C2824  
   // try the following line instead  
   // void* operator new(size_t i, char *m);  
};  
```