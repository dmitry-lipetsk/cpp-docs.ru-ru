---
title: "Предупреждение (уровень 4) C4255 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4255
dev_langs: C++
helpviewer_keywords: C4255
ms.assetid: 2087b635-4b4c-4182-8a01-c26770d2bb88
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b750bc866dbc5eb36eaa25febca8f1fd5cc8b789
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4255"></a>Предупреждение компилятора (уровень 4) C4255
«функция»: не представлен прототип функции: преобразование «()» в «(void)»  
  
 Компилятор не обнаружил явный список аргументов функции. Это предупреждение действует только компилятором C.  
  
 Это предупреждение отключено по умолчанию. Подробнее: [Выключенные по умолчанию предупреждения компилятора](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .  
  
 Следующий пример приводит к возникновению ошибки C4255:  
  
```  
// C4255.c  
// compile with: /W4 /WX  
#pragma warning (default : 4255)  
  
void f()  { // C4255  
// try the following line instead  
//void f(void) {  
}  
  
int main(int argc, char *argv[]) {  
   f();  
}  
```