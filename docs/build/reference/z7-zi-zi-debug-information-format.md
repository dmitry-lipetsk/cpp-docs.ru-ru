---
title: "-Z7, - Zi, - ZI (формат отладочной информации) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /zi
- /z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
dev_langs: C++
helpviewer_keywords:
- C7 compatible compiler option [C++]
- -Zl compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- none compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
ms.assetid: ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0b80339192a7d335b0989ac8a67446c0f5716a76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (формат отладочной информации)
Выбрать тип отладочных данных, созданных для программы, а также определить, следует ли хранить эти данные в объектных файлах (.obj) или в базе данных программы (PDB).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
/Z{7|i|I}  
```  
  
## <a name="remarks"></a>Примечания  
 Данные параметры описаны в следующей таблице.  
  
 Нет  
 Не предоставляет отладочной информации, и компиляция выполняется быстрее.  
  
 **/ Z7**  
 Создает OBJ-файл, содержащий полные сведения об отладке символов для использования с отладчиком. Символьная отладочная информация включает имена и типы переменных, а также функции и номера строк. PDB-файл не создается.  
  
 Отсутствие PDB-файла является преимуществом для распространителей сторонних библиотек. На этапе компоновки и отладки, однако, OBJ-файлы необходимы для предкомпилированных заголовков. Если существует только в PCH-файлы объектов введите сведения (и без кода), также требуется компилировать с [параметр /Yl (Вставка ссылка PCH для библиотеки отладки)](../../build/reference/yl-inject-pch-reference-for-debug-library.md).  
  
 **/ ZI**  
 Создание базы данных программы (PDB), содержащей сведения о типах и символьную отладочную информацию для использования с отладчиком. Символьная отладочная информация включает имена и типы переменных, а также функции и номера строк.  
  
 **/ ZI** не влияет на оптимизацию. Тем не менее **/ZI** подразумевают **/debug**; в разделе [/Debug (создать отладочную информацию)](../../build/reference/debug-generate-debug-info.md) для получения дополнительной информации.  
  
 Информация о типах размещается в PDB-файле, а не в файле OBJ.  
  
 Можно использовать [/Gm (включение минимального перепостроения)](../../build/reference/gm-enable-minimal-rebuild.md) с **/ZI**, тогда как **/Gm** доступен только при компиляции с параметром **/Z7**.  
  
 При компиляции с параметром **/ZI** и **/CLR**, <xref:System.Diagnostics.DebuggableAttribute> атрибута не будет помещаться в метаданные сборки; при необходимости его необходимо указать в исходном коде. Этот атрибут может повлиять на производительность приложения во время выполнения. Дополнительные сведения о том, как атрибут Debuggable влияет на производительность и изменении влияние на производительность см. в разделе [Облегчение образ для отладки](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).  
  
 **/ ZI**  
 Создает базу данных программы, как описано выше, в формате, который поддерживает возможность "Изменить и продолжить". Если необходимо использовать в отладке режим "Изменить и продолжить", следует использовать этот вариант. Поскольку большинство видов оптимизации несовместимы, изменить и продолжить использование **/ZI** отменяет любые `#pragma optimize` инструкций в коде.  
  
 **/ ZI** вызывает [/Gy (включение компоновки на уровне функций)](../../build/reference/gy-enable-function-level-linking.md) и [/FC (полный путь для файлу исходного кода в диагностике)](../../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md) для использования при компиляции.  
  
 **/ ZI** не совместим с [/CLR (компиляция CLR)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
> [!NOTE]
>  **/ ZI** доступен только в компиляторах, предназначенных для процессоров x86- и x64; параметр этого компилятора недоступен в компиляторах, предназначенных для процессоров ARM.  
  
 Компилятор имена базы данных программы *проекта*PDB-файл. При компиляции файла вне проекта, компилятор создает базу данных с именем VC*x*0.pdb, где *x* является основной номер версии [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] используется. Компилятор внедряет имя базы данных PDB во все OBJ-файлы, созданные с помощью этого параметра, указывая отладчику на местоположение сведений о символах и номерах строк. При использовании этого варианты OBJ-файлы будут иметь более компактные размеры, поскольку отладочная информация хранится в PDB-файле, а не в файлах OBJ.  
  
 При создании библиотеки из объектных файлов, созданных с помощью этого параметра, связанный с ними PDB-файл должен быть доступен при компоновке программы с библиотекой. Это означает, что вместе с библиотекой следует распространять и PDB-файл.  
  
 Чтобы создать библиотеку, содержащую отладочную информацию, без использования PDB-файлы, необходимо выбрать компилятора совместимости с C 7.0 (**/Z7**) параметра. При использовании параметров, связанных с предкомпилированными заголовками, в PDB-файл заносится отладочная информация как для предкомпилированного заголовка, так и для оставшегося исходного кода. **/Yd** параметр игнорируется, если указан параметр базы данных программы.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio  
  
1.  Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [работа со свойствами проекта](../../ide/working-with-project-properties.md).  
  
2.  Откройте папку **C/C++** .  
  
3.  Нажмите кнопку **Общие** страницу свойств.  
  
4.  Изменить **формат отладочной информации** свойство.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом  
  
-   См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.  
  
## <a name="see-also"></a>См. также  
 [Параметры компилятора](../../build/reference/compiler-options.md)   
 [Настройка параметров компилятора](../../build/reference/setting-compiler-options.md)