---
title: "Структура COMPAREITEMSTRUCT | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COMPAREITEMSTRUCT
dev_langs: C++
helpviewer_keywords: COMPAREITEMSTRUCT structure [MFC]
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7903e51a83533c8f2458c4400c64717021a1ccb8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compareitemstruct-structure"></a>Структура COMPAREITEMSTRUCT
`COMPAREITEMSTRUCT` Структура предоставляет список идентификаторов и данных приложений для двух элементов в отсортированный, определяемый владельцем список или поле со списком.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef struct tagCOMPAREITEMSTRUCT {  
    UINT CtlType;  
    UINT CtlID;  
    HWND hwndItem;  
    UINT itemID1;  
    DWORD itemData1;  
    UINT itemID2;  
    DWORD itemData2;  
} COMPAREITEMSTRUCT;  
```  
  
#### <a name="parameters"></a>Параметры  
 `CtlType`  
 **ODT_LISTBOX** (которое указывает список рисуемый владельцем) или **ODT_COMBOBOX** (которое указывает рисуемый владельцем поле со списком).  
  
 `CtlID`  
 Идентификатор элемента управления для списка или поля со списком.  
  
 `hwndItem`  
 Дескриптор окна элемента управления.  
  
 *itemID1*  
 Индекс первого элемента в список или поле со списком сравниваемых.  
  
 *itemData1*  
 Указанное приложением данных сравниваемых первого элемента. Это значение было передано в вызове, добавившего элемент в поле со списком или списка.  
  
 *itemID2*  
 Индекс второго элемента в список или поле со списком сравниваемых.  
  
 *itemData2*  
 Указанное приложением данных сравниваемых второго элемента. Это значение было передано в вызове, добавившего элемент в поле со списком или списка.  
  
## <a name="remarks"></a>Примечания  
 Каждый раз, когда приложение добавляет новый элемент — определяемый владельцем список или поле со списком создается **CBS_SORT** или **LBS_SORT** стиля, Windows отправляет владельцу `WM_COMPAREITEM` сообщения. `lParam` Сообщения содержит длинный указатель `COMPAREITEMSTRUCT` структуры. При получении сообщения, владелец сравнивает два элемента и возвращает значение, указывающее, какой элемент сортируется до другого.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** winuser.h  
  
## <a name="see-also"></a>См. также  
 [Структуры, стили, обратные вызовы и схемы сообщений](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)

