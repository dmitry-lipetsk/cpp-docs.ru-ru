---
title: "Общие сведения о трансляции файлов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- file translation [C++], about file translation
- translation [C++]
- translation phases
- files [C++], translation
- programs [C++], lexical conventions of
- preprocessing translation phase
ms.assetid: 5036c7b7-ccff-4e2c-b052-a9ea6c71af87
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a088d2da30aa77f477f3f6e5064b6b98170e953b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-file-translation"></a>Общие сведения о трансляции файлов
Программы на языке C++ подобно программам на языке C состоят из одного или нескольких файлов. Каждый из этих файлов преобразуется в указанном ниже концептуальном порядке (реальный порядок соответствует правилу "как если бы": преобразование должно происходить так, как если бы соблюдался следующий порядок действий).  
  
1.  Лексический анализ. На этом этапе преобразования сопоставляются символы, обрабатываются триграфы, соединяются строки и выполняется разбивка на лексемы.  
  
2.  Предварительная обработка. Этом этапе преобразования вводятся вспомогательные исходные файлы ссылается `#include` директивы, обрабатывает «строковый» и «преобразования в символы» директивы и выполняет маркер вставки и расширение макроса (см. [директивы препроцессора](../preprocessor/preprocessor-directives.md) в *справочника по препроцессору* для получения дополнительной информации). Результат этапа предварительной обработки — последовательность токенов, которые в совокупности определяют "запись преобразования".  
  
     Директивы препроцессора всегда начинаются со знака решетки (**#**) символ (то есть, первый непробельный символ в строке должен быть знак решетки). В строке может присутствовать только одна директива препроцессора. Пример:  
  
    ```  
    #include <iostream>  // Include text of iostream in   
                         //  translation unit.  
    #define NDEBUG       // Define NDEBUG (NDEBUG contains empty   
                         //  text string).  
    ```  
  
3.  Создание кода. На этом этапе преобразования токены, созданные на этапе предварительной обработки, используются для создания объектного кода.  
  
     Выполняется синтаксическая и семантическая проверка исходного кода.  
  
 В разделе [этапы преобразования](../preprocessor/phases-of-translation.md) в *справочника по препроцессору* для получения дополнительной информации.  
  
 Препроцессор C++ — это строгое надмножество препроцессора ANSI C, но имеет ряд отличий. Ниже указано несколько различий между препроцессорами ANSI C и C++.  
  
-   Поддерживаются однострочные комментарии. В разделе [комментарии](../cpp/comments-cpp.md) для получения дополнительной информации.  
  
-   Один предустановленный макрос **__cplusplus**, определяется только для C++. В разделе [предустановленные макросы](../preprocessor/predefined-macros.md) в *справочника по препроцессору* для получения дополнительной информации.  
  
-   Препроцессор C не распознает операторы C++: **.\*** ,  **-> \*** , и `::`. В разделе [операторы](../cpp/cpp-built-in-operators-precedence-and-associativity.md) и [выражений](../cpp/expressions-cpp.md), Дополнительные сведения об операторах.  
  
## <a name="see-also"></a>См. также  
 [Лексические соглашения](../cpp/lexical-conventions.md)