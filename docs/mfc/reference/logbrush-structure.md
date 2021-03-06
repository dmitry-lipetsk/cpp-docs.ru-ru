---
title: "Структура LOGBRUSH | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LOGBRUSH
dev_langs: C++
helpviewer_keywords: LOGBRUSH structure [MFC]
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ec6cc9b61f837db4c9766c077fa60f4d9c2b95bd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="logbrush-structure"></a>Структура LOGBRUSH
`LOGBRUSH` Структура определяет стиль, цвет и шаблон физического кисти. Он используется Windows [CreateBrushIndirect](http://msdn.microsoft.com/library/windows/desktop/dd183487) и [ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705) функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
typedef struct tag LOGBRUSH { /* lb */  
    UINT lbStyle;  
    COLORREF lbColor;  
    LONG lbHatch;  
} LOGBRUSH;  
```  
  
#### <a name="parameters"></a>Параметры  
 `lbStyle`  
 Задает стиль кисти. `lbStyle` Член должен быть одним из следующих стилей:  
  
- **BS_DIBPATTERN** шаблон кисти, определенные спецификацией аппаратно независимый точечный рисунок (DIB). Если `lbStyle` — **BS_DIBPATTERN**, **lbHatch** член содержит дескриптор упакованный DIB.  
  
- **BS_DIBPATTERNPT** шаблон кисти, определенные спецификацией аппаратно независимый точечный рисунок (DIB). Если `lbStyle` — **BS_DIBPATTERNPT**, **lbHatch** член содержит указатель на упакованный DIB.  
  
- **BS_HATCHED** Hatched кисти.  
  
- **BS_HOLLOW** пустая кисти.  
  
- **BS_NULL** то же, что **BS_HOLLOW**.  
  
- **BS_PATTERN** шаблона кисти определяется Битовая карта памяти.  
  
- **BS_SOLID** сплошной кисти.  
  
 `lbColor`  
 Задает цвет, в котором будет рисоваться кисти. Если `lbStyle` — **BS_HOLLOW** или **BS_PATTERN** стиля, **lbColor** учитывается. Если `lbStyle` — **BS_DIBPATTERN** или **BS_DIBPATTERNBT**, слова низкого порядка **lbColor** указывает, является ли **bmiColors**члены [BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md) структура содержит явное красный, зеленый, синий значений (RGB) или индексов в момент реализованных логическую палитру. **LbColor** член должен быть одним из следующих значений:  
  
- **DIB_PAL_COLORS** таблица цветов состоит из массива 16-разрядными индексами, в момент реализованных логическую палитру.  
  
- **DIB_RGB_COLORS** таблица цветов содержит литеральные значения RGB.  
  
 *lbHatch*  
 Задает стиль штриховки. Значение зависит от стиля кисти, описанного в `lbStyle`. Если `lbStyle` — **BS_DIBPATTERN**, **lbHatch** член содержит дескриптор упакованный DIB. Если `lbStyle` — **BS_DIBPATTERNPT**, **lbHatch** член содержит указатель на упакованный DIB. Если `lbStyle` — **BS_HATCHED**, **lbHatch** задает ориентацию линии, используемые для создания штриховки. Он может принимать одно из следующих значений:  
  
- `HS_BDIAGONAL`45 градусов штриховку вверх, слева направо  
  
- `HS_CROSS`Горизонтальные и вертикальные штриховки.  
  
- `HS_DIAGCROSS`штриховки 45 градусов  
  
- `HS_FDIAGONAL`45 градусов штриховку вниз, влево и вправо  
  
- `HS_HORIZONTAL`Горизонтальная штриховка  
  
- `HS_VERTICAL`Вертикальная штриховка  
  
 Если `lbStyle` — **BS_PATTERN**, **lbHatch** — это дескриптор для точечного рисунка, который определяет шаблон. Если `lbStyle` — **BS_SOLID** или **BS_HOLLOW**, **lbHatch** учитывается.  
  
## <a name="remarks"></a>Примечания  
 Несмотря на то что **lbColor** определяет цвет переднего плана для кистей штриховки [CDC::SetBkMode](../../mfc/reference/cdc-class.md#setbkmode) и [CDC::SetBkColor](../../mfc/reference/cdc-class.md#setbkcolor) функции управления цветом фона.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** wingdi.h  
  
## <a name="see-also"></a>См. также  
 [Структуры, стили, обратные вызовы и схемы сообщений](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

