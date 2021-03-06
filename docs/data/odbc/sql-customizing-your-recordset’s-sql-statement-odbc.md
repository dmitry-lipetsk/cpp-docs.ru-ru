---
title: "SQL. Настройка инструкции SQL набора записей (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "настройка инструкций SQL"
  - "наборы записей ODBC, инструкции SQL"
  - "переопределение, инструкции SQL"
  - "наборы записей, инструкции SQL"
  - "инструкции SQL, настройка"
  - "инструкции SQL, наборы записей"
  - "SQL, открытие наборов записей"
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SQL. Настройка инструкции SQL набора записей (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Содержание раздела:  
  
-   Процесс создания платформой инструкции SQL  
  
-   Процесс переопределения инструкции SQL  
  
> [!NOTE]
>  В этом разделе приведены сведения, относящиеся к классам ODBC библиотеки MFC.  Сведения, относящиеся к классам DAO библиотеки MFC, см. в разделе "Сравнение ядра СУБД Microsoft Jet SQL и ANSI SQL" в справке DAO.  
  
## Создание инструкции SQL  
 Выбор записей для набора записей главным образом основан на инструкции SQL **SELECT**.  При объявлении класса с помощью мастера он создает переопределение функции\-члена `GetDefaultSQL`, которое выглядит примерно следующим образом \(для класса набора записей с именем `CAuthors`\).  
  
```  
CString CAuthors::GetDefaultSQL()  
{  
    return "AUTHORS";  
}  
```  
  
 По умолчанию в результате переопределения возвращается название таблицы, указанное в мастере.  В этом примере в качестве названия таблицы используется "AUTHORS". При последующем вызове функции\-члена набора записей **Open** функция **Open** создает окончательную инструкцию **SELECT** для формы:  
  
```  
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]   
       [ORDER BY m_strSort]  
```  
  
 Здесь имя `table-name` получено в результате вызова `GetDefaultSQL`, а список `rfx-field-list` формируется путем вызова функций RFX в функции `DoFieldExchange`.  Инструкция **SELECT** будет иметь именно такой вид, если только она не будет заменена переопределением во время выполнения, хотя инструкцию по умолчанию также можно изменить с помощью параметров или фильтра.  
  
> [!NOTE]
>  При указании имени столбца, который содержит \(или может содержать\) пробелы, его необходимо заключать в квадратные скобки.  Например, имя "Имя автора" должно иметь вид "\[Имя автора\]".  
  
 Чтобы переопределить используемую по умолчанию инструкцию **SELECT**, при вызове функции **Open** следует передать строку с полноценной инструкцией **SELECT**.  Вместо создания собственной строки по умолчанию набор записей будет использовать указанную строку.  Если замещающая инструкция содержит предложение **WHERE**, то указывать фильтр в элементе **m\_strFilter** не следует, иначе будет получено две инструкции фильтрации.  Аналогично, если замещающая инструкция содержит предложение **ORDER BY**, то не следует задавать сортировку в `m_strSort`, иначе это приведет к созданию двух инструкций сортировки.  
  
> [!NOTE]
>  Если в фильтрах \(или других фрагментах инструкции SQL\) используются строковые литералы, то эти строки может потребоваться "закавычить" \(заключить в указанные разделители\) необходимыми СУБД литеральными знаками префикса и суффикса.  
  
 В зависимости от используемой СУБД также могут встречаться особые требования к синтаксису для инструкций — например, для внешнего соединения.  Для получения соответствующей информации от драйвера СУБД можно использовать функции ODBC.  Так, например, можно вызвать функцию **::SQLGetTypeInfo** для определенного типа данных, например **SQL\_VARCHAR**, чтобы запросить знаки **LITERAL\_PREFIX** и **LITERAL\_SUFFIX**.  При создании кода, не зависящего от базы данных, подробные сведения по синтаксису см. в приложении В к *Справочнику программиста* *пакета SDK ODBC* на компакт\-диске библиотеки MSDN.  
  
 Объект набора записей создает инструкцию SQL, используемую для выбора записей, если не была задана пользовательская инструкция SQL.  Способ передачи главным образом зависит от значения, передаваемого в параметре `lpszSQL` функции\-члена **Open**.  
  
 Созданная инструкция SQL **SELECT** выглядит следующим образом:  
  
```  
SELECT [ALL | DISTINCT] column-list FROM table-list  
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]  
```  
  
 Одним из способов добавления ключевого слова **DISTINCT** к инструкции SQL набора записей является внедрение этого ключевого слова в первый вызов функции RFX в `DoFieldExchange`.  Примеры.  
  
```  
...  
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);  
...  
```  
  
> [!NOTE]
>  Этот способ следует использовать только для наборов данных, открываемых в режиме "только для чтения".  
  
## Переопределение инструкции SQL  
 В следующей таблице перечислены возможности параметра `lpszSQL` функции **Open**.  Приведенные в таблице случаи поясняются ниже.  
  
 **Параметр lpszSQL и результирующая строка SQL**  
  
|Case|Элементы, передаваемые в lpszSQL|Результирующая инструкция SELECT|  
|----------|--------------------------------------|--------------------------------------|  
|1|**NULL**|**SELECT** *rfx\-field\-list* **FROM** *table\-name*<br /><br /> Для получения имени таблицы функция `CRecordset::Open` вызывает функцию `GetDefaultSQL`.  Результирующая строка будет соответствовать одному из случаев 2–5, в зависимости от того, что возвращает функция `GetDefaultSQL`.|  
|2|Имя таблицы|**SELECT** *rfx\-field\-list* **FROM** *table\-name*<br /><br /> Список полей извлекается из инструкций RFX в `DoFieldExchange`.  Если поля **m\_strFilter** и `m_strSort` не пусты, добавляются предложения **WHERE** и\/или **ORDER BY**.|  
|3 \*|Полная инструкция **SELECT** без предложений **WHERE** или **ORDER BY**|В соответствии с переданным значением.  Если поля **m\_strFilter** и `m_strSort` не пусты, добавляются предложения **WHERE** и\/или **ORDER BY**.|  
|4 \*|Полная инструкция **SELECT** с предложениями **WHERE** и\/или **ORDER BY**|В соответствии с переданным значением.  Поля **m\_strFilter** и `m_strSort` должны быть пустыми, или же будет создано две инструкции фильтрации или сортировки.|  
|5 \*|Вызов хранимой процедуры|В соответствии с переданным значением.|  
  
 \* Значение `m_nFields` должно быть меньше или равно количеству столбцов, указанных в инструкции **SELECT**.  Тип данных каждого столбца, указанного в инструкции **SELECT**, должен совпадать с типом данных соответствующего выходного столбца RFX.  
  
### Случай 1   lpszSQL \= NULL  
 Выборка набора записей зависит от того, что возвращает функция `GetDefaultSQL` при вызове из функции `CRecordset::Open`.  В случаях 2\-5 описываются возможные строки.  
  
### Случай 2   lpszSQL \= "имя таблицы"  
 Набор записей использует обмен полей записей \(RFX\) для создания списка столбцов по именам столбцов, полученных в результате вызова функций RFX в переопределенной функции\-члене `DoFieldExchange` класса набора записей.  Если для объявления класса набора записей использовался мастер, результат в этом случае будет совпадать с результатом в случае 1 \(при условии, что переданное имя таблицы соответствует имени, указанному в мастере\).  Если для создания класса мастер не использовался, наиболее простым способом создания инструкции SQL является случай 2.  
  
 В следующем примере показано создание инструкции SQL, которая выбирает записи из базы данных в приложении MFC.  При вызове платформой функции\-члена `GetDefaultSQL` функция возвращает имя таблицы — `SECTION`.  
  
```  
CString CEnrollSet::GetDefaultSQL()  
{  
    return "SECTION";  
}  
```  
  
 Чтобы получить имена столбцов для инструкции SQL **SELECT**, платформа вызывает функцию\-член `DoFieldExchange`.  
  
```  
void CEnrollSet::DoFieldExchange(CFieldExchange* pFX)  
{  
    pFX->SetFieldType(CFieldExchange::outputColumn);  
    RFX_Text(pFX, "CourseID", m_strCourseID);  
    RFX_Text(pFX, "InstructorID", m_strInstructorID);  
    RFX_Text(pFX, "RoomNo", m_strRoomNo);  
    RFX_Text(pFX, "Schedule", m_strSchedule);  
    RFX_Text(pFX, "SectionNo", m_strSectionNo);  
}  
```  
  
 После завершения инструкция SQL выглядит следующим образом:  
  
```  
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo   
    FROM SECTION  
```  
  
### Случай 3   lpszSQL \= инструкция SELECT\/FROM  
 Вместо автоматического создания с помощью RFX список столбцов задается вручную.  Такой способ может быть предпочтительным в следующих случаях:  
  
-   Если после инструкции **SELECT** необходимо указать ключевое слово **DISTINCT**.  
  
     Список столбцов должен соответствовать именам, типам и порядку перечисления столбцов в `DoFieldExchange`.  
  
-   Если необходимо вручную извлечь значения столбцов с помощью функции ODBC **::SQLGetData** вместо того, чтобы использовать RFX для автоматического связывания и извлечения столбцов.  
  
     Например, может быть необходимо включить новые столбцы, которые пользователь приложения добавил в базу данных после распространения приложения.  Соответственно, необходимо добавить новые члены\-поля данных, которые не были известны во время объявления класса с помощью мастера.  
  
     Список столбцов должен соответствовать именам, типам и порядку перечисления столбцов `DoFieldExchange`, после которых должны следовать имена столбцов, связываемых вручную.  Для получения дополнительной информации см. [Набор записей. Динамическая привязка столбцов данных \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
-   Если в предложении **FROM** необходимо выполнить соединение таблиц.  
  
     Дополнительные сведения и пример см. в разделе [Набор записей. Объединение \(ODBC\)](../Topic/Recordset:%20Performing%20a%20Join%20\(ODBC\).md).  
  
### Случай 4   lpszSQL \= SELECT\/FROM плюс WHERE и\/или ORDER BY  
 Указывается все: список столбцов \(основанный на вызовах RFX в `DoFieldExchange`\), список таблиц и содержимое предложений **WHERE** и\/или **ORDER BY**.  При указании предложений **WHERE** и\/или **ORDER BY** подобным образом нельзя использовать поля **m\_strFilter** и\/или `m_strSort`.  
  
### Случай 5   lpszSQL \= вызов хранимой процедуры  
 Если необходимо вызвать предопределенный запрос \(например, хранимую процедуру в базе данных Microsoft SQL Server\), следует записать оператор **CALL** в строке, передаваемой в `lpszSQL`.  Мастера не поддерживает объявление класса набора записей для вызова предопределенного запроса.  Не все предопределенные запросы возвращают записи.  
  
 Если предопределенный запрос не возвращает записи, можно воспользоваться функцией\-членом класса `CDatabase` `ExecuteSQL` напрямую.  Для предопределенных запросов, возвращающих записи, необходимо вручную записать вызовы RFX в `DoFieldExchange` для всех столбцов, возвращаемых процедурой.  Вызовы RFX должны иметь тот же порядок и возвращать те же типы, что и предопределенный запрос.  Для получения дополнительной информации см. [Набор записей. Объявление класса для предопределенного запроса \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).  
  
## См. также  
 [SQL. Типы данных SQL и C\+\+ \(ODBC\)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)   
 [SQL. Выполнение прямых вызовов SQL \(ODBC\)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)