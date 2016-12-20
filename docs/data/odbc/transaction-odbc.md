---
title: "異動 (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資料庫 [C++], 異動"
  - "ODBC [C++], 異動"
  - "ODBC 資料錄集 [C++], 異動"
  - "ODBC 資料錄集 [C++], 更新"
  - "資料錄集 [C++], 異動"
  - "資料錄集 [C++], 更新"
  - "異動 [C++], MFC ODBC 類別"
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 異動 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 交易是對[資料來源](../../data/odbc/data-source-odbc.md)以群組或批次一系列更新的方法，使得所有更新一次認可，或在您復原交易時不認可任何更新。  如果您不使用交易，資料來源的變動將會自動地認可，而非視需求來認可。  
  
> [!NOTE]
>  不是所有的 ODBC 資料庫驅動程式都支援交易。  您可呼叫 [CDatabase](../../mfc/reference/cdatabase-class.md) 或 [CRecordset](../../mfc/reference/crecordset-class.md) 物件的 `CanTransact` 成員函式，以決定驅動程式是否支援指定資料庫的交易。  請注意，`CanTransact` 並不會告訴您資料來源是否提供完整的交易支援。  您同時必須在 **CommitTrans** 和 **Rollback** 後呼叫 `CDatabase::GetCursorCommitBehavior` 和 `CDatabase::GetCursorRollbackBehavior` 以檢查所開啟的 `CRecordset` 物件之交易效果。  
  
 對於 `CRecordset` 物件的 `AddNew` 和 **Edit** 成員函式的呼叫將會在呼叫 **Update** 時立即影響資料來源。  **Delete** 呼叫也會立即生效。  反之，您可使用一筆包含多個呼叫 `AddNew`、**Edit**、**Update** 和 **Delete** 的交易，它雖會執行但卻不認可直到您明確地呼叫 **CommitTrans** 為止。  藉由建立交易，您可執行一系列這種呼叫卻仍能保留將其復原的能力。  若一個重要的資源已不適用或某些其他的情況造成整個交易不能完成，您可復原此交易而不用認可它。  在這種情況下，交易所做的所有變更將不會影響資料來源。  
  
> [!NOTE]
>  目前，如果您實作大量資料列擷取 \(Bulk Row Fetching\)，`CRecordset` 類別並不支援資料來源的更新。  這意謂您不能呼叫 `AddNew`、**Edit**、**Delete** 或 **Update**。  然而，您可撰寫您自己的函式來執行更新，並在給予的交易下呼叫這些函式。  如需關於大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
> [!NOTE]
>  除了影響您的資料錄集 \(Recordset\) 以外，只要您使用與 `CDatabase` 物件相關的 ODBC **HDBC**  或依據此 **HDBC** 的 ODBC **HSTMT**，交易就會影響您直接執行的 SQL 陳述式 \(Statement\)。  
  
 當您需要同時更新多重資料錄時，交易尤其有用。  在這種情況下，您想要避免交易只完成一半，例如若在完成最後更新之前擲回例外狀況 \(Exception\)，就可能會發生。  將這樣的更新群組成一筆交易將允許從變更中復原，並使得資料錄回到尚未交易的狀態。  例如，若一間銀行將錢由 A 帳戶轉帳到 B 帳戶，從 A 提錢和存錢至 B 都必須成功才能正確地處理存款，否則整筆交易必定會失敗。  
  
 在資料庫類別中，您是透過 `CDatabase` 物件來執行交易。  一個 `CDatabase` 物件代表對一個資料來源的連接，而一或多個和 `CDatabase` 物件相關的資料錄集是透過資料錄集成員函式在資料庫內的資料表上作業。  
  
> [!NOTE]
>  只支援一個層級的交易。  您不能使用巢狀交易，也無法將一筆交易擴展成多個資料庫物件。  
  
 下列主題提供如何執行交易的詳細資訊：  
  
-   [交易：在一個資料錄集內執行交易 \(ODBC\)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)  
  
-   [交易：交易如何影響更新 \(ODBC\)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)  
  
## 請參閱  
 [開放式資料庫連接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)