---
title: "Ошибка компилятора C2486 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2486
dev_langs: C++
helpviewer_keywords: C2486
ms.assetid: 436da349-6461-4e32-bfca-4f3e620108e2
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ab37ca48b5537bdb2902f6947c238a4c605ffa5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2486"></a>Ошибка компилятора C2486
«__LOCAL_SIZE» допускается только в функции с атрибутом «naked»  
  
 Во встроенных функциях сборки, имя `__LOCAL_SIZE` зарезервировано для функций, объявленных с [naked](../../cpp/naked-cpp.md) атрибута.  
  
 Следующий пример приводит к возникновению ошибки C2486:  
  
```  
// C2486.cpp  
// processor: x86  
void __declspec(naked) f1() {  
   __asm {  
      mov   eax,   __LOCAL_SIZE  
   }  
}  
void f2() {  
   __asm {  
      mov   eax,   __LOCAL_SIZE   // C2486  
   }  
}  
```