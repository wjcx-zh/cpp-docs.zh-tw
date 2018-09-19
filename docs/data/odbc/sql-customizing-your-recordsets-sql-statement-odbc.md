---
title: SQL： 自訂資料錄集的 SQL 陳述式 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0f35f2160914f498479a7fcc9fd9712eaaa6f897
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036679"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL：自訂資料錄集的 SQL 陳述式 (ODBC)

本主題說明：  
  
- 架構如何建構 SQL 陳述式  
  
- 如何覆寫的 SQL 陳述式  
  
> [!NOTE]
>  這項資訊適用於 MFC ODBC 類別。 如果您使用 MFC DAO 類別時，請參閱 「 比較 Microsoft Jet 資料庫引擎 SQL 和 ANSI SQL"DAO [說明] 中的主題。  
  
## <a name="sql-statement-construction"></a>SQL 陳述式建構  

資料錄集基底記錄的選取項目主要是根據 SQL**選取**陳述式。 當您宣告您的類別使用精靈時，它會寫入覆寫的新版`GetDefaultSQL`看起來像這樣的成員函式 (資料錄集類別稱為`CAuthors`)。  
  
```cpp  
CString CAuthors::GetDefaultSQL()  
{  
    return "AUTHORS";  
}  
```  
  
根據預設，此覆寫會傳回您指定使用精靈的資料表名稱。 在範例中，資料表名稱是 「 著作人 」。 當您稍後呼叫資料錄集的`Open`成員函式`Open`建構最終**選取**表單的陳述式：  
  
```  
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]   
       [ORDER BY m_strSort]  
```  
  
其中`table-name`取得藉由呼叫`GetDefaultSQL`並`rfx-field-list`取自 RFX 函式呼叫`DoFieldExchange`。 這是您取得**選取**陳述式除非您版本取代它覆寫在執行階段，雖然您也可以修改預設的陳述式使用的參數或篩選。  
  
> [!NOTE]
>  如果您指定的資料行名稱包含 （或可能包含） 空格，必須以方括號括住的名稱。 比方說，「 名字 」 的名稱應該是 「 [名字] 」。  
  
若要覆寫預設值**選取**陳述式，傳遞字串，包含完整**選取**當您呼叫的陳述式`Open`。 而不是建構它自己的預設字串，資料錄集，請使用您提供的字串。 如果您取代陳述式包含**何處**子句中，未指定篩選條件中的`m_strFilter`因為您會有兩個篩選條件陳述式。 同樣地，如果您取代陳述式包含**ORDER BY**子句中，未指定以排序`m_strSort`如此就不會有兩種排序陳述式。  
  
> [!NOTE]
>  如果您使用您的篩選 （或其他部分的 SQL 陳述式） 中的常值字串，您可能必須 「 加上引號"（指定的分隔符號括住） 這類特定 DBMS 的常值前置詞和字串常值後置字元 （字元）。  
  
也可能發生的作業，例如外部聯結中，特殊語法的需求視您的 DBMS 而定。 使用 ODBC 函數來取得這項資訊從您的驅動程式，針對 DBMS。 例如，呼叫`::SQLGetTypeInfo`特定的資料類型，例如`SQL_VARCHAR`、 要求的 LITERAL_PREFIX 和 LITERAL_SUFFIX 字元。 如果您要撰寫獨立資料庫的程式碼，請參閱在 < 附錄 C *ODBC SDK * * 程式設計人員參考*在 MSDN Library CD，如需詳細的語法資訊。  
  
資料錄集物件建構 SQL 陳述式，用來選取記錄，除非您傳遞自訂的 SQL 陳述式。 如何做到這點主要取決於您所傳遞的值*lpszSQL*參數`Open`成員函式。  
  
SQL 的一般形式**選取**陳述式：  
  
```  
SELECT [ALL | DISTINCT] column-list FROM table-list  
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]  
```  
  
其中一種方式新增**DISTINCT**關鍵字來資料錄集的 SQL 陳述式是內嵌在第一次的 RFX 函式呼叫中的關鍵字`DoFieldExchange`。 例如:   
  
```  
...  
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);  
...  
```  
  
> [!NOTE]
>  這項技術只能用於以唯讀方式開啟資料錄集。  
  
## <a name="overriding-the-sql-statement"></a>覆寫的 SQL 陳述式  

下表顯示作業的可能性*lpszSQL*參數來`Open`。 下表說明的案例資料表中。  
  
**LpszSQL 參數和產生的 SQL 字串**  
  
|案例|您傳遞 lpszSQL|結果的 SELECT 陳述式|  
|----------|------------------------------|------------------------------------|  
|1|NULL|**選取 ** *rfx 欄位清單* **FROM** *資料表名稱*<br /><br /> `CRecordset::Open` 呼叫`GetDefaultSQL`取得資料表名稱。 產生的字串是其中一個案例 2 到 5，依據`GetDefaultSQL`傳回。|  
|2|資料表名稱|**選取 ** *rfx 欄位清單* **FROM** *資料表名稱*<br /><br /> 欄位清單取自 RFX 陳述式，在`DoFieldExchange`。 如果`m_strFilter`並`m_strSort`不是空的將**何處**和/或**ORDER BY**子句。|  
|3 \*|完整**選取 **陳述式但不含**何處**或是**ORDER BY**子句|為成功。 如果`m_strFilter`並`m_strSort`不是空的將**何處**和/或**ORDER BY**子句。|  
|4 \*|完整**選取 **陳述式搭配**所在**和/或**ORDER BY**子句|為成功。 `m_strFilter` 和/或`m_strSort`必須保持空白或兩個篩選及 （或) 排序陳述式所產生。|  
|5 \*|預存程序的呼叫|為成功。|  
  
\* `m_nFields` 必須是小於或等於指定之資料行的數目**選取**陳述式。 每個資料行內指定的資料型別**選取**陳述式必須是相對應的 RFX 輸出資料行的資料類型相同。  
  
### <a name="case-1---lpszsql--null"></a>案例 1 lpszSQL = NULL  

資料錄集選取範圍取決於什麼`GetDefaultSQL`時傳回`CRecordset::Open`呼叫它。 案例 2 至 5 說明可能的字串。  
  
### <a name="case-2---lpszsql--a-table-name"></a>案例 2 lpszSQL = 資料表名稱  

資料錄集使用資料錄欄位交換 (RFX) 來建置資料行名稱的資料行清單，提供在 RFX 函式呼叫中的資料錄集類別的覆寫`DoFieldExchange`。 如果您使用精靈來宣告您的資料錄集類別時，此情況下 （前提是您傳遞您在精靈中指定相同的資料表名稱），就會有與案例 1 相同的結果。 如果您不使用精靈來撰寫您的類別，則案例 2 會是最簡單的方式來建構 SQL 陳述式。  
  
下列範例會建構從 MFC 資料庫應用程式中選取資料錄的 SQL 陳述式。 當架構會呼叫`GetDefaultSQL`成員函式，函式會傳回資料表，名稱`SECTION`。  
  
```cpp  
CString CEnrollSet::GetDefaultSQL()  
{  
    return "SECTION";  
}  
```  
  
若要取得的資料行名稱為 SQL**選取 **陳述式中，這個架構會呼叫`DoFieldExchange`成員函式。  
  
```cpp  
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
  
完成時，SQL 陳述式看起來像這樣：  
  
```sql  
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo   
    FROM SECTION  
```  
  
### <a name="case-3---lpszsql--a-selectfrom-statement"></a>案例 3 lpszSQL = SELECT / FROM 陳述式  

而不是依賴自動建構 RFX 以手動方式指定資料行清單。 您可能想要執行時：  
  
- 您想要指定**DISTINCT**關鍵字後面**選取**。  
  
     您的資料行清單應該符合的資料行名稱和類型相同的順序，因為它們會列在`DoFieldExchange`。  
  
- 您有理由要手動擷取資料行值使用 ODBC 函數`::SQLGetData`而不是依賴 RFX 繫結，並為您擷取資料行。  
  
     您可能，比方說，要配合您的應用程式的客戶會加入至資料庫資料表之後已散發應用程式, 的新資料行。 您必須加入這些額外的欄位資料成員，在類別宣告使用精靈時所不知道。  
  
     您的資料行清單應該符合的資料行名稱和類型相同的順序，因為它們會列在`DoFieldExchange`，後面接著手動繫結的資料行的名稱。 如需詳細資訊，請參閱 <<c0> [ 資料錄集： 動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
- 您想要藉由指定多個資料表中的聯結的資料表**FROM**子句。  
  
     資訊和範例，請參閱[資料錄集： 執行聯結 (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)。  
  
### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>案例 4 lpszSQL = SELECT / 從加上其中和/或 ORDER BY  

您指定的所有項目： 資料行清單 (根據 RFX 呼叫`DoFieldExchange`)，[資料表] 清單中，與內容**其中**及/或**ORDER BY**子句。 如果您指定您**何處**及/或**ORDER BY**子句如此一來，請勿使用`m_strFilter`及/或`m_strSort`。  
  
### <a name="case-5---lpszsql--a-stored-procedure-call"></a>案例 5 lpszSQL = 預存程序呼叫  

如果您需要呼叫預先定義的查詢 （例如 Microsoft SQL Server 資料庫中的預存程序），您必須撰寫**呼叫**傳遞至字串中的陳述式*lpszSQL*。 精靈不支援宣告用於呼叫預先定義的查詢的資料錄集類別。 並非所有預先定義的查詢會傳回資料錄。  
  
如果預先定義的查詢不會傳回記錄，您可以使用`CDatabase`成員函式`ExecuteSQL`直接。 預先定義的查詢傳回的記錄，您必須一併手動撰寫呼叫 RFX`DoFieldExchange`程序會傳回任何資料行。 Rfx 必須位於相同的順序，並傳回相同的類型，預先定義的查詢。 如需詳細資訊，請參閱 <<c0> [ 資料錄集： 宣告的類別的預先定義的查詢 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。  
  
## <a name="see-also"></a>另請參閱  

[SQL：SQL 和 C++ 資料類型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL：製作直接的 SQL 呼叫 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)