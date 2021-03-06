---
title: "Семантика стека C++ для ссылочных типов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: reference types, C++ stack semantics for
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8f4bf38fa6512b0dc86edad43c893d2dd09a97a4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="c-stack-semantics-for-reference-types"></a>Семантика стека C++ для ссылочных типов
До Visual C++ 2005 экземпляр ссылочного типа могут создаваться только с помощью `new` куче, оператор, который создал объект в сборке мусора. Тем не менее теперь можно создать экземпляр ссылочного типа, используя тот же синтаксис, используемый для создания экземпляра собственного типа в стеке. Поэтому, не требуется использовать [ref new gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md) для создания объекта ссылочного типа. И, когда объект выходит за пределы области, компилятор вызывает деструктор объекта.  
  
## <a name="remarks"></a>Примечания  
 При создании экземпляра с использованием семантики стека ссылочного типа, компилятор внутренним образом создать экземпляр в куче сбора мусора (с помощью `gcnew`).  
  
 При подписи или типа возвращаемого значения функции включает экземпляр ссылочного типа по значению, функция будут помечены в метаданных, как они требуют специальной обработки (с modreq). Эта специальная обработка в данный момент предоставляется только клиентам Visual C++; других языках в настоящее время не поддерживают много функций или данных, использовать ссылочные типы, созданные с помощью семантики стека.  
  
 Одна из причин для использования `gcnew` (динамическое выделение) вместо стека семантику бы определить, имеет ли тип деструктор. Кроме того с помощью ссылочных типов, созданных с помощью семантики стека сигнатур функций невозможна, если требуется функций для использования в языках, отличных от Visual C++.  
  
 Компилятор не создает конструктор копии для ссылочного типа. Таким образом Если определить функцию, которая использует тип ссылки по значению в сигнатуре, необходимо определить конструктор копии для ссылочных типов. Конструктор копии для ссылочного типа имеет подпись следующего вида: `R(R%){}`.  
  
 Компилятор не создает оператор присваивания по умолчанию для типа ссылки. Оператор присваивания позволяет создать объект с использованием семантики стека и инициализируйте его с существующие объекта, созданного с помощью семантики стека. Оператор присваивания для ссылочного типа имеет подпись следующего вида: `void operator=( R% ){}`.  
  
 Если ваш тип деструктор освобождает ресурсы, критические и для ссылочных типов с помощью семантики стека, необходимо явным образом вызовите деструктор (или вызвать `delete`). Дополнительные сведения о деструкторах в ссылочных типах см. в разделе [деструкторы и методы завершения в разделе: определение и использование классов и структур (C + +/ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
 Оператор присваивания, созданные компилятором выполняются обычные правила standard C++ со следующими дополнениями.  
  
-   Все данные нестатических членов, тип которого является дескриптором ссылочного типа будет shallow скопированный (рассматриваются как нестатические данные-член, тип которого является указателем).  
  
-   Любой член нестатических данных, тип которого является типом значения, будет неполной копируются.  
  
-   Любой член нестатических данных, тип которого является экземпляр ссылочного типа будет вызывать вызов конструктора копирования ссылочного типа.  
  
 Компилятор также предоставляет `%` унарный оператор для преобразования экземпляра ссылочного типа, созданные с помощью семантики стека к его базовому типу дескриптора.  
  
 Следующие типы ссылок не доступны для использования с семантикой стека:  
  
-   [delegate (расширения компонентов C++)](../windows/delegate-cpp-component-extensions.md)  
  
-   [Массивы](../windows/arrays-cpp-component-extensions.md)  
  
-   <xref:System.String>  
  
## <a name="example"></a>Пример  
  
### <a name="description"></a>Описание:  
 В следующем образце кода показано, как объявить экземпляров ссылочных типов в соответствии с семантикой стека, как оператор присваивания и работает конструктор копирования и каким образом выполняется инициализация отслеживаемую ссылку со ссылочным типом, созданных с помощью семантики стека.  
  
### <a name="code"></a>Код  
  
```  
// stack_semantics_for_reference_types.cpp  
// compile with: /clr  
ref class R {  
public:  
   int i;  
   R(){}  
  
   // assignment operator  
   void operator=(R% r) {  
      i = r.i;  
   }  
  
   // copy constructor  
   R(R% r) : i(r.i) {}  
};  
  
void Test(R r) {}   // requires copy constructor  
  
int main() {  
   R r1;  
   r1.i = 98;  
  
   R r2(r1);   // requires copy constructor  
   System::Console::WriteLine(r1.i);  
   System::Console::WriteLine(r2.i);  
  
   // use % unary operator to convert instance using stack semantics  
   // to its underlying handle  
   R ^ r3 = %r1;  
   System::Console::WriteLine(r3->i);  
  
   Test(r1);  
  
   R r4;  
   R r5;  
   r5.i = 13;  
   r4 = r5;   // requires a user-defined assignment operator  
   System::Console::WriteLine(r4.i);  
  
   // initialize tracking reference  
   R % r6 = r4;  
   System::Console::WriteLine(r6.i);  
}  
```  
  
### <a name="output"></a>Вывод  
  
```  
98  
98  
98  
13  
13  
```  
  
## <a name="see-also"></a>См. также  
 [Классы и структуры](../windows/classes-and-structs-cpp-component-extensions.md)