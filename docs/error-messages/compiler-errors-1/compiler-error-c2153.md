---
title: "Ошибка компилятора C2153 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2153
dev_langs: C++
helpviewer_keywords: C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c766d2ef62f22bcdc61c23790d70fa3f09b490c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2153"></a>Ошибка компилятора C2153
шестнадцатеричные константы должны содержать по крайней мере одну шестнадцатеричную цифру  
  
 Шестнадцатеричные константы 0 x 0 X и \x являются недопустимыми. Необходимо выполнить по крайней мере одну шестнадцатеричную цифру x или X.  
  
 Следующий пример приводит к возникновению ошибки C2153:  
  
```  
// C2153.cpp  
int main() {  
   int a= 0x;    // C2153  
   int b= 0xA;   // OK  
}  
```