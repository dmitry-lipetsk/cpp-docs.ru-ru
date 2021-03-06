---
title: "Константы поля st_mode структуры _stat | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- S_IFCHR
- S_IFDIR
- _S_IWRITE
- S_IFMT
- _S_IFDIR
- _S_IREAD
- S_IEXEC
- _S_IEXEC
- _S_IFMT
- S_IWRITE
- S_IFREG
- S_IREAD
- _S_IFCHR
- _S_IFREG
dev_langs: C++
helpviewer_keywords:
- S_IFDIR constant
- stat structure
- S_IWRITE constant
- S_IEXEC constant
- _S_IFREG constant
- S_IREAD constant
- stat structure, constants
- _S_IFMT constant
- st_mode field constants
- S_IFMT constant
- _S_IEXEC constant
- _S_IWRITE constant
- _S_IFDIR constant
- S_IFREG constant
- S_IFCHR constant
- _S_IREAD constant
- _S_IFCHR constant
ms.assetid: fd462004-7563-4766-8443-30b0a86174b6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d5502a563c674818626627a5161e7051682f258
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="stat-structure-stmode-field-constants"></a>Константы поля st_mode структуры _stat
## <a name="syntax"></a>Синтаксис  
  
```  
  
#include <sys/stat.h>  
  
```  
  
## <a name="remarks"></a>Примечания  
 Эти константы помогают указать тип файла в поле **st_mode** структуры [_stat](../c-runtime-library/standard-types.md).  
  
 Ниже перечислены константы битовой маски.  
  
|Константа|Значение|  
|--------------|-------------|  
|`_S_IFMT`|Маска типа файла|  
|`_S_IFDIR`|Каталог|  
|`_S_IFCHR`|Специальный символ (если задана, указывает устройство)|  
|`_S_IFREG`|Регулярное|  
|`_S_IREAD`|Разрешение на чтение, владелец|  
|`_S_IWRITE`|Разрешение на запись, владелец|  
|`_S_IEXEC`|Разрешение на выполнение или поиск, владелец|  
  
## <a name="see-also"></a>См. также  
 [Функции _stat, _wstat](../c-runtime-library/reference/stat-functions.md)   
 [_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [Стандартные типы](../c-runtime-library/standard-types.md)   
 [Глобальные константы](../c-runtime-library/global-constants.md)