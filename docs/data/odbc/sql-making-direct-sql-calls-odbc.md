---
title: SQL： 製作直接的 SQL 呼叫 (ODBC) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2134fc41b604ffd659f9ee075abc9d462ff4f0db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093369"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL：製作直接的 SQL 呼叫 (ODBC)
本主題說明：  
  
-   何時使用直接 SQL 呼叫。  
  
-   [如何進行直接 SQL 呼叫到資料來源](#_core_making_direct_sql_function_calls)。  
  
> [!NOTE]
>  這項資訊適用於 MFC ODBC 類別。 如果您使用 MFC DAO 類別時，請參閱"比較的 Microsoft Jet 資料庫引擎 SQL 和 ANSI SQL"DAO [說明] 中的主題。  
  
##  <a name="_core_when_to_call_sql_directly"></a> 當直接呼叫 SQL  
 若要建立新的資料表，卸除資料表 (delete)、 變更現有的資料表、 建立索引，以及執行其他 SQL 功能變更[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)結構描述中，您必須發出 SQL 陳述式來使用資料庫的資料來源定義語言 (DDL)。 當您使用精靈來建立資料表的資料錄集 （在設計階段） 時，您可以選擇以代表資料錄集中的資料表資料行。 這不允許您或其他使用者的資料來源加入資料表之後，編譯您的程式之後的資料行。 資料庫類別不直接支援 DDL，但您仍然可以寫入新資料行繫結至您的資料錄集，以動態方式在執行階段的程式碼。 如需如何執行此繫結資訊，請參閱[資料錄集： 動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
 您可以使用 DBMS 本身來變更結構描述或另一個工具，可讓您執行 DDL 函式。 您也可以使用 ODBC 函數呼叫的將 SQL 陳述式，例如先呼叫預先定義的查詢 （預存程序） 不會傳回記錄傳送。  
  
##  <a name="_core_making_direct_sql_function_calls"></a> 進行直接 SQL 函式呼叫  
 您可以直接執行使用 SQL 呼叫[CDatabase 類別](../../mfc/reference/cdatabase-class.md)物件。 設定您的 SQL 陳述式字串 (通常在`CString`) 並將它傳遞給[cdatabase:: Executesql](../../mfc/reference/cdatabase-class.md#executesql)成員函式的程式`CDatabase`物件。 如果您使用 ODBC 函數呼叫來傳送通常會傳回記錄的 SQL 陳述式時，會忽略記錄。  
  
## <a name="see-also"></a>另請參閱  
 [SQL](../../data/odbc/sql.md)