---
title: "Структура hash (Стандартная библиотека C++) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: thread/std::hash
dev_langs: C++
ms.assetid: 4a8bf5bc-4334-4070-936b-98585f8a073b
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7625249f9d602d9c23daa36d067059bbe66fba34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="hash-structure-c-standard-library"></a>Структура hash (Стандартная библиотека C++)
Определяет функцию-член, возвращающую значение, которое уникально определяется с помощью `Val`. Функция-член определяет функцию [hash](../standard-library/hash-class.md), которую можно использовать для сопоставления значений типа `thread::id` с распределением значений индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template <>  
struct hash<thread::id> :   
    public unary_function<thread::id, size_t>  
{  
    size_t operator()(thread::id Val) const;

 
};  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<поток >  
  
 **Пространство имен:** std  
  
## <a name="see-also"></a>См. также  
 [Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)   
 [\<thread>](../standard-library/thread.md)   
 [Структура unary_function](../standard-library/unary-function-struct.md)
