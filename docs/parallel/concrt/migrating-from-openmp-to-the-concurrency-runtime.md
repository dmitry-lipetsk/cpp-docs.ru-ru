---
title: "Переход от OpenMP к среде выполнения с параллелизмом | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Concurrency Runtime, migrating from OpenMP
- OpenMP, migrating to the Concurrency Runtime
ms.assetid: 9bab7bb1-e45d-44b2-8509-3b226be2c93b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 65359e76e036a0d8d33de2de9f6c96c6425d2152
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="migrating-from-openmp-to-the-concurrency-runtime"></a>Переход от OpenMP к среде выполнения с параллелизмом
Среда выполнения с параллелизмом позволяет использовать самые разные модели программирования. Эти модели могут перекрываться с моделями других библиотек или дополнять их. Документы в этом разделе сравнения [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp) в среду выполнения с параллелизмом и приводятся примеры способов миграции существующего кода OpenMP для использования среды выполнения с параллелизмом.  
  
 Модель программирования OpenMP определяется открытым стандартом и обладает четко определенными привязками к языкам программирования Fortran и C/C++. OpenMP версий 2.0 и 2.5, поддерживаемых компилятором Visual C++, хорошо подходят для параллельные алгоритмы, которые имеют цикличности; то есть они выполнения параллельных перебора массива данных. OpenMP 3.0 поддерживает итерации задачи не только итеративные задачи.  
  
 OpenMP работает наиболее эффективно при предопределенной степени параллелизма и соответствующем уровне доступных ресурсов в системе. Модель OpenMP является особенно хорошо подходит для высокопроизводительных вычислительных систем, где очень крупные вычислительные задачи распределяются между вычислительных ресурсов на одном компьютере. В этом сценарии в среде оборудования обычно не меняется, и разработчик может рассчитывать на монопольный доступ к вычислительным ресурсам при выполнении алгоритма.  
  
 Тем не менее менее ограниченных вычислительных средах может не быть хорошо подходит для использования OpenMP. Например рекурсивные (например, алгоритм быстрой сортировки или поиска в дереве данных), тем сложнее реализовать с помощью OpenMP 2.0 и 2.5. Среда выполнения с параллелизмом дополняет возможности модели OpenMP возможностями [библиотеки асинхронных агентов](../../parallel/concrt/asynchronous-agents-library.md) и [библиотеки параллельных шаблонов](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). Библиотека асинхронных агентов поддерживает параллелизм недетализированного задач; PPL поддерживает более детализированные параллельные задачи. Среда выполнения с параллелизмом предоставляет инфраструктуру, которая требуется для выполнения операций параллельно, что можно сосредоточиться на логике приложения. Тем не менее так как среда выполнения с параллелизмом обеспечивает различные модели программирования, затраты на его планирование может быть больше, чем другие библиотеки параллелизма, например OpenMP. Таким образом рекомендуется проверить производительность добавочного при преобразовании существующего кода OpenMP для использования среды выполнения с параллелизмом.  
  
## <a name="when-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Когда следует выполнять миграцию из OpenMP в среду выполнения с параллелизмом  
 Иногда удобнее перенос существующего кода OpenMP для использования среды выполнения с параллелизмом в следующих случаях.  
  
|Cases|Преимущества среды выполнения с параллелизмом|  
|-----------|-------------------------------------------|  
|Требуется расширяемой платформой параллельного программирования.|Многие функции в среде выполнения с параллелизмом можно расширить. Кроме того, можно объединять существующие функции для создания новых. Поскольку OpenMP основывается на директивы компилятора, его невозможно легко расширить.|  
|Приложения получают преимущества от совместной блокировки.|Когда задача блокируется, так как он требует ресурс, который еще не доступен, среда выполнения с параллелизмом можно выполнить другие задачи, пока первая задача ожидает ресурс.|  
|Приложение очень выгодно динамической балансировки нагрузки.|Среда выполнения с параллелизмом использует алгоритм планирования, который настраивает распределения вычислительных ресурсов при изменении рабочей нагрузки. В OpenMP когда планировщик выделяет вычислительные ресурсы параллельной области, это выделение ресурсов изменяется до окончания вычисления.|  
|Вам требуется поддержка обработки исключений.|PPL позволяет перехватывать исключения как внутри, так и за пределами параллельной области или цикла. В OpenMP необходимо обрабатывать исключение внутри параллельной области или цикла.|  
|Требуется механизм отмены.|PPL позволяет приложениям отменять отдельные задачи и деревья параллельной работы. В OpenMP приложение должно реализовывать собственные механизмы отмены.|  
|Требуется параллельный код завершения в другом контексте, из которого он запускается.|Среда выполнения с параллелизмом позволяет запустить задачу в одном контексте и затем дождаться выполнения или отменить эту задачу в другом контексте. В OpenMP вся параллельная работа необходимо завершить в контекст, из которого он запускается.|  
|Вам требуется расширенная поддержка отладки.|Visual Studio предоставляет **Параллельные стеки** и **параллельные задачи** windows, можно упростить отладку многопоточных приложений.<br /><br /> Дополнительные сведения об отладке поддержка среды выполнения с параллелизмом см. в разделе [использование окна задач](/visualstudio/debugger/using-the-tasks-window), [с помощью окна "Параллельные стеки"](/visualstudio/debugger/using-the-parallel-stacks-window), и [Пошаговое руководство: отладка параллельного Приложение](/visualstudio/debugger/walkthrough-debugging-a-parallel-application).|  
  
## <a name="when-not-to-migrate-from-openmp-to-the-concurrency-runtime"></a>Когда не следует выполнять миграцию из OpenMP в среду выполнения с параллелизмом  
 Следующие варианты описываются при его могут не подходить для миграции существующего кода OpenMP для использования среды выполнения с параллелизмом.  
  
|Cases|Объяснение|  
|-----------|-----------------|  
|Приложение уже удовлетворяет вашим требованиям.|Если вы удовлетворены производительности приложения и поддержка отладки, миграции не следует.|  
|В параллельных циклов выполняют немного работы.|Затраты на планировщик задач среды выполнения с параллелизмом не может компенсировать преимущества выполнения основной части цикла в параллельном режиме, особенно в том случае, если тело цикла относительно невелико.|  
|Приложение написано на языке C.|Поскольку среда выполнения с параллелизмом использует множество функций C++, может оказаться подходящего при написании кода, который позволяет полностью использовать приложение C не может.|  
  
## <a name="related-topics"></a>См. также  
 [Практическое руководство. Преобразование параллельного цикла for OpenMP для использования среды выполнения с параллелизмом](../../parallel/concrt/how-to-convert-an-openmp-parallel-for-loop-to-use-the-concurrency-runtime.md)  

 Простой цикл, использующий OpenMP [параллельных](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel) и [для](../../parallel/openmp/reference/for-openmp.md) директивы, показано, как преобразовать для использования среды выполнения с параллелизмом [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) алгоритм.  

  
 [Практическое руководство. Преобразование цикла OpenMP, использующего отмену для использования среды выполнения с параллелизмом](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md)  
 Учитывая OpenMP [параллельных](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[для](../../parallel/openmp/reference/for-openmp.md) цикл, который не требует всех итераций для выполнения, показано, как преобразовать для использования механизма отмены среды выполнения с параллелизмом.  
  
 [Практическое руководство. Преобразование цикла OpenMP, использующего обработку исключений для использования среды выполнения с параллелизмом](../../parallel/concrt/convert-an-openmp-loop-that uses-exception-handling.md)  
 Учитывая OpenMP [параллельных](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[для](../../parallel/openmp/reference/for-openmp.md) цикл, который выполняет обработку исключений, показано, как преобразовать для использования механизма обработки исключений среды выполнения с параллелизмом.  
  
 [Практическое руководство. Преобразование цикла OpenMP, использующего переменную сокращения для использования среды выполнения с параллелизмом](../../parallel/concrt/convert-an-openmp-loop-that-uses-a-reduction-variable.md)  
 Учитывая OpenMP [параллельных](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[для](../../parallel/openmp/reference/for-openmp.md) цикл, использующий [сокращения](../../parallel/openmp/reference/reduction.md) предложение, показано, как преобразовать для использования среды выполнения с параллелизмом.  
  
## <a name="see-also"></a>См. также  
 [Среда выполнения с параллелизмом](../../parallel/concrt/concurrency-runtime.md)   
 [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)   
 [Библиотека параллельных шаблонов](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Библиотека асинхронных агентов](../../parallel/concrt/asynchronous-agents-library.md)

