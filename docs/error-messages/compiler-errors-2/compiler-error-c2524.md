---
title: "Ошибка компилятора C2524 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2524
dev_langs: C++
helpviewer_keywords: C2524
ms.assetid: e71d17f5-2fc2-416b-8dbd-e9bed85eb33a
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d6f6a8375edc8db75895b103c6311365d571dc65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2524"></a>Ошибка компилятора C2524
«деструктор»: метод завершения или деструктор должен иметь список параметров «void»  
  
 Деструктор или метод завершения бы список параметров, не [void](../../cpp/void-cpp.md). Другие типы параметров не допускаются.  
  
## <a name="example"></a>Пример  
 Следующий код ошибка C2524:  
  
```  
// C2524.cpp  
// compile with: /c  
class A {  
   A() {}  
   ~A(int i) {}    // C2524  
   // try the following line instead  
   // ~A() {}  
};  
```  
  
## <a name="example"></a>Пример  
 Следующий код ошибка C2524:  
  
```  
// C2524_b.cpp  
// compile with: /clr /c  
ref struct I1 {  
protected:  
   !I1(int i);   // C2524  
   // try the following line instead  
   // !I1();  
};  
```