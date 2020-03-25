---
title: 資料錄集：排序資料錄 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 4bbe635cdda9152be6ba178b863147db93b7c706
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212741"
---
# <a name="recordset-sorting-records-odbc"></a>資料錄集：排序資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題說明如何排序記錄集。 您可以指定要做為排序依據的一或多個資料行，而且可以指定遞增或遞減順序（**ASC**或**DESC**）。每個指定資料行的**ASC**是預設值）。 例如，如果您指定兩個數據行，則會先在名為的第一個資料行上排序記錄，然後在第二個名為的資料行上排序。 SQL **ORDER by**子句會定義排序。 當架構將**ORDER BY**子句附加至記錄集的 SQL 查詢時，子句會控制選取範圍的順序。

您必須在建立物件之後，但是在呼叫其 `Open` 成員函式（或在先前已呼叫其 `Open` 成員函式的現有記錄集物件的 `Requery` 成員函式）之前，建立記錄集的排序次序。

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>若要指定記錄集物件的排序次序

1. 建立新的 recordset 物件（或準備呼叫現有的記錄集物件 `Requery`）。

1. 設定物件的[m_strSort](../../mfc/reference/crecordset-class.md#m_strsort)資料成員的值。

   排序是以 null 結束的字串。 它包含**ORDER by**子句的內容，而不是關鍵字**ORDER by**。 例如，使用：

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   否

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. 設定您需要的任何其他選項，例如篩選準則、鎖定模式或參數。

1. 呼叫新物件的 `Open` （或現有物件 `Requery`）。

選取的記錄會依照指定的順序排序。 例如，若要依姓氏和名字的遞減順序排序一組學生記錄，請執行下列動作：

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

記錄集包含所有的學生記錄，並依姓氏和名字的遞減順序（Z 到 A）排序。

> [!NOTE]
>  如果您選擇藉由將您自己的 SQL 字串傳遞至 `Open`來覆寫記錄集的預設 SQL 字串，請勿在您的自訂字串具有**ORDER by**子句的情況下設定排序。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[資料錄集：篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
