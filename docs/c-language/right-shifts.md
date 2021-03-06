---
title: "Сдвиги вправо | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 307cf91bf86f2912ad6cafa7e89f48e614c3865a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="right-shifts"></a>Сдвиги вправо
Результат сдвига вправо отрицательного целого типа со знаком  
  
 Сдвиг вправо отрицательного значения соответствует делению абсолютного значения на два с округлением вниз. Например, значение `short` со знаком, равное –253 (шестнадцатеричное 0xFF03, двоичное 11111111 00000011), сдвинутое вправо на один бит, дает значение –127 (шестнадцатеричное 0xFF81, двоичное 11111111 10000001). Положительное значение 253, сдвинутое вправо, дает значение +126.  
  
 При сдвиге вправо бит знака целочисленных типов со знаком сохраняется. При сдвиге вправо целого числа со знаком старший значащий бит остается установленным. Например, если число 0xF0000000 имеет `int` со знаком, то при сдвиге вправо получается число 0xF8000000. Если 32 раза выполнить сдвиг вправо отрицательного `int`, в результате получается число 0xFFFFFFFF.  
  
 При сдвиге вправо целого числа без знака старший значащий бит очищается. Например, если число 0xF000 не имеет знака, в результате получается 0x7800. При сдвиге 32 раза `unsigned` или положительного числа `int` вправо получается число 0x00000000.  
  
## <a name="see-also"></a>См. также  
 [Целые числа](../c-language/integers.md)