---
title: "Метод MakeAllocator::Detach | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::MakeAllocator::Detach
dev_langs: C++
helpviewer_keywords: Detach method
ms.assetid: 78012634-2dda-4ea2-9ffe-40f105d2fe47
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d114f48a2d4da7916f6ee7439a92297360b8476e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="makeallocatordetach-method"></a>Метод MakeAllocator::Detach
Поддерживает инфраструктуру WRL и не предназначен для использования непосредственно из программного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
__forceinline void Detach();  
```  
  
## <a name="remarks"></a>Примечания  
 Отсоединяет памяти, выделенной с помощью [Allocate](../windows/makeallocator-allocate-method.md) метод с текущим объектом MakeAllocator.  
  
 Если вызвать Detach(), вы отвечаете за удаление памяти, предоставляемый методом распределения.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** implements.h  
  
 **Пространство имен:** Microsoft::wrl:: Details  
  
## <a name="see-also"></a>См. также  
 [MakeAllocator-класс](../windows/makeallocator-class.md)   
 [Пространство имен Microsoft::WRL::Details](../windows/microsoft-wrl-details-namespace.md)