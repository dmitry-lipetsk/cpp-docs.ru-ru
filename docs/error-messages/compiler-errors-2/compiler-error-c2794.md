---
title: "Ошибка компилятора C2794 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2794
dev_langs: C++
helpviewer_keywords: C2794
ms.assetid: d508191c-9044-4c6a-9119-4bca668c0b93
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0cbbc6bdaea9c78b9dba54363ccf6953d8050b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2794"></a>Ошибка компилятора C2794
«функция»: не является членом любой прямой или косвенный базовый класс «класс»  
  
 Предпринята попытка использования [super](../../cpp/super.md) для вызова несуществующей функции-члена.  
  
 Следующий пример приводит к возникновению ошибки C2794  
  
```  
// C2794.cpp  
struct B {  
   void mf();  
};  
  
struct D : B {  
   void mf() {  
      __super::f();  // C2794  
   }  
};  
```