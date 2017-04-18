---
title: "Бинарные операторы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "двоичные операторы"
  - "операторы для выбора членов"
  - "операторы [C++], двоичные"
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Бинарные операторы
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

В следующей таблице приведен список операторов, которые можно перегрузить.  
  
### Переопределяемые бинарные операторы  
  
|Оператор|Имя|  
|--------------|---------|  
|**,**|Comma|  
|`!=`|Неравенство|  
|`%`|Модуль|  
|`%=`|Модуль\/назначение|  
|**&**|Побитовое И|  
|**&&**|Логическое И|  
|**&\=**|Побитовое И\/назначение|  
|**\***|Умножение|  
|**\*\=**|Умножение\/назначение|  
|**\+**|Сложение|  
|`+=`|Сложение\/назначение|  
|**–**|Вычитание|  
|**–\=**|Вычитание\/назначение|  
|**–\>**|Выбор члена|  
|**–\>\***|Выбор указателя на член|  
|**\/**|Деление|  
|`/=`|Деление\/назначение|  
|**\<**|Меньше|  
|**\<\<**|Сдвиг влево|  
|**\<\<\=**|Сдвиг влево\/назначение|  
|**\<\=**|Меньше или равно|  
|**\=**|Присваивание|  
|`==`|Равенство|  
|**\>**|Больше|  
|**\>\=**|Больше или равно|  
|**\>\>**|Сдвиг вправо|  
|**\>\>\=**|Сдвиг вправо\/назначение|  
|**^**|Исключающее ИЛИ|  
|`^=`|Исключающее ИЛИ\/назначение|  
|**&#124;**|Побитовое включающее ИЛИ|  
|`&#124;=`|Побитовое включающее ИЛИ\/назначение|  
|`&#124;&#124;`|Логическое ИЛИ|  
  
 Чтобы объявить функцию бинарного оператора как нестатический член, необходимо объявить ее в виде  
  
 *возвращаемый\-тип* **оператор**`op`**\(** `arg` **\)**  
  
 где *ret\-type* — возвращаемое значение, `op` — один из операторов, перечисленных в предыдущей таблице, а `arg` — аргумент любого типа.  
  
 Чтобы объявить функцию бинарного оператора как глобальную функцию, необходимо объявить ее в виде  
  
 *ret\-type* **operator**`op`**\(** `arg1`**,** `arg2` **\)**  
  
 где *ret\-type* и `op` — элементы, описанные для функций операторов членов, а `arg1` и `arg2` — аргументы.  Хотя бы один из аргументов должен принадлежать типу класса.  
  
> [!NOTE]
>  Ограничений на возвращаемые типы бинарных операторов нет, однако большинство пользовательских бинарных операторов возвращает тип класса или ссылку на тип класса.  
  
## См. также  
 [Перегрузка операторов](../cpp/operator-overloading.md)