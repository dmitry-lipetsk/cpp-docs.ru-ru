---
title: "library_block | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.library_block
dev_langs: C++
helpviewer_keywords: library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ab7c4c8c65d23dc252fb3ce228313fb36aa7e032
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="libraryblock"></a>library_block
Помещает конструкцию внутри блока библиотеки IDL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
[library_block]  
  
```  
  
## <a name="remarks"></a>Примечания  
 При размещении конструкции внутри блока библиотеки убедитесь, оно передается в библиотеку типов, независимо от того, является ли ссылка на. По умолчанию, единственными конструкциями изменяемом [coclass](../windows/coclass.md), [disp-интерфейса](../windows/dispinterface.md), и [idl_module](../windows/idl-module.md) атрибуты помещаются в блок library.  
  
## <a name="example"></a>Пример  
 В следующем коде пользовательский интерфейс помещается внутри блока библиотеки.  
  
```  
// cpp_attr_ref_library_block.cpp  
// compile with: /LD  
#include <windows.h>  
[module(name="MyLib")];  
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface IMyInterface {  
   HRESULT f1();  
};  
```  
  
## <a name="requirements"></a>Требования  
  
### <a name="attribute-context"></a>Контекст атрибута  
  
|||  
|-|-|  
|**Применение**|В любом месте|  
|**Повторяемый**|Нет|  
|**Обязательные атрибуты**|Нет|  
|**Недопустимые атрибуты**|Нет|  
  
 Дополнительные сведения см. в разделе [Контексты атрибутов](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>См. также  
 [Атрибуты компилятора](../windows/compiler-attributes.md)   
 [Изолированные атрибуты](../windows/stand-alone-attributes.md)   
