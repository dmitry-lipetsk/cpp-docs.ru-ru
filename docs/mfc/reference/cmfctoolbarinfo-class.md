---
title: "Класс CMFCToolBarInfo | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo::m_uiColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuResID
dev_langs: C++
helpviewer_keywords:
- CMFCToolBarInfo [MFC], m_uiColdResID
- CMFCToolBarInfo [MFC], m_uiDisabledResID
- CMFCToolBarInfo [MFC], m_uiHotResID
- CMFCToolBarInfo [MFC], m_uiLargeColdResID
- CMFCToolBarInfo [MFC], m_uiLargeDisabledResID
- CMFCToolBarInfo [MFC], m_uiLargeHotResID
- CMFCToolBarInfo [MFC], m_uiMenuDisabledResID
- CMFCToolBarInfo [MFC], m_uiMenuResID
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c47be3ddb2302124b233c39aaf8bd829cd481d79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctoolbarinfo-class"></a>Класс CMFCToolBarInfo
Содержит идентификаторы ресурса изображений панели инструментов в различных состояниях. `CMFCToolBarInfo`— Это вспомогательный класс, используемый в качестве параметра [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
class CMFCToolBarInfo  
```  
  
## <a name="members"></a>Участники  
  
### <a name="data-members"></a>Элементы данных  
  
|name|Описание:|  
|----------|-----------------|  
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|Идентификатор ресурса точечного рисунка панели инструментов, содержащее изображения регулярных (холодный) панели инструментов.|  
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|Идентификатор ресурса точечного рисунка панели инструментов, содержащее изображения отключенные панели инструментов.|  
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|Идентификатор ресурса точечного рисунка панели инструментов, содержащее изображения выбранной панели инструментов ("горячие").|  
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|Идентификатор ресурса точечного рисунка панели инструментов, содержащее изображения больших, регулярного панель инструментов.|  
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|Идентификатор ресурса точечного рисунка панели инструментов, который содержит большие, отключить изображениям значков панели инструментов.|  
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|Идентификатор ресурса точечного рисунка панели инструментов, который содержит большие, выбрать изображениям значков панели инструментов.|  
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|Идентификатор ресурса точечного рисунка панели инструментов, который содержит отключенным изображениям значков меню.|  
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|Идентификатор ресурса точечного рисунка панели инструментов, который содержит изображения меню.|  
  
## <a name="remarks"></a>Примечания  
 Битовая карта инструментов полностью состоит из небольшого инструментов изображений (кнопки) фиксированного размера. Каждый идентификатор ресурса, которые хранятся в `CMFCToolBarInfo` объект является точечного рисунка, который содержит полный набор инструментов изображений в одно состояние (для (например, выбран будет отключен, большой или изображения меню).  
  
## <a name="inheritance-hierarchy"></a>Иерархия наследования  
 [CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** afxtoolbar.h  
  
##  <a name="m_uicoldresid"></a>CMFCToolBarInfo::m_uiColdResID  
 Указывает идентификатор ресурса для всех образов обычная кнопка панели инструментов.  
  
```  
UINT m_uiColdResID;  
```  
  
##  <a name="m_uidisabledresid"></a>CMFCToolBarInfo::m_uiDisabledResID  
 Указывает идентификатор ресурса для изображений недоступна кнопка панели инструментов.  
  
```  
UINT m_uiDisabledResID;  
```  
  
##  <a name="m_uihotresid"></a>CMFCToolBarInfo::m_uiHotResID  
 Указывает идентификатор ресурса для всех образов выделенной кнопки панели инструментов.  
  
```  
UINT m_uiHotResID  
```  
  
##  <a name="m_uilargecoldresid"></a>CMFCToolBarInfo::m_uiLargeColdResID  
 Указывает идентификатор ресурса для всех образов больших обычная кнопка панели инструментов.  
  
```  
UINT m_uiLargeColdResID  
```  
  
##  <a name="m_uilargedisabledresid"></a>CMFCToolBarInfo::m_uiLargeDisabledResID  
 Указывает идентификатор ресурса для всех образов больших отключенной кнопки панели инструментов.  
  
```  
UINT m_uiLargeDisabledResID;  
```  
  
##  <a name="m_uilargehotresid"></a>CMFCToolBarInfo::m_uiLargeHotResID  
 Указывает идентификатор ресурса для всех выделенных больших изображений панели инструментов.  
  
```  
UINT m_uiLargeHotResID;  
```  
  
##  <a name="m_uimenudisabledresid"></a>CMFCToolBarInfo::m_uiMenuDisabledResID  
 Указывает идентификатор ресурса для изображений недоступна команда панели инструментов.  
  
```  
UINT m_uiMenuDisabledResID;  
```  
  
##  <a name="m_uimenuresid"></a>CMFCToolBarInfo::m_uiMenuResID  
 Указывает идентификатор ресурса для всех образов обычное меню элемента панели инструментов.  
  
```  
UINT m_uiMenuResID;  
```  
  
## <a name="see-also"></a>См. также  
 [Диаграмма иерархии](../../mfc/hierarchy-chart.md)   
 [Классы](../../mfc/reference/mfc-classes.md)   
 [Класс CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)
