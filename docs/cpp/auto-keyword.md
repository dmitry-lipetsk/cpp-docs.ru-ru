---
title: "Ключевое слово Auto | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: auto_cpp
dev_langs: C++
helpviewer_keywords:
- automatic storage class [C++], auto keyword
- auto keyword [C++]
ms.assetid: 744a41c0-2510-4140-a1be-96257e722908
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3508217e7dc333543fa2dbff9cf0643d6faff060
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="auto-keyword"></a>Ключевое слово auto
Ключевое слово `auto` является описателем объявления. Однако стандарт языка C++ определяет первоначальное и измененное значение данного ключевого слова. До Visual C++ 2010 `auto` ключевое слово объявляло переменную в *автоматического* класса хранения, то есть переменную с локальным временем существования. Начиная с Visual C++ 2010 `auto` ключевое слово объявляет переменную, тип которой выводится из выражения инициализации в его объявлении. [/Zc: auto &#91;-&#93;](../build/reference/zc-auto-deduce-variable-type.md) параметр компилятора контролирует значение `auto` ключевое слово.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
auto declarator ;  
auto declarator initializer;  
```  
  
## <a name="remarks"></a>Примечания  
 Определение ключевого слова `auto` меняется в языке программирования C++, но не в С.  
  
 В следующих разделах описывается ключевое слово `auto` и соответствующий параметр компилятора:  
  
-   [Auto](../cpp/auto-cpp.md) описывается новое определение `auto` ключевое слово.  
  
  
-   [/ Zc: auto (выведение типа переменной)](../build/reference/zc-auto-deduce-variable-type.md) описание параметра компилятора, который сообщает компилятору, определение которого `auto` ключевое слово для использования.  
  
## <a name="see-also"></a>См. также  
 [Ключевые слова](../cpp/keywords-cpp.md)