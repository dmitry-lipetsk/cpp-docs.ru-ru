---
title: "Ошибка компилятора C3099 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3099
dev_langs: C++
helpviewer_keywords: C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a644a27c834efcd3c3857241927a6e618f600d0c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3099"></a>Ошибка компилятора C3099
keyword: используйте [System::AttributeUsageAttribute] для управляемых атрибутов; используйте [Windows::Foundation::Metadata::AttributeUsageAttribute] для атрибутов WinRT  
  
 Используйте <xref:System.AttributeUsageAttribute> для объявления **/CLR** атрибуты. Используйте `Windows::Foundation::Metadata::AttributeUsageAttribute` для объявления атрибутов среды выполнения Windows.  
  
 Дополнительные сведения об атрибутах/CLR см. в разделе [определяемые пользователем атрибуты](../../windows/user-defined-attributes-cpp-component-extensions.md). Для атрибутов, поддерживаемых в среды выполнения Windows, в разделе [имен Windows.Foundation.Metadata](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.aspx)  
  
## <a name="example"></a>Пример  
 В следующем примере показано возникновение ошибки C3099 и приводятся сведения по ее устранению.  
  
```  
// C3099.cpp  
// compile with: /clr /c  
using namespace System;  
[usage(10)]   // C3099  
// try the following line instead  
// [AttributeUsageAttribute(AttributeTargets::All)]  
ref class A : Attribute {};  
```