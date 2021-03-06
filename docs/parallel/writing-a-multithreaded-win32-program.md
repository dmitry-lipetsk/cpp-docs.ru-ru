---
title: "Написание многопотоковой программы Win32 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- thread stacks [C++]
- resources [C++], multithreading
- stacks [C++]
- shared resources [C++]
- threading [C++], sharing common resources
- multithreading [C++], thread stacks
- multithreading [C++], sharing common resources
- mutual exclusion [C++]
- communications [C++], between threads
- mutex [C++]
- threading [C++], thread stacks
ms.assetid: 1415f47d-417f-4f42-949b-946fb28aab0e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4ede0e6dc1740f93f4905dc69b1927aee0d1a7ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="writing-a-multithreaded-win32-program"></a>Написание многопотоковой программы Win32
При написании программы с несколькими потоками, необходимо скоординировать их поведение и [использования ресурсов программы](#_core_sharing_common_resources_between_threads). Кроме того, необходимо убедиться, что каждый поток получает [собственный стек](#_core_thread_stacks).  
  
##  <a name="_core_sharing_common_resources_between_threads"></a>Общий доступ к ресурсам между потоками  
  
> [!NOTE]
>  Аналогичные сведения с точки зрения MFC см. в разделе [Многопоточность: советы про программированию](../parallel/multithreading-programming-tips.md) и [Многопоточность: использование классов синхронизации](../parallel/multithreading-when-to-use-the-synchronization-classes.md).  
  
 Каждый поток имеет собственный стек и регистрирует свою собственную копию ЦП. Другие ресурсы, такие как файлы, статические данные и память в куче, являются общими для всех потоков в процессе. Потоки, использующие общие ресурсы должны быть синхронизированы. Win32 предоставляет несколько способов синхронизации ресурсов, включая семафоры, критические секции, события и мьютексы.  
  
 Когда несколько потоков обращаются статические данные, необходимо указать программы для возможные конфликты. Рассмотрим программу, когда один поток обновляет статические данные структура, содержащая *x*,*y* координаты для элементов для отображения в другом потоке. Если поток обновления изменяет *x* координации и прерывается до изменения *y* координат, отображение во втором потоке может быть выполнено до *y* координаты обновлены. Элемент может быть отображен в неправильном месте. Этой проблемы можно избежать, если использовать семафоры для управления доступом к структуре.  
  
 Мьютекс (сокращение для *сокращение от mut*ual *ex*clusion) — это способ взаимодействия между потоками и процессами, которые выполняются асинхронно. Обычно эта связь используется для координации действий нескольких потоков или процессов, обычно с помощью управления доступом к общему ресурсу, блокировка и снятие блокировки ресурса. Чтобы устранить эту проблему *x*,*y* проблему обновления координат, поток обновления должен задать мьютекс, указывающее, что структура данных уже используется перед выполнением обновления. Он сбросит мьютекс после обе координаты будут обработаны. Поток отображения должен дождаться сброса мьютекса перед обновлением экрана. Этот процесс ожидания мьютекса часто называют блокировкой мьютекса, поскольку процесс блокируется и не может выполняться до очищает объект взаимного исключения.  
  
 В программе Bounce.c на [Пример многопоточной программы на языке C](../parallel/sample-multithread-c-program.md) используется мьютекс `ScreenMutex` для управления обновлениями экрана. Каждый раз, один из потоков отображения готов к вывод на экран, он вызывает **WaitForSingleObject** с дескриптором для `ScreenMutex` констант и **БЕСКОНЕЧНЫЙ** указывает, что  **WaitForSingleObject** вызова должны блокироваться при мьютекса, а также время ожидания не истекает. Если `ScreenMutex` сброшен, функция ожидания устанавливает объект взаимного исключения, поэтому другие потоки не смогут взаимодействовать с дисплеем и продолжает выполнение потока. В противном случае — поток блокируется, пока не очищает объект взаимного исключения. После завершения обновления дисплея поток освобождает мьютекс путем вызова **ReleaseMutex**.  
  
 На экране отображается и статические данные — ресурсы, требующие аккуратного управления. Например приложение может иметь несколько потоков, доступ к тому же файлу. Так как другой поток может перемещать указатель файла, каждый поток должен сбрасывать указатель файла до чтения или записи. Кроме того каждый поток должен убедитесь, что не высвобождены между устанавливает указатель и временем, он обращается к файлу. Эти потоки должны использовать семафор для управления доступом к файлу с помощью файла **WaitForSingleObject** и **ReleaseMutex** вызовов. В следующем примере кода показан этот принцип.  
  
```  
HANDLE    hIOMutex= CreateMutex (NULL, FALSE, NULL);  
  
WaitForSingleObject( hIOMutex, INFINITE );  
fseek( fp, desired_position, 0L );  
fwrite( data, sizeof( data ), 1, fp );  
ReleaseMutex( hIOMutex);  
```  
  
##  <a name="_core_thread_stacks"></a>Стеки потоков  
 Все пространство стека приложения по умолчанию назначается первый поток выполнения, которая называется поток 1. В результате необходимо указать, какой объем памяти, выделяемой для стека в каждый дополнительный поток программы требуется. Операционная система выделяет пространство дополнительных стека для потока, при необходимости, но необходимо указать значение по умолчанию.  
  
 Первый аргумент в `_beginthread` является указателем на **BounceProc** функции, которая выполняет потоки. Второй аргумент задает размер стека по умолчанию для потока. Последний аргумент является идентификатором, передаваемое **BounceProc**. **BounceProc** использует этот идентификатор для генератора случайных чисел, а также для выбора атрибута цвета потока и отображения символов.  
  
 Потоки, которые выполняют вызовы библиотеки времени выполнения C или API-интерфейса Win32 необходимо разрешить достаточного пространства стека для библиотеки и функций API. C `printf` функции требуется более 500 байт пространство стека, и необходимо 2 КБ места стека при вызове подпрограммы Win32 API.  
  
 Так как каждый поток имеет собственный стек, можно избежать потенциальных конфликтов за элементов данных, используя в качестве меньше статических данных возможно. Создайте программу так, чтобы использовать автоматические переменные стека для всех данных, которые могут быть закрытыми для потока. Только глобальные переменные в программе Bounce.c являются мьютексы и переменные, которые не изменяются после их инициализации.  
  
 Win32 также предоставляет хранилище локального потока (TLS) для хранения данных для каждого потока. Дополнительные сведения см. в разделе [локальное хранилище потока (TLS)](../parallel/thread-local-storage-tls.md).  
  
## <a name="see-also"></a>См. также  
 [Реализация многопоточности на языке C с помощью функций Win32](../parallel/multithreading-with-c-and-win32.md)