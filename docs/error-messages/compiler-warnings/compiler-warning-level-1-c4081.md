---
title: "Предупреждение (уровень 1) C4081 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4081
dev_langs: C++
helpviewer_keywords: C4081
ms.assetid: 6f656373-a080-4989-bbc9-e2f894b03293
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ecf0ffa422abe06f7239ea0c397318582d7f9a71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4081"></a>Предупреждение компилятора (уровень 1) C4081
требуется "токен1"; обнаружено "токен2"  
  
 Компилятору в данном контексте требуется другой токен.  
  
## <a name="example"></a>Пример  
  
```  
// C4081.cpp  
// compile with: /W1 /LD  
#pragma optimize) "l", on )   // C4081  
```