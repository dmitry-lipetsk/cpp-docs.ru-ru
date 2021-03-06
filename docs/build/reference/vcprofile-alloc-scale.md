---
title: "VCPROFILE_ALLOC_SCALE | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VCPROFILE_ALLOC_SCALE
dev_langs: C++
helpviewer_keywords: VCPROFILE_ALLOC_SCALE environment variable
ms.assetid: 5cb5ce27-f9b8-489b-b46c-d6e9bcab2d34
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b7b441f41106544633bd691c409fa04c989146f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE
Измените объем памяти, выделенной для хранения данных профиля.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
VCPROFILE_ALLOC_SCALE=scale_value  
```  
  
#### <a name="parameters"></a>Параметры  
 `scale_value`  
 Значение масштаба для объема памяти, необходимой для запуска сценариев тестирования.  Значение по умолчанию — 1.  
  
## <a name="remarks"></a>Примечания  
 В редких случаях не будет достаточно памяти для сбора данных профиля при выполнении сценариев тестирования.  В таких случаях можно увеличить объем памяти с помощью `VCPROFILE_ALLOC_SCALE`.  
  
 Если появляется сообщение об ошибке во время выполнения теста, указывающее, что имеется недостаток памяти, назначьте большее значение для `VCPROFILE_ALLOC_SCALE`, пока не завершить без ошибок нехватки памяти.  
  
## <a name="example"></a>Пример  
  
```  
set VCPROFILE_ALLOC_SCALE=2  
```  
  
## <a name="see-also"></a>См. также  
 [Переменные среды для профильной оптимизации](../../build/reference/environment-variables-for-profile-guided-optimizations.md)