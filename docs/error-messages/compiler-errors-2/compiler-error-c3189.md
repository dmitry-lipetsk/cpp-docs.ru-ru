---
title: "Ошибка компилятора C3189 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3189
dev_langs: C++
helpviewer_keywords: C3189
ms.assetid: b254de79-931e-4a59-a9f4-1c690d90ca5e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 82bbe23b2dbbda71029e22ef8465a91a1889568b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3189"></a>Ошибка компилятора C3189
' typeid\<введите абстрактный декларатор > ": этот синтаксис больше не поддерживается, используйте:: typeid вместо  
  
 Устаревшая форма [typeid](../../windows/typeid-cpp-component-extensions.md) было использовать, используйте новую форму.  
  
 Следующий пример приводит к возникновению ошибки C3189:  
  
```  
// C3189.cpp  
// compile with: /clr  
int main() {  
   System::Type^ t  = typeid<System::Object>;   // C3189  
   System::Type^ t2  = System::Object::typeid;   // OK  
}  
```