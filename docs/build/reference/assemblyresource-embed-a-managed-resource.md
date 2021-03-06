---
title: "-ASSEMBLYRESOURCE (внедрение управляемого ресурса) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.EmbedManagedResourceFile
- /ASSEMBLYRESOURCE
dev_langs: C++
helpviewer_keywords:
- ASSEMBLYRESOURCE linker option
- assemblies [C++]
- -ASSEMBLYRESOURCE linker option
- assemblies [C++], linking resource files
- /ASSEMBLYRESOURCE linker option
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ed8fd2b127a828eb8279671817cc4f099ae528c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE (внедрение управляемого ресурса)
```  
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]  
```  
  
## <a name="parameters"></a>Параметры  
 *filename*  
 Управляемый ресурс, который требуется внедрить в этой сборке.  
  
 *name*  
 Необязательный. Логическое имя ресурса; имя, используемое для загрузки ресурса. По умолчанию используется имя файла.  
  
 Кроме того можно указать, если этот файл должен быть закрытым в манифесте сборки. По умолчанию *имя* является открытым в сборке.  
  
## <a name="remarks"></a>Примечания  
 Используйте параметр/ASSEMBLYRESOURCE для внедрения ресурса в сборку.  
  
 Ресурсы в сборке при создании с помощью компоновщика открыты. Компоновщик не позволяет переименовать ресурсом в сборке.  
  
 Если *filename* — это файл ресурсов (RESOURCES) .NET Framework, созданным, например, с [генератор файлов ресурсов (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator) или в среде разработки, он может осуществляться с помощью членов **System.Resources** пространства имен (в разделе [System.Resources.ResourceManager](https://msdn.microsoft.com/en-us/library/system.resources.resourcemanager.aspx) для получения дополнительной информации). Другие ресурсы, используйте **GetManifestResource** \* методы в **System.Reflection.Assembly** класса доступа к ресурсам во время выполнения.  
  
 Доступны следующие параметры компоновщика, влияющие на создание сборки.  
  
-   [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Задание данного параметра компоновщика в среде разработки Visual Studio  
  
1.  Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [задание свойств проекта Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Нажмите кнопку **компоновщика** папки.  
  
3.  Нажмите кнопку **ввода** страницу свойств.  
  
4.  Изменить **внедрить управляемый файл ресурсов** свойство.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Задание данного параметра компоновщика программным способом  
  
1.  См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.  
  
## <a name="see-also"></a>См. также  
 [Настройка параметров компоновщика](../../build/reference/setting-linker-options.md)   
 [Параметры компоновщика](../../build/reference/linker-options.md)