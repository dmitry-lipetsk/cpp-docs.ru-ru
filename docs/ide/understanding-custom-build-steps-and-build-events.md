---
title: "Основные сведения об этапах настраиваемого построения и событиях построения. | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- builds [C++], events
- custom build steps [C++], customizing builds
- events [C++], build
- custom build steps [C++]
- build steps [C++]
- build events [C++], order of events and build steps
- build steps [C++], build events
- builds [C++], custom build steps
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9abb7ff0b9a39656999e7a53b476056f7a5b1558
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-custom-build-steps-and-build-events"></a>Сведения об этапах настраиваемого построения и событиях построения.
Из среды разработки Visual C++, существует три основных способа настройки процесса построения:  
  
 **Настраиваемые этапы построения**  
 Этап настраиваемого построения — это правило сборки, связанные с проектом. Этап настраиваемого построения можно указать командную строку для выполнения все дополнительные входные или выходные файлы и сообщения для отображения. Дополнительные сведения см. в разделе [как: Добавление пользовательского шага построения в проекты MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md).  
  
 **Пользовательские средства построения**  
 Пользовательскому средству сборки — это правило сборки, связанные с одного или нескольких файлов. Этап настраиваемого построения может передавать входные файлы средству настраиваемого построения, чего создается один или несколько выходных файлов. Например файлы справки в приложениях MFC создаются с помощью настраиваемого инструмента сборки. Дополнительные сведения см. в разделе [как: Добавление настраиваемых построения средств в проекты MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md) и [Указание средства построения пользовательских](../ide/specifying-custom-build-tools.md).  
  
 **События сборки**  
 События построения позволяют настроить построение проекта. Существует три события построения: *перед построением*, *перед компоновкой*, и *после построения*. Событие построения позволяет указать выполнение действия в определенное время в процессе построения. Например, можно использовать событие построения для регистрации файла с **regsvr32.exe** после завершения построения проекта. Дополнительные сведения см. в разделе [Указание событий сборки](../ide/specifying-build-events.md).  
  
 [Устранение неполадок настроек построения](../ide/troubleshooting-build-customizations.md) поможет вам убедиться, что ваш настраиваемые этапы построения и работают ожидаемым образом события построения.  
  
 Формат вывода пользовательского шага построения или события построения может также повысить удобство использования инструмента. Дополнительные сведения см. в разделе [Форматирование выходных данных этапа настраиваемой сборки или события сборки](../ide/formatting-the-output-of-a-custom-build-step-or-build-event.md).  
  
 События построения и этапы настраиваемого построения запустите в следующем порядке, а также другие этапы построения:  
  
1.  Событие перед построением  
  
2.  Средства настраиваемого построения в отдельных файлов  
  
3.  MIDL  
  
4.  Компилятор ресурсов  
  
5.  Компилятор C/C++  
  
6.  Событие перед компоновкой  
  
7.  Компоновщик или библиотекарь (по необходимости)  
  
8.  Инструмент манифеста  
  
9. BSCMake  
  
10. Этап настраиваемого построения проекта  
  
11. Событие после построения  
  
 `custom build step on the project` И `post-build event` выполнения последовательно после всех остальных построения обрабатывает Готово.  
  
## <a name="see-also"></a>См. также  
 [Построение проектов C++ в Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)   
 [Общие макросы для команд и свойств построения](../ide/common-macros-for-build-commands-and-properties.md)   
 [Диалоговое окно порядок построения средства](http://msdn.microsoft.com/en-us/6204c5b1-7ce9-4948-9ff6-0268642ee14c)