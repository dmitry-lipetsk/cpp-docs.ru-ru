---
title: "Ошибка компилятора C2362 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2362"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2362"
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Ошибка компилятора C2362
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

пропуск инициализации "идентификатор" из\-за перехода "goto "метка""  
  
 В процессе компиляции с использованием параметра [\/Za](../../build/reference/za-ze-disable-language-extensions.md) из\-за перехода к метке не выполнена инициализация идентификатора.  
  
 Переход после объявления с инициализатором допускается только в том случае, если объявление содержится в блоке, который не выполняется, или уже инициализирована переменная.  
  
 Следующий пример приводит к возникновению ошибки C2326:  
  
```  
// C2362.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   int i = 1;      // C2362, initialization skipped  
label1:;  
}  
```  
  
 Возможный способ устранения данной ошибки:  
  
```  
// C2362b.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   {  
      int j = 1;   // OK, this block is never entered  
   }  
label1:;  
}  
```