---
title: "Устаревшие интерфейсы API ANSI | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: MFC, ANSI deprecated methods
ms.assetid: c7c5a6fd-95e4-4bee-b3d5-d3826c30947d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3ba520f133ff020b6a1a51e8be7ae75b6fcdb969
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="deprecated-ansi-apis"></a>Нерекомендуемые API ANSI
Библиотека Microsoft Foundation Class (MFC) переносит классы и методы, которые основаны на наборе символов Юникода. Следовательно несколько методов с MFC версии ANSI являются устаревшими. Используйте Юникод версии этих методов в будущие версии приложений.  
  
 Начиная с общих элементах управления Windows версии 6.1, которая включена в состав [!INCLUDE[windowsver](../build/reference/includes/windowsver_md.md)], рекомендуется использовать следующие методы ANSI.  
  
## <a name="cbutton-class"></a>Класс CButton  
  
```  
AFX_ANSI_DEPRECATED BOOL GetIdealSize(LPSIZE psize) const;

 
AFX_ANSI_DEPRECATED BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist) const;

 
AFX_ANSI_DEPRECATED BOOL GetTextMargin(LPRECT pmargin) const;

 
AFX_ANSI_DEPRECATED BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);

AFX_ANSI_DEPRECATED BOOL SetTextMargin(LPRECT pmargin);
```  
  
## <a name="ccomboboxex-class"></a>CComboBoxEx - класс  
  
```  
AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
## <a name="cedit-class"></a>Класс CEdit  
  
```  
AFX_ANSI_DEPRECATED BOOL GetCueBanner(LPWSTR lpszText,
    int cchText) const;

 
AFX_ANSI_DEPRECATED BOOL SetCueBanner(LPCWSTR lpszText,
    BOOL fDrawIfFocused = FALSE);
```  
  
## <a name="clinkctrl-class"></a>Класс классах-оболочках  
 Весь класс является устаревшим.  
  
## <a name="clistctrl-class"></a>CListCtrl - класс  
  
```  
AFX_ANSI_DEPRECATED void CancelEditLabel();

AFX_ANSI_DEPRECATED int EnableGroupView(BOOL fEnable);

AFX_ANSI_DEPRECATED int GetGroupInfo(int iGroupId,
    PLVGROUP pgrp) const;

 
AFX_ANSI_DEPRECATED void GetGroupMetrics(PLVGROUPMETRICS pGroupMetrics) const;

 
AFX_ANSI_DEPRECATED BOOL GetInsertMark(LPLVINSERTMARK lvim) const;

 
AFX_ANSI_DEPRECATED COLORREF GetInsertMarkColor() const;

 
AFX_ANSI_DEPRECATED int GetInsertMarkRect(LPRECT pRect) const;

 
AFX_ANSI_DEPRECATED COLORREF GetOutlineColor() const;

 
AFX_ANSI_DEPRECATED UINT GetSelectedColumn() const;

 
AFX_ANSI_DEPRECATED BOOL GetTileInfo(PLVTILEINFO pti) const;

 
AFX_ANSI_DEPRECATED BOOL GetTileViewInfo(PLVTILEVIEWINFO ptvi) const;

 
AFX_ANSI_DEPRECATED DWORD GetView() const;

 
AFX_ANSI_DEPRECATED BOOL HasGroup(int iGroupId) const;

 
AFX_ANSI_DEPRECATED int InsertGroup(int index,
    PLVGROUP pgrp);

AFX_ANSI_DEPRECATED void InsertGroupSorted(PLVINSERTGROUPSORTED pStructInsert);

AFX_ANSI_DEPRECATED int InsertMarkHitTest(LPPOINT pPoint,
    LPLVINSERTMARK lvim) const;

 
AFX_ANSI_DEPRECATED BOOL IsGroupViewEnabled() const;

 
AFX_ANSI_DEPRECATED void MoveGroup(int iGroupId,
    int toIndex);

AFX_ANSI_DEPRECATED void MoveItemToGroup(int idItemFrom,
    int idGroupTo);

AFX_ANSI_DEPRECATED void RemoveAllGroups();

AFX_ANSI_DEPRECATED int RemoveGroup(int iGroupId);

AFX_ANSI_DEPRECATED BOOL SetGroupInfo(int iGroupId,
    PLVGROUP pGroup);

AFX_ANSI_DEPRECATED void SetGroupMetrics(PLVGROUPMETRICS pGroupMetrics);

AFX_ANSI_DEPRECATED BOOL SetInfoTip(PLVSETINFOTIP plvInfoTip);

AFX_ANSI_DEPRECATED BOOL SetInsertMark(LPLVINSERTMARK lvim);

AFX_ANSI_DEPRECATED COLORREF SetInsertMarkColor(COLORREF color);

AFX_ANSI_DEPRECATED COLORREF SetOutlineColor(COLORREF color);

AFX_ANSI_DEPRECATED void SetSelectedColumn(int iCol);

AFX_ANSI_DEPRECATED BOOL SetTileInfo(PLVTILEINFO pti);

AFX_ANSI_DEPRECATED BOOL SetTileViewInfo(PLVTILEVIEWINFO ptvi);

AFX_ANSI_DEPRECATED DWORD SetView(int iView);

AFX_ANSI_DEPRECATED BOOL SortGroups(PFNLVGROUPCOMPARE _pfnGroupCompare,
    LPVOID _plv);
```  
  
## <a name="crebarctrl-class"></a>CReBarCtrl - класс  
  
```  
AFX_ANSI_DEPRECATED void GetBandMargins(PMARGINS pMargins) const;

 
AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
## <a name="ctoolbarctrl-class"></a>CToolBarCtrl - класс  
  
```  
AFX_ANSI_DEPRECATED void GetMetrics(LPTBMETRICS ptbm) const;

 
AFX_ANSI_DEPRECATED void SetMetrics(LPTBMETRICS ptbm);

AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
## <a name="ctooltipctrl-class"></a>CToolTipCtrl - класс  
  
```  
AFX_ANSI_DEPRECATED HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
## <a name="see-also"></a>См. также  
 [Требования к сборке для использования стандартных элементов управления в Windows Vista](../mfc/build-requirements-for-windows-vista-common-controls.md)

