---
title: "TN068：使用 Microsoft Access 7 ODBC 驅動程式執行異動 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.data.odbc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TN068"
  - "異動, 呼叫 BeginTrans"
  - "異動, Microsoft Access"
ms.assetid: d3f8f5d9-b118-4194-be36-a1aefb630c45
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# TN068：使用 Microsoft Access 7 ODBC 驅動程式執行異動
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個會描述如何執行交易，當使用 MFC ODBC 資料庫類別中，並在桌面 Microsoft ODBC 驅動程式中包括的 Microsoft Access 7.0 ODBC 驅動程式包裝版本 3.0。  
  
## 概觀  
 如果您的資料庫應用程式執行交易，您必須小心呼叫 `CDatabase::BeginTrans` 和 `CRecordset::Open` 以正確的順序在您的應用程式。  Microsoft Access 7.0 驅動程式使用 Microsoft Jet 資料庫引擎， Jet，並要求您的應用程式不會開始在有開啟游標的所有資料庫的取捨。  針對 MFC ODBC 資料庫類別，開放式資料指標與開啟的 `CRecordset` 物件。  
  
 如果您在呼叫 **BeginTrans**之前開啟資料錄集，可能不會記錄任何錯誤訊息。  不過，所有資料錄集更新您的應用程式執行變得永遠在呼叫 `CRecordset::Update`之後，更新，並不會透過呼叫 **Rollback**復原。  若要避免這個問題，您必須先呼叫 **BeginTrans** 然後開啟資料錄集。  
  
 MFC 檢查資料指標進行復原行為功能的驅動程式。  `CDatabase` 類別會開啟 `CRecordset` 物件提供兩個成員函式， `GetCursorCommitBehavior` 和 `GetCursorRollbackBehavior`，判斷所有交易的作用。  如果是 Microsoft Access 7.0 ODBC 驅動程式，，因為存取驅動程式不支援游標保存，這些成員函式會傳回 `SQL_CB_CLOSE` 。  因此，您必須呼叫遵循 **CommitTrans** 或 **Rollback** 作業的 `CRecordset::Requery` 。  
  
 當您需要將由上至下依序執行多重商務處理，您無法在第一種交易之後呼叫 **Requery** 然後開始下一個。  您必須關閉資料錄集，下一個呼叫 **BeginTrans** 為了滿足 Jet 的要求。  這個技術提示描述處理這種情況兩個方法:  
  
-   關閉在每個 **CommitTrans** 或 **Rollback** 作業後的資料錄集。  
  
-   使用 ODBC API 函式 **SQLFreeStmt**。  
  
## 關閉在每個 CommitTrans 或 Rollback 作業後的資料錄集  
 在交易開始之前，請確定資料錄集物件已經關閉。  在呼叫 **BeginTrans**後，請呼叫資料錄集的 **Open** 成員函式。  結束對呼叫 **CommitTrans** 或 **Rollback**之後的資料錄集。  請注意重複開啟和關閉資料錄集可能會使得應用程式的效能。  
  
## 使用 SQLFreeStmt  
 您也可以使用 ODBC API 函式 **SQLFreeStmt** 在完成交易之後明確關閉游標。  若要啟動另一個交易，請呼叫 **BeginTrans** 後面接著 `CRecordset::Requery`。  當呼叫 **SQLFreeStmt**時，您必須指定資料錄集的 HSTMT 做為第一個參數和 **SQL\_CLOSE** 當做第二個參數。  這個方法會關閉並開啟快速資料錄集在每種交易的開始。  下列程式碼示範如何實作這個技術:  
  
```  
CMyDatabase db;  
db.Open( "MYDATASOURCE" );  
CMyRecordset rs( &db );  
  
// start transaction 1 and   
// open the recordset  
db.BeginTrans( );  
rs.Open( );  
  
// manipulate data  
  
// end transaction 1  
db.CommitTrans( );  // or Rollback( )  
  
// close the cursor  
::SQLFreeStmt( rs.m_hstmt, SQL_CLOSE );  
  
// start transaction 2  
db.BeginTrans( );  
  
// now get the result set  
rs.Requery( );  
  
// manipulate data  
  
// end transaction 2  
db.CommitTrans( );  
  
rs.Close( );  
db.Close( );  
```  
  
 另一種實作這個方法會將新的函式， **RequeryWithBeginTrans**，您可以呼叫開始下一個交易，在認可或復原第一個之後。  若要將這類函式，請執行下列步驟:  
  
1.  複製 **CRecordset::Requery\( \)** 的程式碼對新的函式。  
  
2.  將在呼叫之後的下一行到 **SQLFreeStmt**:  
  
     `m_pDatabase->BeginTrans( );`  
  
 現在您可以針對每個對這個函式的交易之間:  
  
```  
// start transaction 1 and   
// open the recordset  
db.BeginTrans( );  
rs.Open( );  
  
// manipulate data  
  
// end transaction 1  
db.CommitTrans( );  // or Rollback( )  
  
// close the cursor, start new transaction,  
// and get the result set  
rs.RequeryWithBeginTrans( );  
  
// manipulate data  
  
// end transaction 2  
db.CommitTrans( );  // or Rollback( )  
```  
  
> [!NOTE]
>  如果您需要變更交易，之間資料錄集成員變數 **m\_strFilter**`m_strSort` 或不要使用這個技術。  在這種情況下，您應該在每個 **CommitTrans** 和 **Rollback** 作業之後關閉資料錄集。  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)