---
title: "_purecall | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _purecall
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
- ntoskrnl.exe
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- purecall
- _purecall
dev_langs:
- C++
helpviewer_keywords:
- _purecall function
- purecall function
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c19324cde907f31ab18a312f3039c2da7a3a40c7
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="purecall"></a>_purecall
Обработчик ошибок вызовов чистой виртуальной функции по умолчанию. При вызове чистой виртуальной функции-члена компилятор создает код для вызова этой функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
extern "C" int __cdecl _purecall();  
```  
  
## <a name="remarks"></a>Примечания  
 Функция `_purecall` является частью реализации компилятора Microsoft Visual C++, использующейся в системах Майкрософт. Эта функция не предназначена для вызова непосредственно из кода и не содержит объявление открытого заголовка. Она описана здесь, так как это общий экспорт библиотеки времени выполнения C.  
  
 Вызов чистой виртуальной функции является ошибкой, так как она не имеет реализации. При вызове чистой виртуальной функции компилятор создает код для вызова этой функции обработчика ошибок `_purecall`. По умолчанию `_purecall` завершает программу. Перед завершением работы функция `_purecall` вызывает функцию `_purecall_handler`, если функция была задана для процесса. Можно установить собственный обработчик ошибок для вызовов чистых виртуальных функций, который будет перехватывать их в целях отладки или ведения отчетности. Чтобы использовать собственный обработчик ошибок, создайте функцию с сигнатурой `_purecall_handler`, а затем с помощью функции [_set_purecall_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md) установите ее в качестве текущего обработчика.  
  
## <a name="requirements"></a>Требования  
 Функция `_purecall` не имеет объявления заголовка. Функция `_purecall_handler` typedef определяется в \<stdlib.h>.  
  
## <a name="see-also"></a>См. также  
 [Алфавитный указатель функций](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_get_purecall_handler, _set_purecall_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)