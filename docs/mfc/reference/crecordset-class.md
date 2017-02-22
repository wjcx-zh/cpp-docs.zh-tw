---
title: "CRecordset Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CRecordset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRecordset class"
  - "database records [C++]"
  - "ODBC 資料錄集 [C++], CRecordset 物件"
  - "sets of records [C++]"
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CRecordset Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示選取自資料來源的資料錄集。  
  
## 語法  
  
```  
class CRecordset : public CObject  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CRecordset::CRecordset](../Topic/CRecordset::CRecordset.md)|建構 `CRecordset` 物件。  您的衍生類別必須提供呼叫這個建構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CRecordset::AddNew](../Topic/CRecordset::AddNew.md)|將新資料錄的準備工作。  呼叫完成附加的 `Update` 。|  
|[CRecordset::CanAppend](../Topic/CRecordset::CanAppend.md)|如果新資料錄加入至資料錄集藉由 `AddNew` 成員函式，傳回非零。|  
|[CRecordset::CanBookmark](../Topic/CRecordset::CanBookmark.md)|如果資料錄集支援書籤，傳回非零。|  
|[CRecordset::Cancel](../Topic/CRecordset::Cancel.md)|取消非同步作業或處理序從第二個執行緒。|  
|[CRecordset::CancelUpdate](../Topic/CRecordset::CancelUpdate.md)|取消任何暫止的更新由於 `AddNew` 或 `Edit` 作業。|  
|[CRecordset::CanRestart](../Topic/CRecordset::CanRestart.md)|如果 `Requery` 可以再次呼叫，來執行資料錄集的查詢傳回非零。|  
|[CRecordset::CanScroll](../Topic/CRecordset::CanScroll.md)|如果只要記錄，則會傳回非零。|  
|[CRecordset::CanTransact](../Topic/CRecordset::CanTransact.md)|如果資料來源支援交易，則會傳回非零。|  
|[CRecordset::CanUpdate](../Topic/CRecordset::CanUpdate.md)|傳回非零，如果資料錄集的可更新 \(更新，您可以加入、更新或刪除資料錄\)。|  
|[CRecordset::CheckRowsetError](../Topic/CRecordset::CheckRowsetError.md)|呼叫處理記錄擷取時產生的錯誤。|  
|[CRecordset::Close](../Topic/CRecordset::Close.md)|關閉資料錄集和 ODBC **HSTMT** 相關聯。|  
|[CRecordset::Delete](../Topic/CRecordset::Delete.md)|刪除資料錄集目前的資料錄。  您必須明確地移動至其他資料錄處於刪除之後。|  
|[CRecordset::DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md)|呼叫交換大量資料列從資料來源至資料錄集。  實作大量資料錄欄位交換 \(Bulk RFX\)。|  
|[CRecordset::DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md)|呼叫以便交換資料 \(在兩個方向\) 在資料錄集的欄位資料成員和資料來源中的對應資料錄之間。  實作資料錄欄位交換 \(Record Field Exchange，RFX\)。|  
|[CRecordset::Edit](../Topic/CRecordset::Edit.md)|提供對目前的記錄變更的準備。  呼叫完成編輯 `Update` 。|  
|[CRecordset::FlushResultSet](../Topic/CRecordset::FlushResultSet.md)|傳回非零，如果有其他的結果會擷取，，當使用預先定義的查詢時。|  
|[CRecordset::GetBookmark](../Topic/CRecordset::GetBookmark.md)|指定資料錄的書籤值至參數物件。|  
|[CRecordset::GetDefaultConnect](../Topic/CRecordset::GetDefaultConnect.md)|呼叫以取得預設的連接字串。|  
|[CRecordset::GetDefaultSQL](../Topic/CRecordset::GetDefaultSQL.md)|呼叫以取得預設 SQL 字串執行。|  
|[CRecordset::GetFieldValue](../Topic/CRecordset::GetFieldValue.md)|傳回一個欄位的值與資料錄集。|  
|[CRecordset::GetODBCFieldCount](../Topic/CRecordset::GetODBCFieldCount.md)|傳回欄位數目的資料錄集。|  
|[CRecordset::GetODBCFieldInfo](../Topic/CRecordset::GetODBCFieldInfo.md)|傳回特定型別欄位相關的資訊資料錄集的。|  
|[CRecordset::GetRecordCount](../Topic/CRecordset::GetRecordCount.md)|傳回資料錄的資料錄集。|  
|[CRecordset::GetRowsetSize](../Topic/CRecordset::GetRowsetSize.md)|會傳回單一擷取期間，您想要擷取的資料錄數目。|  
|[CRecordset::GetRowsFetched](../Topic/CRecordset::GetRowsFetched.md)|傳回在擷取期間擷取實際資料列數目。|  
|[CRecordset::GetRowStatus](../Topic/CRecordset::GetRowStatus.md)|在擷取後傳回資料列的狀態。|  
|[CRecordset::GetSQL](../Topic/CRecordset::GetSQL.md)|取得 SQL 字串會用於中以資料錄集選取資料錄。|  
|[CRecordset::GetStatus](../Topic/CRecordset::GetStatus.md)|若要取得資料錄集的狀態:目前資料錄的索引，並記錄的最終計算是否已取得。|  
|[CRecordset::GetTableName](../Topic/CRecordset::GetTableName.md)|若要取得資料錄集的資料表名稱。|  
|[CRecordset::IsBOF](../Topic/CRecordset::IsBOF.md)|如果資料錄集的位置後，在第一個資料錄之前，傳回非零。  沒有目前資料錄。|  
|[CRecordset::IsDeleted](../Topic/CRecordset::IsDeleted.md)|如果資料錄集在已刪除的記錄，放置傳回非零。|  
|[CRecordset::IsEOF](../Topic/CRecordset::IsEOF.md)|如果資料錄集在最後一筆資料錄後，將其放置傳回非零。  沒有目前資料錄。|  
|[CRecordset::IsFieldDirty](../Topic/CRecordset::IsFieldDirty.md)|如果已變更，則會傳回非零的目前資料錄中指定的欄位。|  
|[CRecordset::IsFieldNull](../Topic/CRecordset::IsFieldNull.md)|傳回非零，如果目前的資料錄中指定的欄位是 null \(沒有值\)。|  
|[CRecordset::IsFieldNullable](../Topic/CRecordset::IsFieldNullable.md)|傳回非零，如果目前的資料錄中指定的欄位可設為 null \(沒有值\)。|  
|[CRecordset::IsOpen](../Topic/CRecordset::IsOpen.md)|如果 `Open` 之前，呼叫會傳回零。|  
|[CRecordset::Move](../Topic/CRecordset::Move.md)|將資料錄集至指定的資料錄數目 \(從目前資料錄的在任一方向。|  
|[CRecordset::MoveFirst](../Topic/CRecordset::MoveFirst.md)|在資料錄集中的第一筆資料錄上目前的資料錄。  首先 `IsBOF` 的測試。|  
|[CRecordset::MoveLast](../Topic/CRecordset::MoveLast.md)|將目前的資料錄在最後一筆資料錄或最後一個資料列集。  首先 `IsEOF` 的測試。|  
|[CRecordset::MoveNext](../Topic/CRecordset::MoveNext.md)|將目前的資料錄、下一筆資料錄或下一個資料列集。  首先 `IsEOF` 的測試。|  
|[CRecordset::MovePrev](../Topic/CRecordset::MovePrev.md)|將目前資料錄中前一個記錄或前一個資料列集。  首先 `IsBOF` 的測試。|  
|[CRecordset::OnSetOptions](../Topic/CRecordset::OnSetOptions.md)|呼叫設定選項 \(在選取範圍\) 的指定 ODBC 陳述式。|  
|[CRecordset::OnSetUpdateOptions](../Topic/CRecordset::OnSetUpdateOptions.md)|呼叫設定選項 \(用於更新\) 的指定 ODBC 陳述式。|  
|[CRecordset::Open](../Topic/CRecordset::Open.md)|藉由擷取資料表或執行資料錄集所代表的查詢來開啟資料錄集。|  
|[CRecordset::RefreshRowset](../Topic/CRecordset::RefreshRowset.md)|重新整理指定資料列的資料和狀態。|  
|[CRecordset::Requery](../Topic/CRecordset::Requery.md)|重新執行資料錄集的查詢重新整理選取的資料錄。|  
|[CRecordset::SetAbsolutePosition](../Topic/CRecordset::SetAbsolutePosition.md)|在這個資料錄的資料錄集和指定的資料錄號碼對應。|  
|[CRecordset::SetBookmark](../Topic/CRecordset::SetBookmark.md)|在書籤指定資料錄的資料錄集。|  
|[CRecordset::SetFieldDirty](../Topic/CRecordset::SetFieldDirty.md)|將目前的資料錄中指定的欄位標記為已變更。|  
|[CRecordset::SetFieldNull](../Topic/CRecordset::SetFieldNull.md)|設定指定之欄位的值目前資料錄的 Null \(沒有值\)。|  
|[CRecordset::SetLockingMode](../Topic/CRecordset::SetLockingMode.md)|設定鎖定模式「開放式」鎖定 \(預設\) 或「封閉式鎖定」。  判斷資料錄如何鎖定進行更新。|  
|[CRecordset::SetParamNull](../Topic/CRecordset::SetParamNull.md)|將指定的參數設定為 null \(沒有值\)。|  
|[CRecordset::SetRowsetCursorPosition](../Topic/CRecordset::SetRowsetCursorPosition.md)|在資料列集內指定的行上放置游標。|  
|[CRecordset::SetRowsetSize](../Topic/CRecordset::SetRowsetSize.md)|指定在擷取時，您想要擷取的資料錄數目。|  
|[CRecordset::Update](../Topic/CRecordset::Update.md)|藉由將新的或編輯之資料進行 `AddNew` 或 `Edit` 作業是在資料來源。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CRecordset::m\_hstmt](../Topic/CRecordset::m_hstmt.md)|包含資料錄集的 ODBC 陳述式控制代碼。  輸入 `HSTMT`。|  
|[CRecordset::m\_nFields](../Topic/CRecordset::m_nFields.md)|在資料錄集的欄位資料成員的數目。  輸入 `UINT`。|  
|[CRecordset::m\_nParams](../Topic/CRecordset::m_nParams.md)|在資料錄集包含參數資料成員的數目。  輸入 `UINT`。|  
|[CRecordset::m\_pDatabase](../Topic/CRecordset::m_pDatabase.md)|含有指向資料錄集連接至資料來源的 `CDatabase` 物件。|  
|[CRecordset::m\_strFilter](../Topic/CRecordset::m_strFilter.md)|包含指定一個結構化查詢語言 \(SQL\) `WHERE` 子句的 `CString` 。  用來篩選選取符合特定準則的記錄而言。|  
|[CRecordset::m\_strSort](../Topic/CRecordset::m_strSort.md)|包含指定 `ORDER BY` SQL 子句的 `CString` 。  用來控制資料錄的排序方式。|  
  
## 備註  
 稱為「資料錄集，」 `CRecordset` 物件通常用於兩種形式:動態集和快照集。  動態集保持同步與其他使用者所做的資料更新。  快照集是資料的靜態檢視。  每個表單都代表一個固定的一組資料錄，在開啟檔案時，資料錄集，但是，當您移動至動態集的資料錄時，它會反映其他資料錄集後續對資料錄，讓其他使用者或變更在應用程式中。  
  
> [!NOTE]
>  如果您使用存取資料時使用物件 \(DAO\) 類別而不是開放式資料庫連接 \(ODBC\) 類別會使用類別， [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 。  如需詳細資訊，請參閱本文 [概觀:資料庫程式開發](../../data/data-access-programming-mfc-atl.md)。  
  
 若要與其中一個使用類型資料錄集，可從 `CRecordset`通常衍生自特定應用程式的資料錄集類別。  資料錄集選取資料來源的資料錄，然後，您可以:  
  
-   捲動記錄。  
  
-   更新資料錄並指定一個鎖定模式。  
  
-   篩選資料錄從這些選取資料來源中可使用的資料錄集限制。  
  
-   排序資料錄集。  
  
-   參數化資料錄集自訂其資訊的選項並不知道在執行階段之前。  
  
 使用類別，開啟資料庫和建構資料錄集物件，透過建構函式指標至 `CDatabase` 物件。  然後呼叫資料錄集的 **開啟** 成員函式，您可以指定物件是否為動態集 \(Dynaset\) 或快照集 \(Snapshot\)。  呼叫 **開啟** 選取資料來源的資料。  在開啟後的資料錄集物件，請使用它的成員函式和資料成員可以捲動記錄和會在它們。  可用的作業是由物件為動態集 \(Dynaset\) 或快照集 \(Snapshot\)，它是否可更新或唯讀 \(這取決於開放式資料庫連接 \(Open Database Connectivity，ODBC\) 資料來源的\)，功能，以及您要實作大量資料列擷取。  重新整理可能已變更或加入的資料錄，因為 **開啟** 呼叫時，呼叫物件的 **Requery** 成員函式。  當您完成使用後，請呼叫物件的成員函式 **關閉** 並終結該物件。  
  
 在衍生的類別， `CRecordset` 資料錄欄位交換 \(RFX\) 或大量資料錄欄位交換 \(Bulk RFX\) 是用來支援讀取和更新資料錄欄位。  
  
 如需資料錄集和資料錄欄位交換的詳細資訊，請參閱 Microsoft 知識庫文件 [概觀:資料庫程式開發](../../data/data-access-programming-mfc-atl.md)、 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)、 [資料錄集:擷取大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和 [資料錄欄位交換 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)。  如需動態集和快照中的焦點，請參閱 Microsoft 知識庫文件 [Dynaset](../../data/odbc/dynaset.md) 和 [快照](../../data/odbc/snapshot.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CRecordset`  
  
## 需求  
 **Header:** afxdb.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CRecordView Class](../../mfc/reference/crecordview-class.md)