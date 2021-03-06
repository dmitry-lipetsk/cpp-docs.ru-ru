---
title: "Параметры, мастер страницы свойств ATL | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.ppg.options
dev_langs: C++
helpviewer_keywords: ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cbc27457fa3ace7b1cdfad4894bbd296739de2ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="options-atl-property-page-wizard"></a>Параметры, мастер страниц свойств ATL
Эта страница мастера позволяет определить потоковую модель и уровень агрегирования страницы свойств, который вы создаете.  
  
 **Модель потоков**  
 Указывает потоковую модель, используемую на странице свойств.  
  
 В разделе [указание потоковой модели проекта](../../atl/specifying-the-threading-model-for-a-project-atl.md) для получения дополнительной информации.  
  
|Параметр|Описание:|  
|------------|-----------------|  
|`Single`|На странице свойств выполняется только в основном потоке COM.|  
|**Подразделение**|На странице свойств могут создаваться в любом однопотоковом подразделении. По умолчанию.|  
  
 **Статистическая обработка**  
 Добавляет поддержку статистической обработки для страницы свойств, который вы создаете. В разделе [статистической обработки](../../atl/aggregation.md) для получения дополнительной информации.  
  
|Параметр|Описание:|  
|------------|-----------------|  
|**Да**|Создание страницы свойств, который может быть статистически вычислена.|  
|**No**|Создание страницы свойств, невозможно выполнить статистическую обработку.|  
|**Только**|Создание страницы свойств, которое может быть создано только путем агрегирования.|  
  
## <a name="see-also"></a>См. также  
 [Мастер страницы свойств ATL](../../atl/reference/atl-property-page-wizard.md)   
 [Строки, мастер страницы свойств ATL](../../atl/reference/strings-atl-property-page-wizard.md)

