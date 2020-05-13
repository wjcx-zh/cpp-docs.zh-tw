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
ms.openlocfilehash: 56b8c4f52ec294f58a760e1309d32aa81286ddec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367009"
---
# <a name="recordset-filtering-records-odbc"></a>資料錄集：篩選資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題介紹如何篩選記錄集,以便它僅選擇可用記錄的特定子集。 例如,您可能只想為特定課程(如 MATH101)選擇類節。 篩選器是由 SQL **WHERE**子句的內容定義的搜索條件。 當框架將其追加到記錄集的 SQL 語句時 **,WHERE**子句將約束選擇。

在建構物件後,但在調用其成員`Open`函數之前(或在調用成員函數之前),必須建立記錄集物件的篩選器(或在調用以前`Requery`調用其成員`Open`函數的現有記錄集物件的成員函數之前)。

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>為記錄集物件指定篩選器

1. 構造新的記錄集物件(或準備調用`Requery`現有物件)。

1. 設置物件[m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)資料成員的值。

   篩選器是一個空端接字串,其中包含 SQL **WHERE**子句的內容,但不包含關鍵字**WHERE**。 例如，使用：

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   否

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  文字字串"MATH101"上面用單個引號顯示。 在 ODBC SQL 規範中,單個引號用於表示字串文本。 在這種情況下,請查看您的 ODBC 驅動程式文件以瞭解 DBMS 的報價要求。 此語法在本主題末尾也進一步討論。

1. 設置所需的任何其他選項,如排序順序、鎖定模式或參數。 指定參數特別有用。 有關對篩選器進行參數化的資訊,請參閱[記錄集:參數化記錄集 (ODBC)。](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

1. 調用`Open`新物件(`Requery`或以前打開的物件)。

> [!TIP]
> 在篩選器中使用參數可能是檢索記錄的最有效方法。

> [!TIP]
> 紀錄組篩選器可用於[聯接](../../data/odbc/recordset-performing-a-join-odbc.md)表和使用以執行時取得或計算的[參數](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

記錄集僅選擇滿足您指定的搜尋條件的記錄。 例如,要指定上述課程篩選器(假設當前設置的變數`strCourseID`,例如設置為"MATH101"),請執行以下操作:

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

記錄集包含 MATH101 的所有類部分的記錄。

請注意,使用字串變數在上面的範例中如何設置篩選器字串。 這是典型的用法。 但是,假設您要為課程 ID 指定文本值 100。 以下程式碼展示如何使用文字值正確設定篩選器字串:

```
m_strFilter = "StudentID = '100'";   // correct
```

請注意使用單引號字元;如果直接設定篩選器字串,則篩選器字串**不是**:

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

上面顯示的報價符合 ODBC 規範,但某些 DBMS 可能需要其他報價字元。 有關詳細資訊,請參閱[SQL:自訂記錄集的 SQL 語句 (ODBC)。](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

> [!NOTE]
> 如果選擇通過將自己的 SQL 字串傳遞`Open`給 來覆蓋記錄集的預設 SQL 字串,則如果自定義字串具有**WHERE**子句,則不應設置篩選器。 有關重寫預設 SQL 的詳細資訊,請參閱[SQL:自訂記錄集的 SQL 語句 (ODBC)。](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：排序資料錄 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[資料錄集：資料錄集選取資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[資料錄集：資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
