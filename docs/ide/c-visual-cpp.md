---
title: "&lt;c&gt; (Visual C++) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <c>
dev_langs: C++
helpviewer_keywords:
- <c> C++ XML tag
- c C++ XML tag
ms.assetid: 3b23fc0f-e10d-4dd0-b197-48a46cbddd9f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b8d4ea984864975196251c9f362283a0df1932cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="ltcgt-visual-c"></a>&lt;c&gt; (Visual C++)
\<c > тег указывает, что текст в описании должен быть помечен как код. Чтобы определить несколько строк в качестве кода, используйте тег [\<code>](../ide/code-visual-cpp.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<c>text</c>  
```  
  
#### <a name="parameters"></a>Параметры  
 `text`  
 Текст, который вы хотите указать в качестве кода.  
  
## <a name="remarks"></a>Примечания  
 Чтобы обработать и сохранить комментарии документации в файл, при компиляции необходимо использовать параметр [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md).  
  
## <a name="example"></a>Пример  
  
```  
// xml_c_tag.cpp  
// compile with: /doc /LD  
// post-build command: xdcmake xml_c_tag.xdc  
  
/// Text for class MyClass.  
class MyClass {  
public:  
   int m_i;  
   MyClass() : m_i(0) {}  
  
   /// <summary><c>MyMethod</c> is a method in the <c>MyClass</c> class.  
   /// </summary>  
   int MyMethod(MyClass * a) {  
      return a -> m_i;  
   }  
};  
```  
  
## <a name="see-also"></a>См. также  
 [Документация XML](../ide/xml-documentation-visual-cpp.md)