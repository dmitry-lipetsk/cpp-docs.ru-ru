---
title: "_isctype, iswctype, _isctype_l, _iswctype_l | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _isctype_l
- iswctype
- _iswctype_l
- _isctype
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- iswctype
- _isctype
- _isctype_l
- _iswctype
- isctype
- iswctype_l
- isctype_l
- _iswctype_l
dev_langs:
- C++
helpviewer_keywords:
- isctype_l function
- iswctype_l function
- iswctype function
- _isctype function
- _isctype_l function
- _iswctype_l function
- isctype function
- _iswctype function
ms.assetid: cf7509b7-12fc-4d95-8140-ad2eb98173d3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fe43830894be3c004fb21598b0324b864fe5b9b0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="isctype-iswctype-isctypel-iswctypel"></a>_isctype, iswctype, _isctype_l, _iswctype_l
Проверяет `c` на наличие свойства, заданного аргументом `desc`. Для каждого допустимого значения аргумента `desc` существует эквивалентная подпрограмма, работающая с расширенными символами.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
int _isctype(  
   int c,  
   _ctype_t desc  
);  
int _isctype_l(  
   int c,  
   _ctype_t desc,  
   _locale_t locale  
);  
int iswctype(  
   wint_t c,  
   wctype_t desc   
);  
int _iswctype_l(  
   wint_t c,  
   wctype_t desc,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `c`  
 Проверяемое целое число.  
  
 `desc`  
 Свойство для проверки. Как правило, извлекается с использованием ctype или [wctype](../../c-runtime-library/reference/wctype.md).  
  
 `locale`  
 Языковой стандарт, используемый для любых зависящих от языкового стандарта проверок.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Функции `_isctype` и `iswctype` возвращают ненулевое значение, если `c` в текущем языковом стандарте имеет свойство, заданное аргументом `desc`, и 0 в остальных случаях. Версии этих функций с суффиксом `_l` идентичны, за исключением того, что для поведения, зависящего от языкового стандарта, они используют переданный параметр языкового стандарта вместо текущего языкового стандарта. Для получения дополнительной информации см. [Locale](../../c-runtime-library/locale.md).  
  
 Поведение функций `_isctype` и `_isctype_l` не определено, если `c` не является концом файла или не находится в диапазоне от 0 по 0xFF включительно. Если используется библиотека отладки CRT и `c` не является одним из этих значений, функции вызывают утверждение.  
  
### <a name="generic-text-routine-mappings"></a>Сопоставления подпрограмм обработки обычного текста  
  
|Подпрограмма Tchar.h|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`n/a`|`_isctype`|`n/a`|`_iswctype`|  
|`n/a`|`_isctype_l`|`n/a`|`_iswctype_l`|  
  
## <a name="requirements"></a>Требования  
  
|Подпрограмма|Обязательный заголовок|  
|-------------|---------------------|  
|`_isctype`|\<ctype.h>|  
|`iswctype`|\<ctype.h> или \<wchar.h>|  
|`_isctype_l`|\<ctype.h>|  
|`_iswctype_l`|\<ctype.h> или \<wchar.h>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md) во введении.  
  
## <a name="libraries"></a>Библиотеки  
 Все версии [библиотек времени выполнения языка C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>См. также  
 [Классификация символов](../../c-runtime-library/character-classification.md)   
 [Языковой стандарт](../../c-runtime-library/locale.md)   
 [Подпрограммы is, isw](../../c-runtime-library/is-isw-routines.md)