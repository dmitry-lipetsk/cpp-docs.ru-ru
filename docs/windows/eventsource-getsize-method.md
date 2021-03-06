---
title: "Метод EventSource::GetSize | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::EventSource::GetSize
dev_langs: C++
helpviewer_keywords: GetSize method
ms.assetid: 7825aab5-1a6b-465f-9159-3a6684142d1f
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ef2f51d2f53b05ae651e811c1d53ceccdab7ad5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="eventsourcegetsize-method"></a>Метод EventSource::GetSize
Возвращает число обработчиков событий, связанных с текущим объектом EventSource  
  
## <a name="syntax"></a>Синтаксис  
  
```  
size_t GetSize() const;  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Количество обработчиков событий в [targets_](../windows/eventsource-targets-data-member.md).  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** event.h  
  
 **Пространство имен:** Microsoft::WRL  
  
## <a name="see-also"></a>См. также  
 [Класс EventSource](../windows/eventsource-class.md)