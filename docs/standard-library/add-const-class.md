---
title: "Класс add_const | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::add_const
dev_langs: C++
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 23032c0906e789dcf24c8e81b3988f6bbe1c7392
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="addconst-class"></a>Класс add_const
Создает тип const из типа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template <class Ty>  
struct add_const;
```  
  
#### <a name="parameters"></a>Параметры  
 `Ty`  
 Тип для изменения.  
  
## <a name="remarks"></a>Примечания  
 Экземпляр типа modifier содержит модифицированный тип, который является `Ty`, если `Ty` является ссылкой, функцией или типом с квалификатором const; в противном случае — `const Ty`.  
  
## <a name="example"></a>Пример  
  
```cpp  
// std__type_traits__add_const.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
int main()   
{   
    std::add_const<int>::type *p = (const int *)0;   
  
    p = p;  // to quiet "unused" warning   
    std::cout << "add_const<int> == "   
        << typeid(*p).name() << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
add_const<int> == int  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<type_traits>  
  
 **Пространство имен:** std  
  
## <a name="see-also"></a>См. также  
 [<type_traits>](../standard-library/type-traits.md)   
 [Класс remove_const](../standard-library/remove-const-class.md)
