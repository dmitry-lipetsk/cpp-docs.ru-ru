---
title: "Класс out_of_range | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: stdexcept/std::out_of_range
dev_langs: C++
helpviewer_keywords: out_of_range class
ms.assetid: d0e14dc0-065e-4666-9ac9-51e52223c503
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2c92933e62f79b22b988099f0d7cbad1f3679888
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="outofrange-class"></a>Класс out_of_range
Этот класс служит базовым для всех исключений, создаваемых для сообщения о том, что аргумент выходит за допустимый диапазон.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
class out_of_range : public logic_error {  
public:  
    explicit out_of_range(const string& message);

    explicit out_of_range(const char *message);

};  
```  
  
## <a name="remarks"></a>Примечания  
 Значение, возвращаемое [what](../standard-library/exception-class.md), — это копия **данных**`.`[сообщения](../standard-library/basic-string-class.md#data).  
  
## <a name="example"></a>Пример  
  
```cpp  
// out_of_range.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
using namespace std;  
  
int main() {  
// out_of_range  
   try {  
      string str( "Micro" );  
      string rstr( "soft" );  
      str.append( rstr, 5, 3 );  
      cout << str << endl;  
   }  
   catch ( exception &e ) {  
      cerr << "Caught: " << e.what( ) << endl;  
   };  
}  
```  
  
## <a name="output"></a>Вывод  
  
```  
Caught: invalid string position  
```  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** \<stdexcept>  
  
 **Пространство имен:** std  
  
## <a name="see-also"></a>См. также  
 [Класс logic_error](../standard-library/logic-error-class.md)   
 [Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

