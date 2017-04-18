---
title: "casin, casinf, casinl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "casin"
  - "casinf"
  - "casinl"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "casin"
  - "casinf"
  - "casinl"
  - "complex/casin"
  - "complex/casinf"
  - "complex/casinl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "функция casin"
  - "функция casinf"
  - "функция casinl"
ms.assetid: b75d1455-7b1e-43b0-bd46-c530be190be9
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# casin, casinf, casinl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Возвращает арксинус комплексное число, с сокращает ветви попадает в интервал \[−1, \+ 1\] реальные оси.  
  
## Синтаксис  
  
```  
_Dcomplex casin(   
   _Dcomplex z   
);  
_Fcomplex casin(   
   _Fcomplex z   
);  // C++ only  
_Lcomplex casin(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex casinf(   
   _Fcomplex z   
);  
_Lcomplex casinl(   
   _Lcomplex z   
);  
```  
  
#### Параметры  
 `z`  
 Комплексное число, представляющее угол в радианах.  
  
## Возвращаемое значение  
 Арксинус `z`, в радианах. Результат неограничен мнимой оси и в интервале \[−π\/2 \+ π\/2\] реальные оси.  
  
## Заметки  
 Поскольку C\+\+ допускает перегрузку, можно вызывать перегрузки `casin`, которые принимают и возвращают значения `_Fcomplex` и `_Lcomplex`. В программе на языке C `casin` всегда принимает и возвращает `_Dcomplex` значение.  
  
## Требования  
  
|Подпрограмма|Заголовок C|Заголовок C\+\+|  
|------------------|-----------------|---------------------|  
|`casin`, `casinf`, `casinl`|\<complex.h\>|\< ccomplex \>|  
  
 Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md) во введении.  
  
## См. также  
 [Алфавитный указатель функций](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [catanh, catanhf, catanhl](../../c-runtime-library/reference/catanh-catanhf-catanhl.md)   
 [ctanh, ctanhf, ctanhl](../../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)   
 [catan, catanf, catanl](../../c-runtime-library/reference/catan-catanf-catanl.md)   
 [csinh, csinhf, csinhl](../Topic/csinh,%20csinhf,%20csinhl.md)   
 [casinh, casinhf, casinhl](../Topic/casinh,%20casinhf,%20casinhl.md)   
 [ccosh, ccoshf, ccoshl](../Topic/ccosh,%20ccoshf,%20ccoshl.md)   
 [cacosh, cacoshf, cacoshl](../../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)   
 [cacos, cacosf, cacosl](../../c-runtime-library/reference/cacos-cacosf-cacosl.md)   
 [ctan, ctanf, ctanl](../../c-runtime-library/reference/ctan-ctanf-ctanl.md)   
 [csin, csinf, csinl](../../c-runtime-library/reference/csin-csinf-csinl.md)   
 [ccos, ccosf, ccosl](../../c-runtime-library/reference/ccos-ccosf-ccosl.md)   
 [csqrt, csqrtf, csqrtl](../../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)