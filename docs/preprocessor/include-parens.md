---
title: "Include() | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: include()
dev_langs: C++
helpviewer_keywords: include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 794152aa30c57f22bc611ef758af23b2f205b7b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="include"></a>include()
**Конкретных C++**  
  
 Отключает автоматическое исключение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
include("Name1"[,"Name2", ...])  
```  
  
#### <a name="parameters"></a>Параметры  
 `Name1`  
 Первый элемент для принудительного включения.  
  
 `Name2`  
 Второй элемент для принудительного включения (при необходимости).  
  
## <a name="remarks"></a>Примечания  
 Библиотеки типов могут содержать определения элементов, которые определены в системных заголовочных файлах или других библиотеках типов. Директива `#import` пытается предотвратить ошибки об использовании нескольких определений, автоматически исключая такие элементы. Если элементы были исключены, как указано в [Предупреждение компилятора (уровень 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md), и они не должны были, этот атрибут можно использовать, чтобы отключить автоматическое исключение. Этот атрибут может принимать любое количество аргументов, каждый из которых является именем включаемого элемента библиотеки типов.  
  
 **КОНЕЦ определенного C++**  
  
## <a name="see-also"></a>См. также  
 [атрибуты #import](../preprocessor/hash-import-attributes-cpp.md)   
 [директива #import](../preprocessor/hash-import-directive-cpp.md)