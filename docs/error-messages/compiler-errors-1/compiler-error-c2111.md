---
title: "Ошибка компилятора C2111 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2111
dev_langs: C++
helpviewer_keywords: C2111
ms.assetid: 38fd42ec-1480-4a44-aaca-ae4593ed5f50
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c8054ddee86aa0bbd8f7200f2bea2e768e5f2daf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2111"></a>Ошибка компилятора C2111
"+": для сложения указателей требуется целый операнд  
  
 Предпринята попытка прибавить нецелочисленное значение к указателю с помощью оператора сложения ( `+` ).  
  
 Следующий пример приводит к возникновению ошибки C2111:  
  
```  
// C2111.cpp  
int main() {  
   int *a = 0, *pa = 0, b = 0;  
   double d = 0.00;  
  
   a = pa + d;   // C2111  
   a = pa + b;   // OK  
}  
```