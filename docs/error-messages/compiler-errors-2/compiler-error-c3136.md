---
title: "Ошибка компилятора C3136 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3136
dev_langs: C++
helpviewer_keywords: C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e2b4daa5076a04825cea6a96709f40716f3eaeff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3136"></a>Ошибка компилятора C3136
«интерфейс»: интерфейс COM может наследовать только от другого интерфейса COM, «интерфейс» не является COM-интерфейс  
  
 Интерфейс, к которому применен [атрибут интерфейса](../../windows/interface-attributes.md) наследует от интерфейса, который не является COM-интерфейса. COM-интерфейс наследует от `IUnknown`. Любой интерфейс предшествует атрибут интерфейса является COM-интерфейса.  
  
 Следующий пример приводит к возникновению ошибки C3136:  
  
```  
// C3136.cpp  
#include "unknwn.h"  
  
__interface A   // C3136  
// try the following line instead  
// _interface A : IUnknown  
{  
   int a();  
};  
  
[object]  
__interface B : A  
{  
   int aa();  
};  
```