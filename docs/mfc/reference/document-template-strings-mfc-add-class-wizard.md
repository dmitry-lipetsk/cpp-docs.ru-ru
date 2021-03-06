---
title: "Строки шаблонов документов мастер добавления классов MFC | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.class.mfc.simple.doctemp
dev_langs: C++
helpviewer_keywords: MFC Add Class Wizard, document control strings
ms.assetid: 14e1c834-5e79-4dbd-811f-ec8f0a9cdcb2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3a9d37b1a886c28d267cd7a387317edce6bf7f3a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="document-template-strings-mfc-add-class-wizard"></a>Страница "Строки шаблонов документов", мастер добавления классов MFC
Эта страница мастера доступна только для классов, отвечающих следующим критериям:  
  
-   Проект MFC поддерживает архитектуру "документ представление".  
  
-   Базовый класс нового класса является [CFormView](../../mfc/reference/cformview-class.md).  
  
-   Флажок **\''создавать ресурсы** проверяется на **имена** раздел [мастер классов MFC](../../mfc/reference/mfc-add-class-wizard.md).  
  
 Мастер предоставляет значения по умолчанию для следующих значений для представления конструктора форм, управления и локализации. Поскольку большинство строки шаблонов документов доступны и используемые пользователями формы, они переводятся в **язык ресурсов** в [типы приложений](../../mfc/reference/application-type-mfc-application-wizard.md) мастера приложений MFC При создании проекта.  
  
> [!NOTE]
>  Мастер не обеспечивает автоматическую поддержку печати для классов, производных от `CFormView`.  
  
 В разделе [шаблоны документов и процесс создания документов и представлений](../../mfc/document-templates-and-the-document-view-creation-process.md) для получения дополнительной информации.  
  
## <a name="nonlocalized-strings"></a>Нелокализованные строки  
 Применяется к приложениям, создающим пользовательские документы. Пользователи могут открывать и сохранять документы, легко Если тип документа имеет расширение файла и идентификатор типа файла. Эти элементы не локализованы, так как они используются системой, а не пользователем.  
  
 **Расширение файла**  
 Задает расширение файла, связанное с типом документа для данного приложения Windows forms. По умолчанию расширение файла, на основе имени класса. Например, если новый класс MFC называется **CWidget**, по умолчанию файл имеет расширение. wid. Фильтры файлов используется расширение файла и **откройте** и **сохранение** диалоговым окнам.  
  
 Если изменить расширение файла, это изменение отражается в **имя фильтра** поле.  
  
> [!NOTE]
>  Если изменить расширение файла по умолчанию, не включайте периода.  
  
 **Идентификатор типа файла**  
 Задает метку для данного типа документа в системном реестре.  
  
## <a name="localized-strings"></a>Локализованные строки  
 Создает строки, связанные с формами и документы, которые считываются и используемый пользователей приложения, поэтому эти строки локализуются.  
  
 **Имя типа документа**  
 Определяет тип документа, в котором могут быть сгруппированы документа приложения. По умолчанию он основан на имя класса. Например, если новый класс MFC называется **CWidget**, по умолчанию имя типа документа является мини-приложения. Изменение значения по умолчанию не изменяет другие параметры в этом окне.  
  
 **Имя фильтра**  
 Задает имя, которое пользователи смогут указывать для поиска файлов заданного типа. Этот параметр доступен из **файлы типа** и **тип** вариантов стандартных Windows **откройте** и **сохранение** диалоговым окнам. По умолчанию имя основано на имени проекта, а также файлы с расширением указано в **расширение файла**. Например, если проект имеет имя мини-приложения, и расширение файла .wid **имя фильтра** является файлы мини-приложения (*.wid) по умолчанию.  
  
 **Короткое имя создаваемого файла**  
 Задает имя, отображаемое в окнах Стандартная `New` диалоговое окно, если в проекте имеется несколько шаблонов документов. Если приложение является [сервера автоматизации](../../mfc/automation-servers.md), это имя используется в качестве краткого имени объекта автоматизации. По умолчанию это имя основано на имени класса.  
  
 **Длинное имя типа файла**  
 Задает имя типа файла в системном реестре. Если ваше приложение сервера автоматизации, это имя используется в качестве длинного имени объекта автоматизации. По умолчанию это имя основано на имени класса. Документ. Например, если имя класса — **CWidget**, **длинное имя типа файла** является документом мини-приложения.  
  
 **Класс документа**  
 Указывает класс документа проекта. По умолчанию этот класс является основного приложения документа, как указано в [обзор созданных классов](../../mfc/reference/generated-classes-mfc-application-wizard.md) мастера приложений MFC. При добавлении других классов документа в проекте, можно выбрать другой класс в списке.  
  
## <a name="see-also"></a>См. также  
 [Мастер добавления классов MFC](../../mfc/reference/mfc-add-class-wizard.md)   
 [Класс MFC](../../mfc/reference/adding-an-mfc-class.md)   
 [Добавление класса](../../ide/adding-a-class-visual-cpp.md)
