---
title: "Класс Platform::OutOfBoundsException | Документы Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::OutOfBoundsException
- VCCORLIB/Platform::OutOfBoundsException::OutOfBoundsException
dev_langs:
- C++
helpviewer_keywords:
- Platform::OutOfBoundsException
ms.assetid: 96f8bf75-1207-4049-964b-7771822cadf3
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6feeaf4947de97ba75c1766b43931da5f6e55742
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="platformoutofboundsexception-class"></a>Класс Platform::OutOfBoundsException
Возникает, когда операция пытается получить доступ к данным за пределами допустимого диапазона.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
public ref class OutOfBoundsException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>Примечания  
 Дополнительные сведения см. в описании класса [COMException](../cppcx/platform-comexception-class.md) .  
  
### <a name="requirements"></a>Требования  
 **Минимальный поддерживаемый клиент:** Windows 8  
  
 **Минимальный поддерживаемый сервер:** Windows Server 2012  
  
 **Пространство имен:** Platform  
  
 **Метаданные:** platform.winmd  
  
## <a name="see-also"></a>См. также  
 [Класс Platform::COMException](../cppcx/platform-comexception-class.md)