---
title: "Ошибка компилятора C2382 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2382
dev_langs: C++
helpviewer_keywords: C2382
ms.assetid: 4d4436f9-d0d6-4bd0-b8ec-767b89adfb2f
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e09d159f2d5afbb8946366ebdf4fe7c5ac2077b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2382"></a>Ошибка компилятора C2382
"функция": переопределение; разные спецификации исключений  
  
 При использовании параметра [/Za](../../build/reference/za-ze-disable-language-extensions.md)эта ошибка означает, что предпринята попытка перегрузки функции только в [спецификации исключений](../../cpp/exception-specifications-throw-cpp.md).  
  
 Следующий пример приводит к возникновению ошибки C2382:  
  
```  
// C2382.cpp  
// compile with: /Za /c  
void f1(void) throw(int) {}  
void f1(void) throw(char) {}   // C2382  
void f2(void) throw(char) {}   // OK  
```