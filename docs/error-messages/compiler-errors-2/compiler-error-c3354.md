---
title: "C3354 Ошибка компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3354
dev_langs:
- C++
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: bebeb383e77e4da16a24867731535d9fa36d6c5e
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3354"></a>Ошибка компилятора C3354
"функция": функция, используемая для создания делегата, не может иметь тип возврата "тип"  
  
 Следующие типы недопустимы в качестве возвращаемых типов для `delegate`:  
  
-   Указатель на функцию  
  
-   Указатель на член  
  
-   Указатель на функцию-член  
  
-   Ссылка на функцию  
  
-   Ссылка на функцию-член  
  
 В следующем примере возникает ошибка C3354:  
  
```  
// C3354_2.cpp  
// compile with: /clr /c  
using namespace System;  
typedef void ( *VoidPfn )();  
  
delegate VoidPfn func(); // C3354  
// try the following line instead  
// delegate  void func();  
```  
