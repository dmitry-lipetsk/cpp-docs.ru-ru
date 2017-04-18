---
title: "Строки языка | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.strings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "строки языка"
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# Строки языка
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Функции `setlocale` и `_create_locale` могут использовать поддерживаемые языки API многоязыковой поддержки Windows для операционных систем, которые не используют кодовую страницу Юникода.  Список всех поддерживаемых языков по версиям операционных систем см. в разделе [API многоязыковой поддержки \(NLS\)](http://msdn.microsoft.com/goglobal/bb896001.aspx).  Переменная с названием языка может быть любым из значений, перечисленных в столбцах **Язык** и **Сокращение названия языка** списка поддерживаемых языков.  Реализация библиотеки времени выполнения C также поддерживает эти строки языка:  
  
|Строка языка|Соответствующее название языкового стандарта|  
|------------------|--------------------------------------------------|  
|american|en\-US|  
|american english|en\-US|  
|american\-english|en\-US|  
|australian|en\-AU|  
|belgian|nl\-BE|  
|canadian|en\-CA|  
|chh|zh\-HK|  
|chi|zh\-SG|  
|chinese|zh|  
|chinese\-hongkong|zh\-HK|  
|chinese\-simplified|zh\-CN|  
|chinese\-singapore|zh\-SG|  
|chinese\-traditional|zh\-TW|  
|dutch\-belgian|nl\-BE|  
|english\-american|en\-US|  
|english\-aus|en\-AU|  
|english\-belize|en\-BZ|  
|english\-can|en\-CA|  
|english\-caribbean|en\-029|  
|english\-ire|en\-IE|  
|english\-jamaica|en\-JM|  
|english\-nz|en\-NZ|  
|english\-south africa|en\-ZA|  
|english\-trinidad y tobago|en\-TT|  
|english\-uk|en\-GB|  
|english\-us|en\-US|  
|english\-usa|en\-US|  
|french\-belgian|fr\-BE|  
|french\-canadian|fr\-CA|  
|french\-luxembourg|fr\-LU|  
|french\-swiss|fr\-CH|  
|german\-austrian|de\-AT|  
|german\-lichtenstein|de\-LI|  
|german\-luxembourg|de\-LU|  
|german\-swiss|de\-CH|  
|irish\-english|en\-IE|  
|italian\-swiss|it\-CH|  
|norwegian|нет|  
|norwegian\-bokmal|nb\-NO|  
|norwegian\-nynorsk|nn\-NO|  
|portuguese\-brazilian|pt\-BR|  
|spanish\-argentina|es\-AR|  
|spanish\-bolivia|es\-BO|  
|spanish\-chile|es\-CL|  
|spanish\-colombia|es\-CO|  
|spanish\-costa rica|es\-CR|  
|spanish\-dominican republic|es\-DO|  
|spanish\-ecuador|es\-EC|  
|spanish\-el salvador|es\-SV|  
|spanish\-guatemala|es\-GT|  
|spanish\-honduras|es\-HN|  
|spanish\-mexican|es\-MX|  
|spanish\-modern|es\-ES|  
|spanish\-nicaragua|es\-NI|  
|spanish\-panama|es\-PA|  
|spanish\-paraguay|es\-PY|  
|spanish\-peru|es\-PE|  
|spanish\-puerto rico|es\-PR|  
|spanish\-uruguay|es\-UY|  
|spanish\-venezuela|es\-VE|  
|swedish\-finland|sv\-FI|  
|swiss|de\-CH|  
|uk|en\-GB|  
|us|en\-US|  
|usa|en\-US|  
  
## См. также  
 [Строки имени языкового стандарта, языка и страны и региона](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Строки стран или регионов](../c-runtime-library/country-region-strings.md)   
 [setlocale, \_wsetlocale](../Topic/setlocale,%20_wsetlocale.md)   
 [\_create\_locale, \_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)