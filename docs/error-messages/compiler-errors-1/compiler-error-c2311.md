---
title: "Ошибка компилятора C2311 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2311
dev_langs: C++
helpviewer_keywords: C2311
ms.assetid: 1aff9bd5-ed0b-4db6-bbc0-01ac89850cf2
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9e7f01947dcab7b8e3fb614ecfef40726e9847fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2311"></a>Ошибка компилятора C2311
«исключение»: перехвачено «...» в строке с номером  
  
 Обработчик "catch" для многоточия (...) должен быть последним обработчиком для исключения.  
  
 Следующий пример приводит к возникновению ошибки C2311:  
  
```  
// C2311.cpp  
// compile with: /EHsc  
#include <eh.h>  
int main() {  
   try {  
      throw "ooops!";  
   }  
   catch( ... ) {}  
   catch( int ) {}   // C2311  ellipsis handler not last catch  
}  
```