---
title: "Ошибка компилятора C2809 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2809
dev_langs: C++
helpviewer_keywords: C2809
ms.assetid: ce796b8e-1a8c-4074-995d-1ad09afd0e93
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1cf631f54e9cf4da6dd3edda423cddb8148e912b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2809"></a>Ошибка компилятора C2809
«оператор» не имеет формальных параметров  
  
 Оператор отсутствуют необходимые параметры.  
  
 Следующий пример приводит к возникновению ошибки C2809:  
  
```  
// C2809.cpp  
// compile with: /c  
class A{};  
int operator+ ();   // C2809  
int operator+ (A);   // OK  
```