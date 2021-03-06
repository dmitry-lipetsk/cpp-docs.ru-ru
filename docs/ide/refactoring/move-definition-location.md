---
title: "Переместить расположение определения | Документы Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 838f3d01f5e6d8612948304b80b79cf9c7cb4720
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="move-definition-location"></a>Переместить расположение определения
**Что:** позволяет немедленно перенести определение функции в соответствующий файл заголовка.

**Когда:** имеется функция, которую требуется переместить в файл заголовка.  

**Почему:** можно вручную переместить функции, но этот компонент будет их перемещать автоматически, создание файла заголовка, при необходимости.

**Как:**

1. Поместите курсор текст или мыши с помощью функции, для которого требуется переместить.

   ![Выделенный код](images/movedefinition_highlight.png)

1. Затем выполните одно из следующих действий.
   * **Клавиатура**
     * Нажмите клавишу **Ctrl +.** для запуска **Быстрые действия и рефакторинг** и выбрать пункт **переместить расположение определения** в контекстном меню.
   * **Мышь**
     * Щелкните правой кнопкой мыши и выберите **Быстрые действия и рефакторинг** и выбрать пункт **переместить расположение определения** в контекстном меню.

1. Функция будут перемещены в соответствующем файле заголовка, которое отображается во всплывающем окне предварительного просмотра.  Если файл заголовка не существует, он также будет создан и помещен в проекте.

   ![Создать объявление или определение привести](images/movedefinition_result.png)
