---
title: "__svm_stgi | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __svm_stgi
dev_langs: C++
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94e386827ae747fb3289354ba380d390756359ff
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/03/2018
---
# <a name="svmstgi"></a>__svm_stgi
**Блок, относящийся только к системам Microsoft**  
  
 Устанавливает флаг глобальной прерываний.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
void __svm_stgi(void);  
```  
  
## <a name="remarks"></a>Примечания  
 `__svm_stgi` Функция эквивалентна `STGI` инструкции компьютера. Прерывание глобальный флаг определяет микропроцессора игнорирует, откладывает или обработка прерываний из-за события, такие как завершение ввода-вывода, температуры это аппаратное оповещение или исключение отладки.  
  
 Эта функция поддерживает взаимодействие монитора виртуальной машины узла с гостевой операционной системой и ее приложениями. Дополнительные сведения, выполните поиск документа, «AMD64 архитектура программист вручную тома 2: программирование системы» номер 24593, 3.11, редакции документа в [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746) сайта.  
  
## <a name="requirements"></a>Требования  
  
|Встроенная функция|Архитектура|  
|---------------|------------------|  
|`__svm_stgi`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Файл заголовка** \<intrin.h >  
  
**Завершение блока, относящегося только к системам Майкрософт**  
  
## <a name="see-also"></a>См. также  
 [Встроенные объекты компилятора](../intrinsics/compiler-intrinsics.md)   
 [__svm_clgi](../intrinsics/svm-clgi.md)