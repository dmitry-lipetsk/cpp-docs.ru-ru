---
title: "Ошибка компилятора C3454 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3454
dev_langs: C++
helpviewer_keywords: C3454
ms.assetid: dc4e6d57-5b4d-4114-8d6f-22f9ae62925b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 42a685d7084f5edd2a3f6b2fe6f1ab9d83e9c18f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3454"></a>Ошибка компилятора C3454
в объявлении класса [attribute] не допускается  
  
 Чтобы класс был атрибутом, его необходимо определить.  
  
 Для получения дополнительной информации см. [attribute](../../windows/attribute.md).  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению ошибки C3454:  
  
```  
// C3454.cpp  
// compile with: /clr /c  
using namespace System;  
  
[attribute]   // C3454  
ref class Attr1;  
  
[attribute]   // OK  
ref class Attr2 {};  
```