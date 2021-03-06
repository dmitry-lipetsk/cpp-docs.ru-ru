---
title: "Справочник по языку Visual C++ (C + +/ CX) | Документы Microsoft"
ms.custom: 
ms.date: 09/15/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0867cb30f1337ffaf1cb726a0c52977899f02d0a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="visual-c-language-reference-ccx"></a>Справочник по языку C++ (C++/CX)

C + +/ CX — это набор расширений языка C++, позволяющий создавать приложения для Windows и компоненты среды выполнения Windows с идиоматикой, максимально близкой к современному C++. Использование C + +/ CX для написания приложений для Windows и компонентов в машинном коде, легко взаимодействующих с Visual C#, Visual Basic и JavaScript, а также другими языками, поддерживающими среды выполнения Windows. В редких случаях, когда требуется прямой доступ к интерфейсам COM или код без поддержки исключений, можно использовать [библиотеки шаблонов C++ (WRL) среды выполнения Windows](../windows/windows-runtime-cpp-template-library-wrl.md).

Новая модель представляет следующее поколение средств создания машинного кода для Windows в C++. С его помощью можно создавать:

- Приложения C++ универсальной платформы Windows (UWP), использующие XAML для определения пользовательского интерфейса и используется собственный стек. Дополнительные сведения см. в разделе [создать приложение «hello world» в C++ (UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- Компоненты среды выполнения Windows на C++, которые могут использоваться приложениями для Windows на базе JavaScript. Дополнительные сведения см. в разделе [создание компонентов среды выполнения Windows в C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Игры Windows на базе DirectX и приложения, активно использующие графику. Дополнительные сведения см. в разделе [создание простой игры UWP с DirectX](/windows/uwp/gaming/tutorial--create-your-first-metro-style-directx-game).

## <a name="related-articles"></a>Связанные статьи

|||
|-|-|
|[Краткий справочник](../cppcx/quick-reference-c-cx.md)|Таблица ключевых слов и операторов для C + +/ CX.|
|[Система типов](../cppcx/type-system-c-cx.md)|Описывает основные C + +/ CX типы и программные конструкции и как использовать C + +/ CX для использования и создания типов среды выполнения Windows.|
|[Построение приложений и библиотек](../cppcx/building-apps-and-libraries-c-cx.md)|Принципы использования интегрированной среды разработки для построения приложений и подключения статических библиотек и DLL.|
|[Взаимодействие с другими языками](../cppcx/interoperating-with-other-languages-c-cx.md)|Рассматриваются как компоненты, написанные с использованием C + +/ CX можно использовать с компонентами, написанными на языке JavaScript, любом управляемом языке или [!INCLUDE[cppwrl](../cppcx/includes/cppwrl-md.md)].|
|[Работа с потоками и маршалинг](../cppcx/threading-and-marshaling-c-cx.md)|Принципы указания поведения при использовании потоков и маршалинга в создаваемых компонентах.|
|[Справочник по пространствам имен](../cppcx/namespaces-reference-c-cx.md)|Справочная документация по следующим пространствам имен: по умолчанию, Platform, Platform::Collections и другим связанным с ними пространствам имен.|
|[Функции CRT, которые не поддерживаются в приложениях универсальной платформы Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)|Список функций CRT, недоступных для использования в приложениях среды выполнения Windows.|
|[Практические руководства по приложениям Windows 10](http://msdn.microsoft.com/library/windows/apps/xaml/mt244352.aspx)|Общие рекомендации по приложениям Windows 10, а также ссылки на дополнительную информацию.|
|[C + +/ CX: часть 0 из \[ n \]: введение](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction/)<br /><br />[C + +/ CX: часть 1 из \[ n \]: простого класса](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class/)<br /><br />[C + +/ CX: часть 2 из \[ n \]: типы с крышками](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C + +/ CX: часть 3 из \[ n \]: В процессе разработки](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)<br /><br />[C + +/ CX: часть 4 из \[ n \]: статические функции-члены](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions/)|Вводные серия записей в блоге Visual C++, C + +/ CX.|
