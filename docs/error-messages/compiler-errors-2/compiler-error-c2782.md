---
title: "Ошибка компилятора C2782 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2782"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2782"
ms.assetid: 8b685422-294d-4f64-9f3d-c14eaf03a93d
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Ошибка компилятора C2782
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

"объявление": неоднозначный параметр шаблона "идентификатор"  
  
 Не удается определить тип аргумента шаблона во время компиляции.  
  
 Следующий пример приводит к возникновению ошибки C2782:  
  
```  
// C2782.cpp  
template<typename T>  
void f(T, T) {}  
  
int main() {  
   f(1, 'c');   // C2782  
   // try the following line instead  
   // f<int>(1, 'c');  
}  
```  
  
 Ошибка C2782 также может возникнуть при использовании универсальных шаблонов:  
  
```  
// C2782b.cpp  
// compile with: /clr  
generic<typename T> void gf(T, T) { }  
  
int main() {  
   gf(1, 'c'); // C2782  
   // try the following line instead  
   // gf<int>(1, 'c');  
}  
```