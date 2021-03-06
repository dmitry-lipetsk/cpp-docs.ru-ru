---
title: "Оператор dynamic_cast | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: dynamic_cast_cpp
dev_langs: C++
helpviewer_keywords: dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 29add795c7adeca67fc85c7cf3b1b90d17f804fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="dynamiccast-operator"></a>Оператор dynamic_cast
Преобразует операнд `expression` в объект типа `type-id`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dynamic_cast < type-id > ( expression )  
```  
  
## <a name="remarks"></a>Примечания  
 Параметр `type-id` должен быть указателем или ссылкой на ранее определенный тип класса или "указателем на void". Тип операнда `expression` должен быть указателем, если `type-id` является указателем, или l-значением, если `type-id` является ссылкой.  
  
 В разделе [static_cast](../cpp/static-cast-operator.md) объяснение различий между статическим и динамическим приведения преобразованиями, и когда следует использовать каждое.  
  
 В поведении `dynamic_cast` в управляемом коде имеется два критических изменения:  
  
-   `dynamic_cast` на указатель к базовому типу упакованного перечисления вызывает сбой во время выполнения; вместо преобразованного указателя будет возвращено значение 0.  
  
-   `dynamic_cast` больше не создает исключение, если `type-id` является внутренним указателем на тип значения, в результате чего приведение вызывает сбой во время выполнения.  Приведение теперь возвращает значение указателя 0, а исключение не создается.  
  
 Если `type-id` является указателем на однозначно доступный прямой или косвенный базовый класс операнда `expression`, то результатом будет указатель на уникальный подобъект типа `type-id`. Пример:  
  
```  
// dynamic_cast_1.cpp  
// compile with: /c  
class B { };  
class C : public B { };  
class D : public C { };  
  
void f(D* pd) {  
   C* pc = dynamic_cast<C*>(pd);   // ok: C is a direct base class  
                                   // pc points to C subobject of pd   
   B* pb = dynamic_cast<B*>(pd);   // ok: B is an indirect base class  
                                   // pb points to B subobject of pd  
}  
```  
  
 Этот тип преобразования называется "восходящим приведением типа", поскольку при нем указатель перемещается вверх по иерархии классов: от производного класса к классу, от которого он является производным. Восходящее приведение типа является неявным преобразованием.  
  
 Если `type-id` является указателем void*, выполняется проверка во время выполнения, чтобы определить фактический тип операнда `expression`. Результатом является указатель на полный объект, на который указывает операнд `expression`. Пример:  
  
```  
// dynamic_cast_2.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B {virtual void f();};  
  
void f() {  
   A* pa = new A;  
   B* pb = new B;  
   void* pv = dynamic_cast<void*>(pa);  
   // pv now points to an object of type A  
  
   pv = dynamic_cast<void*>(pb);  
   // pv now points to an object of type B  
}  
```  
  
 Если `type-id` не является указателем void*, то выполняется проверка во время выполнения, чтобы определить, может ли объект, на который указывает операнд `expression`, быть преобразован в тип, указанный параметром `type-id`.  
  
 Если тип операнда `expression` является базовым классом типа, заданного параметром `type-id`, то выполняется проверка во время выполнения, чтобы определить, указывает ли операнд `expression` на полный объект типа, заданного параметром `type-id`. Если это так, то результатом является указатель на полный объект типа, заданного параметром `type-id`. Пример:  
  
```  
// dynamic_cast_3.cpp  
// compile with: /c /GR  
class B {virtual void f();};  
class D : public B {virtual void f();};  
  
void f() {  
   B* pb = new D;   // unclear but ok  
   B* pb2 = new B;  
  
   D* pd = dynamic_cast<D*>(pb);   // ok: pb actually points to a D  
   D* pd2 = dynamic_cast<D*>(pb2);   // pb2 points to a B not a D  
}  
```  
  
 Этот тип преобразования называется "нисходящим приведением типа", поскольку при нем указатель перемещается вниз по иерархии классов: от заданного класса к производному от него классу.  
  
 В случаях множественного наследования возникают возможности для неоднозначности. Рассмотрим для примера иерархию классов, показанную на следующем рисунке.  
  
 Для типов среды CLR результатом динамического приведения `dynamic_cast` является либо холостая команда, если преобразование было выполнено неявно, либо инструкция MSIL `isinst`, которая выполняет динамическую проверку и в случае сбоя преобразования возвращает `nullptr`.  
  
 В следующем примере используется динамическое приведение (`dynamic_cast`), чтобы определить, является ли класс экземпляром определенного типа:  
  
```  
// dynamic_cast_clr.cpp  
// compile with: /clr  
using namespace System;  
  
void PrintObjectType( Object^o ) {  
   if( dynamic_cast<String^>(o) )  
      Console::WriteLine("Object is a String");  
   else if( dynamic_cast<int^>(o) )  
      Console::WriteLine("Object is an int");  
}  
  
int main() {  
   Object^o1 = "hello";  
   Object^o2 = 10;  
  
   PrintObjectType(o1);  
   PrintObjectType(o2);  
}  
```  
  
 ![Иерархии, показывающая множественное наследование классов](../cpp/media/vc39011.gif "vc39011")  
Иерархия классов, демонстрирующая множественное наследование  
  
 Указатель на объект типа `D` можно безопасно привести к `B` или `C`. Однако если в результате приведения `D` указывает на объект `A`, какой экземпляр объекта `A` будет являться результатом? Это может привести к ошибке неоднозначного приведения. Чтобы обойти эту проблему, можно выполнить два однозначных приведения. Пример:  
  
```  
// dynamic_cast_4.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B {virtual void f();};  
class D : public B {virtual void f();};  
  
void f() {  
   D* pd = new D;  
   B* pb = dynamic_cast<B*>(pd);   // first cast to B  
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous  
}  
```  
  
 При использовании виртуальных базовых классов могут возникать дополнительные неоднозначности. Рассмотрим для примера иерархию классов, показанную на следующем рисунке.  
  
 ![Класс иерархия, показывающая виртуальные базовые классы](../cpp/media/vc39012.gif "vc39012")  
Иерархия классов, демонстрирующая виртуальные базовые классы  
  
 В этой иерархии объект `A` является виртуальным базовым классом. При использовании заданного экземпляра класса `E` и указателя на подобъект `A` динамическое приведение `dynamic_cast` к указателю на `B` вызовет сбой в силу неоднозначности. Необходимо сначала выполнить обратное приведение к полному объекту `E`, затем однозначным образом вернуться вверх по иерархии, чтобы дойти до нужного объекта `B`.  
  
 Рассмотрим для примера иерархию классов, показанную на следующем рисунке.  
  
 ![Класс иерархия, показывающая повторяющиеся базовые классы](../cpp/media/vc39013.gif "vc39013")  
Иерархия классов, демонстрирующая дублирование базовых классов  
  
 При использовании заданного объекта типа `E` и указателя на подобъект `D` можно выполнить три преобразования, чтобы перейти от подобъекта `D` к крайнему слева подобъекту `A`. Можно выполнить преобразование `dynamic_cast` из указателя `D` в указатель `E`, затем преобразование (либо `dynamic_cast`, либо неявное преобразование) из `E` в `B`, и наконец неявное преобразование из `B` в `A`. Пример:  
  
```  
// dynamic_cast_5.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B : public A {virtual void f();};  
class C : public A { };  
class D {virtual void f();};  
class E : public B, public C, public D {virtual void f();};  
  
void f(D* pd) {  
   E* pe = dynamic_cast<E*>(pd);  
   B* pb = pe;   // upcast, implicit conversion  
   A* pa = pb;   // upcast, implicit conversion  
}  
```  
  
 Оператор `dynamic_cast` также можно использовать для "перекрестного приведения". В иерархии классов из предыдущего примера можно выполнить приведение указателя, например, из подобъекта `B` в подобъект `D`, если полный объект имеет тип `E`.  
  
 С учетом перекрестного приведения можно выполнить преобразование из указателя на объект `D` в крайний левый подобъект `A` всего за два шага. Можно перекрестное приведение из `D` в `B`, а затем неявное преобразование из `B` в `A`. Пример:  
  
```  
// dynamic_cast_6.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B : public A {virtual void f();};  
class C : public A { };  
class D {virtual void f();};  
class E : public B, public C, public D {virtual void f();};  
  
void f(D* pd) {  
   B* pb = dynamic_cast<B*>(pd);   // cross cast  
   A* pa = pb;   // upcast, implicit conversion  
}  
```  
  
 Значение пустого указателя преобразуется в значение пустого указателя целевого типа при помощи оператора `dynamic_cast`.  
  
 Если при использовании оператора `dynamic_cast < type-id > ( expression )` невозможно точно преобразовать операнд `expression` в тип `type-id`, то проверка во время выполнения приводит к сбою приведения. Пример:  
  
```  
// dynamic_cast_7.cpp  
// compile with: /c /GR  
class A {virtual void f();};  
class B {virtual void f();};  
  
void f() {  
   A* pa = new A;  
   B* pb = dynamic_cast<B*>(pa);   // fails at runtime, not safe;  
   // B not derived from A  
}  
```  
  
 Значением приведения к типу указателя, которое привело к сбою, является пустой указатель. Ошибки приведения для ссылки на тип вызывает [исключение bad_cast](../cpp/bad-cast-exception.md).   Если `expression` указывать или не ссылаются на допустимый объект `__non_rtti_object` исключения.  
  
 В разделе [typeid](../cpp/typeid-operator.md) объяснение `__non_rtti_object` исключение.  
  
## <a name="example"></a>Пример  
 В следующем примере создается указатель базового класса (структура A) на объект (структура C).  Это (а также тот факт, что они являются виртуальными функциями) порождает полиморфизм времени выполнения.  
  
 В этом примере также вызывается невиртуальная функция в иерархии.  
  
```  
// dynamic_cast_8.cpp  
// compile with: /GR /EHsc  
#include <stdio.h>  
#include <iostream>  
  
struct A {  
    virtual void test() {  
        printf_s("in A\n");  
   }  
};  
  
struct B : A {  
    virtual void test() {  
        printf_s("in B\n");  
    }  
  
    void test2() {  
        printf_s("test2 in B\n");  
    }  
};  
  
struct C : B {  
    virtual void test() {  
        printf_s("in C\n");  
    }  
  
    void test2() {  
        printf_s("test2 in C\n");  
    }  
};  
  
void Globaltest(A& a) {  
    try {  
        C &c = dynamic_cast<C&>(a);  
        printf_s("in GlobalTest\n");  
    }  
    catch(std::bad_cast) {  
        printf_s("Can't cast to C\n");  
    }  
}  
  
int main() {  
    A *pa = new C;  
    A *pa2 = new B;  
  
    pa->test();  
  
    B * pb = dynamic_cast<B *>(pa);  
    if (pb)  
        pb->test2();  
  
    C * pc = dynamic_cast<C *>(pa2);  
    if (pc)  
        pc->test2();  
  
    C ConStack;  
    Globaltest(ConStack);  
  
   // will fail because B knows nothing about C  
    B BonStack;  
    Globaltest(BonStack);  
}  
```  
  
```Output  
in C  
test2 in B  
in GlobalTest  
Can't cast to C  
```  
  
## <a name="see-also"></a>См. также  
 [Операторы приведения](../cpp/casting-operators.md)   
 [Ключевые слова](../cpp/keywords-cpp.md)