---
title: "Ошибка компилятора C2633 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2633
dev_langs: C++
helpviewer_keywords: C2633
ms.assetid: a7aceb65-4255-42d6-a8fb-e3cb6c4d2270
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d95a37fee29da2051809a8c1c5fc4dc816d0e923
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2633"></a>Ошибка компилятора C2633
«Идентификатор»: «inline» является единственным допустимым классом хранения для конструкторов  
  
 Конструктор объявлен как класс хранения, отличные от встроенной.  
  
 Следующий пример приводит к возникновению ошибки C2633:  
  
```  
// C2633.cpp  
// compile with: /c  
class C {  
   extern C();   // C2633, not inline  
   inline C();   // OK  
};  
```