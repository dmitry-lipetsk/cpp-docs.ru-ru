---
title: "Ошибка компилятора C2720 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2720
dev_langs: C++
helpviewer_keywords: C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cfd1e41ea3b9479f07faa9a1cbf0739bc0b7e8b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2720"></a>Ошибка компилятора C2720  
  
> "*идентификатор*": "*описатель*" спецификатор класса хранения недопустим для членов  
  
Класс хранения нельзя использовать для членов класса вне объявления. Чтобы устранить эту ошибку, удалите ненужный [класс хранения](../../cpp/storage-classes-cpp.md) описатель из определения члена вне объявления класса.  
  
## <a name="example"></a>Пример  
  
В следующем примере показано возникновение ошибки C2720 и приводятся сведения по ее устранению.  
  
```cpp  
// C2720.cpp  
struct S {  
   static int i;  
};  
static S::i;   // C2720 - remove the unneeded 'static' to fix it  
```