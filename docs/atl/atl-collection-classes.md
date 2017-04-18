---
title: "Классы коллекций ATL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "классы коллекций"
  - "классы коллекций, сведения о классах коллекций"
  - "классы коллекций, выбор"
  - "ConstructElements - функция"
  - "CTraits - классы"
  - "DestructElements - функция"
  - "SerializeElements - функция"
  - "traits - классы"
ms.assetid: 4d619d46-5b4e-41dd-b9fd-e86b1fbc00b5
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Классы коллекций ATL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Библиотеки ATL предоставляет множество классов для хранения и доступа к данным.  , Какому классу решено использовать зависит от нескольких факторов, включая:  
  
-   Количество данных, которое будет храниться  
  
-   Эффективность по производительности в доступа к данным  
  
-   Возможность доступа к данным индексом или ключом  
  
-   Данные упорядочиваются как  
  
-   Личное параметры  
  
## Малые классы коллекций  
 Библиотеки ATL предоставляет следующие классы массива для ведения дела с нескольких объектов.  Однако эти классы ограниченными и предназначены для использования внутри библиотеки ATL.  Не рекомендуется использовать их в программах.  
  
|Класс|Тип хранилища данных|  
|-----------|--------------------------|  
|[CSimpleArray](../atl/reference/csimplearray-class.md)|Реализует класс массива для ведения дела с нескольких объектов.|  
|[CSimpleMap](../atl/reference/csimplemap-class.md)|Реализует класс сопоставления для ведения дела с нескольких объектов.|  
  
## Классы коллекций общего назначения  
 Ниже представлена классификация массивы, списки и сопоставления " и предоставляется как общецелевая коллекция классифицирует:  
  
|Класс|Тип хранилища данных|  
|-----------|--------------------------|  
|[CAtlArray](../atl/reference/catlarray-class.md)|Реализует массив.|  
|[CAtlList](../Topic/CAtlList%20Class.md)|Реализует списка.|  
|[CAtlMap](../atl/reference/catlmap-class.md)|Реализует структуру сопоставления, посредством которого данные могут ссылаться по ключу или значению.|  
|[CRBMap](../atl/reference/crbmap-class.md)|Реализует структуру сопоставления с помощью Красн\- Черный алгоритм.|  
|[CRBMultiMap](../atl/reference/crbmultimap-class.md)|Реализует Красн\- Black multimapping структуру.|  
  
 Эти классы поглотят много ошибок программирования при использовании в отладочные построения, но для ради производительности этих проверок не выполняются в розничных построениях.  
  
## Специализированные классы коллекций  
 Более специализировать классы коллекций также предоставляются для управления указатели памяти и указатели интерфейса:  
  
|Класс|Назначение|  
|-----------|----------------|  
|[CAutoPtrArray](../atl/reference/cautoptrarray-class.md)|Предоставляет методы умных полезные при создании массива указателей.|  
|[CAutoPtrList](../atl/reference/cautoptrlist-class.md)|Предоставляет методы полезных для построения списка умных указателей.|  
|[CComUnkArray](../atl/reference/ccomunkarray-class.md)|Хранит указатели `IUnknown` и проектирует использоваться в качестве параметра к классу шаблона [IConnectionPointImpl](../Topic/IConnectionPointImpl%20Class.md).|  
|[CHeapPtrList](../atl/reference/cheapptrlist-class.md)|Предоставляет методы полезных для построения списка указателей кучи.|  
|[CInterfaceArray](../atl/reference/cinterfacearray-class.md)|Предоставляет методы, полезные при создании массива указателей интерфейса модели COM.|  
|[CInterfaceList](../Topic/CInterfaceList%20Class.md)|Предоставляет методы полезных для построения списка указателей интерфейса модели COM.|  
  
## Выбор класса коллекции  
 Каждый из доступных классов коллекций предлагает различные характеристики производительности, как показано в таблице ниже.  
  
-   Столбцы, описывающие характеристики 2 и 3 для каждого типа упорядочение и доступа.  В таблице "упорядоченная" термин означает, что порядок, в котором элементы вставляются и удалены определяет их порядок в коллекции. оно не означает, что элементы отсортированы на их содержимое.  Индексированная" термин "означает, что элементы в коллекции могут быть восстановлены индексом целого числа, как элементы в типичном массиве.  
  
-   Столбцы, 4 и 5 описывают производительность каждого типа.  В приложениях, требующих много вставок в коллекцию, скорость вставки может быть особенно важна. для других приложений, скорость поиска может оказаться важнее.  
  
-   Описывает столбец 6, позволяет ли каждая фигура повторяющиеся элементы.  
  
-   Производительность данной операции класса коллекции выражается в терминах связи между временем необходимые для завершенных операцию и количество элементов в коллекции.  Операция, принимающая количество времени, которое увеличивает линейно по мере увеличения числа увеличений элементов описано, как алгоритм o \(n\).  Напротив, при операции период времени, увеличениям менее, и по мере увеличения числа элементов увеличивает описывают алгоритм o \(log n\).  Следовательно, с точки зрения производительности, алгоритмы o \(n\) выполняют алгоритмы журнала лучше o \(n\) больше, как количество увеличений элементов.  
  
### Функции фигуры коллекции  
  
|Фигура|Упорядоченный?|Индексированный?|Insert<br /><br /> Элемент|Поиск<br /><br /> указанный элемент|Дубликат<br /><br /> элементы?|  
|------------|--------------------|----------------------|------------------------|---------------------------------|----------------------------|  
|List|Да|Нет|Быстрый \(постоянного времени\)|Медленный o \(n\)|Да|  
|Массив|Да|Int \(постоянного времени\)|Медленный o \(n\) за исключением если вставка на окончании, в котором момент варианты постоянно|Медленный o \(n\)|Да|  
|Сопоставление|Нет|Постоянным ключом \(time\)|Быстрый \(постоянного времени\)|Быстрый \(постоянного времени\)|Нет \(ключи\) да \(значение\)|  
|Красн\-Черное сопоставление|Да \(ключ\)|Ключом o \(log n\)|Быстрый o \(log n\)|Быстрый o \(log n\)|Нет|  
|Красн\-Черное Multimap|Да \(ключ\)|Ключом o \(log n\) \(несколько значений в ключ\)|Быстрый o \(log n\)|Быстрый o \(log n\)|Да \(несколько значений в ключ\)|  
  
## Использование объектов CTraits  
 Так как классы коллекций библиотеку ATL можно использовать для хранения широкий диапазон определяемых пользователем типа данных, может быть полезно иметь возможность переопределить важные функции сравнения.  Это достигается с помощью классов CTraits.  
  
 Классы CTraits аналогичны, но является более гибким, чем вспомогательные функции классов коллекций MFC; дополнительные сведения см. в разделе [Вспомогательные функции классов коллекции](../mfc/reference/collection-class-helpers.md).  
  
 При построении класс коллекции, можно указать класс CTraits.  Этот класс будет содержать код, который выполняется как операции сравнения вызываемый другими методами, которые составляют классом коллекции.  Например, если объект списка содержит собственных определяемых пользователем структуры, то можно переопределить только тест равенства для сравнения некоторые переменные членов.  Таким образом, метод find объекта списка будет работать в более полезном образом.  
  
## Пример  
  
### Код  
 [!CODE [NVC_ATL_Utilities#112](../CodeSnippet/VS_Snippets_Cpp/NVC_ATL_Utilities#112)]  
  
## Комментарии  
 Список классов CTraits см. в разделе [Классы коллекций](../Topic/Collection%20Classes.md).  
  
 Следующая диаграмма показывает иерархию класса для классов CTraits.  
  
 ![Иерархия характеристик классов коллекции](../atl/media/vctraitscollectionclasseshierarchy.png "vcTraitsCollectionClassesHierarchy")  
  
## Коллекция образцов classify  
 В следующих примерах демонстрируются классы коллекций.  
  
-   [Образец MMXSwarm](../top/visual-cpp-samples.md)  
  
-   [Образец DynamicConsumer](../top/visual-cpp-samples.md)  
  
-   [Образец UpdatePV](../top/visual-cpp-samples.md)  
  
-   [Образец бегущей строки](../top/visual-cpp-samples.md)  
  
## См. также  
 [Основные понятия](../atl/active-template-library-atl-concepts.md)   
 [Классы коллекций](../Topic/Collection%20Classes.md)