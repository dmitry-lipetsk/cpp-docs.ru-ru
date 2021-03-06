---
title: "Как: запись данных в реестр Windows (C + +/ CLI) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- registry, writing to
- Visual C++, writing to Windows Registry
ms.assetid: 3d40b978-4baa-4779-bfe3-47e2917b757f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f3bd5cedbf3c981964c9d03eb8a30fc5e1652081
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-write-data-to-the-windows-registry-ccli"></a>Практическое руководство. Запись данных в реестр Windows (C++/CLI)
Следующий пример кода использует <xref:Microsoft.Win32.Registry.CurrentUser> ключ для создания записи экземпляра <xref:Microsoft.Win32.RegistryKey> соответствующий класс **программного обеспечения** ключа. <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> Метод затем используется для создания нового ключа и добавления в пары "ключ значение".  
  
## <a name="example"></a>Пример  
  
### <a name="code"></a>Код  
  
```  
// registry_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main()  
{  
   // The second OpenSubKey argument indicates that  
   // the subkey should be writable.   
   RegistryKey^ rk;  
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);  
   if (!rk)  
   {  
      Console::WriteLine("Failed to open CurrentUser/Software key");  
      return -1;  
   }  
  
   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");  
   if (!nk)  
   {  
      Console::WriteLine("Failed to create 'NewRegKey'");  
      return -1;  
   }  
  
   String^ newValue = "NewValue";  
   try  
   {  
      nk->SetValue("NewKey", newValue);  
      nk->SetValue("NewKey2", 44);  
   }  
   catch (Exception^)  
   {  
      Console::WriteLine("Failed to set new values in 'NewRegKey'");  
      return -1;  
   }  
  
   Console::WriteLine("New key created.");  
   Console::Write("Use REGEDIT.EXE to verify ");  
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");  
   return 0;  
}  
```  
  
## <a name="remarks"></a>Примечания  
 Платформа .NET Framework можно использовать для доступа к реестру с <xref:Microsoft.Win32.Registry> и [RegistryKey](https://msdn.microsoft.com/en-us/library/microsoft.win32.registrykey.aspx) классы, оба из которых определены в <xref:Microsoft.Win32> пространства имен. **Реестра** класс — это контейнер для статических экземпляров <xref:Microsoft.Win32.RegistryKey> класса. Каждый экземпляр представляет корневой узел реестра. Экземпляры <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, и <xref:Microsoft.Win32.Registry.Users>.  
  
## <a name="see-also"></a>См. также  
 [Как: чтение данных из реестра Windows (C + +/ CLI)](../dotnet/how-to-read-data-from-the-windows-registry-cpp-cli.md)   
 [Программирование .NET с использованием C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)