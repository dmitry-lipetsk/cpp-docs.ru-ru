---
title: "Класс CMFCAutoHideButton | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::BringToTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Create
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAlignment
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetAutoHideWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetParentToolBar
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetRect
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::GetTextSize
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::HighlightButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsActive
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHighlighted
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsHorizontal
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsTop
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::IsVisible
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::Move
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDraw
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnDrawBorder
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::OnFillBackground
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ReplacePane
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowAttachedWindow
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::ShowButton
- AFXAUTOHIDEBUTTON/CMFCAutoHideButton::UnSetAutoHideMode
dev_langs: C++
helpviewer_keywords:
- CMFCAutoHideButton [MFC], BringToTop
- CMFCAutoHideButton [MFC], Create
- CMFCAutoHideButton [MFC], GetAlignment
- CMFCAutoHideButton [MFC], GetAutoHideWindow
- CMFCAutoHideButton [MFC], GetParentToolBar
- CMFCAutoHideButton [MFC], GetRect
- CMFCAutoHideButton [MFC], GetSize
- CMFCAutoHideButton [MFC], GetTextSize
- CMFCAutoHideButton [MFC], HighlightButton
- CMFCAutoHideButton [MFC], IsActive
- CMFCAutoHideButton [MFC], IsHighlighted
- CMFCAutoHideButton [MFC], IsHorizontal
- CMFCAutoHideButton [MFC], IsTop
- CMFCAutoHideButton [MFC], IsVisible
- CMFCAutoHideButton [MFC], Move
- CMFCAutoHideButton [MFC], OnDraw
- CMFCAutoHideButton [MFC], OnDrawBorder
- CMFCAutoHideButton [MFC], OnFillBackground
- CMFCAutoHideButton [MFC], ReplacePane
- CMFCAutoHideButton [MFC], ShowAttachedWindow
- CMFCAutoHideButton [MFC], ShowButton
- CMFCAutoHideButton [MFC], UnSetAutoHideMode
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 80f40b7ab03e79d38d36a1b25a4cd973a5077468
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcautohidebutton-class"></a>Класс CMFCAutoHideButton
Кнопка, отображающая или скрывающая [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) , настроенный на скрытие.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>Синтаксис  
  
```  
class CMFCAutoHideButton : public CObject  
```  
  
## <a name="members"></a>Участники  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[CMFCAutoHideButton::BringToTop](#bringtotop)||  
|[CMFCAutoHideButton::Create](#create)|Создает и инициализирует кнопку автоматического скрытия.|  
|[CMFCAutoHideButton::GetAlignment](#getalignment)|Извлекает выравнивание кнопки автоматического скрытия.|  
|[CMFCAutoHideButton::GetAutoHideWindow](#getautohidewindow)|Возвращает [CDockablePane](../../mfc/reference/cdockablepane-class.md) объект, связанный с кнопкой автоматического скрытия.|  
|[CMFCAutoHideButton::GetParentToolBar](#getparenttoolbar)||  
|[CMFCAutoHideButton::GetRect](#getrect)||  
|[CMFCAutoHideButton::GetSize](#getsize)|Определяет размер кнопки автоматического скрытия.|  
|[CMFCAutoHideButton::GetTextSize](#gettextsize)|Возвращает размер текстовой метки для кнопки автоматического скрытия.|  
|[CMFCAutoHideButton::HighlightButton](#highlightbutton)|Выделяет кнопку автоматического скрытия.|  
|[CMFCAutoHideButton::IsActive](#isactive)|Указывает, активна ли кнопка автоматического скрытия.|  
|[CMFCAutoHideButton::IsHighlighted](#ishighlighted)|Возвращает выделенное состояние кнопки автоматического скрытия.|  
|[CMFCAutoHideButton::IsHorizontal](#ishorizontal)|Определяет, является кнопка автоматического скрытия горизонтальной или вертикальной.|  
|[CMFCAutoHideButton::IsTop](#istop)||  
|[CMFCAutoHideButton::IsVisible](#isvisible)|Указывает, является ли кнопка видимой.|  
|[CMFCAutoHideButton::Move](#move)||  
|[CMFCAutoHideButton::OnDraw](#ondraw)|Этот метод вызывается платформой при рисовании кнопки автоматического скрытия.|  
|[CMFCAutoHideButton::OnDrawBorder](#ondrawborder)|Этот метод вызывается платформой при рисовании границ кнопки автоматического скрытия.|  
|[CMFCAutoHideButton::OnFillBackground](#onfillbackground)|Этот метод вызывается платформой при заливке фона кнопки автоматического скрытия.|  
|[CMFCAutoHideButton::ReplacePane](#replacepane)||  
|[CMFCAutoHideButton::ShowAttachedWindow](#showattachedwindow)|Показывает или скрывает связанный [класс CDockablePane](../../mfc/reference/cdockablepane-class.md).|  
|[CMFCAutoHideButton::ShowButton](#showbutton)|Показывает или скрывает кнопку автоматического скрытия.|  
|[CMFCAutoHideButton::UnSetAutoHideMode](#unsetautohidemode)||  
  
## <a name="remarks"></a>Примечания  
 При его создании `CMFCAutoHideButton` объект присоединяется к [класс CDockablePane](../../mfc/reference/cdockablepane-class.md). В результате взаимодействия пользователя с объектом `CMFCAutoHideButton` показывается или скрывается объект `CDockablePane`.  
  
 По умолчанию при включении автоматического скрытия платформа автоматически создает объект класса `CMFCAutoHideButton`. Вместо объекта класса `CMFCAutoHideButton` платформа может создавать элемент настраиваемого класса пользовательского интерфейса. Чтобы указать, какой настраиваемый класс пользовательского интерфейса должна использовать платформа, задайте для статической переменной-члена `CMFCAutoHideBar::m_pAutoHideButtonRTS` значение, равное необходимому настраиваемому классу. Значение этой переменной по умолчанию — `CMFCAutoHideButton`.  
  
## <a name="example"></a>Пример  
 В этом примере демонстрируется создание объекта `CMFCAutoHideButton` и использование различных методов класса `CMFCAutoHideButton`. В этом примере демонстрируется инициализация объекта `CMFCAutoHideButton` с помощью метода `Create`, а также отображение связанного класса `CDockablePane` и кнопки автоматического скрытия.  
  
 [!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/cpp/cmfcautohidebutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Иерархия наследования  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAutoHideButton`  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** afxautohidebutton.h  
  
##  <a name="bringtotop"></a>CMFCAutoHideButton::BringToTop  

  
```  
void BringToTop();
```  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="create"></a>CMFCAutoHideButton::Create  
 Создает и инициализирует кнопку автоматического скрытия.  
  
```  
virtual BOOL Create(
    CMFCAutoHideBar* pParentBar,  
    CDockablePane* pAutoHideWnd,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `pParentBar`  
 Указатель на панель инструментов родительского.  
  
 [in] `pAutoHideWnd`  
 Указатель на [CDockablePane](../../mfc/reference/cdockablepane-class.md) объекта. Эта кнопка автоматического скрытия скрывает и показывает, что `CDockablePane`.  
  
 [in] `dwAlignment`  
 Значение, указывающее выравнивание кнопки с фрейма главного окна.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Имеет ненулевое значение в случае успешного выполнения, иначе — 0.  
  
### <a name="remarks"></a>Примечания  
 При создании `CMFCAutoHideButton` объекта кнопки автоматического скрытия необходимо связать с определенным `CDockablePane`. Пользователь может использовать кнопки автоматического скрытия, чтобы скрыть или отобразить связанный `CDockablePane`.  
  
 Параметр `dwAlignment` указывает, где в приложении находится кнопка автоматического скрытия. Параметру может быть присвоено одно из следующих значений:  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CBRS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
##  <a name="getalignment"></a>CMFCAutoHideButton::GetAlignment  
 Извлекает выравнивание кнопки автоматического скрытия.  
  
```  
DWORD GetAlignment() const;  
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Объект `DWORD` значение, содержащее текущее выравнивание кнопки автоматического скрытия.  
  
### <a name="remarks"></a>Примечания  
 Выравнивание кнопки автоматического скрытия указывает, где находится кнопка в приложении. Он может быть одним из следующих значений:  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CRBS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
##  <a name="getautohidewindow"></a>CMFCAutoHideButton::GetAutoHideWindow  
 Возвращает [CDockablePane](../../mfc/reference/cdockablepane-class.md) объект, связанный с кнопкой автоматического скрытия.  
  
```  
CDockablePane* GetAutoHideWindow() const;  
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Указатель на связанный `CDockablePane` объекта.  
  
### <a name="remarks"></a>Примечания  
 Чтобы связать кнопка автоматического скрытия с `CDockablePane`, передайте `CDockablePane` как параметр [CMFCAutoHideButton::Create](#create) метод.  
  
##  <a name="getparenttoolbar"></a>CMFCAutoHideButton::GetParentToolBar  

  
```  
CMFCAutoHideBar* GetParentToolBar();
```  
  
### <a name="return-value"></a>Возвращаемое значение  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="getrect"></a>CMFCAutoHideButton::GetRect  

  
```  
CRect GetRect() const;  
```  
  
### <a name="return-value"></a>Возвращаемое значение  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="getsize"></a>CMFCAutoHideButton::GetSize  
 Определяет размер кнопки автоматического скрытия.  
  
```  
CSize GetSize() const;  
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Объект `CSize` , содержащий размер кнопки.  
  
### <a name="remarks"></a>Примечания  
 Вычисляемый размер включает размер границы кнопки автоматического скрытия.  
  
##  <a name="gettextsize"></a>CMFCAutoHideButton::GetTextSize  
 Возвращает размер текстовой метки для кнопки автоматического скрытия.  
  
```  
virtual CSize GetTextSize() const;  
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Объект [CSize](../../atl-mfc-shared/reference/csize-class.md) , содержащий размер текста для кнопки автоматического скрытия.  
  
##  <a name="isactive"></a>CMFCAutoHideButton::IsActive  
 Указывает, активна ли кнопка автоматического скрытия.  
  
```  
BOOL IsActive() const;  
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 `TRUE`Если кнопка автоматического скрытия активна; `FALSE` в противном случае.  
  
### <a name="remarks"></a>Примечания  
 Кнопка автоматического скрытия активен, когда связанный [класс CDockablePane](../../mfc/reference/cdockablepane-class.md) окна.  
  
##  <a name="ishorizontal"></a>CMFCAutoHideButton::IsHorizontal  
 Определяет, является кнопка автоматического скрытия горизонтальной или вертикальной.  
  
```  
BOOL IsHorizontal() const;  
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Ненулевое значение, если кнопка горизонтальной; в противном случае — 0.  
  
### <a name="remarks"></a>Примечания  
 Платформа задает ориентацию [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) объекта при его создании.  Ориентацию можно контролировать с помощью `dwAlignment` параметр в [CMFCAutoHideButton::Create](#create) метод.  
  
##  <a name="istop"></a>CMFCAutoHideButton::IsTop  

  
```  
BOOL IsTop() const;  
```  
  
### <a name="return-value"></a>Возвращаемое значение  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="isvisible"></a>CMFCAutoHideButton::IsVisible  
 Указывает, отображается ли кнопка автоматического скрытия.  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 `TRUE`Если отображается кнопка; `FALSE` в противном случае.  
  
##  <a name="ondraw"></a>CMFCAutoHideButton::OnDraw  
 Этот метод вызывается платформой при рисовании кнопки автоматического скрытия.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `pDC`  
 Указатель на контекст устройства.  
  
### <a name="remarks"></a>Примечания  
 Если вы хотите настроить внешний вид кнопок автоматического скрытия в приложении, создайте новый класс, производный от `CMFCAutoHideButton`. В производном классе переопределите этот метод.  
  
##  <a name="ondrawborder"></a>CMFCAutoHideButton::OnDrawBorder  
 Этот метод вызывается платформой при рисовании границ кнопки автоматического скрытия.  
  
```  
virtual void OnDrawBorder(
    CDC* pDC,  
    CRect rectBounds,  
    CRect rectBorderSize);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `pDC`  
 Указатель на контекст устройства.  
  
 [in] `rectBounds`  
 Ограничивающий прямоугольник кнопки автоматического скрытия.  
  
 [in] `rectBorderSize`  
 Толщина границы для каждой стороны кнопки автоматического скрытия.  
  
### <a name="remarks"></a>Примечания  
 Если вы хотите настроить границы каждая кнопка автоматического скрытия в приложении, создайте новый класс, производный от `CMFCAutoHideButton`. В производном классе переопределите этот метод.  
  
##  <a name="onfillbackground"></a>CMFCAutoHideButton::OnFillBackground  
 Этот метод вызывается платформой при заливке фона кнопки автоматического скрытия.  
  
```  
virtual void OnFillBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `pDC`  
 Указатель на контекст устройства.  
  
 [in] `rect`  
 Ограничивающий прямоугольник кнопки автоматического скрытия.  
  
### <a name="remarks"></a>Примечания  
 Если вы хотите настроить фон для кнопки автоматического скрытия в приложении, создайте новый класс, производный от `CMFCAutoHideButton`. В производном классе переопределите этот метод.  
  
##  <a name="showattachedwindow"></a>CMFCAutoHideButton::ShowAttachedWindow  
 Показывает или скрывает связанный [класс CDockablePane](../../mfc/reference/cdockablepane-class.md).  
  
```  
void ShowAttachedWindow(BOOL bShow);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `bShow`  
 Логическое значение, указывающее, отображает ли этот метод прикрепленное `CDockablePane`.  
  
##  <a name="showbutton"></a>CMFCAutoHideButton::ShowButton  
 Показывает или скрывает кнопку автоматического скрытия.  
  
```  
virtual void ShowButton(BOOL bShow);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `bShow`  
 Логическое значение, указывающее, следует ли отображать кнопки автоматического скрытия.  
  
##  <a name="move"></a>CMFCAutoHideButton::Move  

  
```  
void Move(int nOffset);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `nOffset`  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="replacepane"></a>CMFCAutoHideButton::ReplacePane  

  
```  
void ReplacePane(CDockablePane* pNewBar);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `pNewBar`  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="unsetautohidemode"></a>CMFCAutoHideButton::UnSetAutoHideMode  
 Отключение режима автоматического скрытия.  
  
```  
virtual void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup);
```  
  
### <a name="parameters"></a>Параметры  
 [in] `pFirstBarInGroup`  
 Указатель на первую строку в группе.  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="highlightbutton"></a>CMFCAutoHideButton::HighlightButton  
 Выделяет кнопки автоматического скрытия.  
  
```  
virtual void HighlightButton(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Параметры  
 `bHighlight`  
 Указывает новое Автоскрытие состояние кнопки. `TRUE`Указывает, выделяется кнопки, `FALSE` указывает кнопки не выделяется.  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="ishighlighted"></a>CMFCAutoHideButton::IsHighlighted  
 Возвращает состояние выделения кнопки автоматического скрытия.  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Возвращает `TRUE` Если кнопки автоматического скрытия выделенный; в противном случае `FALSE`.  
  
### <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Диаграмма иерархии](../../mfc/hierarchy-chart.md)   
 [Классы](../../mfc/reference/mfc-classes.md)   
 [Класс CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)   
 [Класс CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)
