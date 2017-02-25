---
title: "TN042：ODBC 驅動程式開發人員建議 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.odbc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料庫 [C++], ODBC"
  - "ODBC 驅動程式 [C++], 撰寫"
  - "TN042"
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# TN042：ODBC 驅動程式開發人員建議
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個附註描述 ODBC 驅動程式寫入器的方針。  大綱功能 MFC ODBC 資料庫類別進行各種專案語意詳細資料的一般需求和做法。  支援三個 `CRecordset` 開啟模式所需的驅動程式功能 \(**forwardOnly**和 **snapshot** 和 **dynaset**\) 中所述。  
  
## ODBC 資料指標程式庫  
 MFC 資料庫類別目前功能分類給在許多情況下多大部分層級 1 ODBC 驅動程式提供的功能的使用者。  所幸， ODBC 資料指標程式庫將分層自己在資料庫類別和驅動程式之間和自動提供這個額外的功能。  
  
 例如，大部分 1.0 驅動程式不支援向後捲動。  資料指標程式庫在 FETCH\_PREV 呼叫 **SQLExtendedFetch**可能偵測到和快取從驅動程式的資料列並顯示它們按照需求。  
  
 資料指標程式庫相依性的另一個重要範例是定位更新。  大部分 1.0 驅動程式可能未將更新，不過，資料指標程式庫會產生識別資料來源的目標資料列會根據其目前快取的資料值的更新陳述式，或快取的時間戳記值。  
  
 類別庫從未使用多個資料列集。  因此，幾個 **SQLSetPos** 陳述式一律套用資料列 1 資料列集。  
  
## CDatabases  
 每個 `CDatabase` 指派唯一 **HDBC**。\(如果使用 `CDatabase``ExecuteSQL` 函式，暫時配置 **HSTMT** \)。因此，如果需要多 entity\_CODECDatabase 的，必須支援多個 **HDBC**的每個 **HENV** 。  
  
 資料庫類別要求資料指標程式庫。  這在 **SQLSetConnections** 呼叫 **SQL\_ODBC\_CURSORS**， **SQL\_CUR\_USE\_ODBC**反映。  
  
 `CDatabase::Open` 用來**SQLDriverConnectSQL\_DRIVER\_COMPLETE** ，建立與資料來源的連接。  
  
 驅動程式必須支援 **SQLGetInfo SQL\_ODBC\_API\_CONFORMANCE** \>\= **SQL\_OAC\_LEVEL1**， **SQLGetInfo SQL\_ODBC\_SQL\_CONFORMANCE** \>\= **SQL\_OSC\_MINIMUM**。  
  
 為 `CDatabase` 和其相依的資料錄集要支援的交易， **SQLGetInfo SQL\_CURSOR\_COMMIT\_BEHAVIOR** 和 **SQL\_CURSOR\_ROLLBACK\_BEHAVIOR** 都必須有 **SQL\_CR\_PRESERVE**。  否則，嘗試執行交易控制將被忽略。  
  
 必須支援**SQLGetInfoSQL\_DATA\_SOURCE\_READ\_ONLY** 。  如果它傳回「Y」，更新作業在資料來源不會執行。  
  
 如果 `CDatabase` 開啟的唯讀，嘗試設定唯讀資料來源以 **SQLSetConnectOption SQL\_ACCESS\_MODE**， **SQL\_MODE\_READ\_ONLY**會做出。  
  
 如果識別項需要使用引號，應該從具有 **SQLGetInfo SQL\_IDENTIFIER\_QUOTE\_CHAR** 呼叫的驅動程式傳回這項資訊。  
  
 進行偵錯， **SQLGetInfo SQL\_DBMS\_VER** 和 **SQL\_DBMS\_NAME** 從驅動程式擷取。  
  
 **SQLSetStmtOption SQL\_QUERY\_TIMEOUT** 和 **SQL\_ASYNC\_ENABLE** 可能呼叫 `CDatabase`**HDBC**。  
  
 **SQLError** 可能呼叫與任一或所有的引數為 null。  
  
 當然，必須支援 **SQLAllocEnv**和 **SQLAllocConnect**和 **SQLDisconnect** 和 **SQLFreeConnect** 。  
  
## ExecuteSQL  
 除了配置和釋放暫存 **HSTMT**之外， `ExecuteSQL` 呼叫 **SQLExecDirect**、、 **SQLNumResultCol** 和 **SQLFetch**`SQLMoreResults`。  **SQLCancel** 可能呼叫 **HSTMT**。  
  
## GetDatabaseName  
 **SQLGetInfo SQL\_DATABASE\_NAME** 會呼叫。  
  
## BeginTrans，以及，復原  
 如果交易產生要求，**SQLSetConnectOption SQL\_AUTOCOMMIT** 和 **SQLTransact SQL\_COMMIT**， **SQL\_ROLLBACK** 和 **SQL\_AUTOCOMMIT** 會呼叫。  
  
## CRecordsets  
 必須支援**SQLAllocStmt**， **SQLPrepare**， **SQLExecute** \( **Open** 和 **Requery**\)， **SQLExecDirect** \(為更新作業\)， **SQLFreeStmt** 。  **SQLNumResultCols** 和 **SQLDescribeCol** 會呼叫在不同時間設定的結果。  
  
 **SQLSetParam** 為繫結參數資料和 **DATA\_AT\_EXEC** 功能大量使用。  
  
 **SQLBindCol** 廣泛使用於登錄輸出行 ODBC 資料儲存體儲存位置。  
  
 兩個 **SQLGetData** 呼叫用來擷取 **SQL\_LONG\_VARCHAR** 和 **SQL\_LONG\_VARBINARY** 資料。  先嘗試藉由呼叫 **SQLGetData** 尋找資料行值的總長度與 cbMaxValue 0，不過，以有效的 pcbValue。  如果 pcbValue 保留 **SQL\_NO\_TOTAL**，就會擲回例外狀況。  否則， `HGLOBAL` 會配置和進行的另一個 **SQLGetData** 呼叫擷取整個結果。  
  
## Updating  
 如果封閉式鎖定要求， **SQLGetInfo SQL\_LOCK\_TYPES** 要查詢。  如果 **SQL\_LCK\_EXCLUSIVE** 不受支援，將擲回例外狀況。  
  
 嘗試更新 `CRecordset` \(**snapshot** 或 **dynaset**\) 會使一秒 **HSTMT** 配置。  對於不支援第二個 **HSTMT**的驅動程式，資料指標程式庫會模擬這項功能。  可惜的是，這有時可能表示強制在第一個 **HSTMT** 的目前查詢到完成處理第二個 **HSTMT** 要求。  
  
 在更新作業期間，**SQLFreeStmt SQL\_CLOSE** 和 **SQL\_RESET\_PARAMS** 和 **SQLGetCursorName** 會呼叫。  
  
 如果在 **outputColumns**的 **CLongBinarys** ， ODBC 的必須支援 **DATA\_AT\_EXEC** 功能。  這包括從傳回 **SQLExecDirect**和 **SQLParamData** 和 **SQLPutData**的 **SQL\_NEED\_DATA** 。  
  
 **SQLRowCount** 在執行驗證之後呼叫 **SQLExecDirect**只更新 1 筆資料錄。  
  
## 僅順向資料指標  
 只有 **SQLFetch** 對於 **Move** 作業所需的。  請注意 **forwardOnly** 游標不支援更新。  
  
## 快照游標  
 快照功能需要 **SQLExtendedFetch** 支援。  如先前所述， ODBC 資料指標程式庫會偵測驅動程式時不支援 **SQLExtendedFetch**，並提供必要的支援。  
  
 **SQLGetInfo**， **SQL\_SCROLL\_OPTIONS** 必須支援 **SQL\_SO\_STATIC**。  
  
## Dynaset 游標  
 下面所需的最小支援開啟動態集:  
  
 **SQLGetInfo**， **SQL\_ODBC\_VER** 必須傳回「 \> 01 "。  
  
 **SQLGetInfo**， **SQL\_SCROLL\_OPTIONS** 必須支援 **SQL\_SO\_KEYSET\_DRIVEN**。  
  
 **SQLGetInfo**， **SQL\_ROW\_UPDATES** 必須傳回「Y」。  
  
 **SQLGetInfo**， **SQL\_POSITIONED\_UPDATES** 必須支援 **SQL\_PS\_POSITIONED\_DELETE** 和 **SQL\_PS\_POSITIONED\_UPDATE**。  
  
 此外，如果，封閉式鎖定要求，對 **SQLSetPos** 的呼叫與 irow 1， fRefresh false 和群組 **SQL\_LCK\_EXCLUSIVE** 即將執行。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)