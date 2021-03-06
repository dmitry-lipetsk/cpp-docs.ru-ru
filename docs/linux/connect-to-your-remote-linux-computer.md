---
title: "Подключение к удаленному компьютеру Linux | Документы Майкрософт"
ms.custom: 
ms.date: 11/06/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-linux
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5eeaa683-4e63-4c46-99ef-2d5f294040d4
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 4ff19875064302e891236c931f28ebef630904e4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="connect-to-your-remote-linux-computer"></a>Подключение к удаленному компьютеру Linux

При сборке код Linux копируется на удаленный компьютер Linux и затем компилируются в этой системе в соответствии с параметрами, выбранными в Visual Studio.  Чтобы настроить удаленное подключение:

1. Постройте проект в первый раз или вручную создайте новую запись, выбрав в меню  **> Параметры**, затем открыв узел **Кроссплатформенный > Диспетчер подключений** и нажав кнопку **Добавить**.

   ![Диспетчер подключений](media/settings_connectionmanager.png)

   В любом сценарии будет отображаться окно **Подключение к удаленной системе**.
   
   ![Подключение к удаленной системе](media/connect.png)

1. Введите следующую информацию.

   | Ввод | Описание:
   | ----- | ---
   | **Имя узла**           | Имя или IP-адрес целевого устройства
   | **Порт**                | Порт, в котором работает служба SSH, обычно 22
   | **Имя пользователя**           | Пользователь для проверки подлинности
   | **Тип проверки подлинности** | Поддерживается и пароль, и закрытый ключ
   | **Пароль**            | Пароль для указанного имени пользователя
   | **Файл закрытого ключа**    | Закрытый ключ, созданный для ssh-подключения
   | **Парольная фраза**          | Парольная фраза, используемая с закрытым ключом, выбранным выше

1. Нажмите кнопку **Подключить**, чтобы попытаться подключиться к удаленному компьютеру.  Если подключение не удастся, поля ввода, которые необходимо изменить, будут выделены красным цветом.

   ![Ошибки диспетчера подключений](media/settings_connectionmanagererror.png)