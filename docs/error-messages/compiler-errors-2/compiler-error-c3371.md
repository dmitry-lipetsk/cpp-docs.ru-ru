---
title: "Ошибка компилятора C3371 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3371
dev_langs: C++
helpviewer_keywords: C3371
ms.assetid: f7ecf1aa-ed0a-4f73-81e5-62cf98f88ea1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0691c1a3598a9f0f143142fb1620448fe47a816
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3371"></a>Ошибка компилятора C3371
idl_module: здесь допускается только свойство "name"  
  
 Использование[idl_module](../../windows/idl-module.md) непосредственно в объявлении функции не может иметь никакие параметры, кроме имени.  
  
 В следующем примере возникает ошибка C3371:  
  
```  
// C3371.cpp  
[idl_module(name="Name", dllname="Some.dll")];  
[idl_module(name="Name", helpstring="Some help")]   // C3371  
int f1();  
// try  
// [idl_module(name="Name")]  
// int f1();  
  
int main()  
{  
}  
```