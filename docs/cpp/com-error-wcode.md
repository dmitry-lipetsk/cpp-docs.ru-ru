---
title: "_com_error::WCode | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_error::WCode
dev_langs: C++
helpviewer_keywords: WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 74f79491b9d4f88e19bcd0f7a20c94b26d0f7909
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="comerrorwcode"></a>_com_error::WCode
**Блок, относящийся только к системам Microsoft**  
  
 Извлекает 16-битный код ошибки, сопоставленный инкапсулированному значению `HRESULT`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
WORD WCode ( ) const throw( );  
  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если `HRESULT` находится в пределах диапазона от 0x80040200 до 0x8004FFFF **WCode** возвращает `HRESULT` минус 0x80040200; в противном случае возвращается ноль.  
  
## <a name="remarks"></a>Примечания  
 **WCode** метод используется для отмены сопоставления, выполняемого в коде поддержки COM. Программа-оболочка для **disp-интерфейса** свойство или метод вызывает вспомогательную процедуру, которая упаковывает аргументы и вызывает **IDispatch::Invoke**. Если сбой при возврате `HRESULT` из `DISP_E_EXCEPTION` возвращается, сведения об ошибках извлекаются из **EXCEPINFO** структуры передается **IDispatch::Invoke**. Код ошибки может быть 16-разрядное значение, хранящееся в `wCode` членом **EXCEPINFO** или полным 32-разрядным значением в **scode** членом **EXCEPINFO**структуры. Если возвращен 16-разрядный код `wCode`, его необходимо сначала сопоставить 32-разрядному коду сбоя `HRESULT`.  
  
 **Завершение блока, относящегося только к системам Майкрософт**  
  
## <a name="see-also"></a>См. также  
 [_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)   
 [_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)   
 [Класс _com_error](../cpp/com-error-class.md)