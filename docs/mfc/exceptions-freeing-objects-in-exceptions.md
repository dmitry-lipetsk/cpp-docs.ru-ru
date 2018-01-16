---
title: "Исключения: Высвобождение объектов в исключениях | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a422347e319fabbd91f20e0ebf7897865f1ca4c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Исключения. Высвобождение объектов в исключениях
В этой статье объясняется необходимость и способ освобождение объектов при возникновении исключения. Ниже приведен список разделов.  
  
-   [Обработка исключения локально](#_core_handling_the_exception_locally)  
  
-   [Создание исключений после уничтожения объектов](#_core_throwing_exceptions_after_destroying_objects)  
  
 Исключений, создаваемых средой или с вашего приложения прерываний нормального выполнения программы. Таким образом очень важно отслеживать закрыть объекты, чтобы может правильно реализации их в случае, если возникает исключение.  
  
 Существует два основных способа это сделать.  
  
-   Обработка исключений локально с помощью **повторите** и **перехватывать** ключевые слова, затем удалите все объекты с помощью одного оператора.  
  
-   Удаление любого объекта в **перехватывать** блок до исключения за пределы блока для дальнейшей обработки.  
  
 Эти два подхода представлены ниже как решения проблемы следующим образом:  
  
 [!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]  
  
 Как написано выше, `myPerson` не будут удалены, если исключение вызывается `SomeFunc`. Выполнение переходит непосредственно к Далее внешнему обработчику исключений, обход при выходе из обычной функции и код, который удаляет объект. Указатель на объект выходит за пределы области, когда исключение покидает функции и никогда не будут восстановлены память, занимаемую объектом, при условии, что программа выполняется. Это имеет место утечка памяти; она будет обнаружена с помощью диагностики памяти.  
  
##  <a name="_core_handling_the_exception_locally"></a>Обработка исключения локально  
 **Try/catch** парадигма предоставляет защитного метода программирования помогает избежать утечки памяти и обеспечивая уничтожение объектов при возникновении исключения. Например пример, приведенный ранее в этом разделе можно переписать следующим образом:  
  
 [!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]  
  
 В этом примере задает обработчика исключений для перехвата исключения и обрабатывать его локально. Затем выходит из функции, как правило и удаляет объект. Важный аспект этого примера заключается в том, что установлен контекст для перехвата исключения с **try/catch** блоков. Без рамки локальные исключения функция никогда не будет знать, что исключение было исключение и не должны иметь возможность выйти в обычном режиме и удалите этот объект.  
  
##  <a name="_core_throwing_exceptions_after_destroying_objects"></a>Создание исключений после уничтожения объектов  
 Другой способ обработки исключений — для передачи их далее внешнего контекста обработки исключений. В вашей **перехватывать** блока, можно выполнить некоторые операции очистки локально выделенных объектов и затем вызвать исключение для дальнейшей обработки.  
  
 Вызывающая функция может или не может потребоваться освободить объекты кучи. Если функция также следует освобождать кучи объекта до создания исключения, а затем перед возвратом в обычном случае функция всегда освобождает кучи объекта. С другой стороны Если функция не освобождает объект перед возвращением в обычном случае обычным образом, затем необходимо решить, на основе случая должно быть освобождена кучи объекта.  
  
 В следующем примере показан способ локально выделенные объекты могут быть очищены:  
  
 [!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]  
  
 Механизм обработки исключений, автоматически освобождает объекты фрейма; объект кадра также деструктора.  
  
 При вызове функции, которые могут вызывать исключения, можно использовать **try/catch** блоки перехватывать исключения, и иметь возможность удалить все объекты, которые вы создали. В частности Имейте в виду, что многие функции MFC могут вызывать исключения.  
  
 Дополнительные сведения см. в разделе [исключений: исключения перехвата и удаление](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>См. также  
 [Обработка исключений](../mfc/exception-handling-in-mfc.md)
