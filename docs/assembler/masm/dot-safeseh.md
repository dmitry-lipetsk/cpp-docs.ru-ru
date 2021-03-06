---
title: ". SAFESEH | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- .SAFESEH
dev_langs:
- C++
helpviewer_keywords:
- registering functions as exception handlers
- SAFESEH directive
- .SAFESEH directive
ms.assetid: 6eaac8c4-c46f-47ae-8a66-f5cfeb267e43
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 69212e7a3542a6b6ac88ccbe2ecbbf8894862e65
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="safeseh"></a>.SAFESEH
Регистрирует функцию как структурированного обработчика исключений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
.SAFESEH identifier  
```  
  
## <a name="remarks"></a>Примечания  
 *Идентификатор* должен быть Идентификатором для локально определенная [PROC](../../assembler/masm/proc.md) или [EXTRN](../../assembler/masm/extrn.md) коде Объект [МЕТКА](../../assembler/masm/label-masm.md) не допускается. . Требуется директива SAFESEH [/SAFESEH](../../assembler/masm/ml-and-ml64-command-line-reference.md) ml.exe параметр командной строки.  
  
 Дополнительные сведения об обработчиках структурированных исключений см. в разделе [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md).  
  
 Например регистрация обработчика безопасных исключений, создайте новый файл MASM (как показано ниже), объединить с/SAFESEH и добавить его к связанным объектам.  
  
```  
.386  
.model  flat  
MyHandler   proto  
.safeseh    MyHandler  
end  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по директивам](../../assembler/masm/directives-reference.md)