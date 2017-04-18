---
title: "Практическое руководство. Маршалирование строк Юникода для ADO.NET (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ADO.NET [C++], маршалинг строк Unicode"
  - "строки [C++], Юникод"
  - "Юникод [C++], строки"
ms.assetid: 1da090ff-6b53-40be-841f-dc79dfe8ba10
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Практическое руководство. Маршалирование строк Юникода для ADO.NET (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Способы добавления собственных строк Юникода \(`wchar_t *`\) в базу данных, а также маршалирование объекта <xref:System.String?displayProperty=fullName> из базы данных в собственную строку Юникода.  
  
## Пример  
 В данном примере класс DatabaseClass создается для взаимодействия с объектом <xref:System.Data.DataTable> ADO.NET.  Обратите внимание, что этот класс должен представлять собой исходный класс C\+\+ `class` \(по сравнению с `ref class` или `value class`\).  Это необходимо, поскольку данный класс будет использоваться в машинном коде, в котором применение управляемых типов недопустимо.  Данный класс будет компилироваться для среды CLR в соответствии с директивой `#pragma managed`, предшествующей объявлению класса.  Дополнительные сведения об этой директиве см. в разделе [managed, unmanaged](../preprocessor/managed-unmanaged.md).  
  
 Обратите внимание на закрытый член класса DatabaseClass: `gcroot<DataTable ^> table`.  Поскольку собственные типы не могут содержать управляемые типы, необходимо использовать ключевое слово `gcroot`.  Дополнительные сведения о `gcroot` см. в разделе [Практическое руководство. Объявление дескрипторов в собственных типах](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Остальная часть кода в данном примере представляет собой машинный код C\+\+ в соответствии с директивой `#pragma unmanaged`, предшествующей `main`.  В данном примере создается новый экземпляр класса DatabaseClass, а также вызываются его методы для создания таблицы и добавления в нее нескольких строк.  Обратите внимание, что строки Юникода для C\+\+ передаются в качестве значений в столбец StringCol базы данных.  Внутри класса DatabaseClass эти строки маршалируются в управляемые строки с помощью механизма маршалинга пространства имен <xref:System.Runtime.InteropServices?displayProperty=fullName>.  В частности, метод <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> используется для маршалирования `wchar_t *` в <xref:System.String>, а метод <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> — для маршалирования <xref:System.String> в `wchar_t *`.  
  
> [!NOTE]
>  Память, выделенная методу <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A>, должна быть отменено с помощью вызова метода <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> или `GlobalFree`.  
  
```  
// adonet_marshal_string_wide.cpp  
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll  
#include <comdef.h>  
#include <gcroot.h>  
#include <iostream>  
using namespace std;  
  
#using <System.Data.dll>  
using namespace System;  
using namespace System::Data;  
using namespace System::Runtime::InteropServices;  
  
#define MAXCOLS 100  
  
#pragma managed  
class DatabaseClass  
{  
public:  
    DatabaseClass() : table(nullptr) { }  
  
    void AddRow(wchar_t *stringColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["StringCol"] = Marshal::PtrToStringUni(  
            (IntPtr)stringColValue);  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("StringCol",  
            Type::GetType("System.String"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, wchar_t **values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringUni(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed string  
            // to a wchar_t *.  
            values[i] = (wchar_t *)Marshal::StringToHGlobalUni(  
                (String ^)rows[i][columnStr]).ToPointer();  
        }  
  
        return len;  
    }  
  
private:  
    // Using gcroot, you can use a managed type in  
    // a native class.  
    gcroot<DataTable ^> table;  
};  
  
#pragma unmanaged  
int main()  
{  
    // Create a table and add a few rows to it.  
    DatabaseClass *db = new DatabaseClass();  
    db->CreateAndPopulateTable();  
    db->AddRow(L"This is string 1.");  
    db->AddRow(L"This is string 2.");  
  
    // Now retrieve the rows and display their contents.  
    wchar_t *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"StringCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        wcout << "StringCol: " << values[i] << endl;  
  
        // Deallocate the memory allocated using  
        // Marshal::StringToHGlobalUni.  
        GlobalFree(values[i]);  
    }  
  
    delete db;  
  
    return 0;  
}  
```  
  
  **StringCol: это строка 1.**  
**StringCol: это строка 2.**   
## Компиляция кода  
  
-   Для компилирования кода из командной строки следует сохранить пример кода в файл adonet\_marshal\_string\_wide.cpp и ввести следующий оператор:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp  
    ```  
  
## Безопасность платформы .NET Framework  
 Дополнительные сведения о вопросах безопасности, связанные с ADO.NET, см. в разделе [Защита приложений ADO.NET](../Topic/Securing%20ADO.NET%20Applications.md).  
  
## См. также  
 <xref:System.Runtime.InteropServices>   
 [Доступ к данным](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](../Topic/ADO.NET.md)   
 [Interoperability](http://msdn.microsoft.com/ru-ru/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Взаимодействие исходного кода и платформы.NET](../Topic/Native%20and%20.NET%20Interoperability.md)