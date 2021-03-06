---
title: "Ошибка компилятора C2228 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2228
dev_langs: C++
helpviewer_keywords: C2228
ms.assetid: 901cadb1-ce90-4ae0-a360-547a9ba2ca18
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0d2f16e67f67ac00fa17f6b60f70af53ae7345df
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2228"></a>Ошибка компилятора C2228
слева от ".identifier" должен быть указан класс, структура или объединение  
  
 Операнд слева от точки (.) не класса, структуры или объединения.  
  
 Следующий пример приводит к возникновению ошибки C2228:  
  
```  
// C2228.cpp  
int i;  
struct S {  
public:  
    int member;  
} s, *ps = &s;  
  
int main() {  
   i.member = 0;   // C2228 i is not a class type  
   ps.member = 0;  // C2228 ps is a pointer to a structure  
  
   s.member = 0;   // s is a structure type  
   ps->member = 0; // ps points to a structure S  
}  
```  
  
 Эта ошибка также возникает из-за неправильного синтаксиса при использовании управляемых расширений. В то время как в других языках Visual Studio для доступа к члену управляемого класса можно использовать оператор "точка", в C++ указатель на объект означает, что для доступа к члену вы должны использовать оператор ->:  
  
 Неправильно: `String * myString = checkedListBox1->CheckedItems->Item[0].ToString();`  
  
 Правильно: `String * myString = checkedListBox1->CheckedItems->Item[0]->ToString();`