---
title: "__vmx_vmptrst | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __vmx_vmptrst
dev_langs: C++
helpviewer_keywords:
- __vmx_vmptrst intrinsic
- VMPTRST instruction
ms.assetid: 8dc66e47-03a0-41b0-8e25-c1485f42817a
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 176d8fe48e5719c345ab39135468edf324eeeaa5
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/03/2018
---
# <a name="vmxvmptrst"></a>__vmx_vmptrst
**Блок, относящийся только к системам Microsoft**  
  
 Хранит указатель на текущую структуру управления виртуальной машины (VMCS) по указанному адресу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void __vmx_vmptrst(   
   unsigned __int64 *VmcsPhysicalAddress   
);  
```  
  
#### <a name="parameters"></a>Параметры  
 [in] *`VmcsPhysicalAddress`  
 Адрес, где хранятся указатель текущей VMCS.  
  
## <a name="remarks"></a>Примечания  
 Указатель VMCS — это физический адрес 64-разрядной.  
  
 `__vmx_vmptrst` Функция эквивалентна `VMPTRST` инструкции компьютера. Эта функция поддерживает взаимодействие монитора виртуальной машины узла с гостевой операционной системой и ее приложениями. Для поиска документа «Intel виртуализации технические спецификации для архитектуры IA-32 Intel,» Дополнительные сведения документа номера C97063-002, на [Корпорация Intel](http://go.microsoft.com/fwlink/p/?linkid=127) сайта.  
  
## <a name="requirements"></a>Требования  
  
|Встроенная функция|Архитектура|  
|---------------|------------------|  
|`__vmx_vmptrst`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Файл заголовка** \<intrin.h >  
  
**Завершение блока, относящегося только к системам Майкрософт**  
  
## <a name="see-also"></a>См. также  
 [Встроенные объекты компилятора](../intrinsics/compiler-intrinsics.md)   
 [__vmx_vmptrld](../intrinsics/vmx-vmptrld.md)