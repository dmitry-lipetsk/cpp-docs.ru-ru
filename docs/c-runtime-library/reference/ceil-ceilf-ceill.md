---
title: "ceil, ceilf, ceill | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ceilf
- ceil
- ceill
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
- ntdll.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- ceil
- ceilf
- ceill
dev_langs:
- C++
helpviewer_keywords:
- calculating value ceilings
- ceill function
- ceil function
- ceilf function
ms.assetid: f4e5acab-5c8f-4b10-9ae2-9561e6453718
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fcc33dd5fc9c00b537345d613cd47452a425a00e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="ceil-ceilf-ceill"></a>ceil, ceilf, ceill
Рассчитывает верхний предел значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
double ceil(   
   double x   
);  
float ceil(  
   float x  
);  // C++ only  
long double ceil(  
   long double x  
);  // C++ only  
float ceilf(  
   float x  
);  
long double ceill(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `x`  
 Значение с плавающей запятой.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Функции `ceil` возвращают значение с плавающей запятой, которое представляет наименьшее целое число, большее или равное `x`. Ошибка не возвращается.  
  
|Ввод|Исключение SEH|Исключение Matherr|  
|-----------|-------------------|-----------------------|  
|± `QNAN`,`IND`|Нет|`_DOMAIN`|  
  
 Функция `ceil` содержит реализацию, которая использует Streaming SIMD Extensions 2 (SSE2). Сведения о реализации SSE2 и ограничениях на ее использование см. в разделе [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md).  
  
## <a name="remarks"></a>Примечания  
 Так как C++ допускает перегрузку, можно вызывать перегрузки `ceil`. В программе на языке C `ceil` всегда принимает и возвращает значение типа double.  
  
## <a name="requirements"></a>Требования  
  
|Подпрограмма|Обязательный заголовок|  
|-------------|---------------------|  
|`ceil`, `ceilf`, `ceill`|\<math.h>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Пример  
 См. пример для [floor](../../c-runtime-library/reference/floor-floorf-floorl.md).  
  
## <a name="see-also"></a>См. также  
 [Поддержка чисел с плавающей запятой](../../c-runtime-library/floating-point-support.md)   
 [floor, floorf, floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [fmod, fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [round, roundf, roundl](../../c-runtime-library/reference/round-roundf-roundl.md)
