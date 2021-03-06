---
title: "Потокобезопасность в стандартной библиотеке C++ | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- thread safety
- C++ Standard Library, thread safety
- thread safety, C++ Standard Library
ms.assetid: 9351c8fb-4539-4728-b0e9-226e2ac4284b
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1fa4c69e79a918d7b8cf77e03f76c81e846d5a5b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="thread-safety-in-the-c-standard-library"></a>Потокобезопасность в стандартной библиотеке C++
Следующие правила потокобезопасности применяются ко всем классам в стандартной библиотеке C++, включая `shared_ptr`, как описано ниже.  Иногда предоставляются более строгие гарантии, например, для стандартных объектов iostream, как описано ниже, и типов, специально предназначенных для многопотоковой работы, таких как типы [\<atomic>](../standard-library/atomic.md).  
  
 Объект является потокобезопасным при чтении из нескольких потоков. Например, объект А можно безопасно считать из потока 1 и потока 2 одновременно.  
  
 Если объект записывается одним потоком, то все операции чтения и записи в этот объект в одном или других потоках должны быть защищены. Например, если поток 1 записывает данные в объект А, потоку 2 следует запретить чтение из объекта А и запись в него.  
  
 Можно безопасно читать и записывать данные в один экземпляр типа, даже если другой поток читает или записывает другой экземпляр того же типа. Например, при наличии объектов А и Б одного типа можно безопасно записывать объект А в потоке 1 и читать объект Б в потоке 2.  
  
## <a name="sharedptr"></a>shared_ptr  
 Несколько потоков могут одновременно читать и записывать разные объекты [shared_ptr](../standard-library/shared-ptr-class.md), даже если они являются копиями с одним владельцем.  
  
## <a name="iostream"></a>iostream  
 Стандартные объекты iostream `cin`, `cout`, `cerr`, `clog`, `wcin`, `wcout`, `wcerr` и `wclog` следуют тем же правилам, что и другие классы, с одним исключением: можно безопасно записывать объект из нескольких потоков. Например, поток 1 может записывать данные в [cout](../standard-library/iostream.md#cout) одновременно с потоком 2. Однако это может привести к смешиванию выходных данных двух потоков.  
  
> [!NOTE]
>  Чтение из буфера потока считается не операцией чтения, а операцией записи, так как состояние класса меняется.  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о стандартной библиотеке C++](../standard-library/cpp-standard-library-overview.md)



