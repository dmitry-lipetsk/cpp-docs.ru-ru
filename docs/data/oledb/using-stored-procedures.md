---
title: "С помощью хранимых процедур | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, Visual C++
- stored procedures, about stored procedures
- OLE DB provider templates, stored procedures
- stored procedures, OLE DB
ms.assetid: 90507e4c-eca2-46c9-ad8c-07e10dc1d41b
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 093cbd3d2ae101bbc06c45a920f8a2c108eb3bfa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="using-stored-procedures"></a>Использование хранимых процедур
Хранимая процедура является исполняемым объектом, хранящимся в базе данных. Вызов хранимой процедуры похож на вызов команды SQL. Использование хранимых процедур в источнике данных (вместо выполнения или подготовки инструкции в клиентском приложении) обеспечивает несколько преимуществ, включая повышение производительности, снижение сетевых издержек и улучшенную согласованность и точности.  
  
 Хранимая процедура может иметь любое количество (включая ноль) входные или выходные параметры и возвращаемое значение можно передать. Значения могут быть либо жестко параметр конкретные данные значения и не использует маркер параметра (вопросительный знак "?").  
  
> [!NOTE]
>  SQL Server среды CLR, хранимые процедуры, созданные с помощью Visual C++, которые должны быть скомпилированы с **/CLR: safe** параметр компилятора.  
  
 Поставщик OLE DB для SQL Server (SQLOLEDB) поддерживает следующие механизмы, используемые хранимыми процедурами для возвращения данных.  
  
-   Каждая инструкция SELECT в процедуре формирует результирующий набор.  
  
-   Процедура может возвращать данные через выходные параметры.  
  
-   Процедура может иметь целочисленный код возврата.  
  
> [!NOTE]
>  Нельзя использовать хранимые процедуры с поставщиком OLE DB для Jet, поскольку этот поставщик не поддерживает хранимые процедуры; в строках запроса, допустимы только константы.  
  
## <a name="see-also"></a>См. также  
 [Работа с шаблонами объекта-получателя OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)