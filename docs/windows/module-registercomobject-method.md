---
title: "Метод Module::RegisterCOMObject | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::RegisterCOMObject
dev_langs: C++
helpviewer_keywords: RegisterCOMObject method
ms.assetid: 59f223dc-03c6-429d-95da-b74b3f73b702
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a2984d5950464385ea47301db356b7364707e667
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="moduleregistercomobject-method"></a>Метод Module::RegisterCOMObject
Регистрирует один или несколько объектов модели COM, чтобы другие приложения могли к ним подключиться.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
WRL_NOTHROW virtual HRESULT RegisterCOMObject(  
   const wchar_t* serverName,  
   IID* clsids,  
   IClassFactory** factories,  
   DWORD* cookies,  
   unsigned int count);  
  
```  
  
#### <a name="parameters"></a>Параметры  
 `serverName`  
 Полное имя сервера.  
  
 `clsids`  
 Массив регистрируемых идентификаторов CLSID.  
  
 `factories`  
 Массив интерфейсов IUnknown объектов класса, чья доступность публикуется.  
  
 `cookies`  
 После завершения операции представляет массив указателей на значения, которые определяют зарегистрированные объекты класса. Эти значения в дальнейшем используются для отмены регистрации.  
  
 `count`  
 Количество идентификаторов CLSID, которые необходимо зарегистрировать.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение S_OK, если операция завершилась успешно; в противном случае — значение HRESULT (например, CO_E_OBJISREG), указывающее причину неудачного завершения операции.  
  
## <a name="remarks"></a>Примечания  
 COM-объекты зарегистрированы с помощью перечислителя CLSCTX_LOCAL_SERVER перечисления CLSCTX.  
  
 Тип подключения к зарегистрированным объектам определяется сочетанием текущего параметра шаблона `comflag` и перечислителя REGCLS_SUSPENDED перечисления REGCLS.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** module.h  
  
 **Пространство имен:** Microsoft::WRL
 
 ## <a name="see-also"></a>См. также
 [Класс Module](../windows/module-class.md)