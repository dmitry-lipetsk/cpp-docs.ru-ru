---
title: "Идентификатор ProgID | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.progid
dev_langs: C++
helpviewer_keywords: progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 862629af7e279cf1f03a5e9adc9424b330ee1d90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="progid"></a>progid
Указывает идентификатор ProgID для COM-объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      [ progid(  
   name  
) ];  
```  
  
#### <a name="parameters"></a>Параметры  
 *name*  
 Идентификатор ProgID, представляющий объект.  
  
 Идентификаторы ProgID предоставляют более удобной для чтения версии идентификатор класса (CLSID), используемый для идентификации объектов COM и ActiveX.  
  
## <a name="remarks"></a>Примечания  
 **Progid** языка c++ позволяет указать идентификатор ProgID для COM-объекта. Идентификатор ProgID имеет форму *name1.name2.version*. Если вы не укажете *версии* для ProgID, версия по умолчанию равно 1. Если вы не укажете *name1.name2*, является именем по умолчанию *classname.classname*. Если вы не укажете **progid** и указать **vi_progid**, *name1.name2* взяты из **vi_progid** и (Далее последовательных добавляется номер) версии.  
  
 Если блок атрибута, который использует **progid** также не используйте `uuid`, компилятор проверяет реестр на наличие `uuid` существует для указанного **progid**. Если **progid** не указан, версии (и именем компонентного класса, если создание компонентного класса) будет использоваться для создания **progid**.  
  
 **Идентификатор ProgID** подразумевает **coclass** атрибута, то есть, при указании **progid**, это то же самое, что и при указании **coclass** и  **Идентификатор ProgID** атрибуты.  
  
 **Progid** атрибут заставляет класс автоматически регистрироваться под указанным именем. Созданного IDL-файла не будут отображаться **progid** значение.  
  
 Если этот атрибут используется в проект, использующий ATL, изменяет поведение атрибута. Помимо описанное выше поведение сведений, указанных с помощью этого атрибута используется в **GetProgID** функции, введенному **coclass** атрибута. Дополнительные сведения см. в разделе [coclass](../windows/coclass.md) атрибута.  
  
## <a name="example"></a>Пример  
 Далее приведен пример [coclass](../windows/coclass.md) для приведен пример использования **progid**.  
  
## <a name="requirements"></a>Требования  
  
### <a name="attribute-context"></a>Контекст атрибута  
  
|||  
|-|-|  
|**Применение**|**class**, `struct`|  
|**Повторяемый**|Нет|  
|**Обязательные атрибуты**|Нет|  
|**Недопустимые атрибуты**|Нет|  
  
 Дополнительные сведения о контекстах атрибутов см. в разделе [Контексты атрибутов](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>См. также  
 [Атрибуты IDL](../windows/idl-attributes.md)   
 [Атрибуты классов](../windows/class-attributes.md)   
 [TypeDef, Enum, Union и Struct атрибуты](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Идентификатор progID ключ](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
