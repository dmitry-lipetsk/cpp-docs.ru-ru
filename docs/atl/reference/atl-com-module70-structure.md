---
title: "Структура _ATL_COM_MODULE70 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 573bf43c783a1fb5dbd0eca364fedddb9bafbac7
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="atlcommodule70-structure"></a>Структура _ATL_COM_MODULE70
Используемый код с COM в ATL  
  
## <a name="syntax"></a>Синтаксис  
  
```
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```  
  
## <a name="members"></a>Участники  
 `cbSize`  
 Размер структуры, используемые для управления версиями.  
  
 `m_hInstTypeLib`  
 Дескриптор экземпляра, в библиотеку типов для этого модуля.  
  
 **m_ppAutoObjMapFirst**  
 Адрес элемента массива, указывающее начало карты записей объект для этого модуля.  
  
 **m_ppAutoObjMapLast**  
 Адрес элемента массива, указывая на конец объекта карты записей для этого модуля.  
  
 `m_csObjMap`  
 Для сериализации доступ к записям карты объект критической секции. Используется внутренними механизмами ATL.  
  
## <a name="remarks"></a>Примечания  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) определяется как typedef из `_ATL_COM_MODULE70`.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atlbase.h  
  
## <a name="see-also"></a>См. также  
 [Структуры](../../atl/reference/atl-structures.md)





