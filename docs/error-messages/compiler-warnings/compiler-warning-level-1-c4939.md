---
title: "Предупреждение (уровень 1) C4939 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4939
dev_langs: C++
helpviewer_keywords: C4939
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2714963f2b6538805e2352ccb96a19f01f843e73
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4939"></a>Предупреждение компилятора (уровень 1) C4939
\#Директива #pragma vtordisp является устаревшим и будет удален в будущих версиях Visual C++  
  
 Директива pragma [vtordisp](../../preprocessor/vtordisp.md) будет удалена в будущих выпусках Visual C++.  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению предупреждения C4939:  
  
```  
// C4939.cpp  
// compile with: /c /W1  
#pragma vtordisp(off)   // C4939  
```