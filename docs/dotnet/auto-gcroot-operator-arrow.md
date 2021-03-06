---
title: "auto_gcroot::operator -&gt; | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- auto_gcroot.operator->
- msclr::auto_gcroot::operator->
- auto_gcroot::operator->
- msclr.auto_gcroot.operator->
dev_langs: C++
helpviewer_keywords: operator->
ms.assetid: 2c77bc53-5f77-4544-9485-c950cd8e0bb1
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4e5fcce39ca44297d28744b5ce663be0db4dd185
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="autogcrootoperator-gt"></a>auto_gcroot::operator-&gt;
Оператор доступа к членам.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
_element_type operator->() const;  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект, который является оболочкой для `auto_gcroot`.  
  
## <a name="example"></a>Пример  
  
```  
// msl_auto_gcroot_op_arrow.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
protected:     
   String^ m_s;  
public:  
   ClassA( String^ s ) : m_s( s ) {}  
  
   virtual void PrintHello() {  
      Console::WriteLine( "Hello from {0} A!", m_s );  
   }  
  
   int m_i;  
};  
  
int main() {  
   auto_gcroot<ClassA^> a( gcnew ClassA( "first" ) );  
   a->PrintHello();  
  
   a->m_i = 5;  
   Console::WriteLine( "a->m_i = {0}", a->m_i );  
}  
```  
  
```Output  
Hello from first A!  
a->m_i = 5  
```  
  
## <a name="requirements"></a>Требования  
 **Файл заголовка** \<msclr\auto_gcroot.h >  
  
 **Пространство имен** msclr  
  
## <a name="see-also"></a>См. также  
 [Члены auto_gcroot](../dotnet/auto-gcroot-members.md)   
 [auto_gcroot::get](../dotnet/auto-gcroot-get.md)