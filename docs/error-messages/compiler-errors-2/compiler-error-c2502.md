---
title: "Ошибка компилятора C2502 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2502
dev_langs: C++
helpviewer_keywords: C2502
ms.assetid: affa0b86-15fc-4e17-b7f2-6aad4a3771c4
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 954e4df57a3bf4c56f639531f96448d727f8219b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2502"></a>Ошибка компилятора C2502
«Идентификатор»: слишком много модификаторов доступа для базового класса  
  
 Базовый класс имеет несколько модификаторов доступа. Только один модификатор доступа (`public`, `private`, или `protected`) разрешено.  
  
 Следующий пример приводит к возникновению ошибки C2502:  
  
```  
// C2502.cpp  
// compile with: /c  
class A { };  
class B { };  
class C : private public A { };   // C2502  
  
// OK  
class D : private A {};  
class E : public A, private B {};  
```