---
title: "Класс Call | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- call
- AGENTS/concurrency::call
- AGENTS/concurrency::call::call
- AGENTS/concurrency::call::process_input_messages
- AGENTS/concurrency::call::process_message
- AGENTS/concurrency::call::propagate_message
- AGENTS/concurrency::call::send_message
- AGENTS/concurrency::call::supports_anonymous_source
dev_langs: C++
helpviewer_keywords: call class
ms.assetid: 1521970a-1e9c-4b0c-a681-d18e40976f49
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2d575aaa01a3668925c6a81eda7d8d99cc591180
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="call-class"></a>Класс call
Блок обмена сообщениями `call` — это упорядоченный блок `target_block` с несколькими источниками, который вызывает заданную функцию при получении сообщения.  
  
## <a name="syntax"></a>Синтаксис  
  
```
template<class T, class _FunctorType = std::function<void(T const&)>>
class call : public target_block<multi_link_registry<ISource<T>>>;
```  
  
#### <a name="parameters"></a>Параметры  
 `T`  
 Тип полезных данных сообщения, распространяются в этот блок.  
  
 `_FunctorType`  
 Подпись функции, которые может принимать этот блок.  
  
## <a name="members"></a>Участники  
  
### <a name="public-constructors"></a>Открытые конструкторы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[вызов](#ctor)|Перегружен. Создает `call` блока обмена сообщениями.|  
|[~ вызова деструктора](#dtor)|Уничтожает `call` блока обмена сообщениями.|  
  
### <a name="protected-methods"></a>Защищенные методы  
  
|Имя|Описание:|  
|----------|-----------------|  
|[process_input_messages](#process_input_messages)|Выполняет функцию вызвать для входящих сообщений.|  
|[process_message](#process_message)|Обрабатывает сообщение, которое было принято данным `call` блока обмена сообщениями.|  
|[propagate_message](#propagate_message)|Асинхронно передает сообщение от `ISource` блока к этому `call` блока обмена сообщениями. Он вызывается по `propagate` метод при вызове исходного блока.|  
|[send_message](#send_message)|Синхронно передает сообщение от `ISource` блока к этому `call` блока обмена сообщениями. Он вызывается по `send` метод при вызове исходного блока.|  
|[supports_anonymous_source](#supports_anonymous_source)|Переопределяет метод `supports_anonymous_source`, чтобы указать, что данный блок может принимать сообщения, предоставляемые ему несвязанным источником. (Переопределяет [ITarget::supports_anonymous_source](itarget-class.md#supports_anonymous_source).)|  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения см. в разделе [асинхронные блоки сообщений](../../../parallel/concrt/asynchronous-message-blocks.md).  
  
## <a name="inheritance-hierarchy"></a>Иерархия наследования  
 [ITarget](itarget-class.md)  
  
 [target_block](target-block-class.md)  
  
 `call`  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** agents.h  
  
 **Пространство имен:** concurrency  
  
##  <a name="ctor"></a>вызов 

 Создает `call` блока обмена сообщениями.  
  
```
call(
    _Call_method const& _Func);

call(
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func);

call(
    Scheduler& _PScheduler,
    _Call_method const& _Func,
    filter_method const& _Filter);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func);

call(
    ScheduleGroup& _PScheduleGroup,
    _Call_method const& _Func,
    filter_method const& _Filter);
```  
  
### <a name="parameters"></a>Параметры  
 `_Func`  
 Функция, которая будет вызываться для каждого принятого сообщения.  
  
 `_Filter`  
 Функции фильтров, который определяет, следует ли принять предложенное сообщения.  
  
 `_PScheduler`  
 `Scheduler` Объекта, в течение которого задача распространения для `call` запланирована блока обмена сообщениями.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Объекта, в течение которого задача распространения для `call` запланирована блока обмена сообщениями. Используемый объект `Scheduler` подразумевается группой расписаний.  
  
### <a name="remarks"></a>Примечания  
 Среда выполнения использует планировщик по умолчанию, если вы не указали параметры `_PScheduler` или `_PScheduleGroup` .  
  
 Тип `_Call_method` является функтор с сигнатурой `void (T const &)` которого вызывается этим `call` блока обмена сообщениями для обработки сообщения.  
  
 Тип `filter_method` является функтор с сигнатурой `bool (T const &)` которого вызывается этим `call` блока обмена сообщениями, чтобы определить ли он должен принять предложенное сообщение.  
  
##  <a name="dtor"></a>~ вызова 

 Уничтожает `call` блока обмена сообщениями.  
  
```
~call();
```  
  
##  <a name="process_input_messages"></a>process_input_messages 

 Выполняет функцию вызвать для входящих сообщений.  
  
```
virtual void process_input_messages(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Параметры  
 `_PMessage`  
  
##  <a name="process_message"></a>process_message 

 Обрабатывает сообщение, которое было принято данным `call` блока обмена сообщениями.  
  
```
virtual void process_message(_Inout_ message<T>* _PMessage);
```  
  
### <a name="parameters"></a>Параметры  
 `_PMessage`  
 Указатель на сообщение, которое будет обрабатываться.  
  
##  <a name="propagate_message"></a>propagate_message 

 Асинхронно передает сообщение от `ISource` блока к этому `call` блока обмена сообщениями. Он вызывается по `propagate` метод при вызове исходного блока.  
  
```
virtual message_status propagate_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>Параметры  
 `_PMessage`  
 Указатель на объект `message`.  
  
 `_PSource`  
 Указатель на исходный блок, предлагающий сообщение.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Объект [message_status](concurrency-namespace-enums.md) , указывающее, что целевой объект решил сделать с сообщением.  
  
##  <a name="send_message"></a>send_message 

 Синхронно передает сообщение от `ISource` блока к этому `call` блока обмена сообщениями. Он вызывается по `send` метод при вызове исходного блока.  
  
```
virtual message_status send_message(
    _Inout_ message<T>* _PMessage,
    _Inout_ ISource<T>* _PSource);
```  
  
### <a name="parameters"></a>Параметры  
 `_PMessage`  
 Указатель на объект `message`.  
  
 `_PSource`  
 Указатель на исходный блок, предлагающий сообщение.  
  
### <a name="return-value"></a>Возвращаемое значение  
 Объект [message_status](concurrency-namespace-enums.md) , указывающее, что целевой объект решил сделать с сообщением.  
  
##  <a name="supports_anonymous_source"></a>supports_anonymous_source 

 Переопределяет метод `supports_anonymous_source`, чтобы указать, что данный блок может принимать сообщения, предоставляемые ему несвязанным источником.  
  
```
virtual bool supports_anonymous_source();
```  
  
### <a name="return-value"></a>Возвращаемое значение  
 Значение `true`, поскольку блок не откладывает предоставляемые сообщения.  
  
## <a name="see-also"></a>См. также  
 [пространство имен Concurrency](concurrency-namespace.md)   
 [Класс transformer](transformer-class.md)
