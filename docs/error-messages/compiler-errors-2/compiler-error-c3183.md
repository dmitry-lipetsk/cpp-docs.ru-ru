---
title: "Ошибка компилятора C3183 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3183
dev_langs: C++
helpviewer_keywords: C3183
ms.assetid: dbd0f020-c739-43c9-947e-9ce21537331b
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ac58735947f7586d3929b4ada6da3e1988b94c9d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3183"></a>Ошибка компилятора C3183
не удается определить класс, структуру или объединение без имени внутри управляемого типа или типа WinRT type  
  
Тип, который внедряется в управляемый тип или тип WinRT, должен быть именованным.  
  
Следующий пример приводит к возникновению ошибки C3183:  
  
```  
// C3183a.cpp  
// compile with: /clr /c  
ref class Test  
{  
   ref class  
   {  // C3183, delete class or name it  
      int a;  
      int b;  
   };  
};  
```  
