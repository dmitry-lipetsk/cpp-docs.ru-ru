---
title: "Ошибка компилятора C2333 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2333
dev_langs: C++
helpviewer_keywords: C2333
ms.assetid: 2636fc1e-d3e7-4e68-8628-3c81a99ba813
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9788ae2aa17de0b965d1935652df6017810d9c67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2333"></a>Ошибка компилятора C2333
«функция»: ошибка в объявлении функции; тело функции пропускается  
  
 Эта ошибка возникает после другой ошибки в функциях-членах определяемых внутри своего класса.  
  
 Следующий пример приводит к возникновению ошибки C2333:  
  
```  
// C2333.cpp  
struct s1 {  
   s1(s1) {}   // C2333  
};  
```