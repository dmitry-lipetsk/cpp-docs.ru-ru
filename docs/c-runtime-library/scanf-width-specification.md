---
title: "Спецификация ширины scanf | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr100.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords: scanf
dev_langs: C++
helpviewer_keywords: scanf function, width specification
ms.assetid: 94b4e8fe-c4a2-4799-8b6c-a2cf28ffb09c
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ee2fa7f80f47e2d3379bc4e68aec4496e8f4f01a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="scanf-width-specification"></a>Спецификация ширины scanf
Эти данные применяются для интерпретации строк формата в семействе функций `scanf`, включая безопасные версии, такие как `scanf_s`. Эти функции обычно предполагают, что входной поток разбивается на последовательность токенов. Токены разделяются пробельным символом (пробелом, табуляцией или символом новой строки) или, в случае численных типов, естественным завершением числового типа данных, определяемым первым символом, который нельзя преобразовать в числовой текст. Однако с помощью спецификации ширины можно остановить анализ входных данных перед естественным концом токена.  
  
 Спецификация *width* состоит из символов между символом `%` и описателем типа поля, который может содержать целое положительное число, называемое полем ширины *width*, и один или несколько символов, указывающих размер поля, которые также могут считаться модификаторами типа поля, например показывать, является ли целочисленный тип типом **short** или **long**. Такие символы называются префиксами размера.  
  
## <a name="the-width-field"></a>Поле width  
 Поле ширины *width* — это положительное десятичное целое число, управляющее максимальным количеством символов для чтения из поля. Преобразуются и сохраняются в соответствующем аргументе `argument` не более *width* символов. Может быть прочитано менее *width* символов, если пробельный символ (пробел, табуляция, новая строка) или символ, который не может быть преобразован в соответствии с указанным форматом, встречается до того, как достигнута величина *width*.  
  
 Спецификация ширины — это отдельный параметр, отличный от аргумента размер буфера, требуемого безопасными версиями этих функций (например, `scanf_s`, `wscanf_s` и т. д.). В следующем примере спецификация ширины равна 20; это означает, что из входного потока могут быть прочитаны до 20 символов. Длина буфера равна 21, что включает место для возможных 20 символов плюс завершающий нуль-символ:  
  
```  
char str[21];  
scanf_s("%20s", str, 21);  
```  
  
 Если поле *width* не используется, функция `scanf_s` попытается прочитать в строку весь токен. Если указанный размер недостаточно велик для хранения всего токена, в строку назначения ничего не записывается. Если поле *width* указано, в строку назначения записываются первые *width* символов токена и завершающий нуль-символ.  
  
## <a name="the-size-prefix"></a>Префикс размера  
 Необязательные префиксы **h**, **l**, **ll**, **I64** и **L** указывают размер аргумента `argument` (long или short, однобайтовый символ или расширенный символ, в зависимости от символа типа, который они изменяют). Эти символы спецификации формата используются с символами типа в функциях `scanf` и `wscanf` для определения интерпретации аргументов, как показано в следующей таблице. Префикс типа **I64** является расширением Майкрософт и не совместим с ANSI. Символы типа и их значения описаны в таблице "Символы типа для функций scanf" в разделе [Символы поля типа scanf](../c-runtime-library/scanf-type-field-characters.md).  
  
> [!NOTE]
>  При использовании с данными типа `char` префиксы **h**, **l** и **L** — это расширения Майкрософт.  
  
### <a name="size-prefixes-for-scanf-and-wscanf-format-type-specifiers"></a>Префиксы размера для описателей типа формата функций scanf и wscanf  
  
|Чтобы указать|Используемый префикс|Со спецификатором типа|  
|----------------|----------------|-------------------------|  
|**double**|**l**|**e**, **E**, **f**, **g**или **G**|  
|**long double** (аналогично double)|**L**|**e**, **E**, **f**, **g** или **G**|  
|**long int**|**l**|**d**, **i**, **o**, **x** или **X**|  
|**long unsigned int**|**l**|**u**|  
|**long long**|**ll**|**d**, **i**, **o**, **x** или **X**|  
|`short int`|**h**|**d**, **i**, **o**, **x** или **X**|  
|**short unsigned int**|**h**|**u**|  
|__**int64**|**I64**|**d**, **i**, **o**, **u**, **x** или **X**|  
|Однобайтовый символ для функции `scanf`|**h**|**c** или **C**|  
|Однобайтовый символ для функции `wscanf`|**h**|**c** или **C**|  
|Расширенный символ для функции `scanf`|**l**|**c** или **C**|  
|Расширенный символ для функции `wscanf`|**l**|**c** или **C**|  
|Строка однобайтовых символов для функции `scanf`|**h**|**s** или **S**|  
|Строка однобайтовых символов для функции `wscanf`|**h**|**s** или **S**|  
|Строка расширенных символов для функции `scanf`|**l**|**s** или **S**|  
|Строка расширенных символов для функции `wscanf`|**l**|**s** или **S**|  
  
 В следующих примерах префиксы **h** и **l** используются с функциями `scanf_s` и `wscanf_s`:  
  
```  
scanf_s("%ls", &x, 2);     // Read a wide-character string  
wscanf_s(L"%hC", &x, 2);    // Read a single-byte character  
```  
  
 При использовании небезопасной функции из семейства `scanf` опустите параметр размера, указывающий длину буфера предыдущего аргумента.  
  
## <a name="reading-undelimited-strings"></a>Чтение строк без разделителей  
 Для чтения строк, не разделенных пробельными символами, вместо символа типа **s** (строка) можно подставлять набор символов в квадратных скобках (**[ ]**). Набор символов в квадратных скобках называется строкой управления. Соответствующее поле ввода считывается до первого символа, отсутствующего в строке управления. Если первый символ в наборе — символ каретки (**^**), логика работы меняется на обратную: поле ввода считывается до первого символа, который есть в остальной части набора символов.  
  
 Обратите внимание, что **%[a–z]** и **%[z–a]** интерпретируются как эквивалент **%[abcde...z]**. Это обычное расширения функции `scanf`, но следует заметить, что стандарт ANSI не требует его.  
  
## <a name="reading-unterminated-strings"></a>Чтение незавершенных строк  
 Чтобы сохранить строку без конечного нуль-символа ("\0"), используйте спецификацию `%`*n***c**, где *n* — десятичное целое число. В этом случае символ типа **c** указывает, что аргумент — указатель на массив символов. Следующие символы (*n*) считываются из входного потока в указанное расположение, и нуль-символ ("\0") не добавляется. Если не указать *n*, значение по умолчанию будет равно 1.  
  
## <a name="when-scanf-stops-reading-a-field"></a>Когда функция scanf прекращает чтение поля  
 Функция `scanf` считывает каждое поле ввода, символ за символом. Она может прекратить чтение определенного поля ввода до достижения пробельного символа по различным причинам:  
  
-   Достигнута указанная ширина.  
  
-   Следующий символ не может быть преобразован указанным образом.  
  
-   Следующий символ конфликтует с символом в строке управления, которой он должен соответствовать.  
  
-   Следующий символ отсутствует в заданном наборе символов.  
  
 По какой бы причине функция `scanf` не прекратила чтение поля ввода, считается, что следующее поле ввода начинается с первого непрочитанного символа. Конфликтующий символ, если такой есть, считается непрочитанным и является первым символом следующего поля ввода или первым символом в последующих операциях чтения входного потока.  
  
## <a name="see-also"></a>См. также  
 [scanf, _scanf_l, wscanf, _wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [Поля спецификации формата. Функции scanf и wscanf](../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)   
 [Символы поля типа для функции scanf](../c-runtime-library/scanf-type-field-characters.md)