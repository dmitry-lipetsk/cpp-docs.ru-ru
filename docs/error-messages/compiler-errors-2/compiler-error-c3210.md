---
title: "Ошибка компилятора C3210 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3210
dev_langs: C++
helpviewer_keywords: C3210
ms.assetid: c6e9d309-fabc-4e7d-b526-be20d9fe3f6a
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b710aa15591a0e8a0a5613d5023ea7ba48d13d70
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3210"></a>Ошибка компилятора C3210
«Тип»: объявление уровня доступа может применяться только к члену базового класса  
  
 Объект [объявление using](../../cpp/using-declaration.md) указан неправильно.  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению ошибки C3210.  
  
```  
// C3210.cpp  
// compile with: /c  
struct A {  
protected:  
   int i;  
};  
  
struct B {  
   using A::i;   // C3210  
};  
  
struct C : public A {  
   using A::i;   // OK  
};  
```