---
title: "Кодовые страницы | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.international
dev_langs: C++
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a0899f5f617fd28d121b85183280bd28fe91ee46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="code-pages"></a>Кодовые страницы
`code page` (кодовая страница) — это набор символов, который может содержать числа, знаки пунктуации и другие глифы. Различные языки и языковые стандарты могут использовать разные кодовые страницы. Например, кодовая страница ANSI 1252 используется для английского и большинства европейских языков; кодовая страница OEM 932 используется для японского иероглифического письма Кандзи.  
  
 Кодовую страницу можно представить в виде таблицы как сопоставление символов и однобайтовых или многобайтовых значений. Многие кодовые страницы включают в себя набор символов ASCII для символов в диапазоне 0x00–0x7F.  
  
 В библиотеке времени выполнения Microsoft используются следующие типы кодовых страниц:  
  
-   Системная кодовая страница ANSI по умолчанию. По умолчанию во время запуска система времени выполнения устанавливает в качестве многобайтовой кодовой страницы системную кодовую страницу ANSI по умолчанию, которая получается из файловой системы. Вызов  
  
    ```  
    setlocale ( LC_ALL, "" );  
    ```  
  
     также устанавливает для языкового стандарта системную кодовую страницу ANSI по умолчанию.  
  
-   Кодовая страница языкового стандарта. Поведение ряда подпрограмм времени выполнения зависит от текущей настройки языкового стандарта, которая включает в себя кодовую страницу языкового стандарта. (Дополнительные сведения см. в разделе [Подпрограммы, зависящие от языкового стандарта](../c-runtime-library/locale.md).) По умолчанию все подпрограммы, зависящие от языкового стандарта, в библиотеке времени выполнения Microsoft используют кодовую страницу, соответствующую языковому стандарту "C". Во время выполнения можно изменить или запросить текущую кодовую страницу языкового стандарта, вызвав функцию [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
-   Многобайтовая кодовая страница. Поведение большинства подпрограмм библиотеки времени выполнения, работающих с многобайтовыми символами, зависит от текущей настройки многобайтовой кодовой страницы. По умолчанию эти подпрограммы используют системную кодовую страницу ANSI по умолчанию. Во время выполнения можно запросить или изменить многобайтовую кодовую страницу с помощью функций [_getmbcp](../c-runtime-library/reference/getmbcp.md) и [_setmbcp](../c-runtime-library/reference/setmbcp.md) соответственно.  
  
-   Языковой стандарт "C" определен ANSI для обеспечения соответствия языковому стандарту, с которым обычно выполнялись программы C. Кодовая страница для языкового стандарта "C" (кодовая страница "C") соответствует кодировке ASCII. Например, в языковом стандарте "C" функция `islower` возвращает значение true только для значений 0x61–0x7A. В другом языковом стандарте функция `islower` может возвращать значение true как для этих, так и для других значений, заданных этим языковым стандартом.  
  
## <a name="see-also"></a>См. также  
 [Интернационализация](../c-runtime-library/internationalization.md)   
 [Процедуры среды выполнения по категориям](../c-runtime-library/run-time-routines-by-category.md)