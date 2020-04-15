---
title: SQL：製作直接的 SQL 呼叫 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
ms.openlocfilehash: e2421e047d217fdc7a138509385399fa37d36a1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374504"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL：製作直接的 SQL 呼叫 (ODBC)

本主題將說明：

- 何時使用直接 SQL 調用。

- [如何直接對資料來源進行 SQL 呼叫](#_core_making_direct_sql_function_calls)。

> [!NOTE]
> 此資訊適用於 MFC ODBC 類別。 如果您正在使用 MFC DAO 類,請參閱 DAO 説明中的主題「微軟噴氣資料庫引擎 SQL 和 ANSI SQL 的比較」。。

## <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a>何時直接呼叫 SQL

要建立新表、刪除(刪除)表、更改現有表、創建索引和執行更改[資料源 (ODBC)](../../data/odbc/data-source-odbc.md)架構的其他 SQL 函數,必須使用資料庫定義語言 (DDL) 直接向資料來源發出 SQL 語句。 使用嚮導為表創建記錄集(在設計時)時,可以選擇要在記錄集中表示的表的列。 這不允許在編譯程式後,稍後將數據源的其他使用者添加到表中。 資料庫類不直接支援 DDL,但您仍然可以編寫代碼,在運行時動態地將新列綁定到記錄集。 有關如何執行此操作綁定的資訊,請參閱[記錄集:動態綁定數據列 (ODBC)。](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

您可以使用 DBMS 本身來更改架構或其他工具,以便執行 DDL 函數。 您還可以使用 ODBC 函數呼叫發送 SQL 語句,例如呼叫不返回記錄的預定義查詢(儲存過程)。

## <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a>直接 SQL 函式呼叫

您可以使用[CDatabase 類](../../mfc/reference/cdatabase-class.md)物件直接執行 SQL 呼叫。 設置 SQL 語句字串(通常`CString`在中),並將其傳遞`CDatabase`給 物件的[CDatabase::執行 SQL](../../mfc/reference/cdatabase-class.md#executesql)成員函數。 如果使用 ODBC 函數呼叫發送通常傳回記錄的 SQL 語句,則忽略這些記錄。

## <a name="see-also"></a>另請參閱

[SQL](../../data/odbc/sql.md)
