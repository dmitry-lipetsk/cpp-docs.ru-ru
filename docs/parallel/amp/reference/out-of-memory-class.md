---
title: "Класс out_of_memory | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
dev_langs: C++
helpviewer_keywords: out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6eb7b4e46d0d91779bf7c4c9047cad2f49100cd1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="outofmemory-class"></a>out_of_memory - класс
Исключение, возникающее при сбое метода из-за недостатка памяти системы или устройства.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
class out_of_memory : public runtime_exception;  
```  
  
## <a name="members"></a>Участники  
  
### <a name="public-constructors"></a>Открытые конструкторы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[out_of_memory конструктор](#ctor)|Инициализирует новый экземпляр класса `out_of_memory`.|  
  
## <a name="inheritance-hierarchy"></a>Иерархия наследования  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** amprt.h  
  
 **Пространство имен** : Concurrency  
## <a name="ctor"></a>out_of_memory 

 Инициализирует новый экземпляр класса.  
  
### <a name="syntax"></a>Синтаксис  
  
```  
explicit out_of_memory(  
    const char * _Message ) throw();  
  
out_of_memory () throw();  
```  
  
### <a name="parameters"></a>Параметры  
 `_Message`  
 Описание ошибки.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Новый экземпляр класса `out_of_memory`.  
  
  
## <a name="see-also"></a>См. также  
 [Пространство имен Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
