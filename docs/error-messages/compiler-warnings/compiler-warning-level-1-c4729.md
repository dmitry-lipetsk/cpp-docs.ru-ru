---
title: "Предупреждение (уровень 1) C4729 компилятора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4729
dev_langs: C++
helpviewer_keywords: C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 57d6d5dc95ce3ef9cf4890b93ef1ab3abe2d6601
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4729"></a>Предупреждение компилятора (уровень 1) C4729
слишком большая функция для предупреждений, основанных на оптимизации структуры кода  
  
 Это предупреждение возникает в случае, если функция слишком велика для компиляции с надежной проверкой ситуаций, в которых могут возникать предупреждения. Это предупреждение появляется только в том случае, если используется параметр компилятора [/Od](../../build/reference/od-disable-debug.md) .  
  
 Чтобы устранить это предупреждение, разделите функцию на более мелкие функции.