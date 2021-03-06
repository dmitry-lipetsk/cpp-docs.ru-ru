---
title: "__segmentlimit | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __segmentlimit
dev_langs: C++
helpviewer_keywords:
- __segmentlimit intrinsic
- lsl instruction
ms.assetid: d0bc3630-90cb-4185-8667-686fd41e23d4
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5e7c93923a3fdbb2a5e62163b41c83be30d0a54e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="segmentlimit"></a>__segmentlimit
**Блок, относящийся только к системам Microsoft**  
  
 Приводит к возникновению ошибки `lsl` инструкций (предел сегмента нагрузки).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
unsigned long __segmentlimit(   
   unsigned long a   
);  
```  
  
#### <a name="parameters"></a>Параметры  
 [in] `a`  
 Константа, указывающая область выделения сегментов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Предел сегмента сегмент селектора заданные `a`, при условии, что область выделения является допустимым и видны на текущем уровне разрешений.  
  
## <a name="requirements"></a>Требования  
  
|Встроенная функция|Архитектура|  
|---------------|------------------|  
|`__segmentlimit`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Файл заголовка** \<intrin.h >  
  
## <a name="remarks"></a>Примечания  
 Если не удается получить ограничение размера сегмента, эта инструкция завершается ошибкой. В случае сбоя эта инструкция снимает флаг ZF и возвращаемое значение не определено.  
  
 Эта процедура доступна только как встроенная функция.  
  
## <a name="example"></a>Пример  
  
```  
#include <stdio.h>  
  
#ifdef _M_IX86  
typedef unsigned int READETYPE;  
#else  
typedef unsigned __int64 READETYPE;  
#endif  
  
#define EFLAGS_ZF      0x00000040  
#define KGDT_R3_DATA    0x0020  
#define RPL_MASK        0x3  
  
extern "C"  
{  
unsigned long __segmentlimit (unsigned long);  
READETYPE __readeflags();  
}  
  
#pragma intrinsic(__readeflags)  
#pragma intrinsic(__segmentlimit)  
  
int main(void)  
{  
   const unsigned long initsl = 0xbaadbabe;  
   READETYPE eflags = 0;  
   unsigned long sl = initsl;  
  
   printf("Before: segment limit =0x%x eflags =0x%x\n", sl, eflags);  
   sl = __segmentlimit(KGDT_R3_DATA + RPL_MASK);  
  
   eflags = __readeflags();  
  
   printf("After: segment limit =0x%x eflags =0x%x eflags.zf = %s\n", sl, eflags, (eflags & EFLAGS_ZF) ? "set" : "clear");  
  
   // If ZF is set, the call to lsl succeeded; if ZF is clear, the call failed.  
   printf("%s\n", eflags & EFLAGS_ZF ? "Success!": "Fail!");  
  
   // You can verify the value of sl to make sure that the instruction wrote to it  
   printf("sl was %s\n", (sl == initsl) ? "unchanged" : "changed");  
  
   return 0;  
}  
```  
  
```Output  
Before: segment limit =0xbaadbabe eflags =0x0  
After: segment limit =0xffffffff eflags =0x256 eflags.zf = set  
Success!  
sl was changed  
```  
  
**Завершение блока, относящегося только к системам Майкрософт**  
  
## <a name="see-also"></a>См. также  
 [Встроенные инструкции компилятора](../intrinsics/compiler-intrinsics.md)