---
title: "Ошибка компилятора предупреждение (уровень 1) C4075 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4075
dev_langs: C++
helpviewer_keywords: C4075
ms.assetid: 19a700b6-f210-4b9d-a2f2-76cfe39ab178
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c4f2fe1355f883addfd162614bad3ec861002abc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4075"></a>Предупреждение компилятора (уровень 1) C4075
инициализаторы в неопознанной области инициализации  
  
 Директива [#pragma init_seg](../../preprocessor/init-seg.md) использует неизвестное имя раздела. Компилятор игнорирует команду **pragma** .  
  
 В следующем примере возникает ошибка C4075.  
  
```  
// C4075.cpp  
// compile with: /W1  
#pragma init_seg("mysegg")   // C4075  
  
// try..  
// #pragma init_seg(user)  
  
int main() {  
}  
```