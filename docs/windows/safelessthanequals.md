---
title: "SafeLessThanEquals | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: SafeLessThanEquals
dev_langs: C++
helpviewer_keywords: SafeLessThanEquals function
ms.assetid: cbd70526-faf2-4fbc-96a0-b61e8cf5f04a
caps.latest.revision: "6"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cb5765d9ea353558d7a297fb7867c6889be928ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="safelessthanequals"></a>SafeLessThanEquals
Сравнивает два числа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template <typename T, typename U>  
inline bool SafeLessThanEquals (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### <a name="parameters"></a>Параметры  
 [in] `t`  
 Первое число для сравнения. Это должен быть типа T.  
  
 [in] `u`  
 Второе число для сравнения. Это должен быть типа u.  
  
## <a name="return-value"></a>Возвращаемое значение  
 `true`Если `t` меньше или равно `u`; в противном случае `false`.  
  
## <a name="remarks"></a>Примечания  
 `SafeLessThanEquals`оператор сравнения, регулярные расширяет путем сравнения двух различных типов чисел.  
  
 Этот метод является частью [библиотека SafeInt](../windows/safeint-library.md) и предназначена для операции сравнения одного без создания экземпляра [класс SafeInt](../windows/safeint-class.md).  
  
> [!NOTE]
>  Этот метод использовать только в том случае, когда один математической операции должны быть защищены. При наличии нескольких операций, следует использовать `SafeInt` класса вместо вызова автономного отдельных функций.  
  
 Дополнительные сведения о типах шаблонов T и U см. в разделе [функции SafeInt](../windows/safeint-functions.md).  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** safeint.h  
  
 **Пространство имен:** Microsoft::Utilities  
  
## <a name="see-also"></a>См. также  
 [Функции SafeInt](../windows/safeint-functions.md)   
 [Библиотека SafeInt](../windows/safeint-library.md)   
 [SafeInt-класс](../windows/safeint-class.md)   
 [SafeGreaterThan](../windows/safegreaterthan.md)   
 [SafeLessThan](../windows/safelessthan.md)   
 [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)