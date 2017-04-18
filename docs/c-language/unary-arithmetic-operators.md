---
title: "Унарные арифметические операторы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "! оператор, унарные арифметические операторы"
  - "~ - оператор, оператор дополнения до единицы"
  - "+ - оператор, унарные операторы"
  - "арифметические операторы [C++], унарные"
  - "оператор поразрядного дополнения"
  - "восклицательные знаки"
  - "логическое отрицание"
  - "операторы [C], унарные"
  - "тильда (~) - оператор дополнения до единицы"
  - "унарные операторы"
ms.assetid: 78c91415-d469-499e-9dfe-4435350fd333
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Унарные арифметические операторы
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Оператор унарного плюса C, арифметического отрицания, дополнения и логического отрицания обсуждаются в следующем списке.  
  
|Оператор|Описание|  
|--------------|--------------|  
|**\+**|Оператор унарного плюса, предшествующий выражению в скобках, вызывает принудительную группировку включенных операций.  Он используется с выражениями, которые включают несколько ассоциативных или коммутативных бинарных операторов.  Операнд должен иметь арифметический тип.  Результат — значение этого операнда.  В отношении целочисленного операнда выполняется восходящее приведение целого типа.  Тип результата — это тип операнда более высокого уровня.|  
|**–**|Оператор арифметического отрицания создает отрицательную форму своего операнда \(дополнение двух\).  Операнд должен являться целочисленным значением или значением с плавающей запятой.  Этот оператор выполняет обычные арифметические преобразования.|  
|`~`|Оператор побитового дополнения \(или bitwise\-NOT\) создает побитовое дополнение своего операнда.  Операнд должен иметь целочисленный тип.  Этот оператор выполняет обычные арифметические преобразования; результат имеет тип операнда после преобразования.|  
|**\!**|Оператор логического отрицания \(logical\-NOT\) создает значение 0, если операнд равен true \(ненулевой\), и значение 1, если операнд равен false \(0\).  Результат имеет тип `int`.  Этот операнд должен представлять собой целочисленное значение, значение с плавающей запятой или значение указателя.|  
  
 Унарные арифметические операции с указателями недопустимы.  
  
## Примеры  
 В следующих примерах показаны унарные арифметические операторы:  
  
```  
short x = 987;  
    x = -x;  
```  
  
 В приведенном выше примере новое значение `x` является отрицательной формой 987 или –987.  
  
```  
unsigned short y = 0xAAAA;  
    y = ~y;  
```  
  
 В этом примере новое значение, присвоенное переменной `y`, является дополнением до единицы значения 0xAAAA или 0x5555 без знака.  
  
```  
if( !(x < y) )  
```  
  
 Если `x` больше или равно `y`, результат выражения равен 1 \(true\).  Если `x` меньше `y`, результат равен 0 \(false\).  
  
## См. также  
 [Выражения с унарными операторами](../Topic/Expressions%20with%20Unary%20Operators.md)