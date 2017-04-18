---
title: "Двоичные выходные файлы | Документы Майкрософт"
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
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
caps.latest.revision: 8
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: f566da8ea00f0a52db3539c81bb3d19d6fc9da99
ms.lasthandoff: 02/24/2017

---
# <a name="binary-output-files"></a>Двоичные выходные файлы
Потоки изначально были разработаны для текста, поэтому по умолчанию установлен режим вывода текста. В текстовом режиме символ перевода строки (шестнадцатеричное 10) расширяется до символа возврата каретки и перевода строки (только 16-битовый). Расширение может вызвать проблемы, как показано ниже:  
  
```  
// binary_output_files.cpp  
// compile with: /EHsc  
#include <fstream>  
using namespace std;  
int iarray[2] = { 99, 10 };  
int main( )  
{  
    ofstream os( "test.dat" );  
    os.write( (char *) iarray, sizeof( iarray ) );  
}  
```  
  
 Можно предположить, что эта программа будет выводить байтовую последовательность {99, 0, 10, 0}; вместо этого она выводит {99, 0, 13, 10, 0}, что приводит к проблемам в программе, ожидающей ввод двоичных данных. Если требуются настоящие двоичные входные денные, в которых символы записаны непреобразованными, можно указать вывод двоичных данных с помощью аргумента openmode конструктора [ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream__basic_ofstream):  
  
```  
// binary_output_files2.cpp  
// compile with: /EHsc  
#include <fstream>  
using namespace std;  
int iarray[2] = { 99, 10 };  
  
int main()  
{  
   ofstream ofs ( "test.dat", ios_base::binary );  
  
   // Exactly 8 bytes written  
   ofs.write( (char*)&iarray[0], sizeof(int)*2 );   
}  
```  
  
## <a name="see-also"></a>См. также  
 [Потоки вывода](../standard-library/output-streams.md)

