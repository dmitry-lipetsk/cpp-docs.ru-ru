---
title: "Предупреждение (уровень 1) C4917 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4917
dev_langs: C++
helpviewer_keywords: C4917
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 37849850c89f8c02726b730fbdbabed66bd849b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4917"></a>Предупреждение компилятора (уровень 1) C4917
«декларатор»: идентификатор GUID может быть связан только с классом, интерфейсом или пространством имен  
  
Пользовательские структуры, отличных от [класса](../../cpp/class-cpp.md), [интерфейс](../../cpp/interface.md), или [имен](../../cpp/namespaces-cpp.md) не может иметь идентификатор GUID.  
  
Это предупреждение отключено по умолчанию. Подробнее: [Выключенные по умолчанию предупреждения компилятора](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .  
  
## <a name="example"></a>Пример  
В следующем образце кода приводит к возникновению ошибки C4917:  
  
```cpp  
// C4917.cpp  
// compile with: /W1  
#pragma warning(default : 4917)  
__declspec(uuid("00000000-0000-0000-0000-000000000001")) struct S  
{  
} s;   // C4917, don't put uuid on a struct  
  
int main()  
{  
}  
```