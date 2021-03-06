---
title: "Ошибка компилятора C2217 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2217
dev_langs: C++
helpviewer_keywords: C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6af2bbd43d6e522bbe6ede2a874b7e8ebbf27c10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2217"></a>Ошибка компилятора C2217
«атрибут1» требуется «атрибут2»  
  
 Первый атрибут функции требует второй атрибут.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Чтобы устранить ошибку, проверьте указанные ниже возможные причины ее возникновения.  
  
1.  Прерывание (`__interrupt`) функция объявлена как `near`. Прерывание функции должны быть `far`.  
  
2.  Прервать в функции, объявленной с `__stdcall`, или `__fastcall`. Функции обработки прерываний должны использовать C соглашения о вызовах.  
  
## <a name="example"></a>Пример  
 C2217 также может возникать при попытке привязать делегат функции среды CLR, которая принимает переменное число аргументов. Если функция имеет массив e param, используйте ее. Следующий пример приводит к возникновению ошибки C2217.  
  
```  
// C2217.cpp  
// compile with: /clr  
using namespace System;  
delegate void MyDel(String^, Object^, Object^, ...);   // C2217  
delegate void MyDel2(String ^, array<Object ^> ^);   // OK  
  
int main() {  
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);  
   array<Object ^ > ^ x = gcnew array<Object ^>(2);  
   x[0] = safe_cast<Object^>(0);  
   x[1] = safe_cast<Object^>(1);  
  
   // wl("{0}, {1}", 0, 1);  
   wl("{0}, {1}", x);  
}  
```