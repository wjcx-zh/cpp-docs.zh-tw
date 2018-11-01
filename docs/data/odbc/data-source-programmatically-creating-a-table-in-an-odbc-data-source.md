---
title: 以程式設計方式建立 ODBC 資料來源中的資料表
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 139efb7a34baacb2bb6ad424d13f2d337eb12af6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661652"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>資料來源：以程式設計方式建立 ODBC 資料來源資料表

本主題說明如何建立資料表的資料來源，使用`ExecuteSQL`類別成員函式`CDatabase`，將函式傳遞字串，包含**CREATE TABLE** SQL 陳述式。

一般 MFC ODBC 資料來源的詳細資訊，請參閱[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)。 本主題[資料來源： 以程式設計方式設定 ODBC 資料來源](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md)描述建立資料來源。

當您建立的資料來源時，您可以輕鬆地建立使用資料表`ExecuteSQL`成員函式與**CREATE TABLE** SQL 陳述式。 例如，如果您有`CDatabase`物件呼叫`myDB`，您可以使用下列的 MFC 程式碼來建立資料表：

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

此程式碼範例會建立名為 「 辦公室 」 中所維護的 Microsoft Access 資料來源連接的資料表`myDB`; 資料表包含兩個欄位"OfficeID"和"OfficeName。 」

> [!NOTE]
>  中指定的欄位型別**CREATE TABLE** SQL 陳述式可能會根據您使用的 ODBC 驅動程式而有所不同。 Microsoft 的查詢計畫 （隨附於 Visual c + + 1.5） 是一種方式找出哪些欄位型別可為資料來源。 在查詢中，按一下**檔案**，按一下**Table_Definition**資料來源選取資料表，看看所示的型別**型別**下拉式方塊。 SQL 語法也可用來建立索引。

## <a name="see-also"></a>另請參閱

[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)