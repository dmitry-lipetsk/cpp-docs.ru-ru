---
title: "Ошибка компилятора C2561 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2561
dev_langs: C++
helpviewer_keywords: C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 604c5b4ce8c8e1b5477d076a061fdf56fdfd9c54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2561"></a>Ошибка компилятора C2561
«Идентификатор»: функция должна возвращать значение  
  
 Функция была объявлена как возвращающая значение, но не содержит определение функции `return` инструкции.  
  
 Эта ошибка может быть вызвана неверным прототипом функции:  
  
1.  Если функция не возвращает значение, объявите функцию с возвращаемым типом [void](../../cpp/void-cpp.md).  
  
2.  Убедитесь, что все возможные ветви выполнения функции возвращают значение в тип, объявленный в прототипе.  
  
3.  Функции C++, содержащие встроенные подпрограммы сборки, возвращаемое значение в `AX` регистра может потребоваться оператор return. Скопируйте значение в `AX` во временную переменную и верните ее из функции.  
  
 Следующий пример приводит к возникновению ошибки C2561:  
  
```  
// C2561.cpp  
int Test(int x) {  
   if (x) {  
      return;   // C2561  
      // try the following line instead  
      // return 1;  
   }  
   return 0;  
}  
  
int main() {  
   Test(1);  
}  
```