---
title: "Комментарии в файле Makefile | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: makefiles, comments
ms.assetid: 76fd9e3d-5966-47f4-a091-c9e80b232b49
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dfd8e3dda4014048a4f39191b555b1eff1d97288
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="comments-in-a-makefile"></a>Комментарии в файлах makefile
Перед комментарием символом решетки (#). NMAKE игнорирует текст из решетки к следующему символу новой строки. Примеры  
  
```  
# Comment on line by itself  
OPTIONS = /MAP  # Comment on macro definition line  
  
all.exe : one.obj two.obj  # Comment on dependency line  
    link one.obj two.obj  
# Comment in commands block  
#   copy *.obj \objects  # Command turned into comment  
    copy one.exe \release  
  
.obj.exe:  # Comment on inference rule line  
    link $<  
  
my.exe : my.obj ; link my.obj  # Err: cannot comment this  
 # Error: # must be the first character  
.obj.exe: ; link $<  # Error: cannot comment this  
```  
  
 Чтобы указать литерал решетки, поместите перед ней знак вставки (**^**), как показано ниже:  
  
```  
DEF = ^#define  #Macro for a C preprocessing directive  
```  
  
## <a name="see-also"></a>См. также  
 [Содержимое файла Makefile](../build/contents-of-a-makefile.md)