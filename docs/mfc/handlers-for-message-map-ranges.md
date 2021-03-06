---
title: "Обработчики для диапазонов схем сообщений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- message handlers [MFC]
- handlers [MFC], message-map ranges
- message maps [MFC], message handler functions
- message maps [MFC], ranges
- control-notification messages [MFC]
- command IDs [MFC], message mapping
- message-map ranges [MFC]
- handlers [MFC]
- message handling [MFC], message handler functions
- mappings [MFC], message ranges
- command handling [MFC], command update handlers
- controls [MFC], notifications
- handler functions [MFC], message-map ranges
- handler functions [MFC]
- command update handlers [MFC]
- command routing [MFC], command update handlers
- message ranges [MFC]
- handler functions [MFC], declaring
- message ranges [MFC], mapping
ms.assetid: a271478b-5e1c-46f5-9f29-e5be44b27d08
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 02b44288d21ab2df68468b0e39cb1ee35b7b8810
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="handlers-for-message-map-ranges"></a>Обработчики для диапазонов схем сообщений
В этой статье описывается ряд сообщений сопоставляются функция обработки одного сообщения (а не только одну функцию сопоставления одно сообщение).  
  
 Бывают случаи, когда требуется обработать несколько сообщений или управления уведомления точно так же. В таких случаях может потребоваться сопоставить все сообщения на функцию один обработчик. Диапазоны схемы сообщений позволяют сделать это для смежных сообщений:  
  
-   Можно сопоставить диапазоны идентификаторов команд для:  
  
    -   Функции обработчика команд.  
  
    -   Функция обработчика команды обновления.  
  
-   Функции обработки сообщений, можно сопоставить сообщения уведомление элемента управления для диапазона идентификаторов элементов управления.  
  
 В этой статье рассматриваются:  
  
-   [Создание записи схемы сообщений](#_core_writing_the_message.2d.map_entry)  
  
-   [Объявление функции обработчика](#_core_declaring_the_handler_function)  
  
-   [Пример для диапазона идентификаторов команд](#_core_example_for_a_range_of_command_ids)  
  
-   [Пример для диапазона идентификаторов элементов управления](#_core_example_for_a_range_of_control_ids)  
  
##  <a name="_core_writing_the_message.2d.map_entry"></a>Создание записи схемы сообщений  
 В. CPP файлов, добавьте запись в схеме сообщений, как показано в следующем примере:  
  
 [!code-cpp[NVC_MFCMessageHandling#6](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_1.cpp)]  
  
 Операция сопоставления сообщений состоит из следующих элементов:  
  
-   Макрос диапазона схемы сообщений:  
  
    -   [ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)  
  
    -   [ON_UPDATE_COMMAND_UI_RANGE](reference/message-map-macros-mfc.md#on_update_command_ui_range)  
  
    -   [ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)  
  
-   Параметры в макрос:  
  
     Первых двух макросов принимать три параметра:  
  
    -   Идентификатор команды диапазона  
  
    -   Идентификатор команды, которым он заканчивается  
  
    -   Имя функции обработчика сообщений  
  
     Диапазон идентификаторов, должны быть смежными.  
  
     Третий макрос `ON_CONTROL_RANGE`, принимает дополнительный параметр первый: сообщения уведомление элемента управления, например **EN_CHANGE**.  
  
##  <a name="_core_declaring_the_handler_function"></a>Объявление функции обработчика  
 Добавьте в объявление функции обработчика. H-файл. В следующем коде показано, как может выглядеть, как показано ниже:  
  
 [!code-cpp[NVC_MFCMessageHandling#7](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_2.h)]  
  
 Функции обработчика для одного команд обычно не принимают никаких параметров. За исключением функции обработчика обновления, функции обработчика для диапазонов схем сообщений требуют дополнительного параметра `nID`, типа **UINT**. Этот параметр является первым параметром. Дополнительный параметр включает идентификатор дополнительные команды, необходимые для задания команды, которая фактически Выбор пользователя.  
  
 Дополнительные сведения о требованиях к параметра для функции обработчика обновления см. в разделе [пример для диапазон команда идентификаторов](#_core_example_for_a_range_of_command_ids).  
  
##  <a name="_core_example_for_a_range_of_command_ids"></a>Пример для идентификаторов диапазона команды  
 Когда может использовать диапазоны, одним из примеров является при обработке команды, как и команда увеличения в образце MFC [HIERSVR](../visual-cpp-samples.md). Эта команда устанавливает масштаб представления его масштабирования между 25% и % 300 от нормального размера. Класс представления HIERSVR использует диапазон для обработки команд масштаб с записью карты сообщение наподобие этого:  
  
 [!code-cpp[NVC_MFCMessageHandling#8](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_3.cpp)]  
  
 При добавлении записи схемы сообщений, необходимо указать:  
  
-   Идентификаторы, открывающая и закрывающая непрерывный диапазон двух команд.  
  
     Ниже приводится `ID_VIEW_ZOOM25` и `ID_VIEW_ZOOM300`.  
  
-   Имя функции обработчика команд.  
  
     Здесь он имеет `OnZoom`.  
  
 В объявлении функции будет выглядеть так:  
  
 [!code-cpp[NVC_MFCMessageHandling#9](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_4.h)]  
  
 В случае функции обработчика обновления, аналогичные и более широко полезными. Довольно часто для записи `ON_UPDATE_COMMAND_UI` обработчики для некоторых команд и обнаружите записи или копирование тот же код снова и снова. Решение состоит в отображении диапазона идентификаторов для одного обновления с помощью функции обработчика команды `ON_UPDATE_COMMAND_UI_RANGE` макрос. Идентификаторы команд должны формировать непрерывный диапазон. Пример см. в разделе **OnUpdateZoom** обработчика и его `ON_UPDATE_COMMAND_UI_RANGE` записи схемы сообщений в класс образца HIERSVR представления.  
  
 Функции обработчика обновления, для одной команды обычно имеют один параметр `pCmdUI`, типа **CCmdUI\***. В отличие от функции обработчика функции обработчика обновления для диапазонов схем сообщений не требуют дополнительного параметра `nID`, типа **UINT**. Идентификатор команды, который необходим для указания команды фактически Выбор пользователя находится в `CCmdUI` объекта.  
  
##  <a name="_core_example_for_a_range_of_control_ids"></a>Пример для управления диапазоном идентификаторов  
 Другой случай интересных сопоставление сообщений уведомление элемента управления для диапазона идентификаторов элементов управления к одному обработчику. Предположим, что пользователь может щелкнуть любой из 10 кнопок. Чтобы сопоставить все 10 кнопок один обработчик, запись схемы сообщений будет выглядеть следующим образом:  
  
 [!code-cpp[NVC_MFCMessageHandling#10](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_5.cpp)]  
  
 При написании `ON_CONTROL_RANGE` укажите макрос на карте сообщение:  
  
-   Сообщение определенной уведомление элемента управления.  
  
     Здесь он имеет **BN_CLICKED**.  
  
-   Идентификатор элемента управления значения, связанные с непрерывный диапазон элементов управления.  
  
     Вот эти `IDC_BUTTON1` и `IDC_BUTTON10`.  
  
-   Имя функции обработки сообщений.  
  
     Здесь он имеет `OnButtonClicked`.  
  
 При написании функции обработчика, укажите дополнительного **UINT** параметра, как показано в следующем примере:  
  
 [!code-cpp[NVC_MFCMessageHandling#11](../mfc/codesnippet/cpp/handlers-for-message-map-ranges_6.cpp)]  
  
 `OnButtonClicked` Обработчик одного и того же **BN_CLICKED** сообщения не принимает никаких параметров. Один и тот же обработчик для диапазона кнопок принимает один **UINT**. Дополнительный параметр позволяет для идентификации определенного элемента управления, отвечающий за создание **BN_CLICKED** сообщения.  
  
 Код, показанный в примере является типичным: преобразование значение, передаваемое `int` в пределах диапазона сообщения и подтверждение, что это так. Затем можно выполнять некоторые разные действия в зависимости от того, что была нажата кнопка.  
  
## <a name="see-also"></a>См. также  
 [Объявление функций обработчиков сообщений](../mfc/declaring-message-handler-functions.md)
