---
title: "Ошибка компилятора C2805 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2805
dev_langs: C++
helpviewer_keywords: C2805
ms.assetid: c997dc56-e199-442f-b94e-ac551ec9b015
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ec67cd98f92b731338d729530d53918d7c761993
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2805"></a>Ошибка компилятора C2805
двоичный оператор «оператор» содержит слишком мало параметров  
  
 Бинарный оператор не имеет параметров.  
  
 Следующий пример приводит к возникновению ошибки C2805:  
  
```  
// C2805.cpp  
// compile with: /c  
class X {  
public:  
   X operator< ( void );   // C2805 must take one parameter  
   X operator< ( X );   // OK  
};  
```