---
title: "Ошибка компилятора C3749 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3749
dev_langs: C++
helpviewer_keywords: C3749
ms.assetid: 3d26b468-4757-41b8-b5a2-78022a5295fb
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9f94c8bd51f959f84cd42979a8503ad05d5130a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3749"></a>Ошибка компилятора C3749
«атрибут»: настраиваемый атрибут не может использоваться внутри функции  
  
 Настраиваемый атрибут не может использоваться внутри функции. Дополнительные сведения о настраиваемых атрибутах см. в разделе [атрибут](../../windows/attribute.md).  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению ошибки C3749:  
  
```  
// C3749a.cpp  
// compile with: /clr /c  
using namespace System;  
  
[AttributeUsage(AttributeTargets::All)]  
public ref struct ABC : public Attribute {  
   ABC() {}  
};  
  
void f1() { [ABC]; };  // C3749  
```  
