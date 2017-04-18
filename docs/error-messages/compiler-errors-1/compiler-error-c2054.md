---
title: "Ошибка компилятора C2054 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2054"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2054"
ms.assetid: 37f7c612-0d7d-4728-9e67-ac4160555f48
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Ошибка компилятора C2054
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

за "идентификатором" должна следовать скобка "\("  
  
 Идентификатор функции используется в контексте, в котором за ним должны следовать скобки.  
  
 Эта ошибка может возникать, если в сложном выражении инициализации не указан знак равенства \("\="\).  
  
 Следующий пример приводит к возникновению ошибки C2054:  
  
```  
// C2054.c  
int array1[] { 1, 2, 3 };   // C2054, missing =  
```  
  
 Возможный способ устранения данной ошибки:  
  
```  
// C2054b.c  
int main() {  
   int array2[] = { 1, 2, 3 };  
}  
```