---
title: "Ошибка компилятора C2277 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2277
dev_langs: C++
helpviewer_keywords: C2277
ms.assetid: 15a83b07-8731-4524-810b-267f65a7844f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c305da90c5065740b442a431f004347852bc0a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2277"></a>Ошибка компилятора C2277
«Идентификатор»: невозможно получить адрес этой функции-члена  
  
 Невозможно получить адрес функции-члена.  
  
 Следующий пример приводит к возникновению ошибки C2277:  
  
```  
// C2277.cpp  
class A {  
public:  
   A();  
};  
(*pctor)() = &A::A;   // C2277   
```