---
title: "_cexit _c_exit | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _c_exit
- _cexit
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cexit
- c_exit
- _c_exit
- cexit
dev_langs:
- C++
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 825ed933d5a164fd6a07f13319d30fdf97a928e1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="cexit-cexit"></a>_cexit, _c_exit
Выполняет операции очистки и возвращает значение, не прерывая процесс.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void _cexit( void );  
void _c_exit( void );  
```  
  
## <a name="remarks"></a>Примечания  
 Функция `_cexit` вызывает функции, зарегистрированные `atexit` и `_onexit`, в обратном порядке. Перед возвратом `_cexit` очищает все буферы ввода-вывода и закрывает все открытые потоки. Функция `_c_exit` аналогична функции `_exit`, но возвращается к вызывающему процессу без обработки `atexit` или `_onexit` либо очистки буферов потоков. Поведение `exit`,`_exit`, `_cexit` и `_c_exit` показано в следующей таблице.  
  
|Функция|Поведение|  
|--------------|--------------|  
|`exit`|Выполняет полные процедуры завершения библиотеки C, завершает процесс и завершается с предоставленным кодом состояния.|  
|`_exit`|Выполняет быстрые процедуры завершения библиотеки C, завершает процесс и завершается с предоставленным кодом состояния.|  
|`_cexit`|Выполняет полные процедуры завершения библиотеки C и возвращает управление вызывающему объекту, но не завершает процесс.|  
|`_c_exit`|Выполняет быстрые процедуры завершения библиотеки C и возвращает управление вызывающему объекту, но не завершает процесс.|  
  
 При вызове функции `_cexit` или `_c_exit` деструкторы для любых существующих во время вызова временных или автоматических объектов не вызываются. Автоматический объект — это объект, который определяется в функции, если он не объявлен статическим. Временный объект — это объект, созданный компилятором. Чтобы удалить автоматический объект перед вызовом `_cexit` или `_c_exit`, явным образом вызовите деструктор объекта следующим образом:  
  
```  
myObject.myClass::~myClass( );  
```  
  
## <a name="requirements"></a>Требования  
  
|Подпрограмма|Обязательный заголовок|  
|-------------|---------------------|  
|`_cexit`|\<process.h>|  
|`_c_exit`|\<process.h>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md) во введении.  
  
## <a name="see-also"></a>См. также  
 [Управление процессами и средой](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [Функции _exec, _wexec](../../c-runtime-library/exec-wexec-functions.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [Функции _spawn, _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)