---
title: "Предупреждение (уровень 3) C4414 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4414
dev_langs: C++
helpviewer_keywords: C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 76745a1cf505a685bcb9a6d2e74faf98bad77556
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4414"></a>Предупреждение компилятора (уровень 3) C4414
«функция»: короткий переход к функции преобразован в Ближний переход  
  
 Сокращенный переход генерирует компактную инструкцию, которая разветвляется на адреса в ограниченном диапазоне из инструкции. Инструкция включает короткое смещение, которое представляет расстояние между переходом и конечным адресом, определение функции. Во время компоновки функция может быть перемещена или подвергнута оптимизации во время компоновки, вызывающие функции за пределы диапазона, доступного из короткого смещения. Компилятор должен создать конкретную запись для перехода, который требует инструкция безусловный БЛИЖАЙШЕМ или РАССТОЯНИЕ. Компилятор сделал преобразование.  
  
 Например следующий код приводит к возникновению ошибки C4414:  
  
```  
// C4414.cpp  
// compile with: /W3 /c  
// processor: x86  
int DoParityEven();  
int DoParityOdd();  
unsigned char global;  
int __declspec(naked) DoParityEither()  
{  
   __asm  
   {  
      test global,0  
      jpe SHORT DoParityEven  // C4414  
      jmp SHORT DoParityOdd   // C4414  
   }  
}  
```