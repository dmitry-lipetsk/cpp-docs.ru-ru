---
title: "Предупреждение (уровень 2) C4156 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4156
dev_langs: C++
helpviewer_keywords: C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ce2e30be92e555584fef0977674b03a550500e6d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-2-c4156"></a>Предупреждение (уровень 2) C4156 компилятора
Удаление выражения массива без использования формы «DELETE»; подставлена форма  
  
 Не являющиеся массивами форме **удалить** не может удалить массив. Компилятор преобразует **удалить** форму для массивов.  
  
 Это предупреждение возникает только при использовании расширений Майкрософт (/Ze).  
  
## <a name="example"></a>Пример  
  
```  
// C4156.cpp  
// compile with: /W2  
int main()  
{  
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];  
   delete array; // C4156, changed by compiler to "delete [] array;"  
}  
```