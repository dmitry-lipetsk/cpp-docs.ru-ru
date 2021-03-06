---
title: "Неустранимая ошибка C1052 | Документы Microsoft"
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1052
dev_langs: C++
helpviewer_keywords: C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6b9d7cc04fa863d30829c5484b328effc55125e6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1052"></a>Неустранимая ошибка C1052  
  
> файл базы данных программы, "*filename*", был сформирован компоновщиком с/debug: fastlink; компилятор не может обновить такой PDB-файл; удалите его или используйте параметр /Fd, чтобы указать другое имя файла PDB-файла  
  
Компилятору не удается обновить те же файлы базы данных (PDB) программы, которые создаются компоновщиком при [/debug: fastlink](../../build/reference/debug-generate-debug-info.md) параметра. Обычно компилятором PDB-файлы и PDB-файлы компоновщиком иметь разные имена. Тем не менее если они настроены для использования с теми же именами, эта ошибка может возникнуть.  
  
Чтобы устранить эту проблему, можно явным образом удалить PDB-файлы перед повторите компиляцию, или можно создать разные имена для создаваемых компилятора и компоновщика PDB-файлы.  
  
Чтобы указать имя созданного компилятором PDB-файла в командной строке, используйте [/Fd](../../build/reference/fd-program-database-file-name.md) параметр компилятора. Чтобы указать имя созданного компилятором PDB-файла в Интегрированной среде разработки, откройте **страницы свойств** диалогового окна проекта, а в **свойства конфигурации**, **C/C++**,  **Выходные файлы** задайте **имя файла базы данных программы** свойство. По умолчанию это свойство является `$(IntDir)vc$(PlatformToolsetVersion).pdb`.  
  
Кроме того можно задать имя PDB-файла компоновщиком. Чтобы указать имя создаваемой компоновщиком PDB-файла в командной строке, используйте [/PDB](../../build/reference/pdb-use-program-database.md) компоновщика. Чтобы указать имя создаваемой компоновщиком PDB-файла в Интегрированной среде разработки, откройте **страницы свойств** диалогового окна проекта, а в **свойства конфигурации**, **компоновщика**,  **Отладка** задайте **создавать файл базы данных программы** свойство. По умолчанию для свойства задано значение `$(OutDir)$(TargetName).pdb`.  
