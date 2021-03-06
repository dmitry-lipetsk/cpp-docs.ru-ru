---
title: "Предупреждение компилятора C4485 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4485
dev_langs: C++
helpviewer_keywords: C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1289ee1ce2a5f756d7a21f966424007eee704ac1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4485"></a>Предупреждение компилятора C4485
«переопределяющая_функция»: соответствует методу базового класса «базового класса», но не помеченные «new» или «override»; предполагается «new» (и «virtual»)  
  
 Переопределяет метод доступа, независимо от `virtual` ключевое слово, функцию доступа базового класса, но `override` или `new` описатель не является частью подписи переопределяющей функции. Добавить `new` или `override` описатель, чтобы устранить это предупреждение.  
  
 В разделе [переопределить](../../windows/override-cpp-component-extensions.md) и [new (новый слот в vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md) для получения дополнительной информации.  
  
 C4485 всегда выдается как ошибка. Используйте [предупреждение](../../preprocessor/warning.md) pragma, чтобы отключить предупреждение C4485.  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению ошибки C4485  
  
```  
// C4485.cpp  
// compile with: /clr  
delegate void Del();  
  
ref struct A {  
   virtual event Del ^E;  
};  
  
ref struct B : A {  
   virtual event Del ^E;   // C4485  
};  
  
ref struct C : B {  
   virtual event Del ^E {  
      void raise() override {}  
      void add(Del ^) override {}  
      void remove(Del^) override {}  
   }  
};  
```