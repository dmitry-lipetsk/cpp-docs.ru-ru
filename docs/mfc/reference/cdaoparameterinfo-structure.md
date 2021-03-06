---
title: "Структура CDaoParameterInfo | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDaoParameterInfo
dev_langs: C++
helpviewer_keywords:
- CDaoParameterInfo structure [MFC]
- DAO (Data Access Objects), Parameters collection
ms.assetid: 45fd53cd-cb84-4e12-b48d-7f2979f898ad
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3aabdb1dd59e1039f81d2ffe75c0d9e0770e43db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="cdaoparameterinfo-structure"></a>Структура CDaoParameterInfo
`CDaoParameterInfo` Структура содержит сведения об объекте параметров, определенных для объекты доступа к данным (DAO).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
struct CDaoParameterInfo  
{  
    CString m_strName;       // Primary  
    short m_nType;           // Primary  
    ColeVariant m_varValue;  // Secondary  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 `m_strName`  
 Однозначно называет объект параметра. Дополнительные сведения см. в разделе «Имя свойства» в справке DAO.  
  
 `m_nType`  
 Значение, указывающее тип данных объекта parameter. Список возможных значений см. в разделе `m_nType` членом [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) структуры. Дополнительные сведения см. в разделе «Тип свойства» в справке DAO.  
  
 *m_varValue*  
 Значение параметра, хранящиеся в [COleVariant](../../mfc/reference/colevariant-class.md) объекта.  
  
## <a name="remarks"></a>Примечания  
 Ссылки на первичной и вторичной выше указывают, как возвращаются сведения по [GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) функции-члена в классе `CDaoQueryDef`.  
  
 MFC не содержит объектов DAO параметра в классе. MFC базовых объектов DAO querydef `CDaoQueryDef` объекты хранят параметры в коллекциях параметров. Для доступа к объектам параметра в [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) , вызовите объекта querydef `GetParameterInfo` функции-члена имя определенного параметра или индекса в коллекции параметров. Можно использовать [CDaoQueryDef::GetParameterCount](../../mfc/reference/cdaoquerydef-class.md#getparametercount) функции-члена в сочетании с `GetParameterInfo` выполнить цикл по коллекции параметров.  
  
 Сведений, получаемых методом [CDaoQueryDef::GetParameterInfo](../../mfc/reference/cdaoquerydef-class.md#getparameterinfo) функции-члена хранится в `CDaoParameterInfo` структуры. Вызовите `GetParameterInfo` для объекта querydef, в которых коллекции параметров хранится объект параметра.  
  
> [!NOTE]
>  Если вы хотите получить или задать значение параметра, используйте [GetParamValue](../../mfc/reference/cdaorecordset-class.md#getparamvalue) и [SetParamValue](../../mfc/reference/cdaorecordset-class.md#setparamvalue) функции-члены класса `CDaoRecordset`.  
  
 `CDaoParameterInfo`также определяет `Dump` функции-члена в отладочных построений. Можно использовать `Dump` для помещения в дамп содержимого `CDaoParameterInfo` объекта.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** afxdao.h  
  
## <a name="see-also"></a>См. также  
 [Структуры, стили, обратные вызовы и схемы сообщений](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [Класс CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)
