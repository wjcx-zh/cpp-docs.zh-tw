---
title: "CRecordset 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRecordset
- AFXDB/CRecordset
- AFXDB/CRecordset::CRecordset
- AFXDB/CRecordset::AddNew
- AFXDB/CRecordset::CanAppend
- AFXDB/CRecordset::CanBookmark
- AFXDB/CRecordset::Cancel
- AFXDB/CRecordset::CancelUpdate
- AFXDB/CRecordset::CanRestart
- AFXDB/CRecordset::CanScroll
- AFXDB/CRecordset::CanTransact
- AFXDB/CRecordset::CanUpdate
- AFXDB/CRecordset::CheckRowsetError
- AFXDB/CRecordset::Close
- AFXDB/CRecordset::Delete
- AFXDB/CRecordset::DoBulkFieldExchange
- AFXDB/CRecordset::DoFieldExchange
- AFXDB/CRecordset::Edit
- AFXDB/CRecordset::FlushResultSet
- AFXDB/CRecordset::GetBookmark
- AFXDB/CRecordset::GetDefaultConnect
- AFXDB/CRecordset::GetDefaultSQL
- AFXDB/CRecordset::GetFieldValue
- AFXDB/CRecordset::GetODBCFieldCount
- AFXDB/CRecordset::GetODBCFieldInfo
- AFXDB/CRecordset::GetRecordCount
- AFXDB/CRecordset::GetRowsetSize
- AFXDB/CRecordset::GetRowsFetched
- AFXDB/CRecordset::GetRowStatus
- AFXDB/CRecordset::GetSQL
- AFXDB/CRecordset::GetStatus
- AFXDB/CRecordset::GetTableName
- AFXDB/CRecordset::IsBOF
- AFXDB/CRecordset::IsDeleted
- AFXDB/CRecordset::IsEOF
- AFXDB/CRecordset::IsFieldDirty
- AFXDB/CRecordset::IsFieldNull
- AFXDB/CRecordset::IsFieldNullable
- AFXDB/CRecordset::IsOpen
- AFXDB/CRecordset::Move
- AFXDB/CRecordset::MoveFirst
- AFXDB/CRecordset::MoveLast
- AFXDB/CRecordset::MoveNext
- AFXDB/CRecordset::MovePrev
- AFXDB/CRecordset::OnSetOptions
- AFXDB/CRecordset::OnSetUpdateOptions
- AFXDB/CRecordset::Open
- AFXDB/CRecordset::RefreshRowset
- AFXDB/CRecordset::Requery
- AFXDB/CRecordset::SetAbsolutePosition
- AFXDB/CRecordset::SetBookmark
- AFXDB/CRecordset::SetFieldDirty
- AFXDB/CRecordset::SetFieldNull
- AFXDB/CRecordset::SetLockingMode
- AFXDB/CRecordset::SetParamNull
- AFXDB/CRecordset::SetRowsetCursorPosition
- AFXDB/CRecordset::SetRowsetSize
- AFXDB/CRecordset::Update
- AFXDB/CRecordset::m_hstmt
- AFXDB/CRecordset::m_nFields
- AFXDB/CRecordset::m_nParams
- AFXDB/CRecordset::m_pDatabase
- AFXDB/CRecordset::m_strFilter
- AFXDB/CRecordset::m_strSort
dev_langs:
- C++
helpviewer_keywords:
- database records [C++]
- CRecordset class
- ODBC recordsets [C++], CRecordset objects
- sets of records [C++]
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: f7a05a5eefd6f55a68c6e9f1726dfb7c29f399f2
ms.lasthandoff: 02/24/2017

---
# <a name="crecordset-class"></a>CRecordset 類別
表示選取自資料來源的資料錄集。  
  
## <a name="syntax"></a>語法  
  
```  
class CRecordset : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CRecordset::CRecordset](#crecordset)|建構 `CRecordset` 物件。 您的衍生的類別必須提供呼叫這個建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CRecordset::AddNew](#addnew)|準備要加入新記錄。 呼叫`Update`完成加入。|  
|[CRecordset::CanAppend](#canappend)|傳回非零值，如果可以加入新的記錄，透過在資料錄集`AddNew`成員函式。|  
|[CRecordset::CanBookmark](#canbookmark)|傳回非零，如果資料錄集支援書籤。|  
|[CRecordset::Cancel](#cancel)|取消非同步作業或從第二個執行緒的處理序。|  
|[CRecordset::CancelUpdate](#cancelupdate)|取消任何暫止的更新，因為`AddNew`或`Edit`作業。|  
|[CRecordset::CanRestart](#canrestart)|傳回非零值如果`Requery`可以呼叫一次執行資料錄集的查詢。|  
|[CRecordset::CanScroll](#canscroll)|傳回非零，如果您可以捲動資料錄。|  
|[CRecordset::CanTransact](#cantransact)|傳回非零，如果資料來源支援交易。|  
|[CRecordset::CanUpdate](#canupdate)|傳回非零值，如果可以更新資料錄集 （您可以新增、 更新或刪除記錄）。|  
|[CRecordset::CheckRowsetError](#checkrowseterror)|呼叫以處理期間擷取的記錄產生的錯誤。|  
|[CRecordset::Close](#close)|關閉資料錄集和 ODBC **HSTMT**與其相關聯。|  
|[CRecordset::Delete](#delete)|刪除資料錄集目前的記錄。 在刪除之後，您必須明確地捲動至另一筆記錄。|  
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|呼叫以交換大量資料列的資料來源的資料錄集。 實作大量資料錄欄位交換 (Bulk RFX)。|  
|[CRecordset::DoFieldExchange](#dofieldexchange)|呼叫之間交換資料 （在兩個方向） 的資料錄集的欄位資料成員和資料來源上對應的記錄。 實作資料錄欄位交換 (RFX)。|  
|[CRecordset::Edit](#edit)|準備變更為目前的記錄。 呼叫`Update`來完成編輯。|  
|[CRecordset::FlushResultSet](#flushresultset)|擷取，使用預先定義的查詢時將傳回非零，如果沒有其他結果。|  
|[CRecordset::GetBookmark](#getbookmark)|將記錄的書籤值指派給參數物件。|  
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|呼叫以取得預設的連接字串。|  
|[CRecordset::GetDefaultSQL](#getdefaultsql)|呼叫以取得要執行的預設 SQL 字串。|  
|[CRecordset::GetFieldValue](#getfieldvalue)|傳回資料錄集中的欄位的值。|  
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|傳回資料錄集中的欄位數目。|  
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|傳回資料錄集中的特定類型的欄位資訊。|  
|[CRecordset::GetRecordCount](#getrecordcount)|傳回資料錄集中的記錄數目。|  
|[CRecordset::GetRowsetSize](#getrowsetsize)|傳回您想要在單一擷取期間所擷取的記錄數目。|  
|[CRecordset::GetRowsFetched](#getrowsfetched)|傳回一次擷取中擷取資料列的實際數目。|  
|[CRecordset::GetRowStatus](#getrowstatus)|在提取之後傳回資料列的狀態。|  
|[CRecordset::GetSQL](#getsql)|取得用來選取資料錄集的記錄的 SQL 字串。|  
|[CRecordset::GetStatus](#getstatus)|取得資料錄集的狀態︰ 目前的記錄，以及是否已經取得最後計數記錄的索引。|  
|[CRecordset::GetTableName](#gettablename)|取得資料錄集所依據的資料表名稱。|  
|[CRecordset::IsBOF](#isbof)|傳回非零，如果第一個資料錄之前已置於資料錄集。 沒有目前資料錄。|  
|[CRecordset::IsDeleted](#isdeleted)|傳回非零，如果資料錄集位於已刪除的記錄。|  
|[CRecordset::IsEOF](#iseof)|傳回非零，如果已位置之後的最後一個記錄的資料錄集。 沒有目前資料錄。|  
|[CRecordset::IsFieldDirty](#isfielddirty)|傳回非零，如果目前的記錄中指定的欄位已變更。|  
|[CRecordset::IsFieldNull](#isfieldnull)|傳回非零值，如果目前的記錄中指定的欄位為 null （沒有任何值）。|  
|[CRecordset::IsFieldNullable](#isfieldnullable)|傳回非零，如果目前的記錄中指定的欄位可以設定為 null （具有任何值）。|  
|[CRecordset::IsOpen](#isopen)|傳回非零值如果`Open`先前已經呼叫。|  
|[CRecordset::Move](#move)|任一方向的目前資料錄來定位資料錄集為指定的記錄數。|  
|[CRecordset::MoveFirst](#movefirst)|置於資料錄集的第一個記錄目前的記錄。 測試`IsBOF`第一次。|  
|[CRecordset::MoveLast](#movelast)|將目前的記錄，或最後一個資料列集上最後一筆記錄。 測試`IsEOF`第一次。|  
|[CRecordset::MoveNext](#movenext)|將目前的記錄放在下一筆記錄或下一個資料列集上。 測試`IsEOF`第一次。|  
|[CRecordset::MovePrev](#moveprev)|將目前的記錄放在上一筆記錄或前一個資料列集上。 測試`IsBOF`第一次。|  
|[CRecordset::OnSetOptions](#onsetoptions)|針對指定的 ODBC 陳述式來呼叫設定選項 （選取項目上使用）。|  
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|呼叫以針對指定的 ODBC 陳述式來設定 （用於更新） 的選項。|  
|[Crecordset:: Open](#open)|開啟資料錄集擷取資料表或查詢資料錄集表示。|  
|[CRecordset::RefreshRowset](#refreshrowset)|重新整理的資料和狀態的指定資料列。|  
|[CRecordset::Requery](#requery)|執行一次重新整理選取的資料錄的資料錄集的查詢。|  
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|資料錄集置於對應至指定的記錄數目的記錄。|  
|[CRecordset::SetBookmark](#setbookmark)|資料錄集置於書籤所指定的記錄。|  
|[CRecordset::SetFieldDirty](#setfielddirty)|將目前記錄中指定的欄位標記為已變更。|  
|[CRecordset::SetFieldNull](#setfieldnull)|設定指定之欄位的值為 null （具有任何值） 是目前記錄中。|  
|[CRecordset::SetLockingMode](#setlockingmode)|將鎖定模式設定為 「 開放式 」 鎖定 （預設值） 或 「 封閉式 」 鎖定。 決定如何更新鎖定的記錄。|  
|[CRecordset::SetParamNull](#setparamnull)|將指定的參數設定為 null （具有任何值）。|  
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|將游標放在指定的資料列集中的資料列。|  
|[CRecordset::SetRowsetSize](#setrowsetsize)|指定您想要一次擷取中擷取的記錄數目。|  
|[CRecordset::Update](#update)|完成`AddNew`或`Edit`新增或編輯資料儲存在資料來源上的作業。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CRecordset::m_hstmt](#m_hstmt)|包含資料錄集的 ODBC 陳述式控制代碼。 輸入 `HSTMT`。|  
|[CRecordset::m_nFields](#m_nfields)|包含在資料錄集欄位資料成員的數目。 輸入 `UINT`。|  
|[CRecordset::m_nParams](#m_nparams)|包含參數資料成員的資料錄集的數目。 輸入 `UINT`。|  
|[CRecordset::m_pDatabase](#m_pdatabase)|包含一個指向`CDatabase`透過此資料錄集連接到資料來源的物件。|  
|[CRecordset::m_strFilter](#m_strfilter)|包含`CString`，指定結構化查詢語言 (SQL)`WHERE`子句。 做為篩選條件來選取只在符合特定準則的記錄。|  
|[CRecordset::m_strSort](#m_strsort)|包含`CString`，指定 SQL`ORDER BY`子句。 用來控制記錄的排序方式。|  
  
## <a name="remarks"></a>備註  
 稱為 「 資料錄集 」`CRecordset`物件通常用於兩種形式︰ 動態集和快照集。 與其他使用者所做的資料更新，動態集保持同步。 快照集是靜態的資料檢視。 每個表單代表一組固定在開啟資料錄集時的時間的記錄，但捲動動態集內的記錄，其會反映之後所做的變更記錄，其他使用者或應用程式中的其他資料錄集。  
  
> [!NOTE]
>  如果您正在使用的資料存取物件 (DAO) 類別，而不是開放式資料庫連接 (ODBC) 類別，使用類別[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)改。 如需詳細資訊，請參閱文章[概觀︰ 資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。  
  
 若要使用資料錄集的其中一種，您通常衍生應用程式特定資料錄集類別從`CRecordset`。 資料錄集選取資料來源的記錄，然後您可以︰  
  
-   捲動資料錄。  
  
-   更新的記錄，並指定鎖定模式。  
  
-   篩選資料錄集，以限制它會從選取的可用資料來源的記錄。  
  
-   排序資料錄集。  
  
-   參數化的資料錄集的執行階段之前無法得知資訊來自訂其選項。  
  
 若要使用您的類別，開啟資料庫，並建構資料錄集物件，傳遞建構函式的指標，您`CDatabase`物件。 然後呼叫資料錄集的**開啟**成員函式，其中指定的物件是否動態集或快照集。 呼叫**開啟**選取資料來源中的資料。 開啟資料錄集物件之後，請捲動資料錄和操作上使用其成員函式和資料成員。 可用的作業取決於物件是動態集或快照集，它是可更新或唯讀模式 （這取決於開放式資料庫連接 (ODBC) 資料來源的功能），以及您是否有實作大量資料列擷取。 若要重新整理記錄可能會變更或自**開啟**呼叫，呼叫物件的**Requery**成員函式。 呼叫物件的**關閉**成員函式，並在您完成時終結物件。  
  
 在衍生`CRecordset`類別中，資料錄欄位交換 (RFX) 或大量資料錄欄位交換 (Bulk RFX) 用來支援讀取和更新的記錄欄位。  
  
 如需詳細資料錄集和資料錄欄位交換的詳細資訊，請參閱文章[概觀︰ 資料庫程式設計](../../data/data-access-programming-mfc-atl.md)，[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)，[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)，和[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。 著重於動態集和快照集，請參閱文章[動態](../../data/odbc/dynaset.md)和[快照](../../data/odbc/snapshot.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CRecordset`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  
  
##  <a name="addnew"></a>CRecordset::AddNew  
 準備新的記錄加入至資料表。  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>備註  
 您必須呼叫[Requery](#requery)成員函式，以查看新加入的記錄。 記錄的欄位是一開始是 Null。 (在資料庫術語中，為 Null 」 有任何值 」 的方式，不與相同**NULL** c + + 中。)若要完成此作業，您必須呼叫[更新](#update)成員函式。 **更新**將變更儲存至資料來源。  
  
> [!NOTE]
>  如果您已實作大量資料列擷取，您不能呼叫`AddNew`。 這會導致失敗的判斷提示。 雖然類別`CRecordset`不會提供一種機制來更新資料的大量資料列，您可以撰寫自己的函式使用 ODBC API 函式**SQLSetPos**。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 `AddNew`準備新的空白記錄使用資料錄集的欄位資料成員。 在您呼叫後`AddNew`，在資料錄集的欄位資料成員中設定您想要的值。 (您不需要呼叫[編輯](#edit)成員函式，針對此目的，請改用**編輯**僅為現有記錄。)當您後續呼叫**更新**、 已變更的欄位資料成員中的值會儲存在資料來源上。  
  
> [!CAUTION]
>  如果您捲動到新的記錄才能呼叫**更新**、 新的記錄會遺失，而且會提供任何警告。  
  
 如果資料來源支援交易，您可以讓您`AddNew`呼叫交易的一部分。 如需有關交易的詳細資訊，請參閱類別[CDatabase](../../mfc/reference/cdatabase-class.md)。 請注意，您應該呼叫[CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans)之前，先呼叫`AddNew`。  
  
> [!NOTE]
>  動態集，新的記錄會新增至資料錄集，為最後一筆記錄。 加入的記錄不會加入至快照集;您必須呼叫**Requery**重新整理資料錄集。  
  
 您不能呼叫`AddNew`資料錄集的**開啟**尚未呼叫成員函式。 A`CDBException`會擲回，如果您呼叫`AddNew`以無法附加至資料錄集。 您可以判斷資料錄集是否可以更新，藉由呼叫[CanAppend](#canappend)。  
  
 如需詳細資訊，請參閱下列文章︰[資料錄集︰ 資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)，[資料錄集︰ 加入、 更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)，和[交易 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
### <a name="example"></a>範例  
 請參閱文章[交易︰ 資料錄集 (ODBC) 中執行交易](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
##  <a name="canappend"></a>CRecordset::CanAppend  
 決定是否先前開啟的資料錄集可讓您新增新的記錄。  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果資料錄集允許加入新資料錄。否則為 0。 `CanAppend`如果您開啟為唯讀資料錄集時，就會傳回 0。  
  
##  <a name="canbookmark"></a>CRecordset::CanBookmark  
 決定是否資料錄集可讓您將使用書籤的記錄。  
  
```  
BOOL CanBookmark() const;  
```  
  
### <a name="return-value"></a>傳回值  
 資料錄集支援書籤 」; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 此函式是獨立的**CRecordset::useBookmarks**選項`dwOptions`參數[開啟](#open)成員函式。 `CanBookmark`指出指定的 ODBC 驅動程式和資料指標類型支援書籤。 **CRecordset::useBookmarks**指出書籤會可用，提供支援。  
  
> [!NOTE]
>  順向的資料錄集不支援書籤。  
  
 如需書籤和資料錄集巡覽的詳細資訊，請參閱文章[資料錄集︰ 書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[資料錄集︰ 捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
##  <a name="cancel"></a>CRecordset::Cancel  
 資料來源取消非同步作業進行中的或從第二個執行緒的處理序的要求。  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>備註  
 請注意，MFC ODBC 類別不會再使用非同步處理。若要執行的非同步作業，您必須直接呼叫 ODBC API 函式**SQLSetConnectOption**。 如需詳細資訊，請參閱 「 非同步執行函式 」 主題中*ODBC SDK 程式設計人員指南*。  
  
##  <a name="cancelupdate"></a>CRecordset::CancelUpdate  
 取消任何暫止的更新，因[編輯](#edit)或[AddNew](#addnew)作業之前[更新](#update)呼叫。  
  
```  
void CancelUpdate();
```  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  此成員函式不適用於使用大量資料列擷取，因為無法呼叫這類資料錄集的資料錄集**編輯**， `AddNew`，或**更新**。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 如果已啟用自動變更欄位的檢查，`CancelUpdate`會還原至之前的值的成員變數**編輯**或`AddNew`呼叫; 否則值的任何變更將會維持。 根據預設，自動欄位啟用檢查資料錄集開啟時。 若要停用，您必須指定**CRecordset::noDirtyFieldCheck**中`dwOptions`參數[開啟](#open)成員函式。  
  
 如需更新資料的詳細資訊，請參閱文章[資料錄集︰ 加入、 更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。  
  
##  <a name="canrestart"></a>CRecordset::CanRestart  
 決定資料錄集是否允許重新啟動其查詢 （若要更新其記錄），藉由呼叫**Requery**成員函式。  
  
```  
BOOL CanRestart() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果允許重新查詢;否則為 0。  
  
##  <a name="canscroll"></a>CRecordset::CanScroll  
 決定是否允許捲動資料錄集。  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>傳回值  
 資料錄集可讓捲動; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如需捲動的詳細資訊，請參閱文章[資料錄集︰ 捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
##  <a name="cantransact"></a>CRecordset::CanTransact  
 決定資料錄集是否允許交易。  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>傳回值  
 資料錄集可以讓交易; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱文章[交易 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="canupdate"></a>CRecordset::CanUpdate  
 決定是否可以更新資料錄集。  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果可以更新資料錄集。否則為 0。  
  
### <a name="remarks"></a>備註  
 資料錄集可能是唯讀屬性，如果基礎資料來源是唯讀，或您指定**CRecordset::readOnly**中`dwOptions`開啟資料錄集時的參數。  
  
##  <a name="checkrowseterror"></a>CRecordset::CheckRowsetError  
 呼叫以處理期間擷取的記錄產生的錯誤。  
  
```  
virtual void CheckRowsetError(RETCODE nRetCode);
```  
  
### <a name="parameters"></a>參數  
 `nRetCode`  
 ODBC API 函式傳回碼。 如需詳細資料，請參閱＜備註＞。  
  
### <a name="remarks"></a>備註  
 此虛擬成員函式會處理錯誤發生時擷取的記錄，並在大量資料列擷取期間非常有用。 您可能要考慮覆寫`CheckRowsetError`實作錯誤處理。  
  
 `CheckRowsetError`會自動呼叫在資料指標巡覽作業，例如**開啟**， **Requery**，或任何**移動**作業。 它會傳遞 ODBC API 函式的傳回值**SQLExtendedFetch**。 下表列出可能的值為`nRetCode`參數。  
  
|nRetCode|說明|  
|--------------|-----------------|  
|**SQL_SUCCESS**|函式完成可順利啟動。使用任何其他資訊不。|  
|**SQL_SUCCESS_WITH_INFO**|順利完成，可能發生非嚴重錯誤的函式。 可取得其他資訊，請呼叫**SQLError**。|  
|**SQL_NO_DATA_FOUND**|已經提取從結果集中的所有資料列。|  
|**SQL_ERROR**|函式失敗。 可取得其他資訊，請呼叫**SQLError**。|  
|**SQL_INVALID_HANDLE**|函式失敗，因為無效的環境控制代碼、 連接控制代碼或陳述式控制代碼。 這會指出程式設計錯誤。 沒有其他資訊可從**SQLError**。|  
|`SQL_STILL_EXECUTING`|以非同步方式啟動的函式仍在執行中。 請注意，根據預設，MFC 將永遠不會將此值傳遞至`CheckRowsetError`;MFC 將會繼續呼叫**SQLExtendedFetch**之前不會再傳回`SQL_STILL_EXECUTING`。|  
  
 如需詳細資訊**SQLError**，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="close"></a>CRecordset::Close  
 關閉資料錄集。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 ODBC **HSTMT**及所有配置給資料錄集架構會解除配置的記憶體。 通常在呼叫**關閉**，如果它已配置，會刪除 c + + 資料錄集物件**新**。  
  
 您可以呼叫**開啟**，然後再次呼叫**關閉**。 這可讓您重複使用資料錄集物件。 替代方法是呼叫**Requery**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase #&17;](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]  
  
##  <a name="crecordset"></a>CRecordset::CRecordset  
 建構 `CRecordset` 物件。  
  
```  
CRecordset(CDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pDatabase`  
 包含一個指向`CDatabase`物件或值**NULL**。 如果不是**NULL**和`CDatabase`物件的**開啟**尚未呼叫成員函式將它連接到資料來源、 資料錄集嘗試為您開啟在它自己**開啟**呼叫。 如果您傳遞**NULL**、`CDatabase`建構及連接，以您要使用您指定當您衍生您的資料錄集類別與類別的資料來源資訊的物件。  
  
### <a name="remarks"></a>備註  
 您可以使用`CRecordset`直接衍生從應用程式特定類別或`CRecordset`。 您可以使用類別來衍生資料錄集類別。  
  
> [!NOTE]
>  在衍生的類別*必須*提供它自己的建構函式。 在衍生類別的建構函式，呼叫建構函式`CRecordset::CRecordset`，沿著適當的參數傳遞給它。  
  
 傳遞**NULL**到您的資料錄集建構函式有`CDatabase`物件建構，並為您自動連接。 這是不需要您建構，以及連線的有用縮寫`CDatabase`之前建構資料錄集物件。  
  
### <a name="example"></a>範例  
 如需詳細資訊，請參閱文章[資料錄集︰ 宣告資料表 (ODBC) 為](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。  
  
##  <a name="delete"></a>CRecordset::Delete  
 刪除現有的記錄。  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>備註  
 之後成功刪除資料錄集的欄位資料成員設為 Null 值，而且您必須明確呼叫其中一個**移動**函式，以便將之移除刪除的記錄。 一旦您將之移除刪除的記錄，它不使用它。 如果資料來源支援交易，您可以將**刪除**呼叫交易的一部分。 如需詳細資訊，請參閱文章[交易 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
> [!NOTE]
>  如果您已實作大量資料列擷取，您不能呼叫**刪除**。 這會導致失敗的判斷提示。 雖然類別`CRecordset`不會提供一種機制來更新資料的大量資料列，您可以撰寫自己的函式使用 ODBC API 函式**SQLSetPos**。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
> [!CAUTION]
>  資料錄集必須是可更新，且必須有有效的記錄資料錄集中目前當您呼叫**刪除**，否則會發生錯誤。 例如，如果您刪除記錄，但不是會捲動到新的記錄才能呼叫**刪除**，**刪除**會擲回[CDBException](../../mfc/reference/cdbexception-class.md)。  
  
 不同於[AddNew](#addnew)和[編輯](#edit)，呼叫**刪除**後面不是呼叫[更新](#update)。 如果**刪除**呼叫失敗，欄位資料成員則會保留不變。  
  
### <a name="example"></a>範例  
 這個範例示範建立函式的框架上的資料錄集。 此範例假設存在`m_dbCust`，型別的成員變數`CDatabase`已經連接到資料來源。  
  
 [!code-cpp[NVC_MFCDatabase #&18;](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]  
  
##  <a name="dobulkfieldexchange"></a>CRecordset::DoBulkFieldExchange  
 呼叫以交換大量資料列的資料來源的資料錄集。 實作大量資料錄欄位交換 (Bulk RFX)。  
  
```  
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 指標[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件。 架構會已經設定這個物件指定欄位的交換作業的內容。  
  
### <a name="remarks"></a>備註  
 當實作大量資料列擷取時，架構會呼叫此成員函式，將會自動從資料來源的資料傳送至資料錄集物件。 `DoBulkFieldExchange`也會繫結參數資料成員，如果有的話，資料錄集的選取範圍的 SQL 陳述式字串中的參數替代符號。  
  
 如果未實作大量資料列擷取，架構會呼叫[DoFieldExchange](#dofieldexchange)。 若要實作大量資料列擷取，您必須指定`CRecordset::useMultiRowFetch`選項`dwOptions`中的參數[開啟](#open)成員函式。  
  
> [!NOTE]
> `DoBulkFieldExchange`使用衍生自的類別時，才可以使用`CRecordset`。 如果您已經建立資料錄集物件，直接從`CRecordset`，您必須呼叫[GetFieldValue](#getfieldvalue)成員函式來擷取資料。  
  
 大量資料錄欄位交換 (Bulk RFX) 很相似資料錄欄位交換 (RFX)。 資料來源的資料錄集物件會自動傳輸資料。 不過，您無法呼叫`AddNew`，**編輯**，**刪除**，或**更新**變更傳送回資料來源。 類別`CRecordset`目前不提供機制，以更新大量資料列的資料; 不過，您可以撰寫自己的函式使用 ODBC API 函式**SQLSetPos**。  
  
 請注意，類別不支援大量資料錄欄位交換;因此，您必須覆寫`DoBulkFieldExchange`以手動方式是藉由撰寫 Bulk RFX 函式的呼叫。 如需有關這些函式的詳細資訊，請參閱[資料錄欄位交換函式](../../mfc/reference/record-field-exchange-functions.md)。  
  
 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 如需相關資訊，請參閱文章[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。  
  
##  <a name="dofieldexchange"></a>CRecordset::DoFieldExchange  
 呼叫之間交換資料 （在兩個方向） 的資料錄集的欄位資料成員和資料來源上對應的記錄。 實作資料錄欄位交換 (RFX)。  
  
```  
virtual void DoFieldExchange(CFieldExchange* pFX);
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 指標[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件。 架構會已經設定這個物件指定欄位的交換作業的內容。  
  
### <a name="remarks"></a>備註  
 未實作大量資料列擷取，架構會呼叫此成員函式自動之間交換資料的資料錄集物件的欄位資料成員和對應的資料行的資料來源上目前的記錄。 `DoFieldExchange`也會繫結參數資料成員，如果有的話，資料錄集的選取範圍的 SQL 陳述式字串中的參數替代符號。  
  
 如果實作大量資料列擷取時，架構會呼叫[DoBulkFieldExchange](#dobulkfieldexchange)。 若要實作大量資料列擷取，您必須指定`CRecordset::useMultiRowFetch`選項`dwOptions`中的參數[開啟](#open)成員函式。  
  
> [!NOTE]
> `DoFieldExchange`使用衍生自的類別時，才可以使用`CRecordset`。 如果您已經建立資料錄集物件，直接從`CRecordset`，您必須呼叫[GetFieldValue](#getfieldvalue)成員函式來擷取資料。  
  
 交換欄位資料，呼叫資料錄欄位交換 (RFX)，可以雙向運作︰ 從資料來源上的記錄欄位的資料錄集物件的欄位資料成員和資料來源的資料錄集物件上的記錄。  
  
 唯一的動作，您通常必須採取實作`DoFieldExchange`對於衍生資料錄集類別是使用類別建立類別，並指定欄位資料成員的名稱和資料型別。 您也可以加入程式碼什麼 ClassWizard 寫入至指定的參數資料成員，或處理動態繫結的任何資料行。 如需詳細資訊，請參閱文章[資料錄集︰ 動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
 當您宣告類別衍生的資料錄集類別時，精靈會撰寫的覆寫`DoFieldExchange`，它會類似下列範例︰  
  
 [!code-cpp[NVC_MFCDatabase #&19;](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]  
  
 如需 RFX 函式的詳細資訊，請參閱主題[資料錄欄位交換函式](../../mfc/reference/record-field-exchange-functions.md)。  
  
 如需進一步的範例和詳細`DoFieldExchange`，請參閱文章[資料錄欄位交換︰ RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。 如需 RFX 的一般資訊，請參閱文章[資料錄欄位交換](../../data/odbc/record-field-exchange-rfx.md)。  
  
##  <a name="edit"></a>CRecordset::Edit  
 允許的最新記錄的變更。  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>備註  
 在您呼叫後**編輯**，您可以變更的欄位資料成員直接重設其值。 在作業完成時，接著再呼叫[更新](#update)將變更儲存在資料來源上的成員函式。  
  
> [!NOTE]
>  如果您已實作大量資料列擷取，您不能呼叫**編輯**。 這會導致失敗的判斷提示。 雖然類別`CRecordset`不會提供一種機制來更新資料的大量資料列，您可以撰寫自己的函式使用 ODBC API 函式**SQLSetPos**。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 **編輯**儲存資料錄集的資料成員的值。 如果您呼叫**編輯**，進行變更，然後呼叫**編輯**同樣地，記錄的值會還原至原先的前面**編輯**呼叫。  
  
 在某些情況下，您可能想要更新資料行，所以 Null （包含任何資料）。 若要這樣做，請呼叫[SetFieldNull](#setfieldnull)參數與**TRUE**標示的欄位為 Null; 這也會造成要更新的資料行。 如果您想要寫入至資料來源，即使沒有變更其值，請呼叫的欄位[SetFieldDirty](#setfielddirty)參數與**TRUE**。 就算欄位具有 Null 值。  
  
 如果資料來源支援交易，您可以將**編輯**呼叫交易的一部分。 請注意，您應該呼叫[CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans)之前，先呼叫**編輯**並開啟資料錄集之後。 也請注意，呼叫[CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)不呼叫取代**更新**完成**編輯**作業。 如需有關交易的詳細資訊，請參閱類別[CDatabase](../../mfc/reference/cdatabase-class.md)。  
  
 根據目前的鎖定模式，要更新資料錄可能被鎖住**編輯**直到您呼叫**更新**或捲動到另一筆記錄，則可能只在被鎖定或**編輯**呼叫。 您可以變更的鎖定模式[SetLockingMode](#setlockingmode)。  
  
 如果您捲動到新的記錄，然後再呼叫，便會還原先前的值，目前記錄的**更新**。 A`CDBException`如果您呼叫會擲回**編輯**無法更新資料錄集，或如果沒有目前資料錄。  
  
 如需詳細資訊，請參閱文章[交易 (ODBC)](../../data/odbc/transaction-odbc.md)和[資料錄集︰ 鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase #&20;](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]  
  
##  <a name="flushresultset"></a>CRecordset::FlushResultSet  
 如果有多個結果集，擷取下一個結果集的預先定義的查詢 （預存程序）。  
  
```  
BOOL FlushResultSet();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果有多個結果集擷取。否則為 0。  
  
### <a name="remarks"></a>備註  
 您應該呼叫`FlushResultSet`只有您何時完成目前的結果集資料指標。 請注意，當您擷取下一個結果集呼叫`FlushResultSet`，游標不正確的結果集上，您應該呼叫[MoveNext](#movenext)成員函式呼叫之後`FlushResultSet`。  
  
 如果預先定義的查詢會使用輸出參數或輸入/輸出參數，您必須呼叫`FlushResultSet`直到傳回`FALSE`（值 0），以取得這些參數值。  
  
 `FlushResultSet`呼叫 ODBC API 函式`SQLMoreResults`。 如果`SQLMoreResults`傳回`SQL_ERROR`或`SQL_INVALID_HANDLE`，然後`FlushResultSet`將會擲回例外狀況。 如需詳細資訊`SQLMoreResults`，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 您的預存程序必須有繫結欄位，如果您想要呼叫`FlushResultSet`。  
  
### <a name="example"></a>範例  
 下列程式碼會假設`COutParamRecordset`是`CRecordset`-根據預先定義查詢的輸入的參數和一個 output 參數，並讓多個結果集的衍生的物件。 請注意結構[DoFieldExchange](#dofieldexchange)覆寫。  
  
 [!code-cpp[NVC_MFCDatabase #&21;](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]  
  
 [!code-cpp[NVC_MFCDatabase #&22;](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]  
  
##  <a name="getbookmark"></a>CRecordset::GetBookmark  
 取得目前資料錄的書籤值。  
  
```  
void GetBookmark(CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>參數  
 `varBookmark`  
 參考[CDBVariant](../../mfc/reference/cdbvariant-class.md)物件，表示目前資料錄的書籤。  
  
### <a name="remarks"></a>備註  
 若要判斷是否支援將書籤資料錄集，請呼叫[CanBookmark](#canbookmark)。 若要使用並支援書籤，您必須設定**CRecordset::useBookmarks**選項`dwOptions`參數[開啟](#open)成員函式。  
  
> [!NOTE]
>  如果書籤不支援或無法使用，則呼叫`GetBookmark`會導致擲回例外狀況。 順向的資料錄集不支援書籤。  
  
 `GetBookmark`將目前記錄的書籤的值指派`CDBVariant`物件。 若要移動到不同的記錄之後，隨時回到該記錄，請呼叫[SetBookmark](#setbookmark)對應`CDBVariant`物件。  
  
> [!NOTE]
>  特定資料錄集作業之後，書籤可能不再有效。 例如，如果您呼叫`GetBookmark`後面**Requery**，您可能無法傳回的記錄`SetBookmark`。 呼叫[CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)來檢查您是否能安全地呼叫`SetBookmark`。  
  
 如需書籤和資料錄集巡覽的詳細資訊，請參閱文章[資料錄集︰ 書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[資料錄集︰ 捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
##  <a name="getdefaultconnect"></a>CRecordset::GetDefaultConnect  
 呼叫以取得預設的連接字串。  
  
```  
virtual CString GetDefaultConnect();
```  
  
### <a name="return-value"></a>傳回值  
 A `CString` ，其中包含預設的連接字串。  
  
### <a name="remarks"></a>備註  
 架構會呼叫此成員函式資料錄集所依據的資料來源取得預設的連接字串。 類別精靈為您實作此函式，藉由識別相同的資料來源用於 ClassWizard 來取得資料表和資料行的相關資訊。 您可能會發現它容易依賴此開發您的應用程式時的預設連線。 但是，預設的連線可能不適合您的應用程式的使用者。 如果是這樣，您應該實作此函式，並捨棄 ClassWizard 的版本。 如需連接字串的詳細資訊，請參閱文章[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)。  
  
##  <a name="getdefaultsql"></a>CRecordset::GetDefaultSQL  
 呼叫以取得要執行的預設 SQL 字串。  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>傳回值  
 A `CString` ，其中包含預設的 SQL 陳述式。  
  
### <a name="remarks"></a>備註  
 架構會呼叫此成員函式，以取得資料錄集所依據的預設 SQL 陳述式。 這可能是資料表名稱或 SQL**選取**陳述式。  
  
 間接定義預設的 SQL 陳述式藉由宣告類別精靈，您的資料錄集類別和類別精靈會為您執行這項工作。  
  
 如果您需要的 SQL 陳述式字串供自己使用時，呼叫`GetSQL`，它會傳回 SQL 陳述式，用來開啟網頁時，請選取資料錄集的記錄。 您可以編輯的類別的覆寫中的預設 SQL 字串`GetDefaultSQL`。 例如，您可以指定預先定義的查詢，使用呼叫**呼叫**陳述式。 (請注意，不過，如果您編輯`GetDefaultSQL`，您還需要修改`m_nFields`以符合資料來源中的資料行數目。)  
  
 如需詳細資訊，請參閱文章[資料錄集︰ 宣告資料表 (ODBC) 為](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。  
  
> [!CAUTION]
>  資料表名稱會是空架構無法識別的資料表名稱，如果提供多個資料表名稱，或如果**呼叫**無法解譯陳述式。 請注意，當使用**呼叫**陳述式中，您必須插入的大括號之間的空白字元和**呼叫**關鍵字，也應該插入之前的大括號前後的空白字元不**選取**關鍵字**選取**陳述式。  
  
##  <a name="getfieldvalue"></a>CRecordset::GetFieldValue  
 擷取目前的記錄中的欄位資料。  
  
```  
void GetFieldValue(
    LPCTSTR lpszName,  
    CDBVariant& varValue,  
    short nFieldType = DEFAULT_FIELD_TYPE);

 
void GetFieldValue(
    short nIndex,  
    CDBVariant& varValue,  
    short nFieldType = DEFAULT_FIELD_TYPE);

 
void GetFieldValue(
    short nIndex,  
    CStringA& strValue);

 
void GetFieldValue(
    short nIndex,  
    CStringW& strValue);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 欄位的名稱。  
  
 *varValu*e  
 參考[CDBVariant](../../mfc/reference/cdbvariant-class.md)欄位的值將儲存的物件。  
  
 `nFieldType`  
 ODBC C 資料類型的欄位。 使用預設值， **DEFAULT_FIELD_TYPE**，強制`GetFieldValue`決定 C 資料型別，從 SQL 資料類型，根據下表。 否則，您可以指定將資料直接輸入，或選擇相容的資料類型。比方說，您可以儲存任何資料型別讀入**SQL_C_CHAR**。  
  
|C 資料類型|SQL 資料型別|  
|-----------------|-------------------|  
|**SQL_C_BIT**|**SQL_BIT**|  
|**SQL_C_UTINYINT**|**SQL_TINYINT**|  
|**SQL_C_SSHORT**|**SQL_SMALLINT**|  
|**SQL_C_SLONG**|**SQL_INTEGER**|  
|**SQL_C_FLOAT**|**SQL_REAL**|  
|**SQL_C_DOUBLE**|**SQL_FLOATSQL_DOUBLE**|  
|**SQL_C_TIMESTAMP**|**SQL_DATESQL_TIMESQL_TIMESTAMP**|  
|**SQL_C_CHAR**|**SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR**|  
|**SQL_C_BINARY**|**SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY**|  
  
 如需 ODBC 資料類型的詳細資訊，請參閱主題 < SQL 資料類型 > 和 < C 資料類型 > 中的附錄 D [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `nIndex`  
 欄位的以零為起始的索引。  
  
 `strValue`  
 參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)欄位的值將儲存的物件轉換成文字，不論欄位的資料類型。  
  
### <a name="remarks"></a>備註  
 您可以查詢的欄位名稱或索引。 您可以將欄位值儲存在`CDBVariant`物件或`CString`物件。  
  
 如果您已實作大量資料列擷取，目前的記錄一律位於資料列集的第一個記錄。 若要使用`GetFieldValue`上指定的資料列集內的記錄，您必須先呼叫[SetRowsetCursorPosition](#setrowsetcursorposition)成員函式，將游標移到所需的資料列，該資料列集內。 然後呼叫`GetFieldValue`該資料列。 若要實作大量資料列擷取，您必須指定`CRecordset::useMultiRowFetch`選項`dwOptions`中的參數[開啟](#open)成員函式。  
  
 您可以使用`GetFieldValue`動態擷取欄位在執行的階段，而不是靜態設計階段的繫結。 例如，如果您是直接從資料錄集物件宣告`CRecordset`，您必須使用`GetFieldValue`擷取欄位資料; 資料錄欄位交換 (RFX) 或大量資料錄欄位交換 (Bulk RFX) 未實作。  
  
> [!NOTE]
>  如果您宣告資料錄集物件，而不需從衍生`CRecordset`，不需要載入 ODBC 資料指標程式庫。 資料指標程式庫，必須具備資料錄集至少一個繫結的資料行。不過，當您使用`CRecordset`直接，沒有資料行已繫結。 成員函式[CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex)和[CDatabase::Open](../../mfc/reference/cdatabase-class.md#open)控制是否會載入資料指標程式庫。  
  
 `GetFieldValue`呼叫 ODBC API 函式**SQLGetData**。 如果您的驅動程式會輸出值**SQL_NO_TOTAL**的欄位值的實際長度`GetFieldValue`擲回例外狀況。 如需詳細資訊**SQLGetData**，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列範例程式碼說明如何呼叫`GetFieldValue`資料錄集物件宣告直接從`CRecordset`。  
  
 [!code-cpp[NVC_MFCDatabase #&23;](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]  
  
> [!NOTE]
>  不同於 DAO 類別`CDaoRecordset`，`CRecordset`沒有`SetFieldValue`成員函式。 如果您建立的物件，直接從`CRecordset`，它是有效唯讀狀態。  
  
 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="getodbcfieldcount"></a>CRecordset::GetODBCFieldCount  
 擷取資料錄集物件中的欄位的總數。  
  
```  
short GetODBCFieldCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 資料錄集中的欄位數目。  
  
### <a name="remarks"></a>備註  
 如需建立資料錄集的詳細資訊，請參閱文章[資料錄集︰ 建立和關閉資料錄集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。  
  
##  <a name="getodbcfieldinfo"></a>CRecordset::GetODBCFieldInfo  
 取得資料錄集欄位的相關資訊。  
  
```  
void GetODBCFieldInfo(
    LPCTSTR lpszName,  
    CODBCFieldInfo& fieldinfo);

 
void GetODBCFieldInfo(
    short nIndex,  
    CODBCFieldInfo& fieldinfo);
```  
  
### <a name="parameters"></a>參數  
 `lpszName`  
 欄位的名稱。  
  
 `fieldinfo`  
 參考`CODBCFieldInfo`結構。  
  
 `nIndex`  
 欄位的以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 一個版本的函式可讓您依名稱查閱欄位。 另一個版本可讓您查詢索引欄位。  
  
 傳回的資訊的相關說明，請參閱[CODBCFieldInfo](../../mfc/reference/codbcfieldinfo-structure.md)結構。  
  
 如需建立資料錄集的詳細資訊，請參閱文章[資料錄集︰ 建立和關閉資料錄集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。  
  
##  <a name="getrecordcount"></a>CRecordset::GetRecordCount  
 判斷資料錄集的大小。  
  
```  
long GetRecordCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 資料錄集; 中的記錄數目0，表示資料錄集不包含任何記錄。或如果無法判別記錄計數-1。  
  
### <a name="remarks"></a>備註  
  
> [!CAUTION]
>  記錄計數維持為 「 高水位，「 最高編號的記錄，但當使用者在記錄之間移動。 之後使用者已超越最後一筆記錄，只有已知記錄總數。 基於效能考量，計數時不會更新您呼叫`MoveLast`。 若要自行計算記錄，請呼叫`MoveNext`重複直到`IsEOF`傳回非零值。 新增記錄，以透過**CRecordset:AddNew**和**更新**增加計數; 刪除透過記錄`CRecordset::Delete`減少計數。  
  
##  <a name="getrowsetsize"></a>CRecordset::GetRowsetSize  
 取得目前的設定，您想要指定提取時擷取的資料列數目。  
  
```  
DWORD GetRowsetSize() const;  
```  
  
### <a name="return-value"></a>傳回值  
 若要指定提取時擷取的資料列數目。  
  
### <a name="remarks"></a>備註  
 如果您使用大量資料列擷取，資料錄集開啟時的預設資料列集大小是 25。否則，它是 1。  
  
 若要實作大量資料列擷取，您必須指定`CRecordset::useMultiRowFetch`選項`dwOptions`參數[開啟](#open)成員函式。 若要變更資料列集大小設定，請呼叫[SetRowsetSize](#setrowsetsize)。  
  
 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="getrowsfetched"></a>CRecordset::GetRowsFetched  
 決定在提取之後實際擷取記錄數目。  
  
```  
DWORD GetRowsFetched() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指定提取之後，從資料來源擷取的資料列數目。  
  
### <a name="remarks"></a>備註  
 當您已實作大量資料列擷取時，這非常有用。 資料列集大小，通常表示多少資料列將取自 fetch;不過，在資料錄集的資料列總數也會影響資料列數目將會擷取資料列集中。 例如，如果您的資料錄集資料列集大小設定為 4 的 10 筆記錄，然後循環使用資料錄集藉由呼叫`MoveNext`會導致最後一個資料列集，並具有 2 的記錄。  
  
 若要實作大量資料列擷取，您必須指定`CRecordset::useMultiRowFetch`選項`dwOptions`參數[開啟](#open)成員函式。 若要指定資料列集大小，請呼叫[SetRowsetSize](#setrowsetsize)。  
  
 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase #&24;](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]  
  
##  <a name="getrowstatus"></a>CRecordset::GetRowStatus  
 取得目前資料列集中的資料列的狀態。  
  
```  
WORD GetRowStatus(WORD wRow) const;  
```  
  
### <a name="parameters"></a>參數  
 `wRow`  
 以一為位置的資料列中目前資料列集。 這個值可以介於 1 的資料列集大小。  
  
### <a name="return-value"></a>傳回值  
 資料列的狀態值。 如需詳細資料，請參閱＜備註＞。  
  
### <a name="remarks"></a>備註  
 `GetRowStatus`傳回值，指出其中一個資料列的狀態中的任何變更，自上次擷取從資料來源，或沒有資料列對應至`wRow`提取。 下表列出可能的傳回值。  
  
|狀態值|描述|  
|------------------|-----------------|  
|`SQL_ROW_SUCCESS`|資料列不會變更。|  
|`SQL_ROW_UPDATED`|已更新資料列。|  
|`SQL_ROW_DELETED`|已刪除資料列。|  
|`SQL_ROW_ADDED`|已加入資料列。|  
|`SQL_ROW_ERROR`|資料列已因錯誤而無法擷取。|  
|`SQL_ROW_NOROW`|沒有資料列對應至`wRow`。|  
  
 如需詳細資訊，請參閱 ODBC API 函式**SQLExtendedFetch**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getstatus"></a>CRecordset::GetStatus  
 判斷目前記錄中的資料錄集，和最後一筆記錄是否已看過的索引。  
  
```  
void GetStatus(CRecordsetStatus& rStatus) const;  
```  
  
### <a name="parameters"></a>參數  
 `rStatus`  
 參考**CRecordsetStatus**物件。 如需詳細資訊，請參閱＜備註＞一節。  
  
### <a name="remarks"></a>備註  
 `CRecordset`嘗試追蹤索引，但在某些情況下就可能無法進行。 請參閱[GetRecordCount](#getrecordcount)說明。  
  
 **CRecordsetStatus**結構具有下列格式︰  
  
 `struct CRecordsetStatus`  
  
 `{`  
  
 `long m_lCurrentRecord;`  
  
 `BOOL m_bRecordCountFinal;`  
  
 `};`  
  
 兩個成員**CRecordsetStatus**具有下列意義︰  
  
- **m_lCurrentRecord**如果已知包含目前資料錄集，以零起始的索引。 如果無法判斷索引，這個成員會包含**AFX_CURRENT_RECORD_UNDEFINED** – (2)。 如果`IsBOF`是**TRUE** （空的資料錄集或嘗試捲動第一筆之前），然後**m_lCurrentRecord**設為**AFX_CURRENT_RECORD_BOF** (–&1;)。 如果在第一筆記錄，則它會設定為 0，第二個記錄 1，並以此類推。  
  
- **m_bRecordCountFinal** Nonzero 如果判斷出資料錄集中的記錄總數。 通常這必須透過資料錄集的開頭開始，然後呼叫`MoveNext`直到`IsEOF`傳回非零值。 這個成員是零，如果記錄計算所傳回的`GetRecordCount`，如果不 –&1;，只有 「 高水位 」 的記錄個數。  
  
##  <a name="getsql"></a>CRecordset::GetSQL  
 呼叫此成員函式，以取得用來開啟網頁時，請選取資料錄集的資料錄的 SQL 陳述式。  
  
```  
const CString& GetSQL() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A **const**參考`CString`，其中包含 SQL 陳述式。  
  
### <a name="remarks"></a>備註  
 這通常是 SQL**選取**陳述式。 所傳回的字串`GetSQL`是唯讀的。  
  
 所傳回的字串`GetSQL`通常不同於您可能會傳送到資料錄集的任何字串`lpszSQL`參數**開啟**成員函式。 這是因為資料錄集建構完整的 SQL 陳述式，根據您傳遞至**開啟**，您指定的類別，可能會指定在**m_strFilter**和`m_strSort`資料成員，而您已指定任何參數。 如詳細資料錄集如何建構 SQL 陳述式，請參閱文章[資料錄集︰ 如何資料錄集選取資料錄 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。  
  
> [!NOTE]
>  只有在呼叫之後呼叫此成員函式[開啟](#open)。  
  
##  <a name="gettablename"></a>CRecordset::GetTableName  
 取得資料錄集的查詢為基礎的 SQL 資料表名稱。  
  
```  
const CString& GetTableName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A **const**參考`CString`包含資料表的名稱，如果資料錄集是根據資料表; 否則為空字串。  
  
### <a name="remarks"></a>備註  
 `GetTableName`才有效，如果資料錄集根據預先定義的查詢 （預存程序） 的多個資料表的聯結資料表。 名稱為唯讀。  
  
> [!NOTE]
>  只有在呼叫之後呼叫此成員函式[開啟](#open)。  
  
##  <a name="isbof"></a>CRecordset::IsBOF  
 傳回非零，如果第一個資料錄之前已置於資料錄集。 沒有目前資料錄。  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果資料錄集不包含任何記錄，或是第一筆記錄中前, 向後捲動到非零值否則為 0。  
  
### <a name="remarks"></a>備註  
 您從資料錄捲動記錄，以了解是否有發生第一筆資料錄集之前先呼叫此成員函式。 您也可以使用`IsBOF`連同`IsEOF`來判斷資料錄集是否包含任何記錄，或為空白。 之後立即呼叫**開啟**，如果資料錄集不包含任何記錄，`IsBOF`傳回非零值。當您開啟已至少一筆記錄的資料錄集時，第一筆記錄是目前的記錄和`IsBOF`傳回 0。  
  
 如果第一筆記錄是目前的記錄，而且您呼叫`MovePrev`，`IsBOF`後續將會傳回非零值。 如果`IsBOF`傳回非零，而且您呼叫`MovePrev`，則會發生錯誤。 如果`IsBOF`傳回非零，目前的記錄會是未定義，以及任何需要目前記錄的動作將會產生錯誤。  
  
### <a name="example"></a>範例  
 這個範例會使用`IsBOF`和`IsEOF`即可偵測程式碼捲動資料錄集，兩個方向的資料錄集的限制。  
  
 [!code-cpp[NVC_MFCDatabase #&25;](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]  
  
##  <a name="isdeleted"></a>CRecordset::IsDeleted  
 判斷是否已刪除目前的記錄。  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果資料錄集位於已刪除的記錄。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您捲動至資料錄和`IsDeleted`傳回**TRUE** （非零），然後您必須捲動至另一筆記錄之前，您可以執行任何其他資料錄集作業。  
  
 結果`IsDeleted`取決於許多因素，例如您的資料錄集類型、 您是否指定是否可以更新資料錄集**CRecordset::skipDeletedRecords**選項是否驅動程式套件中刪除記錄時，請開啟資料錄集，以及是否有多個使用者。  
  
 如需詳細資訊**CRecordset::skipDeletedRecords**和驅動程式封裝，請參閱[開啟](#open)成員函式。  
  
> [!NOTE]
>  如果您已實作大量資料列擷取，您不應該呼叫`IsDeleted`。 請改為呼叫[GetRowStatus](#getrowstatus)成員函式。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="iseof"></a>CRecordset::IsEOF  
 傳回非零，如果已位置之後的最後一個記錄的資料錄集。 沒有目前資料錄。  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果資料錄集不包含任何記錄，或是已經超過最後一筆記錄中。否則為 0。  
  
### <a name="remarks"></a>備註  
 當您從資料錄捲動記錄，以了解您是否已超過最後一筆記錄的資料錄集已經呼叫此成員函式。 您也可以使用`IsEOF`來判斷資料錄集是否包含任何記錄，或為空白。 之後立即呼叫**開啟**，如果資料錄集不包含任何記錄，`IsEOF`傳回非零值。 當您開啟已至少一筆記錄的資料錄集時，第一筆記錄是目前的記錄和`IsEOF`傳回 0。  
  
 如果最後一筆記錄是目前的記錄，當您呼叫`MoveNext`，`IsEOF`後續將會傳回非零值。 如果`IsEOF`傳回非零，而且您呼叫`MoveNext`，則會發生錯誤。 如果`IsEOF`傳回非零，目前的記錄會是未定義，以及任何需要目前記錄的動作將會產生錯誤。  
  
### <a name="example"></a>範例  
 請參閱範例[IsBOF](#isbof)。  
  
##  <a name="isfielddirty"></a>CRecordset::IsFieldDirty  
 判斷指定的欄位資料成員是否已變更自[編輯](#edit)或[AddNew](#addnew)呼叫。  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 您想要檢查其狀態的欄位資料成員的指標或**NULL**來判斷是否有任何欄位已變更。  
  
### <a name="return-value"></a>傳回值  
 如果指定的欄位資料成員已自呼叫變更為非零`AddNew`或**編輯**，否則為 0。  
  
### <a name="remarks"></a>備註  
 所有已變更的欄位資料成員中的資料會傳輸至記錄資料來源上呼叫更新目前的記錄時[更新](#update)成員函式`CRecordset`(到呼叫**編輯**或`AddNew`)。  
  
> [!NOTE]
>  此成員函式不適用於使用大量資料列擷取的資料錄集。 如果您已實作大量資料列擷取，然後`IsFieldDirty`一律會傳回**FALSE**而導致失敗的判斷提示。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 呼叫`IsFieldDirty`會重設先前呼叫的效果[SetFieldDirty](#setfielddirty)因為欄位已變更狀態，也會重新評估。 在`AddNew`的情況下，如果目前的欄位值不同於虛擬 null 值，欄位狀態設定已變更。 在**編輯**情況下，如果與快取的值，然後設定已變更欄位狀態不同的欄位值。  
  
 `IsFieldDirty`透過實作[DoFieldExchange](#dofieldexchange)。  
  
 如需有關記錄變更旗標的詳細資訊，請參閱文章[資料錄集︰ 如何資料錄集選取資料錄 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。  
  
##  <a name="isfieldnull"></a>CRecordset::IsFieldNull  
 傳回非零值，如果目前的記錄中指定的欄位為 Null （沒有任何值）。  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 您想要檢查其狀態的欄位資料成員的指標或**NULL**來決定的任何欄位都是 Null。  
  
### <a name="return-value"></a>傳回值  
 指定的欄位資料成員標示為 Null; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式，以判斷資料錄集的指定的欄位資料成員是否被標示為 Null。 (在資料庫術語中，為 Null 」 有任何值 」 的方式，不與相同**NULL** c + + 中。)如果欄位資料成員被標示為 Null，它會解譯為資料行的任何值是目前的記錄。  
  
> [!NOTE]
>  此成員函式不適用於使用大量資料列擷取的資料錄集。 如果您已實作大量資料列擷取，然後`IsFieldNull`一律會傳回**FALSE**而導致失敗的判斷提示。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 `IsFieldNull`透過實作[DoFieldExchange](#dofieldexchange)。  
  
##  <a name="isfieldnullable"></a>CRecordset::IsFieldNullable  
 傳回非零，如果目前的記錄中指定的欄位可以設定為 Null （具有任何值）。  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 您想要檢查其狀態的欄位資料成員的指標或**NULL**判斷如果任一欄位可設為 Null 值。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式，以判斷指定的欄位資料成員是 「 null 」 （可以是設定為 Null 值。C + + **NULL**不是 Null，表示，在資料庫術語中，相同不擁有任何值 」)。  
  
> [!NOTE]
>  如果您已實作大量資料列擷取，您不能呼叫`IsFieldNullable`。 請改為呼叫[GetODBCFieldInfo](#getodbcfieldinfo)成員函式來判斷資料是否可以設定為 Null 值。 請注意，您一律可以致電`GetODBCFieldInfo`，不論您是否有實作大量資料列擷取。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 不能是 Null 的欄位必須有值。 如果您嘗試將這類欄位設定為 Null，新增或更新一筆記錄時，資料來源會拒絕新增或更新，以及[更新](#update)將會擲回例外狀況。 當您呼叫時，就會發生例外狀況**更新**，不會在您呼叫[SetFieldNull](#setfieldnull)。  
  
 使用**NULL**函式的第一個引數只能套用函式的**outputColumn**欄位中不**param**欄位。 例如，呼叫  
  
 [!code-cpp[NVC_MFCDatabase #&26;](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 集合只**outputColumn**欄位**NULL**;**param**欄位不會受到影響。  
  
 若要致力於**param**欄位中，您必須提供個別的實際位址**param**您想要使用，例如︰  
  
 [!code-cpp[NVC_MFCDatabase #&27;](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 這表示您無法設定所有**param**欄位**NULL**，您可以使用如**outputColumn**欄位。  
  
 `IsFieldNullable`透過實作[DoFieldExchange](#dofieldexchange)。  
  
##  <a name="isopen"></a>CRecordset::IsOpen  
 判斷是否已開啟資料錄集。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零資料錄集物件的[開啟](#open)或[Requery](#requery)先前呼叫成員函式和資料錄集尚未關閉，否則為 0。  
  
##  <a name="m_hstmt"></a>CRecordset::m_hstmt  
 包含 ODBC 陳述式資料結構類型的控制代碼**HSTMT**、 資料錄集相關聯。  
  
### <a name="remarks"></a>備註  
 每個查詢至 ODBC 資料來源相關聯**HSTMT**。  
  
> [!CAUTION]
>  請勿使用**m_hstmt**之前[開啟](#open)被呼叫。  
  
 通常您不需要存取**HSTMT**直接，但您可能需要直接執行 SQL 陳述式。 `ExecuteSQL`類別成員函式`CDatabase`舉例說明使用**m_hstmt**。  
  
##  <a name="m_nfields"></a>CRecordset::m_nFields  
 包含資料錄集類別; 中的欄位資料成員的數目也就是說，資料來源的資料錄集選取資料行數目。  
  
### <a name="remarks"></a>備註  
 資料錄集類別的建構函式必須初始化`m_nFields`及正確的數值。 如果您未實作大量資料列擷取，ClassWizard 您用它來宣告資料錄集類別時，就會寫入此初始化的。 您也可以撰寫它以手動方式。  
  
 架構會管理對應的資料行的資料來源上的目前記錄的欄位資料成員之間的互動，使用這個數字。  
  
> [!CAUTION]
>  這個數字必須對應到 「 輸出資料行 」 中登錄數目`DoFieldExchange`或`DoBulkFieldExchange`呼叫後[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)參數**CFieldExchange::outputColumn**。  
  
 可以繫結資料行，以動態方式一文所述，「 資料錄集︰ 動態地繫結資料行。 」 如果您這樣做，您必須增加計數`m_nFields`以反映 RFX 或 Bulk RFX 函式的數字會呼叫您`DoFieldExchange`或`DoBulkFieldExchange`動態繫結的資料行的成員函式。  
  
 如需詳細資訊，請參閱文章[資料錄集︰ 動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)和[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>範例  
 請參閱文章[資料錄欄位交換︰ RFX 的使用](../../data/odbc/record-field-exchange-using-rfx.md)。  
  
##  <a name="m_nparams"></a>CRecordset::m_nParams  
 包含在資料錄集類別中，參數資料成員的數目也就是使用資料錄集的查詢傳遞的參數數目。  
  
### <a name="remarks"></a>備註  
 如果您的資料錄集類別有任何參數資料成員，必須初始化類別的建構函式`m_nParams`及正確的數值。 值`m_nParams`預設值為 0。 如果您加入參數資料成員 （這是您必須以手動方式執行） 您必須手動加入初始化類別建構函式，以反映的參數數目 (必須是至少一樣大的數目 ' 中的預留位置程式**m_strFilter**或`m_strSort`字串)。  
  
 當它參數化資料錄集的查詢時，架構會使用這個數字。  
  
> [!CAUTION]
>  這個數字必須對應到 「 參數 」 中登錄數目`DoFieldExchange`或`DoBulkFieldExchange`呼叫後[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)參數值是**CFieldExchange::inputParam**， **CFieldExchange::param**， **CFieldExchange::outputParam**，或**CFieldExchange::inoutParam**。  
  
### <a name="example"></a>範例  
  請參閱文章[資料錄集︰ 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)和[資料錄欄位交換︰ RFX 的使用](../../data/odbc/record-field-exchange-using-rfx.md)。  
  
##  <a name="m_pdatabase"></a>CRecordset::m_pDatabase  
 包含一個指向`CDatabase`透過此資料錄集連接到資料來源的物件。  
  
### <a name="remarks"></a>備註  
 兩種方式設定這個變數。 一般而言，您將指標傳遞至已連線`CDatabase`物件建構資料錄集物件時。 如果您傳遞**NULL**反而`CRecordset`建立`CDatabase`物件，並將它連線。 在任一情況下，`CRecordset`指標儲存在此變數。  
  
 通常您會直接不必使用指標儲存在**m_pDatabase**。 如果您撰寫自己的延伸模組來`CRecordset`，不過，您可能需要使用該指標。 例如，您可能需要將指標如果您擲回自己`CDBException`s。 或者如果您需要執行一些動作使用的相同，可能需要它`CDatabase`物件，例如執行交易，設定逾時值，或呼叫`ExecuteSQL`類別成員函式`CDatabase`直接執行 SQL 陳述式。  
  
##  <a name="m_strfilter"></a>CRecordset::m_strFilter  
 但您建構資料錄集物件之後, 才能呼叫其**開啟**成員函式中，使用此資料成員來儲存`CString`包含 SQL**其中**子句。  
  
### <a name="remarks"></a>備註  
 資料錄集限制 （或篩選） 的記錄，它會選取期間會使用此字串**開啟**或**Requery**呼叫。 這可用來選取記錄，例如 「 居住在加州的所有銷售人員 」 的子集 (「 狀態 = CA 」)。 ODBC SQL 語法**其中**子句  
  
 `WHERE search-condition`  
  
 請注意，不包含**其中**在字串中的關鍵字。 架構會提供它。  
  
 您可以藉由放置也參數化篩選字串 ' 預留位置，在宣告參數資料成員在類別中的每個替代符號，並將參數傳遞至資料錄集在執行階段。 這可讓您在執行階段建構篩選條件。 如需詳細資訊，請參閱文章[資料錄集︰ 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
 如需有關 SQL**其中**子句，請參閱文章[SQL](../../data/odbc/sql.md)。 如需選取和篩選記錄的詳細資訊，請參閱文章[資料錄集︰ 篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase #&30;](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]  
  
##  <a name="m_strsort"></a>CRecordset::m_strSort  
 但您建構資料錄集物件之後, 才能呼叫其**開啟**成員函式中，使用此資料成員來儲存`CString`包含 SQL **ORDER BY**子句。  
  
### <a name="remarks"></a>備註  
 資料錄集來排序的記錄，它會選取期間會使用此字串**開啟**或**Requery**呼叫。 若要排序的一或多個資料行的資料錄集，您可以使用這項功能。 ODBC SQL 語法**ORDER BY**子句  
  
 `ORDER BY sort-specification [, sort-specification]...`  
  
 其中排序規格是整數或資料行名稱。 您也可以藉由附加"ASC"或"DESC"排序字串中的資料行清單來指定遞增或遞減順序 （預設為遞增順序）。 選取的資料錄先進行排序所列出的第一欄，再依第二個，依此類推。 例如，您可能訂購 「 客戶 」 資料錄集的最後一個名稱，然後再按照名字。 您可以列出的資料行數目取決於資料來源。 如需詳細資訊，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] *。*  
  
 請注意，不包含**ORDER BY**在字串中的關鍵字。 架構會提供它。  
  
 如需 SQL 子句的詳細資訊，請參閱文章[SQL](../../data/odbc/sql.md)。 如需排序資料錄的詳細資訊，請參閱文章[資料錄集︰ 排序資料錄 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase #&31;](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]  
  
##  <a name="move"></a>CRecordset::Move  
 將目前的記錄指標內資料錄集，向前或向後移。  
  
```  
virtual void Move(
    long nRows,  
    WORD wFetchType = SQL_FETCH_RELATIVE);
```  
  
### <a name="parameters"></a>參數  
 `nRows`  
 向前或向後移動的資料列數目。 正值向前，移到資料錄集的結尾。 負數值後，移到開頭。  
  
 `wFetchType`  
 判斷資料列集的**移動**會提取。 如需詳細資料，請參閱＜備註＞。  
  
### <a name="remarks"></a>備註  
 如果您傳遞的值為 0，表示`nRows`，**移動**重新整理目前的記錄。**移動**會結束目前`AddNew`或**編輯**模式中，將會還原之前的目前記錄的值和`AddNew`或**編輯**呼叫。  
  
> [!NOTE]
>  當您移動的資料錄集時，您無法略過已刪除的記錄。 請參閱[CRecordset::IsDeleted](#isdeleted)如需詳細資訊。 當您開啟`CRecordset`與**skipDeletedRecords**選項集，**移動**判斷提示，如果`nRows`參數是 0。 這種行為可避免在重新整理的其他用戶端應用程式使用相同的資料已刪除的資料列。 請參閱`dwOption`中的參數[開啟](#open)的說明**skipDeletedRecords**。  
  
 **移動**重新定位的資料列集的資料錄集。 根據的值`nRows`和`wFetchType`，**移動**擷取適當資料列集，然後將第一筆記錄中該資料列集目前的記錄。 如果您未實作大量資料列擷取，然後資料列集大小永遠為 1。 當提取資料列集，**移動**直接呼叫[CheckRowsetError](#checkrowseterror)成員函式，以處理擷取的任何錯誤。  
  
 依據值傳遞，**移動**相當於其他`CRecordset`成員函式。 特別是，值`wFetchType`可能表示更直覺的成員函式，並經常移動目前記錄的慣用的方法。  
  
 下表列出可能的值為`wFetchType`，資料列集的**移動**會提取根據`wFetchType`和`nRows`，對應至任何對等成員函式`wFetchType`。  
  
|wFetchType|擷取資料列集|對等成員函式|  
|----------------|--------------------|--------------------------------|  
|`SQL_FETCH_RELATIVE`（預設值）|資料列集啟動`nRows`中目前資料列集的第一個資料列的資料列。||  
|`SQL_FETCH_NEXT`|下一個資料列集。`nRows`會被忽略。|[MoveNext](#movenext)|  
|`SQL_FETCH_PRIOR`|先前的資料列。`nRows`會被忽略。|[MovePrev](#moveprev)|  
|`SQL_FETCH_FIRST`|第一個資料列集資料錄集。`nRows`會被忽略。|[MoveFirst](#movefirst)|  
|`SQL_FETCH_LAST`|最後的完整資料列集資料錄集。`nRows`會被忽略。|[MoveLast](#movelast)|  
|`SQL_FETCH_ABSOLUTE`|如果`nRows`> 0，資料列集啟動`nRows`開始從資料錄集的資料列。 如果`nRows` < 0,="" the="" rowset="" starting=""> `nRows`個資料列從資料錄集的結尾。 如果`nRows`= 0，則會傳回開頭的檔案 (BOF) 條件。|[SetAbsolutePosition](#setabsoluteposition)|  
|`SQL_FETCH_BOOKMARK`|資料列集的書籤值會對應到資料列開始`nRows`。|[SetBookmark](#setbookmark)|  
  
> [!NOTE]
>  順向的資料錄集的**移動**才有效，值為`SQL_FETCH_NEXT`的`wFetchType`。  
  
> [!CAUTION]
>  呼叫**移動**擲回例外狀況，如果資料錄集沒有任何記錄。 若要判斷資料錄集是否有任何記錄，請呼叫[IsBOF](#isbof)和[IsEOF](#iseof)。  
  
> [!NOTE]
>  如果您有捲動過去的開頭或結尾的資料錄集 (`IsBOF`或`IsEOF`傳回非零值)，則呼叫**移動**函式可能會擲回`CDBException`。 例如，如果`IsEOF`傳回非零值和`IsBOF`不存在，然後`MoveNext`將會擲回例外狀況，但`MovePrev`則不會。  
  
> [!NOTE]
>  如果您呼叫**移動**目前的記錄時，更新或加入更新都會遺失，而不發出警告。  
  
 如需巡覽資料錄集的詳細資訊，請參閱文章[資料錄集︰ 捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[資料錄集︰ 書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 如需相關資訊，請參閱 ODBC API 函式**SQLExtendedFetch**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase #&28;](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]  
  
##  <a name="movefirst"></a>CRecordset::MoveFirst  
 讓第一筆記錄中的第一個資料列集目前的記錄。  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>備註  
 不論是否大量資料列擷取已實作，這一定是資料錄集的第一個記錄。  
  
 您不需要呼叫**MoveFirst**立即開啟資料錄集之後。 此時，第一筆記錄 （如果有的話） 會自動為目前的記錄。  
  
> [!NOTE]
>  此成員函式的順向的資料錄集無效。  
  
> [!NOTE]
>  當您移動的資料錄集時，您無法略過已刪除的記錄。 請參閱[IsDeleted](#isdeleted)成員函式，如需詳細資訊。  
  
> [!CAUTION]
>  呼叫的任何**移動**函式擲回例外狀況，如果資料錄集沒有任何記錄。 若要判斷資料錄集是否有任何記錄，請呼叫`IsBOF`和`IsEOF`。  
  
> [!NOTE]
>  如果您呼叫任何**移動**函式時，目前的記錄更新或加入更新都會遺失，而不發出警告。  
  
 如需巡覽資料錄集的詳細資訊，請參閱文章[資料錄集︰ 捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[資料錄集︰ 書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>範例  
  請參閱範例[IsBOF](#isbof)。  
  
##  <a name="movelast"></a>CRecordset::MoveLast  
 讓第一筆記錄中的最後一個完整的資料列集目前的記錄。  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>備註  
 若未實作大量資料列擷取，資料錄集的資料列集大小為 1，因此`MoveLast`就會直接移到最後一個記錄集。  
  
> [!NOTE]
>  此成員函式的順向的資料錄集無效。  
  
> [!NOTE]
>  當您移動的資料錄集時，您無法略過已刪除的記錄。 請參閱[IsDeleted](#isdeleted)成員函式，如需詳細資訊。  
  
> [!CAUTION]
>  呼叫的任何**移動**函式擲回例外狀況，如果資料錄集沒有任何記錄。 若要判斷資料錄集是否有任何記錄，請呼叫`IsBOF`和`IsEOF`。  
  
> [!NOTE]
>  如果您呼叫任何**移動**函式時，目前的記錄更新或加入更新都會遺失，而不發出警告。  
  
 如需巡覽資料錄集的詳細資訊，請參閱文章[資料錄集︰ 捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[資料錄集︰ 書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>範例  
  請參閱範例[IsBOF](#isbof)。  
  
##  <a name="movenext"></a>CRecordset::MoveNext  
 讓第一筆記錄中的下一個資料列集目前的記錄。  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>備註  
 若未實作大量資料列擷取，資料錄集的資料列集大小為 1，因此`MoveNext`就會直接移至下一筆記錄。  
  
> [!NOTE]
>  當您移動的資料錄集時，您無法略過已刪除的記錄。 請參閱[IsDeleted](#isdeleted)成員函式，如需詳細資訊。  
  
> [!CAUTION]
>  呼叫的任何**移動**函式擲回例外狀況，如果資料錄集沒有任何記錄。 若要判斷資料錄集是否有任何記錄，請呼叫`IsBOF`和`IsEOF`。  
  
> [!NOTE]
>  也建議您呼叫`IsEOF`之前，先呼叫`MoveNext`。 例如，如果您有捲動超過結尾的資料錄集，`IsEOF`會傳回非零值; 的後續呼叫`MoveNext`會擲回例外狀況。  
  
> [!NOTE]
>  如果您呼叫任何**移動**函式時，目前的記錄更新或加入更新都會遺失，而不發出警告。  
  
 如需巡覽資料錄集的詳細資訊，請參閱文章[資料錄集︰ 捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[資料錄集︰ 書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>範例  
  請參閱範例[IsBOF](#isbof)。  
  
##  <a name="moveprev"></a>CRecordset::MovePrev  
 讓第一筆記錄中的前一個資料列集目前的記錄。  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>備註  
 若未實作大量資料列擷取，資料錄集的資料列集大小為 1，因此`MovePrev`就會直接移至前一筆記錄。  
  
> [!NOTE]
>  此成員函式的順向的資料錄集無效。  
  
> [!NOTE]
>  當您移動的資料錄集時，您無法略過已刪除的記錄。 請參閱[IsDeleted](#isdeleted)成員函式，如需詳細資訊。  
  
> [!CAUTION]
>  呼叫的任何**移動**函式擲回例外狀況，如果資料錄集沒有任何記錄。 若要判斷資料錄集是否有任何記錄，請呼叫`IsBOF`和`IsEOF`。  
  
> [!NOTE]
>  也建議您呼叫`IsBOF`之前，先呼叫`MovePrev`。 例如，如果您有捲動資料錄集，開頭前面`IsBOF`會傳回非零值; 的後續呼叫`MovePrev`會擲回例外狀況。  
  
> [!NOTE]
>  如果您呼叫任何**移動**函式時，目前的記錄更新或加入更新都會遺失，而不發出警告。  
  
 如需巡覽資料錄集的詳細資訊，請參閱文章[資料錄集︰ 捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[資料錄集︰ 書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
### <a name="example"></a>範例  
  請參閱範例[IsBOF](#isbof)。  
  
##  <a name="onsetoptions"></a>CRecordset::OnSetOptions  
 針對指定的 ODBC 陳述式來呼叫設定選項 （選取項目上使用）。  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>參數  
 `hstmt`  
 **HSTMT** ODBC 陳述式的選項是用來設定。  
  
### <a name="remarks"></a>備註  
 呼叫`OnSetOptions`來針對指定的 ODBC 陳述式來設定選項 （用於選取）。 架構會呼叫此成員函式初始設定資料錄集。 `OnSetOptions`判斷資料來源的支援可捲動資料指標和資料指標並行處理，並據以設定資料錄集的選項。 (而`OnSetOptions`適用於選取作業`OnSetUpdateOptions`適用於更新作業。)  
  
 覆寫`OnSetOptions`設定驅動程式或資料來源的特定選項。 例如，如果您的資料來源支援的獨佔存取開啟，您可能會覆寫`OnSetOptions`善用這項功能。  
  
 如需資料指標的詳細資訊，請參閱文章[ODBC](../../data/odbc/odbc-basics.md)。  
  
##  <a name="onsetupdateoptions"></a>CRecordset::OnSetUpdateOptions  
 呼叫以針對指定的 ODBC 陳述式來設定 （用於更新） 的選項。  
  
```  
virtual void OnSetUpdateOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>參數  
 `hstmt`  
 **HSTMT** ODBC 陳述式的選項是用來設定。  
  
### <a name="remarks"></a>備註  
 呼叫`OnSetUpdateOptions`（用於更新） 的選項設定為指定的 ODBC 陳述式。 建立 HSTMT 來更新資料錄集中的記錄之後，架構會呼叫此成員函式。 (而`OnSetOptions`適用於選取作業`OnSetUpdateOptions`適用於更新作業。)`OnSetUpdateOptions`判斷資料來源的支援可捲動資料指標和資料指標並行處理，並據以設定資料錄集的選項。  
  
 覆寫`OnSetUpdateOptions`設定 ODBC 陳述式的選項後，該陳述式用來存取資料庫。  
  
 如需資料指標的詳細資訊，請參閱文章[ODBC](../../data/odbc/odbc-basics.md)。  
  
##  <a name="open"></a>Crecordset:: Open  
 開啟資料錄集擷取資料表或查詢資料錄集表示。  
  
```  
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,  
    LPCTSTR lpszSQL = NULL,  
    DWORD dwOptions = none);
```  
  
### <a name="parameters"></a>參數  
 `nOpenType`  
 接受預設值， **AFX_DB_USE_DEFAULT_TYPE**，或使用下列其中一個值從**列舉 OpenType**:  
  
- **CRecordset::dynaset**雙向捲動資料錄集。 成員資格和順序的記錄會在開啟資料錄集時，但其他使用者的資料值所做的變更會顯示下列提取作業時決定。 動態集也是索引鍵集驅動資料錄集。  
  
- **CRecordset::snapshot**靜態雙向捲動資料錄集。 開啟資料錄集時，決定成員資格和順序的記錄擷取記錄時，會決定資料值。 其他使用者所做的變更是不可見，直到關閉後再重新開啟資料錄集。  
  
- **CRecordset::dynamic**雙向捲動資料錄集。 成員資格、 順序和資料值的其他使用者所做的變更會顯示下列提取作業。 請注意，許多 ODBC 驅動程式不支援這種類型的資料錄集。  
  
- **CRecordset::forwardOnly**只會順向捲動的唯讀資料錄集。  
  
     如`CRecordset`，預設值是**CRecordset::snapshot**。 預設值的機制可讓您能與 ODBC 的 Visual c + + 精靈`CRecordset`和 DAO `CDaoRecordset`，其中有不同的預設值。  
  
 如需這些資料錄集類型的詳細資訊，請參閱文章[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)。 如需相關資訊，請參閱文件 」 使用區塊和可捲動資料指標 」 中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
> [!CAUTION]
>  如果不支援要求的型別，架構就會擲回例外狀況。  
  
 `lpszSQL`  
 字串指標，其中包含下列其中之一︰  
  
-   A **NULL**指標。  
  
-   資料表的名稱。  
  
-   SQL**選取**陳述式 (並選擇性地使用 SQL**其中**或**ORDER BY**子句)。  
  
-   A**呼叫**陳述式指定預先定義的查詢 （預存程序） 的名稱。 請小心不要將大括號之間的空白字元和**呼叫**關鍵字。  
  
 如需這個字串的詳細資訊，請參閱資料表與討論的 < 備註 > 底下的 ClassWizard 的角色。  
  
> [!NOTE]
>  在結果集中資料行的順序必須符合的 RFX 的順序，或 Bulk RFX 函式呼叫您[DoFieldExchange](#dofieldexchange)或[DoBulkFieldExchange](#dobulkfieldexchange)函式覆寫。  
  
 `dwOptions`  
 位元遮罩可以指定下列值的組合。 其中有些是互斥的。 預設值是**無**。  
  
- **CRecordset::none**設定任何選項。 此參數值是互斥的所有其他值。 根據預設，可以更新資料錄集與[編輯](#edit)或[刪除](#delete)，並允許附加新資料錄[AddNew](#addnew)。 可更新性取決於資料來源上，以及`nOpenType`您指定的選項。 無法使用大量加入的最佳化。 將未實作大量資料列擷取。 已刪除的記錄不會在資料錄集巡覽期間略過。 沒有可用的書籤。 實作檢查自動記錄變更的欄位。  
  
- **CRecordset::appendOnly**不允許**編輯**或**刪除**資料錄集。 允許`AddNew`只。 此選項會與互斥**CRecordset::readOnly**。  
  
- **CRecordset::readOnly**開啟為唯讀資料錄集。 此選項會與互斥**CRecordset::appendOnly**。  
  
- **CRecordset::optimizeBulkAdd**使用備妥的 SQL 陳述式最佳化一次新增多筆記錄。 您不想要使用的 ODBC API 函式時，才會套用**SQLSetPos**來更新資料錄集。 第一次更新判斷哪些欄位會標示為已變更。 此選項會與互斥`CRecordset::useMultiRowFetch`。  
  
- `CRecordset::useMultiRowFetch`實作以允許多個資料列擷取單一擷取作業中的大量資料列擷取。 這是設計成可增進效能; 的進階的功能不過，大量資料錄欄位交換不受到 ClassWizard。 此選項會與互斥**CRecordset::optimizeBulkAdd**。 請注意，如果您指定`CRecordset::useMultiRowFetch`的選項**CRecordset::noDirtyFieldCheck**會自動開啟 （雙重緩衝將無法使用），順向的資料錄集，此選項在**CRecordset::useExtendedFetch**會自動開啟。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
- **CRecordset::skipDeletedRecords**巡覽資料錄集時，略過所有已刪除的記錄。 這會降低效能，在某些相對提取。 這個選項不正確的順向的資料錄集。 如果您呼叫[移動](#move)與`nRows`參數設定為 0，而**CRecordset::skipDeletedRecords**選項集，**移動**會判斷提示。 請注意， **CRecordset::skipDeletedRecords**類似*驅動程式封裝*，表示已刪除資料列會從資料錄集。 不過，如果驅動程式套件的記錄，則會略過的記錄，您將其刪除。它會略過資料錄集開啟時，由其他使用者刪除記錄。 **CRecordset::skipDeletedRecords**會略過刪除其他使用者的資料列。  
  
- **CRecordset::useBookmarks**可能書籤資料錄集，如果使用支援。 書籤擷取資料可是改善資料瀏覽的效能。 順向的資料錄集上不正確。 如需詳細資訊，請參閱文章[資料錄集︰ 書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。  
  
- **CRecordset::noDirtyFieldCheck**關閉自動記錄變更的欄位檢查 （雙重緩衝）。 這將可改善效能。不過，您必須手動標示欄位為中途藉由呼叫`SetFieldDirty`和`SetFieldNull`成員函式。請注意在類別中的雙重緩衝`CRecordset`類似於類別中的雙重緩衝`CDaoRecordset`。 不過，在`CRecordset`，您無法啟用雙重緩衝的個別欄位; 您啟用的所有欄位，或停用的所有欄位。 請注意，如果您指定選項`CRecordset::useMultiRowFetch`，然後**CRecordset::noDirtyFieldCheck**將會開啟自動; 不過，`SetFieldDirty`和`SetFieldNull`上實作大量資料列擷取資料錄集無法使用。  
  
- **CRecordset::executeDirect**不使用備妥的 SQL 陳述式。 為了增進效能，如果指定這個選項**Requery**絕不會呼叫成員函式。  
  
- **CRecordset::useExtendedFetch**實作**SQLExtendedFetch**而不是**SQLFetch**。 這被設計用於實作大量順向的資料錄集的資料列擷取。 如果您指定選項`CRecordset::useMultiRowFetch`順向的資料錄集，然後**CRecordset::useExtendedFetch**會自動開啟。  
  
- **CRecordset::userAllocMultiRowBuffers**使用者將會配置儲存緩衝區的資料。 使用此選項搭配`CRecordset::useMultiRowFetch`如果您想要配置您的存放區; 否則架構會自動配置必要的儲存體。 如需詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 請注意該指定**CRecordset::userAllocMultiRowBuffers**但未指定`CRecordset::useMultiRowFetch`會導致失敗的判斷提示。  
  
### <a name="return-value"></a>傳回值  
 如果為非零`CRecordset`物件已成功開啟，否則為 0 [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) （如果呼叫） 會傳回 0。  
  
### <a name="remarks"></a>備註  
 您必須呼叫此成員函式，以執行查詢資料錄集所定義。 然後再呼叫**開啟**，您必須建構資料錄集物件。  
  
 此資料錄集的資料來源的連接取決於您如何建構資料錄集，然後再呼叫**開啟**。 如果您傳遞[CDatabase](../../mfc/reference/cdatabase-class.md)物件未連接到資料來源，資料錄集建構函式會使用此成員函式[GetDefaultConnect](#getdefaultconnect)嘗試開啟資料庫物件。 如果您傳遞**NULL**建構函式建構資料錄集建構函式，`CDatabase`物件，和**開啟**嘗試連接的資料庫物件。 關閉資料錄集，並在這些不同的情況下連接的詳細資訊，請參閱[關閉](#close)。  
  
> [!NOTE]
>  透過資料來源的存取權`CRecordset`一律共用物件。 不同於`CDaoRecordset`類別中，您不能使用`CRecordset`物件開啟資料來源使用獨佔存取權。  
  
 當您呼叫**開啟**，查詢時，通常是 SQL**選取**陳述式中，選取資料錄根據下表所示的準則。  
  
|LpszSQL 參數的值|取決於選取的記錄|範例|  
|------------------------------------|----------------------------------------|-------------|  
|**NULL**|所傳回的字串`GetDefaultSQL`。||  
|SQL 資料表名稱|資料表清單中的所有資料行`DoFieldExchange`或`DoBulkFieldExchange`。|`"Customer"`|  
|預先定義的查詢 （預存程序） 的名稱|定義查詢傳回的資料行。|`"{call OverDueAccts}"`|  
|**選取**資料行清單**FROM**資料表清單|指定的資料表中指定的資料行。|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|  
  
> [!CAUTION]
>  請務必小心您執行 SQL 字串中插入的額外空白。 例如，如果您插入的大括號之間的空白字元和**呼叫**關鍵字，MFC 會錯誤解譯為資料表名稱的 SQL 字串，並將它**選取**陳述式，這會導致擲回例外狀況。 同樣地，如果您預先定義的查詢會使用輸出參數，不會將插入的大括號之間的空白字元和 ' 符號。 最後，您必須插入之前的大括號中的空白字元**呼叫**陳述式或之前**選取**關鍵字**選取**陳述式。  
  
 一般程序是將**NULL**至**開啟**; 在此情況下，**開啟**呼叫[GetDefaultSQL](#getdefaultsql)。 如果您使用衍生`CRecordset`類別， **GetDefaultSQL**可讓您在類別中指定的資料表名稱。 您可以指定中的其他資訊`lpszSQL`參數。  
  
 無論您傳遞，**開啟**建構查詢的最終 SQL 字串 (字串可能有 SQL**其中**和**ORDER BY**子句附加至`lpszSQL`字串傳遞給您)，然後執行查詢。 您可以藉由呼叫檢查建構的字串[GetSQL](#getsql)之後呼叫**開啟**。 如其他詳細資料錄集如何建構 SQL 陳述式，並選取資料錄，請參閱文章[資料錄集︰ 如何資料錄集選取資料錄 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。  
  
 資料錄集類別的欄位資料成員會繫結至選取的資料的資料行。 如果傳回任何記錄，第一筆記錄會變成目前的記錄。  
  
 如果您想要設定資料錄集篩選或排序，例如在建構資料錄集物件之後，但在呼叫之前指定這些**開啟**。 如果您想要重新整理資料錄集之後的記錄資料錄集已經開啟，請呼叫[Requery](#requery)。  
  
 如需詳細資訊，包括其他範例，請參閱文章[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)，[資料錄集︰ 如何資料錄集選取資料錄 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)，和[資料錄集︰ 建立和關閉資料錄集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。  
  
### <a name="example"></a>範例  
 下列程式碼範例會顯示不同形式的**開啟**呼叫。  
  
 [!code-cpp[NVC_MFCDatabase #&16;](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]  
  
##  <a name="refreshrowset"></a>CRecordset::RefreshRowset  
 更新資料和目前的資料列集中的資料列的狀態。  
  
```  
void RefreshRowset(
    WORD wRow,  
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>參數  
 `wRow`  
 以一為位置的資料列中目前資料列集。 這個值可以介於零的資料列集大小。  
  
 `wLockType`  
 值，指出已重新整理之後，鎖定資料列的方式。 如需詳細資料，請參閱＜備註＞。  
  
### <a name="remarks"></a>備註  
 如果您傳遞的值為零的`wRow`，然後將重新整理的資料列集中的每個資料列。  
  
 若要使用`RefreshRowset`，您必須藉由指定的大量資料列擷取已實作**CRecordset::useMulitRowFetch**選項[開啟](#open)成員函式。  
  
 `RefreshRowset`呼叫 ODBC API 函式**SQLSetPos**。 `wLockType`參數會指定資料列之後的鎖定狀態**SQLSetPos**已經執行。 下表說明可能的值為`wLockTyp`e。  
  
|wLockType|描述|  
|---------------|-----------------|  
|`SQL_LOCK_NO_CHANGE`（預設值）|驅動程式或資料來源可確保資料列中相同的鎖定或解除鎖定狀態前`RefreshRowset`呼叫。|  
|`SQL_LOCK_EXCLUSIVE`|驅動程式或資料來源以獨佔方式鎖定資料列。 並非所有資料來源都支援這種類型的鎖定。|  
|`SQL_LOCK_UNLOCK`|驅動程式或資料來源會解除鎖定資料列。 並非所有資料來源都支援這種類型的鎖定。|  
  
 如需詳細資訊**SQLSetPos**，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="requery"></a>CRecordset::Requery  
 重建 （重新整理） 資料錄集。  
  
```  
virtual BOOL Requery();
```  
  
### <a name="return-value"></a>傳回值  
 已成功重建資料錄集; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果傳回任何記錄，第一筆記錄會變成目前的記錄。  
  
 為了讓資料錄集，以反映您或其他使用者對資料來源的刪除和新增項目，您必須重建資料錄集，藉由呼叫**Requery**。 動態資料錄集時，它會自動反映您或其他使用者對其現有的記錄 （但不是新增項目） 的更新。 如果資料錄集是快照集，您必須呼叫**Requery**以反映其他使用者，以及新增和刪除作業的編輯。  
  
 動態集或快照集，呼叫**Requery**每當您想要重建資料錄集使用新的篩選或排序或新的參數值。 設定新的篩選或排序屬性指派新值給**m_strFilter**和`m_strSort`之前，先呼叫**Requery**。 設定新的參數指派新值給參數資料成員，然後再呼叫**Requery**。 如果篩選和排序字串並不會變更，您可以重複使用查詢，進而改善效能。  
  
 如果嘗試重建資料錄集失敗，就會關閉資料錄集。 然後再呼叫**Requery**，您可以判斷是否可以藉由呼叫重新查詢資料錄集`CanRestart`成員函式。 `CanRestart`不保證**Requery**會成功。  
  
> [!CAUTION]
>  呼叫**Requery**之後才呼叫[開啟](#open)。  
  
### <a name="example"></a>範例  
 這個範例會重建資料集，套用不同的排序順序。  
  
 [!code-cpp[NVC_MFCDatabase #&29;](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]  
  
##  <a name="setabsoluteposition"></a>CRecordset::SetAbsolutePosition  
 資料錄集置於對應至指定的記錄數目的記錄。  
  
```  
void SetAbsolutePosition(long nRows);
```  
  
### <a name="parameters"></a>參數  
 `nRows`  
 一個架構中的序數位置目前的記錄資料錄集。  
  
### <a name="remarks"></a>備註  
 `SetAbsolutePosition`將目前的記錄指標根據此序數位置。  
  
> [!NOTE]
>  此成員函式的順向的資料錄集無效。  
  
 ODBC 資料錄集的絕對位置設定為 1 是指第一筆記錄，在資料錄集。設定為 0，是指在檔案的開頭 (BOF) 位置。  
  
 您也可以傳遞至負值`SetAbsolutePosition`。 在此情況下會評估資料錄集的位置，從資料錄集的結尾。 例如，`SetAbsolutePosition( -1 )`將目前的記錄指標移到資料錄集中的最後一筆記錄。  
  
> [!NOTE]
>  絕對位置不是要做為代理的記錄數目。 書籤仍會保留，並傳回至指定的位置，因為刪除先前的記錄時，記錄的位置變更的建議的方式。 此外，您無法確定指定的記錄都有相同的絕對位置，如果因為無法保證除非則會以 SQL 陳述式來建立資料錄集內的個別記錄的順序重新重新建立資料錄集**ORDER BY**子句。  
  
 如需有關資料錄集巡覽和書籤的詳細資訊，請參閱文章[資料錄集︰ 捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[資料錄集︰ 書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。  
  
##  <a name="setbookmark"></a>CRecordset::SetBookmark  
 資料錄集置於包含指定的書籤的記錄。  
  
```  
void SetBookmark(const CDBVariant& varBookmark);
```  
  
### <a name="parameters"></a>參數  
 `varBookmark`  
 參考[CDBVariant](../../mfc/reference/cdbvariant-class.md)物件，其中包含書籤值的特定記錄。  
  
### <a name="remarks"></a>備註  
 若要判斷是否支援將書籤資料錄集，請呼叫[CanBookmark](#canbookmark)。 若要使用並支援書籤，您必須設定**CRecordset::useBookmarks**選項`dwOptions`參數[開啟](#open)成員函式。  
  
> [!NOTE]
>  如果書籤不支援或無法使用，則呼叫`SetBookmark`會導致擲回例外狀況。 順向的資料錄集不支援書籤。  
  
 若要先擷取目前的資料錄的書籤，請呼叫[GetBookmark](#getbookmark)，用於儲存的書籤值`CDBVariant`物件。 稍後，您可以傳回該記錄藉由呼叫`SetBookmark`使用已儲存的書籤值。  
  
> [!NOTE]
>  特定資料錄集作業之後，您應該檢查之前，先呼叫的書籤永續性`SetBookmark`。 例如，如果您擷取的書籤`GetBookmark`，然後呼叫**Requery**，書籤可能不再有效。 呼叫[CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)來檢查您是否能安全地呼叫`SetBookmark`。  
  
 如需書籤和資料錄集巡覽的詳細資訊，請參閱文章[資料錄集︰ 書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[資料錄集︰ 捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。  
  
##  <a name="setfielddirty"></a>CRecordset::SetFieldDirty  
 旗標為已變更的資料錄集，或為不變的欄位資料成員。  
  
```  
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 包含資料錄集中的欄位資料成員的地址或**NULL**。 如果**NULL**，資料錄集中的所有欄位資料成員會加上旗都標。 (C + + **NULL**不是 Null 相同資料庫術語而言，這表示 「 有任何值 」。)  
  
 `bDirty`  
 **TRUE**欄位資料成員是否被標示為 「 中途 」 （變更）。 否則**FALSE**欄位資料成員是否被標示為 「 清除 」 （未變更）。  
  
### <a name="remarks"></a>備註  
 標記成未變更的欄位，可確保不會更新欄位，並且產生的 SQL 流量。  
  
> [!NOTE]
>  此成員函式不適用於使用大量資料列擷取的資料錄集。 如果您已實作大量資料列擷取，然後`SetFieldDirty`會導致失敗的判斷提示。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 Framework 標記變更欄位資料成員，以確保它們會寫入資料來源上的記錄資料錄欄位交換 (RFX) 機制。 一般來說，變更欄位的值欄位已變更會自動設定，因此您很少需要呼叫`SetFieldDirty`，但是您有時候可能想要確保資料行將會明確地更新或插入不論什麼值是欄位資料成員中。  
  
> [!CAUTION]
>  呼叫此成員函式呼叫之後，才[編輯](#edit)或[AddNew](#addnew)。  
  
 使用**NULL**函式的第一個引數只能套用函式的**outputColumn**欄位中不**param**欄位。 例如，呼叫  
  
 [!code-cpp[NVC_MFCDatabase #&26;](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 集合只**outputColumn**欄位**NULL**;**param**欄位不會受到影響。  
  
 若要致力於**param**欄位中，您必須提供個別的實際位址**param**您想要使用，例如︰  
  
 [!code-cpp[NVC_MFCDatabase #&27;](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 這表示您無法設定所有**param**欄位**NULL**，您可以使用如**outputColumn**欄位。  
  
##  <a name="setfieldnull"></a>CRecordset::SetFieldNull  
 以旗標資料錄集欄位資料的成員為 Null （特別具有任何值） 或非 Null。  
  
```  
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 包含資料錄集中的欄位資料成員的地址或**NULL**。 如果**NULL**，資料錄集中的所有欄位資料成員會加上旗都標。 (C + + **NULL**不是 Null 相同資料庫術語而言，這表示 「 有任何值 」。)  
  
 `bNull`  
 如果將欄位資料成員標示為已不具有任何值 (Null) 為非零。 否則為 0，表示欄位資料成員會標示為非 Null。  
  
### <a name="remarks"></a>備註  
 當您新增新的記錄至資料錄集時，所有欄位資料成員一開始會設為 Null 值，並標示為 「 中途 」 （變更）。 當您從資料來源擷取一筆記錄時，其資料行已經有值或都是 Null。  
  
> [!NOTE]
>  沒有要使用大量資料列擷取的資料錄集上呼叫此成員函式。 如果您已實作大量資料列擷取，則呼叫`SetFieldNull`導致失敗的判斷提示。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 如果您特別想要將目前記錄的欄位指定為沒有值，呼叫`SetFieldNull`與`bNull`設**TRUE**加上旗標為 Null。 如果先前已將某個欄位標記 Null，而且現在想要將其值，只要設定其新值。 您不需要移除 Null 旗標`SetFieldNull`。 若要判斷此欄位是否可為 Null，請呼叫`IsFieldNullable`。  
  
> [!CAUTION]
>  呼叫此成員函式呼叫之後，才[編輯](#edit)或[AddNew](#addnew)。  
  
 使用**NULL**函式的第一個引數只能套用函式的**outputColumn**欄位中不**param**欄位。 例如，呼叫  
  
 [!code-cpp[NVC_MFCDatabase #&26;](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]  
  
 集合只**outputColumn**欄位**NULL**;**param**欄位不會受到影響。  
  
 若要致力於**param**欄位中，您必須提供個別的實際位址**param**您想要使用，例如︰  
  
 [!code-cpp[NVC_MFCDatabase #&27;](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]  
  
 這表示您無法設定所有**param**欄位**NULL**，您可以使用如**outputColumn**欄位。  
  
> [!NOTE]
>  當參數設定為 Null 時，呼叫`SetFieldNull`資料錄集開啟的結果中判斷提示之前。 在此情況下，呼叫[SetParamNull](#setparamnull)。  
  
 `SetFieldNull`透過實作[DoFieldExchange](#dofieldexchange)。  
  
##  <a name="setlockingmode"></a>CRecordset::SetLockingMode  
 將鎖定模式設定為 「 開放式 」 鎖定 （預設值） 或 「 封閉式 」 鎖定。 決定如何更新鎖定的記錄。  
  
```  
void SetLockingMode(UINT nMode);
```  
  
### <a name="parameters"></a>參數  
 `nMode`  
 從下列值的其中一個**列舉 LockMode**:  
  
- **開放式**開放式鎖定鎖定只有在呼叫期間更新資料錄**更新**。  
  
- **封閉式**封閉式鎖定會鎖定資料錄儘速**編輯**呼叫，它會保持鎖定直到**更新**呼叫完成，或移至新的記錄。  
  
### <a name="remarks"></a>備註  
 如果您需要指定這兩種記錄鎖定的策略使用資料錄集來進行更新，請呼叫此成員函式。 根據預設，資料錄集的鎖定模式是**開放式**。 您可以變更，以更加小心**封閉式**鎖定策略。 呼叫`SetLockingMode`但在建構並開啟資料錄集物件之後才能呼叫**編輯**。  
  
##  <a name="setparamnull"></a>CRecordset::SetParamNull  
 旗標參數，為 Null （特別具有任何值） 或非 Null。  
  
```  
void SetParamNull(
    int nIndex,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 參數之以零為起始的索引。  
  
 `bNull`  
 如果**TRUE** （預設值），將參數標示為 Null。 否則，將參數標示為非 Null。  
  
### <a name="remarks"></a>備註  
 不同於[SetFieldNull](#setfieldnull)，您可以呼叫`SetParamNull`開啟資料錄集之前。  
  
 `SetParamNull`通常使用預先定義的查詢 （預存程序）。  
  
##  <a name="setrowsetcursorposition"></a>CRecordset::SetRowsetCursorPosition  
 將游標移至目前資料列集內的資料列。  
  
```  
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```  
  
### <a name="parameters"></a>參數  
 `wRow`  
 以一為位置的資料列中目前資料列集。 這個值可以介於 1 的資料列集大小。  
  
 `wLockType`  
 值，指出已重新整理之後，鎖定資料列的方式。 如需詳細資料，請參閱＜備註＞。  
  
### <a name="remarks"></a>備註  
 在實作大量資料列擷取時，會擷取記錄的資料列集，其中第一個記錄中擷取的資料列集是目前的記錄。 若要讓資料列集內的另一筆記錄目前的記錄，呼叫`SetRowsetCursorPosition`。 例如，您可以結合`SetRowsetCursorPosition`與[GetFieldValue](#getfieldvalue)成員函式，以動態方式從資料錄集的記錄中擷取資料。  
  
 若要使用`SetRowsetCursorPosition`，您必須藉由指定的大量資料列擷取已實作`CRecordset::useMultiRowFetch`選項`dwOptions`中的參數[開啟](#open)成員函式。  
  
 `SetRowsetCursorPosition`呼叫 ODBC API 函式**SQLSetPos**。 `wLockType`參數會指定資料列之後的鎖定狀態**SQLSetPos**已經執行。 下表說明可能的值為`wLockTyp`e。  
  
|wLockType|描述|  
|---------------|-----------------|  
|`SQL_LOCK_NO_CHANGE`（預設值）|驅動程式或資料來源可確保資料列中相同的鎖定或解除鎖定狀態前`SetRowsetCursorPosition`呼叫。|  
|`SQL_LOCK_EXCLUSIVE`|驅動程式或資料來源以獨佔方式鎖定資料列。 並非所有資料來源都支援這種類型的鎖定。|  
|`SQL_LOCK_UNLOCK`|驅動程式或資料來源會解除鎖定資料列。 並非所有資料來源都支援這種類型的鎖定。|  
  
 如需詳細資訊**SQLSetPos**，請參閱[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="setrowsetsize"></a>CRecordset::SetRowsetSize  
 指定您想要一次擷取中擷取的記錄數目。  
  
```  
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```  
  
### <a name="parameters"></a>參數  
 *dwNewRowsetSize*  
 若要指定提取時擷取的資料列數目。  
  
### <a name="remarks"></a>備註  
 此虛擬成員函式會指定您想要使用大量資料列擷取時，擷取一個單一擷取的資料列數目。 若要實作大量資料列擷取，您必須設定`CRecordset::useMultiRowFetch`選項`dwOptions`參數[開啟](#open)成員函式。  
  
> [!NOTE]
>  呼叫`SetRowsetSize`但不會實作大量資料列擷取將會導致失敗的判斷提示。  
  
 呼叫`SetRowsetSize`之前，先呼叫**開啟**一開始設定資料錄集的資料列集大小。 實作大量資料列擷取時的預設資料列集大小為 25。  
  
> [!NOTE]
>  呼叫時請特別小心`SetRowsetSize`。 如果您以手動方式配置的資料存放區 (依照**CRecordset::userAllocMultiRowBuffers** dwOptions 參數中的選項**開啟**)，您應該檢查您是否需要重新配置存放區的緩衝區之後您呼叫, `SetRowsetSize`，但在執行任何資料指標瀏覽作業之前。  
  
 若要取得資料列集大小的目前設定，請呼叫[GetRowsetSize](#getrowsetsize)。  
  
 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="update"></a>CRecordset::Update  
 完成`AddNew`或**編輯**新增或編輯資料儲存在資料來源上的作業。  
  
```  
virtual BOOL Update();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功更新一筆記錄。否則為 0，如果沒有資料行已變更。 如果更新沒有記錄，或多個更新一筆記錄，則會擲回例外狀況。 例外狀況也會擲回任何其他失敗的資料來源。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式呼叫之後[AddNew](#addnew)或[編輯](#edit)成員函式。 這個呼叫才可完成`AddNew`或**編輯**作業。  
  
> [!NOTE]
>  如果您已實作大量資料列擷取，您不能呼叫**更新**。 這會導致失敗的判斷提示。 雖然類別`CRecordset`不會提供一種機制來更新資料的大量資料列，您可以撰寫自己的函式使用 ODBC API 函式**SQLSetPos**。 如需大量資料列擷取的詳細資訊，請參閱文章[資料錄集︰ 擷取記錄在大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 同時`AddNew`和**編輯**準備儲存至資料來源中的新增或編輯過的資料放在其中編輯緩衝區。 **更新**儲存資料。 只有這些欄位標記，或偵測到變更時都會更新。  
  
 如果資料來源支援交易，您可以將**更新**呼叫 (和其相對應`AddNew`或**編輯**呼叫) 交易的一部分。 如需有關交易的詳細資訊，請參閱文章[交易 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
> [!CAUTION]
>  如果您呼叫**更新**但未先呼叫`AddNew`或**編輯**，**更新**會擲回`CDBException`。 如果您呼叫`AddNew`或**編輯**，您必須呼叫**更新**之前先呼叫**移動**作業或之前關閉資料錄集或資料來源連接。 否則，您的變更都會遺失而不另行通知。  
  
 如需有關處理**更新**失敗，請參閱文章[資料錄集︰ 資料錄集更新資料錄的方式 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。  
  
### <a name="example"></a>範例  
 請參閱文章[交易︰ 資料錄集 (ODBC) 中執行交易](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDatabase 類別](../../mfc/reference/cdatabase-class.md)   
 [CRecordView 類別](../../mfc/reference/crecordview-class.md)

