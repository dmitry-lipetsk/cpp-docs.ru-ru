---
title: "Ошибка компилятора C2464 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2464
dev_langs: C++
helpviewer_keywords: C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3992f1ecc19beb5c4fa1208fe82a93deab546260
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2464"></a>Ошибка компилятора C2464
«Идентификатор»: нельзя использовать «new» для выделения памяти для ссылки  
  
 Идентификатор ссылки был выделен с помощью `new` оператор. Ссылки не являются объектами памяти, поэтому `new` не может вернуть указатель на них. Используйте стандартные объявление переменной синтаксис для объявления ссылки.  
  
 Следующий пример приводит к возникновению ошибки C2464:  
  
```  
// C2464.cpp  
int main() {  
   new ( int& ir );   // C2464  
}  
```