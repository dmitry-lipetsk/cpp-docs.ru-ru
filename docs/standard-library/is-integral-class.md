---
title: "Класс is_integral | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_integral
dev_langs: C++
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: de9db1c9ebf6e95670a36f44c9233458badd74c9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="isintegral-class"></a>Класс is_integral
Проверяет, является ли тип целочисленным.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template <class Ty>  
struct is_integral;  
```  
  
#### <a name="parameters"></a>Параметры  
 `Ty`  
 Запрашиваемый тип.  
  
## <a name="remarks"></a>Примечания  
 Экземпляр предиката типа имеет значение true, если тип `Ty` является одним из целочисленных типов или формой `cv-qualified` одного из целочисленных типов, , в противном случае — значение false.  
  
 Целочисленный тип — один из типов `bool`, `char`, `unsigned char`, `signed char`, `wchar_t`, `short`, `unsigned short`, `int`, `unsigned int`, `long` и `unsigned long`. Кроме того, целочисленный тип может быть одним из `long long`, `unsigned long long`, `__int64` и `unsigned __int64` при использовании компиляторов, поддерживающих такие типы.  
  
## <a name="example"></a>Пример  
  
```cpp  
// std__type_traits__is_integral.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_integral<trivial> == " << std::boolalpha   
        << std::is_integral<trivial>::value << std::endl;   
    std::cout << "is_integral<int> == " << std::boolalpha   
        << std::is_integral<int>::value << std::endl;   
    std::cout << "is_integral<float> == " << std::boolalpha   
        << std::is_integral<float>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
is_integral<trivial> == false  
is_integral<int> == true  
is_integral<float> == false  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<type_traits>  
  
 **Пространство имен:** std  
  
## <a name="see-also"></a>См. также  
 [<type_traits>](../standard-library/type-traits.md)   
 [Класс is_enum](../standard-library/is-enum-class.md)   
 [Класс is_floating_point](../standard-library/is-floating-point-class.md)
