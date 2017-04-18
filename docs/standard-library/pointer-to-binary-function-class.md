---
title: "Класс pointer_to_binary_function | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::pointer_to_binary_function
- xfunctional/std::pointer_to_binary_function
- pointer_to_binary_function
- std.pointer_to_binary_function
dev_langs:
- C++
helpviewer_keywords:
- pointer_to_binary_function function
- pointer_to_binary_function class
ms.assetid: fb50599f-bcb3-4076-a669-6dcc3eb189a5
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 9a806934810286e22fdea70c2af982de10f48ee5
ms.lasthandoff: 02/24/2017

---
# <a name="pointertobinaryfunction-class"></a>Класс pointer_to_binary_function
Преобразует указатель на бинарную функцию в адаптируемую бинарную функцию.  
  
## <a name="syntax"></a>Синтаксис  
  
```
template <class Arg1, class Arg2, class Result>
class pointer_to_binary_function
    : public binary_function <Arg1, Arg2, Result>
{
public:
    explicit pointer_to_binary_function(
        Result(*pfunc)(Arg1, Arg2));
    Result operator()(Arg1 left, Arg2 right) const;
};
```  
  
#### <a name="parameters"></a>Параметры  
 `pfunc`  
 Бинарная функция для преобразования.  
  
 `left`  
 Левый объект, для которого вызывается функция *\*pfunc*.  
  
 `right`  
 Правый объект, для которого вызывается функция *\*pfunc*.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Шаблон класса хранит копию **pfunc**. Он определяет свою функцию-член `operator()` как возвращающую (\* **pfunc**)(_ *Left*, \_ *Right*).  
  
## <a name="remarks"></a>Примечания  
 Указатель на бинарную функцию является объектом функции и может передаваться в любой алгоритм стандартной библиотеки C++, ожидающий бинарную функцию в качестве параметра, но не может настраиваться. Для применения его с адаптером, например привязки к нему значения или использования его с negator, он должен быть представлен с вложенными типами **first_argument_type**, **second_argument_type** и **result_type**, что делает такую настройку возможной. Преобразование посредством `pointer_to_binary_function` позволяет адаптерам функций работать с указателями бинарных функций.  
  
## <a name="example"></a>Пример  
 Конструктор `pointer_to_binary_function` редко используется напрямую. См. раздел по вспомогательной функции [ptr_fun](../standard-library/functional-functions.md#ptr_fun_function) с примером того, как объявлять и использовать предикат адаптера `pointer_to_binary_function`.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<functional>  
  
 **Пространство имен:** std  
  
## <a name="see-also"></a>См. также  
 [Справочник по стандартной библиотеке C++](../standard-library/cpp-standard-library-reference.md)



