---
title: "Ошибка компилятора C3490 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3490
dev_langs: C++
helpviewer_keywords: C3490
ms.assetid: 7638559a-fd06-4527-a9c1-0c8ae68b3123
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6439b48dc752d2bed01371cae59b2d77db16f1f9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3490"></a>Ошибка компилятора C3490
"переменная" не может быть изменен, поскольку доступ к нему осуществляется через константный объект  
  
 Лямбда-выражение, объявленное в методе `const` , не может изменять данные недоступного для изменения члена.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Удалите модификатор `const` из объявления метода.  
  
## <a name="example"></a>Пример  
 Приведенный ниже пример вызывает ошибку C3490, так как переменная-член `_i` изменяется в методе `const` .  
  
```  
// C3490a.cpp  
// compile with: /c  
  
class C  
{  
   void f() const   
   {  
      auto x = [=]() { _i = 20; }; // C3490  
   }  
  
   int _i;  
};  
```  
  
## <a name="example"></a>Пример  
 В приведенном ниже примере ошибка C3490 устраняется путем удаления модификатора `const` из объявления метода.  
  
```  
// C3490b.cpp  
// compile with: /c  
  
class C  
{  
   void f()  
   {  
      auto x = [=]() { _i = 20; };  
   }  
  
   int _i;  
};  
```  
  
## <a name="see-also"></a>См. также  
 [Лямбда-выражения](../../cpp/lambda-expressions-in-cpp.md)