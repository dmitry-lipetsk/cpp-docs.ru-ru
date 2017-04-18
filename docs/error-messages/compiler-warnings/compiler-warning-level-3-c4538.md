---
title: "Предупреждение (уровень 3) C4538 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4538
dev_langs:
- C++
helpviewer_keywords:
- C4538
ms.assetid: 747e3d51-b6d0-41c1-a726-7af3253b59d7
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 9436b01456fd35b8d19e46f513d82d8a58c75237
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-3-c4538"></a>Предупреждение компилятора (уровень 3) C4538
«Тип»: квалификаторы const и volatile для этого типа не поддерживаются.  
  
 Ключевое слово квалификатор был применен к массиву неправильно. Дополнительные сведения см. в разделе [массива](../../windows/arrays-cpp-component-extensions.md).  
  
 Следующий пример приводит к возникновению ошибки C4538:  
  
```  
// C4538.cpp  
// compile with: /clr /W3 /LD  
const array<int> ^f1();   // C4538  
array<const int> ^f2();   // OK  
```