---
title: "Предупреждение (уровень 1) C4616 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4616
dev_langs: C++
helpviewer_keywords: C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b8c8817cd7ded31f7664f32130159fbe324ef929
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4616"></a>Предупреждение компилятора (уровень 1) C4616
\#в директиве pragma warning: номер предупреждения «число» не является действительным предупреждением компилятора  
  
 Число предупреждений, указанное в [предупреждение](../../preprocessor/warning.md) pragma может быть переназначен. Директива pragma была пропущена.  
  
 Следующий пример приводит к возникновению ошибки C4616:  
  
```  
// C4616.cpp  
// compile with: /W1 /c  
#pragma warning( disable : 0 )   // C4616  
#pragma warning( disable : 999 )   // OK  
#pragma warning( disable : 4998 )   // OK  
```