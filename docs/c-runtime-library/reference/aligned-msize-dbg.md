---
title: "_aligned_msize_dbg | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _aligned_msize_dbg
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
apitype: DLLExport
f1_keywords:
- _aligned_msize_dbg
dev_langs:
- C++
helpviewer_keywords:
- _aligned_msize_dbg
ms.assetid: f1c44af0-3f66-4033-81d1-d71d3afecba0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e0c26a876f6ef4f77d4f9c649a3993fe666cb6f3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="alignedmsizedbg"></a>_aligned_msize_dbg
Возвращает размер блока памяти, выделенного в куче (только в отладочной версии).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
size_t _aligned_msize_dbg(  
   void *memblock,  
   size_t alignment,  
   size_t offset  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 [in] `memblock`  
 Указатель на блок памяти.  
  
 [in] `alignment`  
 Значение выравнивания, которое должно быть целой степенью числа 2.  
  
 [входной] `offset`  
 Смещение в выделение памяти для принудительного выполнения выравнивания.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает размер (в байтах) как целое число без знака.  
  
## <a name="remarks"></a>Примечания  
 Значения `alignment` и `offset` должны совпадать со значениями, которые были переданы функции, выделившей блок.  
  
 `_aligned_msize_dbg` — это отладочная версия функции [_aligned_msize](../../c-runtime-library/reference/aligned-msize.md). Если функция [_DEBUG](../../c-runtime-library/debug.md) не определена, каждый вызов функции `_aligned_msize_dbg` сокращается до вызова функции `_aligned_msize`. Обе функции, `_aligned_msize` и `_aligned_msize_dbg`, вычисляют размер блока памяти в основной куче, но `_aligned_msize_dbg` добавляет функцию отладки: она включает в возвращаемый размер буферы с обеих сторон пользовательской части блока памяти.  
  
 Эта функция проверяет свои параметры. Если `memblock` является указателем NULL или `alignment` не является степенью двойки, функция `_msize` вызывает обработчик недопустимого параметра, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если ошибка обработана, функция задает для параметра `errno` значение `EINVAL` и возвращает -1.  
  
 Сведения о выделении, инициализации и управлении блоками памяти в отладочной версии базовой кучи, см. в статье [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Сведения о типах блоков выделения и способах их использования см. в разделе [Типы блоков в отладочной куче](/visualstudio/debugger/crt-debug-heap-details). Сведения о различиях между вызовом стандартной функции кучи и ее отладочной версии в сборке отладки приложения см. в разделе [Версии отладки функций выделения кучи](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
## <a name="requirements"></a>Требования  
  
|Подпрограмма|Обязательный заголовок|  
|-------------|---------------------|  
|`_aligned_msize_dbg`|\<crtdbg.h>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md) во введении.  
  
## <a name="libraries"></a>Библиотеки  
 Только отладочные версии [библиотек времени выполнения языка C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>См. также  
 [Выделение памяти](../../c-runtime-library/memory-allocation.md)