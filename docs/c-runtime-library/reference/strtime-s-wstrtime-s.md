---
title: "_strtime_s, _wstrtime_s | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _wstrtime_s
- _strtime_s
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wstrtime_s
- strtime_s
- wstrtime_s
- _strtime_s
dev_langs:
- C++
helpviewer_keywords:
- wstrtime_s function
- copying time to buffers
- strtime_s function
- _wstrtime_s function
- time, copying
- _strtime_s function
ms.assetid: 42acf013-c334-485d-b610-84c0af8a46ec
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c93a98d7be13b19357b1308183519650411ec775
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="strtimes-wstrtimes"></a>_strtime_s, _wstrtime_s
Копирует текущее время в буфер. Это версии функции [_strtime, _wstrtime](../../c-runtime-library/reference/strtime-wstrtime.md) с усовершенствованной безопасностью, как описано в разделе [Функции безопасности в CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
errno_t _strtime_s(  
   char *buffer,  
   size_t numberOfElements  
);  
errno_t _wstrtime_s(  
   wchar_t *buffer,  
   size_t numberOfElements  
);  
template <size_t size>  
errno_t _strtime_s(  
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
errno_t _wstrtime_s(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Параметры  
 [выходной] `buffer`  
 Буфер длиной не менее 10 символов, в который будет записано время.  
  
 [in] `numberOfElements`  
 Размер буфера.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Нуль при успешном завершении.  
  
 Если возникает ошибка, вызывается обработчик недопустимого параметра, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). В случае сбоя возвращаемое значение представляет собой код ошибки. Коды ошибок определены в ERRNO.H; ошибки, создаваемые этой функцией, см. в таблице ниже. Дополнительные сведения о кодах ошибок см. в разделе [Константы errno](../../c-runtime-library/errno-constants.md).  
  
### <a name="error-conditions"></a>Условия ошибок  
  
|`buffer`|`numberOfElements`|Назад|Содержимое `buffer`|  
|--------------|------------------------|------------|--------------------------|  
|`NULL`|(любые)|`EINVAL`|Без изменений|  
|Не `NULL` (указывает на допустимый буфер)|0|`EINVAL`|Без изменений|  
|Не `NULL` (указывает на допустимый буфер)|0 < size < 9|`EINVAL`|Пустая строка|  
|Не `NULL` (указывает на допустимый буфер)|Size > 9|0|Текущая дата в формате, указанном в разделе "Примечания"|  
  
## <a name="security-issues"></a>Проблемы безопасности  
 При передаче в качестве буфера недействительного значения, отличного от NULL, возникнет нарушение прав доступа, если значение параметра `numberOfElements` больше 9.  
  
 Передача в качестве `numberOfElements` значения, превышающего фактический размер буфера, приведет к переполнению буфера.  
  
## <a name="remarks"></a>Примечания  
 Эти функции представляют собой более безопасные версии `_strtime` и `_wstrtime`. `_strtime_s` Функция копирует текущее местное время в буфере, на который указывает `timestr`. Время представлено в формате `hh:mm:ss`, где `hh` — две цифры, представляющие час в 24-часовом формате, `mm` — две цифры, представляющие минуты после начала часа, `ss` — две цифры, представляющие секунды. Например, строка `18:23:44` представляет 23 минуты и 44 секунды после 18 часов. Размер буфера должен составлять не менее 9 байт; фактический размер указывается в качестве второго параметра.  
  
 `_wstrtime` — это версия с расширенными символами для `_strtime`; аргумент и возвращаемое значение `_wstrtime` являются строками с расширенными символами. В остальном эти функции ведут себя одинаково.  
  
 В C++ использование данных функций упрощено наличием шаблонных перегрузок; перегруженные методы могут автоматически определять длину буфера (что исключает необходимость указания аргумента с размером буфера), а также они могут автоматически заменять более старые, незащищенные функции их новыми безопасными аналогами. Дополнительные сведения см. в разделе [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mapping"></a>Сопоставление универсальных текстовых функций:  
  
|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstrtime_s`|`_strtime_s`|`_strtime_s`|`_wstrtime_s`|  
  
## <a name="requirements"></a>Требования  
  
|Подпрограмма|Обязательный заголовок|  
|-------------|---------------------|  
|`_strtime_s`|\<time.h>|  
|`_wstrtime_s`|\<time.h> или \<wchar.h>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md) во введении.  
  
## <a name="example"></a>Пример  
  
```  
// strtime_s.c  
  
#include <time.h>  
#include <stdio.h>  
  
int main()  
{  
    char tmpbuf[9];  
    errno_t err;  
  
    // Set time zone from TZ environment variable. If TZ is not set,  
    // the operating system is queried to obtain the default value   
    // for the variable.   
    //  
    _tzset();  
  
    // Display operating system-style date and time.   
    err = _strtime_s( tmpbuf, 9 );  
    if (err)  
    {  
       printf("_strdate_s failed due to an invalid argument.");  
      exit(1);  
    }  
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );  
    err = _strdate_s( tmpbuf, 9 );  
    if (err)  
    {  
       printf("_strdate_s failed due to an invalid argument.");  
       exit(1);  
    }  
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );  
  
}  
```  
  
```Output  
OS time:            14:37:49  
OS date:            04/25/03  
```  
  
## <a name="see-also"></a>См. также  
 [Управление временем](../../c-runtime-library/time-management.md)   
 [asctime_s, _wasctime_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [ctime_s, _ctime32_s, _ctime64_s, _wctime_s, _wctime32_s, _wctime64_s](../../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)   
 [gmtime_s, _gmtime32_s, _gmtime64_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime_s, _localtime32_s, _localtime64_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [mktime, _mktime32, _mktime64](../../c-runtime-library/reference/mktime-mktime32-mktime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [_tzset](../../c-runtime-library/reference/tzset.md)