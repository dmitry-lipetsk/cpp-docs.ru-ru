---
title: "Ошибка компилятора C3296 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3296
dev_langs: C++
helpviewer_keywords: C3296
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 73f6e8260532164e9ea6a4d3f7330ba51043aa82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3296"></a>Ошибка компилятора C3296
"свойство": свойство с таким именем уже существует  
  
 Компилятор обнаружил несколько свойств с одинаковым именем. Каждое свойство в типе должно иметь уникальное имя.  
  
 Дополнительные сведения см. в разделе [property](../../windows/property-cpp-component-extensions.md).  
  
## <a name="example"></a>Пример  
 В следующем примере возникает ошибка C3296:  
  
```  
// C3296.cpp  
// compile with: /clr /c  
using namespace System;  
  
ref class R {  
public:  
   property int MyProp[int] { int get(int); }  
  
   property String^ MyProp[int] { void set(int, String^); }   // C3296  
};  
```