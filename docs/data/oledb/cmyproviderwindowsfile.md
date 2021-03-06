---
title: "CMyProviderWindowsFile | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cmyproviderwindowsfile
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e0ac247c418efa7800eeef469ecf54da75f5b15c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2018
---
# <a name="cmyproviderwindowsfile"></a>Класс CMyProviderWindowsFile
Мастер создает класс, содержащий одну строку данных. в этом случае вызывается `CMyProviderWindowsFile`. В следующем коде для `CMyProviderWindowsFile` — созданный мастером и выводит все файлы в каталоге с помощью **WIN32_FIND_DATA** структуры. `CMyProviderWindowsFile` наследует от **WIN32_FIND_DATA** структуры:  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
class CMyProviderWindowsFile:   
   public WIN32_FIND_DATA  
{  
public:  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)  
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)  
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)  
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)  
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)  
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)  
END_PROVIDER_COLUMN_MAP()  
};  
```  
  
 `CMyProviderWindowsFile` вызывается [класс записей пользователя](../../data/oledb/user-record.md) , так как он также содержит сопоставление, описывающее столбцы в наборе строк поставщика. Сопоставление столбцов поставщика содержит одну запись для каждого поля в наборе строк с помощью макросов PROVIDER_COLUMN_ENTRY. Макросы укажите имя столбца, порядковый номер и смещения относительно записи структуры. В записях столбцов поставщика в приведенном выше коде содержится значение смещения в **WIN32_FIND_DATA** структуры. Когда потребитель вызывает метод **IRowset::GetData**, данные передаются в один непрерывный буфер. Вместо выполнения арифметических операций с указателями карты можно указать данные-член.  
  
 `CMyProviderRowset` Класс также содержит `Execute` метод. `Execute` предназначен для считывания данных из источника. В следующем коде показано, созданный с помощью мастера `Execute` метод. Эта функция использует Win32 **FindFirstFile** и `FindNextFile` API-интерфейсы для извлечения сведений о файлах в каталоге и поместите их в экземпляры `CMyProviderWindowsFile` класса.  
  
```cpp
/////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)  
{  
   USES_CONVERSION;  
   BOOL bFound = FALSE;  
   HANDLE hFile;  
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :  
       OLE2T(m_strCommandText);  
   CMyProviderWindowsFile wf;  
   hFile = FindFirstFile(szDir, &wf);  
   if (hFile == INVALID_HANDLE_VALUE)  
      return DB_E_ERRORSINCOMMAND;  
   LONG cFiles = 1;  
   BOOL bMoreFiles = TRUE;  
   while (bMoreFiles)  
   {  
      if (!m_rgRowData.Add(wf))  
         return E_OUTOFMEMORY;  
      bMoreFiles = FindNextFile(hFile, &wf);  
      cFiles++;  
   }  
   FindClose(hFile);  
   if (pcRowsAffected != NULL)  
      *pcRowsAffected = cFiles;  
   return S_OK;  
}  
```  
  
 Представленный к каталогу для поиска `m_strCommandText`; содержит текст, определяемый `ICommandText` интерфейса в объекте command. Если каталог не указан, используется текущий каталог.  
  
 Метод создает одну запись для каждого файла (соответствует строке) и помещает его в **m_rgRowData** члена данных. `CRowsetImpl` Класс определяет **m_rgRowData** члена данных. Данные в этом массиве представляют всю таблицу и используется во всех шаблонах.  
  
## <a name="see-also"></a>См. также  
 [Созданные мастером поставщика файлы](../../data/oledb/provider-wizard-generated-files.md)