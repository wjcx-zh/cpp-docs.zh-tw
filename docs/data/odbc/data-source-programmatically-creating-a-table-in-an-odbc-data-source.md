---
title: 以程式設計方式在 ODBC 資料來源中建立資料表
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 25c975560d6a73ce67294d97830b2f5bec9cd635
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213274"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>資料來源：以程式設計方式建立 ODBC 資料來源資料表

本主題說明如何使用 `CDatabase`類別的 `ExecuteSQL` 成員函式，為您的資料來源建立資料表，並將包含**CREATE TABLE** SQL 語句的字串傳遞給該函數。

如需 MFC 中 ODBC 資料來源的一般資訊，請參閱[資料來源（ODBC）](../../data/odbc/data-source-odbc.md)。 主題[資料來源：以程式設計方式設定 ODBC 資料來源](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md)說明如何建立資料來源。

建立資料來源之後，您可以使用 `ExecuteSQL` 成員函式和**CREATE TABLE** SQL 語句輕鬆地建立資料表。 例如，如果您有一個稱為 `myDB`的 `CDatabase` 物件，您可以使用下列 MFC 程式碼來建立資料表：

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

此程式碼範例會在 `myDB`維護的 Microsoft Access 資料來源連接中，建立名為「辦公室」的資料表;資料表包含 "OfficeID" 和 "OfficeName" 兩個欄位。

> [!NOTE]
>  **CREATE TABLE** SQL 語句中指定的欄位類型可能會根據您所使用的 ODBC 驅動程式而有所不同。 Microsoft Query 程式（與 Visual C++ 1.5 一起散發）是探索哪些欄位類型適用于資料來源的一種方式。 在 Microsoft 查詢 中 **，按一下** 檔案，按一下  **Table_Definition**，選取資料來源中的資料表，然後查看 **類型** 下拉式方塊中顯示的類型。 SQL 語法也存在於建立索引。

## <a name="see-also"></a>另請參閱

[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)
