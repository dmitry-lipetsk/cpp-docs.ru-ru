---
title: "Ошибка компилятора C2897 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2897
dev_langs: C++
helpviewer_keywords: C2897
ms.assetid: a88349e2-823f-42a0-8660-0653b677afa4
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64d99fb6854a9cf1c1acee88c0d8bddadc30557c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2897"></a>Ошибка компилятора C2897
деструктор или метод завершения не может быть шаблоном функции  
  
 Деструкторы и методы завершения не могут быть перегружены, поэтому объявление деструктора в качестве шаблона (приводящее к определению набора деструкторов) не допускается.  
  
 Следующий пример приводит к возникновению ошибки C2897:  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению ошибки C2897.  
  
```  
// C2897.cpp  
// compile with: /c  
class X {  
public:  
   template<typename T> ~X() {}   // C2897  
};  
```  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению ошибки C2897.  
  
```  
// C2897_b.cpp  
// compile with: /c /clr  
ref struct R2 {  
protected:  
   template<typename T> !R2(){}   // C2897 error  
};  
```