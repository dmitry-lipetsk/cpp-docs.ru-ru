---
title: "Предупреждение (уровень 1) C4618 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4618
dev_langs: C++
helpviewer_keywords: C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9482fef776cfb7a1c30ecaecada45f0fdf5856b0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4618"></a>Предупреждение компилятора (уровень 1) C4618
параметры директивы pragma включают пустую строку; Директива pragma проигнорирована  
  
 Пустая строка в качестве аргумента представлена **#pragma**.  
  
 Директива pragma обработана без аргумента.  
  
 Следующий пример приводит к возникновению ошибки C4618:  
  
```  
// C4618.cpp  
// compile with: /W1 /LD  
#pragma code_seg("")   // C4618  
```