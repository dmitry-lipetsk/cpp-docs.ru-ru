---
title: ". ЕСЛИ | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .IF
dev_langs:
- C++
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1ad05314b9ee0612622f0b57508d30016eeeff5d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="if"></a>.IF
Создает код, который проверяет `condition1` (например, AX > 7) и выполняет *инструкций* Если это условие истинно.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
   .IF condition1   
statements  
[[.ELSEIF condition2   
   statements]]  
[[.ELSE  
   statements]]  
.ENDIF  
```  
  
## <a name="remarks"></a>Примечания  
 Если [. ELSE](../../assembler/masm/dot-else.md) следующим свои операторы выполняются в том случае, если исходное состояние имел значение false. Обратите внимание, что условия проверяются во время выполнения.  
  
## <a name="see-also"></a>См. также  
 [Справочник по директивам](../../assembler/masm/directives-reference.md)