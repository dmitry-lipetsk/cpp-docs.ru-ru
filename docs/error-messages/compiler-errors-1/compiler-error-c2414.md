---
title: "Ошибка компилятора C2414 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2414
dev_langs: C++
helpviewer_keywords: C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c6238cf17686eb168a2f120c00fc34655715a950
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2414"></a>Ошибка компилятора C2414
Недопустимое число операторов  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Чтобы устранить ошибку, проверьте указанные ниже возможные причины ее возникновения.  
  
1.  Код операции не поддерживает количество используемых операндов. Проверьте сборку с руководством по языку определить правильное число операндов.  
  
2.  Новый процесс поддерживает инструкцию с различным количеством операндов. Настройка [/arch (минимальная архитектура ЦП)](../../build/reference/arch-minimum-cpu-architecture.md) параметр, чтобы использовать более новый процессор.