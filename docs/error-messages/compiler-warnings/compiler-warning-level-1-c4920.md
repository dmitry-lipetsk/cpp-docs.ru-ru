---
title: "Предупреждение (уровень 1) C4920 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4920
dev_langs: C++
helpviewer_keywords: C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c87237f5ac2240cfd2063c58055d626b72285287
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4920"></a>Предупреждение компилятора (уровень 1) C4920
enum enum member member=value уже включен в перечисление enum как member=value  
  
 Если TLB-файл, который передается в директиву #import, имеет один знак, определенный как минимум в двух перечислениях, это предупреждение указывает, что последующие идентичные знаки игнорируются и будут переведены в комментарии в TLH-файле.  
  
 Предположим, TLB-файл имеет следующее содержимое:  
  
```  
library MyLib  
{  
    typedef enum {  
        enumMember = 512  
    } AProblem;  
  
    typedef enum {  
        enumMember = 1024  
    } BProblem;  
};  
```  
  
 В следующих примерах возникнет предупреждение C4920:  
  
```  
// C4920.cpp  
// compile with: /W1  
#import "t4920.tlb"   // C4920  
  
int main() {  
}  
```