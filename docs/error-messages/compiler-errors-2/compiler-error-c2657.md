---
title: "Ошибка компилятора C2657 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2657
dev_langs: C++
helpviewer_keywords: C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 709adacf558341dc31a48defd0ca7da5e08879ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2657"></a>Ошибка компилятора C2657
"класс:: *" в начале оператора (забыли указать тип?)  
  
 Строка начинается с идентификатора указателя на член.  
  
 Эта ошибка может быть вызвана отсутствует спецификатор типа в объявлении указателя на член.  
  
 Следующий пример приводит к возникновению ошибки C2657:  
  
```  
// C2657.cpp  
class C {};  
int main() {  
   C::* pmc1;        // C2657  
   int C::* pmc2;   // OK  
}  
```