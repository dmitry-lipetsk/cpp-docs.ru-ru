---
title: "Кодовые страницы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.international"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ANSI [C++], кодовые страницы"
  - "кодировки [C++], кодовые страницы"
  - "кодовые страницы [C++], типы"
  - "кодовые страницы языковых стандартов [C++]"
  - "локализация [C++], кодовые страницы"
  - "несколько кодовых страниц [C++]"
  - "системная кодовая страница по умолчанию"
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Кодовые страницы
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`code page` \(кодовая страница\) \- это кодировка, которая может содержать числа, знаки пунктуации и другие глифы.  Различные языки и языковые стандарты могут использовать разные кодовые страницы.  Например, кодовая страница ANSI 1252 используется для английского и большинства европейских языков; кодовая страница OEM 932 используется для японского иероглифического языка.  
  
 Кодовую страницу можно представить в таблице как сопоставления символов и однобайтовых или многобайтовых значений.  Многие кодовые страницы используют кодировку ASCII для символов в диапазоне от 0x00 — 0x7F.  
  
 В библиотеке времени выполнения Майкрософт используются следующие типы кодовых страниц:  
  
-   Системная кодовая страница ANSI по умолчанию.  По умолчанию во время запуска система времени выполнения устанавливает многобайтовую кодовую страницу на системную кодовую страницу ANSI по умолчанию, которая получается из файловой системы.  Вызов:  
  
    ```  
    setlocale ( LC_ALL, "" );  
    ```  
  
     также устанавливает языковой стандарт на системную кодовую страницу ANSI по умолчанию.  
  
-   Кодовая страница языковых стандартов.  Расширение некоторого числа процедур времени выполнения зависит от текущих языковых настроек, которые включают в себя кодовую страницу языковых стандартов. \(Дополнительные сведения см. в разделе [Процедуры, зависящие от языкового стандарта](../c-runtime-library/locale.md).\) По умолчанию все процедуры, зависящие от языкового стандарта, в библиотеке времени выполнения Майкрософт используют кодовую страницу, соответствующую языковому стандарту «C».  Во время выполнения можно изменить или получить текущую кодовую страницу языкового стандарта вызовом метода [setlocale](../Topic/setlocale,%20_wsetlocale.md).  
  
-   Многобайтовая кодовая страница.  Поведение большинства процедур, работающих с многобайтовыми символами, в библиотеки времени выполнения зависит от текущих настроек многобайтовой кодовой страницы.  По умолчанию эти процедуры используют системную кодовую страницу ANSI по умолчанию.  Во время выполнения можно запросить или изменить многобайтовую кодовую страницу методами [\_getmbcp](../c-runtime-library/reference/getmbcp.md) и [\_setmbcp](../c-runtime-library/reference/setmbcp.md) соответственно.  
  
-   Языковой стандарт «C» определен ANSI для обеспечения соответствия языковому стандарту, с которым обычно выполнялись программы C.  Кодовая страница для языкового стандарта «C» \(кодовая страница «C»\) соответствует кодировке ASCII.  Например, в языковом стандарте «C», `islower` возвращает значение true только для значений 0x61 — 0x7A.  В другом языковом стандарте, `islower` может возвращать значение true как для этих, так и для других значений, заданных этим языковым стандартом.  
  
## См. также  
 [Интернационализация](../c-runtime-library/internationalization.md)   
 [Процедуры среды выполнения по категориям](../c-runtime-library/run-time-routines-by-category.md)