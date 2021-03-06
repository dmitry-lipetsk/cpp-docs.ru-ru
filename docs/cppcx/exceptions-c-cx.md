---
title: "Исключения (C + +/ CX) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2018
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 6cbdc1f1-e4d7-4707-a670-86365146432f
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f7e54d98ac4e1398753746dcac074de53ee2e7a0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="exceptions-ccx"></a>Исключения (C++/CX)

Обработка ошибок в C + +/ CX основана на исключениях. На самом базовом уровне компоненты среды выполнения Windows на предмет ошибок значений HRESULT. В C + +/ CX, эти значения преобразуются в строго типизированные исключения, которые содержат значение HRESULT и строковое описание, доступное программным образом.  Исключения реализованы как классы `ref class` , производные от класса `Platform::Exception`.  В пространстве имен `Platform` определены отдельные классы исключений для наиболее часто встречающихся значений HRESULT. Все остальные значения передаются через класс `Platform::COMException` . Все классы исключений имеют [Exception::HResult](platform-exception-class.md#hresult) , которое можно использовать для получения исходного значения HRESULT. Также можно просматривать сведения о стеке вызовов для пользовательского кода в отладчике, что позволяет точно определять источник исключения, даже если он находится в коде, написанном на языке, отличном от C++.

## <a name="exceptions"></a>Исключения

В программе C++, можно создавать и перехватывать исключения, поступающие от операций среды выполнения Windows, а также исключения, который является производным от `std::exception`, или определяемого пользователем типа. Необходимо только в том случае, если его к примеру, пересекает границы двоичного интерфейса (ABI) приложения, если код, который перехватывает это исключение, написан на языке JavaScript исключения среды выполнения Windows. Когда исключение C++, отличных от Windows среда выполнения достигает границы интерфейса ABI, оно преобразуется в `Platform::FailureException` исключение, которое представляет значение HRESULT E_FAIL. Дополнительные сведения об интерфейсе ABI см. в разделе [создание компонентов среды выполнения Windows в C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

Можно объявить [Platform::Exception](platform-exception-class.md) с помощью одного или двух конструкторов, принимающих параметр HRESULT либо параметры HRESULT и [Platform::String](platform-string-class.md)^ параметр, который можно передать через Интерфейс ABI в любое приложение среды выполнения Windows, который обрабатывает его. Либо можно объявить исключение, воспользовавшись одним из двух перегрузок [метода Exception::CreateException](platform-exception-class.md#createexception) , которые могут принимать параметр HRESULT или параметры HRESULT и `Platform::String^` .

## <a name="standard-exceptions"></a>Стандартные исключения

C + +/ CX поддерживает набор стандартных исключений, которые представляют типичные ошибки HRESULT. Каждое стандартное исключение наследуется от класса [Platform::COMException](platform-comexception-class.md), который, в свою очередь, наследуется от `Platform::Exception`. Если вы вызываете исключение через границы интерфейса ABI, оно должно быть одним из стандартных исключений.

Делать собственные типы исключений производными от класса `Platform::Exception`не допускается. Чтобы создать пользовательское исключение, используйте определяемое пользователем значение HRESULT для создания объекта `COMException` .

В следующей таблице перечислены стандартные исключения.

|name|Значение HRESULT|Описание:|
|----------|------------------------|-----------------|
|COMException|*Определяемое пользователем значение hresult*|Возникает при возвращении неизвестного значения HRESULT после вызова метода COM.|
|AccessDeniedException|E\_ДОСТУП ЗАПРЕЩЕН|Возникает при запрете доступа к ресурсу или функции.|
|ChangedStateException|E\_CHANGED\_СОСТОЯНИЯ|Возникает, если метод итератора коллекции или представления коллекции вызван после изменения родительской коллекции, что делает результаты метода недействительными.|
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|Возникает, если COM-класс не зарегистрирован.|
|DisconnectedException|RPC\_E\_DISCONNECTED|Возникает, если объект отключен от своих клиентов.|
|FailureException|E\_ОШИБКОЙ|Возникает, если операция завершается неудачно.|
|InvalidArgumentException|E\_INVALIDARG|Вызывается, если один из передаваемых методу аргументов является недопустимым.|
|InvalidCastException|E\_NOINTERFACE|Возникает, если тип не удается привести к другому типу.|
|NotImplementedException|E\_NOTIMPL|Возникает, если метод интерфейса не реализован в классе.|
|NullReferenceException|E\_УКАЗАТЕЛЬ|Возникает при попытке разыменовать ссылку на объект NULL.|
|ObjectDisposedException|RO\_E\_ЗАКРЫТО|Вызывается при выполнении операции над ликвидированным объектом.|
|OperationCanceledException|E\_ABORT|Возникает при отмене операции.|
|OutOfBoundsException|E\_ГРАНИЦЫ|Возникает, когда операция пытается получить доступ к данным за пределами допустимого диапазона.|
|OutOfMemoryException|E\_OUTOFMEMORY|Возникает, если недостаточно памяти для выполнения операции.|
|WrongThreadException|RPC\_E\_НЕПРАВИЛЬНЫЙ\_ПОТОКОВ|Вызывается, если поток выполняет вызов посредством указателя на интерфейс для прокси-объекта, который не принадлежит к подразделению потока.|

## <a name="hresult-and-message-properties"></a>Свойства HResult и Message

Все исключения имеют свойство [HResult](platform-comexception-class.md#hresult) и свойство [Message](platform-comexception-class.md#message) . Свойство [Exception::HResult](platform-exception-class.md#hresult) получает базовое числовое значение HRESULT соответствующего исключения. Свойство [Exception::Message](platform-exception-class.md#message) получает предоставленную системой строку с описанием исключения. В Windows 8 сообщение доступно только в отладчике и только для чтения. Это означает, что его невозможно изменить после повторного создания исключения. В Windows 8.1 к строке сообщения можно получить доступ программным образом и предоставить новое сообщение, если необходимо заново создать исключение. В отладчике доступны более подробные данные стеков вызовов, включая данные об асинхронных вызовах методов.

### <a name="examples"></a>Примеры

В этом примере показано, как вызывать исключение среды выполнения Windows для синхронных операций:

[!code-cpp[cx_exceptions#01](codesnippet/CPP/exceptiontest/class1.cpp#01)]

В следующем пример показано, как перехватить исключение.

[!code-cpp[cx_exceptions#02](codesnippet/CPP/exceptiontest/class1.cpp#02)]

Для перехвата исключений, создаваемых во время асинхронной операции, используйте класс задачи и добавьте продолжение обработки ошибок. Продолжение обработки ошибок маршалирует исключения, вызванные в других потоках, обратно вызывающему потоку, что позволяет обрабатывать все возможные исключения в одной структурной единице кода. Дополнительные сведения см. в разделе [асинхронное программирование в C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps).

## <a name="unhandlederrordetected-event"></a>Событие UnhandledErrorDetected

В Windows 8.1 можно подписаться на [Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected](/uwp/api/windows.applicationmodel.core.icoreapplicationunhandlederror#Windows_ApplicationModel_Core_ICoreApplicationUnhandledError_UnhandledErrorDetected) статическое событие, которое предоставляет доступ к необработанным ошибкам, которые должны привести к остановке процесса. Независимо от того, где возникла ошибка, она достигнет этого обработчика как [Windows::applicationmodel:: Core::](/uwp/api/windows.applicationmodel.core.unhandlederror) объекта, который передается с аргументами события. При вызове метода `Propagate` для объекта он создает исключение `Platform::*Exception` типа, соответствующего коду ошибки. В блоках catch можно при необходимости сохранить состояние пользователя, а затем либо разрешить завершение процесса путем вызова `throw`, либо каким-либо образом вернуть программу в известное состояние. В следующем примере демонстрируется использование основного подхода:

В app.xaml.h:

```cpp
void OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e);
```

В app.xaml.cpp:

```cpp
// Subscribe to the event, for example in the app class constructor:
Windows::ApplicationModel::Core::CoreApplication::UnhandledErrorDetected += ref new EventHandler<UnhandledErrorDetectedEventArgs^>(this, &App::OnUnhandledException);

// Event handler implementation:
void App::OnUnhandledException(Platform::Object^ sender, Windows::ApplicationModel::Core::UnhandledErrorDetectedEventArgs^ e)
{
    auto err = e->UnhandledError;

    if (!err->Handled) //Propagate has not been called on it yet.
{
     try
    {
        err->Propagate();
    }
    // Catch any specific exception types if you know how to handle them
    catch (AccessDeniedException^ ex)
    {
        // TODO: Log error and either take action to recover
        // or else re-throw exception to continue fail-fast
    }

}
```

### <a name="remarks"></a>Примечания

C + +/ CX не использует `finally` предложения.

## <a name="see-also"></a>См. также

[Справочник по языку Visual C++](visual-c-language-reference-c-cx.md)  
[Справочник по пространствам имен](namespaces-reference-c-cx.md)  
