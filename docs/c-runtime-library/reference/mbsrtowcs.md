---
title: "mbsrtowcs | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- mbsrtowcs
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- mbsrtowcs
dev_langs:
- C++
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ff120fea2ec3f1ea659233ccee3f66514d0fd76b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="mbsrtowcs"></a>mbsrtowcs
Преобразует строку многобайтовых символов в текущем языковом стандарте в соответствующую строку расширенных символов с возможностью перезапуска в середине многобайтового символа. Существует более безопасная версия этой функции; см. раздел [mbsrtowcs_s](../../c-runtime-library/reference/mbsrtowcs-s.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
size_t mbsrtowcs(  
   wchar_t *wcstr,  
   const char **mbstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t mbsrtowcs(  
   wchar_t (&wcstr)[size],  
   const char **mbstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>Параметры  
 [выходной] `wcstr`  
 Адрес для сохранения результирующей преобразованной строки расширенных символов.  
  
 [in, out] `mbstr`  
 Косвенный указатель на расположение преобразуемой строки многобайтовых символов.  
  
 [in] `count`  
 Максимальное число символов (не байтов) для преобразования и сохранения в `wcstr`.  
  
 [in, out] `mbstate`  
 Указатель на объект состояния преобразования `mbstate_t`. Если это значение является пустым указателем, используется статичный внутренний объект состояния преобразования. Так как внутренний объект `mbstate_t` не является потокобезопасным, мы рекомендуем всегда передавать собственный параметр `mbstate`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает число успешно преобразованных символов без учета завершающего нуль-символа, если он есть. В случае ошибки возвращает (size_t)(-1) и устанавливает для `errno` значение EILSEQ.  
  
## <a name="remarks"></a>Примечания  
 Функция `mbsrtowcs` преобразует строку многобайтовых символов, на которую косвенно указывает параметр `mbstr`, в расширенные символы, сохраняемые в буфере, на который указывает параметр `wcstr`. При этом используется состояние преобразования, содержащееся в `mbstate`. Преобразование продолжается для каждого символа до тех пор, пока не встретится завершающий многобайтовый нуль-символ, многобайтовая последовательность, не соответствующая допустимому символу в текущем языковом стандарте, или пока не будет преобразовано `count` симв. Если функция `mbsrtowcs` встречает многобайтовый нуль-символ ("\0") до или после `count` симв., она преобразовывает его в 16-разрядный завершающий нуль-символ и останавливается.  
  
 Таким образом, строка расширенных символов `wcstr` завершается нуль-символом только в том случае, если функция `mbsrtowcs` встречает многобайтовый нуль-символ во время преобразования. Если последовательности, на которые указывают параметры `mbstr` и `wcstr`, перекрываются, то поведение `mbsrtowcs` не определено. На функцию `mbsrtowcs` влияет категория LC_TYPE текущего языкового стандарта.  
  
 Функция `mbsrtowcs` отличается от функций [mbstowcs, _mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md) возможностью перезапуска. Состояние преобразования хранится в переменной `mbstate` для последующих вызовов тех же или других перезапускаемых функций. При смешанном использовании перезапускаемых и неперезапускаемых функций результаты становятся неопределенными.  Например, в приложении необходимо использовать функцию `mbsrlen` вместо функции `mbslen`, если в последующем вызове используется функция `mbsrtowcs`, а не функция `mbstowcs.`.  
  
 Если `wcstr` не является пустым указателем, то объекту указателя, на который указывает параметр `mbstr`, присваивается пустой указатель, если преобразование останавливается из-за достижения завершающего нуль-символа. В противном случае ему назначается адрес позиции, следующей за последним преобразованным многобайтовым символом, если таковая имеется. Это позволяет продолжить преобразование с того же места при последующем вызове функции.  
  
 Если аргумент `wcstr` является пустым указателем, аргумент `count` игнорируется и `mbsrtowcs` возвращает необходимый размер конечной строки в расширенных символах. Если `mbstate` является пустым указателем, функция использует статичный внутренний объект состояния преобразования `mbstate_t`, не являющийся потокобезопасным. Если у последовательности символов `mbstr` нет соответствующего представления в виде многобайтовых символов, возвращается значение -1 и для `errno` устанавливается значение `EILSEQ`.  
  
 Если параметр `mbstr` является пустым указателем, вызывается обработчик недопустимого параметра, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если продолжение выполнения разрешено, эта функции задает для `errno` значение `EINVAL` и возвращает -1.  
  
 В C++ эта функция имеет шаблонную перегрузку, которая вызывает более новые и безопасные аналоги этой функции. Дополнительные сведения см. в разделе [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="exceptions"></a>Исключения  
 Функция `mbsrtowcs` является потокобезопасной, если ни одна из функций в текущем потоке не вызывает `setlocale`, пока выполняется данная функция, и аргумент `mbstate` не является пустым указателем.  
  
## <a name="requirements"></a>Требования  
  
|Подпрограмма|Обязательный заголовок|  
|-------------|---------------------|  
|`mbsrtowcs`|\<wchar.h>|  
  
## <a name="see-also"></a>См. также  
 [Преобразование данных](../../c-runtime-library/data-conversion.md)   
 [Языковой стандарт](../../c-runtime-library/locale.md)   
 [Интерпретация последовательностей многобайтовых символов](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtowc](../../c-runtime-library/reference/mbrtowc.md)   
 [mbtowc, _mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [mbstowcs, _mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)