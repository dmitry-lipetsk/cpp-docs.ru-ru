---
title: "Предупреждение (уровень 1) C4090 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4090
dev_langs: C++
helpviewer_keywords: C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 81506e59243cd8ec17087af6a06391ff097ab05d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4090"></a>Предупреждение (уровень 1) C4090 компилятора
«Операция»: квалификаторы разных «модификатор»  
  
 Переменная, которая используется в операции определен с указанным модификатор, который предотвращает изменение без обнаружения компилятором. Выражение компилируется без изменений.  
  
 Это предупреждение может возникать при создании указателя на **const** или `volatile` не объявлен как указатель на указатель назначается элемент **const** или `volatile`.  
  
 Это предупреждение выдается для программ. В программе на C++, компилятор выдает сообщение об ошибке: [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md).  
  
 Следующий пример приводит к возникновению ошибки C4090:  
  
```  
// C4090.c  
// compile with: /W1  
int *volatile *p;  
int *const *q;  
int **r;  
  
int main() {  
   p = q;   // C4090  
   p = r;  
   q = p;   // C4090  
   q = r;  
   r = p;   // C4090  
   r = q;   // C4090  
}  
```