---
title: "Предупреждение компилятора (уровень 1) C4395 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4395
dev_langs: C++
helpviewer_keywords: C4395
ms.assetid: 8051469a-3a39-4677-80f7-1300fbffe8ea
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4befed8df0b9fe9960db1060150b238c0707d8f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4395"></a>Предупреждение компилятора (уровень 1) C4395
«функция»: функция-член будет вызываться для копии данных initonly «член»  
  
 Функция-член вызывается на [initonly (C + +/ CLI)](../../dotnet/initonly-cpp-cli.md) члена данных.  Предупреждение C4395, что **initonly** член данных не может изменяться функцией.  
  
 Следующий пример приводит к возникновению ошибки C4395:  
  
```  
// C4395.cpp  
// compile with: /W1 /clr  
public value class V {  
public:  
   V(int data) : m_data(data) {}  
  
   void Mutate() {  
      System::Console::WriteLine("Enter Mutate: m_data = {0}", m_data);  
      m_data *= 2;  
      System::Console::WriteLine("Leave Mutate: m_data = {0}", m_data);  
   }  
  
   int m_data;  
};  
  
public ref class R {  
public:  
   static void f() {  
      System::Console::WriteLine("v.m_data = {0}", v.m_data);  
      v.Mutate();   // C4395  
      System::Console::WriteLine("v.m_data = {0}", v.m_data);  
   }  
  
private:  
   initonly static V v = V(4);  
};  
  
int main() {  
   R::f();  
}  
```