---
title: "Локальное хранилище потока (TLS) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- multithreading [C++], Thread Local Storage
- TLS [C++]
- threading [C++], Thread Local Storage
- storing thread-specific data
- thread attribute
- Thread Local Storage [C++]
ms.assetid: 80801907-d792-45ca-b776-df0cf2e9f197
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 47e6be3645e03892d17e45256a5a003d982d973f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="thread-local-storage-tls"></a>Локальное хранилище потока (TLS)
Локальное хранилище потока (TLS) — это механизм, с помощью которого каждый поток в указанном многопоточном процессе может выделять расположения для хранения данных определенного потока. Динамически данные привязки (во время выполнения) определенного потока поддерживаются посредством TLS API ([TlsAlloc](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686801), [TlsGetValue](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686812), [TlsSetValue](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686818), и [TlsFree](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686804)). Дополнительные сведения о реализации локального хранилища потока в Windows см. в разделе [локальное хранилище потока (Windows)](https://msdn.microsoft.com/en-us/library/windows/desktop/ms686749\(v=vs.85\).aspx).  Win32 и компилятор Visual C++ теперь поддерживают статически привязываемые (во время загрузки) данные потока, в дополнение к существующей реализации API.  
  
##  <a name="_core_compiler_implementation_for_tls"></a>Реализация компилятора для TLS  
 **C ++ 11:** `thread_local` спецификатор класса хранения — рекомендуемый способ указать локальное хранилище потока для объектов и членов класса. Дополнительные сведения см. в разделе [классы хранения (C++)](../cpp/storage-classes-cpp.md).  
  
 Visual C++ также предоставляет атрибут систем Майкрософт, [поток](../cpp/thread.md), как расширенный модификатор класса хранилища. Используйте `__declspec` ключевое слово для объявления **поток** переменной. В следующем примере кода показано, как объявлять целочисленную локальную переменную потока и инициализировать её некоторым значением:  
  
```  
__declspec( thread ) int tls_i = 1;  
```  
  
## <a name="rules-and-limitations"></a>Правила и ограничения  
 При объявлении статистически связываемых локальных объектов и переменных потока необходимо соблюдать следующие рекомендации. Эти правила применяются и к [поток](../cpp/thread.md)и в большинстве случаев также [thread_local](../cpp/storage-classes-cpp.md):  
  
-   Атрибут `thread` может применяться только к объявлениям и определениям классов и данных. Его невозможно использовать в объявлениях или определениях функций. Например, следующий код вызовет ошибку компиляции:  
  
    ```  
  
    __declspec( thread )void func();     // This will generate an error.  
    ```  
  
-   Модификатор `thread` может указываться только в элементах данных с экстентом `static`. К ним относятся глобальные объекты данных (`static` и `extern`), локальные статические объекты и статические элементы данных классов C++. Автоматические объекты данных не могут объявляться с атрибутом `thread`. Следующий код вызывает ошибки компилятора:  
  
    ```  
  
    void func1()  
    {  
        __declspec( thread )int tls_i;            // This will generate an error.  
    }  
  
    int func2(__declspec( thread )int tls_i )    // This will generate an error.  
    {  
        return tls_i;  
    }  
    ```  
  
-   В объявлениях и определениях локального объекта потока должен указываться атрибут `thread`. Например, следующий код вызывает ошибку:  
  
    ```  
    #define Thread  __declspec( thread )  
    extern int tls_i;        // This will generate an error, since the  
    int __declspec( thread )tls_i;        // declaration and definition differ.  
    ```  
  
-   Атрибут `thread` не может использоваться в качестве модификатора типа. Например, следующий код вызовет ошибку компиляции:  
  
    ```  
    char __declspec( thread ) *ch;        // Error  
    ```  
  
-   Так как объявление объектов, использующих атрибут `thread`, разрешено, следующие два примера семантически эквивалентны:  
  
    ```  
  
    __declspec( thread ) class B  
    {  
    // Code  
    } BObject;  // OK--BObject is declared thread local.  
  
    class B  
    {  
    // Code  
    };  
    __declspec( thread ) B BObject;  // OK--BObject is declared thread local.  
    ```  
  
-   Адрес локального объекта потока не считается постоянным, и любое выражение с таким адресом не будет константным. В стандартном языке C это вызвано запретом на использование адреса локальной переменной потока в качестве инициализатора объекта или указателя. Например, компилятор C отмечает следующий код как ошибочный:  
  
    ```  
  
    __declspec( thread )int tls_i;  
    int *p = &tls_i;       //This will generate an error in C.  
    ```  
  
     Это ограничение не относится к C++. Так как C++ допускает динамическую инициализацию всех объектов, можно инициализировать объект с помощью выражения, которое использует адрес локальной переменной потока. Это делается так же, как и при построении локальных объектов потока. Например, приведенный выше код не вызывает ошибку при компиляции в файле кода C++. Обратите внимание, что адрес локальной переменной потока допустим, только если поток, из которого взят адрес, все еще существует.  
  
-   В стандартном языке C разрешена инициализация объекта или переменной с помощью выражения, предусматривающего ссылку на себя, но только для объектов нестатической области памяти. Хотя в C++ обычно разрешена такая динамическая инициализация объекта выражениями с ссылкой на себя, данный тип инициализации не допускается в отношении локальных объектов потока. Пример:  
  
    ```  
    __declspec( thread )int tls_i = tls_i;                // Error in C and C++   
    int j = j;                               // OK in C++, error in C  
    __declspec( thread )int tls_i = sizeof( tls_i )       // Legal in C and C++  
    ```  
  
     Обратите внимание, что выражение `sizeof`, включающее инициализируемый объект, не представляет ссылку на себя и допустимо как в C, так и в C++.  
  
     C++ не допускает такой динамической инициализации данных потока из-за возможных будущих улучшений локального хранилища потока.  
  
-   В операционных системах Windows до [!INCLUDE[wiprlhext](../c-runtime-library/reference/includes/wiprlhext_md.md)] `__declspec`(thread) имеет некоторые ограничения. Если библиотека DLL объявляет любые данные или объекты как `__declspec`(thread), это может привести к сбою защиты при динамической загрузке. После загрузки библиотеки DLL с [LoadLibrary](http://msdn.microsoft.com/library/windows/desktop/ms684175), сбой в системе всякий раз, когда код ссылается на `__declspec`данных (thread). Поскольку пространство глобальных переменных для потока выделяется во время выполнения, размер данного пространства основан на расчете требований приложению, а также требований всех библиотек DLL, которые привязываются статически. При использовании `LoadLibrary` невозможно расширить это пространство, чтобы объявлять локальные переменные потока с помощью `__declspec`(thread). Используйте API-интерфейсы TLS, например [TlsAlloc](http://msdn.microsoft.com/library/windows/desktop/ms686801), библиотеки DLL, чтобы выделить TLS, если библиотека DLL может загружаться с помощью `LoadLibrary`.  
  
## <a name="see-also"></a>См. также  
 [Реализация многопоточности на языке C с помощью функций Win32](../parallel/multithreading-with-c-and-win32.md)   
