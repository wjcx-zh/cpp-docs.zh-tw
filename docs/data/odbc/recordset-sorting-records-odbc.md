---
title: 資料錄集：排序資料錄 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 8b4deea1d8cbd4abe01ccc7a4114131378abe463
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366918"
---
# <a name="recordset-sorting-records-odbc"></a>資料錄集：排序資料錄 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題介紹如何對記錄集進行排序。 您可以指定一個或多個列,以這些列為基礎排序,也可以指定升序或降序 **(ASC**或**DESC;****ASC**是每個指定列的預設值。 例如,如果指定兩列,則記錄首先在命名的第一列上排序,然後對命名的第二列進行排序。 SQL **ORDER BY**子句定義排序。 當框架將 ORDER **BY**子句追加到記錄集的 SQL 查詢時,子句將控制所選內容的順序。

在構造物件后,但在調用物件`Open`成員函數之前(或在調`Requery``Open`用 成員函數之前),必須建立記錄集的排序順序。

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>為紀錄集物件指定排序順序

1. 建構新的記錄集物件(或準備調用`Requery`現有記錄集物件)。

1. 設置物件[m_strSort](../../mfc/reference/crecordset-class.md#m_strsort)資料成員的值。

   排序是 null 中止的字串。 它包含**ORDER BY**子句的內容,但不包含關鍵字**ORDER BY**。 例如，使用：

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   否

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. 設定所需的任何其他選項,如篩選器、鎖定模式或參數。

1. 調用`Open`新物件(`Requery`或現有物件)。

所選記錄按指定順序排序。 例如,要按姓氏(名字)降序排序一組學生記錄,然後按名字排序,可以執行以下操作:

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

記錄集包含所有學生記錄,按姓氏按降序排序 (Z 到 A),然後按名字排序。

> [!NOTE]
> 如果選擇通過將自己的 SQL 字串傳遞`Open`給 來覆蓋記錄集的預設 SQL 字串,則如果自定義字串具有 ORDER **BY**子句,請不要設置排序。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[資料錄集：篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
