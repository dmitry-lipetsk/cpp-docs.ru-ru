---
title: "Ошибка компилятора C2731 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2731
dev_langs: C++
helpviewer_keywords: C2731
ms.assetid: 9b563999-febd-4582-9147-f355083c091e
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b6df60a548c5601c7f7ff7827a8982dab56605ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2731"></a>Ошибка компилятора C2731
«Идентификатор»: функция не может быть перегружен  
  
 Функции `main`, `WinMain`, `DllMain`, и `LibMain` не могут быть перегружены.  
  
 Следующий пример приводит к возникновению ошибки C2731:  
  
```  
// C2731.cpp  
extern "C" void WinMain(int, char *, char *);  
void WinMain(int, short, char *, char*);   // C2731  
```