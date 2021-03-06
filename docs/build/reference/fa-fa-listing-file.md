---
title: "/ FA, /Fa (файл листинга) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AssemblerListingLocation
- VC.Project.VCCLCompilerTool.ConfigureASMListing
- VC.Project.VCCLWCECompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.AssemblerListingLocation
- /fa
- VC.Project.VCCLCompilerTool.AssemblerOutput
- VC.Project.VCCLCompilerTool.UseUnicodeForAssemblerListing
dev_langs: C++
helpviewer_keywords:
- FA compiler option [C++]
- /FA compiler option [C++]
- -FA compiler option [C++]
- listing file type
- assembly-only listing
ms.assetid: c7507d0e-c69d-44f9-b8e2-d2c398697402
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0cd569cf16e7b2a14faaa119eacaef0994d09dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="fa-fa-listing-file"></a>/FA, /Fa (файл листинга)
Создает файл листинга, содержащего кода на языке ассемблера.  
  
## <a name="syntax"></a>Синтаксис  
  
> **/FA**[**c**\][**s**\][**u**]  
> **/FA**_pathname_  
  
## <a name="remarks"></a>Примечания  
`/FA` Параметр компилятора создает файл листинга ассемблера для каждого блока трансляции в компиляции, что исходный файл C или C++ в целом соответствует. По умолчанию только сборщик данных включен в файле листинга кодировке ANSI. Необязательный `c`, `s`, и `u` аргументы `/FA` управления ли машинного кода или исходного кода, выводятся вместе с код на языке ассемблера со списком и ли листинг кодируется как UTF-8.  
  
По умолчанию каждый файл получает такое же базовое имя исходного файла и имеет расширение .asm. Когда машинный код включается с помощью `c` параметр листинг файл имеет расширение .cod. Можно изменить имя и расширение файла листинга и каталог, в котором он создан с помощью `/Fa` параметр.  

### <a name="fa-arguments"></a>/FA аргументов  
Нет  
Только для языка ассемблера, включены в листинг.  
  
`c`  
Необязательный. Содержит машинный код в листинг.  
  
`s`  
Необязательный. В списке, включает исходный код.  
  
`u`Необязательный параметр. Файл списка в формате UTF-8 и содержит метку порядка байтов. По умолчанию файл кодировке ANSI. Используйте `u` Чтобы создать файл листинга, который будет правильно отображать в любой системе, или если вы используете Юникода файлы исходного кода в качестве входного для компилятора.  
  
Если оба `s` и `u` были указаны, а если файл исходного кода использует кодировку Юникод, отличного от UTF-8, то строки кода в файле ASM могут отображаться неправильно.  
  
### <a name="fa-argument"></a>/FA аргумент  
Нет  
Один *источника*ASM-файл создается для каждого файла исходного кода при компиляции.  
  
*Имя файла* файл с именем *filename*.asm помещается в текущем каталоге. Это допустимо только при компиляции одного файла исходного кода.  
  
*файл имяфайла.расширение*  
Файл с именем *файл имяфайла.расширение* помещается в текущем каталоге. Это допустимо только при компиляции одного файла исходного кода.  
  
*каталог*\  
Один *файл с именем исходный_файл*ASM-файл, который помещается в указанном *каталога* для каждого файла исходного кода при компиляции. Обратите внимание, требуется обратную косую черту. Разрешены только пути на текущем диске.  
  
*каталог*\\*filename* файл с именем *filename*.asm помещается в указанный *каталога*. Это допустимо только при компиляции одного файла исходного кода.  
  
*каталог*\\*файл имяфайла.расширение*  
Файл с именем *файл имяфайла.расширение* помещается в указанном *каталога*. Это допустимо только при компиляции одного файла исходного кода.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio  
  
1.  Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [работа со свойствами проекта](../../ide/working-with-project-properties.md).  
  
2.  Откройте **C/C++** папку и выберите **выходные файлы** страницу свойств.  
  
3.  Изменить **ассемблерного** задаваемого свойства `/FAc` и `/FAs` параметры ассемблер, компьютера и исходного кода. Изменить **использование Юникода для ассемблера перечисление** задаваемого свойства `/FAu` параметр для вывода ANSI или UTF-8. Изменить **местоположение ASM-списка** для задания `/Fa` параметр для перечисления имя и расположение файла.  
  
Обратите внимание, что установка **ассемблерного** и **использование Юникода для ассемблера перечисление** свойства может привести к [Предупреждение командной строки D9025](../../error-messages/tool-errors/command-line-warning-d9025.md). Чтобы объединить эти параметры в Интегрированной среде разработки, используйте **Дополнительные параметры** в **командной строки** странице свойств.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом  
  
-   См. описания свойств <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerListingLocation%2A> и <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AssemblerOutput%2A>. Чтобы указать `/FAu`, в разделе <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="example"></a>Пример  
Следующая команда создает объединенный исходный и машинного кода с именем HELLO.cod:  
  
```  
CL /FAcs HELLO.CPP  
```  
  
## <a name="see-also"></a>См. также  
 [Выходного файла (/ F) параметры](../../build/reference/output-file-f-options.md)   
 [Параметры компилятора](../../build/reference/compiler-options.md)   
 [Настройка параметров компилятора](../../build/reference/setting-compiler-options.md)   
 [Указание пути](../../build/reference/specifying-the-pathname.md)