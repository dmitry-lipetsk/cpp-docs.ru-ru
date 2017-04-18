---
title: "Ограничения констант с плавающей запятой | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- FLOAT.H header file
- constants, floating-point
- limits, floating-point constants
- floating-point numbers, floating limits
ms.assetid: 2d975868-2af6-45d7-a8af-db79f2c6b67b
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 2663e4f10a27ca37e4d77ad5e1200cd1e0b861b2
ms.lasthandoff: 02/24/2017

---
# <a name="limits-on-floating-point-constants"></a>Ограничения на константы с плавающей запятой
**Блок, относящийся только к системам Майкрософт**  
  
 В следующей таблице представлены ограничения на значения констант с плавающей запятой. Эта информация содержится в файле заголовка FLOAT.H.  
  
### <a name="limits-on-floating-point-constants"></a>Ограничения на константы с плавающей запятой  
  
|Константа|Значение|Значение|  
|--------------|-------------|-----------|  
|**FLT_DIG**<br />**DBL_DIG**<br />**LDBL_DIG**|Количество цифр *q*, при котором число с плавающей запятой с *q* десятичными цифрами можно округлить в представление с плавающей запятой и обратно без потери точности.|6<br />15<br />15|  
|**FLT_EPSILON**<br />**DBL_EPSILON**<br />**LDBL_EPSILON**|Наименьшее положительное число *x*, при котором *x* + 1,0 не равно 1,0.|1,192092896e–07F<br />2,2204460492503131e–016<br />2,2204460492503131e–016|  
|**FLT_GUARD**||0|  
|**FLT_MANT_DIG**<br />**DBL_MANT_DIG**<br />**LDBL_MANT_DIG**|Количество цифр для основания, заданного константой **FLT_RADIX**, в значащей части числа с плавающей запятой. Основание содержит два знака; следовательно, эти значения определяют разряды.|24<br />53<br />53|  
|**FLT_MAX**<br />**DBL_MAX**<br />**LDBL_MAX**|Максимальное представимое число с плавающей запятой.|3,402823466e+38F<br />1,7976931348623158e+308<br />1,7976931348623158e+308|  
|**FLT_MAX_10_EXP**<br />**DBL_MAX_10_EXP**<br />**LDBL_MAX_10_EXP**|Максимальное целое число, при котором число 10, возведенное в степень этого числа, является представимым числом с плавающей запятой.|38<br />308<br />308|  
|**FLT_MAX_EXP**<br />**DBL_MAX_EXP**<br />**LDBL_MAX_EXP**|Максимальное целое число, при котором значение **FLT_RADIX**, возведенное в степень этого числа, является представимым числом с плавающей запятой.|128<br />1024<br />1024|  
|**FLT_MIN**<br />**DBL_MIN**<br />**LDBL_MIN**|Минимальное положительное значение.|1,175494351e–38F<br />2,2250738585072014e–308<br />2,2250738585072014e–308|  
|**FLT_MIN_10_EXP**<br />**DBL_MIN_10_EXP**<br />**LDBL_MIN_10_EXP**|Минимальное отрицательное целое число, при котором число 10, возведенное в степень этого числа, является представимым числом с плавающей запятой.|–37<br />–307<br />–307|  
|**FLT_MIN_EXP**<br />**DBL_MIN_EXP**<br />**LDBL_MIN_EXP**|Минимальное отрицательное целое число, при котором значение **FLT_RADIX**, возведенное в степень этого числа, является представимым числом с плавающей запятой.|–125<br />–1021<br />–1021|  
|**FLT_NORMALIZE**||0|  
|**FLT_RADIX**<br />**_DBL_RADIX**<br />**_LDBL_RADIX**|Основание экспоненциальной формы представления.|2<br />2<br />2|  
|**FLT_ROUNDS**<br />**_DBL_ROUNDS**<br />**_LDBL_ROUNDS**|Режим округления для сложения чисел с плавающей запятой.|1 (приблизительно)<br />1 (приблизительно)<br />1 (приблизительно)|  
  
 Обратите внимание, что в будущих реализациях информация из приведенной выше таблицы может отличаться.  
  
 **Завершение блока, относящегося только к системам Майкрософт**  
  
## <a name="see-also"></a>См. также  
 [Константы с плавающей запятой в C](../c-language/c-floating-point-constants.md)