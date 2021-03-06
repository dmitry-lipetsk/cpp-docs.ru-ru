---
title: "-ALLOWISOLATION | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /ALLOWISOLATION
dev_langs: C++
helpviewer_keywords:
- -ALLOWISOLATION editbin option
- /ALLOWISOLATION editbin option
- ALLOWISOLATION editbin option
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0ba0295d73e51e28fbdd953d7d9a3a2ae5131c27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="allowisolation"></a>/ALLOWISOLATION
Задает поведение нахождения файлов манифеста.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>Примечания  
 **/ ALLOWISOLATION** вынуждает операционную систему на поиск и загрузку манифеста.  
  
 **/ ALLOWISOLATION** значение по умолчанию.  
  
 **/ALLOWISOLATION:no** указывает, что исполняемые файлы загружаются, как если бы не манифеста и причины [Справочник ЕDITBIN](../../build/reference/editbin-reference.md) для задания `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` бит в необязательном заголовке `DllCharacteristics` поля.  
  
 Если изоляция для исполняемого файла отключена, загрузчик Windows не пытается найти манифест приложения для нового процесса. Новый процесс не имеет контекста активации по умолчанию, даже если отсутствует манифест в исполняемом файле сам или если отсутствует манифест с именем *имя исполняемого файла*. exe.manifest.  
  
## <a name="see-also"></a>См. также  
 [Параметры EDITBIN](../../build/reference/editbin-options.md)   
 [/ ALLOWISOLATION (поиск манифеста)](../../build/reference/allowisolation-manifest-lookup.md)   
 [Ссылки на файлы манифеста](http://msdn.microsoft.com/library/aa375632.aspx)