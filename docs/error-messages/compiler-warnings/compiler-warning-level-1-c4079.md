---
title: "Предупреждение (уровень 1) C4079 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4079
dev_langs: C++
helpviewer_keywords: C4079
ms.assetid: 549759f0-e168-47e9-8c9a-de93ac843689
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ead27a4a9cf2da2b97089cef207ccf518d268ff7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4079"></a>Предупреждение (уровень 1) C4079 компилятора
непредвиденный токен "токен"  
  
 Непредвиденная лексема-разделитель в списке аргументов директивы pragma. В оставшейся части директива pragma была пропущена.  
  
 Следующий пример приводит к возникновению ошибки C4079:  
  
```  
// C4079.cpp  
// compile with: /W1  
#pragma warning(disable : 4081)  
#pragma pack(c,16)   // C4079  
  
int main() {  
}  
```