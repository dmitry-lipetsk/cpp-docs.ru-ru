---
title: "Предупреждение компилятора C4972 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4972
dev_langs: C++
helpviewer_keywords: C4972
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cafe6f8d69407a3877155ed715e3c5217b56b9bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4972"></a>Предупреждение компилятора C4972
Прямое изменение или обработка результатов операции распаковки в виде левостороннего значения недоступны для проверки  
  
 Разыменование дескриптора до типа значения, также называемое распаковкой, а затем присвоение ему значения не проверяется.  
  
 Дополнительные сведения см. в разделе [упаковка-преобразование](../../windows/boxing-cpp-component-extensions.md).  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению предупреждения C4972:  
  
```  
// C4972.cpp  
// compile with: /clr:safe  
using namespace System;  
ref struct R {  
   int ^ p;   // a value type  
};  
  
int main() {  
   R ^ r = gcnew R;  
   *(r->p) = 10;   // C4972  
  
   // OK  
   r->p = 10;  
   Console::WriteLine( r->p );  
   Console::WriteLine( *(r->p) );  
}  
```