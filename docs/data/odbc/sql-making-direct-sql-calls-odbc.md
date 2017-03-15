---
title: "SQL：製作直接的 SQL 呼叫 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "從 ODBC 進行直接 SQL 呼叫"
  - "ODBC, SQL 呼叫"
  - "SQL 呼叫"
  - "SQL, 直接從 ODBC 呼叫"
  - "SQL, 從 ODBC 的直接呼叫"
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# SQL：製作直接的 SQL 呼叫 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個主題說明：  
  
-   使用直接 SQL 呼叫的時機  
  
-   [如何執行資料來源的直接 SQL 呼叫](#_core_making_direct_sql_function_calls)  
  
> [!NOTE]
>  本資訊適用於 MFC ODBC 類別。  如果您正在使用 MFC DAO 類別，請參閱《DAO 說明》中的＜比較 Microsoft Jet Database Engine SQL 與 ANSI SQL＞主題。  
  
##  <a name="_core_when_to_call_sql_directly"></a> 直接呼叫 SQL 的時機  
 若要建立新的資料表、卸除 \(刪除\) 資料表、變更現有的資料表、建立索引和執行其他變更[資料來源 \(ODBC\)](../../data/odbc/data-source-odbc.md) 結構描述的 SQL 函式，您必須向使用資料定義語言 \(DDL\) 的資料來源直接發出一個 SQL 陳述式。  當您使用精靈來建立資料表的資料錄集 \(設計階段\) 時，您可選擇要在資料錄集中表示的資料表資料行。  但在編譯程式後，由您或資料來源的另一個使用者加入的資料行就不能這麼做。  資料庫類別無法直接支援 DDL，但您仍可在執行階段寫入程式碼，將新的資料行動態繫結至資料錄集。  如需如何執行此項繫結的詳細資訊，請參閱[資料錄集：動態地繫結資料行 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
 您可使用 DBMS 本身來變更結構描述，或可以讓您執行 DDL 函式的其他工具。  您也可使用 ODBC 函式呼叫來傳送 SQL 陳述式，例如呼叫一個不會傳回資料錄的預先定義查詢 \(預存的程序\)。  
  
##  <a name="_core_making_direct_sql_function_calls"></a> 執行直接的 SQL 函式呼叫  
 您可以使用 [CDatabase Class](../../mfc/reference/cdatabase-class.md) 物件，直接執行 SQL 呼叫。  請設定您的 SQL 陳述式字串 \(通常是在 `CString` 內\)，並將它傳遞至 `CDatabase` 物件的 [CDatabase::ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md) 成員函式。  若您使用 ODBC 函式呼叫來傳送一個通常會傳回資料錄的 SQL 陳述式，該資料錄會被忽略。  
  
## 請參閱  
 [SQL](../../data/odbc/sql.md)