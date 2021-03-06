---
title: "Перечисление AsyncStatusInternal | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::Details::AsyncStatusInternal
dev_langs: C++
helpviewer_keywords: AsyncStatusInternal enumeration
ms.assetid: b783923f-3f1c-4487-9384-be572cbc62d7
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bd277fecb0bc63d5ee823af98df8aa298b285964
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="asyncstatusinternal-enumeration"></a>AsyncStatusInternal - перечисление
Поддерживает инфраструктуру WRL и не предназначен для использования непосредственно из программного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum AsyncStatusInternal;  
```  
  
## <a name="remarks"></a>Примечания  
 Задает сопоставление между внутренними перечислениями состояний асинхронных операций и **Windows::Foundation::AsyncStatus** перечисления.  
  
## <a name="members"></a>Участники  
 `_Created`  
 Эквивалентно ::Windows::Foundation::AsyncStatus::Created  
  
 `_Started`  
 Эквивалентно ::Windows::Foundation::AsyncStatus::Started  
  
 `_Completed`  
 Эквивалентно ::Windows::Foundation::AsyncStatus::Completed  
  
 `_Cancelled`  
 Эквивалентно ::Windows::Foundation::AsyncStatus::Cancelled  
  
 `_Error`  
 Эквивалентно ::Windows::Foundation::AsyncStatus::Error  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** async.h  
  
 **Пространство имен:** Microsoft::wrl:: Details  
  
## <a name="see-also"></a>См. также  
 [Пространство имен Microsoft::WRL::Details](../windows/microsoft-wrl-details-namespace.md)