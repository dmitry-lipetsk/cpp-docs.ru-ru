---
title: "#<a name=\"define-directive-cc--microsoft-docs\"></a>#define-директива (C/C++) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#define'
dev_langs: C++
helpviewer_keywords:
- define directive (#define), syntax
- preprocessor, directives
- define directive (#define)
- '#define directive, syntax'
- '#define directive'
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a42b1b823ac69ba9a92535076ba8ec45f6c9710d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="define-directive-cc"></a>Директива #define (C/C++)
`#define` Создает *макрос*, который представляет собой взаимосвязь или параметризованного идентификатора со строкой токена. После определения макроса компилятор может подставить строку токена для каждого обнаруженного идентификатора в исходном файле.  
  
## <a name="syntax"></a>Синтаксис  
 `#define`*идентификатор* *строке токена*необязательно  
  
 `#define`*идентификатор* `(` *идентификатор*необ`,`*...*  `,` *идентификатор*необ`)`*строке токена*необязательно  
  
## <a name="remarks"></a>Примечания  
 `#define` Директива указывает компилятору заменить *строке токена* для каждого вхождения *идентификатор* в исходном файле. *Идентификатор* заменяется только в том случае, если он формирует токен. То есть *идентификатор* не будет заменен, если он появляется в комментарии, в строке или как часть идентификатора больше времени. Дополнительные сведения см. в разделе [маркеры](../cpp/tokens-cpp.md).  
  
 *Строке токена* аргумент состоит из ряда токены, такие как ключевые слова, константы или завершения инструкции. Необходимо разделить один или несколько символов пробела *строке токена* из *идентификатор*. Эти пробелы не считаются частью замененного текста, как и все остальные пробелы, следующие за последним токеном текста.  
  
 Объект `#define` без *строке токена* удаляет вхождения *идентификатор* из исходного файла. *Идентификатор* остается определен и может быть проверен с помощью `#if defined` и `#ifdef` директивы.  
  
 Вторая форма синтаксиса определяет макрос, подобный функции, с параметрами. Эта форма допускает использование необязательного списка параметров, которые должны находиться в скобках. После макрос определен, каждый последующий вхождения *идентификатор*( *идентификатор*необязательно,..., *идентификатор*необязательно) заменяется версии  *маркер строки* аргумент, который имеет формальные параметры заменены фактических аргументов.  
  
 Отображаются имена формальных параметров в *строке токена* пометить расположения, где заменяются фактическими значениями. Имя каждого параметра может встречаться несколько раз в *строке токена*, а имена можно в любом порядке. Число аргументов в вызове должно соответствовать числу параметров в определении макроса. Надлежащее использование скобок обеспечит правильную обработку сложных фактических аргументов.  
  
 Формальные параметры в списке разделяются запятыми. Все имена в списке должны быть уникальными, и список должен быть заключен в скобки. Пробелы для разделения *идентификатор* и открывающей скобкой. Используйте сцепления строк — поместите обратную косую черту (`\`) непосредственно перед символом новой строки — для много директив на несколько строк исходного кода. Область является именем формального параметра распространяется на новую строку, которая завершается *строке токена*.  
  
 Если макрос определен во второй форме синтаксиса, последующие текстовые экземпляры, за которыми находится список аргументов, указывают на вызов макроса. Фактические аргументы, которым следует экземпляр *идентификатор* в исходном файле сопоставляются с соответствующих формальных параметров в определении макроса. Каждый формальный параметр в *строке токена* , не предшествует строковый (`#`), преобразования в символы (`#@`), или вставки токена (`##`) оператор, или не следуют `##` оператор, заменяется соответствующим фактическим аргументом. Перед заменой директивой формального параметра все макросы в фактическом аргументе разворачиваются. (Операторы описаны в [операторы препроцессора](../preprocessor/preprocessor-operators.md).)  
  
 В следующих примерах макросов с аргументами показана вторая форма синтаксиса `#define`:  
  
```  
// Macro to define cursor lines   
#define CURSOR(top, bottom) (((top) << 8) | (bottom))  
  
// Macro to get a random integer with a specified range   
#define getrandom(min, max) \  
    ((rand()%(int)(((max) + 1)-(min)))+ (min))  
```  
  
 Аргументы с побочными эффектами иногда приводят к тому, что макросы дают непредвиденные результаты. Данный формальный параметр появляется более одного раза в *строке токена*. Если этот формальный параметр заменяется выражением с побочными эффектами, выражение с такими эффектами может вычисляться несколько раз. (См. в разделе Примеры [оператор вставки токена (##)](../preprocessor/token-pasting-operator-hash-hash.md).)  
  
 Директива `#undef` приводит к тому, что определение препроцессора идентификатора забывается. В разделе [директива #undef](../preprocessor/hash-undef-directive-c-cpp.md) для получения дополнительной информации.  
  
 Если имя макроса в процессе определения появляется *строке токена* (даже в результате другого расширения макроса) еще не развернут.  
  
 Вторая директива `#define` для макроса с таким же именем выдает предупреждение, если вторая последовательность токенов не идентична первой.  
  
 **Блок, относящийся только к системам Microsoft**  
  
 Если новое определение синтаксически совпадает с исходным, Microsoft C и C++ позволяют переопределить макрос. Другими словами, два определения могут иметь разные имена параметров. Это поведение отличается от поведения языка [!INCLUDE[vcpransi](../atl-mfc-shared/reference/includes/vcpransi_md.md)] C, который требует лексической идентичности двух определений.  
  
 Например, следующие два макроса идентичны, за исключением имен параметров. [!INCLUDE[vcpransi](../atl-mfc-shared/reference/includes/vcpransi_md.md)]C не допускает такое переопределение, но Microsoft C и C++ компилируют его без ошибок.  
  
```  
#define multiply( f1, f2 ) ( f1 * f2 )  
#define multiply( a1, a2 ) ( a1 * a2 )  
```  
  
 С другой стороны, следующие два макроса неидентичны и приводят к выдаче предупреждения в Microsoft C и C++.  
  
```  
#define multiply( f1, f2 ) ( f1 * f2 )  
#define multiply( a1, a2 ) ( b1 * b2 )  
```  
  
 **Завершение блока, относящегося только к системам Майкрософт**  
  
 В следующем примере иллюстрируется директива `#define`:  
  
```  
#define WIDTH       80  
#define LENGTH      ( WIDTH + 10 )  
```  
  
 Первый оператор определяет идентификатор `WIDTH` как целочисленную константу 80, а затем `LENGTH` задается в виде `WIDTH` и целочисленной константы 10. Каждое вхождение `LENGTH` заменяется на (`WIDTH + 10`). В свою очередь, каждое вхождение `WIDTH + 10` заменяется выражением (`80 + 10`). Скобки вокруг `WIDTH + 10` имеют важное значение, поскольку управляют интерпретацией в операторах, например в следующем:  
  
```  
var = LENGTH * 20;  
```  
  
 После этапа предварительной обработки этот оператор принимает следующий вид:  
  
```  
var = ( 80 + 10 ) * 20;  
```  
  
 что равно 1800. Без скобок результат будет следующим:  
  
```  
var = 80 + 10 * 20;  
```  
  
 что дает в результате 280.  
  
 **Блок, относящийся только к системам Microsoft**  
  
 Определение макросов и констант с [/D](../build/reference/d-preprocessor-definitions.md) параметр компилятора действует так же, как с помощью `#define` директивы предварительной обработки в начале файла. С помощью параметра /D можно определить до 30 макросов.  
  
 **Завершение блока, относящегося только к системам Майкрософт**  
  
## <a name="see-also"></a>См. также  
 [Директивы препроцессора](../preprocessor/preprocessor-directives.md)