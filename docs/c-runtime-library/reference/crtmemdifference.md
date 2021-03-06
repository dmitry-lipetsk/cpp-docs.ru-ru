---
title: "_CrtMemDifference | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _CrtMemDifference
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
- _CrtMemDifference
- CrtMemDifference
dev_langs:
- C++
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 68d0aa43167e9c4641851927bd56819e384fed4d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="crtmemdifference"></a>_CrtMemDifference
Сравнивает два состояния памяти и возвращает их различия (только отладочная версия).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
int _CrtMemDifference(   
   _CrtMemState *stateDiff,  
   const _CrtMemState *oldState,  
   const _CrtMemState *newState   
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `stateDiff`  
 Указатель на структуру `_CrtMemState` , которая используется для хранения различий между двумя (возвращенными) состояниями памяти.  
  
 `oldState`  
 Указатель на более раннее состояние памяти (структура`_CrtMemState` ).  
  
 `newState`  
 Указатель на более позднее состояние памяти (структура`_CrtMemState` ).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если состояния памяти значительно отличаются, функция `_CrtMemDifference` возвращает значение TRUE. В противном случае функция возвращает значение FALSE.  
  
## <a name="remarks"></a>Примечания  
 Функция `_CrtMemDifference` сравнивает `oldState` и `newState` и сохраняет их различия в `stateDiff`. Приложение затем использует эти сведения для обнаружения утечек памяти и других проблем с памятью. Если параметр [_DEBUG](../../c-runtime-library/debug.md) не определен, вызовы `_CrtMemDifference` удаляются на этапе предварительной обработки.  
  
 `newState` и `oldState` должны быть допустимыми указателями на структуру `_CrtMemState` , определенную в файле Crtdbg.h, которая должна быть заполнена [_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) перед вызовом `_CrtMemDifference`. Значение`stateDiff` должно быть указателем на ранее выделенный экземпляр структуры `_CrtMemState` . Если параметр `stateDiff`, `newState` или `oldState` имеет значение `NULL`, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, параметру [errno, _doserrno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) присваивается значение `EINVAL`, а функция возвращает значение FALSE.  
  
 `_CrtMemDifference` сравнивает значения полей `_CrtMemState` блоков в `oldState` со значениями полей в `newState` и сохраняет результат в `stateDiff`. Если количество выделенных типов блоков или общее количество выделенных блоков каждого типа различается в двух состояниях памяти, считается, что состояния значительно отличаются. Также в `stateDiff`сохраняются разница между максимальными объемами, выделенными когда-либо за раз для двух состояний, и разница между общим числом выделенных блоков для двух состояний.  
  
 По умолчанию внутренние блоки времени выполнения C (`_CRT_BLOCK`) не учитываются операциями контроля состояния памяти. Функция [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) можно использовать для включения бита `_CRTDBG_CHECK_CRT_DF` флага `_crtDbgFlag` для учета этих блоков в процессе обнаружения утечек памяти и контроля других операций состояния памяти. Освобожденные блоки памяти (`_FREE_BLOCK`) не приводят к возвращению функцией `_CrtMemDifference` значения TRUE.  
  
 Дополнительные сведения о функциях состояния кучи и структуре `_CrtMemState` см. в разделе [Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details). Сведения о выделении, инициализации и управлении блоками памяти в отладочной версии базовой кучи, см. в статье [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Требования  
  
|Подпрограмма|Обязательный заголовок|Необязательный заголовок|  
|-------------|---------------------|---------------------|  
|`_CrtMemDifference`|\<crtdbg.h>|\<errno.h>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md) во введении.  
  
 **Библиотеки:** только отладочные версии [функций библиотеки CRT](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>См. также  
 [Подпрограммы отладки](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)