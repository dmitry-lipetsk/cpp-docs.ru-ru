---
title: "Интерфейс IRegistrar | Документы Microsoft"
ms.custom: 
ms.date: 2/1/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IRegistrar
- ATLIFASE/ATL::IRegistrar
- ATLIFASE/ATL::IRegistrar::ResourceRegisterSz
- ATLIFASE/ATL::IRegistrar::ResourceUnregisterSz
- ATLIFASE/ATL::IRegistrar::FileRegister
- ATLIFASE/ATL::IRegistrar::FileUnregister
- ATLIFASE/ATL::IRegistrar::StringRegister
- ATLIFASE/ATL::IRegistrar::StringUnregister
- ATLIFASE/ATL::IRegistrar::ResourceRegister
- ATLIFASE/ATL::IRegistrar::ResourceUnregister
dev_langs: C++
helpviewer_keywords: Iregistrar Interface
ms.assetid: e88c04b7-0c93-4ae8-aeb9-ecd78f87421e
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c0b304b00b5cc5c613ff7e81818d1c637989e5f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="iregistrar-interface"></a>Интерфейс IRegistrar
Этот интерфейс определяется см и используется внутри функции-члены CAtlModule например [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced).   
  
## <a name="syntax"></a>Синтаксис  
  
```
typedef interface IRegistrar IRegistrar;
```  
## <a name="remarks"></a>Примечания
См. в разделе [с помощью подстановочные параметры (препроцессор регистратора)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) для получения дополнительных сведений.  

## <a name="members"></a>Участники  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[IRegistrar::ResourceRegisterSz](#resourceregistersz)|Регистрирует ресурс. |  
|[IRegistrar::ResourceUnregisterSz](#resourceunregistersz)| Отменяет регистрацию ресурса.|  
|[IRegistrar::FileRegister](#fileregister)|Регистрирует файл.|  
|[IRegistrar::FileUnregister](#fileunregister)|Отменяет регистрацию файла.|  
|[IRegistrar::StringRegister](#stringregister)|Регистрирует строки.|  
|[IRegistrar::StringUnregister](#stringunregister)|Отменяет регистрацию строки|  
|[IRegistrar::ResourceRegister](#resourceregister)|Регистрирует ресурс.|  
|[IRegistrar::ResourceUnregister](#resourceunregister)|Отменяет регистрацию ресурса.| 
  

 
## <a name="requirements"></a>Требования  
 **Заголовок:** atlifase.h  
  
##  <a name="resourceregistersz"></a>IRegistrar::ResourceRegisterSz 
 Регистрирует ресурс.  
  
```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```  
  
 
  
##  <a name="resourceunregistersz"></a>IRegistrar::ResourceUnregisterSz  
 Отменяет регистрацию ресурса.
  
```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```  
  
  
##  <a name="fileregister"></a>IRegistrar::FileRegister  
Регистрирует файл.
  
```
virtual HRESULT STDMETHODCALLTYPE FileRegister( 
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```  
  
  
##  <a name="fileunregister"></a>IRegistrar::FileUnregister  
Отменяет регистрацию файла.

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister( 
    */ _In_z_ LPCOLESTR fileName) = 0;
```  
  
 
##  <a name="stringregister"></a>IRegistrar::StringRegister  
  Регистрирует указанную строку данных.
```
virtual HRESULT STDMETHODCALLTYPE StringRegister( 
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```  
  
##  <a name="stringunregister"></a>IRegistrar::StringUnregister
 Отменяет регистрацию указанного строковые данные.  
  
```
virtualHRESULT STDMETHODCALLTYPE StringUnregister( 
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```  

  
##  <a name="resourceregister"></a>IRegistrar::ResourceRegister  
 Регистрирует ресурс.  
  
```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```  
   
  
##  <a name="resourceunregister"></a>IRegistrar::ResourceUnregister  
 Отменяет регистрацию ресурса.  
  
```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister( 
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0; 
```  
 
## <a name="see-also"></a>См. также  
 [Использование подстановочных параметров (препроцессор регистратора)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)  
 [Общие сведения о классе](../../atl/atl-class-overview.md)   
 [Классы модуля](../../atl/atl-module-classes.md)   
 [Компонент реестра (регистратор)](../../atl/atl-registry-component-registrar.md)  
