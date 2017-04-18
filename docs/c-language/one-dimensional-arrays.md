---
title: "Одномерные массивы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "массивы [C++], одно измерение"
  - "квадратные скобки [ ]"
  - "квадратные скобки [ ], массивы"
  - "одномерные массивы"
  - "квадратные скобки [ ]"
  - "квадратные скобки [ ], массивы"
  - "подстрочные выражения"
ms.assetid: e28536e5-3b77-46b5-97fd-9b938c771816
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Одномерные массивы
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Постфиксное выражения, за которым следует выражение в квадратных скобках \(**\[ \]**\), является представлением элемента объекта массива с индексом.  Выражение индекса представляет значение по адресу, который находится на *выражение* позиций после *постфиксного\-выражения* при записи в следующем виде  
  
```  
  
postfix-expression [ expression ]  
```  
  
 Обычно *постфиксное\-выражение* представляет значение указателя, например идентификатор массива, а *выражение* является целочисленным значением.  Однако все, что необходимо синтаксически, — это чтобы одно из выражений имело тип указателя, а другие — целочисленный тип.  Таким образом, целочисленное значение может находиться в позиции *постфиксного\-выражения*, а значение указателя может находиться в квадратных скобках в позиции *выражения* \(позиции "индекса"\).  Например, такой код является допустимым:  
  
```  
// one_dimensional_arrays.c  
int sum, *ptr, a[10];  
int main() {  
   ptr = a;  
   sum = 4[ptr];  
}  
```  
  
 Выражения индекса обычно используются для ссылки на элементы массива, но индекс может применяться к любому указателю.  Независимо от порядка значений, *выражение* должно быть заключено в квадратные скобки \(**\[ \]**\).  
  
 Выражение индекса вычисляется путем добавления целочисленного значения к значению указателя с последующим применением к результату оператора косвенного обращения \(**\***\). \(Обсуждение оператора косвенного обращения см. в разделе [Операторы косвенного обращения и определения адреса](../c-language/indirection-and-address-of-operators.md).\) В конечном итоге в случае одномерного массива следующие 4 выражения эквивалентны, при условии что `a` является указателем, а `b` — целым числом:  
  
```  
a[b]  
*(a + b)  
*(b + a)  
b[a]  
```  
  
 В соответствии с правилами преобразования для оператора сложения \(приведенными в разделе [Аддитивные операторы](../c-language/c-additive-operators.md)\) целочисленное значение преобразуется в смещение адреса умножением целочисленного значения на длину типа, на который указывает указатель.  
  
 Например, предположим, что идентификатор `line` ссылается на массив значений `int`.  Для вычисления выражения индекса `line[ i ]` используется следующая процедура:  
  
1.  Целочисленное значение `i` умножается на количество байт, определенное как длина элемента `int`.  Преобразованное значение `i` представляет позиции `i` `int`.  
  
2.  Это преобразованное значение добавляется к исходному значению указателя \(`line`\) для получения адреса, представляющего смещенные позиции `i` `int` относительно `line`.  
  
3.  Оператор косвенного обращения применяется к новому адресу.  Результат представляет собой значение элемента массива в этой позиции \(интуитивно, `line [ i ]`\).  
  
 Выражение индекса `line[0]` представляет значение первого элемента массива line, поскольку смещение от адреса, представляемого `line`, равно 0.  Аналогично, выражение `line[5]` ссылается на элемент, смещенный на 5 позиций относительно line, или на шестой элемент массива.  
  
## См. также  
 [Подстрочный оператор:](../Topic/Subscript%20Operator:.md)