---
title: "Автоматизация в библиотеке DLL | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3e3630aab764988ad86e6120301dfff548ad4368
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="automation-in-a-dll"></a>Автоматизация в библиотеке DLL
При выборе параметра автоматизации в мастер MFC DLL мастер предоставляет следующее:  
  
-   Язык описания начального объекта (. Файл ODL)  
  
-   Директива include в файле STDAFX.h Afxole.h  
  
-   Реализация `DllGetClassObject` функции, которая вызывает **AfxDllGetClassObject** функции  
  
-   Реализация `DllCanUnloadNow` функции, которая вызывает **AfxDllCanUnloadNow** функции  
  
-   Реализация `DllRegisterServer` функции, которая вызывает [COleObjectFactory::UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall) функции  
  
## <a name="what-do-you-want-to-know-more-about"></a>Дополнительные сведения  
  
-   [Серверы автоматизации](../mfc/automation-servers.md)  
  
## <a name="see-also"></a>См. также  
 [DLL в Visual C++](../build/dlls-in-visual-cpp.md)