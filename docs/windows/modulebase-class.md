---
title: "Класс ModuleBase | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::ModuleBase
dev_langs: C++
helpviewer_keywords: ModuleBase class
ms.assetid: edce7591-6893-46f7-94a7-382827775548
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b02efe3ee61234b2439c1cbbae07827d6a879b2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="modulebase-class"></a>Класс ModuleBase
Поддерживает инфраструктуру WRL и не предназначен для использования непосредственно из программного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
class ModuleBase;  
```  
  
## <a name="remarks"></a>Примечания  
 Представляет базовый класс для [модуль](../windows/module-class.md) классы.  
  
## <a name="members"></a>Участники  
  
### <a name="public-constructors"></a>Открытые конструкторы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[Конструктор ModuleBase::ModuleBase](../windows/modulebase-modulebase-constructor.md)|Инициализирует новый экземпляр класса Module.|  
|[Деструктор ModuleBase::~ModuleBase](../windows/modulebase-tilde-modulebase-destructor.md)|Деинициализирует текущий экземпляр класса Module.|  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[Метод ModuleBase::DecrementObjectCount](../windows/modulebase-decrementobjectcount-method.md)|При реализации уменьшает число объектов, отслеживаемых модулем.|  
|[Метод ModuleBase::IncrementObjectCount](../windows/modulebase-incrementobjectcount-method.md)|При реализации увеличивает число объектов, отслеживаемых модулем.|  
  
## <a name="inheritance-hierarchy"></a>Иерархия наследования  
 `ModuleBase`  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** implements.h  
  
 **Пространство имен:** Microsoft::wrl:: Details  
  
## <a name="see-also"></a>См. также  
 [Пространство имен Microsoft::WRL::Details](../windows/microsoft-wrl-details-namespace.md)