---
title: "_expand_dbg | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _expand_dbg
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
- expand_dbg
- _expand_dbg
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 41f3d59cec6ec4a064143e0211ebd956f30e16e5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="expanddbg"></a>_expand_dbg
Изменяет размер указанного блока памяти в куче путем его расширения или сжатия (только отладочная версия).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void *_expand_dbg(   
   void *userData,  
   size_t newSize,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `userData`  
 Указатель на ранее выделенный блок памяти.  
  
 `newSize`  
 Запрашиваемый новый размер для блока (в байтах).  
  
 `blockType`  
 Запрашиваемый тип для блока с измененным размером: `_CLIENT_BLOCK` или `_NORMAL_BLOCK`.  
  
 `filename`  
 Указатель на имя исходного файла, который запросил операцию расширения, или `NULL`.  
  
 `linenumber`  
 Номер строки в исходном файле, где была запрошена операция расширения, или `NULL`.  
  
 Параметры `filename` и `linenumber` доступны, только если функция `_expand_dbg` была явно вызвана или была определена константа препроцессора [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 При успешном завершении `_expand_dbg` возвращает указатель на блок памяти, размер которого изменен. Поскольку память не перемещается, адрес совпадает с userData. Если произошла ошибка или блок не удалось расширить до запрашиваемого размера, возвращается значение `NULL`. Если происходит сбой, `errno` содержит сведения из операционной системы о причине сбоя. Дополнительные сведения о функции `errno` см. в разделе [errno, _doserrno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Примечания  
 Функция `_expand_dbg` является отладочной версией функции _[expand](../../c-runtime-library/reference/expand.md). Если [_DEBUG](../../c-runtime-library/debug.md) не определен, каждый вызов функции `_expand_dbg` сокращается до вызова функции `_expand`. Функции `_expand`и `_expand_dbg` изменяют размер блока памяти в базовой куче, но возможность `_expand_dbg` поддерживает несколько возможностей отладки: буферы по обеим сторонам пользовательского участка блока для тестирования на наличие утечек, параметр типа блока для отслеживания определенных типов выделения памяти и сведения `filename`/`linenumber` для определения источника запросов выделения памяти.  
  
 `_expand_dbg` изменяет размер указанного блока памяти, выделяя под него немного больше пространства, чем запрашивается в `newSize`. `newSize` может быть больше или меньше размера первоначально выделенного блока памяти. Дополнительное пространство используется диспетчером кучи отладки, чтобы связать блоки памяти отладки и предоставить приложению сведения о заголовке отладки и буферы перезаписи. Изменение размера достигается либо расширением, либо сжатием исходного блока памяти. `_expand_dbg` не перемещает блок памяти, как это делает функция _[realloc_dbg](../../c-runtime-library/reference/realloc-dbg.md).  
  
 Если `newSize` больше исходного размера блока, блок памяти расширяется. При расширении, если блок памяти нельзя увеличить до запрошенного размера, возвращается значение `NULL`. Если `newSize` меньше исходного размера блока, блок памяти сжимается до достижения нового размера.  
  
 Сведения о выделении, инициализации и управлении блоками памяти в отладочной версии базовой кучи см. в разделе [Сведения о куче отладки CRT](/visualstudio/debugger/crt-debug-heap-details). Сведения о типах блоков выделения и способах их использования см. в разделе [Типы блоков в отладочной куче](/visualstudio/debugger/crt-debug-heap-details). Сведения о различиях между вызовом стандартной функции кучи и ее отладочной версии в сборке отладки приложения см. в разделе [Версии отладки функций выделения кучи](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).  
  
 Эта функция проверяет свои параметры. Если `memblock` представляет собой пустой указатель или его размер больше `_HEAP_MAXREQ`, эта функция вызывает обработчик недопустимого параметра, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, параметр `errno` устанавливается в значение `EINVAL` , и функция возвращает значение `NULL`.  
  
## <a name="requirements"></a>Требования  
  
|Подпрограмма|Обязательный заголовок|  
|-------------|---------------------|  
|`_expand_dbg`|\<crtdbg.h>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Библиотеки  
 Только отладочные версии [библиотек времени выполнения языка C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Пример  
  
```  
// crt_expand_dbg.c  
//  
// This program allocates a block of memory using _malloc_dbg  
// and then calls _msize_dbg to display the size of that block.  
// Next, it uses _expand_dbg to expand the amount of  
// memory used by the buffer and then calls _msize_dbg again to  
// display the new amount of memory allocated to the buffer.  
//  
  
#include <stdio.h>  
#include <malloc.h>  
#include <stdlib.h>  
#include <crtdbg.h>  
  
int main( void )  
{  
   long *buffer;  
   size_t size;  
  
   // Call _malloc_dbg to include the filename and line number  
   // of our allocation request in the header  
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),  
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );  
   if( buffer == NULL )  
      exit( 1 );  
  
   // Get the size of the buffer by calling _msize_dbg  
   size = _msize_dbg( buffer, _NORMAL_BLOCK );  
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );  
  
   // Expand the buffer using _expand_dbg and show the new size  
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),  
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );  
  
   if( buffer == NULL )  
      exit( 1 );  
   size = _msize_dbg( buffer, _NORMAL_BLOCK );  
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",  
           size );  
  
   free( buffer );  
   exit( 0 );  
}  
```  
  
```Output  
Size of block after _malloc_dbg of 40 longs: 160  
Size of block after _expand_dbg of 1 more long: 164  
```  
  
## <a name="comment"></a>Комментарий  
 Вывод этой программы зависит от того, способен ли ваш компьютер расширить все разделы. Если все разделы развернуты, результат отражается в секции вывода.  
  
## <a name="see-also"></a>См. также  
 [Подпрограммы отладки](../../c-runtime-library/debug-routines.md)   
 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)