---
title: ". ПОВТОРИТЕ | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .REPEAT
dev_langs:
- C++
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b5e2bee231ebbf1ec04e56a6cc3a2b2d8b03ecd2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="repeat"></a>.REPEAT
Создает код, который повторяет выполнение блока *инструкций* до `condition` становится значение true. [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md), которая становится значение true, когда CX равно нулю, может быть замещен [. ПОКА](../../assembler/masm/dot-until.md). `condition` Необязателен с **. UNTILCXZ**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
   .REPEAT  
statements  
.UNTIL condition  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по директивам](../../assembler/masm/directives-reference.md)