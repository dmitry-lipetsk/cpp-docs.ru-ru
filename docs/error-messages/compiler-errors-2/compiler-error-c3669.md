---
title: "Ошибка компилятора C3669 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3669
dev_langs: C++
helpviewer_keywords: C3669
ms.assetid: be9c7ae4-e96f-47ab-922a-39a3537d5ca6
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0dc4197da5cafc986b9293c3428c80f6f43fc25f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3669"></a>Ошибка компилятора C3669
«член»: спецификатор переопределения «override» не допускаются статические функции-члены или конструкторы  
  
 Переопределение указан неправильно. Дополнительные сведения см. в разделе [явное переопределение](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению ошибки C3669.  
  
```  
// C3669.cpp  
// compile with: /clr  
public ref struct R {  
   R() override {}   // C3669  
};  
```