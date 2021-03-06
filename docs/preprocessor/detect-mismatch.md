---
title: "detect_mismatch | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 90f4013606ba94c6ea18aa4369bb2e3298034081
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="detectmismatch"></a>detect_mismatch
Помещает запись в объект. Компоновщик проверяет эти записи на предмет наличия потенциальных несоответствий.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
#pragma detect_mismatch( "name", "value"))  
```  
  
## <a name="remarks"></a>Примечания  
 При компоновке проекта компоновщик создает ошибку `LNK2038`, если проект содержит 2 объекта с одинаковыми именами `name`, но разными значениями `value`. Используйте эту директиву #pragma для предотвращения компоновки несогласованных объектных файлов.  
  
 Имя и значение являются строковыми литералами и подчиняются правилам для строковых литералов в отношении escape-символов и объединения. В них учитывается регистр, и они не могут содержать запятую, знак равенства, кавычки или символ `null`.  
  
## <a name="example"></a>Пример  
 В этом примере создаются два файла, имеющие разные номера версий для одной метки версии.  
  
```  
// pragma_directive_detect_mismatch_a.cpp  
#pragma detect_mismatch("myLib_version", "9")  
int main ()  
{  
   return 0;  
}  
  
// pragma_directive_detect_mismatch_b.cpp  
#pragma detect_mismatch("myLib_version", "1")  
```  
  
 При компиляции обоих этих файлов с помощью командной строки `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp` возникает ошибка `LNK2038`.  
  
## <a name="see-also"></a>См. также  
 [Директивы Pragma и ключевое слово __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)