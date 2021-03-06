---
title: "Как: включить технологию IntelliSense для проекта makefile | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VC.Project.VCNMakeTool.IntelliSense
dev_langs: C++
helpviewer_keywords:
- Makefile projects, IntelliSense
- IntelliSense, Makefile projects
ms.assetid: 9443f453-f18f-4f12-a9a1-ef9dbf8b188f
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fae3ec35259250f71ad672d9468b991033608ae4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-enable-intellisense-for-makefile-projects"></a>Практическое руководство. Использование IntelliSense для проекта Makefile
IntelliSense не работает в среде разработки для проектов Visual C++ makefile, если определенные параметры проекта или параметры компилятора заданы неправильно. Эта процедура позволяет настроить в проектах Visual C++ makefile, что IntelliSense при makefile проекты открыты в среде разработки Visual Studio.  
  
### <a name="to-enable-intellisense-for-makefile-projects-in-the-ide"></a>Чтобы включить IntelliSense для проекта makefile в Интегрированной среде разработки  
  
1.  Откройте **страницы свойств** диалоговое окно. Дополнительные сведения см. в разделе [работа со свойствами проекта](../ide/working-with-project-properties.md).  
  
2.  Разверните **свойства конфигурации** узла.  
  
3.  Выберите **NMake** свойств страницы и измените свойства в разделе **IntelliSense** соответствующим образом.  
  
    -   Задать **определения препроцессора** свойство, чтобы определить символы препроцессора в проекте makefile. В разделе [/D (определения препроцессора)](../build/reference/d-preprocessor-definitions.md), Дополнительные сведения.  
  
    -   Задать **путь поиска включаемых файлов** свойство, чтобы указать список каталогов, в которых компилятор будет выполнять поиск для разрешения ссылок на файлы, которые передаются в директивы препроцессора в проекте makefile. В разделе [/I (Дополнительные каталоги включаемых файлов)](../build/reference/i-additional-include-directories.md), Дополнительные сведения.  
  
         Для проектов, которые создаются с помощью среды CL. Задать exe-файла в командном окне **INCLUDE** переменной среды можно указать каталоги, в которых компилятор будет выполнять поиск для разрешения ссылок на файлы, которые передаются в директивы препроцессора в проекте makefile.  
  
    -   Задать **принудительно включает** свойство, чтобы указать заголовок, который файлы в процесс, при построении проекта makefile. В разделе [/FI (имя принудительно включать файла)](../build/reference/fi-name-forced-include-file.md), Дополнительные сведения.  
  
    -   Задать **путь поиска сборок** свойство, чтобы указать список каталогов, в которых компилятор будет выполнять поиск для разрешения ссылок на сборки .NET в проекте. В разделе [/AI (укажите каталогов метаданных)](../build/reference/ai-specify-metadata-directories.md), Дополнительные сведения.  
  
    -   Задать **принудительное использование сборок** свойство, чтобы указать, какие сборки .NET будут обрабатываться при построении проекта makefile. В разделе [/FU (имя принудительно #using файла)](../build/reference/fu-name-forced-hash-using-file.md), Дополнительные сведения.  
  
    -   Задать **Дополнительные параметры** свойство, чтобы указать дополнительные параметры компилятора должны использоваться Intellisense при синтаксическом анализе файлов C++.  
  
4.  Нажмите кнопку **ОК** чтобы закрыть страницы свойств.  
  
5.  Используйте **сохранить все** команду, чтобы сохранить измененные параметры проекта.  
  
 При очередном открытии проекта makefile в среде разработки Visual Studio, запустите **Очистить решение** команды и затем **построить решение** команду для проекта makefile. IntelliSense должны обеспечивать нормальную работу в Интегрированной среде разработки.  
  
## <a name="see-also"></a>См. также  
 [Использование IntelliSense](/visualstudio/ide/using-intellisense)   
 [Справочник по программе NMAKE](../build/nmake-reference.md)   
 [Практическое руководство. Создание проекта C++ из существующего кода](../ide/how-to-create-a-cpp-project-from-existing-code.md)