---
title: "Неустранимая ошибка C1510 | Документы Microsoft"
ms.custom: 
ms.date: 04/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1510
dev_langs: C++
helpviewer_keywords: C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8d4128580facdc87239d0087fef1cf9eff701854
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1510"></a>Неустранимая ошибка C1510
Не удается открыть языковой ресурс clui.dll  
  
 Компилятору не удается загрузить DLL языковой ресурс.  
  
Существуют две распространенные причины этой проблемы. При использовании 32-разрядный компилятор и средства, появится это сообщение об ошибке для крупных проектов, использующих более 2 ГБ памяти во время компоновки. Возможное решение на 64-разрядных системах Windows — использовать собственный 64-разрядный или кросс-компилятор и средства для создания кода. Это дает техническое преимущество больше памяти для 64-разрядных приложений. Если необходимо использовать 32-разрядный компилятор, так как выполняются в 32-разрядной системе, в некоторых случаях можно увеличить объем памяти, чтобы компоновщик 3 ГБ. Дополнительные сведения см. в разделе [настройки 4 ГБ: BCDEdit и Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473(v=vs.85).aspx) и [BCDEdit/set increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx) команды.  

Другой распространенной причиной является установкой Visual Studio прервана или неполна. В этом случае запустите установщик еще раз для восстановления или переустановки Visual Studio.  
  