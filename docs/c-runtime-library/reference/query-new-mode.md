---
title: "_query_new_mode | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _query_new_mode
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- query_new_mode
- _query_new_mode
dev_langs:
- C++
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cbbdec8c5a8cd9af5e6a17518cc40bca455b3f98
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="querynewmode"></a>_query_new_mode
Возвращает целое число, указывающее новый режим обработчика, заданный `_set_new_mode` для `malloc`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      int _query_new_mode(  
   void   
);  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает текущий новый режим обработчика, а именно, 0 или 1, для `malloc`. Возвращаемое значение 1 указывает, что в случае сбоя процесса выделения памяти `malloc` вызывает новую подпрограмму обработчика; возвращаемое значение 0 указывает, что функция не выполняет этого действия.  
  
## <a name="remarks"></a>Примечания  
 Функция C++ `_query_new_mode`возвращает целое число, указывающее новый режим обработчика, заданный функцией C++ [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) для [malloc](../../c-runtime-library/reference/malloc.md). Новый режим обработки указывает, должна ли функция `malloc` при сбое процесса выделения памяти вызывать новую подпрограмму обработчика, заданную функцией [_set_new_handler](../../c-runtime-library/reference/set-new-handler.md). По умолчанию в случае сбоя `malloc` не вызывает новую подпрограмму обработчика. Можно использовать `_set_new_mode` для переопределения этого поведения по умолчанию, чтобы в случае сбоя предоставления памяти функция `malloc` вызывала новую подпрограмму обработчика таким же образом, как это делает оператор **new** при таком же сбое. Дополнительные сведения см. в разделе о [новых и удаленных операторах](../../cpp/new-and-delete-operators.md) справочника по языку C++.  
  
## <a name="requirements"></a>Требования  
  
|Подпрограмма|Обязательный заголовок|  
|-------------|---------------------|  
|`_query_new_mode`|\<new.h>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md) во введении.  
  
## <a name="libraries"></a>Библиотеки  
 Все версии [библиотек времени выполнения языка C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>См. также  
 [Выделение памяти](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)   
 [_query_new_handler](../../c-runtime-library/reference/query-new-handler.md)