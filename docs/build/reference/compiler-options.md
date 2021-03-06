---
title: "Параметры компилятора | Документы Microsoft"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler
- x86 Visual C++ compiler
- ARM Visual C++ compiler
- compiler options, C++
- x64 Visual C++ compiler
ms.assetid: ed3376c8-bef4-4c9a-80e9-3b5da232644c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4addd9f5dce819f554e6ab04707929a32f7b7d9d
ms.sourcegitcommit: 30ab99c775d99371ed22d1a46598e542012ed8c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="compiler-options"></a>Параметры компилятора

CL.exe — это средство, управляет Microsoft Visual C++ (параметры MSVC) C и C++ компиляторов и компоновщика. CL.exe может выполняться только в операционных системах, поддерживающих Microsoft Visual Studio для Windows.

> [!NOTE]  
> Это средство можно запустить только из командной строки разработчика Visual Studio. В системной командной строке или проводнике это невозможно. Дополнительные сведения см. в разделе [кода C/C++ на сборки в командной строке](../building-on-the-command-line.md).

Компиляторы создают общий объект файла формат COFF объектных файлах (.obj). Компоновщик создает исполняемые файлы (.exe) или библиотеки динамической компоновки (DLL).

Обратите внимание, что все параметры компилятора чувствительны к регистру. Вы можете использовать косую черту (`/`) или тире (`-`) позволяет задать параметры компилятора.

Для компиляции без компоновки, используйте [/c](../../build/reference/c-compile-without-linking.md) параметр.

## <a name="find-a-compiler-option"></a>Найти параметр компилятора

Чтобы найти конкретный параметр компилятора, см. в одном из следующих списков:

- [Параметры компилятора в алфавитном порядке](../../build/reference/compiler-options-listed-alphabetically.md)

- [Параметры компилятора, упорядоченные по категориям](../../build/reference/compiler-options-listed-by-category.md)

## <a name="specify-compiler-options"></a>Укажите параметры компилятора

В этом разделе для каждого параметра компилятора обсуждается, как это можно сделать в среде разработки. Сведения об установке параметров вне среды разработки см. в разделе:

- [Синтаксис командной строки компилятора](../../build/reference/compiler-command-line-syntax.md)

- [Командные файлы компилятора CL](../../build/reference/cl-command-files.md)

- [Переменные среды CL](../../build/reference/cl-environment-variables.md)

## <a name="related-build-tools"></a>Связанные средства построения

[Параметры компоновщика](../../build/reference/linker-options.md) также влияют на построение программы.

## <a name="see-also"></a>См. также

[Справочные сведения о сборке C/C++](../../build/reference/c-cpp-building-reference.md)  
[Настройка параметров компилятора](../../build/reference/setting-compiler-options.md)  
[Быстрая компиляция](../../build/reference/fast-compilation.md)  
[Вызов компоновщика компилятором CL](../../build/reference/cl-invokes-the-linker.md)  
