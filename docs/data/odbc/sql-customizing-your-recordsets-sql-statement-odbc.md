---
title: SQL：自訂資料錄集的 SQL 陳述式 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
ms.openlocfilehash: 083d268d2b2f2eef072809b1afde9d6ea34f6996
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374510"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL：自訂資料錄集的 SQL 陳述式 (ODBC)

本主題將說明：

- 框架如何建構 SQL 語句

- 如何重寫 SQL 語句

> [!NOTE]
> 此資訊適用於 MFC ODBC 類別。 如果您正在使用 MFC DAO 類,請參閱 DAO 説明中的主題「微軟噴氣資料庫引擎 SQL 和 ANSI SQL 的比較」。。

## <a name="sql-statement-construction"></a>SQL 語句建構

記錄集主要基於 SQL **SELECT**語句選擇記錄。 使用嚮導聲明類時,它會編寫一個類似於這樣的`GetDefaultSQL`成員函數的重寫版本(對於`CAuthors`稱為的記錄集類)。

```cpp
CString CAuthors::GetDefaultSQL()
{
    return "AUTHORS";
}
```

預設情況下,此覆蓋返回使用嚮導指定的表名稱。 在此示例中,表名稱為"問題"。 稍後呼叫紀錄集`Open`的成員函數時,`Open`建構窗體的最終**SELECT**語句:

```
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]
       [ORDER BY m_strSort]
```

其中`table-name`通過調`GetDefaultSQL`用 獲得,`rfx-field-list`並`DoFieldExchange`從中的 RFX 函數調用獲得。 這是**選擇**語句的啟用,除非您在執行時將其替換為重寫版本,儘管您也可以使用參數或篩選器修改預設語句。

> [!NOTE]
> 如果指定包含(或可能包含)空格的列名稱,則必須將名稱括在方括弧中。 例如,"名字"的名稱應為"[名字]。

要重寫預設**SELECT**語句,請在`Open`呼叫 時傳遞包含完整**SELECT**語句的字串。 記錄集使用您提供的字串,而不是建構自己的預設字串。 如果替換語句包含**WHERE**子句,請不要指定篩選`m_strFilter`器, 因為您將有兩個篩選器語句。 同樣,如果替換語句包含 ORDER **BY**子句,則不要`m_strSort`指定 排序 ,這樣您就不會有兩個排序語句。

> [!NOTE]
> 如果在篩選器(或 SQL 語句的其他部分)中使用文字字串,則可能需要使用特定於 DBMS 的文本前置碼和文字後綴字元(或字元)來「報價」(在指定的分隔符中)引用此類字串。

根據 DBMS,您可能還會遇到外部聯接等操作的特殊語法要求。 使用 ODBC 函數從 DBMS 的驅動程式獲取此資訊。 例如,調用`::SQLGetTypeInfo`特定數據類型(`SQL_VARCHAR`如 )以請求LITERAL_PREFIX和LITERAL_SUFFIX字元。 如果要編寫與資料庫無關的代碼,請參閱[ODBC 程式師參考](/sql/odbc/reference/odbc-programmer-s-reference)中的[附錄 C:SQL 語法](/sql/odbc/reference/appendixes/appendix-c-sql-grammar),瞭解詳細的語法資訊。

記錄集物件建構它用來選擇記錄的 SQL 語句,除非您傳遞自訂 SQL 語句。 如何做到這一點主要取決於您在`Open`成員函數的*lpszSQL*參數中傳遞的值。

SQL **SELECT**語句的一般形式是:

```
SELECT [ALL | DISTINCT] column-list FROM table-list
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]
```

將**DISTINCT**關鍵字添加到記錄集的 SQL 語句的一種方法是在 中的第一個`DoFieldExchange`RFX 函數調用 中嵌入該關鍵字。 例如：

```
...
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);
...
```

> [!NOTE]
> 僅此技術將打開為唯讀的記錄集使用。

## <a name="overriding-the-sql-statement"></a>重寫 SQL 語句

下表顯示了*lpszSQL*`Open`參數到 的可能性。 下表中的案例在表之後進行說明。

**lpszSQL 參數與產生的 SQL 字串**

|案例|您在 lpszSQL 中傳遞的內容|產生的 SELECT 敘述|
|----------|------------------------------|------------------------------------|
|1|NULL|**從***表名***中選擇** *rfx 欄位清單*<br /><br /> `CRecordset::Open`調用`GetDefaultSQL`以獲取表名稱。 產生的字串是案例 2 到 5`GetDefaultSQL`之一, 具體取決於返回的內容。|
|2|資料表名稱|**從***表名***中選擇** *rfx 欄位清單*<br /><br /> 欄位清單取自`DoFieldExchange`中的 RFX 語句。 如果`m_strFilter``m_strSort`和 不是空,則添加**WHERE**和/或**ORDER BY**子句。|
|3\*|完整的**SELECT**語句,但沒有**WHERE**或**ORDER BY**子句|通過。 如果`m_strFilter``m_strSort`和 不是空,則添加**WHERE**和/或**ORDER BY**子句。|
|4\*|帶有**WHERE**和/或 ORDER **BY**子句的完整**SELECT**語句|通過。 `m_strFilter`和/或`m_strSort`必須保持空,或生成兩個篩選器和/或排序語句。|
|5\*|儲存程序的呼叫|通過。|

\*`m_nFields`必須小於或等於**SELECT**語句中指定的列數。 **SELECT**語句中指定的每列的數據類型必須與相應 RFX 輸出列的數據類型相同。

### <a name="case-1---lpszsql--null"></a>案例 1 lpszSQL = NULL

記錄集選擇取決於調用時`GetDefaultSQL``CRecordset::Open`返回的內容。 案例 2 到 5 描述可能的字串。

### <a name="case-2---lpszsql--a-table-name"></a>案例 2 lpszSQL = 表名稱

紀錄集使用記錄欄位交換 (RFX) 從紀錄集類別重寫中的 RFX 函數呼叫中提供的欄`DoFieldExchange`位中的欄位中的欄位 。 如果使用嚮導聲明記錄集類,則此案例的結果與案例 1 相同(前提是傳遞您在嚮導中指定的表名)。 如果不使用嚮導編寫類,則案例 2 是構造 SQL 語句的最簡單方法。

下面的示例構造一個 SQL 語句,該語句從 MFC 資料庫應用程式中選擇記錄。 當框架呼叫`GetDefaultSQL`成員函數時,該函數會傳回表`SECTION`的名稱 。

```cpp
CString CEnrollSet::GetDefaultSQL()
{
    return "SECTION";
}
```

要取得 SQL **SELECT**語句的列名稱,框架`DoFieldExchange`將調用 成員函數。

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

完成後,SQL 語句如下所示:

```sql
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo
    FROM SECTION
```

### <a name="case-3---lpszsql--a-selectfrom-statement"></a>案例 3 lpszSQL = SELECT/FROM 語句

您可以手動指定列清單,而不是依靠 RFX 自動構造它。 您可能需要在:

- 您希望在**SELECT**之後指定 **「指定**」關鍵字。

   列清單應按與 在`DoFieldExchange`中 列出的列名稱和類型的順序匹配。

- 您有理由使用 ODBC`::SQLGetData`函數 手動檢索列值,而不是依賴 RFX 為您綁定和檢索列。

   例如,您可能希望容納應用程式客戶在應用程式分發後添加到資料庫表的新列。 您需要添加這些額外的欄位數據成員,這些成員在使用嚮導聲明類時並不知道。

   列清單應按與`DoFieldExchange`列 名稱和類型的順序匹配,後跟手動綁定列的名稱。 有關詳細資訊,請參閱[記錄集:動態綁定數據列 (ODBC)。](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- 您希望透過在**FROM**子句中指定多個表來聯接表。

   有關資訊和示例,請參閱[記錄集:執行聯接 (ODBC)。](../../data/odbc/recordset-performing-a-join-odbc.md)

### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>案例 4 lpszSQL = 選擇/從+WHERE 和/或 ORDER BY

指定所有內容:列清單(基於中的`DoFieldExchange`RFX 調用),表清單以及**WHERE**和/或 ORDER **BY**子句的內容。 如果以這種方式指定**WHERE**和/或**ORDER BY**`m_strFilter`子句`m_strSort`,請不要 使用和 /或 。

### <a name="case-5---lpszsql--a-stored-procedure-call"></a>案例 5 lpszSQL = 儲存過程呼叫

如果需要調用預定義的查詢(如 Microsoft SQL Server 資料庫中的儲存過程),則必須在傳遞給*lpszSQL*的字串中編寫**CALL**語句。 嚮導不支援聲明用於調用預定義查詢的記錄集類。 並非所有預定義的查詢都返回記錄。

如果預定義的查詢不返回記錄,則可以直接使用`CDatabase`成員函數`ExecuteSQL`。 對於返回記錄的預定義查詢,還必須手動`DoFieldExchange`為過程返回的任何列寫入 RFX 調用。 RFX 調用必須按與預定義的查詢相同的順序返回相同的類型。 有關詳細資訊,請參閱[記錄集:為預先定義查詢 (ODBC) 宣告類別](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。

## <a name="see-also"></a>另請參閱

[SQL：SQL 和 C++ 資料類型 (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL：製作直接的 SQL 呼叫 (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
