---
title: "Ошибка компилятора C3420 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3420
dev_langs: C++
helpviewer_keywords: C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: da0c47ccb08d1d4e9aa4c75fbce4d4fe8252a340
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3420"></a>Ошибка компилятора C3420
"метод_завершения": метод завершения не может быть виртуальным  
  
 Метод завершения можно вызвать только не виртуально из его включающего типа. Следовательно, это ошибка для объявления виртуального метода завершения.  
  
 Дополнительные сведения см. в разделе [деструкторы и методы завершения в разделе: определение и использование классов и структур (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
## <a name="example"></a>Пример  
 При компиляции следующего примера возникнет ошибка C3420.  
  
```  
// C3420.cpp  
// compile with: /clr /c  
ref class R {  
   virtual !R() {}   // C3420  
};  
```