---
title: "mktime, _mktime32, _mktime64 | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _mktime32
- mktime
- _mktime64
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
- mktime
- _mktime64
dev_langs:
- C++
helpviewer_keywords:
- _mktime32 function
- mktime function
- time functions
- mktime64 function
- converting times
- mktime32 function
- _mktime64 function
- time, converting
ms.assetid: 284ed5d4-7064-48a2-bd50-15effdae32cf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee2673f98f219559fd42d192dd934c8fe3eaed8c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="mktime-mktime32-mktime64"></a>mktime, _mktime32, _mktime64
Преобразуют локальное время в календарное значение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
time_t mktime(  
   struct tm *timeptr   
);  
__time32_t _mktime32(  
   struct tm *timeptr   
);  
__time64_t _mktime64(  
   struct tm *timeptr   
);  
```  
  
#### <a name="parameters"></a>Параметры  
 *timeptr*  
 Указатель на структуру времени; см. [asctime](../../c-runtime-library/reference/asctime-wasctime.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Функция `_mktime32` возвращает указанное календарное время, закодированное как значение типа [time_t](../../c-runtime-library/standard-types.md). Если *timeptr* ссылается на время до полуночи 1 января 1970 года, или если невозможно представить Календарное время, `_mktime32` возвращает -1, приведенное к типу `time_t`. При использовании `_mktime32` и, если *timeptr* ссылается на время после 23:59:59 18 января 2038 года, универсальное глобальное (UTC), возвращается значение -1, приведенное к типу `time_t`.  
  
 `_mktime64` Возвращает -1, приведенное к типу `__time64_t` Если *timeptr* ссылается на дату после 23:59:59, 31 декабря 3000 года, время UTC.  
  
## <a name="remarks"></a>Примечания  
 Функции `mktime`, `_mktime32` и `_mktime64` преобразуют предоставленную структуру (возможно, неполную), на которую указывает *timeptr*, в полностью определенную структуру с нормализованными значениями, а затем преобразуют ее в значение календарного времени `time_t`. Преобразованное время имеет ту же кодировку, что и значения, возвращаемые функцией [time](../../c-runtime-library/reference/time-time32-time64.md). Исходные значения компонентов `tm_wday` и `tm_yday` структуры *timeptr* пропускаются, а исходные значения других компонентов не ограничиваются их нормальными диапазонами.  
  
 `mktime` — это встроенная функция, эквивалентная `_mktime64`, если не определен флаг `_USE_32BIT_TIME_T` (в этом случае она эквивалентна `_mktime32`).  
  
 После корректировки в соответствии с форматом UTC `_mktime32` обрабатывает даты с полуночи 1 января 1970 г. до 23:59:59 18 января 2038 г. `_mktime64` обрабатывает даты с полуночи 1 января 1970 г. до 23:59:59 31 декабря 3000 г. Этот аргумент может вызывать возвращение данными функциями значения -1 (приведенного к `time_t`, `__time32_t` или `__time64_t`), даже если указанная дата находится в пределах диапазона. Например, если вы находитесь в Каире (Египет), часовой пояс которого на два часа раньше UTC, два часа сначала будут вычтены из даты, указанной в *timeptr*; это может привести к тому, что дата выйдет за пределы диапазона.  
  
 Эти функции можно использовать для проверки и заполнения структуры времени (tm). В случае успешного выполнения функции задают значения для `tm_wday` и `tm_yday` и настраивают другие компоненты для отображения указанного календарного времени (однако значения принудительно задаются в их нормальных диапазонах). Последнее значение `tm_mday` не задается, пока не определены `tm_mon` и `tm_year`. При указании времени структуры `tm` задайте для поля `tm_isdst` значение:  
  
-   нуль (0), чтобы указать, что действует стандартное время;  
  
-   значение больше нуля, чтобы указать, что действует переход на зимнее время;  
  
-   значение меньше нуля, чтобы указать, что код библиотеки времени выполнения языка C должен вычислить, действует ли стандартное время или переход на зимнее время.  
  
 Библиотека времени выполнения языка C определит режим перехода на зимнее время на основе значения переменной среды [TZ](../../c-runtime-library/reference/tzset.md). Если `TZ` не задана, для получения от операционной системы сведений о летнем времени вызывается функция [GetTimeZoneInformation](http://msdn.microsoft.com/library/windows/desktop/ms724421.aspx) API Win32. В случае сбоя библиотека предполагает, что для реализации вычисления перехода на зимнее время используются правила для США. `tm_isdst` — это обязательное поле. Если оно не задано, его значение является неопределенным, а возвращаемые значения этих функций — непредсказуемыми. Если *timeptr* указывает на структуру `tm`, возвращенную предыдущим вызовом функции `asctime`, `gmtime` или `localtime` (или вариаций этих функций), поле `tm_isdst` содержит правильное значение.  
  
 Учтите, что `gmtime` и `localtime` (а также `_gmtime32`, `_gmtime64`, `_localtime32` и `_localtime64`) используют один буфер на поток для преобразования. Если вы предоставляете этот буфер `mktime`, `_mktime32` или `_mktime64`, предыдущее содержимое удаляется.  
  
 Эти функции проверяют свои параметры. Если параметр *timeptr* является пустым указателем, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если продолжение выполнения разрешено, функции возвращают значение -1 и задают для `errno` значение `EINVAL`.  
  
## <a name="requirements"></a>Требования  
  
|Подпрограмма|Обязательный заголовок|  
|-------------|---------------------|  
|`mktime`|\<time.h>|  
|`_mktime32`|\<time.h>|  
|`_mktime64`|\<time.h>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md) во введении.  
  
## <a name="libraries"></a>Библиотеки  
 Все версии [библиотек времени выполнения языка C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Пример  
  
```  
// crt_mktime.c  
/* The example takes a number of days  
 * as input and returns the time, the current  
 * date, and the specified number of days.  
 */  
  
#include <time.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct tm  when;  
   __time64_t now, result;  
   int        days;  
   char       buff[80];  
  
   time( &now );  
   _localtime64_s( &when, &now );  
   asctime_s( buff, sizeof(buff), &when );  
   printf( "Current time is %s\n", buff );  
   days = 20;  
   when.tm_mday = when.tm_mday + days;  
   if( (result = mktime( &when )) != (time_t)-1 ) {  
      asctime_s( buff, sizeof(buff), &when );  
      printf( "In %d days the time will be %s\n", days, buff );  
   } else  
      perror( "mktime failed" );  
}  
```  
  
## <a name="sample-output"></a>Пример результатов выполнения  
  
```  
Current time is Fri Apr 25 13:34:07 2003  
  
In 20 days the time will be Thu May 15 13:34:07 2003  
```  
  
## <a name="see-also"></a>См. также  
 [Управление временем](../../c-runtime-library/time-management.md)   
 [asctime, _wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [gmtime, _gmtime32, _gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime, _localtime32, _localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [_mkgmtime, _mkgmtime32, _mkgmtime64](../../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)   
 [time, _time32, _time64](../../c-runtime-library/reference/time-time32-time64.md)