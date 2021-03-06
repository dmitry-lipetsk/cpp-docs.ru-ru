---
title: "Назначение атрибутов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: attributes [C++], about attributes
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ed20c29d017527d5c2ce0b0c5ab8053fc75dc6ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="purpose-of-attributes"></a>Назначение атрибутов
Атрибуты расширения C++ в направлениях в настоящее время невозможно без нарушения классический структуру языка. Атрибуты позволяют поставщикам (отдельных библиотек DLL) для расширения функциональных возможностей языка динамически. Основная цель атрибутов является упрощение разработки COM-компонентов, кроме увеличить уровень производительности разработчика компонента. Атрибуты могут применяться к практически любой конструкции C++, таких как классы, члены данных или функции-члены. Ниже приведен выделения преимущества этой новой технологии.  
  
-   Предоставляет знакомые и простые соглашения о вызовах.  
  
-   Использует вставлять код, который, в отличие от макросы, распознаваемые отладчиком.  
  
-   Позволяет легко производным от базовых классов не сведения о реализации утомительным.  
  
-   Заменяет большой объем кода языка IDL, предусмотренного COM-компонента с нескольких четкими атрибутов.  
  
 Например, для реализации простых событий приемника для универсального класса ATL, можно применить [event_receiver](../windows/event-receiver.md) атрибут для определенного класса, например `CMyReceiver`. **Event_receiver** атрибут затем компилируется компилятором Visual C++, который вставляет в объектный файл соответствующего кода.  
  
```  
[event_receiver(com)]  
class CMyReceiver   
{  
   void handler1(int i) { ... }  
   void handler2(int i, float j) { ... }  
}  
```  
  
 Затем можно настроить **CMyReceiver** методы `handler1` и `handler2` для обработки событий (с помощью встроенной функции [__hook](../cpp/hook.md)) из источника события, которую можно создать с помощью [event_source](../windows/event-source.md).  
  
## <a name="see-also"></a>См. также  
 [Основные понятия](../windows/attributed-programming-concepts.md)