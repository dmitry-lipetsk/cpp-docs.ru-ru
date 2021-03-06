---
title: "-C (сохранять комментарии во время предварительной обработки) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- /c
- VC.Project.VCCLWCECompilerTool.KeepComments
dev_langs: C++
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6d27e6ed0f6a2ff6e6f63bc1b87522fb598953c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (сохранять комментарии во время предварительной обработки)
Сохраняет комментарии на этапе предварительной обработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
/C  
```  
  
## <a name="remarks"></a>Примечания  
 Этот параметр компилятора требует **/E**, **/P**, или **/EP** параметр.  
  
 В следующем образце кода отобразит комментарий исходного кода.  
  
```  
// C_compiler_option.cpp  
// compile with: /E /C /c  
int i;   // a variable  
```  
  
 В этом примере будут получены следующие выходные данные.  
  
```  
#line 1 "C_compiler_option.cpp"  
int i;   // a variable  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio  
  
1.  Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [работа со свойствами проекта](../../ide/working-with-project-properties.md).  
  
2.  Откройте папку **C/C++** .  
  
3.  Нажмите кнопку **препроцессор** страницу свойств.  
  
4.  Изменить **оставлять комментарии** свойство.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом  
  
-   См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.  
  
## <a name="see-also"></a>См. также  
 [Параметры компилятора](../../build/reference/compiler-options.md)   
 [Настройка параметров компилятора](../../build/reference/setting-compiler-options.md)   
 [/E (Предварительная обработка до stdout)](../../build/reference/e-preprocess-to-stdout.md)   
 [/P (вывод результатов предварительной обработки файла)](../../build/reference/p-preprocess-to-a-file.md)   
 [/EP (Предварительная обработка в поток стандартных выходных файлов без директив #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)