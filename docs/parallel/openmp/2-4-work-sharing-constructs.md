---
title: "2.4 конструкции совместной работы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 476e4e23b22527accaa095d80b827c95aed58c15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="24-work-sharing-constructs"></a>2.4 Конструкции совместной работы
Конструкции совместной работы распределяет выполнение связанные инструкции между членами команды, в которых она возникает. Директивы совместной работы не запускать новые потоки, и нет не подразумеваемых барьера операции конструкции совместной работы.  
  
 Создает последовательность совместной работы и **барьера** обнаружил директивы должны быть одинаковыми для каждого потока в команде.  
  
 OpenMP определяет следующие конструкции совместной работы и описаны в следующих разделах:  
  
-   **для** директивы  
  
-   **разделы** директивы  
  
-   **один** директивы