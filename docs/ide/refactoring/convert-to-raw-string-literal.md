---
title: "Преобразовать в необработанный строковый литерал | Документы Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 12aa512270ecce4564561634f99be9cbf155448a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="convert-to-raw-string-literal"></a>Преобразовать в литерал неформатированной строки
**Что:** позволяет включать любую строку в C++ необработанного строкового литерала.

**Когда:** имеется строка с escape-символов, которые не должны обрабатываться как escape-символов.

**Почему:** удалось двойной escape-символы, но это обычно приводит к строки путаницу и может быть прочитан.  Необработанные строковые литералы с помощью строки значительно упрощает для чтения.

**Как:**

1. Наведите указатель на текст или мышь на строки, в которой для преобразования.

   ![Выделенный код](images/stringliteral_highlight.png)

1. Затем выполните одно из следующих действий.
   * **Клавиатура**
     * Нажмите клавишу **Ctrl +.** для запуска **Быстрые действия и рефакторинг** и выбрать пункт **преобразовать в необработанный строковый литерал** в контекстном меню.
   * **Мышь**
     * Щелкните его правой кнопкой мыши, выберите **Быстрые действия и рефакторинг** и выбрать пункт **преобразовать в необработанный строковый литерал** в контекстном меню.
     * Нажмите кнопку ![Lightbulb](images/bulb.png) значок, который отображается в левом поле и выберите **преобразовать в необработанный строковый литерал** в контекстном меню.

1. Строка будет немедленно преобразовать в необработанный строковый литерал.  

   ![Результат необработанного строкового литерала](images/stringliteral_result.png)