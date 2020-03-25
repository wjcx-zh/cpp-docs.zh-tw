---
title: 資料錄集：篩選資料錄 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
ms.openlocfilehash: 2e742ee02e142fd87df3f149379d9971c4acd166
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212900"
---
# <a name="recordset-filtering-records-odbc"></a>資料錄集：篩選資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題說明如何篩選記錄集，使其只選取可用記錄的特定子集。 例如，您可能只想要選取特定課程的類別區段，例如 MATH101。 篩選器是由 SQL **WHERE**子句的內容所定義的搜尋條件。 當架構將它附加至記錄集的 SQL 語句時， **WHERE**子句會限制選取範圍。

您必須在建立物件之後，但是在呼叫其 `Open` 成員函式（或在先前已呼叫其 `Open` 成員函式的現有記錄集物件的 `Requery` 成員函式）之前，建立記錄集物件的篩選。

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>若要指定記錄集物件的篩選

1. 建立新的記錄集物件（或準備呼叫現有物件的 `Requery`）。

1. 設定物件的[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)資料成員的值。

   篩選器是以 null 終止的字串，其中包含 SQL **WHERE**子句的內容，而不是關鍵字**WHERE**。 例如，使用：

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   否

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  常值字串 "MATH101" 會以上面的單引號括住。 在 ODBC SQL 規格中，單引號是用來表示字元字串常值。 在此情況下，請檢查您的 ODBC 驅動程式檔，以取得 DBMS 的報價需求。 此語法也會在本主題的結尾附近進一步討論。

1. 設定您需要的任何其他選項，例如排序次序、鎖定模式或參數。 指定參數特別有用。 如需參數化篩選器的相關資訊，請參閱[記錄集：參數化記錄集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

1. 呼叫新物件的 `Open` （或先前開啟之物件的 `Requery`）。

> [!TIP]
>  在篩選準則中使用參數可能是最有效率的方式來抓取記錄。

> [!TIP]
>  記錄集篩選適用于[聯結](../../data/odbc/recordset-performing-a-join-odbc.md)資料表，以及根據在執行時間取得或計算的資訊來使用[參數](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

記錄集只會選取符合您指定之搜尋條件的記錄。 例如，若要指定上述的課程篩選器（假設目前已設定變數 `strCourseID`，例如 "MATH101"），請執行下列動作：

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

記錄集包含 MATH101 所有類別區段的記錄。

請注意，在上述範例中使用字串變數設定篩選字串的方式。 這是典型的使用方式。 但假設您想要為課程識別碼指定常值100。 下列程式碼顯示如何使用常值來正確設定篩選字串：

```
m_strFilter = "StudentID = '100'";   // correct
```

請注意單引號字元的使用;如果您直接設定篩選字串，篩選字串**不**會是：

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

如上所示的引號符合 ODBC 規格，但部分 Dbms 可能需要其他引號字元。 如需詳細資訊，請參閱[SQL：自訂記錄集的 SQL 語句（ODBC）](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。

> [!NOTE]
>  如果您選擇藉由將您自己的 SQL 字串傳遞至 `Open`來覆寫記錄集的預設 SQL 字串，如果您的自訂字串具有**WHERE**子句，則不應該設定篩選。 如需覆寫預設 SQL 的詳細資訊，請參閱[SQL：自訂記錄集的 SQL 語句（ODBC）](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：排序資料錄 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[資料錄集：資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[資料錄集：資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
