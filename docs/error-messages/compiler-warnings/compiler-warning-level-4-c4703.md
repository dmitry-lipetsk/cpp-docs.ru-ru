---
title: "Предупреждение компилятора (уровень 4) C4703 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4703
dev_langs: C++
helpviewer_keywords: C4703
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f8c2bacdb938cacc451011cffed2b41a1092dabe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4703"></a>Предупреждение компилятора (уровень 4) C4703
Потенциально неинициализированная локальная переменная-указатель используется «имя»  
  
 Локальная переменная-указатель *имя* использован без назначения им значение. Это может привести к непредсказуемым результатам.  
  
## <a name="example"></a>Пример  
 Следующий код приводит к возникновению ошибки C4701 и C4703.  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr) // C4701 and C4703  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
```Output  
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used  
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used  
  
```  
  
 Чтобы устранить это предупреждение, инициализируйте переменную, как показано в следующем примере:  
  
```cpp  
#include <malloc.h>  
  
void func(int size)  
{  
    void* p = nullptr;  
    if (size < 256) {  
        p = malloc(size);  
    }  
  
    if (p != nullptr)  
        free(p);  
}  
  
void main()  
{  
    func(9);  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Предупреждение компилятора (уровень 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)   
 [Предупреждения, / SDL и улучшение обнаружения неинициализированных переменных](http://blogs.msdn.com/b/sdl/archive/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection.aspx)