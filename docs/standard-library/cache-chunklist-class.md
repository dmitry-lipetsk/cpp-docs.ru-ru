---
title: "Класс cache_chunklist | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
dev_langs: C++
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 13d81e3eab6e93a138ac55ca53cbf8e61f195507
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="cachechunklist-class"></a>Класс cache_chunklist
Задает [распределитель блоков](../standard-library/allocators-header.md), который выделяет и освобождает блоки памяти одного размера.  
  
## <a name="syntax"></a>Синтаксис  
  
```
template <std::size_t Sz, std::size_t Nelts = 20>  
class cache_chunklist
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`Sz`|Число элементов в массиве, которые нужно выделить.|  
  
## <a name="remarks"></a>Примечания  
 Этот класс шаблона использует `operator new` для выделения участков необработанной памяти, распределяющей блоки, чтобы выделять хранилище для блока памяти при необходимости; он хранит освобожденные блоки памяти в отдельном списке свободных для каждого участка памяти и применяет `operator delete` для освобождения участка памяти, если ни один из его блоков памяти не используется.  
  
 Каждый блок памяти содержит `Sz` байт свободной памяти и указатель на участок памяти, к которому он принадлежит. Каждый участок памяти содержит `Nelts` блоков памяти, три указателя, int и данные, которые требуются `operator new` и `operator delete`.  
  
### <a name="constructors"></a>Конструкторы  
  
|||  
|-|-|  
|[cache_chunklist](#cache_chunklist)|Создает объект типа `cache_chunklist`.|  
  
### <a name="member-functions"></a>Функции-члены  
  
|||  
|-|-|  
|[allocate](#allocate)|Выделяет блок памяти.|  
|[deallocate](#deallocate)|Освобождает указанное число объектов из памяти, начиная с заданной позиции.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<allocators>  
  
 **Пространство имен:** stdext  
  
##  <a name="allocate"></a>  cache_chunklist::allocate  
 Выделяет блок памяти.  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`count`|Число элементов в массиве, которые нужно выделить.|  
  
### <a name="return-value"></a>Возвращаемое значение  
 Указатель на выделяемый объект.  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="cache_chunklist"></a>  cache_chunklist::cache_chunklist  
 Создает объект типа `cache_chunklist`.  
  
```
cache_chunklist();
```  
  
### <a name="remarks"></a>Примечания  
  
##  <a name="deallocate"></a>  cache_chunklist::deallocate  
 Освобождает указанное число объектов из памяти, начиная с заданной позиции.  
  
```
void deallocate(void* ptr, std::size_t count);
```  
  
### <a name="parameters"></a>Параметры  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`ptr`|Указатель на первый объект, который необходимо освободить из хранилища.|  
|`count`|Количество объектов для освобождения из хранилища.|  
  
### <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [\<allocators>](../standard-library/allocators-header.md)



