---
title: "Ошибка компилятора C2262 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2262
dev_langs: C++
helpviewer_keywords: C2262
ms.assetid: 727d1c6e-53e8-40e5-b7b8-6a7ac2011727
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f569c3aa09c08b7553800d39be8ad6d50f8a5b3a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2262"></a>Ошибка компилятора C2262
"спецификаторы_атрибутов": в объявлениях InternalsVisibleTo невозможно указывать версию, культуру или архитектуру процессора  
  
 Атрибут <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> указан неправильно.  
  
## <a name="example"></a>Пример  
 Следующий пример приводит к возникновению ошибки C2262:  
  
```  
// C2262.cpp  
// compile with: /clr /c  
using namespace System::Runtime::CompilerServices;  
[assembly: InternalsVisibleTo("assembly_name, version=1.2.3.7")];   // C2262  
[assembly: InternalsVisibleTo("assembly_name ")];   // OK  
```