---
title: "Класс independent_bits_engine | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: random/std::independent_bits_engine
dev_langs: C++
helpviewer_keywords: independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8ec9a4b9beac581df0060f239916c06b8b6191de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="independentbitsengine-class"></a>Класс independent_bits_engine
Создает случайную последовательность чисел с указанным числом разрядов, перемешивая разряды из значений, возвращенных базовым механизмом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template <class Engine, size_t W, class UIntType>  
class independent_bits_engine;  
```  
  
### <a name="parameters"></a>Параметры  
 `Engine`  
 Тип базового механизма.  
  
 `W`  
 **Размер слова**. Размер каждого полученного числа в битах. **Предварительные условия**: `0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `UIntType`  
 Беззнаковый целочисленный тип результата. Возможные типы см. в разделе [\<random>](../standard-library/random.md).  
  
## <a name="members"></a>Участники  
  
||||  
|-|-|-|  
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|  
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|  
  
 Дополнительные сведения о членах механизма см. в разделе [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Примечания  
 Этот класс шаблона описывает *адаптер механизма*, формирующий значения за счет упаковки разрядов из значений, возвращаемых базовым механизмом, что приводит к получению `W`-разрядных значений.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<random>  
  
 **Пространство имен:** std  
  
## <a name="see-also"></a>См. также  
 [\<random>](../standard-library/random.md)

