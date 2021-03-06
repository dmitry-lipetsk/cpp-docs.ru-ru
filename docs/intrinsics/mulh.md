---
title: "__mulh | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __mulh
dev_langs: C++
helpviewer_keywords: __mulh intrinsic
ms.assetid: cd2ab093-9ef6-404d-ac34-0bee033882f3
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2e8d2b8f9b6a697bedeccef46c37a27bfd3559c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="mulh"></a>__mulh
**Блок, относящийся только к системам Microsoft**  
  
 Возвращает старшие 64 разряда произведения двух 64-разрядных целых чисел со знаком.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
__int64 __mulh(   
   __int64 a,   
   __int64 b   
);  
```  
  
#### <a name="parameters"></a>Параметры  
 [in] `a`  
 Первое число для умножения.  
  
 [in] `b`  
 Второе число для умножения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Старшие 64 разряда 128-разрядного результата умножения.  
  
## <a name="requirements"></a>Требования  
  
|Встроенная функция|Архитектура|  
|---------------|------------------|  
|`__mulh`|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Файл заголовка** \<intrin.h >  
  
## <a name="remarks"></a>Примечания  
 Эта процедура доступна только как встроенная функция.  
  
## <a name="example"></a>Пример  
  
```  
// mulh.cpp  
// processor: x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic (__mulh)  
  
int main()  
{  
    __int64 a = 0x0fffffffffffffffI64;  
    __int64 b = 0xf0000000I64;  
  
    __int64 result = __mulh(a, b); // the high 64 bits  
    __int64 result2 = a * b; // the low 64 bits  
  
    printf_s(" %#I64x * %#I64x = %#I64x%I64x\n",  
             a, b, result, result2);  
}  
```  
  
```Output  
0xfffffffffffffff * 0xf0000000 = 0xeffffffffffffff10000000  
```  
  
**Завершение блока, относящегося только к системам Майкрософт**  
  
## <a name="see-also"></a>См. также  
 [Встроенные инструкции компилятора](../intrinsics/compiler-intrinsics.md)