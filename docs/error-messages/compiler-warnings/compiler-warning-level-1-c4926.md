---
title: "Ошибка компилятора предупреждение (уровень 1) C4926 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4926
dev_langs: C++
helpviewer_keywords: C4926
ms.assetid: 5717fce0-146f-4ef2-bde0-e9a01c0922d1
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2e552fb7014b5afcda70f0b69c53dd0f9008e1d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4926"></a>Предупреждение компилятора (уровень 1) C4926
"идентификатор": символ уже определен: атрибуты игнорируются  
  
 Обнаружено опережающее объявление, но конструкция с атрибутами с тем же именем уже существует. Атрибуты для опережающего объявления игнорируются.  
  
 В следующем примере возникает ошибка C4926.  
  
```  
// C4926.cpp  
// compile with: /W1  
[module(name="MyLib")];  
  
[coclass]  
struct a {  
};  
  
[coclass]  
struct a;   // C4926  
  
int main() {  
}  
```