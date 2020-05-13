---
title: 在 ODBC 資料來源以程式設計來建立表
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: 6cf26cad7fe39f374daf371902525087b446658c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358830"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>資料來源：以程式設計方式建立 ODBC 資料來源資料表

本主題介紹如何使用類`ExecuteSQL``CDatabase`的成員函數為數據源創建表,傳遞包含 CREATE **TABLE** SQL 語句的字串。

有關 MFC 中 ODBC 數據來源的一般資訊,請參閱[資料來源 (ODBC)。](../../data/odbc/data-source-odbc.md) 主題[資料來源:以程式設計方式配置 ODBC 資料來源](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md)描述建立資料來源。

建立資料來源後,可以輕鬆地使用`ExecuteSQL`成員函數和 CREATE **TABLE** SQL 語句創建表。 例如,如果您有一個`CDatabase`稱為的`myDB`物件 ,則可以使用以下 MFC 代碼建立表:

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

此代碼示例在 Microsoft 訪問數據源連接中創建名為「OFFICE」的`myDB`表,該表包含兩個字段"OfficeID"和"辦公室名稱"。

> [!NOTE]
> **CREATE TABLE** SQL 語句中指定的欄位類型可能因您使用的 ODBC 驅動程式而異。 Microsoft 查詢程式(使用 Visual C++ 1.5 分發)是發現數據來源可用的欄位類型的一種方式。 在 Microsoft**File**查詢 中,按下「**檔」,按一下「Table_Definition」**,從資料源中選擇一個表,並查看 **「類型組合」** 框中顯示的類型。 SQL 語法也存在以創建索引。

## <a name="see-also"></a>另請參閱

[資料來源](../../data/odbc/data-source-odbc.md)
