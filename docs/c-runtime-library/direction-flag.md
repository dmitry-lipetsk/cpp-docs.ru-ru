---
title: "Флаг направления | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.flags
dev_langs: C++
helpviewer_keywords: direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e0a43bac113c013ecb93f5b6e84aa2075a052f8c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="direction-flag"></a>Флаг направления
Флаг направления — это флаг ЦП, относящийся к процессорам Intel 80x86. Он применяется для всех инструкций сборки, которые используют префикс REP (повтор), например для MOVS, MOVSD, MOVSW и др. Если флаг направления не установлен, предоставляемые этим инструкциям адреса увеличиваются.  
  
 Подпрограммы времени выполнения C предполагают, что флаг направления не установлен. Если вы используете другие функции совместно с функциями времени выполнения C, эти дополнительные функции должны не изменять флаг направления или восстанавливать его исходное состояние. Если предполагать, что флаг направления при входе не установлен, код времени выполнения будет более быстрым и эффективным.  
  
 Функции библиотеки времени выполнения C, например подпрограммы обработки строк и управления буфером, ожидают, что флаг направления не установлен.  
  
## <a name="see-also"></a>См. также  
 [Функции библиотеки CRT](../c-runtime-library/crt-library-features.md)