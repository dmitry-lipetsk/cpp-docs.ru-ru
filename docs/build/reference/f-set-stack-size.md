---
title: "-F (задание размера стека) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /f
dev_langs: C++
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5b464a4fb28eb83ef0570416d0cb18fd8f965e0a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="f-set-stack-size"></a>/F (Задание размера стека)
Задает размер стека программы в байтах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
/F number  
```  
  
## <a name="arguments"></a>Аргументы  
 `number`  
 Размер стека в байтах.  
  
## <a name="remarks"></a>Примечания  
 Без этого параметра размер стека по умолчанию равно 1 МБ. `number` Аргумент может быть в десятичном или нотации языка. Аргумент находится в диапазоне от 1 до максимального размера стека допускаемого компоновщиком. Компоновщик Округляет указанное значение до ближайших 4 байт. Расстояние между **/F** и `number` является необязательным.  
  
 Может потребоваться увеличить размер стека, если программа возвращает сообщения о переполнении стека.  
  
 Можно также задать размер стека:  
  
-   С помощью **/STACK** компоновщика. Дополнительные сведения см. в разделе [/STACK](../../build/reference/stack.md).  
  
-   С помощью EDITBIN файл .exe. Дополнительные сведения см. в разделе [Справочник ЕDITBIN](../../build/reference/editbin-reference.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio  
  
1.  Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [работа со свойствами проекта](../../ide/working-with-project-properties.md).  
  
2.  Откройте папку **C/C++** .  
  
3.  Выберите страницу свойств **Командная строка** .  
  
4.  Введите параметр компилятора в поле **Дополнительные параметры** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом  
  
-   См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>См. также  
 [Параметры компилятора](../../build/reference/compiler-options.md)   
 [Настройка параметров компилятора](../../build/reference/setting-compiler-options.md)