---
title: event (C++/CLI и C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- event
- event_cpp
helpviewer_keywords:
- event keyword [C++]
ms.assetid: c4998e42-883c-4419-bbf4-36cdc979dd27
ms.openlocfilehash: 26bfc3bb9892486353f55a71cfd86a17f2de98b5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516589"
---
# <a name="event--ccli-and-ccx"></a>event (C++/CLI и C++/CX)

Ключевое слово **event** объявляет *событие*, которое является уведомлением для зарегистрированных подписчиков (*обработчиков событий*) о том, что произошло нечто интересное.

## <a name="all-runtimes"></a>Все среды выполнения

C++/CX поддерживает объявление *элемента события* или *блока событий*. Член события является сокращением для объявления блока событий. По умолчанию член события объявляет функции `add()`, `remove()` и `raise()`, явно объявленные в блоке событий. Для настройки функций в члене события объявите блок событий и затем переопределите нужные вам функции.

### <a name="syntax"></a>Синтаксис

```cpp
// event data member
modifiereventdelegate^ event_name;

// event block
modifiereventdelegate^ event_name
{
   modifierreturn_valueadd(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>Параметры

*modifier*<br/>
Модификатор, который может использоваться в объявлении события или в методе доступа события.  Возможные значения: **static** и **virtual**.

*delegate*<br/>
[Делегат](delegate-cpp-component-extensions.md), сигнатура которого должна соответствовать обработчику событий.

*event_name*<br/>
Имя события.

*return_value*<br/>
Возвращаемое значение метода доступа события.  Чтобы возвращаемое значение было проверяемым, его тип должен быть **void**.

*parameters*<br/>
(Необязательно) Параметры для метода `raise`, соответствующие сигнатуре параметра *delegate*.

### <a name="remarks"></a>Примечания

Событие — это связь между делегатом и функцией-членом (обработчиком событий), которая отвечает за инициацию события и позволяет клиентам из любого класса регистрировать методы, соответствующие сигнатуре и типу возвращаемого значения базового делегата.

Существует два вида объявлений событий.

*Элемент данных события*<br/>
Компилятор автоматически создает хранилище для события в виде члена типа делегата и создает внутренние функции-члены `add()`, `remove()` и `raise()`. Элемент данных события должен объявляться внутри класса. Тип возвращаемого значения типа возвращаемого значения делегата должен соответствовать типу возвращаемого значения обработчика событий.

*Блок событий*<br/>
Блок событий позволяет явно объявить и настроить поведение методов `add()`, `remove()` и `raise()`.

Вы можете использовать **operators+=** и **operator-=** для добавления и удаления обработчика событий или для явного вызова методов `add()` и `remove()`.

**event** — контекстно-зависимое ключевое слово. Подробные сведения см. в статье [Context-Sensitive Keywords (C++/CLI and C++/CX)](context-sensitive-keywords-cpp-component-extensions.md) (Контекстно-зависимые ключевые слова (C++/CLI и C++/CX)).

## <a name="windows-runtime"></a>Среда выполнения Windows

### <a name="remarks"></a>Примечания

Дополнительные сведения см. в статье [Events (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh755799.aspx) (События (C++/CX)).

Если вы собираетесь добавить и затем удалить обработчик событий, необходимо сохранить структуру EventRegistrationToken, возвращаемую операцией добавления. Затем в операции удаления необходимо использовать сохраненную структуру EventRegistrationToken для определения удаляемого обработчика событий.

### <a name="requirements"></a>Требования

Параметр компилятора: `/ZW`

## <a name="common-language-runtime"></a>Среда CLR

Ключевое слово **event** позволяет объявить событие. Событие — это способ, которым класс предоставляет уведомление о том, что произошло нечто интересное.

### <a name="syntax"></a>Синтаксис

```cpp
// event data member
modifiereventdelegate^ event_name;

// event block
modifiereventdelegate^ event_name
{
   modifierreturn_valueadd(delegate^ name);
   modifier void remove(delegate^ name);
   modifier void raise(parameters);
}
```

### <a name="parameters"></a>Параметры

*modifier*<br/>
Модификатор, который может использоваться в объявлении события или в методе доступа события.  Возможные значения: **static** и **virtual**.

*delegate*<br/>
[Делегат](delegate-cpp-component-extensions.md), сигнатура которого должна соответствовать обработчику событий.

*event_name*<br/>
Имя события.

*return_value*<br/>
Возвращаемое значение метода доступа события.  Чтобы возвращаемое значение было проверяемым, его тип должен быть **void**.

*parameters*<br/>
(Необязательно) Параметры для метода `raise`, соответствующие сигнатуре параметра *delegate*.

### <a name="remarks"></a>Примечания

Событие — это связь между делегатом и функцией-членом (обработчиком событий), которая отвечает за инициацию события и позволяет клиентам из любого класса регистрировать методы, соответствующие сигнатуре и типу возвращаемого значения базового делегата.

Делегат может иметь один или несколько связанных методов, вызываемых, когда код указывает, что произошло событие. Событие в одной программе можно сделать доступным для других программ, предназначенных для среды CLR .NET Framework.

Существует два вида объявлений событий.

*Элементы данных события*<br/>
Хранилище для события в виде члена типа делегата создается компилятором для событий элементов данных.  Элемент данных события должен объявляться внутри класса. Он также называется простым событием (см. пример кода ниже).

*Блоки событий*<br/>
Блоки событий позволяют настраивать поведение методов добавления, удаления и порождения путем реализации методов добавления, удаления и порождения. Сигнатура методов добавления, удаления и порождения должна соответствовать сигнатуре делегата.  События блока событий не являются элементами данных, и любое их использование в качестве элемента данных приведет к ошибке компилятора.

Возвращаемый тип обработчика события должен соответствовать возвращаемому типу делегата.

В платформе .NET Framework данные-член можно рассматривать, как если бы это был сам метод (т. е., метод `Invoke` соответствующего делегата). Необходимо заранее определить тип делегата для объявления данных-члена управляемого события. Напротив, метод управляемого события неявно определяет соответствующий управляемый делегат, если он еще не определен.  См. пример кода в конце этого раздела.

При объявлении управляемого события можно указать методы доступа добавления и удаления, которые будут вызываться в случае добавления или удаления обработчиков события с помощью операторов += и -=. Методы добавления, удаления и порождения могут вызываться явно.

Для создания и использования событий в Visual C++ необходимо выполнить следующие действия.

1. Создать или определить делегат. При определении собственных событий необходимо также убедиться, что существует делегат для использования с ключевым словом **event**. Если событие является предопределенным, например в .NET Framework, то потребителям этого события нужно знать только имя делегата.

2. Создать класс, содержащий следующие объекты.

   - Событие, созданное из делегата.

   - (Необязательно) Метод, который проверяет, что экземпляр делегата, объявленный с ключевым словом **event**, существует. В противном случае эту логику необходимо разместить в коде, который инициирует событие.

   - Методы, которые вызывают события. Эти методы могут быть переопределениями некоторых функциональных возможностей базового класса.

   Этот класс определяет событие.

3. Определить один или несколько классов, которые связывают методы с событием. Каждый из этих классов будет связывать один или несколько методов с событием в базовом классе.

4. Использовать событие.

   - Создать объект класса, содержащего объявление события.

   - Создать объект класса, содержащего определение события.

Дополнительные сведения о событиях C++/CLI см. в статье

- [Практическое руководство. Использование событий в C++/CLI](../dotnet/how-to-use-events-in-cpp-cli.md)

### <a name="requirements"></a>Требования

Параметр компилятора: `/clr`

### <a name="examples"></a>Примеры

В следующем примере кода демонстрируется объявление пар делегатов, событий и обработчиков событий; подписка (добавление) обработчиков событий; вызов обработчиков событий и затем отмена подписки (удаление) обработчиков событий.

```cpp
// mcppv2_events.cpp
// compile with: /clr
using namespace System;

// declare delegates
delegate void ClickEventHandler(int, double);
delegate void DblClickEventHandler(String^);

// class that defines events
ref class EventSource {
public:
   event ClickEventHandler^ OnClick;   // declare the event OnClick
   event DblClickEventHandler^ OnDblClick;   // declare OnDblClick

   void FireEvents() {
      // raises events
      OnClick(7, 3.14159);
      OnDblClick("Hello");
   }
};

// class that defines methods that will called when event occurs
ref class EventReceiver {
public:
   void OnMyClick(int i, double d) {
      Console::WriteLine("OnClick: {0}, {1}", i, d);
   }

   void OnMyDblClick(String^ str) {
      Console::WriteLine("OnDblClick: {0}", str);
   }
};

int main() {
   EventSource ^ MyEventSource = gcnew EventSource();
   EventReceiver^ MyEventReceiver = gcnew EventReceiver();

   // hook handler to event
   MyEventSource->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);
   MyEventSource->OnDblClick += gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);

   // invoke events
   MyEventSource->FireEvents();

   // unhook handler to event
   MyEventSource->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);
   MyEventSource->OnDblClick -= gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);
}
```

```Output
OnClick: 7, 3.14159

OnDblClick: Hello
```

В следующем примере кода демонстрируется логика, используемая для создания метода `raise` простого события. Если событие имеет один или несколько подписчиков, при вызове метода `raise` явно или неявно вызывается делегат. Если типом возвращаемого значения делегата не является **void** и если отсутствуют подписчики на событие, метод `raise` возвращает значение по умолчанию для типа делегата. Если подписчики на событие отсутствуют, вызов метода `raise` просто возвращается и исключение не вызывается. Если типом возвращаемого значения делегата не является **void**, возвращается тип делегата.

```cpp
// trivial_events.cpp
// compile with: /clr /c
using namespace System;
public delegate int Del();
public ref struct C {
   int i;
   event Del^ MyEvent;

   void FireEvent() {
      i = MyEvent();
   }
};

ref struct EventReceiver {
   int OnMyClick() { return 0; }
};

int main() {
   C c;
   c.i = 687;

   c.FireEvent();
   Console::WriteLine(c.i);
   c.i = 688;

   EventReceiver^ MyEventReceiver = gcnew EventReceiver();
   c.MyEvent += gcnew Del(MyEventReceiver, &EventReceiver::OnMyClick);
   Console::WriteLine(c.i);
}
```

```Output
0

688
```

## <a name="see-also"></a>См. также

[Расширения компонентов для .NET и UWP](component-extensions-for-runtime-platforms.md)