---
title: "Конструктор WeakRef::WeakRef | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::WeakRef::WeakRef
dev_langs: C++
helpviewer_keywords: WeakRef, constructor
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 125fe25179ddbe975530a0c368a4dfc7e4caaf1a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="weakrefweakref-constructor"></a>Конструктор WeakRef::WeakRef
Инициализирует новый экземпляр класса WeakRef.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
WeakRef();  
WeakRef(  
   decltype(__nullptr)  
);  
  
WeakRef(  
   _In_opt_ IWeakReference* ptr  
);  
  
WeakRef(  
   const ComPtr<IWeakReference>& ptr  
);  
  
WeakRef(  
   const WeakRef& ptr  
);  
  
WeakRef(  
   _Inout_ WeakRef&& ptr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ptr`  
 Указатель, ссылка или ссылка rvalue на существующий объект, который инициализирует текущий объект WeakRef.  
  
## <a name="remarks"></a>Примечания  
 Первый конструктор инициализирует пустой объект WeakRef. Второй конструктор инициализирует объект WeakRef из указателя на интерфейс IWeakReference. Третий конструктор инициализирует объект WeakRef из ссылки на объект ComPtr\< IWeakReference > объекта. Четвертый и пятый конструкторы инициализирует объект WeakRef из другой объект WeakRef.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** client.h  
  
 **Пространство имен:** Microsoft::WRL  
  
## <a name="see-also"></a>См. также  
 [Класс WeakRef](../windows/weakref-class.md)