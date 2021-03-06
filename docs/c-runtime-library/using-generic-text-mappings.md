---
title: "Использование универсальных текстовых сопоставлений | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _UNICODE
dev_langs: C++
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- _UNICODE constant
- TXCHAR type
- generic-text mappings
- _TSCHAR type
- T type
- mappings, generic-text
- _TUCHAR type
- MBCS data type
- _MBCS data type
- _TEXT type
- UNICODE constant
- _T type
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1d0049643ef7a3695eef8c3271e22586b5c7454d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="using-generic-text-mappings"></a>Использование универсальных текстовых сопоставлений
**Блок, относящийся только к системам Microsoft**  
  
 Чтобы упростить написание кода для разных международных рынков, в библиотеке времени выполнения Microsoft имеются специфичные для Microsoft "универсальные текстовые" сопоставления для многих типов данных, подпрограмм и других объектов. Эти сопоставления определяются в TCHAR.H. Данные сопоставления имен можно использовать для написания универсального кода, который можно компилировать в любом из трех типов наборов символов (ASCII (однобайтовая кодировка), многобайтовая кодировка или Юникод), в зависимости от константы манифеста, указанной с помощью оператора `#define`. Универсальные текстовые сопоставления представляют собой расширения Microsoft, несовместимые со стандартами ANSI.  
  
### <a name="preprocessor-directives-for-generic-text-mappings"></a>Директивы препроцессора для универсальных текстовых сопоставлений  
  
|#define|Скомпилированная версия|Пример|  
|--------------|----------------------|-------------|  
|`_UNICODE`|Юникод (расширенные символы)|`_tcsrev` сопоставляется с `_wcsrev`|  
|`_MBCS`|Многобайтовые символы|`_tcsrev` сопоставляется с `_mbsrev`|  
|Нет (по умолчанию: не определена ни константа `_UNICODE`, ни константа `_MBCS`)|Однобайтовая кодировка (ASCII)|`_tcsrev` сопоставляется с `strrev`|  
  
 Например, определенная в файле TCHAR.H универсальная текстовая функция `_tcsrev` сопоставляется с функцией `mbsrev`, если в программе определена константа `MBCS`, или с функцией `_wcsrev`, если определена константа `_UNICODE`. В противном случае `_tcsrev` сопоставляется с `strrev`.  
  
 Универсальный текстовый тип данных `_TCHAR`, также определенный в TCHAR.H, сопоставляется типу `char`, если определена константа `_MBCS`, типу `wchar_t`, если определена константа `_UNICODE`, и типу `char`, если ни одна из констант не определена. Для удобства в файле TCHAR.H также предусмотрены другие сопоставления типов данных, однако `_TCHAR` является наиболее полезным типом.  
  
### <a name="generic-text-data-type-mappings"></a>Сопоставления типов данных универсального текста  
  
|Имя универсального текстового типа данных|Однобайтовая кодировка (_UNICODE, _MBCS не определены)|_MBCS определено|_UNICODE определено|  
|----------------------------------|--------------------------------------------|--------------------|-----------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_TINT`|`int`|`int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` или `_TEXT`|Не действует (удаляется препроцессором)|Не действует (удаляется препроцессором)|`L` (преобразует следующий символ или строку в аналог в Юникоде)|  
  
 Полный список универсальных текстовых сопоставлений для подпрограмм, переменных и других объектов см. в статье [Универсальные текстовые сопоставления](../c-runtime-library/generic-text-mappings.md).  
  
 В следующих примерах кода показано использование функций `_TCHAR` и `_tcsrev` для сопоставления моделям многобайтовой кодировки, Юникод и однобайтовой кодировки.  
  
```  
_TCHAR *RetVal, *szString;  
RetVal = _tcsrev(szString);  
```  
  
 Если указано `MBCS`, препроцессор сопоставляет предыдущий фрагмент следующему коду:  
  
```  
char *RetVal, *szString;  
RetVal = _mbsrev(szString);  
```  
  
 Если указано `_UNICODE`, препроцессор сопоставляет тот же фрагмент следующему коду:  
  
```  
wchar_t *RetVal, *szString;  
RetVal = _wcsrev(szString);  
```  
  
 Если не определена ни константа `_MBCS`, ни константа `_UNICODE`, препроцессор сопоставляет этот фрагмент коду в однобайтовой кодировке ASCII, как показано ниже:  
  
```  
char *RetVal, *szString;  
RetVal = strrev(szString);  
```  
  
 Таким образом, можно создавать, обслуживать и компилировать единый исходный файл кода, который будет выполняться с подпрограммами, использующими любую из трех описанных выше кодировок.  
  
 **Завершение блока, относящегося только к системам Майкрософт**  
  
## <a name="see-also"></a>См. также  
 [Универсальные текстовые сопоставления](../c-runtime-library/generic-text-mappings.md)   
 [Сопоставления типов данных](../c-runtime-library/data-type-mappings.md)   
 [Сопоставления констант и глобальных переменных](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [Сопоставления подпрограмм](../c-runtime-library/routine-mappings.md)   
 [Пример программы с использованием универсального текста](../c-runtime-library/a-sample-generic-text-program.md)