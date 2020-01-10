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
ms.openlocfilehash: 1ebdb18254171d28b5d5e02367596b79142df284
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626195"
---
# <a name="crecordset-class"></a>CRecordset 類別

表示選取自資料來源的資料錄集。

## <a name="syntax"></a>語法

```
class CRecordset : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名字|描述|
|----------|-----------------|
|[CRecordset：： CRecordset](#crecordset)|建構 `CRecordset` 物件。 您的衍生類別必須提供可呼叫此函式的函式。|

### <a name="public-methods"></a>公用方法

|名字|描述|
|----------|-----------------|
|[CRecordset：： AddNew](#addnew)|準備加入新記錄。 呼叫 `Update` 以完成新增。|
|[CRecordset：： CanAppend](#canappend)|如果可以透過 `AddNew` 成員函式，將新記錄加入至記錄集，則傳回非零。|
|[CRecordset：： CanBookmark](#canbookmark)|如果記錄集支援書簽，則傳回非零。|
|[CRecordset：： Cancel](#cancel)|從第二個執行緒取消非同步作業或進程。|
|[CRecordset：： CancelUpdate](#cancelupdate)|因為 `AddNew` 或 `Edit` 作業，而取消任何暫止的更新。|
|[CRecordset：： CanRestart](#canrestart)|如果可以呼叫 `Requery` 來重新執行記錄集的查詢，則傳回非零。|
|[CRecordset：： CanScroll](#canscroll)|如果您可以流覽記錄，則傳回非零。|
|[CRecordset：： CanTransact](#cantransact)|如果資料來源支援交易，則傳回非零。|
|[CRecordset：： CanUpdate](#canupdate)|如果可以更新記錄集，則傳回非零（您可以加入、更新或刪除記錄）。|
|[CRecordset：： CheckRowsetError](#checkrowseterror)|呼叫以處理在記錄提取期間產生的錯誤。|
|[CRecordset：： Close](#close)|關閉記錄集和與其相關聯的 ODBC HSTMT。|
|[CRecordset：:D 刪除](#delete)|從記錄集刪除目前的記錄。 刪除之後，您必須明確地滾動到另一筆記錄。|
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|呼叫以將資料來源中的大量資料列交換到記錄集。 執行大量記錄欄位交換（Bulk RFX）。|
|[CRecordset::DoFieldExchange](#dofieldexchange)|呼叫以在記錄集的欄位資料成員和資料來源上的對應記錄之間交換資料（雙向）。 實行記錄欄位交換（RFX）。|
|[CRecordset：： Edit](#edit)|準備目前記錄的變更。 呼叫 `Update` 以完成編輯。|
|[CRecordset：： FlushResultSet](#flushresultset)|當使用預先定義的查詢時，如果有另一個要抓取的結果集，則傳回非零。|
|[CRecordset：： GetBookmark](#getbookmark)|將記錄的書簽值指派給參數物件。|
|[CRecordset：： GetDefaultConnect](#getdefaultconnect)|呼叫以取得預設連接字串。|
|[CRecordset：： GetDefaultSQL](#getdefaultsql)|呼叫以取得要執行的預設 SQL 字串。|
|[CRecordset：： GetFieldValue](#getfieldvalue)|傳回記錄集中的欄位值。|
|[CRecordset：： GetODBCFieldCount](#getodbcfieldcount)|傳回記錄集內的欄位數目。|
|[CRecordset：： GetODBCFieldInfo](#getodbcfieldinfo)|傳回有關記錄集中欄位的特定資訊類型。|
|[CRecordset：： GetRecordCount](#getrecordcount)|傳回記錄集中的記錄數目。|
|[CRecordset：： GetRowsetSize](#getrowsetsize)|傳回您想要在單一提取期間取得的記錄數目。|
|[CRecordset：： GetRowsFetched](#getrowsfetched)|傳回提取期間取出的實際資料列數目。|
|[CRecordset：： GetRowStatus](#getrowstatus)|傳回提取之後的資料列狀態。|
|[CRecordset：： GetSQL](#getsql)|取得用來選取記錄集記錄的 SQL 字串。|
|[CRecordset：： GetStatus](#getstatus)|取得記錄集的狀態：目前記錄的索引，以及是否已取得記錄的最終計數。|
|[CRecordset：： GetTableName](#gettablename)|取得記錄集所依據之資料表的名稱。|
|[CRecordset：： IsBOF](#isbof)|如果記錄集已放在第一筆記錄之前，則傳回非零。 沒有目前的記錄。|
|[CRecordset：： IsDeleted](#isdeleted)|如果記錄集位於已刪除的記錄上，則傳回非零。|
|[CRecordset：： IsEOF](#iseof)|如果記錄集已放在最後一筆記錄之後，則傳回非零。 沒有目前的記錄。|
|[CRecordset：： IsFieldDirty](#isfielddirty)|如果目前記錄中指定的欄位已變更，則傳回非零。|
|[CRecordset：： IsFieldNull](#isfieldnull)|如果目前記錄中的指定欄位為 null （沒有值），則傳回非零。|
|[CRecordset：： IsFieldNullable](#isfieldnullable)|如果目前記錄中的指定欄位可以設定為 null （沒有值），則傳回非零。|
|[CRecordset：： IsOpen](#isopen)|如果先前已呼叫 `Open`，則傳回非零。|
|[CRecordset：： Move](#move)|以任一方向將記錄集置於目前記錄中指定數目的記錄。|
|[CRecordset：： MoveFirst](#movefirst)|將目前的記錄放置在記錄集的第一筆記錄上。 先測試 `IsBOF`。|
|[CRecordset：： MoveLast](#movelast)|將目前的記錄放置在最後一筆記錄或最後一個資料列集上。 先測試 `IsEOF`。|
|[CRecordset：： MoveNext](#movenext)|將目前的記錄置於下一筆記錄或下一個資料列集。 先測試 `IsEOF`。|
|[CRecordset：： MovePrev](#moveprev)|將目前的記錄置於上一個記錄或上一個資料列集。 先測試 `IsBOF`。|
|[CRecordset：： OnSetOptions](#onsetoptions)|呼叫以針對指定的 ODBC 語句設定選項（用於選取）。|
|[CRecordset：： OnSetUpdateOptions](#onsetupdateoptions)|呼叫以針對指定的 ODBC 語句設定選項（用於 update）。|
|[CRecordset：： Open](#open)|藉由抓取資料表或執行記錄集所代表的查詢，來開啟記錄集。|
|[CRecordset：： RefreshRowset](#refreshrowset)|重新整理指定資料列的資料和狀態。|
|[CRecordset：： Requery](#requery)|再次執行記錄集的查詢，以重新整理選取的記錄。|
|[CRecordset：： SetAbsolutePosition](#setabsoluteposition)|將記錄集置於對應于指定記錄號碼的記錄上。|
|[CRecordset：： SetBookmark](#setbookmark)|將記錄集放置在書簽所指定的記錄上。|
|[CRecordset：： SetFieldDirty](#setfielddirty)|將目前記錄中指定的欄位標記為已變更。|
|[CRecordset：： SetFieldNull](#setfieldnull)|將目前記錄中指定欄位的值設定為 null （沒有值）。|
|[CRecordset：： SetLockingMode](#setlockingmode)|將鎖定模式設定為「開放式」鎖定（預設值）或「封閉式」鎖定。 決定如何鎖定記錄以進行更新。|
|[CRecordset：： SetParamNull](#setparamnull)|將指定的參數設定為 null （沒有值）。|
|[CRecordset：： SetRowsetCursorPosition](#setrowsetcursorposition)|將資料指標置於資料列集內的指定資料列。|
|[CRecordset：： SetRowsetSize](#setrowsetsize)|指定提取期間您想要取得的記錄數目。|
|[CRecordset：： Update](#update)|藉由將新的或編輯過的資料儲存在資料來源上，完成 `AddNew` 或 `Edit` 作業。|

### <a name="public-data-members"></a>公用資料成員

|名字|描述|
|----------|-----------------|
|[CRecordset：： m_hstmt](#m_hstmt)|包含記錄集的 ODBC 語句控制碼。 輸入 `HSTMT`。|
|[CRecordset：： m_nFields](#m_nfields)|包含記錄集中的欄位資料成員數目。 輸入 `UINT`。|
|[CRecordset：： m_nParams](#m_nparams)|包含記錄集中的參數資料成員數目。 輸入 `UINT`。|
|[CRecordset：： m_pDatabase](#m_pdatabase)|包含將記錄集連接到資料來源之 `CDatabase` 物件的指標。|
|[CRecordset：： m_strFilter](#m_strfilter)|包含指定結構化查詢語言 (SQL) （SQL） `WHERE` 子句的 `CString`。 用來做為篩選準則，只選取符合特定準則的記錄。|
|[CRecordset：： m_strSort](#m_strsort)|包含指定 SQL `ORDER BY` 子句的 `CString`。 用來控制記錄的排序方式。|

## <a name="remarks"></a> 備註

稱為「記錄集」，`CRecordset` 物件通常用於兩種形式：動態集和快照。 動態集會與其他使用者所做的資料更新保持同步。 快照集是資料的靜態視圖。 每個表單都代表一組在記錄集開啟時固定的記錄，但當您滾動到動態集中的記錄時，它會反映後續對記錄所做的變更，由其他使用者或應用程式中的其他記錄集所進行。

> [!NOTE]
>  如果您使用的是資料存取物件（DAO）類別，而不是開放式資料庫連接（ODBC）類別，請改用 [類別[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) ]。 如需詳細資訊，請參閱 [總覽：資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。

若要使用任一種記錄集，您通常會從 `CRecordset`衍生應用程式特定的記錄集類別。 記錄集從資料來源選取記錄，然後您可以：

- 流覽記錄。

- 更新記錄，並指定鎖定模式。

- 篩選記錄集，以限制從資料來源可用的記錄中選取的記錄。

- 排序記錄集。

- 將記錄集參數化，以自訂在執行時間之前不知道的資訊。

若要使用您的類別，請開啟資料庫並建立記錄集物件，並將指標傳遞至您的 `CDatabase` 物件。 然後通話記錄集的 `Open` 成員函式，您可以在其中指定物件是動態集或快照。 呼叫 `Open` 會從資料來源選取資料。 在開啟記錄集物件之後，請使用其成員函式和資料成員來流覽記錄，並對其進行操作。 可用的作業取決於物件是動態集或快照集、是否可更新或唯讀（這取決於開放式資料庫連接（ODBC）資料來源的功能），以及您是否已執行大量資料列提取。 若要重新整理自 `Open` 呼叫之後可能已變更或新增的記錄，請呼叫物件的 `Requery` 成員函式。 呼叫物件的 `Close` 成員函式，並在完成時終結物件。

在衍生的 `CRecordset` 類別中，記錄欄位交換（RFX）或大量記錄欄位交換（Bulk RFX）是用來支援記錄欄位的讀取和更新。

如需有關記錄集和記錄欄位交換的詳細資訊，請參閱 [總覽中的文章：資料庫程式設計](../../data/data-access-programming-mfc-atl.md)、[記錄集（ODBC）](../../data/odbc/recordset-odbc.md)、[記錄集：提取大量（ODBC）](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[記錄欄位交換（RFX）](../../data/odbc/record-field-exchange-rfx.md)中的記錄。 如需專注于動態程式和快照集，請參閱「[動態集](../../data/odbc/dynaset.md)」和「[快照](../../data/odbc/snapshot.md)」文章。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>需求

**標頭：** afxdb。h

##  <a name="addnew"></a>CRecordset：： AddNew

準備將新記錄加入至資料表。

```
virtual void AddNew();
```

### <a name="remarks"></a>備註

您必須呼叫[Requery](#requery)成員函式，才能看到新加入的記錄。 記錄的欄位一開始是 Null。 （在資料庫術語中，Null 表示「沒有值」，而且與中C++的 null 不同）。若要完成此作業，您必須呼叫[Update](#update)成員函式。 `Update` 會將您的變更儲存至資料來源。

> [!NOTE]
>  如果您已執行大量資料列提取，就無法呼叫 `AddNew`。 這會導致失敗的判斷提示。 雖然類別 `CRecordset` 不會提供更新大量資料列的機制，但是您可以使用 ODBC API 函式 `SQLSetPos`來撰寫自己的函式。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

`AddNew` 使用記錄集的欄位資料成員來準備新的空白記錄。 在您呼叫 `AddNew`之後，請在記錄集的欄位資料成員中設定您想要的值。 （您不需要針對此用途呼叫[Edit](#edit)成員函式，請只針對現有的記錄使用 `Edit`）。當您後續呼叫 `Update`時，欄位資料成員中已變更的值會儲存在資料來源上。

> [!CAUTION]
>  如果您在呼叫 `Update`之前，先滾動到新的記錄，則會遺失新的記錄，而且不會提供任何警告。

如果資料來源支援交易，您可以讓您的 `AddNew` 呼叫交易的一部分。 如需交易的詳細資訊，請參閱類別[CDatabase](../../mfc/reference/cdatabase-class.md)。 請注意，在呼叫 `AddNew`之前，您應該先呼叫[CDatabase：： BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) 。

> [!NOTE]
>  若為動態集，新記錄會加入至記錄集做為最後一筆記錄。 新增的記錄不會加入至快照集;您必須呼叫 `Requery` 來重新整理記錄集。

對於尚未呼叫 `Open` 成員函式的記錄集，則不合法地呼叫 `AddNew`。 如果您為無法附加至的記錄集呼叫 `AddNew`，則會擲回 `CDBException`。 您可以藉由呼叫[CanAppend](#canappend)來判斷記錄集是否可更新。

如需詳細資訊，請參閱下列文章：[資料錄集：記錄集更新記錄（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)、[記錄集的方式：加入、更新和刪除記錄（ODBC）](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)和[交易（odbc）](../../data/odbc/transaction-odbc.md)。

### <a name="example"></a>範例

請參閱 [交易的文章：在記錄集（ODBC）](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)中執行交易。

##  <a name="canappend"></a>CRecordset：： CanAppend

判斷先前開啟的記錄集是否可讓您加入新的記錄。

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>傳回值

如果記錄集允許加入新記錄，則為非零。否則為0。 如果您以唯讀方式開啟記錄集，`CanAppend` 將會傳回0。

##  <a name="canbookmark"></a>CRecordset：： CanBookmark

判斷記錄集是否允許您使用書簽來標示記錄。

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>傳回值

如果記錄集支援書簽，則為非零。否則為0。

### <a name="remarks"></a>備註

這個函數與[Open](#open)成員函式之*dwOptions*參數中的 `CRecordset::useBookmarks` 選項無關。 `CanBookmark` 指出給定的 ODBC 驅動程式和資料指標類型是否支援書簽。 `CRecordset::useBookmarks` 指出是否可使用書簽（如果有支援的話）。

> [!NOTE]
>  順向記錄集不支援書簽。

如需書簽和記錄集導覽的詳細資訊，請參閱 [記錄集的文章：書簽和絕對位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 和 [記錄集：滾動（ODBC）](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="cancel"></a>CRecordset：： Cancel

要求資料來源取消進行中的非同步作業，或來自第二個執行緒的進程。

```
void Cancel();
```

### <a name="remarks"></a>備註

請注意，MFC ODBC 類別不再使用非同步處理;若要執行非同步作業，您必須直接呼叫 ODBC API 函數 `SQLSetConnectOption`。 如需詳細資訊，請參閱《 *ODBC SDK 程式設計人員指南》* 中的「非同步執行函式」主題。

##  <a name="cancelupdate"></a>CRecordset：： CancelUpdate

在呼叫[Update](#update)之前，取消任何暫止的更新，由[編輯](#edit)或[AddNew](#addnew)作業所造成。

```
void CancelUpdate();
```

### <a name="remarks"></a>備註

> [!NOTE]
>  此成員函式不適用於使用大量資料列提取的記錄集，因為這類記錄集無法呼叫 `Edit`、`AddNew`或 `Update`。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

如果已啟用自動中途欄位檢查，`CancelUpdate` 會將成員變數還原為 `Edit` 或 `AddNew` 被呼叫之前所擁有的值;否則，任何值變更都會保留。 根據預設，當記錄集開啟時，自動欄位檢查會啟用。 若要停用此功能，您必須在[Open](#open)成員函式的*dwOptions*參數中指定 `CRecordset::noDirtyFieldCheck`。

如需有關更新資料的詳細資訊，請參閱 [記錄集的文章：新增、更新和刪除記錄（ODBC）](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)。

##  <a name="canrestart"></a>CRecordset：： CanRestart

藉由呼叫 `Requery` 成員函式，判斷記錄集是否允許重新開機其查詢（以重新整理其記錄）。

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>傳回值

如果允許重新查詢，則為非零值;否則為0。

##  <a name="canscroll"></a>CRecordset：： CanScroll

判斷記錄集是否允許滾動。

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>傳回值

如果記錄集允許滾動，則為非零。否則為0。

### <a name="remarks"></a>備註

如需有關滾動的詳細資訊，請參閱 [記錄集的文章：滾動（ODBC）](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="cantransact"></a>CRecordset：： CanTransact

判斷記錄集是否允許交易。

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>傳回值

如果記錄集允許交易則為非零;否則為0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱[交易（ODBC）](../../data/odbc/transaction-odbc.md)一文。

##  <a name="canupdate"></a>CRecordset：： CanUpdate

判斷是否可以更新記錄集。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>傳回值

如果可以更新記錄集，則為非零。否則為0。

### <a name="remarks"></a>備註

如果基礎資料來源為唯讀，或當您開啟記錄集時，如果您在*dwOptions*參數中指定 `CRecordset::readOnly`，則記錄集可能是唯讀的。

##  <a name="checkrowseterror"></a>CRecordset：： CheckRowsetError

呼叫以處理在記錄提取期間產生的錯誤。

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>參數

*nRetCode*<br/>
ODBC API 函式傳回碼。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

此虛擬成員函式會處理提取記錄時所發生的錯誤，而且在大量資料列提取期間很有用。 您可能想要考慮覆寫 `CheckRowsetError`，以執行您自己的錯誤處理。

`CheckRowsetError` 會在資料指標導覽作業中自動呼叫，例如 `Open`、`Requery`或任何 `Move` 作業。 它會傳遞 ODBC API 函數 `SQLExtendedFetch`的傳回值。 下表列出*nRetCode*參數的可能值。

|nRetCode|描述|
|--------------|-----------------|
|SQL_SUCCESS|已成功完成函數;沒有其他資訊可供使用。|
|SQL_SUCCESS_WITH_INFO|函數已順利完成，可能發生非嚴重錯誤。 您可以藉由呼叫 `SQLError`來取得其他資訊。|
|SQL_NO_DATA_FOUND|已提取結果集的所有資料列。|
|SQL_ERROR|函數失敗。 您可以藉由呼叫 `SQLError`來取得其他資訊。|
|SQL_INVALID_HANDLE|函數失敗，因為環境控制碼無效、連接控制碼或語句控制碼不正確。 這表示程式設計錯誤。 `SQLError`不提供任何其他資訊。|
|SQL_STILL_EXECUTING|以非同步方式啟動的函式仍在執行中。 請注意，根據預設，MFC 永遠不會將此值傳遞給 `CheckRowsetError`。MFC 會繼續呼叫 `SQLExtendedFetch`，直到不再傳回 SQL_STILL_EXECUTING。|

如需 `SQLError`的詳細資訊，請參閱 Windows SDK。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="close"></a>CRecordset：： Close

關閉記錄集。

```
virtual void Close();
```

### <a name="remarks"></a>備註

ODBC HSTMT 和為記錄集配置的所有記憶體都會解除配置。 通常在呼叫 `Close`之後，如果C++記錄集物件是使用**new**所配置，您就會刪除它。

呼叫 `Close`之後，您可以再次呼叫 `Open`。 這可讓您重複使用記錄集物件。 替代方式是呼叫 `Requery`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

##  <a name="crecordset"></a>CRecordset：： CRecordset

建構 `CRecordset` 物件。

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>參數

*pDatabase*<br/>
包含 `CDatabase` 物件的指標或 Null 值。 如果不是 Null，而且尚未呼叫 `CDatabase` 物件的 `Open` 成員函式來將它連接到資料來源，記錄集就會在其本身的 `Open` 呼叫中，嘗試為您開啟它。 如果您傳遞 Null，則會使用您在使用 ClassWizard 來衍生記錄集類別時所指定的資料來源資訊，為您建立 `CDatabase` 物件的結構並加以連接。

### <a name="remarks"></a>備註

您可以直接使用 `CRecordset`，或從 `CRecordset`衍生應用程式特定的類別。 您可以使用 ClassWizard 來衍生您的記錄集類別。

> [!NOTE]
>  衍生的類別*必須*提供自己的函數。 在衍生類別的函式中，呼叫 `CRecordset::CRecordset`的函式，並將適當的參數傳遞至該函數。

將 Null 傳遞至您的記錄集函式，以自動為您建立 `CDatabase` 物件並為您連接。 這是有用的速記，不需要您在建立記錄集之前，先建立和連接 `CDatabase` 物件。

### <a name="example"></a>範例

如需詳細資訊，請參閱 [記錄集的文章：宣告資料表的類別（ODBC）](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。

##  <a name="delete"></a>CRecordset：:D 刪除

刪除目前的記錄。

```
virtual void Delete();
```

### <a name="remarks"></a>備註

成功刪除之後，記錄集的欄位資料成員會設定為 Null 值，而且您必須明確地呼叫其中一個 `Move` 函數，才能移出已刪除的記錄。 當您移出已刪除的記錄之後，就無法返回它。 如果資料來源支援交易，您可以讓 `Delete` 呼叫交易的一部分。 如需詳細資訊，請參閱[交易（ODBC）](../../data/odbc/transaction-odbc.md)一文。

> [!NOTE]
>  如果您已執行大量資料列提取，就無法呼叫 `Delete`。 這會導致失敗的判斷提示。 雖然類別 `CRecordset` 不會提供更新大量資料列的機制，但是您可以使用 ODBC API 函式 `SQLSetPos`來撰寫自己的函式。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

> [!CAUTION]
>  記錄集必須是可更新的，而且當您呼叫 `Delete`時，記錄集中必須有有效的記錄。否則，就會發生錯誤。 例如，如果您刪除記錄，但在再次呼叫 `Delete` 之前，未滾動到新的記錄，`Delete` 會擲回[CDBException](../../mfc/reference/cdbexception-class.md)。

不同于[AddNew](#addnew)和[Edit](#edit)，`Delete` 的呼叫之後不會呼叫[Update](#update)。 如果 `Delete` 呼叫失敗，欄位資料成員會保持不變。

### <a name="example"></a>範例

這個範例會顯示在函數框架上建立的記錄集。 此範例假設存在 `m_dbCust`，即類型的成員變數 `CDatabase` 已經連接到資料來源。

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

##  <a name="dobulkfieldexchange"></a>CRecordset：:D oBulkFieldExchange

呼叫以將資料來源中的大量資料列交換到記錄集。 執行大量記錄欄位交換（Bulk RFX）。

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>參數

*pFX*<br/>
[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件的指標。 架構已經設定此物件來指定欄位交換作業的內容。

### <a name="remarks"></a>備註

實作用大量資料列提取時，架構會呼叫這個成員函式，自動將資料從資料來源傳送到您的記錄集物件。 `DoBulkFieldExchange` 也會將您的參數資料成員（如果有的話）系結至記錄集選取之 SQL 語句字串中的參數預留位置。

如果未執行大量資料列提取，架構會呼叫[DoFieldExchange](#dofieldexchange)。 若要執行大量資料列提取，您必須在[Open](#open)成員函式中指定*dwOptions*參數的 `CRecordset::useMultiRowFetch` 選項。

> [!NOTE]
> 只有當您使用衍生自 `CRecordset`的類別時，才可以使用 `DoBulkFieldExchange`。 如果您已直接從 `CRecordset`建立記錄集物件，則必須呼叫[GetFieldValue](#getfieldvalue)成員函式來取出資料。

大量記錄欄位交換（Bulk RFX）類似于記錄欄位交換（RFX）。 資料會自動從資料來源傳送到記錄集物件。 不過，您無法呼叫 `AddNew`、`Edit`、`Delete`或 `Update` 來將變更傳送回資料來源。 類別 `CRecordset` 目前未提供更新大量資料列的機制;不過，您可以使用 ODBC API 函數 `SQLSetPos`來撰寫自己的函式。

請注意，ClassWizard 不支援大量記錄欄位交換;因此，您必須撰寫對 Bulk RFX 函數的呼叫，以手動覆寫 `DoBulkFieldExchange`。 如需這些函數的詳細資訊，請參閱[記錄欄位交換](../../mfc/reference/record-field-exchange-functions.md)函式主題。

如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 如需相關資訊，請參閱[記錄欄位交換（RFX）](../../data/odbc/record-field-exchange-rfx.md)一文。

##  <a name="dofieldexchange"></a>CRecordset：:D oFieldExchange

呼叫以在記錄集的欄位資料成員和資料來源上的對應記錄之間交換資料（雙向）。 實行記錄欄位交換（RFX）。

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>參數

*pFX*<br/>
[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件的指標。 架構已經設定此物件來指定欄位交換作業的內容。

### <a name="remarks"></a>備註

未執行大量資料列提取時，架構會呼叫這個成員函式，在記錄集物件的欄位資料成員和資料來源上目前記錄的對應資料行之間，自動交換資料。 `DoFieldExchange` 也會將您的參數資料成員（如果有的話）系結至記錄集選取之 SQL 語句字串中的參數預留位置。

如果執行大量資料列提取，架構會呼叫[DoBulkFieldExchange](#dobulkfieldexchange)。 若要執行大量資料列提取，您必須在[Open](#open)成員函式中指定*dwOptions*參數的 `CRecordset::useMultiRowFetch` 選項。

> [!NOTE]
> 只有當您使用衍生自 `CRecordset`的類別時，才可以使用 `DoFieldExchange`。 如果您已直接從 `CRecordset`建立記錄集物件，則必須呼叫[GetFieldValue](#getfieldvalue)成員函式來取出資料。

欄位資料的交換（稱為記錄欄位交換（RFX））可以雙向運作：從記錄集物件的欄位資料成員，到資料來源上記錄的欄位，以及從資料來源的記錄到記錄集物件。

執行衍生記錄集類別的 `DoFieldExchange` 時，您通常必須採取的動作是使用 ClassWizard 建立類別，並指定欄位資料成員的名稱和資料類型。 您也可以將程式碼新增至 ClassWizard 寫入的內容，以指定參數資料成員，或處理您動態繫結的任何資料行。 如需詳細資訊，請參閱 [記錄集的文章：動態地繫結資料行 (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。

當您使用 ClassWizard 宣告您的衍生記錄集類別時，嚮導會為您撰寫 `DoFieldExchange` 的覆寫，如下列範例所示：

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

如需 RFX 函數的詳細資訊，請參閱主題[記錄欄位交換](../../mfc/reference/record-field-exchange-functions.md)函式。

如需有關 `DoFieldExchange`的進一步範例和詳細資料，請參閱 [記錄欄位交換的文章：RFX 的運作方式](../../data/odbc/record-field-exchange-how-rfx-works.md)。 如需 RFX 的一般資訊，請參閱[記錄欄位交換](../../data/odbc/record-field-exchange-rfx.md)一文。

##  <a name="edit"></a>CRecordset：： Edit

允許對目前記錄進行變更。

```
virtual void Edit();
```

### <a name="remarks"></a>備註

呼叫 `Edit`之後，您可以直接重設欄位資料成員的值，藉以變更它們。 當您後續呼叫[Update](#update)成員函式以儲存資料來源的變更時，作業就會完成。

> [!NOTE]
>  如果您已執行大量資料列提取，就無法呼叫 `Edit`。 這會導致失敗的判斷提示。 雖然類別 `CRecordset` 不會提供更新大量資料列的機制，但是您可以使用 ODBC API 函式 `SQLSetPos`來撰寫自己的函式。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

`Edit` 儲存記錄集的資料成員值。 如果您呼叫 `Edit`、進行變更，然後再次呼叫 `Edit`，則記錄的值會還原為第一次 `Edit` 呼叫之前的內容。

在某些情況下，您可能想要將資料行設為 Null （不包含任何資料）來更新它。 若要這麼做，請使用 TRUE 的參數呼叫[SetFieldNull](#setfieldnull) ，將欄位標記為 Null;這也會導致更新資料行。 如果您想要將欄位寫入至資料來源，即使其值尚未變更，請呼叫[SetFieldDirty](#setfielddirty) ，並將參數設為 TRUE。 即使欄位具有 Null 值，也可以這麼做。

如果資料來源支援交易，您可以讓 `Edit` 呼叫交易的一部分。 請注意，在呼叫 `Edit` 之前，以及在開啟記錄集之後，您應該呼叫[CDatabase：： BeginTrans](../../mfc/reference/cdatabase-class.md#begintrans) 。 另請注意，呼叫[CDatabase：： CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)並不是呼叫 `Update` 來完成 `Edit` 作業的替代方案。 如需交易的詳細資訊，請參閱類別[CDatabase](../../mfc/reference/cdatabase-class.md)。

根據目前的鎖定模式而定，要更新的記錄可能會被 `Edit` 鎖定，直到您呼叫 `Update` 或滾動到另一筆記錄為止，或是只有在 `Edit` 呼叫期間才會鎖定。 您可以使用[SetLockingMode](#setlockingmode)來變更鎖定模式。

如果您在呼叫 `Update`之前，先滾動到新的記錄，則會還原目前記錄的先前值。 如果您為無法更新的記錄集呼叫 `Edit`，或是沒有目前的記錄，就會擲回 `CDBException`。

如需詳細資訊，請參閱[交易（ODBC）](../../data/odbc/transaction-odbc.md)和 [記錄集的文章：鎖定記錄（ODBC）](../../data/odbc/recordset-locking-records-odbc.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

##  <a name="flushresultset"></a>CRecordset：： FlushResultSet

如果有多個結果集，則會抓取預先定義之查詢（預存程式）的下一個結果集。

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>傳回值

如果要抓取更多結果集，則為非零值;否則為0。

### <a name="remarks"></a>備註

只有當您完全完成目前結果集上的資料指標時，才應該呼叫 `FlushResultSet`。 請注意，當您藉由呼叫 `FlushResultSet`來取出下一個結果集時，您的資料指標在該結果集上無效;呼叫 `FlushResultSet`之後，您應該呼叫[MoveNext](#movenext)成員函式。

如果預先定義的查詢使用輸出參數或輸入/輸出參數，您必須呼叫 `FlushResultSet`，直到它傳回 `FALSE` （值0），才能取得這些參數值。

`FlushResultSet` 會呼叫 ODBC API 函數 `SQLMoreResults`。 如果 `SQLMoreResults` 傳回 SQL_ERROR 或 SQL_INVALID_HANDLE，則 `FlushResultSet` 將會擲回例外狀況。 如需 `SQLMoreResults`的詳細資訊，請參閱 Windows SDK。

如果您想要呼叫 `FlushResultSet`，您的預存程式必須具有系結欄位。

### <a name="example"></a>範例

下列程式碼假設 `COutParamRecordset` 是以具有輸入參數和輸出參數的預先定義查詢為基礎的 `CRecordset`衍生物件，並具有多個結果集。 請注意[DoFieldExchange](#dofieldexchange)覆寫的結構。

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

##  <a name="getbookmark"></a>CRecordset：： GetBookmark

取得目前記錄的書簽值。

```
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>參數

*varBookmark*<br/>
[CDBVariant](../../mfc/reference/cdbvariant-class.md)物件的參考，代表目前記錄上的書簽。

### <a name="remarks"></a>備註

若要判斷記錄集上是否支援書簽，請呼叫[CanBookmark](#canbookmark)。 若要讓書簽可供使用（如果支援的話），您必須在[Open](#open)成員函式的*dwOptions*參數中設定 `CRecordset::useBookmarks` 選項。

> [!NOTE]
>  如果書簽不受支援或無法使用，則呼叫 `GetBookmark` 會導致擲回例外狀況。 順向記錄集不支援書簽。

`GetBookmark` 將目前記錄的書簽值指派給 `CDBVariant` 物件。 若要在移至不同的記錄之後隨時返回該記錄，請使用對應的 `CDBVariant` 物件來呼叫[SetBookmark](#setbookmark) 。

> [!NOTE]
>  在特定記錄集作業之後，書簽可能不再有效。 例如，如果您呼叫後面接著 `Requery`的 `GetBookmark`，可能就無法使用 `SetBookmark`來返回記錄。 呼叫[CDatabase：： GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) ，以檢查您是否可以安全地呼叫 `SetBookmark`。

如需書簽和記錄集導覽的詳細資訊，請參閱 [記錄集的文章：書簽和絕對位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 和 [記錄集：滾動（ODBC）](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="getdefaultconnect"></a>CRecordset：： GetDefaultConnect

呼叫以取得預設連接字串。

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>傳回值

包含預設連接字串的 `CString`。

### <a name="remarks"></a>備註

架構會呼叫這個成員函式，以取得記錄集所依據之資料來源的預設連接字串。 ClassWizard 會藉由識別您在 ClassWizard 中使用的相同資料來源來為您實作為此函式，以取得資料表和資料行的相關資訊。 在開發您的應用程式時，您可能會發現依賴此預設連接會很方便。 但預設連接可能不適合您應用程式的使用者。 如果是這種情況，您應該重新實現此函式，並捨棄 ClassWizard 的版本。 如需連接字串的詳細資訊，請參閱[資料來源（ODBC）](../../data/odbc/data-source-odbc.md)一文。

##  <a name="getdefaultsql"></a>CRecordset：： GetDefaultSQL

呼叫以取得要執行的預設 SQL 字串。

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>傳回值

包含預設 SQL 語句的 `CString`。

### <a name="remarks"></a>備註

架構會呼叫這個成員函式，以取得記錄集所依據的預設 SQL 語句。 這可能是資料表名稱或 SQL **SELECT**語句。

您可以使用 ClassWizard 宣告您的記錄集類別，間接定義預設的 SQL 語句，而 ClassWizard 會為您執行這項工作。

如果您需要 SQL 語句字串供自己使用，請呼叫 `GetSQL`，這會傳回用來選取記錄集記錄的 SQL 語句（當它開啟時）。 您可以在 `GetDefaultSQL`的類別覆寫中編輯預設的 SQL 字串。 例如，您可以使用**call**語句來指定對預先定義查詢的呼叫。 （請注意，如果您編輯 `GetDefaultSQL`，則也需要修改 `m_nFields` 以符合資料來源中的資料行數目）。

如需詳細資訊，請參閱 [記錄集的文章：宣告資料表的類別（ODBC）](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。

> [!CAUTION]
>  如果架構無法識別資料表名稱、提供多個資料表名稱，或無法解讀**CALL**語句，則資料表名稱會是空的。 請注意，使用**CALL**語句時，您不能在大括弧和**CALL**關鍵字之間插入空白字元，也不應該在大括弧之前或**select**語句中的**select**關鍵字之前插入空白字元。

##  <a name="getfieldvalue"></a>CRecordset：： GetFieldValue

抓取目前記錄中的欄位資料。

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
欄位的名稱。

*varValu*e a [CDBVariant](../../mfc/reference/cdbvariant-class.md)物件的參考，它會儲存域值。

*nFieldType*<br/>
欄位的 ODBC C 資料類型。 使用預設值 DEFAULT_FIELD_TYPE，會強制 `GetFieldValue` 根據下表來決定 SQL 資料類型的 C 資料類型。 否則，您可以直接指定資料類型，或選擇相容的資料類型。例如，您可以將任何資料類型儲存到 SQL_C_CHAR 中。

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

如需有關 ODBC 資料類型的詳細資訊，請參閱 Windows SDK 附錄 D 中的「SQL 資料類型」和「C 資料類型」主題。

*nIndex*<br/>
欄位之以零為起始的索引。

*strValue*<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的參考，它會儲存轉換成文字的域值，而不論欄位的資料類型為何。

### <a name="remarks"></a>備註

您可以依名稱或索引來查閱欄位。 您可以將域值儲存在 `CDBVariant` 物件或 `CString` 物件中。

如果您已執行大量資料列提取，目前的記錄一律會放在資料列集內的第一筆記錄。 若要在指定資料列集內的記錄上使用 `GetFieldValue`，您必須先呼叫[SetRowsetCursorPosition](#setrowsetcursorposition)成員函式，將資料指標移至該資料列集內所需的資料列。 然後，針對該資料列呼叫 `GetFieldValue`。 若要執行大量資料列提取，您必須在[Open](#open)成員函式中指定*dwOptions*參數的 `CRecordset::useMultiRowFetch` 選項。

您可以使用 `GetFieldValue` 在執行時間以動態方式提取欄位，而不是在設計階段以靜態方式系結它們。 例如，如果您已直接從 `CRecordset`宣告記錄集物件，則必須使用 `GetFieldValue` 來抓取欄位資料;不會實作為記錄欄位交換（RFX）或大量記錄欄位交換（Bulk RFX）。

> [!NOTE]
>  如果您宣告記錄集物件，而不是從 `CRecordset`衍生，則不會載入 ODBC 資料指標程式庫。 資料指標程式庫要求記錄集至少有一個系結資料行;不過，當您直接使用 `CRecordset` 時，並不會系結任何資料行。 成員函式[CDatabase：： microsoft.office.interop.visio.documents.open](../../mfc/reference/cdatabase-class.md#openex)和[CDatabase：： Open](../../mfc/reference/cdatabase-class.md#open)控制項是否將載入資料指標程式庫。

`GetFieldValue` 會呼叫 ODBC API 函數 `SQLGetData`。 如果您的驅動程式輸出域值的實際長度 SQL_NO_TOTAL 值，`GetFieldValue` 就會擲回例外狀況。 如需 `SQLGetData`的詳細資訊，請參閱 Windows SDK。

### <a name="example"></a>範例

下列範例程式碼說明直接從 `CRecordset`宣告之記錄集物件 `GetFieldValue` 的呼叫。

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
>  不同于 DAO 類別 `CDaoRecordset`，`CRecordset` 沒有 `SetFieldValue` 的成員函式。 如果您直接從 `CRecordset`建立物件，它實際上是唯讀的。

如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="getodbcfieldcount"></a>CRecordset：： GetODBCFieldCount

抓取記錄集物件中的欄位總數。

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>傳回值

記錄集中的欄位數目。

### <a name="remarks"></a>備註

如需建立記錄集的詳細資訊，請參閱 [記錄集的文章：建立和關閉記錄集（ODBC）](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。

##  <a name="getodbcfieldinfo"></a>CRecordset：： GetODBCFieldInfo

取得有關記錄集中之欄位的資訊。

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
欄位的名稱。

*fieldinfo*<br/>
`CODBCFieldInfo` 結構的參考。

*nIndex*<br/>
欄位之以零為起始的索引。

### <a name="remarks"></a>備註

函數的其中一個版本可讓您依名稱查閱欄位。 另一個版本可讓您依索引查閱欄位。

如需傳回之資訊的相關說明，請參閱[CODBCFieldInfo](../../mfc/reference/codbcfieldinfo-structure.md)結構。

如需建立記錄集的詳細資訊，請參閱 [記錄集的文章：建立和關閉記錄集（ODBC）](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。

##  <a name="getrecordcount"></a>CRecordset：： GetRecordCount

決定記錄集的大小。

```
long GetRecordCount() const;
```

### <a name="return-value"></a>傳回值

記錄集中的記錄數目;如果記錄集沒有包含任何記錄，則為 0;如果無法判斷記錄計數，則為-1。

### <a name="remarks"></a>備註

> [!CAUTION]
>  記錄計數會保留為「上限標準」，但當使用者在記錄中移動時，就會看到最高編號的記錄。 只有在使用者移至最後一筆記錄之後，才知道記錄總數。 基於效能的考慮，當您呼叫 `MoveLast`時，不會更新計數。 若要自行計算記錄，請重複呼叫 `MoveNext`，直到 `IsEOF` 傳回非零值為止。 透過 `CRecordset:AddNew` 和 `Update` 新增記錄會增加計數;透過 `CRecordset::Delete` 刪除記錄會減少計數。

##  <a name="getrowsetsize"></a>CRecordset：： GetRowsetSize

針對您想要在指定的提取期間取得的資料列數目，取得目前的設定。

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>傳回值

要在指定的提取期間取得的資料列數目。

### <a name="remarks"></a>備註

如果您使用大量資料列提取，則當記錄集開啟時的預設資料列集大小為 25;否則，它會是1。

若要執行大量資料列提取，您必須在[Open](#open)成員函式的*dwOptions*參數中指定 `CRecordset::useMultiRowFetch` 選項。 若要變更資料列集大小的設定，請呼叫[SetRowsetSize](#setrowsetsize)。

如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="getrowsfetched"></a>CRecordset：： GetRowsFetched

判斷提取之後實際取出的記錄數目。

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>傳回值

在給定的提取之後，從資料來源抓取的資料列數目。

### <a name="remarks"></a>備註

當您已執行大量資料列提取時，這會很有用。 資料列集大小通常會指出將從提取抓取多少資料列;不過，記錄集中的資料列總數也會影響資料列集內所要抓取的資料列數目。 例如，如果您的記錄集有10筆記錄，其中資料列集大小設定為4，然後藉由呼叫 `MoveNext` 來迴圈流覽記錄集，將會導致最終資料列集只有2筆記錄。

若要執行大量資料列提取，您必須在[Open](#open)成員函式的*dwOptions*參數中指定 `CRecordset::useMultiRowFetch` 選項。 若要指定資料列集大小，請呼叫[SetRowsetSize](#setrowsetsize)。

如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

##  <a name="getrowstatus"></a>CRecordset：： GetRowStatus

取得目前資料列集中的資料列狀態。

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>參數

*wRow*<br/>
目前資料列集中，資料列的以一為基的位置。 這個值的範圍可以從1到資料列集的大小。

### <a name="return-value"></a>傳回值

資料列的狀態值。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

`GetRowStatus` 會傳回一個值，該值表示自從上次從資料來源抓取之後，任何狀態變更，或未提取對應至*wRow*的任何資料列。 下表列出可能的傳回值。

|狀態值|描述|
|------------------|-----------------|
|SQL_ROW_SUCCESS|資料列未變更。|
|SQL_ROW_UPDATED|資料列已更新。|
|SQL_ROW_DELETED|已刪除資料列。|
|SQL_ROW_ADDED|已新增資料列。|
|SQL_ROW_ERROR|因為發生錯誤，所以資料列 unretrievable。|
|SQL_ROW_NOROW|沒有對應至*wRow*的資料列。|

如需詳細資訊，請參閱 Windows SDK 中的 ODBC API 函數 `SQLExtendedFetch`。

##  <a name="getstatus"></a>CRecordset：： GetStatus

判斷記錄集中目前記錄的索引，以及是否已看到最後一筆記錄。

```
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>參數

*rStatus*<br/>
對 `CRecordsetStatus` 物件的參考。 如需詳細資訊，請參閱＜備註＞一節。

### <a name="remarks"></a>備註

`CRecordset` 嘗試追蹤索引，但在某些情況下，這可能不可行。 如需說明，請參閱[GetRecordCount](#getrecordcount) 。

`CRecordsetStatus` 結構具有下列格式：

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

`CRecordsetStatus` 的兩個成員具有下列意義：

- `m_lCurrentRecord` 包含記錄集內目前記錄之以零為起始的索引（如果知道的話）。 如果無法判斷索引，這個成員就會包含 AFX_CURRENT_RECORD_UNDEFINED （-2）。 如果 `IsBOF` 為 TRUE （空的記錄集或在第一筆記錄之前嘗試滾動），則 `m_lCurrentRecord` 會設定為 AFX_CURRENT_RECORD_BOF （-1）。 如果是第一筆記錄，則會設定為0、第二筆記錄1等等。

- 如果已決定記錄集中的記錄總數，則 `m_bRecordCountFinal` 非零值。 一般來說，這必須從記錄集的開頭開始並呼叫 `MoveNext`，直到 `IsEOF` 傳回非零值為止。 如果這個成員為零，`GetRecordCount`傳回的記錄計數（如果不是-1），就只會是記錄的「上限標準」計數。

##  <a name="getsql"></a>CRecordset：： GetSQL

呼叫這個成員函式，以取得在開啟記錄集的記錄時，用來選取它的 SQL 語句。

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>傳回值

包含 SQL 語句之 `CString` 的**const**參考。

### <a name="remarks"></a>備註

這通常會是 SQL **SELECT**語句。 `GetSQL` 所傳回的字串是唯讀的。

`GetSQL` 所傳回的字串通常與您在*lpszSQL*參數中傳遞至記錄集的任何字串不同，`Open` 成員函式。 這是因為記錄集會根據您傳遞給 `Open`的內容、您使用 ClassWizard 所指定的內容、您在 `m_strFilter` 和 `m_strSort` 資料成員中指定的內容，以及您所指定的任何參數，來建立完整的 SQL 語句。 如需記錄集如何構造此 SQL 語句的詳細資訊，請參閱 [記錄集的文章：記錄集如何選取記錄（ODBC）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。

> [!NOTE]
>  只有在呼叫[Open](#open)之後，才呼叫這個成員函式。

##  <a name="gettablename"></a>CRecordset：： GetTableName

取得記錄集查詢所依據的 SQL 資料表名稱。

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>傳回值

如果記錄集是以資料表為基礎，則為包含資料表名稱之 `CString` 的**const**參考。否則為空字串。

### <a name="remarks"></a>備註

只有當記錄集是以資料表為基礎，而不是多個資料表或預先定義的查詢（預存程式）的聯結時，`GetTableName` 才有效。 名稱是唯讀的。

> [!NOTE]
>  只有在呼叫[Open](#open)之後，才呼叫這個成員函式。

##  <a name="isbof"></a>CRecordset：： IsBOF

如果記錄集已放在第一筆記錄之前，則傳回非零。 沒有目前的記錄。

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>傳回值

如果記錄集不包含任何記錄，或如果您在第一筆記錄之前向前滾動，則為非零。否則為0。

### <a name="remarks"></a>備註

請先呼叫這個成員函式，然後再從記錄中進行滾動，以瞭解您是否已經在記錄集的第一筆記錄之前。 您也可以搭配 `IsEOF` 使用 `IsBOF`，以判斷記錄集是否包含任何記錄或是否為空白。 在您呼叫 `Open`之後，如果記錄集沒有包含任何記錄，`IsBOF` 會傳回非零值。當您開啟至少有一筆記錄的記錄集時，第一筆記錄是目前的記錄，`IsBOF` 傳回0。

如果第一筆記錄是目前的記錄，而您呼叫 `MovePrev`，`IsBOF` 後續會傳回非零值。 如果 `IsBOF` 傳回非零值，而您呼叫 `MovePrev`，就會發生錯誤。 如果 `IsBOF` 傳回非零值，則表示目前的記錄未定義，而且任何需要目前記錄的動作都會導致錯誤。

### <a name="example"></a>範例

這個範例會使用 `IsBOF` 和 `IsEOF` 來偵測記錄集的限制，因為程式碼會在兩個方向的整個記錄集中進行滾動。

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

##  <a name="isdeleted"></a>CRecordset：： IsDeleted

判斷目前的記錄是否已刪除。

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>傳回值

如果記錄集位於已刪除的記錄上，則為非零。否則為0。

### <a name="remarks"></a>備註

如果您流覽至記錄，而 `IsDeleted` 傳回 TRUE （非零），則您必須先滾動到另一筆記錄，才能執行任何其他記錄集作業。

`IsDeleted` 的結果取決於許多因素，例如您的記錄集類型、是否可更新您的記錄集、是否在開啟記錄集時指定了 [`CRecordset::skipDeletedRecords`] 選項、您的驅動程式是否封裝刪除的記錄，以及是否有多個使用者。

如需 `CRecordset::skipDeletedRecords` 和驅動程式封裝的詳細資訊，請參閱[Open](#open)成員函式。

> [!NOTE]
>  如果您已執行大量資料列提取，則不應呼叫 `IsDeleted`。 相反地，請呼叫[GetRowStatus](#getrowstatus)成員函式。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="iseof"></a>CRecordset：： IsEOF

如果記錄集已放在最後一筆記錄之後，則傳回非零。 沒有目前的記錄。

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>傳回值

如果記錄集不包含任何記錄，或如果您已滾動到最後一筆記錄之外，則為非零。否則為0。

### <a name="remarks"></a>備註

當您從記錄中滾動記錄來呼叫這個成員函式，以瞭解您是否已超過記錄集的最後一筆記錄。 您也可以使用 `IsEOF` 來判斷記錄集是否包含任何記錄或是否為空白。 在您呼叫 `Open`之後，如果記錄集沒有包含任何記錄，`IsEOF` 會傳回非零值。 當您開啟至少有一筆記錄的記錄集時，第一筆記錄是目前的記錄，`IsEOF` 傳回0。

當您呼叫 `MoveNext`時，如果最後一筆記錄是目前的記錄，`IsEOF` 後續會傳回非零值。 如果 `IsEOF` 傳回非零值，而您呼叫 `MoveNext`，就會發生錯誤。 如果 `IsEOF` 傳回非零值，則表示目前的記錄未定義，而且任何需要目前記錄的動作都會導致錯誤。

### <a name="example"></a>範例

請參閱[IsBOF](#isbof)的範例。

##  <a name="isfielddirty"></a>CRecordset：： IsFieldDirty

判斷指定的欄位資料成員在呼叫[編輯](#edit)或[AddNew](#addnew)之後是否已變更。

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
您想要檢查其狀態之欄位資料成員的指標，或為 Null 以判斷是否有任何欄位已變更。

### <a name="return-value"></a>傳回值

如果指定的欄位資料成員自呼叫 `AddNew` 或 `Edit`之後已變更，則為非零值;否則為0。

### <a name="remarks"></a>備註

當目前的記錄由 `CRecordset` 的[Update](#update)成員函式（在呼叫 `Edit` 或 `AddNew`之後）進行更新時，所有中途欄位資料成員中的資料都會傳送至資料來源上的記錄。

> [!NOTE]
>  此成員函式不適用於使用大量資料列提取的記錄集。 如果您已執行大量資料列提取，則 `IsFieldDirty` 一律會傳回 FALSE，且會導致失敗的判斷提示。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

呼叫 `IsFieldDirty` 將會重設先前呼叫[SetFieldDirty](#setfielddirty)的效果，因為欄位的中途狀態會重新評估。 在 `AddNew` 案例中，如果目前的域值與虛擬 null 值不同，則欄位狀態會設定為 [已變更]。 在 `Edit` 案例中，如果域值與快取的值不同，則欄位狀態會設定為 [已變更]。

`IsFieldDirty` 是透過[DoFieldExchange](#dofieldexchange)來執行。

如需有關中途旗標的詳細資訊，請參閱 [記錄集的文章：記錄集如何選取記錄（ODBC）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。

##  <a name="isfieldnull"></a>CRecordset：： IsFieldNull

如果目前記錄中的指定欄位為 Null （沒有值），則傳回非零。

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
您想要檢查其狀態之欄位資料成員的指標，或為 Null 以判斷是否有任何欄位為 Null。

### <a name="return-value"></a>傳回值

如果指定的欄位資料成員標示為 Null，則為非零;否則為0。

### <a name="remarks"></a>備註

呼叫這個成員函式，以判斷是否已將記錄集的指定欄位資料成員標示為 Null。 （在資料庫術語中，Null 表示「沒有值」，而且與中C++的 null 不同）。如果欄位資料成員標示為 Null，它會被視為目前記錄中沒有任何值的資料行。

> [!NOTE]
>  此成員函式不適用於使用大量資料列提取的記錄集。 如果您已執行大量資料列提取，則 `IsFieldNull` 一律會傳回 FALSE，且會導致失敗的判斷提示。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

`IsFieldNull` 是透過[DoFieldExchange](#dofieldexchange)來執行。

##  <a name="isfieldnullable"></a>CRecordset：： IsFieldNullable

如果目前記錄中的指定欄位可以設定為 Null （沒有值），則傳回非零。

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
您想要檢查其狀態之欄位資料成員的指標，或為 Null，以判斷是否有任何欄位可以設定為 Null 值。

### <a name="remarks"></a>備註

呼叫這個成員函式，以判斷指定的欄位資料成員是否為 "nullable" （可以設定為 Null 值;C++ Null 與 null 不同，在資料庫術語中，表示「沒有值」）。

> [!NOTE]
>  如果您已執行大量資料列提取，就無法呼叫 `IsFieldNullable`。 相反地，請呼叫[GetODBCFieldInfo](#getodbcfieldinfo)成員函式，以判斷欄位是否可設定為 Null 值。 請注意，不論您是否已執行大量資料列提取，一律可以呼叫 `GetODBCFieldInfo`。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

不可以是 Null 的欄位必須有值。 如果您嘗試在加入或更新記錄時，將這類欄位設定為 Null，則資料來源會拒絕新增或更新，而且[update](#update)將會擲回例外狀況。 當您呼叫 `Update`，而不是呼叫[SetFieldNull](#setfieldnull)時，就會發生例外狀況。

針對函式的第一個引數使用 Null，只會將函式套用至 `outputColumn` 欄位，而不是 `param` 欄位。 例如，呼叫

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

只會將 `outputColumn` 欄位設定為 Null;`param` 欄位將不會受到影響。

若要處理 `param` 欄位，您必須提供您想要使用之個別 `param` 的實際位址，例如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

這表示您無法將所有 `param` 欄位都設定為 Null，就像您可以使用 `outputColumn` 欄位一樣。

`IsFieldNullable` 是透過[DoFieldExchange](#dofieldexchange)來執行。

##  <a name="isopen"></a>CRecordset：： IsOpen

判斷記錄集是否已開啟。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果先前已通話記錄集物件的[Open](#open)或[Requery](#requery)成員函式，而且尚未關閉記錄集，則為非零。否則為0。

##  <a name="m_hstmt"></a>CRecordset：： m_hstmt

包含與記錄集相關聯之 ODBC 語句資料結構（屬於 HSTMT 類型）的控制碼。

### <a name="remarks"></a>備註

ODBC 資料來源的每個查詢都會與 HSTMT 相關聯。

> [!CAUTION]
>  在呼叫[Open](#open)之前，請勿使用 `m_hstmt`。

通常您不需要直接存取 HSTMT，但您可能需要它來直接執行 SQL 語句。 `CDatabase` 類別的 `ExecuteSQL` 成員函式提供使用 `m_hstmt`的範例。

##  <a name="m_nfields"></a>CRecordset：： m_nFields

包含記錄集類別中的欄位資料成員數目;也就是記錄集從資料來源選取的資料行數目。

### <a name="remarks"></a>備註

記錄集類別的處理常式必須使用正確的數位來初始化 `m_nFields`。 如果您未執行大量資料列提取，當您使用它來宣告記錄集類別時，ClassWizard 會為您寫入此初始化。 您也可以手動撰寫它。

架構會使用這個數位來管理欄位資料成員與資料來源上目前記錄之對應資料行之間的互動。

> [!CAUTION]
>  這個數位必須對應至 `DoFieldExchange` 中註冊的「輸出資料行」數目，或使用參數 `CFieldExchange::outputColumn`呼叫[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)之後 `DoBulkFieldExchange`。

您可以動態地系結資料行，如 < 記錄集：動態地系結資料行。」 如果您這樣做，您必須增加 `m_nFields` 中的計數，以反映您的 `DoFieldExchange` 中的 RFX 或 Bulk RFX 函式呼叫數目，或動態繫結資料行的 `DoBulkFieldExchange` 成員函式。

如需詳細資訊，請參閱 [記錄集的文章：動態地系結資料行（ODBC）](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) 和 [記錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

### <a name="example"></a>範例

請參閱 [記錄欄位交換文章：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

##  <a name="m_nparams"></a>CRecordset：： m_nParams

包含記錄集類別中的參數資料成員數目;也就是，與記錄集的查詢一起傳遞的參數數目。

### <a name="remarks"></a>備註

如果您的記錄集類別具有任何參數資料成員，則類別的函式必須使用正確的數位來初始化 `m_nParams`。 `m_nParams` 的值預設為0。 如果您加入參數資料成員（必須手動執行），您也必須手動加入類別函式中的初始化，以反映參數的數目（至少必須與您 `m_strFilter` 或 `m_strSort` 字串中 ' ' 預留位置的數目一樣大）。

架構在參數化記錄集的查詢時，會使用這個數位。

> [!CAUTION]
>  這個數位必須對應至 `DoFieldExchange` 中註冊的 "params" 數目，或在呼叫具有 `CFieldExchange::inputParam`、`CFieldExchange::param`、`CFieldExchange::outputParam`或 `CFieldExchange::inoutParam`參數值的[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)之後 `DoBulkFieldExchange`。

### <a name="example"></a>範例

  請參閱 [記錄集的文章：參數化記錄集（ODBC）](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) 和 [記錄欄位交換：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

##  <a name="m_pdatabase"></a>CRecordset：： m_pDatabase

包含將記錄集連接到資料來源之 `CDatabase` 物件的指標。

### <a name="remarks"></a>備註

這個變數是以兩種方式設定。 一般而言，當您在建立記錄集物件時，會將指標傳遞至已連接的 `CDatabase` 物件。 如果您改為傳遞 Null，`CRecordset` 會為您建立 `CDatabase` 物件，並將其連接。 不論是哪一種情況，`CRecordset` 都會將指標儲存在此變數中。

一般來說，您不需要直接使用儲存在 `m_pDatabase`中的指標。 不過，如果您將自己的延伸模組寫入 `CRecordset`，您可能需要使用指標。 例如，如果您擲回自己的 `CDBException`，您可能需要指標。 或者，如果您需要使用相同的 `CDatabase` 物件（例如執行交易、設定超時或呼叫 `CDatabase` 類別的 `ExecuteSQL` 成員函式）來執行某些作業，則您可能會需要它，以直接執行 SQL 語句。

##  <a name="m_strfilter"></a>CRecordset：： m_strFilter

在您建立記錄集物件之後，但是在呼叫其 `Open` 成員函式之後，請使用此資料成員來儲存包含 SQL **WHERE**子句的 `CString`。

### <a name="remarks"></a>備註

記錄集會使用此字串來限制（或篩選）它在 `Open` 或 `Requery` 呼叫期間所選取的記錄。 這適用于選取記錄的子集，例如「所有以加州為基礎的銷售人員」（「州 = CA」）。 **WHERE**子句的 ODBC SQL 語法為

`WHERE search-condition`

請注意，您不會在字串中包含**WHERE**關鍵字。 架構會提供它。

您也可以參數化篩選字串，方法是在其中放置 ' ' 預留位置，在類別中為每個預留位置宣告參數資料成員，並在執行時間將參數傳遞至記錄集。 這可讓您在執行時間建立篩選準則。 如需詳細資訊，請參閱 [記錄集的文章：將資料錄集參數化 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

如需 SQL **WHERE**子句的詳細資訊，請參閱[sql](../../data/odbc/sql.md)文章。 如需有關選取和篩選記錄的詳細資訊，請參閱 [記錄集的文章：篩選資料錄 (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

##  <a name="m_strsort"></a>CRecordset：： m_strSort

在您建立記錄集物件之後，但是在呼叫其 `Open` 成員函式之後，請使用此資料成員來儲存包含 SQL **ORDER by**子句的 `CString`。

### <a name="remarks"></a>備註

記錄集會使用此字串來排序它在 `Open` 或 `Requery` 呼叫期間所選取的記錄。 您可以使用這項功能來排序一個或多個資料行上的記錄集。 **ORDER by**子句的 ODBC SQL 語法為

`ORDER BY sort-specification [, sort-specification]...`

其中，排序規格是整數或資料行名稱。 您也可以指定遞增或遞減順序（根據預設，順序為遞增），方法是將 "ASC" 或 "DESC" 附加至排序字串中的資料行清單。 選取的記錄會先依照列出的第一個資料行排序，然後再按第二個，依此類推。 例如，您可以依姓氏或名字來排序「客戶」記錄集。 您可以列出的資料行數目取決於資料來源。 如需詳細資訊，請參閱 Windows SDK。

請注意，您不會在字串中包含**ORDER BY**關鍵字。 架構會提供它。

如需 SQL 子句的詳細資訊，請參閱[sql](../../data/odbc/sql.md)文章。 如需排序記錄的詳細資訊，請參閱 [記錄集的文章：排序資料錄 (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

##  <a name="move"></a>CRecordset：： Move

將記錄集內的目前記錄指標往前或往後移動。

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>參數

*nRows*<br/>
要向前或向後移動的資料列數目。 正值會往前移動到記錄集的結尾。 負數值會向後移動，朝一開始。

*wFetchType*<br/>
決定 `Move` 將提取的資料列集。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

如果您針對*nRows*傳遞0的值，`Move` 會重新整理目前的記錄。`Move` 將結束任何目前的 `AddNew` 或 `Edit` 模式，並會在呼叫 `AddNew` 或 `Edit` 之前還原目前記錄的值。

> [!NOTE]
>  當您在記錄集之間移動時，無法略過已刪除的記錄。 如需詳細資訊，請參閱[CRecordset：： IsDeleted](#isdeleted) 。 當您開啟具有 `skipDeletedRecords` 選項組的 `CRecordset` 時，如果*nRows*參數為0，則 `Move` 判斷提示。 這種行為可防止重新整理其他用戶端應用程式使用相同資料刪除的資料列。 如需 `skipDeletedRecords`的描述，請參閱[Open](#open)中的*dwOption*參數。

`Move` 會依資料列集重新置放記錄集。 根據*nRows*和*wFetchType*的值，`Move` 會提取適當的資料列集，然後讓該資料列集中的第一筆記錄成為目前的記錄。 如果您尚未執行大量資料列提取，則資料列集大小一律為1。 提取資料列集時，`Move` 直接呼叫[CheckRowsetError](#checkrowseterror)成員函式來處理提取所產生的任何錯誤。

視您傳遞的值而定，`Move` 等同于其他 `CRecordset` 成員函式。 特別是， *wFetchType*的值可能表示更直覺化的成員函式，通常是移動目前記錄的慣用方法。

下表列出*wFetchType*的可能值、`Move` 將根據*wFetchType*和*nRows*提取的資料列集，以及對應至*wFetchType*的任何對等成員函式。

|wFetchType|提取的資料列集|對等成員函式|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE （預設值）|從目前資料列集的第一個資料列開始*nRows*資料列的資料列集。||
|SQL_FETCH_NEXT|下一個資料列集;已忽略*nRows* 。|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|先前的資料列集;已忽略*nRows* 。|[MovePrev](#moveprev)|
|SQL_FETCH_FIRST|記錄集內的第一個資料列集;已忽略*nRows* 。|[MoveFirst](#movefirst)|
|SQL_FETCH_LAST|記錄集中最後一個完整的資料列集;已忽略*nRows* 。|[MoveLast](#movelast)|
|SQL_FETCH_ABSOLUTE|如果*nRows* > 0，則資料列集會從記錄集的開頭開始*nRows*資料列。 如果*nRows* < 0，則是從記錄集結尾處開始*nRows*資料列的資料列集。 如果*nRows* = 0，則會傳回檔案開頭（BOF）條件。|[SetAbsolutePosition](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|資料列集，從其書簽值對應至*nRows*的資料列開始。|[SetBookmark](#setbookmark)|

> [!NOTE]
>  對於順向記錄集，`Move` 僅適用于*wFetchType*的 SQL_FETCH_NEXT 值。

> [!CAUTION]
>  如果記錄集沒有任何記錄，則呼叫 `Move` 會擲回例外狀況。 若要判斷記錄集是否有任何記錄，請呼叫[IsBOF](#isbof)和[IsEOF](#iseof)。

> [!NOTE]
>  如果您已滾動記錄集的開頭或結尾（`IsBOF` 或 `IsEOF` 傳回非零值），則呼叫 `Move` 函數可能會擲回 `CDBException`。 例如，如果 `IsEOF` 傳回非零值，而 `IsBOF` 不是，則 `MoveNext` 將會擲回例外狀況，但 `MovePrev` 不會。

> [!NOTE]
>  如果您在目前的記錄正在更新或新增時呼叫 `Move`，則更新會遺失而不發出警告。

如需有關記錄集導覽的詳細資訊，請參閱 [記錄集的文章：滾動（ODBC）](../../data/odbc/recordset-scrolling-odbc.md) 和 [記錄集：書簽和絕對位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 如需相關資訊，請參閱 Windows SDK 中的 ODBC API 函數 `SQLExtendedFetch`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

##  <a name="movefirst"></a>CRecordset：： MoveFirst

使第一個資料列集中的第一筆記錄成為目前的記錄。

```
void MoveFirst();
```

### <a name="remarks"></a>備註

不論是否已執行大量資料列提取，這一律會是記錄集內的第一筆記錄。

開啟記錄集之後，您不需要立即呼叫 `MoveFirst`。 此時，第一筆記錄（如果有的話）會自動成為目前的記錄。

> [!NOTE]
>  這個成員函式對順向記錄集無效。

> [!NOTE]
>  當您在記錄集之間移動時，無法略過已刪除的記錄。 如需詳細資訊，請參閱[IsDeleted](#isdeleted)成員函式。

> [!CAUTION]
>  如果記錄集沒有任何記錄，呼叫任何 `Move` 函數都會擲回例外狀況。 若要判斷記錄集是否有任何記錄，請呼叫 `IsBOF` 並 `IsEOF`。

> [!NOTE]
>  如果您在目前的記錄正在更新或新增時呼叫任何 `Move` 函式，更新就會遺失而不發出警告。

如需有關記錄集導覽的詳細資訊，請參閱 [記錄集的文章：滾動（ODBC）](../../data/odbc/recordset-scrolling-odbc.md) 和 [記錄集：書簽和絕對位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

### <a name="example"></a>範例

  請參閱[IsBOF](#isbof)的範例。

##  <a name="movelast"></a>CRecordset：： MoveLast

使最後一個完整資料列集中的第一筆記錄成為目前的記錄。

```
void MoveLast();
```

### <a name="remarks"></a>備註

如果您尚未執行大量資料列提取，您的記錄集的資料列集大小為1，因此 `MoveLast` 只會移至記錄集的最後一筆記錄。

> [!NOTE]
>  這個成員函式對順向記錄集無效。

> [!NOTE]
>  當您在記錄集之間移動時，無法略過已刪除的記錄。 如需詳細資訊，請參閱[IsDeleted](#isdeleted)成員函式。

> [!CAUTION]
>  如果記錄集沒有任何記錄，呼叫任何 `Move` 函數都會擲回例外狀況。 若要判斷記錄集是否有任何記錄，請呼叫 `IsBOF` 並 `IsEOF`。

> [!NOTE]
>  如果您在目前的記錄正在更新或新增時呼叫任何 `Move` 函式，更新就會遺失而不發出警告。

如需有關記錄集導覽的詳細資訊，請參閱 [記錄集的文章：滾動（ODBC）](../../data/odbc/recordset-scrolling-odbc.md) 和 [記錄集：書簽和絕對位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

### <a name="example"></a>範例

  請參閱[IsBOF](#isbof)的範例。

##  <a name="movenext"></a>CRecordset：： MoveNext

使下一個資料列集中的第一筆記錄成為目前的記錄。

```
void MoveNext();
```

### <a name="remarks"></a>備註

如果您尚未執行大量資料列提取，您的記錄集的資料列集大小為1，因此 `MoveNext` 只會移到下一筆記錄。

> [!NOTE]
>  當您在記錄集之間移動時，無法略過已刪除的記錄。 如需詳細資訊，請參閱[IsDeleted](#isdeleted)成員函式。

> [!CAUTION]
>  如果記錄集沒有任何記錄，呼叫任何 `Move` 函數都會擲回例外狀況。 若要判斷記錄集是否有任何記錄，請呼叫 `IsBOF` 並 `IsEOF`。

> [!NOTE]
>  在呼叫 `MoveNext`之前，也建議您先呼叫 `IsEOF`。 例如，如果您已將超過記錄集的結尾，`IsEOF` 將會傳回非零值;後續對 `MoveNext` 的呼叫會擲回例外狀況。

> [!NOTE]
>  如果您在目前的記錄正在更新或新增時呼叫任何 `Move` 函式，更新就會遺失而不發出警告。

如需有關記錄集導覽的詳細資訊，請參閱 [記錄集的文章：滾動（ODBC）](../../data/odbc/recordset-scrolling-odbc.md) 和 [記錄集：書簽和絕對位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

### <a name="example"></a>範例

  請參閱[IsBOF](#isbof)的範例。

##  <a name="moveprev"></a>CRecordset：： MovePrev

使前一個資料列集中的第一筆記錄成為目前的記錄。

```
void MovePrev();
```

### <a name="remarks"></a>備註

如果您尚未執行大量資料列提取，您的記錄集的資料列集大小為1，因此 `MovePrev` 只會移至先前的記錄。

> [!NOTE]
>  這個成員函式對順向記錄集無效。

> [!NOTE]
>  當您在記錄集之間移動時，無法略過已刪除的記錄。 如需詳細資訊，請參閱[IsDeleted](#isdeleted)成員函式。

> [!CAUTION]
>  如果記錄集沒有任何記錄，呼叫任何 `Move` 函數都會擲回例外狀況。 若要判斷記錄集是否有任何記錄，請呼叫 `IsBOF` 並 `IsEOF`。

> [!NOTE]
>  在呼叫 `MovePrev`之前，也建議您先呼叫 `IsBOF`。 例如，如果您已在記錄集的開頭向前滾動，`IsBOF` 將會傳回非零值;後續對 `MovePrev` 的呼叫會擲回例外狀況。

> [!NOTE]
>  如果您在目前的記錄正在更新或新增時呼叫任何 `Move` 函式，更新就會遺失而不發出警告。

如需有關記錄集導覽的詳細資訊，請參閱 [記錄集的文章：滾動（ODBC）](../../data/odbc/recordset-scrolling-odbc.md) 和 [記錄集：書簽和絕對位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

### <a name="example"></a>範例

  請參閱[IsBOF](#isbof)的範例。

##  <a name="onsetoptions"></a>CRecordset：： OnSetOptions

呼叫以針對指定的 ODBC 語句設定選項（用於選取）。

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>參數

*hstmt*<br/>
要設定其選項的 ODBC 語句 HSTMT。

### <a name="remarks"></a>備註

呼叫 `OnSetOptions`，以針對指定的 ODBC 語句設定選項（用於選取）。 架構會呼叫這個成員函式，以設定記錄集的初始選項。 `OnSetOptions` 會判斷資料來源對可滾動資料指標的支援，以及對資料指標並行的支援，並據以設定記錄集的選項。 （而 `OnSetOptions` 用於選取作業，`OnSetUpdateOptions` 用於更新作業）。

覆寫 `OnSetOptions` 以設定驅動程式或資料來源的特定選項。 例如，如果您的資料來源支援開啟獨佔存取，您可能會覆寫 `OnSetOptions` 以利用該功能。

如需資料指標的詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)一文。

##  <a name="onsetupdateoptions"></a>CRecordset：： OnSetUpdateOptions

呼叫以針對指定的 ODBC 語句設定選項（用於 update）。

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>參數

*hstmt*<br/>
要設定其選項的 ODBC 語句 HSTMT。

### <a name="remarks"></a>備註

呼叫 `OnSetUpdateOptions`，為指定的 ODBC 語句設定選項（用於 update）。 架構會在建立 HSTMT 以更新記錄集內的記錄之後，呼叫這個成員函式。 （而 `OnSetOptions` 用於選取作業，`OnSetUpdateOptions` 用於更新作業）。`OnSetUpdateOptions` 會判斷資料來源對可滾動資料指標的支援，以及對資料指標並行的支援，並據以設定記錄集的選項。

覆寫 `OnSetUpdateOptions` 以設定 ODBC 語句的選項，然後使用該語句來存取資料庫。

如需資料指標的詳細資訊，請參閱[ODBC](../../data/odbc/odbc-basics.md)一文。

##  <a name="open"></a>CRecordset：： Open

藉由抓取資料表或執行記錄集所代表的查詢，來開啟記錄集。

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>參數

*nOpenType*<br/>
接受預設值，AFX_DB_USE_DEFAULT_TYPE，或使用 `enum OpenType`中的下列其中一個值：

- `CRecordset::dynaset` 具有雙向滾動的記錄集。 記錄的成員資格和排序是在記錄集開啟時決定，但其他使用者對資料值所做的變更會在提取作業之後顯示。 動態集也稱為索引鍵集驅動的記錄集。

- `CRecordset::snapshot` 具有雙向滾動的靜態記錄集。 記錄的成員資格和排序是在記錄集開啟時決定;資料值會在提取記錄時決定。 在關閉記錄集並重新開啟之前，不會顯示其他使用者所做的變更。

- `CRecordset::dynamic` 具有雙向滾動的記錄集。 其他使用者對成員資格、順序和資料值所做的變更，會在提取作業之後顯示。 請注意，許多 ODBC 驅動程式不支援這種類型的記錄集。

- `CRecordset::forwardOnly` 只有向前滾動的唯讀記錄集。

   針對 `CRecordset`，預設值為 `CRecordset::snapshot`。 預設值機制可讓視覺化C++的嚮導與具有不同預設值的 ODBC `CRecordset` 和 DAO `CDaoRecordset`進行互動。

如需這些記錄集類型的詳細資訊，請參閱[記錄集（ODBC）](../../data/odbc/recordset-odbc.md)一文。 如需相關資訊，請參閱 Windows SDK 中的「使用區塊和可滾動游標」一文。

> [!CAUTION]
>  如果要求的型別不受支援，則架構會擲回例外狀況。

*lpszSQL*<br/>
包含下列其中一項的字串指標：

- Null 指標。

- 資料表的名稱。

- SQL **SELECT**語句（選擇性地使用 sql **WHERE**或**ORDER by**子句）。

- 指定預先定義之查詢名稱的**CALL**語句（預存程式）。 請注意，您不會在大括弧和**CALL**關鍵字之間插入空格。

如需此字串的詳細資訊，請參閱 <<c0>備註一節底下的資料表和 ClassWizard 的角色討論。

> [!NOTE]
>  結果集中的資料行順序必須符合[DoFieldExchange](#dofieldexchange)或[DoBulkFieldExchange](#dobulkfieldexchange)函數覆寫中 rfx 或 Bulk RFX 函式呼叫的順序。

*dwOptions*<br/>
位元遮罩，可以指定下列值的組合。 其中一些是互斥的。 預設值為 [**無**]。

- `CRecordset::none` 未設定任何選項。 這個參數值與所有其他的值都是互斥的。 根據預設，您可以使用 [[編輯](#edit)] 或 [[刪除](#delete)] 來更新記錄集，並允許使用[AddNew](#addnew)附加新記錄。 可更新性取決於資料來源以及您指定的*nOpenType*選項。 無法使用大量新增的優化。 將不會執行大量資料列提取。 在記錄集流覽期間，將不會略過已刪除的記錄。 書簽無法使用。 已執行自動中途欄位檢查。

- `CRecordset::appendOnly` 不允許在記錄集上 `Edit` 或 `Delete`。 僅允許 `AddNew`。 此選項與 `CRecordset::readOnly`互斥。

- `CRecordset::readOnly` 以唯讀方式開啟記錄集。 此選項與 `CRecordset::appendOnly`互斥。

- `CRecordset::optimizeBulkAdd` 使用備妥的 SQL 語句，一次將多筆記錄優化。 只有在您未使用 ODBC API 函數 `SQLSetPos` 來更新記錄集時，才適用。 第一個更新會判斷哪些欄位已標示為已變更。 此選項與 `CRecordset::useMultiRowFetch`互斥。

- `CRecordset::useMultiRowFetch` 執行大量資料列提取，以允許在單一提取作業中抓取多個資料列。 這是為了提升效能而設計的先進功能;不過，ClassWizard 不支援大量記錄欄位交換。 此選項與 `CRecordset::optimizeBulkAdd`互斥。 請注意，如果您指定 `CRecordset::useMultiRowFetch`，則會自動開啟選項 `CRecordset::noDirtyFieldCheck` （將無法使用雙重緩衝）;在順向記錄集上，選項 `CRecordset::useExtendedFetch` 會自動開啟。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

- `CRecordset::skipDeletedRecords` 在流覽記錄集時略過所有已刪除的記錄。 這會使某些相對提取的效能變慢。 這個選項在順向記錄集上無效。 如果您呼叫[Move](#move)並將*nRows*參數設定為0，並設定 `CRecordset::skipDeletedRecords` 選項，`Move` 將會判斷提示。 請注意，`CRecordset::skipDeletedRecords` 類似于*驅動程式封裝*，這表示已刪除的資料列會從記錄集中移除。 不過，如果您的驅動程式套件記錄，則只會略過您刪除的記錄;當記錄集開啟時，它不會略過其他使用者所刪除的記錄。 `CRecordset::skipDeletedRecords` 會略過其他使用者刪除的資料列。

- `CRecordset::useBookmarks` 可能會在記錄集上使用書簽（如果支援的話）。 書簽會使資料抓取變慢，但可改善資料流覽的效能。 在順向記錄集上無效。 如需詳細資訊，請參閱 [記錄集的文章：書簽和絕對位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。

- `CRecordset::noDirtyFieldCheck` 關閉自動的中途欄位檢查（雙重緩衝）。 這將可改善效能;不過，您必須藉由呼叫 `SetFieldDirty` 並 `SetFieldNull` 成員函式，手動將欄位標示為中途。請注意，在類別 `CRecordset` 中的雙重緩衝類似于類別 `CDaoRecordset`中的雙重緩衝。 不過，在 `CRecordset`中，您無法在個別欄位上啟用雙重緩衝;您可以針對所有欄位啟用它，或將它停用於所有欄位。 請注意，如果您指定選項 `CRecordset::useMultiRowFetch`，則 `CRecordset::noDirtyFieldCheck` 會自動開啟;不過，`SetFieldDirty` 和 `SetFieldNull` 無法用於執行大量資料列提取的記錄集。

- `CRecordset::executeDirect` 不使用備妥的 SQL 語句。 為了改善效能，如果永遠不會呼叫 `Requery` 成員函式，請指定此選項。

- `CRecordset::useExtendedFetch` 執行 `SQLExtendedFetch`，而不是 `SQLFetch`。 這是專為在順向記錄集上執行大量資料列提取所設計。 如果您在順向記錄集上指定選項 `CRecordset::useMultiRowFetch`，則 `CRecordset::useExtendedFetch` 會自動開啟。

- `CRecordset::userAllocMultiRowBuffers` 使用者會配置資料的儲存緩衝區。 如果您想要配置自己的儲存體，請將此選項與 `CRecordset::useMultiRowFetch` 搭配使用。否則，架構會自動設定所需的儲存體。 如需詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 請注意，指定 `CRecordset::userAllocMultiRowBuffers` 而不指定 `CRecordset::useMultiRowFetch` 會導致失敗的判斷提示。

### <a name="return-value"></a>傳回值

如果成功開啟 `CRecordset` 物件，則為非零;否則，如果[CDatabase：： Open](../../mfc/reference/cdatabase-class.md#open) （如果有呼叫）傳回0，則為0。

### <a name="remarks"></a>備註

您必須呼叫這個成員函式，才能執行記錄集所定義的查詢。 在呼叫 `Open`之前，您必須先建立記錄集物件。

這個記錄集的資料來源連接取決於您在呼叫 `Open`之前，如何建立記錄集。 如果您將[CDatabase](../../mfc/reference/cdatabase-class.md)物件傳遞至尚未連接到資料來源的記錄集函式，此成員函式會使用[GetDefaultConnect](#getdefaultconnect)來嘗試開啟資料庫物件。 如果您將 Null 傳遞給記錄集的函式，則此函式會為您建立 `CDatabase` 物件，並 `Open` 嘗試連接資料庫物件。 如需在這些不同的情況下關閉記錄集和連接的詳細資訊，請參閱[關閉](#close)。

> [!NOTE]
>  透過 `CRecordset` 物件存取資料來源一律是共用的。 不同于 `CDaoRecordset` 類別，您無法使用 `CRecordset` 物件來開啟具有獨佔存取權的資料來源。

當您呼叫 `Open`時，通常是 SQL **SELECT**語句的查詢會根據下表所示的準則來選取記錄。

|LpszSQL 參數的值|選取的記錄取決於|範例|
|------------------------------------|----------------------------------------|-------------|
|NULL|`GetDefaultSQL`傳回的字串。||
|SQL 資料表名稱|資料表清單中的所有資料行 `DoFieldExchange` 或 `DoBulkFieldExchange`。|`"Customer"`|
|預先定義的查詢（預存程式）名稱|查詢定義為傳回的資料行。|`"{call OverDueAccts}"`|
|從資料表清單**中** **選取**資料行清單|指定之資料表中的指定資料行。|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
>  請注意，您不會在 SQL 字串中插入額外的空白字元。 例如，如果您在大括弧和**CALL**關鍵字之間插入空白字元，MFC 會將 SQL 字串錯誤解譯為數據表名稱，並將它併入**SELECT**語句中，這會導致擲回例外狀況。 同樣地，如果您的預先定義查詢使用輸出參數，請勿在大括弧和 ' ' 符號之間插入空白字元。 最後，您不能在**CALL**語句或**select**語句中的**select**關鍵字之前，插入大括弧之前的空白字元。

平常的程式是將 Null 傳遞給 `Open`。在此情況下，`Open` 會呼叫[GetDefaultSQL](#getdefaultsql)。 如果您使用衍生的 `CRecordset` 類別，`GetDefaultSQL` 會提供您在 ClassWizard 中指定的資料表名稱。 您可以改為在 `lpszSQL` 參數中指定其他資訊。

無論您傳遞哪一種方式，`Open` 會為查詢建立最終的 SQL 字串（字串可能會將 SQL **WHERE**和**ORDER BY**子句附加至您所傳遞的 `lpszSQL` 字串），然後執行查詢。 呼叫 `Open`之後，您可以藉由呼叫[GetSQL](#getsql)來檢查結構化的字串。 如需有關記錄集如何建立 SQL 語句並選取記錄的詳細資訊，請參閱 [記錄集一文：記錄集如何選取記錄（ODBC）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。

記錄集類別的欄位資料成員會系結至選取的資料行。 如果傳回任何記錄，第一筆記錄就會成為目前的記錄。

如果您想要設定記錄集的選項，例如篩選或排序，請在建立記錄集物件之後，但是在呼叫 `Open`之前，指定這些選項。 如果您想要在記錄集已開啟之後重新整理記錄集中的記錄，請呼叫[Requery](#requery)。

如需詳細資訊，包括其他範例，請參閱[記錄集（ODBC）](../../data/odbc/recordset-odbc.md)、[記錄集：記錄集如何選取記錄（ODBC）](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)，以及 [記錄集：建立和關閉記錄集（ODBC）](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)。

### <a name="example"></a>範例

下列程式碼範例會示範不同形式的 `Open` 呼叫。

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

##  <a name="refreshrowset"></a>CRecordset：： RefreshRowset

更新目前資料列集內的資料列和狀態。

```
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>參數

*wRow*<br/>
目前資料列集中，資料列的以一為基的位置。 這個值的範圍可以從零到資料列集的大小。

*wLockType*<br/>
值，指出在重新整理資料列之後，如何鎖定它。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

如果您針對*wRow*傳遞零值，則會重新整理資料列集中的每個資料列。

若要使用 `RefreshRowset`，您必須在[Open](#open)成員函式中指定 `CRecordset::useMulitRowFetch` 選項，以執行大量資料列提取。

`RefreshRowset` 會呼叫 ODBC API 函數 `SQLSetPos`。 *WLockType*參數會在執行 `SQLSetPos` 之後，指定資料列的鎖定狀態。 下表描述*wLockType*的可能值。

|wLockType|描述|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE （預設值）|驅動程式或資料來源會確保資料列與呼叫 `RefreshRowset` 之前的鎖定或解除鎖定狀態相同。|
|SQL_LOCK_EXCLUSIVE|驅動程式或資料來源會以獨佔方式鎖定資料列。 並非所有的資料來源都支援這種類型的鎖定。|
|SQL_LOCK_UNLOCK|驅動程式或資料來源會解除鎖定資料列。 並非所有的資料來源都支援這種類型的鎖定。|

如需 `SQLSetPos`的詳細資訊，請參閱 Windows SDK。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="requery"></a>CRecordset：： Requery

重建（重新整理）記錄集。

```
virtual BOOL Requery();
```

### <a name="return-value"></a>傳回值

如果成功重建記錄集，則為非零;否則為0。

### <a name="remarks"></a>備註

如果傳回任何記錄，第一筆記錄就會成為目前的記錄。

為了讓記錄集反映您或其他使用者對資料來源所做的新增和刪除，您必須藉由呼叫 `Requery`來重建記錄集。 如果記錄集是動態集，它會自動反映您或其他使用者對其現有記錄（但不是新增專案）所做的更新。 如果記錄集是快照，您必須呼叫 `Requery` 以反映其他使用者的編輯，以及新增和刪除。

針對動態集或快照，每當您想要使用新的篩選器或排序，或是新的參數值來重建記錄集時，都可以呼叫 `Requery`。 設定新的篩選或排序屬性，方法是將新值指派給 `m_strFilter` 並 `m_strSort`，然後再呼叫 `Requery`。 呼叫 `Requery`之前，請先將新值指派給參數資料成員，以設定新的參數。 如果篩選和排序字串未變更，您可以重複使用查詢來改善效能。

如果重建記錄集的嘗試失敗，就會關閉記錄集。 在您呼叫 `Requery`之前，您可以藉由呼叫 `CanRestart` 成員函式來判斷是否可以重新查詢記錄集。 `CanRestart` 不保證 `Requery` 會成功。

> [!CAUTION]
>  只有在您呼叫了[Open](#open)之後，才 `Requery` 呼叫。

### <a name="example"></a>範例

這個範例會重建記錄集來套用不同的排序次序。

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

##  <a name="setabsoluteposition"></a>CRecordset：： SetAbsolutePosition

將記錄集置於對應于指定記錄號碼的記錄上。

```
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>參數

*nRows*<br/>
記錄集中目前記錄的以一為基底的序數位置。

### <a name="remarks"></a>備註

`SetAbsolutePosition` 會根據此序數位置移動目前的記錄指標。

> [!NOTE]
>  這個成員函式在順向記錄集上無效。

若為 ODBC 記錄集，絕對位置設定1是指記錄集內的第一筆記錄;設定為0時，是指檔案的開頭（BOF）位置。

您也可以將負數值傳遞給 `SetAbsolutePosition`。 在此情況下，會從記錄集的結尾評估記錄集的位置。 例如，`SetAbsolutePosition( -1 )` 會將目前的記錄指標移至記錄集內的最後一個記錄。

> [!NOTE]
>  絕對位置不適合當做代理記錄號碼使用。 書簽仍然是保留並返回指定位置的建議方式，因為在刪除先前的記錄時，記錄的位置會變更。 此外，如果重新建立記錄集，您無法保證指定的記錄將會有相同的絕對位置，因為記錄集內個別記錄的順序不保證，除非是使用**ORDER BY**子句以 SQL 語句建立的。

如需記錄集導覽和書簽的詳細資訊，請參閱 [記錄集的文章：滾動（ODBC）](../../data/odbc/recordset-scrolling-odbc.md) 和 [記錄集：書簽和絕對位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。

##  <a name="setbookmark"></a>CRecordset：： SetBookmark

將記錄集置於包含指定書簽的記錄上。

```
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>參數

*varBookmark*<br/>
[CDBVariant](../../mfc/reference/cdbvariant-class.md)物件的參考，其中包含特定記錄的書簽值。

### <a name="remarks"></a>備註

若要判斷記錄集上是否支援書簽，請呼叫[CanBookmark](#canbookmark)。 若要讓書簽可供使用（如果支援的話），您必須在[Open](#open)成員函式的*dwOptions*參數中設定 `CRecordset::useBookmarks` 選項。

> [!NOTE]
>  如果書簽不受支援或無法使用，則呼叫 `SetBookmark` 會導致擲回例外狀況。 順向記錄集不支援書簽。

若要先取得目前記錄的書簽，請呼叫[GetBookmark](#getbookmark)，這會將書簽值儲存至 `CDBVariant` 物件。 之後，您可以使用已儲存的書簽值來呼叫 `SetBookmark`，以返回該記錄。

> [!NOTE]
>  在特定記錄集作業之後，您應該先檢查書簽的持續性，再呼叫 `SetBookmark`。 例如，如果您使用 `GetBookmark` 來抓取書簽，然後再呼叫 `Requery`，則書簽可能不再有效。 呼叫[CDatabase：： GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) ，以檢查您是否可以安全地呼叫 `SetBookmark`。

如需書簽和記錄集導覽的詳細資訊，請參閱 [記錄集的文章：書簽和絕對位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 和 [記錄集：滾動（ODBC）](../../data/odbc/recordset-scrolling-odbc.md)。

##  <a name="setfielddirty"></a>CRecordset：： SetFieldDirty

將記錄集的欄位資料成員標示為已變更或保持不變。

```
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>參數

*pv*<br/>
包含記錄集內欄位資料成員的位址，或為 Null。 如果是 Null，則記錄集中的所有欄位資料成員都會加上旗標。 （C++ Null 與資料庫術語中的 null 不同，這表示「沒有任何值」）。

*bDirty*<br/>
如果欄位資料成員要標示為「已變更」，則為 TRUE。 如果欄位資料成員要標示為「清除」（未變更），則為 FALSE。

### <a name="remarks"></a>備註

將欄位標記為未變更可確保欄位不會更新，並導致較少的 SQL 流量。

> [!NOTE]
>  此成員函式不適用於使用大量資料列提取的記錄集。 如果您已執行大量資料列提取，則 `SetFieldDirty` 會產生失敗的判斷提示。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

架構會標示已變更的欄位資料成員，以確保它們會由記錄欄位交換（RFX）機制寫入資料來源上的記錄。 變更欄位的值通常會自動將欄位設定為中途，因此您不常需要自行呼叫 `SetFieldDirty`，但有時您可能會想要確保不論欄位資料成員中的值為何，都會明確更新或插入資料行。

> [!CAUTION]
>  只有在您呼叫了[Edit](#edit)或[AddNew](#addnew)之後，才會呼叫此成員函式。

針對函式的第一個引數使用 Null，只會將函式套用至 `outputColumn` 欄位，而不是 `param` 欄位。 例如，呼叫

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

只會將 `outputColumn` 欄位設定為 Null;`param` 欄位將不會受到影響。

若要處理 `param` 欄位，您必須提供您想要使用之個別 `param` 的實際位址，例如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

這表示您無法將所有 `param` 欄位都設定為 Null，就像您可以使用 `outputColumn` 欄位一樣。

##  <a name="setfieldnull"></a>CRecordset：： SetFieldNull

將記錄集的欄位資料成員標記為 Null （明確沒有值）或為非 Null。

```
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>參數

*pv*<br/>
包含記錄集內欄位資料成員的位址，或為 Null。 如果是 Null，則記錄集中的所有欄位資料成員都會加上旗標。 （C++ Null 與資料庫術語中的 null 不同，這表示「沒有任何值」）。

*bNull*<br/>
如果欄位資料成員要標示為沒有值，則為非零（Null）。 如果欄位資料成員要標記為非 Null，則為0。

### <a name="remarks"></a>備註

當您將新記錄加入至記錄集時，所有欄位資料成員一開始都會設定為 Null 值，並標示為「已變更」。 當您從資料來源抓取記錄時，其資料行可能已經有值或為 Null。

> [!NOTE]
>  請勿在使用大量資料列提取的記錄集上呼叫這個成員函式。 如果您已執行大量資料列提取，呼叫 `SetFieldNull` 會導致失敗的判斷提示。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

如果您特別想要將目前記錄的欄位指定為不具有值，請呼叫 `SetFieldNull` 並將*bNull*設定為 TRUE，以將其標示為 Null。 如果欄位先前標記為 Null，而您現在想要為其指定值，只要設定其新值即可。 您不需要移除具有 `SetFieldNull`的 Null 旗標。 若要判斷欄位是否允許為 Null，請呼叫 `IsFieldNullable`。

> [!CAUTION]
>  只有在您呼叫了[Edit](#edit)或[AddNew](#addnew)之後，才會呼叫此成員函式。

針對函式的第一個引數使用 Null，只會將函式套用至 `outputColumn` 欄位，而不是 `param` 欄位。 例如，呼叫

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

只會將 `outputColumn` 欄位設定為 Null;`param` 欄位將不會受到影響。

若要處理 `param` 欄位，您必須提供您想要使用之個別 `param` 的實際位址，例如：

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

這表示您無法將所有 `param` 欄位都設定為 Null，就像您可以使用 `outputColumn` 欄位一樣。

> [!NOTE]
>  將參數設定為 Null 時，在開啟記錄集之前呼叫 `SetFieldNull` 會導致判斷提示。 在此情況下，請呼叫[SetParamNull](#setparamnull)。

`SetFieldNull` 是透過[DoFieldExchange](#dofieldexchange)來執行。

##  <a name="setlockingmode"></a>CRecordset：： SetLockingMode

將鎖定模式設定為「開放式」鎖定（預設值）或「封閉式」鎖定。 決定如何鎖定記錄以進行更新。

```
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>參數

*nMode*<br/>
包含 `enum LockMode`中的下列其中一個值：

- `optimistic` 開放式鎖定只會在呼叫 `Update`時鎖定正在更新的記錄。

- `pessimistic` 封閉式鎖定會在呼叫 `Edit` 時立即鎖定記錄，並讓它保持鎖定，直到 `Update` 呼叫完成或您移至新記錄為止。

### <a name="remarks"></a>備註

如果您需要指定記錄集用來進行更新的兩個記錄鎖定策略中，請呼叫這個成員函式。 根據預設，會 `optimistic`記錄集的鎖定模式。 您可以將其變更為更謹慎的 `pessimistic` 鎖定策略。 在您建立並開啟記錄集物件之後，但是在呼叫 `Edit`之前，請呼叫 `SetLockingMode`。

##  <a name="setparamnull"></a>CRecordset：： SetParamNull

將參數旗標為 Null （特別沒有值）或為非 Null。

```
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
參數之以零為起始的索引。

*bNull*<br/>
如果為 TRUE （預設值），則參數會標示為 Null。 否則，此參數會標示為非 Null。

### <a name="remarks"></a>備註

不同于[SetFieldNull](#setfieldnull)，您可以在開啟記錄集之前呼叫 `SetParamNull`。

`SetParamNull` 通常與預先定義的查詢（預存程式）搭配使用。

##  <a name="setrowsetcursorposition"></a>CRecordset：： SetRowsetCursorPosition

將資料指標移至目前資料列集內的資料列。

```
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>參數

*wRow*<br/>
目前資料列集中，資料列的以一為基的位置。 這個值的範圍可以從1到資料列集的大小。

*wLockType*<br/>
表示如何在重新整理資料列之後將它鎖定的值。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

在執行大量資料列提取時，資料列集會抓取記錄，其中提取之資料列集內的第一筆記錄是目前的記錄。 若要在資料列集內建立目前記錄的另一筆記錄，請呼叫 `SetRowsetCursorPosition`。 例如，您可以將 `SetRowsetCursorPosition` 與[GetFieldValue](#getfieldvalue)成員函式結合，以動態方式從記錄集的任何記錄中取得資料。

若要使用 `SetRowsetCursorPosition`，您必須藉由在[Open](#open)成員函式中指定*dwOptions*參數的 `CRecordset::useMultiRowFetch` 選項，來執行大量資料列提取。

`SetRowsetCursorPosition` 會呼叫 ODBC API 函數 `SQLSetPos`。 *WLockType*參數會在執行 `SQLSetPos` 之後，指定資料列的鎖定狀態。 下表描述*wLockType*的可能值。

|wLockType|描述|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE （預設值）|驅動程式或資料來源會確保資料列與呼叫 `SetRowsetCursorPosition` 之前的鎖定或解除鎖定狀態相同。|
|SQL_LOCK_EXCLUSIVE|驅動程式或資料來源會以獨佔方式鎖定資料列。 並非所有的資料來源都支援這種類型的鎖定。|
|SQL_LOCK_UNLOCK|驅動程式或資料來源會解除鎖定資料列。 並非所有的資料來源都支援這種類型的鎖定。|

如需 `SQLSetPos`的詳細資訊，請參閱 Windows SDK。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="setrowsetsize"></a>CRecordset：： SetRowsetSize

指定提取期間您想要取得的記錄數目。

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>參數

*dwNewRowsetSize*<br/>
要在指定的提取期間取得的資料列數目。

### <a name="remarks"></a>備註

此虛擬成員函式會指定在使用大量資料列提取時，您想要在單一提取期間取得多少資料列。 若要執行大量資料列提取，您必須在[Open](#open)成員函式的*dwOptions*參數中設定 `CRecordset::useMultiRowFetch` 選項。

> [!NOTE]
>  呼叫 `SetRowsetSize` 而不執行大量資料列提取將會導致失敗的判斷提示。

呼叫 `SetRowsetSize`，再呼叫 `Open` 開始設定記錄集的資料列集大小。 執行大量資料列提取時的預設資料列集大小為25。

> [!NOTE]
>  呼叫 `SetRowsetSize`時請務必小心。 如果您要手動設定資料的儲存空間（如 `Open`中 dwOptions 參數的 `CRecordset::userAllocMultiRowBuffers` 選項所指定），您應該在呼叫 `SetRowsetSize`之後，但在執行任何資料指標導覽作業之前，檢查是否需要重新配置這些儲存緩衝區。

若要取得資料列集大小的目前設定，請呼叫[GetRowsetSize](#getrowsetsize)。

如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="update"></a>CRecordset：： Update

藉由將新的或編輯過的資料儲存在資料來源上，完成 `AddNew` 或 `Edit` 作業。

```
virtual BOOL Update();
```

### <a name="return-value"></a>傳回值

如果已成功更新一筆記錄，則為非零。如果未變更任何資料行，則為0。 如果沒有更新任何記錄，或更新了多筆記錄，則會擲回例外狀況。 對於資料來源上的任何其他失敗，也會擲回例外狀況。

### <a name="remarks"></a>備註

呼叫[AddNew](#addnew)或[Edit](#edit)成員函式之後，呼叫這個成員函式。 這是完成 `AddNew` 或 `Edit` 作業所需的呼叫。

> [!NOTE]
>  如果您已執行大量資料列提取，就無法呼叫 `Update`。 這會導致失敗的判斷提示。 雖然類別 `CRecordset` 不會提供更新大量資料列的機制，但是您可以使用 ODBC API 函式 `SQLSetPos`來撰寫自己的函式。 如需大量資料列提取的詳細資訊，請參閱 [記錄集的文章：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

`AddNew` 和 `Edit` 準備一個編輯緩衝區，在其中放置加入或編輯的資料以儲存至資料來源。 `Update` 儲存資料。 只有標示或偵測到已變更的欄位才會更新。

如果資料來源支援交易，您可以在交易中進行 `Update` 呼叫（及其對應的 `AddNew` 或 `Edit` 呼叫）。 如需交易的詳細資訊，請參閱[交易（ODBC）](../../data/odbc/transaction-odbc.md)一文。

> [!CAUTION]
>  如果您在未先呼叫 `AddNew` 或 `Edit`的情況下呼叫 `Update`，`Update` 會擲回 `CDBException`。 如果您呼叫 `AddNew` 或 `Edit`，則在呼叫 `Move` 作業之前，或在關閉記錄集或資料來源連接之前，您必須先呼叫 `Update`。 否則，在沒有通知的情況下，您的變更就會遺失。

如需處理 `Update` 失敗的詳細資訊，請參閱 [記錄集的文章：記錄集如何更新記錄（ODBC）](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

### <a name="example"></a>範例

請參閱 [交易的文章：在記錄集（ODBC）](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)中執行交易。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView 類別](../../mfc/reference/crecordview-class.md)
