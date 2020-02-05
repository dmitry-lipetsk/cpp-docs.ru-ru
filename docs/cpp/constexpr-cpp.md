---
title: constexpr (C++)
description: Руководствуясь ключевым C++ словом Language constexpr.
ms.date: 01/28/2020
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
no-loc:
- constexpr
- const
- inline
- goto
- try
- if
- switch
- for
- while
ms.openlocfilehash: 4f34eef3217377ab50a2d80d42b5bea4b054c5be
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821783"
---
# <a name="opno-locconstexpr-c"></a>constexpr (C++)

Ключевое слово **constexpr** было введено в c++ 11 и улучшено в c++ 14. Это означает *константное выражение*. Как и **const** , его можно применять к переменным: при попытке любого кода изменить значение возникает ошибка компилятора. В отличие от const **constexpr** также можно применять к функциям и конструкторам классов. **constexpr** указывает, что значение или возвращаемое значение является константой и, по возможности, будет вычисляться во время компиляции.

**constexpr** целочисленное значение можно использовать везде, где требуется const целое число, например в аргументах шаблона и в объявлениях массивов. Если значение вычислено во время компиляции, а не во время выполнения, оно помогает программе работать быстрее и использует меньше памяти.

Для ограничения сложности вычислений времени компиляции и их возможного влияния на время компиляции стандарт C++ 14 требует, чтобы типы в константных выражениях были [литеральными типами](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="syntax"></a>Синтаксис

> **constexpr** *идентификатор типа литерала* **=** *константное выражение* **;** \
> **constexpr** идентификатор *типа литерала* **{** *Constant-Expression* **}** **;** \
> **constexpr** идентификатор *типа литерала* **(** *params* **)** **;** \
> **constexpr** *ctor* **(** *params* **)** **;**

## <a name="parameters"></a>Параметры

*params*\
Один или несколько параметров, каждый из которых должен быть типом литерала и сам должен быть константным выражением.

## <a name="return-value"></a>Возвращаемое значение

**constexpr** переменная или функция должна возвращать [литеральный тип](trivial-standard-layout-and-pod-types.md#literal_types).

## <a name="opno-locconstexpr-variables"></a>Переменные constexpr

Основное различие между **const** и **constexpr** переменными заключается в том, что инициализация **const** переменной может быть отложена до времени выполнения. Переменная **constexpr** должна быть инициализирована во время компиляции.  Все переменные **constexpr** **const** .

- Переменная может быть объявлена с **constexpr** , если она имеет тип литерала и инициализирована. Если инициализация выполняется конструктором, конструктор должен быть объявлен как **constexpr** .

- Ссылка может быть объявлена как **constexpr** при выполнении обоих этих условий: объект, на который указывает ссылка, инициализируется константным выражением, а любые неявные преобразования, вызванные во время инициализации, также являются константными выражениями.

- Все объявления **constexpr** переменной или функции должны иметь спецификатор **constexpr** .

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a>функции constexpr

**constexprом** является функция, возвращаемое значение которой вычисляемым во время компиляции, если это требуется для использования кода. Для использования кода требуется возвращаемое значение во время компиляции для инициализации **constexpr** переменной или для предоставления аргумента шаблона, не являющегося типом. Если его аргументы **constexpr** значения, то функция **constexpr** выдает константу времени компиляции. При вызове с аргументами, не являющимися **constexpr** , или когда его значение не требуется во время компиляции, оно создает значение во время выполнения, например обычную функцию. (Это двойное поведение избавляет от необходимости писать **constexpr** и **неconstexprные** версии одной и той же функции.)

**constexprная** функция или конструктор неявно **inline** .

К функциям constexpr применяются следующие правила.

- Функция **constexpr** должна принимать и возвращать только [типы литералов](trivial-standard-layout-and-pod-types.md#literal_types).

- Функция **constexpr** может быть рекурсивной.

- Он не может быть [виртуальным](../cpp/virtual-cpp.md). Конструктор не может быть определен как **constexpr** , если включающий класс имеет какие-либо виртуальные базовые классы.

- Тело может быть определено как `= default` или `= delete`.

- Текст не может содержать **goto** операторы или блоки **try** .

- Явная специализация шаблона, не относящегося к **constexpr** , может быть объявлена как **constexpr** :

- Явная специализация шаблона **constexpr** также не требуется **constexpr** :

К функциям **constexpr** в Visual Studio 2017 и более поздних версий применяются следующие правила.

- Он может содержать инструкции **if** и **switch** , а также все операторы цикла, **включаяfor** , **for** на основе диапазонов, **while** и **Do-while** .

- Он может содержать объявления локальных переменных, но переменная должна быть инициализирована. Он должен быть типом литерала и не может быть **статическим** или локальным потоком. Локально объявленная переменная не обязательно должна быть **const** и может изменяться.

- **constexpr** **нестатической** функции-члена не обязательно должны быть неявно **const** .

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> В отладчике Visual Studio при отладке неоптимизированной отладочной сборки можно определить, вычисляется ли **constexprная** функция во время компиляции путем помещения точки останова в нее. Попадание в точку останова означает, что функция была вызвана во время выполнения.  Если попадания в точку останова не происходит, это означает, что функция была вызвана во время компиляции.

## <a name="extern-opno-locconstexpr"></a>внешний constexpr

Параметр компилятора [/Zc: externConstexpr](../build/reference/zc-externconstexpr.md) заставляет компилятор применить [внешнюю компоновку](../c-language/external-linkage.md) к переменным, объявленным с помощью **внешнего constexpr** . В более ранних версиях Visual Studio либо по умолчанию, либо при указании параметра **/Zc: externConstexpr —** Visual Studio применяет внутреннюю компоновку к **constexpr** переменным, даже если используется ключевое слово **extern** . Параметр **/Zc: externConstexpr** доступен начиная с Visual Studio 2017 с обновлением 15,6 и по умолчанию отключен. Параметр [/permissive-](../build/reference/permissive-standards-conformance.md) не включает **/Zc: externConstexpr**.

## <a name="example"></a>Пример

В следующем примере показаны переменные, функции и определяемые пользователем типы **constexpr** . В последней инструкции в `main()`функция-член **constexpr** `GetValue()` является вызовом во время выполнения, поскольку значение не обязательно должно быть известно во время компиляции.

```cpp
// constexpr.cpp
// Compile with: cl /EHsc /W4 constexpr.cpp
#include <iostream>

using namespace std;

// Pass by value
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};

// Pass by reference
constexpr float exp2(const float& x, const int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
};

// Compile-time computation of array length
template<typename T, int N>
constexpr int length(const T(&)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue() const
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>Требования

Visual Studio 2015 или более поздней версии.

## <a name="see-also"></a>См. также:

[Объявления и определения](../cpp/declarations-and-definitions-cpp.md)\
[const](../cpp/const-cpp.md)
