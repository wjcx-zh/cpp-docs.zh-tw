---
title: CRecordset 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- CRecordset [MFC], CRecordset
- CRecordset [MFC], AddNew
- CRecordset [MFC], CanAppend
- CRecordset [MFC], CanBookmark
- CRecordset [MFC], Cancel
- CRecordset [MFC], CancelUpdate
- CRecordset [MFC], CanRestart
- CRecordset [MFC], CanScroll
- CRecordset [MFC], CanTransact
- CRecordset [MFC], CanUpdate
- CRecordset [MFC], CheckRowsetError
- CRecordset [MFC], Close
- CRecordset [MFC], Delete
- CRecordset [MFC], DoBulkFieldExchange
- CRecordset [MFC], DoFieldExchange
- CRecordset [MFC], Edit
- CRecordset [MFC], FlushResultSet
- CRecordset [MFC], GetBookmark
- CRecordset [MFC], GetDefaultConnect
- CRecordset [MFC], GetDefaultSQL
- CRecordset [MFC], GetFieldValue
- CRecordset [MFC], GetODBCFieldCount
- CRecordset [MFC], GetODBCFieldInfo
- CRecordset [MFC], GetRecordCount
- CRecordset [MFC], GetRowsetSize
- CRecordset [MFC], GetRowsFetched
- CRecordset [MFC], GetRowStatus
- CRecordset [MFC], GetSQL
- CRecordset [MFC], GetStatus
- CRecordset [MFC], GetTableName
- CRecordset [MFC], IsBOF
- CRecordset [MFC], IsDeleted
- CRecordset [MFC], IsEOF
- CRecordset [MFC], IsFieldDirty
- CRecordset [MFC], IsFieldNull
- CRecordset [MFC], IsFieldNullable
- CRecordset [MFC], IsOpen
- CRecordset [MFC], Move
- CRecordset [MFC], MoveFirst
- CRecordset [MFC], MoveLast
- CRecordset [MFC], MoveNext
- CRecordset [MFC], MovePrev
- CRecordset [MFC], OnSetOptions
- CRecordset [MFC], OnSetUpdateOptions
- CRecordset [MFC], Open
- CRecordset [MFC], RefreshRowset
- CRecordset [MFC], Requery
- CRecordset [MFC], SetAbsolutePosition
- CRecordset [MFC], SetBookmark
- CRecordset [MFC], SetFieldDirty
- CRecordset [MFC], SetFieldNull
- CRecordset [MFC], SetLockingMode
- CRecordset [MFC], SetParamNull
- CRecordset [MFC], SetRowsetCursorPosition
- CRecordset [MFC], SetRowsetSize
- CRecordset [MFC], Update
- CRecordset [MFC], m_hstmt
- CRecordset [MFC], m_nFields
- CRecordset [MFC], m_nParams
- CRecordset [MFC], m_pDatabase
- CRecordset [MFC], m_strFilter
- CRecordset [MFC], m_strSort
ms.assetid: dd89a21d-ef39-4aab-891b-1e373d67c855
ms.openlocfilehash: efb833a8d4cc0b801f75951bc648d6b83df5bae8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305181"
---
# <a name="crecordset-class"></a>CRecordset 類別

表示選取自資料來源的資料錄集。

## <a name="syntax"></a>語法

```
class CRecordset : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CRecordset::CRecordset](#crecordset)|建構 `CRecordset` 物件。 您的衍生的類別必須提供呼叫這個建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRecordset::AddNew](#addnew)|準備新增記錄。 呼叫`Update`完成加入。|
|[CRecordset::CanAppend](#canappend)|傳回非零值，如果可以加入新的記錄，透過在資料錄集`AddNew`成員函式。|
|[CRecordset::CanBookmark](#canbookmark)|傳回非零值，如果資料錄集支援書籤。|
|[CRecordset::Cancel](#cancel)|取消非同步作業或從第二個執行緒的程序。|
|[CRecordset::CancelUpdate](#cancelupdate)|取消任何暫止的更新，因為`AddNew`或`Edit`作業。|
|[CRecordset::CanRestart](#canrestart)|傳回非零值如果`Requery`可以呼叫以重新執行資料錄集的查詢。|
|[CRecordset::CanScroll](#canscroll)|傳回非零值，如果可以捲動資料列。|
|[CRecordset::CanTransact](#cantransact)|傳回非零值，如果資料來源支援交易。|
|[CRecordset::CanUpdate](#canupdate)|傳回非零值，如果可以更新資料錄集 （您可以新增、 更新或刪除記錄）。|
|[CRecordset::CheckRowsetError](#checkrowseterror)|呼叫以處理期間提取的記錄產生的錯誤。|
|[CRecordset::Close](#close)|關閉資料錄集，並與它相關聯的 ODBC HSTMT。|
|[CRecordset::Delete](#delete)|從資料錄集刪除目前的記錄。 在刪除之後，您必須明確地捲動至另一筆記錄。|
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|呼叫以交換大量資料列的資料來源的資料錄集的資料。 實作大量資料錄欄位交換 (Bulk RFX)。|
|[CRecordset::DoFieldExchange](#dofieldexchange)|呼叫以交換資料 （雙向） 之間的資料錄集的欄位資料成員和資料來源上對應的記錄。 實作資料錄欄位交換 (RFX)。|
|[CRecordset::Edit](#edit)|準備變更目前的記錄。 呼叫`Update`完成編輯。|
|[CRecordset::FlushResultSet](#flushresultset)|要擷取，使用預先定義的查詢時，設定傳回非零值，如果有另一個結果。|
|[CRecordset::GetBookmark](#getbookmark)|將記錄的書籤值指派給參數物件中。|
|[CRecordset::GetDefaultConnect](#getdefaultconnect)|呼叫以取得預設的連接字串。|
|[CRecordset::GetDefaultSQL](#getdefaultsql)|呼叫以取得預設的 SQL 字串，來執行。|
|[CRecordset::GetFieldValue](#getfieldvalue)|傳回資料錄集中的欄位值。|
|[CRecordset::GetODBCFieldCount](#getodbcfieldcount)|傳回資料錄集中的欄位數目。|
|[CRecordset::GetODBCFieldInfo](#getodbcfieldinfo)|傳回資料錄集中的特定類型的欄位的相關資訊。|
|[CRecordset::GetRecordCount](#getrecordcount)|資料錄集傳回記錄的數目。|
|[CRecordset::GetRowsetSize](#getrowsetsize)|傳回您想要在單一提取時擷取的記錄數目。|
|[CRecordset::GetRowsFetched](#getrowsfetched)|傳回實際擷取期間所擷取的資料列數目。|
|[CRecordset::GetRowStatus](#getrowstatus)|在提取之後傳回資料列的狀態。|
|[CRecordset::GetSQL](#getsql)|取得用來選取資料錄集的資料錄的 SQL 字串。|
|[CRecordset::GetStatus](#getstatus)|取得資料錄集的狀態： 目前的記錄和記錄的最後一個計數是否已取得的索引。|
|[CRecordset::GetTableName](#gettablename)|取得資料錄集所依據之資料表的名稱。|
|[CRecordset::IsBOF](#isbof)|傳回非零值，如果已位置之前的第一個記錄的資料錄集。 沒有目前資料錄。|
|[CRecordset::IsDeleted](#isdeleted)|傳回非零值，如果資料錄集位於已刪除的資料錄。|
|[CRecordset::IsEOF](#iseof)|傳回非零值，如果已位置之後的最後一個記錄的資料錄集。 沒有目前資料錄。|
|[CRecordset::IsFieldDirty](#isfielddirty)|傳回非零值，如果目前的記錄中指定的欄位已變更。|
|[CRecordset::IsFieldNull](#isfieldnull)|傳回非零值，如果目前的記錄中指定的欄位為 null （沒有任何值）。|
|[CRecordset::IsFieldNullable](#isfieldnullable)|傳回非零值，如果目前的記錄中指定的欄位可以設定為 null （具有任何值）。|
|[CRecordset::IsOpen](#isopen)|傳回非零值如果`Open`先前已呼叫。|
|[CRecordset::Move](#move)|將指定的記錄數的資料錄集，從任一方向中目前的記錄。|
|[CRecordset::MoveFirst](#movefirst)|您可以將目前資料錄置於資料錄集的第一個記錄。 測試`IsBOF`第一次。|
|[CRecordset::MoveLast](#movelast)|在最後一筆資料錄或最後一個資料列集上，請將目前的記錄。 測試`IsEOF`第一次。|
|[CRecordset::MoveNext](#movenext)|在下一筆記錄或下一個資料列集上，請將目前的記錄。 測試`IsEOF`第一次。|
|[CRecordset::MovePrev](#moveprev)|在上一筆記錄或前一個資料列集上，請將目前的記錄。 測試`IsBOF`第一次。|
|[CRecordset::OnSetOptions](#onsetoptions)|針對指定的 ODBC 陳述式，以呼叫設定選項 （選取項目上使用）。|
|[CRecordset::OnSetUpdateOptions](#onsetupdateoptions)|呼叫以指定的 ODBC 陳述式設定選項 （使用 update）。|
|[CRecordset::Open](#open)|開啟資料錄集擷取的資料表，或執行查詢，表示資料錄集。|
|[CRecordset::RefreshRowset](#refreshrowset)|重新整理的資料和狀態的指定資料列。|
|[CRecordset::Requery](#requery)|執行一次重新整理選取的資料錄的資料錄集的查詢。|
|[CRecordset::SetAbsolutePosition](#setabsoluteposition)|您可以將資料錄集置於對應至指定的記錄數目的記錄。|
|[CRecordset::SetBookmark](#setbookmark)|您可以將資料錄集置於書籤所指定的記錄。|
|[CRecordset::SetFieldDirty](#setfielddirty)|為已變更，請將標記在目前的記錄中指定的欄位。|
|[CRecordset::SetFieldNull](#setfieldnull)|設定為 null （具有任何值） 是目前記錄中的指定欄位的值。|
|[CRecordset::SetLockingMode](#setlockingmode)|設定 「 開放式 」 鎖定 （預設值） 或 「 封閉式 」 鎖定的鎖定模式。 決定如何更新鎖定的記錄。|
|[CRecordset::SetParamNull](#setparamnull)|將指定的參數設定為 null （具有任何值）。|
|[CRecordset::SetRowsetCursorPosition](#setrowsetcursorposition)|您可以將資料指標置於指定的資料列集中的資料列。|
|[CRecordset::SetRowsetSize](#setrowsetsize)|指定您想要擷取期間所擷取的記錄數目。|
|[CRecordset::Update](#update)|完成`AddNew`或`Edit`藉由將新的或修改資料儲存在資料來源上的作業。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CRecordset::m_hstmt](#m_hstmt)|包含資料錄集的 ODBC 陳述式控制代碼。 輸入 `HSTMT`。|
|[CRecordset::m_nFields](#m_nfields)|包含資料錄集中的欄位資料成員的數目。 輸入 `UINT`。|
|[CRecordset::m_nParams](#m_nparams)|包含參數的資料錄集中的資料成員的數目。 輸入 `UINT`。|
|[CRecordset::m_pDatabase](#m_pdatabase)|包含一個指向`CDatabase`透過此資料錄集連接到資料來源的物件。|
|[CRecordset::m_strFilter](#m_strfilter)|包含`CString`，指定結構化查詢語言 (SQL)`WHERE`子句。 用做為篩選條件來選取只在符合特定準則的記錄。|
|[CRecordset::m_strSort](#m_strsort)|包含`CString`，指定 SQL`ORDER BY`子句。 用來控制如何排序記錄。|

## <a name="remarks"></a>備註

稱為 「 資料錄集，「`CRecordset`物件通常用於兩種形式： 動態集和快照集。 動態集保持同步的與其他使用者所做的資料更新。 快照集是資料的靜態檢視。 每個表單代表一組固定在開啟資料錄集時的時間的記錄，但當您捲動中動態集的記錄時，它會反映之後所做的變更記錄，其他使用者或應用程式中的其他資料錄集。

> [!NOTE]
>  如果您正在使用的資料存取物件 (DAO) 類別，而不是開放式資料庫連接 (ODBC) 類別，使用類別[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)改。 如需詳細資訊，請參閱文章[概觀：資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。

若要使用資料錄集的其中一種，您通常衍生應用程式特定資料錄集類別從`CRecordset`。 資料錄集選取資料來源的記錄，然後您可以：

- 捲動資料列。

- 更新的記錄，並指定鎖定模式。

- 篩選資料錄集來限制它選取，從可用資料來源的記錄。

- 排序資料錄集。

- 參數化資料錄集，以自訂其選取項目之後執行階段才知道的資訊。

若要使用您的類別，開啟資料庫，並建構資料錄集物件，並傳遞建構函式的指標，您`CDatabase`物件。 然後呼叫資料錄集的`Open`成員函式，其中您可以指定物件是否為動態集或快照集。 呼叫`Open`選取資料來源中的資料。 開啟資料錄集物件之後，使用其成員函式和資料成員來捲動瀏覽記錄，並在其上操作。 可用的作業取決於該物件是動態集或快照集，是否可更新或唯讀狀態 （這取決於開放式資料庫連接 (ODBC) 資料來源的功能，） 以及您是否有實作大量資料列擷取。 若要重新整理記錄可能會變更或新增，因為`Open`呼叫，呼叫物件的`Requery`成員函式。 呼叫物件的`Close`成員函式，並使用它完成時終結物件。

在衍生`CRecordset`類別中，資料錄欄位交換 (RFX) 或大量資料錄欄位交換 (Bulk RFX) 用來支援讀取及更新的記錄欄位。

如需有關資料錄集和記錄欄位交換的詳細資訊，請參閱文章[概觀：資料庫程式設計](../../data/data-access-programming-mfc-atl.md)，[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)，[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)，並[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。 著重於動態集和快照集，請參閱文章[動態](../../data/odbc/dynaset.md)並[快照集](../../data/odbc/snapshot.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>需求

**標頭：** afxdb.h

##  <a name="addnew"></a>  CRecordset::AddNew

準備將新記錄新增至資料表。

```
virtual void AddNew();
```

### <a name="remarks"></a>備註

您必須呼叫[Requery](#requery)成員函式，以查看新加入的記錄。 記錄的欄位是一開始是 Null。 （在資料庫術語中，Null 」 有任何值 」 的方式，而且不是 NULL，c + + 中相同）。若要完成此作業，您必須呼叫[更新](#update)成員函式。 `Update` 將您的變更儲存至資料來源。

> [!NOTE]
>  如果您已實作大量資料列擷取，您不能呼叫`AddNew`。 這會導致失敗的判斷提示。 雖然類別`CRecordset`不會提供一個機制來更新資料的大量資料列，您可以撰寫自己的函式使用 ODBC API 函式`SQLSetPos`。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

`AddNew` 準備新的空白記錄使用資料錄集的欄位資料成員。 在您呼叫後`AddNew`，在資料錄集的欄位資料成員中設定您想要的值。 (您沒有呼叫[編輯](#edit)成員函式，針對此目的; 使用`Edit`僅為現有記錄。)當您後續呼叫`Update`、 已變更的欄位資料成員中的值會儲存在資料來源。

> [!CAUTION]
>  如果您捲動至新的記錄才能呼叫`Update`、 新的記錄會遺失，而且會提供任何警告。

如果資料來源支援交易，您可以讓您`AddNew`呼叫交易的一部分。 如需有關交易的詳細資訊，請參閱類別[CDatabase](../../mfc/reference/cdatabase-class.md)。 請注意，您應該呼叫[CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans)再呼叫`AddNew`。

> [!NOTE]
>  對於動態集，新的記錄會加入至資料錄集做為最後一筆記錄。 已新增的記錄不會加入至快照集;您必須呼叫`Requery`重新整理資料錄集。

它是不合法呼叫`AddNew`的資料錄集其`Open`尚未呼叫成員函式。 A`CDBException`如果您呼叫會擲回`AddNew`以無法附加至資料錄集。 您可以判斷資料錄集是否可更新，藉由呼叫[CanAppend](#canappend)。

如需詳細資訊，請參閱下列文章：[資料錄集：資料錄集更新資料錄 (ODBC) 的方式](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)，[資料錄集：新增、 更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)，並[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。

### <a name="example"></a>範例

請參閱文章[交易：執行異動 (ODBC) 資料錄集中](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。

##  <a name="canappend"></a>  CRecordset::CanAppend

決定是否先前開啟的資料錄集可讓您新增新的記錄。

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>傳回值

如果資料錄集可讓您可新增新記錄; 為非零否則為 0。 `CanAppend` 如果您開啟資料錄集，以唯讀模式時，就會傳回 0。

##  <a name="canbookmark"></a>  CRecordset::CanBookmark

決定是否資料錄集可讓您將使用書籤的記錄標示。

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>傳回值

非零值，如果資料錄集支援書籤 」;否則為 0。

### <a name="remarks"></a>備註

此函式都無關`CRecordset::useBookmarks`選項*dwOptions*參數[開啟](#open)成員函式。 `CanBookmark` 指出指定的 ODBC 驅動程式和資料指標類型支援書籤。 `CRecordset::useBookmarks` 指出提供支援這些書籤是否可用。

> [!NOTE]
>  順向資料錄集不支援書籤。

如需書籤和資料錄集瀏覽的詳細資訊，請參閱文章[資料錄集：書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[資料錄集：捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="cancel"></a>  CRecordset::Cancel

資料來源取消非同步作業進行中的或從第二個執行緒的處理序的要求。

```
void Cancel();
```

### <a name="remarks"></a>備註

請注意，MFC ODBC 類別不會再使用非同步處理;若要執行的非同步作業，您必須直接呼叫 ODBC API 函式`SQLSetConnectOption`。 如需詳細資訊，請參閱 「 非同步執行函式 」 主題中*ODBC SDK 程式設計人員指南*。

##  <a name="cancelupdate"></a>  CRecordset::CancelUpdate

取消任何暫止的更新，因[編輯](#edit)或是[AddNew](#addnew)作業之前,[更新](#update)稱為。

```
void CancelUpdate();
```

### <a name="remarks"></a>備註

> [!NOTE]
>  此成員函式不適用於使用大量資料列擷取，因為無法呼叫這類資料錄集的資料錄集`Edit`， `AddNew`，或`Update`。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

如果已啟用自動變更欄位檢查，`CancelUpdate`會還原為之前的值的成員變數`Edit`或`AddNew`已呼叫; 否則會保留任何值變更。 根據預設，自動欄位啟用檢查開啟資料錄集時。 若要停用，您必須指定`CRecordset::noDirtyFieldCheck`中*dwOptions*參數[開啟](#open)成員函式。

如需有關更新資料的詳細資訊，請參閱[資料錄集：新增、 更新和刪除資料錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。

##  <a name="canrestart"></a>  CRecordset::CanRestart

決定資料錄集是否允許重新啟動其查詢 （若要重新整理其記錄），藉由呼叫`Requery`成員函式。

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>傳回值

非零值，如果允許重新查詢;否則為 0。

##  <a name="canscroll"></a>  CRecordset::CanScroll

決定是否允許捲動的資料錄集。

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>傳回值

非零值，如果資料錄集允許捲動;否則為 0。

### <a name="remarks"></a>備註

如需捲動的詳細資訊，請參閱文章[資料錄集：捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="cantransact"></a>  CRecordset::CanTransact

決定資料錄集是否允許交易。

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>傳回值

非零值，如果資料錄集可讓交易;否則為 0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱文章[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。

##  <a name="canupdate"></a>  CRecordset::CanUpdate

決定是否可以更新資料錄集。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>傳回值

非零值，如果可以更新資料錄集;否則為 0。

### <a name="remarks"></a>備註

資料錄集可能會處於唯讀模式，如果基礎資料來源是唯讀的或者如果指定`CRecordset::readOnly`中*dwOptions*開啟資料錄集時的參數。

##  <a name="checkrowseterror"></a>  CRecordset::CheckRowsetError

呼叫以處理期間提取的記錄產生的錯誤。

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>參數

*nRetCode*<br/>
ODBC API 函式會傳回碼。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

此虛擬成員函式會處理時擷取的記錄，會發生的錯誤和大量資料列擷取期間會很有用。 您可能要考慮覆寫`CheckRowsetError`來實作您自己的錯誤處理。

`CheckRowsetError` 自動在中，稱為游標巡覽作業，例如`Open`， `Requery`，或有任何`Move`作業。 它會傳遞 ODBC API 函式的傳回值`SQLExtendedFetch`。 下表列出可能的值為*nRetCode*參數。

|nRetCode|描述|
|--------------|-----------------|
|SQL_SUCCESS|順利完成的函式不未提供任何額外的資訊。|
|SQL_SUCCESS_WITH_INFO|已順利完成，可能發生非嚴重錯誤的函式。 可取得其他資訊，請呼叫`SQLError`。|
|SQL_NO_DATA_FOUND|已經提取從結果集中的所有資料列。|
|SQL_ERROR|失敗函式。 可取得其他資訊，請呼叫`SQLError`。|
|SQL_INVALID_HANDLE|函式失敗，因為無效的環境控制代碼、 連接控制代碼或陳述式控制代碼。 這會指出程式設計錯誤。 會提供任何額外的資訊`SQLError`。|
|SQL_STILL_EXECUTING|以非同步方式啟動的函式仍在執行中。 請注意，根據預設，MFC 將永遠不會將此值傳遞至`CheckRowsetError`;MFC 會繼續呼叫`SQLExtendedFetch`直到不再傳回 SQL_STILL_EXECUTING。|

如需詳細資訊`SQLError`，請參閱 Windows SDK。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="close"></a>  CRecordset::Close

關閉資料錄集。

```
virtual void Close();
```

### <a name="remarks"></a>備註

ODBC HSTMT 及所有的記憶體配置資料錄集的架構會解除配置。 通常在呼叫後`Close`，您會刪除 c + + 資料錄集物件，如果配置與**新**。

您可以呼叫`Open`呼叫之後，再次`Close`。 這可讓您重複使用的資料錄集物件。 替代方法是呼叫`Requery`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

##  <a name="crecordset"></a>  CRecordset::CRecordset

建構 `CRecordset` 物件。

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>參數

*pDatabase*<br/>
包含一個指向`CDatabase`物件或 NULL 值。 如果不是 NULL，`CDatabase`物件的`Open`不將它連接到資料來源呼叫成員函式，以開啟它進行您在自己的資料錄集嘗試`Open`呼叫。 如果您傳遞 NULL，`CDatabase`物件是建構，而且連線，讓您使用您指定當您衍生您的資料錄集類別與 ClassWizard 的資料來源資訊。

### <a name="remarks"></a>備註

您可以使用`CRecordset`直接衍生應用程式特定類別或`CRecordset`。 您可以使用 ClassWizard 衍生您的資料錄集類別。

> [!NOTE]
>  在衍生的類別*必須*提供它自己的建構函式。 在衍生類別的建構函式，呼叫建構函式`CRecordset::CRecordset`，將適當的參數，以及傳遞給它。

將 NULL 傳遞至您的資料錄集建構函式有`CDatabase`物件建構，並為您自動連接。 這是很有用的速記，其不需要您建構，並連接`CDatabase`才能建構資料錄集物件。

### <a name="example"></a>範例

如需詳細資訊，請參閱文章[資料錄集：宣告的類別 (ODBC) 的資料表](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。

##  <a name="delete"></a>  CRecordset::Delete

刪除目前的記錄。

```
virtual void Delete();
```

### <a name="remarks"></a>備註

成功刪除後，資料錄集的欄位資料成員會設為 Null 值，而且您必須明確呼叫的其中一個`Move`函式，才能移出已刪除的資料錄。 一旦您移出已刪除的資料錄時，不能傳回它。 如果資料來源支援交易，您可以進行`Delete`呼叫交易的一部分。 如需詳細資訊，請參閱文章[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。

> [!NOTE]
>  如果您已實作大量資料列擷取，您不能呼叫`Delete`。 這會導致失敗的判斷提示。 雖然類別`CRecordset`不會提供一個機制來更新資料的大量資料列，您可以撰寫自己的函式使用 ODBC API 函式`SQLSetPos`。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

> [!CAUTION]
>  資料錄集必須能夠更新，而且必須有有效的記錄資料錄集中目前當您呼叫`Delete`; 否則就會發生錯誤。 比方說，如果您刪除的記錄，但不是會捲動至新的記錄才能呼叫`Delete`再次`Delete`就會擲回[CDBException](../../mfc/reference/cdbexception-class.md)。

不同於[AddNew](#addnew)並[編輯](#edit)，來呼叫`Delete`後面沒有呼叫[更新](#update)。 如果`Delete`呼叫失敗，欄位資料成員則會保留不變。

### <a name="example"></a>範例

這個範例示範建立函式的框架上的資料錄集。 此範例假設存在`m_dbCust`，類型的成員變數`CDatabase`已經連接到資料來源。

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

##  <a name="dobulkfieldexchange"></a>  CRecordset::DoBulkFieldExchange

呼叫以交換大量資料列的資料來源的資料錄集的資料。 實作大量資料錄欄位交換 (Bulk RFX)。

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指標[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件。 架構將已經有設定此物件來指定欄位交換作業的內容。

### <a name="remarks"></a>備註

實作大量資料列擷取時，架構會呼叫此成員函式，將會自動從資料來源的資料傳送至您的資料錄集物件。 `DoBulkFieldExchange` 也會繫結參數資料成員，如果有的話，資料錄集的選取範圍的 SQL 陳述式字串中參數預留位置。

如果未實作大量資料列擷取，架構會呼叫[DoFieldExchange](#dofieldexchange)。 若要實作大量資料列擷取，您必須指定`CRecordset::useMultiRowFetch`的選項*dwOptions*中的參數[開啟](#open)成員函式。

> [!NOTE]
> `DoBulkFieldExchange` 您會使用衍生自的類別時，才會提供`CRecordset`。 如果您已建立的資料錄集物件，直接從`CRecordset`，您必須呼叫[GetFieldValue](#getfieldvalue)成員函式來擷取資料。

大量資料錄欄位交換 (Bulk RFX) 是類似於資料錄欄位交換 (RFX)。 資料會自動從資料來源轉移至資料錄集物件。 不過，您無法呼叫`AddNew`， `Edit`， `Delete`，或`Update`傳送回資料來源的變更。 類別`CRecordset`目前不提供機制，以更新大量資料列的資料; 不過，您可以撰寫自己的函式使用 ODBC API 函式`SQLSetPos`。

請注意，ClassWizard 不支援大量資料錄欄位交換;因此，您必須覆寫`DoBulkFieldExchange`以手動方式是藉由撰寫 Bulk RFX 函式的呼叫。 如需有關這些函式的詳細資訊，請參閱主題[記錄欄位交換函式](../../mfc/reference/record-field-exchange-functions.md)。

如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 如需相關資訊，請參閱文章[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。

##  <a name="dofieldexchange"></a>  CRecordset::DoFieldExchange

呼叫以交換資料 （雙向） 之間的資料錄集的欄位資料成員和資料來源上對應的記錄。 實作資料錄欄位交換 (RFX)。

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指標[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件。 架構將已經有設定此物件來指定欄位交換作業的內容。

### <a name="remarks"></a>備註

當未實作大量資料列擷取時，則架構會呼叫此成員函式，來自動交換您的資料錄集物件的欄位資料成員與對應的資料行的資料來源上目前的記錄之間的資料。 `DoFieldExchange` 也會繫結參數資料成員，如果有的話，資料錄集的選取範圍的 SQL 陳述式字串中參數預留位置。

如果實作大量資料列擷取時，架構會呼叫[DoBulkFieldExchange](#dobulkfieldexchange)。 若要實作大量資料列擷取，您必須指定`CRecordset::useMultiRowFetch`的選項*dwOptions*中的參數[開啟](#open)成員函式。

> [!NOTE]
> `DoFieldExchange` 您會使用衍生自的類別時，才會提供`CRecordset`。 如果您已建立的資料錄集物件，直接從`CRecordset`，您必須呼叫[GetFieldValue](#getfieldvalue)成員函式來擷取資料。

交換欄位資料，稱為 「 資料錄欄位交換 (RFX)，可以雙向運作： 從資料錄集物件的欄位資料成員的資料來源上的資料錄的欄位和資料來源的資料錄集物件上的記錄。

唯一的動作，您通常必須採取來實作`DoFieldExchange`對於您衍生的資料錄集類別是建立具有 ClassWizard 類別，並指定欄位資料成員的名稱和資料型別。 您也可能會加入程式碼功能 ClassWizard 寫入至指定的參數資料成員，或處理動態繫結的任何資料行。 如需詳細資訊，請參閱文章[資料錄集：動態繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

當您宣告 ClassWizard 您衍生的資料錄集類別時，精靈會將覆寫`DoFieldExchange`，類似下列的範例：

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

如需 RFX 函式的詳細資訊，請參閱主題[記錄欄位交換函式](../../mfc/reference/record-field-exchange-functions.md)。

如需進一步的範例和詳細`DoFieldExchange`，請參閱文章[資料錄欄位交換：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。 如需 RFX 的一般資訊，請參閱文章[資料錄欄位交換](../../data/odbc/record-field-exchange-rfx.md)。

##  <a name="edit"></a>  CRecordset::Edit

允許變更目前的記錄。

```
virtual void Edit();
```

### <a name="remarks"></a>備註

在您呼叫後`Edit`，您可以藉由直接重設其值變更的欄位資料成員。 在作業完成時，接著再呼叫[更新](#update)，將變更儲存在資料來源上的成員函式。

> [!NOTE]
>  如果您已實作大量資料列擷取，您不能呼叫`Edit`。 這會導致失敗的判斷提示。 雖然類別`CRecordset`不會提供一個機制來更新資料的大量資料列，您可以撰寫自己的函式使用 ODBC API 函式`SQLSetPos`。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

`Edit` 將儲存的資料錄集的資料成員的值。 如果您呼叫`Edit`，進行變更，然後呼叫`Edit`同樣地，將記錄的值還原為之前，先`Edit`呼叫。

在某些情況下，您可能想要更新的資料行，以便為 Null （包含任何資料）。 若要這樣做，請呼叫[SetFieldNull](#setfieldnull)搭配參數標記的欄位為 Null; true 這也會導致要更新的資料行。 如果您想要的欄位寫入至資料來源，即使它的值尚未變更，請呼叫[SetFieldDirty](#setfielddirty)搭配 TRUE 參數。 就算欄位具有 Null 值。

如果資料來源支援交易，您可以進行`Edit`呼叫交易的一部分。 請注意，您應該呼叫[CDatabase::BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans)再呼叫`Edit`及開啟資料錄集之後。 也請注意，呼叫[CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)不能取代呼叫`Update`完成`Edit`作業。 如需有關交易的詳細資訊，請參閱類別[CDatabase](../../mfc/reference/cdatabase-class.md)。

根據目前的鎖定模式，正在更新的記錄可能被鎖住`Edit`直到您呼叫`Update`或捲動到另一筆記錄，或可能只有在已鎖定`Edit`呼叫。 您可以變更的鎖定模式[SetLockingMode](#setlockingmode)。

如果您捲動至新的記錄，然後再呼叫，會還原先前的值，目前資料錄`Update`。 A`CDBException`如果您呼叫會擲回`Edit`無法更新資料錄集，或如果沒有目前資料錄。

如需詳細資訊，請參閱文章[異動 (ODBC)](../../data/odbc/transaction-odbc.md)和[資料錄集：鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

##  <a name="flushresultset"></a>  CRecordset::FlushResultSet

如果有多個結果集，請擷取下一個結果集的預先定義的查詢 （預存程序）。

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>傳回值

要擷取; 的多個結果集時，非零值。否則為 0。

### <a name="remarks"></a>備註

您應該呼叫`FlushResultSet`只時完成目前的結果集資料指標。 請注意，當您擷取下一個結果集藉由呼叫`FlushResultSet`，該結果集資料指標無效; 您應該呼叫[MoveNext](#movenext)成員函式之後呼叫`FlushResultSet`。

如果輸出參數或輸入/輸出參數，則會使用預先定義的查詢，您必須呼叫`FlushResultSet`直到傳回`FALSE`（值 0），以取得這些參數值。

`FlushResultSet` 呼叫 ODBC API 函式`SQLMoreResults`。 如果`SQLMoreResults`會傳回 SQL_ERROR 或 SQL_INVALID_HANDLE，然後`FlushResultSet`將會擲回例外狀況。 如需詳細資訊`SQLMoreResults`，請參閱 Windows SDK。

您的預存程序必須有繫結欄位，如果您想要呼叫`FlushResultSet`。

### <a name="example"></a>範例

下列程式碼會假設`COutParamRecordset`是`CRecordset`-衍生的物件，根據預先定義的查詢，使用輸入的參數和一個 output 參數，而多個結果集。 附註的結構[DoFieldExchange](#dofieldexchange)覆寫。

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

##  <a name="getbookmark"></a>  CRecordset::GetBookmark

取得目前資料錄的書籤值。

```
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>參數

*varBookmark*<br/>
參考[CDBVariant](../../mfc/reference/cdbvariant-class.md)物件，表示目前的記錄上的書籤。

### <a name="remarks"></a>備註

若要判斷是否在資料錄集上支援書籤，請呼叫[CanBookmark](#canbookmark)。 若要提供並支援書籤，您必須設定`CRecordset::useBookmarks`選項*dwOptions*參數[開啟](#open)成員函式。

> [!NOTE]
>  如果書籤不受支援或無法使用，呼叫`GetBookmark`會導致擲回例外狀況。 順向資料錄集不支援書籤。

`GetBookmark` 將目前記錄的書籤的值指派`CDBVariant`物件。 若要移至不同的記錄之後，隨時回到該記錄，請呼叫[SetBookmark](#setbookmark)具有對應`CDBVariant`物件。

> [!NOTE]
>  特定資料錄集作業之後，書籤可能不再有效。 例如，如果您呼叫`GetBookmark`後面接著`Requery`，您可能無法傳回的記錄`SetBookmark`。 呼叫[CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)若要檢查您是否能安全地呼叫`SetBookmark`。

如需書籤和資料錄集瀏覽的詳細資訊，請參閱文章[資料錄集：書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[資料錄集：捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="getdefaultconnect"></a>  CRecordset::GetDefaultConnect

呼叫以取得預設的連接字串。

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>傳回值

A `CString` ，其中包含預設的連接字串。

### <a name="remarks"></a>備註

架構會呼叫此成員函式，以取得資料錄集所依據的資料來源的預設連接字串。 ClassWizard 會為您實作此函式，藉由識別相同的資料來源中 ClassWizard 用以取得資料表和資料行的相關資訊。 您可能會發現它方便依賴此開發您的應用程式時的預設連線。 但可能不適合您的應用程式的使用者預設的連線。 如果是這樣，您應該實作此函式，並捨棄 ClassWizard 的版本。 如需有關連接字串的詳細資訊，請參閱[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)。

##  <a name="getdefaultsql"></a>  CRecordset::GetDefaultSQL

呼叫以取得預設的 SQL 字串，來執行。

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>傳回值

A `CString` ，其中包含預設的 SQL 陳述式。

### <a name="remarks"></a>備註

架構會呼叫此成員函式，以取得資料錄集所依據的預設 SQL 陳述式。 這可能是資料表名稱或 SQL**選取**陳述式。

您藉由宣告 ClassWizard，您的資料錄集類別，間接定義預設的 SQL 陳述式及 ClassWizard 會為您執行這項工作。

如果您需要的 SQL 陳述式字串供自己使用時，呼叫`GetSQL`，它會傳回用來選取資料錄集的記錄，它已開啟時的 SQL 陳述式。 您可以編輯您的類別覆寫中的預設 SQL 字串`GetDefaultSQL`。 例如，您可以指定預先定義的查詢，使用呼叫**呼叫**陳述式。 (請注意，不過，如果您編輯`GetDefaultSQL`，您還需要修改`m_nFields`以符合資料來源中的資料行的數目。)

如需詳細資訊，請參閱文章[資料錄集：宣告的類別 (ODBC) 的資料表](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。

> [!CAUTION]
>  資料表名稱會是空白如果架構無法識別資料表名稱，如果提供多個資料表名稱，或如果**呼叫**無法解譯陳述式。 請注意，當使用**呼叫**陳述式中，您必須插入大括號之間的空白字元和**呼叫**關鍵字，也應該將之前的大括號前後的空白字元**選取 **中的關鍵字**選取**陳述式。

##  <a name="getfieldvalue"></a>  CRecordset::GetFieldValue

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

*lpszName*<br/>
欄位名稱。

*varValu*e 的參考[CDBVariant](../../mfc/reference/cdbvariant-class.md)將儲存欄位值的物件。

*nFieldType*<br/>
ODBC C 資料類型的欄位。 使用預設值，而 DEFAULT_FIELD_TYPE，強制`GetFieldValue`決定 C 資料類型，從 SQL 資料類型，根據下表。 否則，您可以在其中指定資料直接輸入，或選擇相容資料類型;例如，您可以儲存任何資料類型劃分為 SQL_C_CHAR。

|C 資料類型|SQL 資料類型|
|-----------------|-------------------|
|SQL_C_BIT|SQL_BIT|
|SQL_C_UTINYINT|SQL_TINYINT|
|SQL_C_SSHORT|SQL_SMALLINT|
|SQL_C_SLONG|SQL_INTEGER|
|SQL_C_FLOAT|SQL_REAL|
|SQL_C_DOUBLE|SQL_FLOATSQL_DOUBLE|
|SQL_C_TIMESTAMP|SQL_DATESQL_TIMESQL_TIMESTAMP|
|SQL_C_CHAR|SQL_NUMERICSQL_DECIMALSQL_BIGINTSQL_CHARSQL_VARCHARSQL_LONGVARCHAR|
|SQL_C_BINARY|SQL_BINARYSQL_VARBINARYSQL_LONGVARBINARY|

如需 ODBC 資料類型的詳細資訊，請參閱 < SQL 資料類型 > 和附錄 D 的 Windows sdk 中的 < C 資料類型 > 主題。

*nIndex*<br/>
欄位的以零為起始的索引。

*strValue*<br/>
參考[CString](../../atl-mfc-shared/reference/cstringt-class.md)將儲存欄位值的物件轉換成文字，不論欄位的資料類型。

### <a name="remarks"></a>備註

您可以查閱欄位，依名稱或索引。 您可以將欄位值儲存在其中一個`CDBVariant`物件或`CString`物件。

如果您已實作大量資料列擷取，目前的記錄永遠會放置在資料列集中的第一筆記錄。 若要使用`GetFieldValue`上指定的資料列集內的記錄，您必須先呼叫[SetRowsetCursorPosition](#setrowsetcursorposition)成員函式，將游標移至所需的資料列，該資料列集內。 然後呼叫`GetFieldValue`該資料列。 若要實作大量資料列擷取，您必須指定`CRecordset::useMultiRowFetch`的選項*dwOptions*中的參數[開啟](#open)成員函式。

您可以使用`GetFieldValue`動態擷取欄位，在執行的階段，而不是以靜態方式將它們繫結在設計階段。 例如，如果您已經宣告直接從資料錄集物件`CRecordset`，您必須使用`GetFieldValue`擷取欄位資料，資料錄欄位交換 (RFX) 或大量資料錄欄位交換 (Bulk RFX) 尚未實作。

> [!NOTE]
>  如果您宣告的資料錄集物件，而不需要衍生自`CRecordset`，不需要載入 ODBC 資料指標程式庫。 資料指標程式庫，必須具備資料錄集至少一個繫結的資料行;不過，當您使用`CRecordset`直接的資料行都繫結。 成員函式[CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex)並[Openex](../../mfc/reference/cdatabase-class.md#open)控制是否將載入的資料指標程式庫。

`GetFieldValue` 呼叫 ODBC API 函式`SQLGetData`。 如果您的驅動程式輸出的欄位值的實際長度的值 SQL_NO_TOTAL`GetFieldValue`會擲回例外狀況。 如需詳細資訊`SQLGetData`，請參閱 Windows SDK。

### <a name="example"></a>範例

下列範例程式碼說明如何呼叫`GetFieldValue`的資料錄集物件宣告直接從`CRecordset`。

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
>  不同於 DAO 類別`CDaoRecordset`，`CRecordset`沒有`SetFieldValue`成員函式。 如果您建立的物件，直接從`CRecordset`，它是有效唯讀的。

如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="getodbcfieldcount"></a>  CRecordset::GetODBCFieldCount

擷取資料錄集物件中的欄位的總數。

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>傳回值

資料錄集中的欄位數目。

### <a name="remarks"></a>備註

如需有關如何建立資料錄集的詳細資訊，請參閱[資料錄集：建立和關閉資料錄集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。

##  <a name="getodbcfieldinfo"></a>  CRecordset::GetODBCFieldInfo

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

*lpszName*<br/>
欄位名稱。

*fieldinfo*<br/>
參考`CODBCFieldInfo`結構。

*nIndex*<br/>
欄位的以零為起始的索引。

### <a name="remarks"></a>備註

一個版本的函式可讓您依名稱查閱欄位。 另一個版本可讓您依索引查閱欄位。

如需描述傳回的資訊，請參閱[CODBCFieldInfo](../../mfc/reference/codbcfieldinfo-structure.md)結構。

如需有關如何建立資料錄集的詳細資訊，請參閱[資料錄集：建立和關閉資料錄集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。

##  <a name="getrecordcount"></a>  CRecordset::GetRecordCount

判斷資料錄集的大小。

```
long GetRecordCount() const;
```

### <a name="return-value"></a>傳回值

資料錄集; 中的記錄數目0，表示資料錄集不包含任何記錄中;或如果無法判別的記錄計數-1。

### <a name="remarks"></a>備註

> [!CAUTION]
>  記錄計數會維護為 「 上限標準，「 最高編號的記錄，但視為使用者通過記錄。 使用者動作已超越最後一筆記錄之後才知道的資料錄總數。 基於效能考量，計數會不時更新您呼叫`MoveLast`。 若要把自己算記錄，呼叫`MoveNext`重複直到`IsEOF`傳回非零值。 新增記錄，以透過`CRecordset:AddNew`並`Update`增加計數; 刪除透過記錄`CRecordset::Delete`減少計數。

##  <a name="getrowsetsize"></a>  CRecordset::GetRowsetSize

取得目前的設定，您想要在指定 fetch 期間擷取的資料列數目。

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>傳回值

擷取給定的擷取期間的資料列數目。

### <a name="remarks"></a>備註

如果您使用大量資料列擷取，開啟資料錄集時，才會進行預設資料列集大小會是 25;否則，便為 1。

若要實作大量資料列擷取，您必須指定`CRecordset::useMultiRowFetch`選項*dwOptions*參數[開啟](#open)成員函式。 若要變更資料列集大小設定，請呼叫[SetRowsetSize](#setrowsetsize)。

如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="getrowsfetched"></a>  CRecordset::GetRowsFetched

決定在提取之後實際擷取的多少筆記錄。

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>傳回值

在指定的提取之後，從資料來源擷取的資料列數目。

### <a name="remarks"></a>備註

當您已實作大量資料列擷取時，這非常有用。 資料列集大小通常表示會從提取; 擷取多少資料列不過，在資料錄集的資料列的總數也會影響多少資料列將擷取的資料列集內。 例如，如果您的資料錄集有資料列集大小設定為 4 的 10 筆記錄，然後循環使用資料錄集藉由呼叫`MoveNext`會導致最後一個資料列集，並具有只有 2 筆記錄。

若要實作大量資料列擷取，您必須指定`CRecordset::useMultiRowFetch`選項*dwOptions*參數[開啟](#open)成員函式。 若要指定資料列集大小，請呼叫[SetRowsetSize](#setrowsetsize)。

如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

##  <a name="getrowstatus"></a>  CRecordset::GetRowStatus

取得目前的資料列集中的資料列的狀態。

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>參數

*wRow*<br/>
以一為基的一個資料列中位置的目前資料列集。 此值的資料列集大小範圍從 1。

### <a name="return-value"></a>傳回值

資料列的狀態值。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

`GetRowStatus` 傳回值，指出其中一個資料列的狀態中的任何變更，因為它是最後一個擷取從資料來源，或沒有資料列對應至*wRow*擷取。 下表列出可能的傳回值。

|狀態值|描述|
|------------------|-----------------|
|SQL_ROW_SUCCESS|資料列是不變。|
|SQL_ROW_UPDATED|已更新資料列。|
|SQL_ROW_DELETED|已刪除資料列。|
|SQL_ROW_ADDED|已新增資料列。|
|SQL_ROW_ERROR|資料列是因錯誤而無法擷取。|
|SQL_ROW_NOROW|沒有對應至的資料列*wRow*。|

如需詳細資訊，請參閱 ODBC API 函式`SQLExtendedFetch`Windows SDK 中。

##  <a name="getstatus"></a>  CRecordset::GetStatus

判斷資料錄集和最後一筆記錄是否已看過的目前資料錄的索引。

```
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>參數

*rStatus*<br/>
對 `CRecordsetStatus` 物件的參考。 如需詳細資訊，請參閱＜備註＞一節。

### <a name="remarks"></a>備註

`CRecordset` 嘗試追蹤該索引，但在某些情況下這不可能。 請參閱[GetRecordCount](#getrecordcount)取得說明。

`CRecordsetStatus`結構具有下列格式：

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

兩個成員`CRecordsetStatus`具有下列意義：

- `m_lCurrentRecord` 如果知道的話，包含目前資料錄的資料錄集，以零起始的索引。 如果無法判斷索引，這個成員會包含 AFX_CURRENT_RECORD_UNDEFINED (-2)。 如果`IsBOF`為 TRUE （空的資料錄集或嘗試捲動第一筆記錄之前），然後`m_lCurrentRecord`設 AFX_CURRENT_RECORD_BOF (-1)。 第一筆記錄，然後它會設定為 0，如果第二個記錄 1，依此類推。

- `m_bRecordCountFinal` 如果尚未決定資料錄集中的記錄總數，非零值。 通常這必須完成的資料錄集的開頭，並呼叫`MoveNext`直到`IsEOF`傳回非零值。 如果這個成員為零，記錄計算所傳回`GetRecordCount`，如果不為-1，只有 「 上限標準 」 的記錄計數。

##  <a name="getsql"></a>  CRecordset::GetSQL

呼叫此成員函式，以取得用來開啟網頁時，請選取資料錄集的資料錄的 SQL 陳述式。

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>傳回值

A **const**參考`CString`，其中包含 SQL 陳述式。

### <a name="remarks"></a>備註

這通常會是 SQL**選取**陳述式。 所傳回的字串`GetSQL`處於唯讀狀態。

所傳回的字串`GetSQL`通常不同於您可能已傳遞至資料錄集的任何字串*lpszSQL*參數來`Open`成員函式。 這是因為資料錄集建構完整的 SQL 陳述式，根據您傳遞給`Open`，使用 ClassWizard，可能會指定在指定的內容`m_strFilter`和`m_strSort`資料成員，以及您可能會有任何參數指定此項目。 針對詳細資料錄集如何建構此 SQL 陳述式中，請參閱文章[資料錄集：資料錄集選取資料錄 (ODBC) 的方式](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。

> [!NOTE]
>  只有在呼叫之後呼叫此成員函式[開啟](#open)。

##  <a name="gettablename"></a>  CRecordset::GetTableName

取得資料錄集的查詢所依據的 SQL 資料表的名稱。

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>傳回值

A **const**參考`CString`包含資料表的名稱，如果資料錄集是根據資料表，否則為空字串。

### <a name="remarks"></a>備註

`GetTableName` 才有效，如果資料錄集為基礎的資料表，不多個資料表或預先定義的查詢 （預存程序） 的聯結。 名稱為唯讀。

> [!NOTE]
>  只有在呼叫之後呼叫此成員函式[開啟](#open)。

##  <a name="isbof"></a>  CRecordset::IsBOF

傳回非零值，如果已位置之前的第一個記錄的資料錄集。 沒有目前資料錄。

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>傳回值

如果資料錄集不包含任何記錄，或您已向後捲動第一筆記錄中; 之前，非零值。否則為 0。

### <a name="remarks"></a>備註

記錄捲動記錄，以了解您是否已經看之前的資料錄集的第一個記錄之前，請呼叫此成員函式。 您也可以使用`IsBOF`連同`IsEOF`來判斷資料錄集是否包含任何記錄，或為空白。 立即呼叫後`Open`，如果資料錄集不包含任何記錄，`IsBOF`傳回非零值。當您開啟具有至少一個記錄的資料錄集時，第一筆記錄是目前的記錄和`IsBOF`會傳回 0。

如果第一筆記錄是目前的記錄，而且您呼叫`MovePrev`，`IsBOF`後續將會傳回非零值。 如果`IsBOF`傳回非零值，而且您呼叫`MovePrev`，就會發生錯誤。 如果`IsBOF`傳回非零值，目前的記錄為未定義，並需要目前記錄的任何動作將會產生錯誤。

### <a name="example"></a>範例

這個範例會使用`IsBOF`和`IsEOF`來偵測資料錄集的限制，當程式碼捲動透過雙向資料錄集。

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

##  <a name="isdeleted"></a>  CRecordset::IsDeleted

判斷是否已刪除目前的記錄。

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>傳回值

如果資料錄集位於已刪除的資料錄; 上，非零值。否則為 0。

### <a name="remarks"></a>備註

如果您捲動至記錄和`IsDeleted`，則傳回 TRUE （非零），然後才能執行任何其他資料錄集的作業，您必須捲動至另一筆記錄。

結果`IsDeleted`取決於許多因素，例如您的資料錄集類型、 資料錄集是否可更新，您指定是否`CRecordset::skipDeletedRecords`選項，當您開啟資料錄集，您的驅動程式套件已刪除的記錄，是否有多個使用者。

如需詳細資訊`CRecordset::skipDeletedRecords`和驅動程式封裝，請參閱[開啟](#open)成員函式。

> [!NOTE]
>  如果您已實作大量資料列擷取，您不應該呼叫`IsDeleted`。 請改為呼叫[GetRowStatus](#getrowstatus)成員函式。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="iseof"></a>  CRecordset::IsEOF

傳回非零值，如果已位置之後的最後一個記錄的資料錄集。 沒有目前資料錄。

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>傳回值

非零值，如果資料錄集不包含任何記錄，或如果您已經超過最後一筆記錄中;否則為 0。

### <a name="remarks"></a>備註

若要了解是否有超出資料錄集的最後一筆記錄的記錄從資料錄捲動時，請呼叫此成員函式。 您也可以使用`IsEOF`來判斷資料錄集是否包含任何記錄，或為空白。 立即呼叫後`Open`，如果資料錄集不包含任何記錄，`IsEOF`傳回非零值。 當您開啟具有至少一個記錄的資料錄集時，第一筆記錄是目前的記錄和`IsEOF`會傳回 0。

如果最後一筆記錄是目前的記錄，當您呼叫`MoveNext`，`IsEOF`後續將會傳回非零值。 如果`IsEOF`傳回非零值，而且您呼叫`MoveNext`，就會發生錯誤。 如果`IsEOF`傳回非零值，目前的記錄為未定義，並需要目前記錄的任何動作將會產生錯誤。

### <a name="example"></a>範例

範例，請參閱[IsBOF](#isbof)。

##  <a name="isfielddirty"></a>  CRecordset::IsFieldDirty

判斷指定的欄位資料成員是否已變更之後[編輯](#edit)或是[AddNew](#addnew)呼叫。

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
您想要檢查，則為 NULL 來決定的任何欄位是否已變更其狀態的欄位資料成員的指標。

### <a name="return-value"></a>傳回值

如果指定的欄位資料成員已呼叫後變更為非零`AddNew`或`Edit`，否則為 0。

### <a name="remarks"></a>備註

所有已變更的欄位資料成員中的資料會傳輸至記錄在資料來源上呼叫更新目前的記錄時[更新](#update)成員函式`CRecordset`(呼叫`Edit`或`AddNew`).

> [!NOTE]
>  此成員函式不適用於使用大量資料列擷取的資料錄集。 如果您已實作大量資料列擷取，然後`IsFieldDirty`一律會傳回 FALSE，而導致失敗的判斷提示。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

呼叫`IsFieldDirty`將會重設的先前呼叫的效果[SetFieldDirty](#setfielddirty)因為的欄位已變更的狀態會重新評估。 在 `AddNew`的情況下，如果目前的欄位值不同於虛擬 null 值，欄位狀態會設定已變更。 在 `Edit`情況下，如果欄位值不同於快取的值，則欄位狀態會設定已變更。

`IsFieldDirty` 透過實作[DoFieldExchange](#dofieldexchange)。

如需有關變更的旗標的詳細資訊，請參閱文章[資料錄集：資料錄集選取資料錄 (ODBC) 的方式](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。

##  <a name="isfieldnull"></a>  CRecordset::IsFieldNull

傳回非零值，如果目前的記錄中指定的欄位為 Null （沒有任何值）。

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
欄位資料成員的狀態，您想要檢查，則為 NULL 來判斷是否任何欄位都是 Null 指標。

### <a name="return-value"></a>傳回值

將指定的欄位資料成員會標示為 Null; 如果為非零否則為 0。

### <a name="remarks"></a>備註

呼叫此成員函式，以判斷資料錄集的指定的欄位資料成員是否已標示為 Null。 （在資料庫術語中，Null 」 有任何值 」 的方式，而且不是 NULL，c + + 中相同）。如果欄位資料成員被標示為 Null，則會將它解譯為任何值是目前資料錄的資料行。

> [!NOTE]
>  此成員函式不適用於使用大量資料列擷取的資料錄集。 如果您已實作大量資料列擷取，然後`IsFieldNull`一律會傳回 FALSE，而導致失敗的判斷提示。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

`IsFieldNull` 透過實作[DoFieldExchange](#dofieldexchange)。

##  <a name="isfieldnullable"></a>  CRecordset::IsFieldNullable

傳回非零值，如果目前的記錄中指定的欄位可以設定為 Null （具有任何值）。

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
欄位資料成員其狀態，您想要檢查，則為 NULL 以判斷是否的任何欄位可以設定為 Null 值的指標。

### <a name="remarks"></a>備註

呼叫以判斷指定的欄位資料成員是 「 可為 null 」 （可以是設定為 Null 值; 此成員函式C + + NULL 不是 Null，表示，在資料庫術語中，相同 」 有任何值 」)。

> [!NOTE]
>  如果您已實作大量資料列擷取，您不能呼叫`IsFieldNullable`。 請改為呼叫[GetODBCFieldInfo](#getodbcfieldinfo)成員函式，來判斷欄位是否可以設定為 Null 值。 請注意，您隨時都可呼叫`GetODBCFieldInfo`，而不論您是否有實作大量資料列擷取。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

不能是 Null 的欄位必須有值。 如果您嘗試將這類欄位設定為 Null，新增或更新記錄時，資料來源會拒絕的新增或更新，並[更新](#update)將會擲回例外狀況。 當您呼叫時，就會發生例外狀況`Update`不在您呼叫時，才[SetFieldNull](#setfieldnull)。

使用 NULL 函數的第一個引數套用函式的只有`outputColumn`欄位，不`param`欄位。 比方說，在呼叫

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

只會設定`outputColumn`欄位設為 NULL;`param`欄位不會受到影響。

作`param`欄位中，您必須提供個別的實際位址`param`您想要能夠著手進行，例如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

這表示您無法設定所有`param`欄位為 NULL，因為您可以使用`outputColumn`欄位。

`IsFieldNullable` 透過實作[DoFieldExchange](#dofieldexchange)。

##  <a name="isopen"></a>  CRecordset::IsOpen

判斷是否已開啟資料錄集。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

非零的資料錄集物件的[開放](#open)或[Requery](#requery)先前已呼叫成員函式，但尚未關閉資料錄集; 否則為 0。

##  <a name="m_hstmt"></a>  CRecordset::m_hstmt

包含 ODBC 陳述式資料結構的型別 HSTMT，資料錄集相關聯的控制代碼。

### <a name="remarks"></a>備註

每個查詢至 ODBC 資料來源是 HSTMT 相關聯。

> [!CAUTION]
>  請勿使用`m_hstmt`之前[開啟](#open)已呼叫。

通常您不需要 HSTMT 直接存取，但您可能需要直接執行 SQL 陳述式。 `ExecuteSQL`類別成員函式`CDatabase`提供的使用範例`m_hstmt`。

##  <a name="m_nfields"></a>  CRecordset::m_nFields

包含在資料錄集類別中的欄位資料成員的數目也就是說，資料來源的資料錄集選取資料行數目。

### <a name="remarks"></a>備註

資料錄集類別的建構函式必須初始化`m_nFields`與正確的數字。 如果您未實作大量資料列擷取，ClassWizard 會寫入此初始化的當您使用它來宣告您的資料錄集類別。 您也可以撰寫它以手動方式。

架構會使用此數字，來管理的欄位資料成員與對應的資料行的資料來源上目前的記錄之間的互動。

> [!CAUTION]
>  此號碼必須對應至 「 輸出資料行 」 中註冊的數目`DoFieldExchange`或`DoBulkFieldExchange`呼叫後[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)參數`CFieldExchange::outputColumn`。

您可以動態地，文件中所述繫結資料行 」 資料錄集：動態繫結資料行。 」 如果您這樣做，您必須增加中的計數`m_nFields`以反映呼叫 RFX 或 Bulk RFX 函式數目您`DoFieldExchange`或`DoBulkFieldExchange`動態繫結的資料行的成員函式。

如需詳細資訊，請參閱文章[資料錄集：動態繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)和[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

### <a name="example"></a>範例

請參閱文章[資料錄欄位交換：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

##  <a name="m_nparams"></a>  CRecordset::m_nParams

包含在資料錄集類別中的參數資料成員的數目也就是使用資料錄集的查詢傳遞的參數數目。

### <a name="remarks"></a>備註

如果您的資料錄集類別有任何參數的資料成員，該類別的建構函式必須初始化`m_nParams`與正確的數字。 值`m_nParams`預設值為 0。 如果您新增參數的資料成員 （您必須以手動方式執行） 您必須在類別建構函式，以反映參數的數目，也手動加入初始化 (必須是至少一樣大的數目 ' 中的預留位置程式`m_strFilter`或`m_strSort`字串)。

它會將參數化資料錄集的查詢時，架構會使用此數字。

> [!CAUTION]
>  此號碼必須對應至 「 參數 」 中註冊的數目`DoFieldExchange`或`DoBulkFieldExchange`呼叫後[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)參數值是`CFieldExchange::inputParam`， `CFieldExchange::param`， `CFieldExchange::outputParam`，或`CFieldExchange::inoutParam`.

### <a name="example"></a>範例

  請參閱文章[資料錄集：參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)和[資料錄欄位交換：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

##  <a name="m_pdatabase"></a>  CRecordset::m_pDatabase

包含一個指向`CDatabase`透過此資料錄集連接到資料來源的物件。

### <a name="remarks"></a>備註

此變數是兩種方式設定。 一般而言，您將指標傳遞至已連接`CDatabase`物件建構資料錄集物件時。 如果您傳遞 NULL，反而`CRecordset`建立`CDatabase`物件，並將它連線。 在任一情況下，`CRecordset`會儲存在此變數的指標。

通常您會直接不必使用儲存在指標`m_pDatabase`。 如果您要撰寫您自己的擴充功能`CRecordset`，不過，您可能需要使用指標。 例如，您可能需要將指標如果您擲回自己`CDBException`s。 您可能需要或如果您需要執行一些動作使用相同`CDatabase`物件，例如執行中的交易，設定逾時值，或呼叫`ExecuteSQL`類別成員函式`CDatabase`直接執行 SQL 陳述式。

##  <a name="m_strfilter"></a>  CRecordset::m_strFilter

但您建構資料錄集物件之後, 才能呼叫其`Open`成員函式中，使用此資料成員，來儲存`CString`包含 SQL**其中**子句。

### <a name="remarks"></a>備註

資料錄集限制 （或篩選） 它選取期間的記錄會使用此字串`Open`或`Requery`呼叫。 這可用來選取筆記錄，例如"位於加州的舊型的所有銷售人員 」 的子集 (「 狀態 = CA")。 ODBC SQL 語法**其中**子句

`WHERE search-condition`

請注意，您不會包含**其中**在字串中的關鍵字。 架構會提供它。

您可以藉由放置也參數化篩選字串 ' 預留位置，每個預留位置中，宣告您的類別中的參數資料成員和參數傳遞至資料錄集在執行階段。 這可讓您在執行階段建構篩選條件。 如需詳細資訊，請參閱文章[資料錄集：參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

如需有關 SQL**何處**子句，請參閱文章[SQL](../../data/odbc/sql.md)。 如需有關選取和篩選記錄的詳細資訊，請參閱文章[資料錄集：篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

##  <a name="m_strsort"></a>  CRecordset::m_strSort

但您建構資料錄集物件之後, 才能呼叫其`Open`成員函式中，使用此資料成員，來儲存`CString`包含 SQL **ORDER BY**子句。

### <a name="remarks"></a>備註

資料錄集使用這個字串，它會選取期間的記錄排序`Open`或`Requery`呼叫。 若要排序的一或多個資料行的資料錄集，您可以使用這項功能。 ODBC SQL 語法**ORDER BY**子句

`ORDER BY sort-specification [, sort-specification]...`

其中排序規格是整數或資料行名稱。 您也可以藉由附加"ASC"或"DESC"排序字串中的資料行清單來指定遞增或遞減順序 （預設值遞增順序）。 將選取的記錄是先進行排序所列，第一個資料行，再依第二個，依此類推。 例如，您可能會排序的 「 客戶 」 資料錄集的最後一個名稱，然後再依據名字。 您可以列出的資料行數目取決於資料來源。 如需詳細資訊，請參閱 Windows SDK。

請注意，您不會包含**ORDER BY**在字串中的關鍵字。 架構會提供它。

如需有關 SQL 子句的詳細資訊，請參閱[SQL](../../data/odbc/sql.md)。 如需有關如何排序資料錄的詳細資訊，請參閱[資料錄集：排序資料錄 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

##  <a name="move"></a>  CRecordset::Move

移動中資料錄集，向前或向後的目前記錄指標。

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>參數

*nRows*<br/>
向前或向後移動的資料列數目。 正值繼續向前進行，資料錄集的尾端。 負數值後，移到開頭。

*wFetchType*<br/>
判斷資料列集，`Move`會擷取。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

如果您傳遞的值為 0，表示*nRows*，`Move`重新整理目前的記錄;`Move`會結束目前的任何`AddNew`或`Edit`模式中，而且會還原之前的目前資料錄的值`AddNew`或`Edit`呼叫。

> [!NOTE]
>  當您移動的資料錄集時，您無法略過已刪除的記錄。 請參閱[CRecordset::IsDeleted](#isdeleted)如需詳細資訊。 當您開啟`CRecordset`具有`skipDeletedRecords`選項集，`Move`判斷提示，如果*nRows*參數為 0。 此行為可預防其他使用相同的資料的用戶端應用程式會刪除的資料列的重新整理。 請參閱*dwOption*中的參數[開啟](#open)如需描述`skipDeletedRecords`。

`Move` 依資料列集，重新定位資料錄集。 值為基礎*nRows*並*wFetchType*，`Move`提取適當的資料列集，並使第一筆記錄中該資料列集目前的記錄。 如果您未實作大量資料列擷取，則資料列集大小永遠為 1。 在提取資料列集時，`Move`直接呼叫[CheckRowsetError](#checkrowseterror)成員函式來處理任何提取所產生的錯誤。

根據您傳遞的值`Move`相當於其他`CRecordset`成員函式。 特別是，windows 7 *wFetchType*可能表示更直覺式的成員函式，並經常移動目前的資料錄的慣用的方法。

下表列出可能的值為*wFetchType*，資料列集，`Move`將會擷取基礎*wFetchType*並*nRows*，和任何對等項目成員函式對應至*wFetchType*。

|wFetchType|已擷取的資料列集|對等成員函式|
|----------------|--------------------|--------------------------------|
|Sql_fetch_relative 但 （預設值）|資料列集啟動*nRows*從目前的資料列集的第一個資料列的資料列。||
|SQL_FETCH_NEXT|下一步 的資料列集;*nRows*會被忽略。|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|先前的資料列集;*nRows*會被忽略。|[MovePrev](#moveprev)|
|SQL_FETCH_FIRST|資料錄集; 中的第一個資料列集*nRows*會被忽略。|[MoveFirst](#movefirst)|
|SQL_FETCH_LAST|最後一個的完整資料列集的資料錄集;*nRows*會被忽略。|[MoveLast](#movelast)|
|SQL_FETCH_ABSOLUTE|如果*nRows* > 0，資料列集啟動*nRows*從一開始的資料錄集的資料列。 如果*nRows* < 0，資料列集啟動*nRows*個資料列從資料錄集的結尾。 如果*nRows* = 0，則會傳回開頭的檔案 (BOF) 條件。|[SetAbsolutePosition](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|資料列集的書籤值會對應到資料列開始*nRows*。|[SetBookmark](#setbookmark)|

> [!NOTE]
>  順向資料錄集，如`Move`只適用於值是針對 SQL_FETCH_NEXT *wFetchType*。

> [!CAUTION]
>  呼叫`Move`擲回例外狀況，如果資料錄集不有任何記錄。 若要判斷資料錄集是否有任何記錄，請呼叫[IsBOF](#isbof)並[IsEOF](#iseof)。

> [!NOTE]
>  如果您有捲動過去的開頭或結尾的資料錄集 (`IsBOF`或是`IsEOF`傳回非零值)，則呼叫`Move`函式可能會擲回`CDBException`。 比方說，如果`IsEOF`傳回非零值以及`IsBOF`則否，然後`MoveNext`將會擲回例外狀況，但`MovePrev`不會。

> [!NOTE]
>  如果您呼叫`Move`時目前的記錄正在更新或新增，更新會遺失，而不發出警告。

如需有關資料錄集瀏覽的詳細資訊，請參閱文章[資料錄集：捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[資料錄集：書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 如需相關資訊，請參閱 ODBC API 函式`SQLExtendedFetch`Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

##  <a name="movefirst"></a>  CRecordset::MoveFirst

讓第一筆記錄中的第一個資料列集目前的記錄。

```
void MoveFirst();
```

### <a name="remarks"></a>備註

不論是否大量資料列擷取已實作，這一律會是資料錄集的第一個記錄。

您沒有呼叫`MoveFirst`立即開啟資料錄集之後。 此時，第一筆記錄 （如果有的話） 會自動是目前的記錄。

> [!NOTE]
>  此成員函式不是有效的順向資料錄集。

> [!NOTE]
>  當您移動的資料錄集時，您無法略過已刪除的記錄。 請參閱[IsDeleted](#isdeleted)成員函式，如需詳細資訊。

> [!CAUTION]
>  呼叫任一`Move`函式擲回例外狀況，如果資料錄集不有任何記錄。 若要判斷資料錄集是否有任何記錄，請呼叫`IsBOF`和`IsEOF`。

> [!NOTE]
>  如果您呼叫任何`Move`函式時的目前記錄正在更新或新增，更新會遺失，而不發出警告。

如需有關資料錄集瀏覽的詳細資訊，請參閱文章[資料錄集：捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[資料錄集：書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

### <a name="example"></a>範例

  範例，請參閱[IsBOF](#isbof)。

##  <a name="movelast"></a>  CRecordset::MoveLast

讓第一筆記錄中最後一個完整的資料列集目前的記錄。

```
void MoveLast();
```

### <a name="remarks"></a>備註

如果您未實作大量資料列擷取，您的資料錄集的資料列集大小為 1，因此`MoveLast`就會直接移至最後一個記錄中的資料錄集。

> [!NOTE]
>  此成員函式不是有效的順向資料錄集。

> [!NOTE]
>  當您移動的資料錄集時，您無法略過已刪除的記錄。 請參閱[IsDeleted](#isdeleted)成員函式，如需詳細資訊。

> [!CAUTION]
>  呼叫任一`Move`函式擲回例外狀況，如果資料錄集不有任何記錄。 若要判斷資料錄集是否有任何記錄，請呼叫`IsBOF`和`IsEOF`。

> [!NOTE]
>  如果您呼叫任何`Move`函式時的目前記錄正在更新或新增，更新會遺失，而不發出警告。

如需有關資料錄集瀏覽的詳細資訊，請參閱文章[資料錄集：捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[資料錄集：書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

### <a name="example"></a>範例

  範例，請參閱[IsBOF](#isbof)。

##  <a name="movenext"></a>  CRecordset::MoveNext

讓第一筆記錄中的下一個資料列集目前的記錄。

```
void MoveNext();
```

### <a name="remarks"></a>備註

如果您未實作大量資料列擷取，您的資料錄集的資料列集大小為 1，因此`MoveNext`就會直接移至下一筆記錄。

> [!NOTE]
>  當您移動的資料錄集時，您無法略過已刪除的記錄。 請參閱[IsDeleted](#isdeleted)成員函式，如需詳細資訊。

> [!CAUTION]
>  呼叫任一`Move`函式擲回例外狀況，如果資料錄集不有任何記錄。 若要判斷資料錄集是否有任何記錄，請呼叫`IsBOF`和`IsEOF`。

> [!NOTE]
>  也建議您呼叫`IsEOF`再呼叫`MoveNext`。 例如，如果您已超過結尾的資料錄集，捲動`IsEOF`會傳回非零; 後續呼叫`MoveNext`會擲回例外狀況。

> [!NOTE]
>  如果您呼叫任何`Move`函式時的目前記錄正在更新或新增，更新會遺失，而不發出警告。

如需有關資料錄集瀏覽的詳細資訊，請參閱文章[資料錄集：捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[資料錄集：書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

### <a name="example"></a>範例

  範例，請參閱[IsBOF](#isbof)。

##  <a name="moveprev"></a>  CRecordset::MovePrev

讓第一筆記錄中的前一個資料列集目前的記錄。

```
void MovePrev();
```

### <a name="remarks"></a>備註

如果您未實作大量資料列擷取，您的資料錄集的資料列集大小為 1，因此`MovePrev`就會直接移至前一筆記錄。

> [!NOTE]
>  此成員函式不是有效的順向資料錄集。

> [!NOTE]
>  當您移動的資料錄集時，您無法略過已刪除的記錄。 請參閱[IsDeleted](#isdeleted)成員函式，如需詳細資訊。

> [!CAUTION]
>  呼叫任一`Move`函式擲回例外狀況，如果資料錄集不有任何記錄。 若要判斷資料錄集是否有任何記錄，請呼叫`IsBOF`和`IsEOF`。

> [!NOTE]
>  也建議您呼叫`IsBOF`再呼叫`MovePrev`。 例如，如果您已捲動的資料錄集，開頭前面`IsBOF`會傳回非零; 後續呼叫`MovePrev`會擲回例外狀況。

> [!NOTE]
>  如果您呼叫任何`Move`函式時的目前記錄正在更新或新增，更新會遺失，而不發出警告。

如需有關資料錄集瀏覽的詳細資訊，請參閱文章[資料錄集：捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[資料錄集：書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

### <a name="example"></a>範例

  範例，請參閱[IsBOF](#isbof)。

##  <a name="onsetoptions"></a>  CRecordset::OnSetOptions

針對指定的 ODBC 陳述式，以呼叫設定選項 （選取項目上使用）。

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>參數

*hstmt*<br/>
其選項所設定的 ODBC 陳述式的 HSTMT。

### <a name="remarks"></a>備註

呼叫`OnSetOptions`設為指定的 ODBC 陳述式的選項 （選取項目上使用）。 架構會呼叫此成員函式，來設定資料錄集的初始選項。 `OnSetOptions` 判斷可捲動資料指標和資料指標並行的資料來源的支援，並據以設定資料錄集的選項。 (但`OnSetOptions`適用於選取作業`OnSetUpdateOptions`用於更新作業。)

覆寫`OnSetOptions`設定驅動程式或資料來源的特定選項。 例如，如果您的資料來源開啟獨佔存取的支援，您可能會覆寫`OnSetOptions`善用這項功能。

如需有關資料指標的詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)。

##  <a name="onsetupdateoptions"></a>  CRecordset::OnSetUpdateOptions

呼叫以指定的 ODBC 陳述式設定選項 （使用 update）。

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>參數

*hstmt*<br/>
其選項所設定的 ODBC 陳述式的 HSTMT。

### <a name="remarks"></a>備註

呼叫`OnSetUpdateOptions`設定指定的 ODBC 陳述式 （使用 update） 的選項。 建立 HSTMT 來更新資料錄集中的記錄之後，架構會呼叫此成員函式。 (但`OnSetOptions`適用於選取作業`OnSetUpdateOptions`用於更新作業。)`OnSetUpdateOptions`決定可捲動資料指標和資料指標並行的資料來源的支援，並據以設定資料錄集的選項。

覆寫`OnSetUpdateOptions`設定後，該陳述式用來存取資料庫的 ODBC 陳述式的選項。

如需有關資料指標的詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)。

##  <a name="open"></a>  CRecordset::Open

開啟資料錄集擷取的資料表，或執行查詢，表示資料錄集。

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>參數

*nOpenType*<br/>
接受預設值、 AFX_DB_USE_DEFAULT_TYPE 或使用下列其中一個值從`enum OpenType`:

- `CRecordset::dynaset` 使用雙向捲動資料錄集。 開啟資料錄集時，但其他使用者的資料值所做的變更會顯示下列提取作業時，決定成員資格和順序的記錄。 動態集又稱做為索引鍵集導向的資料錄集。

- `CRecordset::snapshot` 使用雙向捲動靜態資料錄集。 開啟資料錄集; 時，則是會決定成員資格和順序的記錄擷取記錄時，會決定資料值。 其他使用者所做的變更不會顯示，直到關閉後再重新開啟資料錄集。

- `CRecordset::dynamic` 使用雙向捲動資料錄集。 其他使用者的成員資格、 排序和資料值所做的變更會顯示下列提取作業。 請注意，許多 ODBC 驅動程式不支援這種類型的資料錄集。

- `CRecordset::forwardOnly` 唯讀資料錄集只會順向捲動。

   針對`CRecordset`，預設值是`CRecordset::snapshot`。 預設值的機制可讓這兩個 ODBC 與互動的 Visual c + + 精靈`CRecordset`和 DAO `CDaoRecordset`，其具有不同的預設值。

如需有關這些資料錄集類型的詳細資訊，請參閱[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)。 如需相關資訊，請參閱文件 」 使用區塊和可捲動資料指標 」 Windows SDK 中。

> [!CAUTION]
>  如果不支援要求的型別，架構就會擲回例外狀況。

*lpszSQL*<br/>
字串指標，包含下列其中之一：

- NULL 指標。

- 資料表的名稱。

- SQL**選取 **陳述式 (選擇性地使用 SQL**位置**或是**ORDER BY**子句)。

- A**呼叫**陳述式，指定預先定義的查詢 （預存程序） 的名稱。 請小心不要插入大括號之間的空白字元和**呼叫**關鍵字。

如需有關這個字串的詳細資訊，請參閱資料表與討論的 < 備註 > 底下的 ClassWizard 的角色。

> [!NOTE]
>  在結果集資料行的順序必須符合的 RFX 的順序，或 Bulk RFX 函式會呼叫您[DoFieldExchange](#dofieldexchange)或是[DoBulkFieldExchange](#dobulkfieldexchange)函式覆寫。

*dwOptions*<br/>
位元遮罩可以指定下列值的組合。 其中有些是互斥的。 預設值是**無**。

- `CRecordset::none` 不設定任何選項。 此參數值是互斥的所有其他值。 根據預設，可以更新資料錄集與[編輯](#edit)或是[刪除](#delete)，並可讓您將使用的新記錄附加[AddNew](#addnew)。 可更新性取決於資料來源上，以及*nOpenType*您指定的選項。 無法使用最佳化大量新增項目。 大量資料列擷取將不會實作。 已刪除的記錄不會在資料錄集巡覽期間略過。 無法使用書籤。 檢查自動變更欄位的實作。

- `CRecordset::appendOnly` 不允許`Edit`或`Delete`上資料錄集。 允許`AddNew`只。 此選項是互斥的`CRecordset::readOnly`。

- `CRecordset::readOnly` 開啟資料錄集，以唯讀模式。 此選項是互斥的`CRecordset::appendOnly`。

- `CRecordset::optimizeBulkAdd` 您可以使用已備妥的 SQL 陳述式，最佳化一次新增多筆記錄。 只有當您不想要使用 ODBC API 函式時，才適用`SQLSetPos`更新資料錄集。 第一次更新判斷哪些欄位會標示為已變更。 此選項是互斥的`CRecordset::useMultiRowFetch`。

- `CRecordset::useMultiRowFetch` 實作以允許在單一提取作業中要擷取多個資料列的大量資料列擷取。 這是設計來改善效能，進階的功能不過，大量資料錄欄位交換不受到 ClassWizard。 此選項是互斥的`CRecordset::optimizeBulkAdd`。 請注意，如果您指定`CRecordset::useMultiRowFetch`，然後選擇`CRecordset::noDirtyFieldCheck`將會自動開啟 （雙重緩衝將無法使用）; 順向資料錄集，此選項在`CRecordset::useExtendedFetch`會自動開啟。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

- `CRecordset::skipDeletedRecords` 瀏覽資料錄集時，請略過所有已刪除的記錄。 這會在特定的相對提取的效能變慢。 這個選項不能在順向資料錄集。 如果您呼叫[移動](#move)具有*nRows*參數設定為 0，而`CRecordset::skipDeletedRecords`選項集，`Move`會判斷提示。 請注意，`CRecordset::skipDeletedRecords`大致*驅動程式封裝*，表示已刪除資料列會從資料錄集。 不過，如果您的驅動程式套件的記錄，然後它會略過只在您刪除; 的記錄它不會略過資料錄集開啟時，其他使用者刪除的記錄。 `CRecordset::skipDeletedRecords` 會略過其他使用者刪除的資料列。

- `CRecordset::useBookmarks` 如果支援在資料錄集，可以使用書籤。 書籤緩慢的資料擷取，但改善資料瀏覽的效能。 順向資料錄集上不正確。 如需詳細資訊，請參閱文章[資料錄集：書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。

- `CRecordset::noDirtyFieldCheck` 關閉自動變更的欄位，檢查 （雙重緩衝）。 這樣可改進效能;不過，您必須手動標記的欄位為中途呼叫`SetFieldDirty`和`SetFieldNull`成員函式。請注意在類別中的雙重緩衝`CRecordset`類似於類別中的雙重緩衝`CDaoRecordset`。 不過，在`CRecordset`，您無法啟用雙重緩衝的個別欄位上; 您啟用的所有欄位，或停用它的所有欄位。 請注意，如果您指定的選項`CRecordset::useMultiRowFetch`，然後`CRecordset::noDirtyFieldCheck`將會開啟自動，但是`SetFieldDirty`和`SetFieldNull`不能用在實作大量資料列擷取的資料錄集。

- `CRecordset::executeDirect` 請勿使用備妥的 SQL 陳述式。 為了提升效能，如果指定這個選項`Requery`絕不會呼叫成員函式。

- `CRecordset::useExtendedFetch` 實作`SQLExtendedFetch`而不是`SQLFetch`。 這被設計用於實作大量順向資料錄集的資料列擷取。 如果您指定的選項`CRecordset::useMultiRowFetch`順向資料錄集，然後`CRecordset::useExtendedFetch`會自動開啟。

- `CRecordset::userAllocMultiRowBuffers` 使用者將會配置儲存體緩衝區的資料。 使用此選項搭配`CRecordset::useMultiRowFetch`如果您想要將您自己的存放裝置; 配置，否則為架構會自動配置所需的儲存體。 如需詳細資訊，請參閱文章[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 請注意，指定`CRecordset::userAllocMultiRowBuffers`但未指定`CRecordset::useMultiRowFetch`會導致失敗的判斷提示。

### <a name="return-value"></a>傳回值

非零`CRecordset`物件已成功開啟，否則為 0 [Openex](../../mfc/reference/cdatabase-class.md#open) （如果呼叫） 會傳回 0。

### <a name="remarks"></a>備註

您必須呼叫此成員函式，來執行資料錄集所定義的查詢。 然後再呼叫`Open`，您必須建構資料錄集物件。

此資料錄集的資料來源連接，取決於您如何建構資料錄集，然後再呼叫`Open`。 如果您傳遞[CDatabase](../../mfc/reference/cdatabase-class.md)物件尚未連接到資料來源的資料錄集建構函式會使用此成員函式[GetDefaultConnect](#getdefaultconnect)嘗試開啟的資料庫物件。 如果您的資料錄集建構函式傳遞 NULL，建構函式會建構`CDatabase`物件，和`Open`來嘗試連接的資料庫物件。 如需關閉資料錄集，並在這些不同的情況下連接的詳細資訊，請參閱[關閉](#close)。

> [!NOTE]
>  透過資料來源的存取`CRecordset`一律共用物件。 不同於`CDaoRecordset`類別，您無法使用`CRecordset`要以獨佔式存取中開啟資料來源物件。

當您呼叫`Open`，通常是 SQL 查詢**選取**陳述式，會選取下表所示的準則為基礎的記錄。

|LpszSQL 參數的值|取決於選取的記錄|範例|
|------------------------------------|----------------------------------------|-------------|
|NULL|所傳回的字串`GetDefaultSQL`。||
|SQL 資料表名稱|中的資料表清單的所有資料行`DoFieldExchange`或`DoBulkFieldExchange`。|`"Customer"`|
|預先定義的查詢 （預存程序） 的名稱|查詢定義會傳回資料行。|`"{call OverDueAccts}"`|
|**選取 **資料行清單**FROM**資料表清單|從指定的資料表指定的資料行。|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
>  請小心您不要在您的 SQL 字串中插入額外的空白字元。 例如，如果您要插入大括號之間的空白字元和**呼叫**關鍵字，MFC 會錯誤解譯為資料表名稱的 SQL 字串，並將它到納入**選取**陳述式，這會導致擲回例外狀況。 同樣地，如果您預先定義的查詢會使用輸出參數，您不能插入大括號之間的空格和 ' 符號。 最後，您必須插入在大括號之前的空格**呼叫**陳述式或之前**選取**中的關鍵字**選取**陳述式。

一般的程序是傳遞 NULL 給`Open`; 在此情況下，`Open`呼叫[GetDefaultSQL](#getdefaultsql)。 如果您使用衍生`CRecordset`類別，`GetDefaultSQL`可讓您在 類別精靈中指定的資料表名稱。 您可以改為指定中的其他資訊`lpszSQL`參數。

傳遞任何方法，`Open`建構查詢的最終 SQL 字串 (字串可能有 SQL**何處**並**ORDER BY**子句附加至`lpszSQL`您傳遞的字串)，然後執行查詢中。 您可以檢查建構的字串，藉由呼叫[GetSQL](#getsql)之後呼叫`Open`。 如有關如何建構 SQL 陳述式資料錄集，並選取記錄，其他詳細資料，請參閱本文[資料錄集：資料錄集選取資料錄 (ODBC) 的方式](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。

您的資料錄集類別的欄位資料成員會繫結至選取的資料的資料行。 如果未傳回任何記錄，第一筆記錄會變成目前的記錄。

如果您想要設定的資料錄集，例如篩選或排序選項在您建構資料錄集物件之後但在您呼叫之前指定這些`Open`。 如果您想要重新整理資料錄集之後的記錄資料錄集已經開啟，請呼叫[Requery](#requery)。

如需詳細資訊，包括其他範例，請參閱文章[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)，[資料錄集：資料錄集選取資料錄 (ODBC) 的方式](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)，和[資料錄集：建立和關閉資料錄集 (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。

### <a name="example"></a>範例

下列程式碼範例顯示不同形式的`Open`呼叫。

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

##  <a name="refreshrowset"></a>  CRecordset::RefreshRowset

更新資料和目前的資料列集中的資料列的狀態。

```
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>參數

*wRow*<br/>
以一為基的一個資料列中位置的目前資料列集。 這個值可以介於 0 到資料列集的大小。

*wLockType*<br/>
值，指出如何鎖定之後重新整理的資料列。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

如果您傳遞的值為零*wRow*，則會重新整理資料列集中的每個資料列。

若要使用`RefreshRowset`，您必須藉由指定的大量資料列擷取已實作`CRecordset::useMulitRowFetch`選項[開啟](#open)成員函式。

`RefreshRowset` 呼叫 ODBC API 函式`SQLSetPos`。 *WLockType*參數指定的資料列之後的鎖定狀態`SQLSetPos`已經執行。 下表說明可能的值為*wLockType*。

|wLockType|描述|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE （預設值）|驅動程式或資料來源可確保資料列在相同的鎖定或解除鎖定狀態之前`RefreshRowset`呼叫。|
|SQL_LOCK_EXCLUSIVE|驅動程式或資料來源以獨佔方式鎖定資料列。 並非所有的資料來源都支援這種類型的鎖定。|
|SQL_LOCK_UNLOCK|驅動程式或資料來源會解除鎖定資料列。 並非所有的資料來源都支援這種類型的鎖定。|

如需詳細資訊`SQLSetPos`，請參閱 Windows SDK。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="requery"></a>  CRecordset::Requery

重建 （重新整理） 資料錄集。

```
virtual BOOL Requery();
```

### <a name="return-value"></a>傳回值

資料錄集已成功重建; 如果為非零否則為 0。

### <a name="remarks"></a>備註

如果未傳回任何記錄，第一筆記錄會變成目前的記錄。

為了讓資料錄集，以反映新增和刪除，您或其他使用者對資料來源，您必須重建資料錄集，藉由呼叫`Requery`。 如果資料錄集是動態集，它會自動反映您或其他使用者對其現有的記錄 （但不是新增項目） 的更新。 如果資料錄集是快照集，您必須呼叫`Requery`以反映其他使用者，以及新增和刪除的編輯。

動態集或快照集，請呼叫`Requery`任何您想要重建使用新的篩選或排序或新的參數值的資料錄集的時間。 設定新的篩選或排序屬性指派新值給`m_strFilter`並`m_strSort`再呼叫`Requery`。 設定新的參數指派新值給參數的資料成員，然後再呼叫`Requery`。 如果篩選和排序字串未變更，您可以重複使用查詢，進而改善效能。

如果嘗試重建資料錄集失敗，就會關閉資料錄集。 在呼叫之前`Requery`，您可以判斷是否可以藉由呼叫重新查詢資料錄集`CanRestart`成員函式。 `CanRestart` 不保證`Requery`會成功。

> [!CAUTION]
>  呼叫`Requery`之後呼叫只[開啟](#open)。

### <a name="example"></a>範例

此範例會重建以套用不同的排序次序的資料錄集。

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

##  <a name="setabsoluteposition"></a>  CRecordset::SetAbsolutePosition

您可以將資料錄集置於對應至指定的記錄數目的記錄。

```
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>參數

*nRows*<br/>
以一為中的序數位置目前記錄資料錄集。

### <a name="remarks"></a>備註

`SetAbsolutePosition` 將目前的記錄指標根據此序數位置。

> [!NOTE]
>  此成員函式在順向資料錄集無效。

ODBC 資料錄集，絕對位置設定為 1 是指第一筆記錄，在資料錄集;設定為 0，是指檔案開頭的 (BOF) 位置。

您也可以傳遞至負值`SetAbsolutePosition`。 在此情況下會評估資料錄集的位置，從資料錄集的結尾。 比方說，`SetAbsolutePosition( -1 )`將目前的記錄指標移至最後一筆記錄，在資料錄集。

> [!NOTE]
>  絕對位置不是要做為 surrogate 資料錄數目。 書籤仍會保留，並傳回至指定的位置，因為刪除先前的記錄時，記錄的位置變更的建議的方式。 此外，您無法確保指定的記錄會有相同的絕對位置，如果資料錄集重新建立一次因為除非它使用 SQL 陳述式使用建立資料錄集內的個別記錄的順序不保證**ORDER BY**子句。

如需有關資料錄集瀏覽和書籤的詳細資訊，請參閱文章[資料錄集：捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)和[資料錄集：書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。

##  <a name="setbookmark"></a>  CRecordset::SetBookmark

將資料錄集記錄，其中包含指定的書籤。

```
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>參數

*varBookmark*<br/>
參考[CDBVariant](../../mfc/reference/cdbvariant-class.md)物件，其中包含書籤值的特定記錄。

### <a name="remarks"></a>備註

若要判斷是否在資料錄集上支援書籤，請呼叫[CanBookmark](#canbookmark)。 若要提供並支援書籤，您必須設定`CRecordset::useBookmarks`選項*dwOptions*參數[開啟](#open)成員函式。

> [!NOTE]
>  如果書籤不受支援或無法使用，呼叫`SetBookmark`會導致擲回例外狀況。 順向資料錄集不支援書籤。

若要先擷取目前資料錄的書籤，請呼叫[GetBookmark](#getbookmark)，以節省的書籤值`CDBVariant`物件。 稍後，您可以傳回該記錄呼叫`SetBookmark`使用已儲存的書籤值。

> [!NOTE]
>  特定資料錄集作業之後，您應該檢查的書籤持續性，然後再呼叫`SetBookmark`。 例如，如果您擷取具有書籤`GetBookmark`，然後呼叫`Requery`，書籤可能不再有效。 呼叫[CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence)若要檢查您是否能安全地呼叫`SetBookmark`。

如需書籤和資料錄集瀏覽的詳細資訊，請參閱文章[資料錄集：書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[資料錄集：捲動 (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="setfielddirty"></a>  CRecordset::SetFieldDirty

旗標為已變更的資料錄集，或為未變更的欄位資料成員。

```
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>參數

*pv*<br/>
包含在資料錄集則為 NULL 的欄位資料成員的位址。 如果是 NULL，則會標示資料錄集中的所有欄位資料成員。 (C + + NULL 不是 Null 相同資料庫術語中，「 有任何值 」。 這表示)

*bDirty*<br/>
如果欄位資料成員會標示為 「 中途 」 （變更），則為 TRUE。 如果欄位資料成員會標示為 「 清除 」 （未變更），則否則為 FALSE。

### <a name="remarks"></a>備註

標示為不變的欄位，可確保欄位不會更新，而且所產生的 SQL 流量。

> [!NOTE]
>  此成員函式不適用於使用大量資料列擷取的資料錄集。 如果您已實作大量資料列擷取，然後`SetFieldDirty`會導致失敗的判斷提示。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

Framework 標記變更欄位資料成員，以確保它們會寫入資料來源上的記錄資料錄欄位交換 (RFX) 機制。 變更欄位的值，通常欄位已變更會自動設定，讓您很少需要呼叫`SetFieldDirty`，但您有時可能會想要確保的資料行可明確地更新或插入不論何種值位於欄位資料成員。

> [!CAUTION]
>  呼叫此成員函式，只有在您呼叫之後，才[編輯](#edit)或是[AddNew](#addnew)。

使用 NULL 函數的第一個引數套用函式的只有`outputColumn`欄位，不`param`欄位。 比方說，在呼叫

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

只會設定`outputColumn`欄位設為 NULL;`param`欄位不會受到影響。

作`param`欄位中，您必須提供個別的實際位址`param`您想要能夠著手進行，例如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

這表示您無法設定所有`param`欄位為 NULL，因為您可以使用`outputColumn`欄位。

##  <a name="setfieldnull"></a>  CRecordset::SetFieldNull

為 Null （特別具有任何值），或為非 Null 旗標的資料錄集的欄位資料成員。

```
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>參數

*pv*<br/>
包含在資料錄集則為 NULL 的欄位資料成員的位址。 如果是 NULL，則會標示資料錄集中的所有欄位資料成員。 (C + + NULL 不是 Null 相同資料庫術語中，「 有任何值 」。 這表示)

*bNull*<br/>
如果欄位資料成員標示為不具有任何值 (Null) 為非零。 否則為 0，表示欄位資料成員會標示為非 Null。

### <a name="remarks"></a>備註

當您將新記錄加入資料錄集時，所有的欄位資料成員一開始會設為 Null 值，並標示為 「 中途 」 （變更）。 當您從資料來源擷取一筆記錄時，其資料行可能已經值或是 Null。

> [!NOTE]
>  請勿在使用大量資料列擷取的資料錄集上呼叫此成員函式。 如果您已實作大量資料列擷取，則呼叫`SetFieldNull`導致失敗的判斷提示。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

如果您特別想要將目前資料錄的欄位指定為沒有值，呼叫`SetFieldNull`具有*bNull*設成 TRUE 來將它標示為 Null。 如果欄位先前標記為 Null，而且您現在想要指定其值，只要設定其新值。 您沒有移除 Null 旗標與`SetFieldNull`。 若要判斷欄位是否可為 Null，請呼叫`IsFieldNullable`。

> [!CAUTION]
>  呼叫此成員函式，只有在您呼叫之後，才[編輯](#edit)或是[AddNew](#addnew)。

使用 NULL 函數的第一個引數套用函式的只有`outputColumn`欄位，不`param`欄位。 比方說，在呼叫

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

只會設定`outputColumn`欄位設為 NULL;`param`欄位不會受到影響。

作`param`欄位中，您必須提供個別的實際位址`param`您想要能夠著手進行，例如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

這表示您無法設定所有`param`欄位為 NULL，因為您可以使用`outputColumn`欄位。

> [!NOTE]
>  設定參數為 Null，呼叫時`SetFieldNull`資料錄集是開啟的結果，在判斷提示之前。 在此情況下，呼叫[SetParamNull](#setparamnull)。

`SetFieldNull` 透過實作[DoFieldExchange](#dofieldexchange)。

##  <a name="setlockingmode"></a>  CRecordset::SetLockingMode

設定 「 開放式 」 鎖定 （預設值） 或 「 封閉式 」 鎖定的鎖定模式。 決定如何更新鎖定的記錄。

```
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>參數

*nMode*<br/>
中的以下值的其中一個`enum LockMode`:

- `optimistic` 開放式鎖定鎖定只有在呼叫期間所更新的資料錄`Update`。

- `pessimistic` 封閉式鎖定會鎖定資料錄一旦`Edit`呼叫，並會保留該鎖定直到`Update`呼叫完成，或移至新的記錄。

### <a name="remarks"></a>備註

如果您需要指定哪一個資料錄集使用更新的兩種記錄鎖定的策略，請呼叫此成員函式。 根據預設，資料錄集的鎖定模式是`optimistic`。 您可以變更，若要更謹慎`pessimistic`鎖定策略。 呼叫`SetLockingMode`建構，並開啟資料錄集物件之後，但在呼叫之前`Edit`。

##  <a name="setparamnull"></a>  CRecordset::SetParamNull

旗標參數，為 Null （特別具有任何值），或為非 Null。

```
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
參數之以零為起始的索引。

*bNull*<br/>
如果 TRUE （預設值），則參數會標示為 Null。 否則，參數會標示為非 Null。

### <a name="remarks"></a>備註

不同於[SetFieldNull](#setfieldnull)，您可以呼叫`SetParamNull`您開啟資料錄集之前。

`SetParamNull` 一般會搭配使用預先定義的查詢 （預存程序）。

##  <a name="setrowsetcursorposition"></a>  CRecordset::SetRowsetCursorPosition

將游標移至目前的資料列集內的資料列。

```
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>參數

*wRow*<br/>
以一為基的一個資料列中位置的目前資料列集。 此值的資料列集大小範圍從 1。

*wLockType*<br/>
值，指出如何鎖定之後重新整理的資料列。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

在實作大量資料列擷取時，記錄會擷取資料列集，其中第一個記錄中擷取的資料列集是目前的記錄。 若要讓資料列集內的另一筆記錄目前的記錄，呼叫`SetRowsetCursorPosition`。 例如，您可以結合`SetRowsetCursorPosition`具有[GetFieldValue](#getfieldvalue)成員函式來以動態方式從您的資料錄集的任何記錄中擷取資料。

若要使用`SetRowsetCursorPosition`，您必須藉由指定的大量資料列擷取已實作`CRecordset::useMultiRowFetch`選項*dwOptions*中的參數[開啟](#open)成員函式。

`SetRowsetCursorPosition` 呼叫 ODBC API 函式`SQLSetPos`。 *WLockType*參數指定的資料列之後的鎖定狀態`SQLSetPos`已經執行。 下表說明可能的值為*wLockType*。

|wLockType|描述|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE （預設值）|驅動程式或資料來源可確保資料列在相同的鎖定或解除鎖定狀態之前`SetRowsetCursorPosition`呼叫。|
|SQL_LOCK_EXCLUSIVE|驅動程式或資料來源以獨佔方式鎖定資料列。 並非所有的資料來源都支援這種類型的鎖定。|
|SQL_LOCK_UNLOCK|驅動程式或資料來源會解除鎖定資料列。 並非所有的資料來源都支援這種類型的鎖定。|

如需詳細資訊`SQLSetPos`，請參閱 Windows SDK。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="setrowsetsize"></a>  CRecordset::SetRowsetSize

指定您想要擷取期間所擷取的記錄數目。

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>參數

*dwNewRowsetSize*<br/>
擷取給定的擷取期間的資料列數目。

### <a name="remarks"></a>備註

此虛擬成員函式會指定您想要使用大量資料列擷取時，單一擷取期間擷取的資料列數目。 若要實作大量資料列擷取，您必須設定`CRecordset::useMultiRowFetch`選項*dwOptions*參數[開啟](#open)成員函式。

> [!NOTE]
>  呼叫`SetRowsetSize`而不需要實作大量資料列擷取將會導致失敗的判斷提示。

呼叫`SetRowsetSize`再呼叫`Open`一開始設定資料錄集的資料列集大小。 實作大量資料列擷取時，才會進行預設資料列集大小為 25。

> [!NOTE]
>  呼叫時請特別小心`SetRowsetSize`。 如果您以手動方式配置的資料存放區 (依照`CRecordset::userAllocMultiRowBuffers`dwOptions 參數中的選項`Open`)，您應該檢查您是否需要配置儲存體的緩衝區之後您呼叫, `SetRowsetSize`，但會在您之前執行任何資料指標瀏覽作業。

若要取得資料列集大小的目前設定，請呼叫[GetRowsetSize](#getrowsetsize)。

如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="update"></a>  CRecordset::Update

完成`AddNew`或`Edit`藉由將新的或修改資料儲存在資料來源上的作業。

```
virtual BOOL Update();
```

### <a name="return-value"></a>傳回值

如果已成功更新一筆記錄; 為非零否則為 0，如果沒有資料行已變更。 如果更新沒有記錄，或如果多個更新一個記錄的時間，則會擲回例外狀況。 例外狀況也會擲回的任何其他失敗的資料來源上。

### <a name="remarks"></a>備註

呼叫此成員函式之後呼叫[AddNew](#addnew)或是[編輯](#edit)成員函式。 這個呼叫才可完成`AddNew`或`Edit`作業。

> [!NOTE]
>  如果您已實作大量資料列擷取，您不能呼叫`Update`。 這會導致失敗的判斷提示。 雖然類別`CRecordset`不會提供一個機制來更新資料的大量資料列，您可以撰寫自己的函式使用 ODBC API 函式`SQLSetPos`。 如需有關大量資料列擷取的詳細資訊，請參閱[資料錄集：擷取大量 (ODBC) 資料錄](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

兩者`AddNew`和`Edit`準備加入或編輯過的資料位於編輯緩衝區，以便儲存到資料來源。 `Update` 儲存資料。 只有這些欄位標記，或偵測到變更會更新。

如果資料來源支援交易，您可以製作`Update`呼叫 (和其相對應`AddNew`或`Edit`呼叫) 交易的一部分。 如需有關交易的詳細資訊，請參閱[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。

> [!CAUTION]
>  如果您呼叫`Update`但未先呼叫`AddNew`或是`Edit`，`Update`就會擲回`CDBException`。 如果您呼叫`AddNew`或`Edit`，您必須呼叫`Update`之前先呼叫`Move`作業期間或之前關閉資料錄集或資料來源連接。 否則，您的變更都會遺失而不另行通知的。

如需有關處理`Update`失敗，請參閱文章[資料錄集：資料錄集更新資料錄 (ODBC) 的方式](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

### <a name="example"></a>範例

請參閱文章[交易：執行異動 (ODBC) 資料錄集中](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView 類別](../../mfc/reference/crecordview-class.md)
