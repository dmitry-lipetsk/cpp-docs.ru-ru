---
title: "Предупреждение (уровень 1) C4033 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4033
dev_langs: C++
helpviewer_keywords: C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aec85fa985b3d8183d7614bdd6b3527b5d671b2b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4033"></a>Предупреждение компилятора (уровень 1) C4033
Функция "функция" должна возвращать значение  
  
 Функция не возвращает значение. Возвращается неопределенное значение.  
  
 Функции, использующие `return` без возвращаемого значения, должны объявляться с типом `void`.  
  
 Эта ошибка для кода на языке C.  
  
 Следующий пример приводит к возникновению ошибки C4033:  
  
```  
// C4033.c  
// compile with: /W1 /LD  
int test_1(int x)   // C4033 expected  
{  
   if (x)  
   {  
      return;   // C4033  
   }  
}  
```