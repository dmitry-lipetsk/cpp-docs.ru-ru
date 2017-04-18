---
title: "Пошаговое руководство. Компиляция машинной программы на языке C++ из командной строки | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "приложения командной строки [C++], в машинном коде"
  - "компиляция программ [C++]"
  - "машинный код [C++]"
  - "Visual C++, машинный код"
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
caps.latest.revision: 63
caps.handback.revision: 57
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Пошаговое руководство. Компиляция машинной программы на языке C++ из командной строки
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

В состав Visual C\+\+ включен компилятор языка C\+\+ для командной строки, позволяющий создавать все, от простых консольных приложений, до универсальных приложений Windows, приложений Магазина Windows и компонентов .NET.  
  
 В этом пошаговом руководстве приводятся инструкции по созданию простой консольной программы на языке Visual C\+\+ в текстовом редакторе с последующей компиляцией из командной строки.  
  
> [!NOTE]
>  В интегрированной среде разработки Visual Studio также можно компилировать программы Visual C\+\+. Для получения дополнительной информации см. [Пошаговое руководство. Работа с проектами и решениями \(C\+\+\)](../Topic/Walkthrough:%20Working%20with%20Projects%20and%20Solutions%20\(C++\).md).  
  
 В этом пошаговом руководстве вместо примера программы, приведенного далее, можно использовать собственную программу на Visual C\+\+. Кроме того, можно использовать образец кода на языке Visual C\+\+ из другого раздела справки.  
  
## Обязательные компоненты  
 Для выполнения этого пошагового руководства у вас должна быть версия Visual Studio, включающая компоненты Visual C\+\+. Для работы рекомендуется владеть основами языка C\+\+. Эти инструкции предполагают, что вы используете Windows 10 и Visual Studio 2015. Для других сред и версий инструкции не будут сильно отличаться.  
  
### Создание файла исходного кода на языке Visual C\+\+ и его компиляция из командной строки  
  
1.  Сначала откройте **командную строку разработчика**. Для запуска компилятора Visual C\+\+ требуется специальная среда командной строки, поэтому вы не можете использовать обычную командную строку в этом пошаговом руководстве.  
  
     В меню **Пуск** Windows откройте раздел **Все приложения**. Прокрутите список вниз, чтобы найти и открыть папку **Visual Studio** для вашей версии [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], а затем щелкните ярлык **Командная строка разработчика**.  
  
2.  Создайте новый каталог для хранения программы. В окне **Командная строка разработчика**  введите команду `cd \`, чтобы перейти в корень диска. Введите команду `md examples`, чтобы создать каталог для примера кода. Затем введите команду `cd examples`, чтобы сделать его текущим рабочим каталогом. Здесь будет храниться ваша первая программа.  
  
3.  В командной строке введите **notepad hello.cpp**.  
  
     Когда появится запрос на создание файла, нажмите кнопку **Да**. Откроется пустое окно Блокнота, в котором можно ввести код.  
  
4.  В Блокноте введите следующие строки:  
  
    ```cpp  
    #include <iostream> using namespace std; void main() { cout << "Hello, world, from Visual C++!" << endl; }  
    ```  
  
     Это очень простая программа, которая выведет одну строку текста на экран, а затем завершит работу. Для сведения числа ошибок к минимуму скопируйте этот код и вставьте его в Блокнот.  
  
5.  Сохраните файл. В Блокноте, в меню **Файл** выберите **Сохранить**.  
  
     Вы создали файл исходного кода Visual C\+\+.  
  
6.  В командной строке введите `cl /EHsc hello.cpp`, чтобы скомпилировать свою программу.  
  
     Компилятор cl.exe создаст OBJ\-файл, содержащий скомпилированный код, а затем запустит компоновщик для создания исполняемой программы с именем hello.exe. Это имя отображается в строках информации, выводимой компилятором. Выходные данные компилятора должны выглядеть следующим образом:  
  
    ```Output  
    Оптимизирующий компилятор Microsoft (R) C/C++ версии 19.00.23504 для x86 (C) Корпорация Майкрософт (Microsoft Corporation).  Все права защищены. hello.cpp Microsoft (R) Инкрементный компоновщик версии 14.00.23504.0 (C) Корпорация Майкрософт (Microsoft Corporation).  Все права защищены. /out:hello.exe hello.obj  
    ```  
  
     При наличии ошибок проверьте код в Блокноте, чтобы убедиться, что он совпадает с примером. Снова запустите команду компилятора после сохранения изменений.  Если не удалось найти команду cl, убедитесь, что вы используете окно командной строки разработчика, а не обычной командной строки. Возможно, при установке Visual Studio потребуется установить компонент Visual C\+\+, если он не установлен.  
  
7.  Чтобы запустить программу hello.exe, в командной строке введите `hello`.  
  
     Программа выводит следующий текст и закрывается:  
  
    ```Output  
    Hello, world, from Visual C++!  
    ```  
  
     Поздравляем, вы создали и скомпилировали программу с помощью программ командной строки.  
  
## Следующие действия  
 Подробности об открытии окна командной строки разработчика для работы с программами командной строки см. в статье [Установка переменных пути и среды при построении из командной строки](../build/setting-the-path-and-environment-variables-for-command-line-builds.md).  
  
 В зависимости от операционной системы и конфигурации компьютера для успешной компиляции кода из этого пошагового руководства могут потребоваться учетные данные администратора. Чтобы запустить окно командной строки разработчика от имени администратора, щелкните правой кнопкой мыши элемент **Командная строка разработчика** и выберите команду **Запуск от имени администратора**.  
  
 Параметр командной строки **\/EHsc** указывает компилятору на необходимость обработки исключений C\+\+. Дополнительные сведения см. в разделе [Параметр \/EH \(модель обработки исключений\)](../build/reference/eh-exception-handling-model.md).  
  
## См. также  
 [Обзор возможностей Visual C\+\+](http://msdn.microsoft.com/ru-ru/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [Справочник по языку C\+\+](../cpp/cpp-language-reference.md)   
 [Сборка программ C\/C\+\+](../build/building-c-cpp-programs.md)   
 [Параметры компилятора](../build/reference/compiler-options.md)