---
title: "Компилятор C4817 предупреждение (уровень 1) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4817
dev_langs:
- C++
helpviewer_keywords:
- C4817
ms.assetid: a68f5486-6940-4934-9f93-bfd4d71f92a9
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: 5a141a631821c7b681bc26857c6b213aeb0f9831
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4817"></a>Предупреждение компилятора (уровень 1) C4817
"член": недопустимое использование "." для обращения к этому члену; заменено на "->" компилятором  
  
 Использован неверный оператор доступа к члену.  
  
## <a name="example"></a>Пример  
 Приведенный ниже пример приводит к возникновению предупреждения C4817.  
  
```  
// C4817.cpp  
// compile with: /clr /W1  
using namespace System;  
int main() {  
   array<Int32> ^ a = gcnew array<Int32>(100);  
   Console::WriteLine( a.Length );   // C4817  
   Console::WriteLine( a->Length );   // OK  
}  
```  
