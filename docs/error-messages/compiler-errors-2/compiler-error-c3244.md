---
title: "Ошибка компилятора C3244 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3244
dev_langs: C++
helpviewer_keywords: C3244
ms.assetid: dae6c49b-5212-4206-8f61-d4010c0b9969
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a67deb7e4b0b123a95a027c9e74e8310452c41be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3244"></a>Ошибка компилятора C3244
"метод": этот метод был создан "интерфейс", но не "интерфейс"  
  
 Вы попытались [явно переопределить](../../cpp/explicit-overrides-cpp.md) элемент, который не существует в указанном интерфейсе, но существует в другом базовом классе.  
  
 Следующий пример приводит к возникновению ошибки C3244:  
  
```  
// C3244.cpp  
#pragma warning(disable:4199)  
  
__interface IX15A {  
   void f();  
};  
  
__interface IX15B {  
   void g();  
};  
  
class CX15 : public IX15A, public IX15B {  
public:        
   void IX15A::f();  
   void IX15B::g();  
};  
  
void CX15::IX15A::g()   // C3244 occurs here  
{  
}  
```