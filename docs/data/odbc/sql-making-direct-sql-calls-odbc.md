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
ms.openlocfilehash: 17b3279a4803a61595af64ab18629d6cf69f0f10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549847"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL：製作直接的 SQL 呼叫 (ODBC)

本主題說明：

- 何時使用直接 SQL 呼叫。

- [如何使直接 SQL 呼叫到資料來源](#_core_making_direct_sql_function_calls)。

> [!NOTE]
>  這項資訊適用於 MFC ODBC 類別。 如果您使用 MFC DAO 類別時，請參閱 「 比較 Microsoft Jet 資料庫引擎 SQL 和 ANSI SQL"DAO [說明] 中的主題。

##  <a name="_core_when_to_call_sql_directly"></a> 直接呼叫 SQL 的時機

若要建立新的資料表，卸除 （刪除） 資料表，改變現有的資料表、 建立索引，以及執行其他 SQL 功能會變更[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)結構描述中，您必須直接到使用資料庫的資料來源發出的 SQL 陳述式定義語言 (DDL)。 當您使用精靈來建立資料表的資料錄集 （在設計階段） 時，您可以選擇哪些資料行的資料表，以便表示資料錄集。 這不允許您或另一位使用者的資料來源加入資料表之後，編譯程式之後的資料行。 資料庫類別直接，不支援 DDL，但您仍然可以撰寫程式碼，以新資料行繫結至您的資料錄集，以動態方式在執行階段。 如需有關如何執行此繫結的資訊，請參閱 <<c0> [ 資料錄集： 繫結資料行的以動態方式 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

您可以使用自己的 DBMS 改變結構描述或另一個工具，可讓您執行 DDL 函式。 您也可以使用 ODBC 函數呼叫的將 SQL 陳述式，例如呼叫預先定義的查詢 （預存程序） 不會傳回記錄傳送。

##  <a name="_core_making_direct_sql_function_calls"></a> 製作直接的 SQL 函式呼叫

您可以直接執行 SQL 呼叫，使用[CDatabase 類別](../../mfc/reference/cdatabase-class.md)物件。 設定您的 SQL 陳述式字串 (通常`CString`) 並將它傳遞給[cdatabase:: Executesql](../../mfc/reference/cdatabase-class.md#executesql)成員函式程式`CDatabase`物件。 如果您使用 ODBC 函數呼叫來傳送通常會傳回資料錄的 SQL 陳述式時，會忽略記錄。

## <a name="see-also"></a>另請參閱

[SQL](../../data/odbc/sql.md)