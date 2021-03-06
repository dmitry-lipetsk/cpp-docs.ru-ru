---
title: "Предупреждение (уровень 4) C4263 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4263
dev_langs: C++
helpviewer_keywords: C4263
ms.assetid: daabb05d-ab56-460f-ab6c-c74d222ef649
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 47f871f956ef07eebc2f528182dde58ba0fa3b2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4263"></a>Предупреждение компилятора (уровень 4) C4263
«функция»: функция-член не переопределяет ни одной функции виртуальный член базового класса  
  
 Определение функции класса имеет то же имя, что и виртуальная функция базового класса, но же число и тип аргументов. Данный подход скрывает виртуальную функцию в базовом классе.  
  
 Это предупреждение отключено по умолчанию. Подробнее: [Выключенные по умолчанию предупреждения компилятора](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .  
  
 Следующий пример приводит к возникновению ошибки C4263:  
  
```  
// C4263.cpp  
// compile with: /W4  
#pragma warning(default:4263)  
#pragma warning(default:4264)  
class B {  
public:  
   virtual void func();  
};  
  
class D : public B {  
   void func(int);   // C4263  
};  
  
int main() {  
}  
```