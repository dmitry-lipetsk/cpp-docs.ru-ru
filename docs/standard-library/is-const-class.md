---
title: "Класс is_const | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_const
dev_langs: C++
helpviewer_keywords:
- is_const class
- is_const
ms.assetid: 55b8e887-9c3f-4a1d-823a-4a257337b205
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ef70926d3896bb67cf173bcce38628901a759d83
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="isconst-class"></a>Класс is_const
Проверяет, является ли тип константой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template <class Ty>  
struct is_const;
```  
  
#### <a name="parameters"></a>Параметры  
 `Ty`  
 Запрашиваемый тип.  
  
## <a name="remarks"></a>Примечания  
 Экземпляр предиката типа содержит значение true, если `Ty` является `const-qualified`.  
  
## <a name="example"></a>Пример  
  
```cpp  
// std__type_traits__is_const.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   

struct trivial
{
    int val;
};

int main()
{
    std::cout << "is_const<trivial> == " << std::boolalpha
        << std::is_const<trivial>::value << std::endl;
    std::cout << "is_const<const trivial> == " << std::boolalpha
        << std::is_const<const trivial>::value << std::endl;
    std::cout << "is_const<int> == " << std::boolalpha
        << std::is_const<int>::value << std::endl;
    std::cout << "is_const<const int> == " << std::boolalpha
        << std::is_const<const int>::value << std::endl;

    return (0);
}

```  
  
```Output  
is_const<trivial> == false  
is_const<const trivial> == true  
is_const<int> == false  
is_const<const int> == true  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<type_traits>  
  
 **Пространство имен:** std  
  
## <a name="see-also"></a>См. также  
 [<type_traits>](../standard-library/type-traits.md)   
 Класс [is_volatile](../standard-library/is-volatile-class.md)
