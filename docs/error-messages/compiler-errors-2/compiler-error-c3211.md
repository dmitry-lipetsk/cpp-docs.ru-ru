---
title: "Ошибка компилятора C3211 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3211
dev_langs: C++
helpviewer_keywords: C3211
ms.assetid: 85e33fed-3b59-4315-97e6-20d31c6a985a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b3ceee4bd6822bcd8faeb2f992c7727e7c083e33
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3211"></a>Ошибка компилятора C3211
"явная специализация": явная специализация с синтаксисом частичной специализации; замените на "template <>"  
  
 Явная специализация имеет неправильный формат.  
  
 Следующий пример приводит к возникновению ошибки C3211:  
  
```  
// C3211.cpp  
// compile with: /LD  
template<class T>  
struct s;  
  
template<class T>  
// use the following line instead  
// template<>  
struct s<int>{};   // C3211  
```