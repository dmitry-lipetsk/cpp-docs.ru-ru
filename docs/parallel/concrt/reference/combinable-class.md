---
title: "Класс combinable | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
dev_langs: C++
helpviewer_keywords: combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 698c59614894314e70019fe2b4621755b4cd3085
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="combinable-class"></a>Класс combinable
Объект `combinable<T>` предназначен для предоставления частной для потока копии данных для выполнения локальных для потока вложенных вычислений без блокировки потока в параллельных алгоритмах. В конце выполнения параллельной операции частные для потока вложенные вычисления можно объединить для получения общего результата. Этот класс можно использовать вместо общей переменной, что может позволить улучшить производительность в случае возникновения большого числа конфликтов доступа к этой общей переменной.  
  
## <a name="syntax"></a>Синтаксис  
  
```
template<typename T>
class combinable;
```  
  
#### <a name="parameters"></a>Параметры  
 `T`  
 Тип данных окончательному результату слияния. Тип должен иметь конструктор копирования и конструктор по умолчанию.  
  
## <a name="members"></a>Участники  
  
### <a name="public-constructors"></a>Открытые конструкторы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[combinable](#ctor)|Перегружен. Создает новое `combinable` объекта.|  
|[~ combinable деструктор](#dtor)|Уничтожает объект `combinable`.|  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[clear](#clear)|Очищает все промежуточные вычислительные результаты из предыдущего использования.|  
|[combine](#combine)|Вычисляет окончательное значение из набора локальных для потока вложенные вычисления, вызывая предоставленный функтор.|  
|[combine_each](#combine_each)|Вычисляет окончательное значение из набора локальных для потока вложенные вычисления, вызывая предоставленный функтор один раз в локальных для потока вложенные вычисления. Окончательный результат накапливаются объектом функции.|  
|[локальные](#local)|Перегружен. Возвращает ссылку на частные для потока вложенные вычисления.|  
  
### <a name="public-operators"></a>Открытые операторы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[оператор=](#operator_eq)|Назначает `combinable` объекта из другого `combinable` объекта.|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения см. в разделе [параллельные контейнеры и объекты](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Иерархия наследования  
 `combinable`  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** ppl.h  
  
 **Пространство имен:** concurrency  
  
##  <a name="clear"></a>Очистить 

 Очищает все промежуточные вычислительные результаты из предыдущего использования.  
  
```
void clear();
```  
  
##  <a name="ctor"></a>combinable 

 Создает новое `combinable` объекта.  
  
```
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```  
  
### <a name="parameters"></a>Параметры  
 `_Function`  
 Тип объекта функтора инициализации.  
  
 `_FnInitialize`  
 Функция, которая будет вызываться для инициализации каждого нового значения частные для потока типа `T`. Он должен поддерживать оператор вызова функции с сигнатурой `T ()`.  
  
 `_Copy`  
 Существующий `combinable` объекта копируются в следующую папку.  
  
### <a name="remarks"></a>Примечания  
 Первый конструктор инициализирует новые элементы с помощью конструктора по умолчанию для типа `T`.  
  
 Второй конструктор инициализирует новые элементы, используя функтор инициализации, предоставленные в качестве `_FnInitialize` параметра.  
  
 Третий конструктор является конструктором копии.  
  
##  <a name="dtor"></a>~ combinable 

 Уничтожает объект `combinable`.  
  
```
~combinable();
```  
  
##  <a name="combine"></a>Объединение 

 Вычисляет окончательное значение из набора локальных для потока вложенные вычисления, вызывая предоставленный функтор.  
  
```
template<typename _Function>
T combine(_Function _FnCombine) const;
```  
  
### <a name="parameters"></a>Параметры  
 `_Function`  
 Тип объекта функции, который будет вызван для объединения двух локальных для потока вложенные вычисления.  
  
 `_FnCombine`  
 Функтор, который используется для объединения вложенные вычисления. Он имеет сигнатуру `T (T, T)` или `T (const T&, const T&)`, и он должен быть ассоциативными и коммуникативными.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Окончательный результат объединения всех частные для потока вложенные вычисления.  
  
##  <a name="combine_each"></a>combine_each 

 Вычисляет окончательное значение из набора локальных для потока вложенные вычисления, вызывая предоставленный функтор один раз в локальных для потока вложенные вычисления. Окончательный результат накапливаются объектом функции.  
  
```
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```  
  
### <a name="parameters"></a>Параметры  
 `_Function`  
 Тип объекта функции, который будет вызван для объединения одного локального потока вложенных вычислений.  
  
 `_FnCombine`  
 Функтор, который используется для объединения одного вложенных вычислений. Он имеет сигнатуру `void (T)` или `void (const T&)`и должен быть ассоциативными и коммуникативными.  
  
##  <a name="local"></a>локальные 

 Возвращает ссылку на частные для потока вложенные вычисления.  
  
```
T& local();

T& local(bool& _Exists);
```  
  
### <a name="parameters"></a>Параметры  
 `_Exists`  
 Ссылка на значение типа boolean. Логическое значение, на который ссылается этот аргумент будет присвоено `true` Если вложенные вычисления уже существовало в данном потоке и значение `false` если бы это был первый вложенных вычислений в этом потоке.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Ссылка на частные для потока вложенные вычисления.  
  
##  <a name="operator_eq"></a>оператор = 

 Назначает `combinable` объекта из другого `combinable` объекта.  
  
```
combinable& operator= (const combinable& _Copy);
```  
  
### <a name="parameters"></a>Параметры  
 `_Copy`  
 Существующий `combinable` объекта копируются в следующую папку.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Ссылку на это `combinable` объекта.  
  
## <a name="see-also"></a>См. также  
 [Пространство имен concurrency](concurrency-namespace.md)
