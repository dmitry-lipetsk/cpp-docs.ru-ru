---
title: "Спецификатор переопределения | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 677a6a0e0107f3ed0d0dc402f36e9d6dd4505c7f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="override-specifier"></a>Спецификатор override
Ключевое слово `override` можно использовать для обозначения функций-членов, переопределяющих виртуальную функцию в базовом классе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
function-declaration override;  
```  
  
## <a name="remarks"></a>Примечания  
 Ключевое слово `override` является контекстным и имеет специальное значение, только если используется после объявления функции-члена; в противном случае оно не является зарезервированным ключевым словом.  
  
## <a name="example"></a>Пример  
 С помощью `override` можно избежать случайного поведения наследования в коде. В следующем примере показано, в какой ситуации без использования `override` поведение функции-члена производного класса может быть случайным. Компилятор не выдает ошибки при использовании этого кода.  
  
```cpp  
class BaseClass  
{  
    virtual void funcA();  
    virtual void funcB() const;  
    virtual void funcC(int = 0);  
    void funcD();  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void funcA(); // ok, works as intended  
  
    virtual void funcB(); // DerivedClass::funcB() is non-const, so it does not  
                          // override BaseClass::funcB() const and it is a new member function  
  
    virtual void funcC(double = 0.0); // DerivedClass::funcC(double) has a different  
                                      // parameter type than BaseClass::funcC(int), so  
                                      // DerivedClass::funcC(double) is a new member function  
  
};  
  
```  
  
 При использовании `override` компилятор создает ошибки вместо того, чтобы автоматически создавать новые функции-члены.  
  
```cpp  
class BaseClass  
{  
    virtual void funcA();  
    virtual void funcB() const;  
    virtual void funcC(int = 0);  
    void funcD();  
};  
  
class DerivedClass: public BaseClass  
{  
    virtual void funcA() override; // ok  
  
    virtual void funcB() override; // compiler error: DerivedClass::funcB() does not   
                                   // override BaseClass::funcB() const  
  
    virtual void funcC( double = 0.0 ) override; // compiler error:   
                                                 // DerivedClass::funcC(double) does not   
                                                 // override BaseClass::funcC(int)  
  
    void funcD() override; // compiler error: DerivedClass::funcD() does not   
                           // override the non-virtual BaseClass::funcD()  
};  
  
```  
  
 Чтобы указать функции не может быть переопределен и не может быть унаследован классами, используйте [окончательного](../cpp/final-specifier.md) ключевое слово.  
  
## <a name="see-also"></a>См. также  
 [Спецификатор final](../cpp/final-specifier.md)   
 [Ключевые слова](../cpp/keywords-cpp.md)   
 