---
title: "Ошибка компилятора C3890 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3890
dev_langs: C++
helpviewer_keywords: C3890
ms.assetid: 2f22c2fd-c14e-45e1-b936-b739ffc0b135
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a83fa8f946ef79cb73fbd04bd67723182a2273a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3890"></a>Ошибка компилятора C3890
«переменная»: невозможно получить адрес данных-члена литерала  
  
 Данные-член литерала существует в куче сбора мусора.  Можно переместить объекта в куче сбора мусора, поэтому получение адреса не является полезным.  
  
 Следующий пример приводит к возникновению ошибки C3890:  
  
```  
// C3890.cpp  
// compile with: /clr  
ref struct Y1 {  
   literal int staticConst = 9;  
};  
  
int main() {  
   int p = &Y1::staticConst;   // C3890  
   int p2 = Y1::staticConst;   // OK  
}  
```