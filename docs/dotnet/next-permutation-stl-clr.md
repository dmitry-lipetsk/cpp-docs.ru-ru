---
title: "next_permutation (STL/CLR) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::next_permutation
dev_langs: C++
helpviewer_keywords: next_permutation function [STL/CLR]
ms.assetid: e36e821f-4b8d-461b-8074-69cd0175ccec
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 446ff06af9c3bb771c2698b40eafc353ed93a2f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="nextpermutation-stlclr"></a>next_permutation (STL/CLR)
Изменяет порядок элементов в диапазоне, чтобы исходный порядок был заменен перестановкой "лексикографически следующий больший", если такая существует, где смысл термина "следующий" может быть задан бинарным предикатом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template<class _BidIt> inline  
    bool next_permutation(_BidIt _First, _BidIt _Last);  
template<class _BidIt, class _Pr> inline  
    bool next_permutation(_BidIt _First, _BidIt _Last, _Pr _Pred);  
```  
  
## <a name="remarks"></a>Примечания  
 Эта функция работает так же, как функция стандартной библиотеки C++ `next_permutation`. Дополнительные сведения см. в разделе [next_permutation](../standard-library/algorithm-functions.md#next_permutation).  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<cliext/алгоритм >  
  
 **Пространство имен:** cliext  
  
## <a name="see-also"></a>См. также  
 [algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)