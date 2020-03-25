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
ms.openlocfilehash: 9240a227cdc4004d1e6e2b7ac26946ca233b71ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212624"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL：製作直接的 SQL 呼叫 (ODBC)

本主題將說明：

- 使用直接 SQL 呼叫的時機。

- 對[資料來源進行直接 SQL 呼叫的方式](#_core_making_direct_sql_function_calls)。

> [!NOTE]
>  此資訊適用於 MFC ODBC 類別。 如果您要使用 MFC DAO 類別，請參閱 DAO 說明中的 < Microsoft Jet 資料庫引擎 SQL 和 ANSI SQL 的比較主題。

##  <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a>直接呼叫 SQL 的時機

若要建立新的資料表、卸載（刪除）資料表、改變現有的資料表、建立索引，以及執行其他可變更[資料來源（ODBC）](../../data/odbc/data-source-odbc.md)架構的 sql 函數，您必須使用資料庫定義語言（DDL）將 sql 語句直接發行至資料來源。 當您使用 wizard 建立資料表的記錄集時（在設計階段），您可以選擇要在記錄集中表示的資料表資料行。 這不允許您或資料來源的其他使用者在您的程式編譯之後加入資料表的資料行。 資料庫類別不直接支援 DDL，但是您仍然可以撰寫程式碼，在執行時間動態地將新的資料行系結至您的記錄集。 如需如何執行此系結的詳細資訊，請參閱[記錄集：動態地系結資料行（ODBC）](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

您可以使用 DBMS 本身來改變架構或另一個可讓您執行 DDL 函數的工具。 您也可以使用 ODBC 函數呼叫來傳送 SQL 語句，例如呼叫不會傳回記錄的預先定義查詢（預存程式）。

##  <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a>進行直接 SQL 函數呼叫

您可以使用[CDatabase 類別](../../mfc/reference/cdatabase-class.md)物件，直接執行 SQL 呼叫。 設定 SQL 語句字串（通常在 `CString`中），並將它傳遞至您 `CDatabase` 物件的[CDatabase：： ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql)成員函式。 如果您使用 ODBC 函數呼叫來傳送通常會傳回記錄的 SQL 語句，則會忽略記錄。

## <a name="see-also"></a>另請參閱

[SQL](../../data/odbc/sql.md)
