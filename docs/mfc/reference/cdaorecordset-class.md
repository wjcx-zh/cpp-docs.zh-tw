---
title: "CDaoRecordset Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDaoRecordset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDaoRecordset 類別"
  - "資料錄, CDaoRecordSet"
  - "資料錄集, types"
ms.assetid: 2322067f-1027-4662-a5d7-aa2fc7488630
caps.latest.revision: 26
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDaoRecordset Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示選取自資料來源的資料錄集。  
  
## 語法  
  
```  
  
class CDaoRecordset : public CObject  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CDaoRecordset::CDaoRecordset](../Topic/CDaoRecordset::CDaoRecordset.md)|建構 `CDaoRecordset` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CDaoRecordset::AddNew](../Topic/CDaoRecordset::AddNew.md)|將新資料錄的準備工作。  呼叫完成附加的 [更新](../Topic/CDaoRecordset::Update.md) 。|  
|[CDaoRecordset::CanAppend](../Topic/CDaoRecordset::CanAppend.md)|如果新資料錄加入至資料錄集藉由 [AddNew](../Topic/CDaoRecordset::AddNew.md) 成員函式，傳回非零。|  
|[CDaoRecordset::CanBookmark](../Topic/CDaoRecordset::CanBookmark.md)|如果資料錄集支援書籤，傳回非零。|  
|[CDaoRecordset::CancelUpdate](../Topic/CDaoRecordset::CancelUpdate.md)|取消任何暫止的更新由於 [編輯](../Topic/CDaoRecordset::Edit.md) 或 [AddNew](../Topic/CDaoRecordset::AddNew.md) 作業。|  
|[CDaoRecordset::CanRestart](../Topic/CDaoRecordset::CanRestart.md)|如果 [重新查詢](../Topic/CDaoRecordset::Requery.md) 可以再次呼叫，來執行資料錄集的查詢傳回非零。|  
|[CDaoRecordset::CanScroll](../Topic/CDaoRecordset::CanScroll.md)|如果只要記錄，則會傳回非零。|  
|[CDaoRecordset::CanTransact](../Topic/CDaoRecordset::CanTransact.md)|如果資料來源支援交易，則會傳回非零。|  
|[CDaoRecordset::CanUpdate](../Topic/CDaoRecordset::CanUpdate.md)|傳回非零，如果資料錄集的可更新 \(更新，您可以加入、更新或刪除資料錄\)。|  
|[CDaoRecordset::Close](../Topic/CDaoRecordset::Close.md)|關閉資料錄集。|  
|[CDaoRecordset::Delete](../Topic/CDaoRecordset::Delete.md)|刪除資料錄集目前的資料錄。  您必須明確地移動至其他資料錄處於刪除之後。|  
|[CDaoRecordset::DoFieldExchange](../Topic/CDaoRecordset::DoFieldExchange.md)|呼叫以便交換資料 \(在兩個方向\) 在資料錄集的欄位資料成員和資料來源中的對應資料錄之間。  實作 DAO 資料錄欄位交換 \(DFX\)。|  
|[CDaoRecordset::Edit](../Topic/CDaoRecordset::Edit.md)|提供對目前的記錄變更的準備。  呼叫完成編輯 **更新** 。|  
|[CDaoRecordset::FillCache](../Topic/CDaoRecordset::FillCache.md)|填滿任何或本機快取的組件包含從 ODBC 資料來源的資料錄集物件的。|  
|[CDaoRecordset::Find](../Topic/CDaoRecordset::Find.md)|找出特定字串的第一個，下，上一個或最後一個位置中符合指定準則的動態集類型的資料錄集並進行記錄中目前的資料錄。|  
|[CDaoRecordset::FindFirst](../Topic/CDaoRecordset::FindFirst.md)|偵測到第一個記錄檔中符合指定準則的動態型別或快照集類型資料錄集並進行記錄中目前的資料錄。|  
|[CDaoRecordset::FindLast](../Topic/CDaoRecordset::FindLast.md)|偵測到最後一個記錄檔中符合指定準則的動態型別或快照集類型資料錄集並進行記錄中目前的資料錄。|  
|[CDaoRecordset::FindNext](../Topic/CDaoRecordset::FindNext.md)|偵測到下一個記錄檔中符合指定準則的動態型別或快照集類型資料錄集並進行記錄中目前的資料錄。|  
|[CDaoRecordset::FindPrev](../Topic/CDaoRecordset::FindPrev.md)|偵測到先前的記錄中符合指定準則的動態型別或快照集類型資料錄集並進行記錄中目前的資料錄。|  
|[CDaoRecordset::GetAbsolutePosition](../Topic/CDaoRecordset::GetAbsolutePosition.md)|傳回資料錄集物件的目前資料錄的資料錄數目。|  
|[CDaoRecordset::GetBookmark](../Topic/CDaoRecordset::GetBookmark.md)|傳回表示資料錄的書籤的值。|  
|[CDaoRecordset::GetCacheSize](../Topic/CDaoRecordset::GetCacheSize.md)|傳回從 ODBC 資料來源是一個動態集類型的資料錄集的資料錄數目包含資料會在本機快取的值。|  
|[CDaoRecordset::GetCacheStart](../Topic/CDaoRecordset::GetCacheStart.md)|傳回資料錄集指定第一筆資料錄書籤要快取的值。|  
|[CDaoRecordset::GetCurrentIndex](../Topic/CDaoRecordset::GetCurrentIndex.md)|傳回包含索引的名稱 `CString` 最近使用索引，此資料表的型別 `CDaoRecordset`。|  
|[CDaoRecordset::GetDateCreated](../Topic/CDaoRecordset::GetDateCreated.md)|傳回基礎 `CDaoRecordset` 物件的基底資料表所建立的日期和時間。|  
|[CDaoRecordset::GetDateLastUpdated](../Topic/CDaoRecordset::GetDateLastUpdated.md)|傳回所做的最新變更的日期和時間轉換為基礎 `CDaoRecordset` 物件的基底資料表的設計。|  
|[CDaoRecordset::GetDefaultDBName](../Topic/CDaoRecordset::GetDefaultDBName.md)|傳回預設的資料來源名稱。|  
|[CDaoRecordset::GetDefaultSQL](../Topic/CDaoRecordset::GetDefaultSQL.md)|呼叫以取得預設 SQL 字串執行。|  
|[CDaoRecordset::GetEditMode](../Topic/CDaoRecordset::GetEditMode.md)|傳回表示狀態可編輯目前資料錄的值。|  
|[CDaoRecordset::GetFieldCount](../Topic/CDaoRecordset::GetFieldCount.md)|傳回表示欄位數目資料錄集的值。|  
|[CDaoRecordset::GetFieldInfo](../Topic/CDaoRecordset::GetFieldInfo.md)|傳回特定型別欄位相關的資訊資料錄集的。|  
|[CDaoRecordset::GetFieldValue](../Topic/CDaoRecordset::GetFieldValue.md)|傳回一個欄位的值與資料錄集。|  
|[CDaoRecordset::GetIndexCount](../Topic/CDaoRecordset::GetIndexCount.md)|在基礎資料錄集的資料表中擷取索引的數目。|  
|[CDaoRecordset::GetIndexInfo](../Topic/CDaoRecordset::GetIndexInfo.md)|傳回各種有關索引的詳細資訊。|  
|[CDaoRecordset::GetLastModifiedBookmark](../Topic/CDaoRecordset::GetLastModifiedBookmark.md)|用來判斷最近加入或更新的資料錄。|  
|[CDaoRecordset::GetLockingMode](../Topic/CDaoRecordset::GetLockingMode.md)|傳回在編譯期間，指出鎖定的型別實際上是。|  
|[CDaoRecordset::GetName](../Topic/CDaoRecordset::GetName.md)|傳回包含資料錄集的名稱 `CString` 。|  
|[CDaoRecordset::GetParamValue](../Topic/CDaoRecordset::GetParamValue.md)|擷取在基礎 DAOParameter 物件中指定之參數的目前值。|  
|[CDaoRecordset::GetPercentPosition](../Topic/CDaoRecordset::GetPercentPosition.md)|傳回目前資料錄的位置 \(以百分比表示資料錄總數。|  
|[CDaoRecordset::GetRecordCount](../Topic/CDaoRecordset::GetRecordCount.md)|傳回資料錄集物件存取資料錄數目。|  
|[CDaoRecordset::GetSQL](../Topic/CDaoRecordset::GetSQL.md)|取得 SQL 字串會用於中以資料錄集選取資料錄。|  
|[CDaoRecordset::GetType](../Topic/CDaoRecordset::GetType.md)|呼叫以決定資料錄集類型:資料表類型，動態集 \(Dynaset\) 或快照集的型別。|  
|[CDaoRecordset::GetValidationRule](../Topic/CDaoRecordset::GetValidationRule.md)|傳回包含驗證資料值的 `CString` ，會在欄位中輸入。|  
|[CDaoRecordset::GetValidationText](../Topic/CDaoRecordset::GetValidationText.md)|擷取顯示的文字，當驗證規則不滿意。|  
|[CDaoRecordset::IsBOF](../Topic/CDaoRecordset::IsBOF.md)|如果資料錄集的位置後，在第一個資料錄之前，傳回非零。  沒有目前資料錄。|  
|[CDaoRecordset::IsDeleted](../Topic/CDaoRecordset::IsDeleted.md)|如果資料錄集在已刪除的記錄，放置傳回非零。|  
|[CDaoRecordset::IsEOF](../Topic/CDaoRecordset::IsEOF.md)|如果資料錄集在最後一筆資料錄後，將其放置傳回非零。  沒有目前資料錄。|  
|[CDaoRecordset::IsFieldDirty](../Topic/CDaoRecordset::IsFieldDirty.md)|如果已變更，則會傳回非零的目前資料錄中指定的欄位。|  
|[CDaoRecordset::IsFieldNull](../Topic/CDaoRecordset::IsFieldNull.md)|傳回非零，如果目前的資料錄中指定的欄位是空的 \(沒有值\)。|  
|[CDaoRecordset::IsFieldNullable](../Topic/CDaoRecordset::IsFieldNullable.md)|傳回非零，如果目前的資料錄中指定的欄位可設為 null \(沒有值\)。|  
|[CDaoRecordset::IsOpen](../Topic/CDaoRecordset::IsOpen.md)|如果 [開啟](../Topic/CDaoRecordset::Open.md) 之前，呼叫會傳回零。|  
|[CDaoRecordset::Move](../Topic/CDaoRecordset::Move.md)|將資料錄集至指定的資料錄數目 \(從目前資料錄的在任一方向。|  
|[CDaoRecordset::MoveFirst](../Topic/CDaoRecordset::MoveFirst.md)|在資料錄集中的第一筆資料錄上目前的資料錄。|  
|[CDaoRecordset::MoveLast](../Topic/CDaoRecordset::MoveLast.md)|在資料錄集的最後一筆資料錄上目前的資料錄。|  
|[CDaoRecordset::MoveNext](../Topic/CDaoRecordset::MoveNext.md)|在資料錄集中的下一筆資料錄上目前的資料錄。|  
|[CDaoRecordset::MovePrev](../Topic/CDaoRecordset::MovePrev.md)|在資料錄集中的一項記錄中目前的資料錄。|  
|[CDaoRecordset::Open](../Topic/CDaoRecordset::Open.md)|建立資料表、動態集 \(Dynaset\) 或快照的新資料錄集。|  
|[CDaoRecordset::Requery](../Topic/CDaoRecordset::Requery.md)|重新執行資料錄集的查詢重新整理選取的資料錄。|  
|[CDaoRecordset::Seek](../Topic/CDaoRecordset::Seek.md)|偵測到記錄符合目前索引的指定準則的之索引的資料表\) 的資料錄集物件並進行記錄中目前的資料錄。|  
|[CDaoRecordset::SetAbsolutePosition](../Topic/CDaoRecordset::SetAbsolutePosition.md)|設定資料錄集物件的目前資料錄的資料錄數目。|  
|[CDaoRecordset::SetBookmark](../Topic/CDaoRecordset::SetBookmark.md)|其中包含指定的書籤資料錄上資料錄集。|  
|[CDaoRecordset::SetCacheSize](../Topic/CDaoRecordset::SetCacheSize.md)|設定從 ODBC 資料來源是一個動態集類型的資料錄集的資料錄數目包含資料會在本機快取的值。|  
|[CDaoRecordset::SetCacheStart](../Topic/CDaoRecordset::SetCacheStart.md)|設定資料錄集指定第一筆資料錄書籤要快取的值。|  
|[CDaoRecordset::SetCurrentIndex](../Topic/CDaoRecordset::SetCurrentIndex.md)|呼叫會使用一個資料表的資料錄集的索引。|  
|[CDaoRecordset::SetFieldDirty](../Topic/CDaoRecordset::SetFieldDirty.md)|將目前的資料錄中指定的欄位標記為已變更。|  
|[CDaoRecordset::SetFieldNull](../Topic/CDaoRecordset::SetFieldNull.md)|設定指定之欄位的值目前資料錄的 Null \(沒有值\)。|  
|[CDaoRecordset::SetFieldValue](../Topic/CDaoRecordset::SetFieldValue.md)|將欄位的值與資料錄集。|  
|[CDaoRecordset::SetFieldValueNull](../Topic/CDaoRecordset::SetFieldValueNull.md)|將欄位值的資料錄集的 NULL。  \(沒有值\)。|  
|[CDaoRecordset::SetLockingMode](../Topic/CDaoRecordset::SetLockingMode.md)|設定指出實作鎖定的型別在編譯期間的值。|  
|[CDaoRecordset::SetParamValue](../Topic/CDaoRecordset::SetParamValue.md)|設定基礎 DAOParameter 物件中指定之參數的目前值。|  
|[CDaoRecordset::SetParamValueNull](../Topic/CDaoRecordset::SetParamValueNull.md)|設定指定之參數的目前值 Null \(沒有值\)。|  
|[CDaoRecordset::SetPercentPosition](../Topic/CDaoRecordset::SetPercentPosition.md)|設定目前資料錄的位置加入內含百分比資料錄總數對應至資料錄集。|  
|[CDaoRecordset::Update](../Topic/CDaoRecordset::Update.md)|藉由將新的或編輯之資料進行 `AddNew` 或 **編輯** 作業是在資料來源。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CDaoRecordset::m\_bCheckCacheForDirtyFields](../Topic/CDaoRecordset::m_bCheckCacheForDirtyFields.md)|包含表示欄位是否有一個旗標會自動標記為已變更。|  
|[CDaoRecordset::m\_nFields](../Topic/CDaoRecordset::m_nFields.md)|在資料錄集類別包含欄位資料成員的數目和資料錄集選取的資料行數目從資料來源。|  
|[CDaoRecordset::m\_nParams](../Topic/CDaoRecordset::m_nParams.md)|在資料錄集類別—參數數目包含參數資料成員數目透過資料錄集的查詢|  
|[CDaoRecordset::m\_pDAORecordset](../Topic/CDaoRecordset::m_pDAORecordset.md)|對基礎資料錄集物件的 DAO 介面的指標。|  
|[CDaoRecordset::m\_pDatabase](../Topic/CDaoRecordset::m_pDatabase.md)|這個結果集的來源資料庫。  含有指向 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 物件。|  
|[CDaoRecordset::m\_strFilter](../Topic/CDaoRecordset::m_strFilter.md)|包含用來 **WHERE** 字串來建構 SQL 陳述式。|  
|[CDaoRecordset::m\_strSort](../Topic/CDaoRecordset::m_strSort.md)|包含用來 **ORDER BY** 字串來建構 SQL 陳述式。|  
  
## 備註  
 稱為「資料錄集，」 `CDaoRecordset` 物件可用以下列三種形式:  
  
-   資料表的資料錄集代表您可以使用單一資料庫資料表，檢查加入、變更，或刪除資料錄的基底資料表。  
  
-   Dynaset 類型資料錄集是可更新的資料錄查詢的結果。  這些資料錄集是可用來從基礎資料庫資料表或檢視，加入、變更，或刪除資料錄的資料錄集。  Dynaset 類型資料錄集可以在資料庫中包含一或多個資料表中的欄位。  
  
-   快照集類型資料錄集是一組的靜態 \(Static\) 複本可用來尋找資料或產生報表記錄。  這些資料錄集在資料庫包含一或多個資料表中的欄位，但無法更新。  
  
 在開啟檔案時，資料錄集每個表單都代表一個固定的一組資料錄的資料錄集。  當您移動至資料表的資料錄集還是動態集類型的資料錄集的資料錄時，它會反映對的變更和資料錄，在開啟資料錄集，而其他使用者或已在應用程式的其他資料錄集。  \(一個快照集類型資料錄集無法更新\)。您可以直接使用 `CDaoRecordset` 或從 `CDaoRecordset`取得特定應用程式的資料錄集類別。  您可以：  
  
-   捲動記錄。  
  
-   設定索引和快速尋找使用記錄中 [搜尋](../Topic/CDaoRecordset::Seek.md) \(僅限資料表的資料錄集\)。  
  
-   尋找資料錄根據字串比較:「\<」， \<\=」， 「\=」， \>\=」或「\>」\(動態集和快照集型別類型的資料錄集\)。  
  
-   更新資料錄並指定一個鎖定模式 \(除了快照集類型資料錄集\)。  
  
-   篩選資料錄從這些選取資料來源中可使用的資料錄集限制。  
  
-   排序資料錄集。  
  
-   參數化資料錄集自訂其資訊的選項並不知道在執行階段之前。  
  
 將 `CDaoRecordset` 提供類別介面類似於類別 `CRecordset`。  主要差異是類別 `CDaoRecordset` 存取資料的方式是將資料存取物件根據 OLE \(DAO\) 的。  透過開放式資料庫連接 \(Open Database Connectivity，ODBC\) 會將 `CRecordset` 存取類別來實作和這個 DBMS 的 ODBC 驅動程式。  
  
> [!NOTE]
>  DAO 資料庫類別會根據 Open 開放式資料庫連接的 MFC 資料庫類別本身不同 \(ODBC\)。  所有 DAO 資料庫類別名稱中有「CDao」前置詞。  您仍然可以存取使用 DAO 類別的 ODBC 資料來源，，因為它們是針對 Microsoft Jet 資料庫引擎， DAO 類別通常會提供絕佳的功能。  
  
 您可以直接使用 `CDaoRecordset` 或從 `CDaoRecordset`衍生類別。  不論是使用資料錄集類別，開啟資料庫和建構資料錄集物件，透過建構函式指標至 `CDaoDatabase` 物件。  您也可以 `CDaoRecordset` 建構物件並讓 MFC 建立暫存 `CDaoDatabase` 做為物件。  然後呼叫資料錄集的成員函式 [開啟](../Topic/CDaoRecordset::Open.md) ，指定物件是否為資料表的資料錄集、動態集類型的資料錄集或快照集類型資料錄集。  呼叫 **開啟** 選取資料從資料庫和擷取第一筆資料錄。  
  
 使用物件的成員函式和資料成員至捲動資料錄並在它們。  可用的作業是由物件是否屬於資料表的資料錄集、動態集類型的資料錄集或快照集類型資料錄集，，且是否可更新的或唯讀—這取決於資料庫或開放式資料庫連接 \(Open Database Connectivity，ODBC\) 資料來源的功能。  重新整理可能已變更或加入的資料錄，因為 **開啟** 呼叫時，呼叫物件的 [重新查詢](../Topic/CDaoRecordset::Requery.md) 成員函式。  當您完成使用後，請呼叫物件的成員函式 **關閉** 並終結該物件。  
  
 `CDaoRecordset` 使用 DAO 資料錄支援讀取和更新的欄位交換 \(DFX\) 記錄欄位會將您的 `CDaoRecordset` 或 `CDaoRecordset`衍生類別的型別安全 C\+\+ 成員。  使用 [GetFieldValue](../Topic/CDaoRecordset::GetFieldValue.md) 和 [SetFieldValue](../Topic/CDaoRecordset::SetFieldValue.md)，您也可以實作動態資料行繫結至資料庫中，而不需要使用 DFX 機制。  
  
 如需相關資訊，請參閱本主題中的\<資料錄集物件」DAO 說明。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoRecordset`  
  
## 需求  
 **Header:** afxdao.h  
  
## 請參閱  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoTableDef Class](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoWorkspace Class](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase Class](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoQueryDef Class](../../mfc/reference/cdaoquerydef-class.md)