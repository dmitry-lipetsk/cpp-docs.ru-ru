---
title: "Ошибка компилятора C3277 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3277
dev_langs: C++
helpviewer_keywords: C3277
ms.assetid: 8ac5f476-e30c-4879-92c6-f03cdbd74045
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 68ff09360a5ea247aae4ca9ad47242b80c194451
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3277"></a>Ошибка компилятора C3277
не удается определить неуправляемый enum «перечисление» в пределах управляемого «тип»  
  
 Недопустимое определение перечисления в управляемом типе.  
  
 Следующий пример приводит к возникновению ошибки C3277:  
  
```  
// C3277a.cpp  
// compile with: /clr  
ref class A  
{  
   enum E {e1,e2};   // C3277  
   // try the following line instead  
   // enum class E {e1,e2};  
};  
  
int main()  
{  
}  
```  
