---
title: "Неустранимая ошибка ML A1007 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A1007
dev_langs:
- C++
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d1ef99cebab226a3af5e7e685acc5a5485872d1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="ml-fatal-error-a1007"></a>Неустранимая ошибка ML A1007
**слишком глубокий уровень вложенности**  
  
 Код на языке ассемблера достигнут предел вложенности. Ограничение составляет 20 уровни, за исключением случаев, оговоренных в противном случае.  
  
 Одно из следующих были вложены слишком глубоко:  
  
-   Директиву высокого уровня, такие как [. Если](../../assembler/masm/dot-if.md), [. ПОВТОРИТЕ](../../assembler/masm/dot-repeat.md), или [. Во время](../../assembler/masm/dot-while.md).  
  
-   Определение структуры.  
  
-   Директива условной сборки.  
  
-   Определение процедуры.  
  
-   Объект [PUSHCONTEXT](../../assembler/masm/pushcontext.md) директивы (ограничение составляет 10).  
  
-   Определение сегмента.  
  
-   Файл заголовка.  
  
-   Макрос.  
  
## <a name="see-also"></a>См. также  
 [Сообщения об ошибках ML](../../assembler/masm/ml-error-messages.md)