---
title: "Ошибка компилятора C3196 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3196
dev_langs: C++
helpviewer_keywords: C3196
ms.assetid: d9c38a13-191d-472d-aa2b-f61a6459d16c
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 16f03511d1f0fced049c6f9b6cdb63e7d06da835
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3196"></a>Ошибка компилятора C3196
«ключевое_слово»: используется более одного раза  
  
 Ключевое слово использовалось несколько раз.  
  
 Следующий пример приводит к возникновению ошибки C3196:  
  
```  
// C3196.cpp  
// compile with: /clr  
ref struct R abstract abstract {};   // C3196  
ref struct S abstract {};   // OK  
```