---
title: "Предупреждение (уровень 1) C4405 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4405
dev_langs: C++
helpviewer_keywords: C4405
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b20bde360df28158ad504739a1de10d90e3ef0cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4405"></a>Предупреждение компилятора (уровень 1) C4405
«Идентификатор»: идентификатор является зарезервированным словом  
  
 Зарезервированное слово для встроенной сборки используется как имя переменной. Это может привести к непредсказуемым результатам. Чтобы устранить это предупреждение, избегайте присваивать имена переменным слова, зарезервированные для встроенной сборки. Следующий пример приводит к возникновению ошибки C4405:  
  
```  
// C4405.cpp  
// compile with: /W1  
// processor: x86  
void func1() {  
   int mov = 0, i = 0;  
   _asm {  
      mov mov, 0;   // C4405  
      // instead, try ..  
      // mov i, 0;  
   }  
}  
  
int main() {  
}  
```