---
title: "Регистрация классов Window | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WndProc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxRegisterWndClass - метод"
  - "классы [C++], регистрация классов окон"
  - "MFC - библиотека, окна"
  - "регистрация классов окон"
  - "реестр, регистрация классов"
  - "классы окон, регистрация"
  - "WinMain - метод"
  - "WinMain - метод, и регистрация классов окон"
  - "WndProc - метод"
ms.assetid: 30994bc4-a362-43da-bcc5-1bf67a3fc929
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Регистрация классов Window
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Окно «классы» в традиционном программировании для Windows определяет характеристики «класса» \(не класс C\+\+\), из которого можно создать любое количество окон.  Этот тип класса шаблона или модели для создания окна.  
  
## Регистрация класса окна в традиционных программах для Windows  
 В традиционной программы для Windows, без MFC, необходимо процесс все сообщения в окно в соответствующей процедуре «окна» или «**WndProc**». **WndProc** Связан с окном «посредством процесса регистрации класса окна».  Главное окно зарегистрированное в функции `WinMain`, но другие классы windows можно зарегистрировать в любом месте приложения.  Регистрация зависит от структуры, содержащей указатель на функцию **WndProc** вместе с спецификациями для курсора, кисти фона и т д  Структура передается в качестве параметра, а также строковым именем класса, прежнем в вызове функции **RegisterClass**.  Таким образом, класс регистрации может совместно использоваться несколькими окнами.  
  
## Регистрация класса окна в программах MFC  
 В отличие от этого, большинство действие регистрации класса окна выполняется автоматически в структурной программе MFC.  При использовании MFC, обычно является производным класса окна C\+\+ из существующего класса библиотеки с помощью стандартного синтаксиса C\+\+ для наследования классов.  Платформа по\-прежнему используется традиционные классы регистрации «,» и предоставляет несколько стандартных одного, зарегистрированный для пользователя.  Можно зарегистрировать классы регистрации дополнительных глобальная путем вызова функции [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md), а затем передав зарегистрирован класс в функцию\-член **Создать**`CWnd`.  Как описано здесь, стандартных «класс» регистрации в Windows не следует путать с классом C\+\+.  
  
 Дополнительные сведения см. в разделе [Техническое примечание 1](../mfc/tn001-window-class-registration.md).  
  
## См. также  
 [Создание окон](../Topic/Creating%20Windows.md)