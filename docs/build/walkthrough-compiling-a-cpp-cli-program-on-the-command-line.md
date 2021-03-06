---
title: "Пошаговое руководство: Компиляция C + +/ CLI программа в командной строке | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d509bc9890f4fa5ccebbd6ae3d1e3bcb3dbb0d93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Пошаговое руководство. Компиляция программы на языке C++/CLI из командной строки
Вы можете создавать программы Visual C++, предназначенные для среды CLR и использующие платформу .NET Framework, и выполнять их сборку из командной строки. Visual C++ поддерживает язык программирования C++/CLI, который предоставляет дополнительные типы и операторы для модели программирования .NET. Введение в C + +/ CLI язык, в разделе [Pure C++: Hello, C + +/ CLI](http://msdn.microsoft.com/magazine/cc163681.aspx). Общие сведения см. в разделе [программирование .NET с использованием C + +/ CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).  
  
 В этом руководстве мы используем текстовый редактор для создания простой программы C++/CLI, а затем компилируем эту программу в командной строке. (Можно использовать вашу собственную программу C++/CLI вместо ввода показанной здесь, или же можно использовать образец кода C++/CLI из другой статьи справки. Эта методика полезна для сборки и тестирования небольших модулей, не содержащих элементы пользовательского интерфейса.)  
  
> [!NOTE]
>  В интегрированной среде разработки (IDE) Visual Studio также можно компилировать программы C++/CLI. Дополнительные сведения см. в разделе [Пошаговое руководство: компиляция программы на языке C++, предназначенной для среды CLR в Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Необходимо понимать основы языка C++.  
  
## <a name="compiling-a-ccli-program"></a>Компиляция программы на C++/CLI  
 Ниже приведены инструкции по компиляции консольного приложения C++/CLI, использующего классы .NET Framework.  
  
 Чтобы включить компиляцию для C + +/ CLI, необходимо использовать [/CLR](../build/reference/clr-common-language-runtime-compilation.md) параметр компилятора. Компилятор Visual C++ создает EXE-файл, содержащий код MSIL (или смешанный код MSIL и собственный код) и ссылки на необходимые библиотеки .NET Framework.  
  
#### <a name="to-compile-a-ccli-application-on-the-command-line"></a>Компиляция приложения C++/CLI из командной строки  
  
1.  Откройте **Командная строка разработчика** окна. Дополнительные инструкции в разделе [чтобы открыть окно командной строки разработчика](../build/building-on-the-command-line.md#developer_command_prompt).  
  
     В зависимости от операционной системы и конфигурации компьютера для успешной компиляции кода могут потребоваться учетные данные администратора. Чтобы запустить окно командной строки с правами администратора, щелкните правой кнопкой мыши, чтобы открыть контекстное меню для окна командной строки, а затем выберите **дополнительные**, **Запуск от имени администратора**.  
  
2.  В командной строке введите **basicclr.cpp Блокнот**.  
  
     Выберите **Да** при появлении для создания файла.  
  
3.  В Блокноте введите следующие строки:  
  
    ```  
    int main()  
    {  
        System::Console::WriteLine("This is a C++/CLI program.");  
    }  
    ```  
  
4.  В строке меню выберите **файл**, **Сохранить**.  
  
     Вы создали файл исходного кода Visual C++, использующий класс .NET Framework (<xref:System.Console>) в пространстве имен <xref:System>.  
  
5.  В командной строке введите **cl/CLR basicclr.cpp**. Компилятор cl.exe скомпилирует исходный код в OBJ-файл, содержащий код MSIL, а затем запустит компоновщик для создания исполняемой программы с именем basicclr.exe.  
  
6.  Чтобы запустить программу basicclr.exe, в командной строке введите **basicclr**.  
  
     Программа выводит следующий текст и закрывается:  
  
    ```Output  
    This is a C++/CLI program.  
    ```  
  
## <a name="see-also"></a>См. также  
 [Справочник по языку C++](../cpp/cpp-language-reference.md)   
 [Сборка программ C/C++](../build/building-c-cpp-programs.md)   
 [Параметры компилятора](../build/reference/compiler-options.md)