---
title: "Ошибка компилятора C2019 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2019
dev_langs: C++
helpviewer_keywords: C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bf5c86bb837b89bd96e8e490e3668018affd6ca7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2019"></a>Ошибка компилятора C2019
требуется директива препроцессора, найден "символ"  
  
 Символ следует за `#` входа, но он не является первой буквой директивы препроцессора.  
  
 Следующий пример приводит к возникновению ошибки C2019:  
  
```  
// C2019.cpp  
#!define TRUE 1   // C2019  
```  
  
 Возможное решение  
  
```  
// C2019b.cpp  
// compile with: /c  
#define TRUE 1  
```