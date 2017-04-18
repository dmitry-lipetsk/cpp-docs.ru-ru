---
title: "ML Fatal Error A1011 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A1011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A1011"
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Fatal Error A1011
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**рекомендация должна находиться в блоке элемента управления**  
  
 Ассемблер обнаружил высокоуровневую директиву, в котором не следует ожидать.  Одной из следующих директив найдено:  
  
-   [.ELSE](../../assembler/masm/dot-else.md) без  [.IF](../Topic/.IF.md)  
  
-   [.ENDIF](../../assembler/masm/dot-endif.md) без  [.IF](../Topic/.IF.md)  
  
-   [.ENDW](../../assembler/masm/dot-endw.md) без  [.WHILE](../../assembler/masm/dot-while.md)  
  
-   [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md) без  [.REPEAT](../../assembler/masm/dot-repeat.md)  
  
-   [.CONTINUE](../Topic/.CONTINUE.md) без  [.WHILE](../../assembler/masm/dot-while.md) OR  [.REPEAT](../../assembler/masm/dot-repeat.md)  
  
-   [.BREAK](../../assembler/masm/dot-break.md) без  [.WHILE](../../assembler/masm/dot-while.md) OR  [.REPEAT](../../assembler/masm/dot-repeat.md)  
  
-   [.ELSE](../../assembler/masm/dot-else.md) уточняющий запрос  `.ELSE`  
  
## См. также  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)