---
title: "Класс CMFCRibbonLinkCtrl | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CopyFrom
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetCompactSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetRegularSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetToolTipText
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::IsDrawTooltipImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDraw
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDrawMenuImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnMouseMove
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnSetIcon
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OpenLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::SetLink
dev_langs: C++
helpviewer_keywords:
- CMFCRibbonLinkCtrl [MFC], CMFCRibbonLinkCtrl
- CMFCRibbonLinkCtrl [MFC], CopyFrom
- CMFCRibbonLinkCtrl [MFC], GetCompactSize
- CMFCRibbonLinkCtrl [MFC], GetLink
- CMFCRibbonLinkCtrl [MFC], GetRegularSize
- CMFCRibbonLinkCtrl [MFC], GetToolTipText
- CMFCRibbonLinkCtrl [MFC], IsDrawTooltipImage
- CMFCRibbonLinkCtrl [MFC], OnDraw
- CMFCRibbonLinkCtrl [MFC], OnDrawMenuImage
- CMFCRibbonLinkCtrl [MFC], OnMouseMove
- CMFCRibbonLinkCtrl [MFC], OnSetIcon
- CMFCRibbonLinkCtrl [MFC], OpenLink
- CMFCRibbonLinkCtrl [MFC], SetLink
ms.assetid: 77ae1941-e0ab-4a9d-911e-1752d34c079b
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3007c98629b83e6302556582220684075d5049b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcribbonlinkctrl-class"></a>Класс CMFCRibbonLinkCtrl
Реализует гиперссылку, которая расположена на ленте. Гиперссылка при щелчке открывает веб-страницу.  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
class CMFCRibbonLinkCtrl : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Участники  
  
### <a name="public-constructors"></a>Открытые конструкторы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|Создает и инициализирует объект `CMFCRibbonLinkCtrl`.|  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|(Переопределяет `CMFCRibbonButton::CopyFrom`.)|  
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(Переопределяет [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|  
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|Возвращает значение гиперссылки.|  
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(Переопределяет [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|  
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(Переопределяет [CMFCRibbonButton::GetToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext).)|  
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|(Переопределяет `CMFCRibbonButton::IsDrawTooltipImage`.)|  
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(Переопределяет [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|  
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(Переопределяет [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|  
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|(Переопределяет `CMFCRibbonButton::OnMouseMove`.)|  
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||  
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|Открывает веб-страницу, указанную в гиперссылке.|  
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|Задает значение гиперссылки.|  
  
## <a name="remarks"></a>Примечания  
 После создания гиперссылки добавьте его на панель, вызвав [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
## <a name="inheritance-hierarchy"></a>Иерархия наследования  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md) [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** afxRibbonLinkCtrl.h  
  
##  <a name="cmfcribbonlinkctrl"></a>CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl  
 Создает и инициализирует [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md) объекта.  
  
```  
CMFCRibbonLinkCtrl(
    UINT nID,  
    LPCTSTR lpszText,  
    LPCTSTR lpszLink);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `nID`  
 Указывает идентификатор команды команда, выполняемая при нажатии элемента управления ссылки.  
  
 [in] `lpszText`  
 Задает метку для отображения элемента управления ссылки.  
  
 [in] `lpszLink`  
 Определяет гиперссылку, связанную с элементом управления link.  
  
### <a name="example"></a>Пример  
 Ниже приведен пример, как использовать конструктор `CMFCRibbonLinkCtrl` класса. Этот фрагмент кода является частью [мини-приложения ленты образец](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]  
  
##  <a name="copyfrom"></a>CMFCRibbonLinkCtrl::CopyFrom  

  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `src`  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="getcompactsize"></a>CMFCRibbonLinkCtrl::GetCompactSize  

  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `pDC`  
  
### <a name="return-value"></a>Возвращаемое значение  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="getlink"></a>CMFCRibbonLinkCtrl::GetLink  
 Возвращает значение гиперссылки.  
  
```  
LPCTSTR GetLink() const;  
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Текущее значение гиперссылки.  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="getregularsize"></a>CMFCRibbonLinkCtrl::GetRegularSize  

  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `pDC`  
  
### <a name="return-value"></a>Возвращаемое значение  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="gettooltiptext"></a>CMFCRibbonLinkCtrl::GetToolTipText  

  
```  
virtual CString GetToolTipText() const;  
```  
  
### <a name="return-value"></a>Возвращаемое значение  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="ondrawmenuimage"></a>CMFCRibbonLinkCtrl::OnDrawMenuImage  

  
```  
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `CDC*`  
 [in] `CRect`  
  
### <a name="return-value"></a>Возвращаемое значение  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="isdrawtooltipimage"></a>CMFCRibbonLinkCtrl::IsDrawTooltipImage  

  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>Возвращаемое значение  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="ondraw"></a>CMFCRibbonLinkCtrl::OnDraw  

  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `pDC`  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="onmousemove"></a>CMFCRibbonLinkCtrl::OnMouseMove  

  
```  
virtual void OnMouseMove(CPoint point);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `point`  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="onseticon"></a>CMFCRibbonLinkCtrl::OnSetIcon  

  
```  
virtual void OnSetIcon();
```  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="openlink"></a>CMFCRibbonLinkCtrl::OpenLink  
 Открывает веб-страницу, указанную в гиперссылке.  
  
```  
BOOL OpenLink();
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 `TRUE`Если связанный веб-страницы был открыт успешно. в противном случае `FALSE`.  
  
### <a name="remarks"></a>Примечания  
 Открытие веб-страницы, с помощью гиперссылки, связанной с `CMFCRibbonLinkCtrl` объекта.  
  
##  <a name="setlink"></a>CMFCRibbonLinkCtrl::SetLink  
 Задает значение гиперссылки.  
  
```  
void SetLink(LPCTSTR lpszLink);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `lpszLink`  
 Задает текст гиперссылки.  
  
## <a name="see-also"></a>См. также  
 [Диаграмма иерархии](../../mfc/hierarchy-chart.md)   
 [Классы](../../mfc/reference/mfc-classes.md)   
 [Класс CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)
