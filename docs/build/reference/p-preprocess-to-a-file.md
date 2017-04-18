---
title: "/P (вывод результатов предварительной обработки в файл) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.GeneratePreprocessedFile"
  - "/p"
  - "VC.Project.VCCLWCECompilerTool.GeneratePreprocessedFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/P - параметр компилятора [C++]"
  - "выходные файлы, препроцессор"
  - "P - параметр компилятора [C++]"
  - "-P - параметр компилятора [C++]"
  - "предварительная обработка выходных файлов"
ms.assetid: 123ee54f-8219-4a6f-9876-4227023d83fc
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /P (вывод результатов предварительной обработки в файл)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Выполняет предварительную обработку файлов на языке C и С\+\+ и записывает выходные данные предварительной обработки в файл.  
  
## Синтаксис  
  
```  
/P  
```  
  
## Заметки  
 Файл имеет базовое имя исходного файла и расширение I.  В процессе выполняются все директивы препроцессора, выполняются расширения макросов, а комментарии удаляются.  Чтобы сохранить комментарии в выходных данных предварительной обработки, используйте вместе с параметром [\/C \(сохранять комментарии во время предварительной обработки\)](../../build/reference/c-preserve-comments-during-preprocessing.md) вместе с **\/P**.  
  
 **\/P** добавляет в выходном файле директивы `#line` в начале и в конце каждого включенного файла, а также вокруг строк, удаленных директивами препроцессора для условной компиляции.  Директивы перенумеровывают строки предварительно обработанного файла.  В результате, ошибки, созданные на более поздних этапах обработки, ссылаются на номера строк исходного файла, а не на номера строк предварительно обработанного файла.  Чтобы запретить создание директив `#line`, используйте вместе с параметром **\/P** параметр [\/EP \(предварительная обработка в поток стандартных выходных файлов без директив \#line\)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md).  
  
 Параметр **\/P** запрещает компиляцию.  OBJ\-файл не создается, даже когда используется параметр [\/Fo \(имя объектного файла\)](../../build/reference/fo-object-file-name.md).  Следует повторить отправку предварительно обработанного файла для компиляции.  **\/P** также запрещает файлы вывода из параметров **\/FA**, **\/Fa** и **\/Fm**.  Дополнительные сведения см. в разделах [\/FA, \/Fa \(файл листинга\)](../../build/reference/fa-fa-listing-file.md) и [Параметр \/Fm \(имя файла сопоставления\)](../Topic/-Fm%20\(Name%20Mapfile\).md).  
  
### Установка данного параметра компилятора в среде разработки Visual Studio  
  
1.  Откройте диалоговое окно **Страницы свойств** проекта.  Дополнительные сведения см. в разделе [Открытие свойств страниц проекта](../../misc/how-to-open-project-property-pages.md).  
  
2.  Откройте папку **C\/C\+\+**.  
  
3.  Щелкните страницу свойств **Препроцессор**.  
  
4.  Измените значение свойства **Создание предварительно обработанного файла**.  
  
### Установка данного параметра компилятора программным способом  
  
-   См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GeneratePreprocessedFile%2A>.  
  
## Пример  
 Следующая командная строка предварительно обрабатывает `ADD.C`, сохраняет комментарии, добавляет директивы `#line` и записывает результаты в файл `ADD.I`:  
  
```  
CL /P /C ADD.C  
```  
  
## См. также  
 [Параметры компилятора](../../build/reference/compiler-options.md)   
 [Настройка параметров компилятора](../Topic/Setting%20Compiler%20Options.md)   
 [\/Fi \(предварительная обработка имени выходного файла\)](../../build/reference/fi-preprocess-output-file-name.md)