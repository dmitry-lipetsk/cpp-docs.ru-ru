---
title: "CDBErrorInfo::GetBasicErrorInfo | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- GetBasicErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- GetBasicErrorInfo method
ms.assetid: 263cec53-63f6-48fe-b46e-31d20251863e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0872d80dea10b5171d008394bd2d7cd9dc81e98c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="cdberrorinfogetbasicerrorinfo"></a>CDBErrorInfo::GetBasicErrorInfo
Вызовы [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) получить основные сведения об ошибке, например, код возврата и номер ошибки поставщика.  
  
## <a name="syntax"></a>Синтаксис  
  
```
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,   
  ERRORINFO* pErrorInfo) const throw();  
```  
  
#### <a name="parameters"></a>Параметры  
 В разделе [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) в *справочника программиста OLE DB*.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Стандартный `HRESULT`.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** atldbcli.h  
  
## <a name="see-also"></a>См. также  
 [Класс CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md)