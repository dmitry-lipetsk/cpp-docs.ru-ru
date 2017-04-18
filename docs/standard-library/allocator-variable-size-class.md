---
title: "Класс allocator_variable_size | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "allocators.allocator_variable_size"
  - "allocators::allocator_variable_size"
  - "allocators/stdext::allocator_variable_size"
  - "stdext.allocators.allocator_variable_size"
  - "allocator_variable_size"
  - "allocators/stdext::allocators::allocator_variable_size"
  - "stdext::allocators::allocator_variable_size"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocator_variable_size - класс"
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# Класс allocator_variable_size
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Описывает объект, который управляет выделение и освобождение памяти для объектов типа `Type` использование кэша управлянная длина типа [cache\_freelist](../standard-library/cache-freelist-class.md) с [max\_variable\_size](../standard-library/max-variable-size-class.md).  
  
## Синтаксис  
  
```  
template <class Type>  
    class allocator_variable_size;  
```  
  
#### Параметры  
  
|Параметр|Описание|  
|--------------|--------------|  
|`Type`|Тип элементов, выбранных распределителем.|  
  
## Заметки  
 Макрос [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) передает этот класс в качестве параметра `name` в следующую инструкцию: `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`  
  
## Требования  
 **Заголовок:**\<allocators\>  
  
 **Пространство имен:** stdext  
  
## См. также  
 [\<allocators\>](../standard-library/allocators-header.md)