---
title: "Ошибка компилятора C3101 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3101
dev_langs: C++
helpviewer_keywords: C3101
ms.assetid: 4f673766-d4f7-4632-94a5-d36a83f7f4b5
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a9e811eb32b5614d9e0aebf049d8eb39d1d07dcf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3101"></a>Ошибка компилятора C3101
Недопустимое выражение для аргумента атрибута с именем «поля»  
  
 При инициализации аргументом именованного атрибута, значение должно быть константой времени компиляции.  
  
 Дополнительные сведения об атрибутах см. в разделе [определяемые пользователем атрибуты](../../windows/user-defined-attributes-cpp-component-extensions.md).  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению ошибки C3101.  
  
```  
// C3101.cpp  
// compile with: /clr /c  
ref class AAttribute : System::Attribute {  
public:  
   int Field;  
};  
  
extern int i;  
  
[assembly:A(Field = i)];   // C3101  
[assembly:A(Field = 0)];   // OK  
```