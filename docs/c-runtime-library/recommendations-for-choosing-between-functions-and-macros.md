---
title: "Рекомендации по выбору между функциями и макросами | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.functions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "функции [CRT], или макросы"
  - "макросы, или функции"
ms.assetid: 18a633d6-cf1c-470c-a649-fa7677473e2b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Рекомендации по выбору между функциями и макросами
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Большинство подпрограмм библиотеки времени выполнения \- это скомпилированные или собранные функции, но некоторые подпрограммы реализованы в виде макросов.  Если файл заголовка объявляет и функцию, и макрос для подпрограммы, макроса имеет приоритет, поскольку он всегда отображается после объявления функций.  При вызове процедуры, которая реализована и как функция, и как макрос можно заставить компилятор использовать функции двумя способами:  
  
-   Заключить имя подпрограммы в скобки.  
  
    ```  
    #include <ctype.h>  
    a = _toupper(a);    // Use macro version of toupper.  
    a = (_toupper)(a);  // Force compiler to use   
                        // function version of toupper.  
    ```  
  
-   Отменить определения макросов с помощью директивы `#undef`:  
  
    ```  
    #include <ctype.h>  
    #undef _toupper  
    ```  
  
 Если необходимо выбрать между реализацией библиотечной подпрограммы в виде функции или макроса, рассмотрите следующие соглашения:  
  
-   **Скорость и размер** Основным преимуществом использования макросов является более быстрое время выполнения.  Во время предварительной обработки, макрос разворачивается \(заменяется его определением\) каждый раз, когда он используется.  Определение функции выполняется только один раз независимо от количества вызовов.  Макросы могут увеличить размер кода, но не имеют нагрузку, связанную с вызовами функции.  
  
-   **Вычисление функции** Функция вычисляет по адресу; а макрос нет.  Таким образом, нельзя использовать имя макроса в контекстах, где требуется указатель.  Например, можно объявить указатель на функцию, но не указатель на макрос.  
  
-   **Проверка типов** При объявлении функции компилятор может проверить типы аргументов.  Поскольку невозможно объявить макрос, компилятор не может проверить типы аргументов макроса; хотя он может проверить количество аргументов, передаваемые макросу.  
  
## См. также  
 [Особенности библиотеки CRT](../c-runtime-library/crt-library-features.md)