---
title: "Ошибка компилятора C2815 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2815
dev_langs:
- C++
helpviewer_keywords:
- C2815
ms.assetid: d0256fd6-0721-4c99-b03c-52d96e77a613
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: 129ad6a0359fbee402b39c5e7ff498602e97479d
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2815"></a>Ошибка компилятора C2815
«operator delete»: первый формальный параметр должен быть "void *", однако «параметр»  
  
 Любые пользовательские [оператор delete](../../standard-library/new-operators.md#operator_delete) функция должна принимать первый формальный параметр типа `void *`.  
  
 Следующий пример приводит к возникновению ошибки C2815:  
  
```  
// C2815.cpp  
// compile with: /c  
class CMyClass {  
public:  
   void mf1(int *a);  
   void operator delete(CMyClass *);   // C2815  
   void operator delete(void *);   
};  
```