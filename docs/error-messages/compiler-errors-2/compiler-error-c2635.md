---
title: "Ошибка компилятора C2635 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2635
dev_langs: C++
helpviewer_keywords: C2635
ms.assetid: 9deca2a8-2d61-42eb-9783-6578132ee3fb
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 717e3979ac0f1309f24e6747946480b4e05ada42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2635"></a>Ошибка компилятора C2635
не удается преобразовать «идентификатор1 *» в "идентификатор2\*"; предполагается преобразование из виртуального базового класса  
  
 Для преобразования требуется приведение из `virtual` базового класса в производном классе не допускается.  
  
 Следующий пример приводит к возникновению ошибки C2635:  
  
```  
// C2635.cpp  
class B {};  
class D : virtual public B {};  
class E : public B {};  
  
int main() {  
   B b;  
   D d;  
   E e;  
  
   D * pD = &d;  
   E * pE = &e;  
   pD = (D*)&b;   // C2635  
   pE = (E*)&b;   // OK  
}  
```