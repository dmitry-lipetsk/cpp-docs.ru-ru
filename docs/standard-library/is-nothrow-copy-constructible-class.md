---
title: "Класс is_nothrow_copy_constructible | Документы Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_nothrow_copy_constructible
dev_langs: C++
helpviewer_keywords: is_nothrow_copy_constructible
ms.assetid: f13a0bea-63b1-492a-9a45-d445df35c282
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3a39161c0715ef709d9f343188851a0b94abfe40
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="isnothrowcopyconstructible-class"></a>Класс is_nothrow_copy_constructible
Проверяет, обладает ли тип конструктором копии **nothrow**.  
  
## <a name="syntax"></a>Синтаксис  
  
```
template <class Ty>
struct is_nothrow_copy_constructible;
```  
  
#### <a name="parameters"></a>Параметры  
 `Ty`  
 Запрашиваемый тип.  
  
## <a name="remarks"></a>Примечания  
 Экземпляр предиката типа имеет значение true, если тип `Ty` имеет конструктор копии nothrow, в противном случае — значение false.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<type_traits>  
  
 **Пространство имен:** std  
  
## <a name="see-also"></a>См. также  
 [<type_traits>](../standard-library/type-traits.md)





