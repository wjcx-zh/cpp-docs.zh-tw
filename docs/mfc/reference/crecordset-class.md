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
ms.openlocfilehash: ab6cde9f478dc6f2e3cb0ba5bb338a3852f083fd
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750499"
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
|[C 記錄集:CRecordset](#crecordset)|建構 `CRecordset` 物件。 派生類必須提供調用此構造函數。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CRecordset::新增新](#addnew)|準備添加新記錄。 調用`Update`以完成添加。|
|[C記錄集::可應用](#canappend)|如果可以通過成員函數將新記錄添加到記錄集`AddNew`, 則傳回非零。|
|[CRecordset::CanBookmark](#canbookmark)|如果記錄集支援書籤,則返回非零。|
|[C 記錄集::取消](#cancel)|從第二個線程取消非同步操作或進程。|
|[C記錄集::取消更新](#cancelupdate)|由於`AddNew`或`Edit`操作而取消任何掛起的更新。|
|[CRecordset::可以重新啟動](#canrestart)|如果`Requery`可以調用以再次運行記錄集的查詢,則返回非零。|
|[CRecordset::CanScroll](#canscroll)|如果可以滾動瀏覽記錄,則返回非零。|
|[CRecordset::可以](#cantransact)|如果數據源支援事務,則返回非零。|
|[CRecordset::可以更新](#canupdate)|如果可以更新記錄集(可以添加、更新或刪除記錄),則返回非零。|
|[C記錄集::檢查羅塞特錯誤](#checkrowseterror)|呼叫 以處理記錄提取期間生成的錯誤。|
|[CRecordset:關閉](#close)|關閉記錄集和與之關聯的ODBC HSTMT。|
|[C記錄集::Delete](#delete)|從記錄集中刪除當前記錄。 刪除後,必須顯式滾動到其他記錄。|
|[CRecordset::DoBulkFieldExchange](#dobulkfieldexchange)|調用以將數據從數據源到記錄集的大量數據行交換。 實現批量記錄欄位交換(批量 RFX)。|
|[CRecordset::DoFieldExchange](#dofieldexchange)|調用 以在記錄集的欄位數據成員和數據源上的相應記錄之間交換數據(雙向)。 實現記錄欄位交換 (RFX)。|
|[CRecordset:編輯](#edit)|準備對當前記錄的更改。 調用`Update`以完成編輯。|
|[C 記錄集::刷新結果集](#flushresultset)|如果使用預定義的查詢時,如果另一個要檢索的結果集,則返回非零。|
|[CRecordset:取得書籤](#getbookmark)|將記錄的書籤值分配給參數物件。|
|[C 記錄集::取得預設連線](#getdefaultconnect)|已呼叫以取得預設連接字串。|
|[C 記錄集:取得預設SQL](#getdefaultsql)|呼叫以取得要執行的預設 SQL 字串。|
|[C記錄集::取得場值](#getfieldvalue)|返回記錄集中的欄位的值。|
|[C記錄集::取得ODBC欄位計數](#getodbcfieldcount)|返回記錄集中的欄位數。|
|[CRecordset::取得ODBC菲爾德資訊](#getodbcfieldinfo)|返回有關記錄集中欄位的特定類型的資訊。|
|[CRecordset:抓取記錄計數](#getrecordcount)|返回記錄集中的記錄數。|
|[C記錄集::取得羅資料集大小](#getrowsetsize)|返回您希望在單個提取期間檢索的記錄數。|
|[CRecordset::取得行](#getrowsfetched)|返回在提取期間檢索的實際行數。|
|[C記錄集:取得羅維狀態](#getrowstatus)|在提取后返回行的狀態。|
|[C記錄集::取得SQL](#getsql)|取得用於選擇記錄集記錄的 SQL 字串。|
|[CRecordset:取得狀態](#getstatus)|獲取記錄集的狀態:當前記錄的索引以及是否已獲取記錄的最終計數。|
|[C 記錄集:抓取表名](#gettablename)|獲取記錄集所基於的表的名稱。|
|[記錄集::IsBOF](#isbof)|如果記錄集已定位在第一條記錄之前,則返回非零。 目前沒有記錄。|
|[CRecordset:已刪除](#isdeleted)|如果記錄集位於已刪除的記錄上,則返回非零。|
|[記錄集::IsEOF](#iseof)|如果記錄集位於最後一條記錄之後,則返回非零。 目前沒有記錄。|
|[C記錄集::IsFieldDirty](#isfielddirty)|如果當前記錄中的指定欄位已更改,則返回非零。|
|[C記錄集::IsFieldNull](#isfieldnull)|如果當前記錄中的指定欄位為空(沒有值),則返回非零。|
|[C 記錄集::可欄位空](#isfieldnullable)|如果目前記錄中的指定欄位可以設置為 null(沒有值),則傳回非零。|
|[CRecordset::是開啟的](#isopen)|如果`Open`以前已調用,則返回非零。|
|[C 記錄集::移動](#move)|將記錄集定位為從當前記錄中的指定記錄數,以任一方向。|
|[C 記錄集::先移動](#movefirst)|將當前記錄定位到記錄集中的第一條記錄上。 首先測試`IsBOF`。|
|[C 記錄集::移動上次](#movelast)|將當前記錄定位到最後一條記錄或最後一個行集上。 首先測試`IsEOF`。|
|[C記錄集::移動下一個](#movenext)|將當前記錄定位在下一條記錄或下一個行集上。 首先測試`IsEOF`。|
|[C記錄集::MovePrev](#moveprev)|將當前記錄定位到上一條記錄或上一個行集上。 首先測試`IsBOF`。|
|[CRecordset::開啟選項](#onsetoptions)|呼叫以為指定的 ODBC 語句設定選項(在選擇時使用)。|
|[CRecordset::開啟更新選項](#onsetupdateoptions)|呼叫以為指定的 ODBC 語句設定選項(在更新時使用)。|
|[CRecordset::開啟](#open)|通過檢索表或執行記錄集表示的查詢來打開記錄集。|
|[C記錄集::刷新羅塞特](#refreshrowset)|刷新指定行的數據和狀態。|
|[C記錄集::重新查詢](#requery)|再次運行記錄集的查詢以刷新所選記錄。|
|[C記錄集::設定絕對位置](#setabsoluteposition)|將記錄集放在與指定記錄編號對應的記錄上。|
|[CRecordset::設定書籤](#setbookmark)|將記錄集放在書籤指定的記錄上。|
|[C記錄集::設定欄位臟](#setfielddirty)|將目前記錄中的指定欄位標記為已更改。|
|[C記錄集::設定欄位無效](#setfieldnull)|將目前記錄中指定欄位的值設定為 null(沒有值)。|
|[C 記錄集::設定鎖定模式](#setlockingmode)|將鎖定模式設置為「樂觀」鎖定(預設)或「悲觀」鎖定。 確定如何鎖定記錄以進行更新。|
|[C 記錄集::SetParamNull](#setparamnull)|將指定的參數設定為 null(沒有值)。|
|[C 記錄集::設定羅塞特游標位置](#setrowsetcursorposition)|將游標定位在行集中的指定行上。|
|[C 記錄集::設定羅塞特大小](#setrowsetsize)|指定您希望在提取期間檢索的記錄數。|
|[CRecordset::更新](#update)|通過在數據源上`AddNew``Edit`保存 新的或編輯的數據來完成 或操作。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CRecordset::m_hstmt](#m_hstmt)|包含記錄集的 ODBC 句句柄。 輸入 `HSTMT`。|
|[CRecordset:m_nFields](#m_nfields)|包含記錄集中的欄位數據成員數。 輸入 `UINT`。|
|[CRecordset:m_nParams](#m_nparams)|包含記錄集中的參數數據成員數。 輸入 `UINT`。|
|[CRecordset:m_pDatabase](#m_pdatabase)|包含指向記錄集連接到數據來源`CDatabase`的物件的指標。|
|[CRecordset::m_strFilter](#m_strfilter)|包含`CString`指定 結構化查詢語言 (SQL)`WHERE`子句的 。 用作篩選器,僅選擇滿足特定條件的記錄。|
|[CRecordset:m_strSort](#m_strsort)|包含指定`CString`SQL`ORDER BY`子句的 。 用於控制記錄的排序方式。|

## <a name="remarks"></a><a name="remarks"></a>備註

物件稱為「記錄集」`CRecordset`通常以兩種形式使用:動態集和快照。 動態集與其他用戶進行的數據更新保持同步。 快照是數據的靜態視圖。 每個表單表示在打開記錄集時修復的一組記錄,但當您滾動到動態集中的記錄時,它反映隨後由其他使用者或應用程式中的其他記錄集對記錄所做的更改。

> [!NOTE]
> 如果使用資料存取物件 (DAO) 類別而不是開放資料庫連接 (ODBC) 類別,請使用類[CDaoRecordset。](../../mfc/reference/cdaorecordset-class.md) 有關詳細資訊,請參閱文章[概述:資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。

要使用任一類型的記錄集,通常從`CRecordset`派生特定於應用程式的記錄集類。 紀錄集從資料來源中選擇紀錄,然後您可以:

- 滾動記錄。

- 更新記錄並指定鎖定模式。

- 篩選記錄集以約束它從數據源上可用的記錄中選擇哪些記錄。

- 對記錄集進行排序。

- 參數化記錄集,以自定義其選擇與在運行時之前不知道的資訊。

要使用類,請打開資料庫並構造記錄集物件,將構造函數傳遞指向物件的`CDatabase`指標。 然後調用記錄集`Open`的成員函數,您可以在其中指定對像是動態集還是快照。 調用`Open`從數據源中選擇數據。 打開記錄集物件后,使用其成員函數和數據成員滾動記錄並對其進行操作。 可用的操作取決於對像是動態集還是快照,它是可更新還是唯讀(這取決於開放資料庫連接 (ODBC) 資料來源的功能,以及您是否實現了批量行提取。 要刷新自`Open`調用以來可能已更改或添加的記錄,請調用`Requery`對象的成員函數。 調用物件的`Close`成員函數,並在物件完成時銷毀該函數。

在派生`CRecordset`類中,記錄欄位交換 (RFX) 或批量記錄欄位交換 (Bulk RFX) 用於支援記錄欄位的讀取和更新。

有關記錄集和記錄欄位交換的詳細資訊,請參閱文章[概述:資料庫程式設計](../../data/data-access-programming-mfc-atl.md)、[記錄集 (ODBC)、](../../data/odbc/recordset-odbc.md)[記錄集:批量提取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)和[記錄欄位交換 (RFX)。](../../data/odbc/record-field-exchange-rfx.md) 有關動態集和快照的重點,請參閱[文章動態集](../../data/odbc/dynaset.md)和[快照](../../data/odbc/snapshot.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CRecordset`

## <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="crecordsetaddnew"></a><a name="addnew"></a>CRecordset::新增新

準備向表添加新記錄。

```
virtual void AddNew();
```

### <a name="remarks"></a>備註

您必須調用[重新查詢](#requery)成員函數才能看到新添加的記錄。 記錄的欄位最初為空。 (在資料庫術語中,Null 表示"沒有值",並且與 C++ 中的 NULL 不同。要完成該操作,必須調用[Update](#update)成員函數。 `Update`將更改保存到數據源。

> [!NOTE]
> 如果已實現大量的批次提取,則無法呼叫`AddNew`。 這將導致斷言失敗。 儘管類`CRecordset`不提供更新批量資料行的機制,但您可以使用 ODBC API 函數編`SQLSetPos`寫自己的函數 。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`AddNew`使用記錄集的欄位數據成員準備新的空記錄。 調用`AddNew`後,在記錄集的欄位數據成員中設置所需的值。 (為此,您不必調用[Edit](#edit)成員函`Edit`數; 僅用於現有記錄。隨後調用`Update`時,欄位數據成員中更改的值將保存在數據源上。

> [!CAUTION]
> 如果在調用`Update`之前滾動到新記錄,則新記錄將丟失,並且不發出警告。

如果數據源支援事務,則可以將`AddNew`呼叫作為事務的一部分。 有關事務的詳細資訊,請參閱類[CDatabase](../../mfc/reference/cdatabase-class.md)。 請注意,在呼叫`AddNew`之前,應呼叫[CDatabase::開始轉換](../../mfc/reference/cdatabase-class.md#begintrans)。

> [!NOTE]
> 對於動態集,新記錄將作為最後一條記錄添加到記錄集。 添加的記錄不會添加到快照中;因此,這些記錄不會添加到快照中。您必須呼叫`Requery`以刷新記錄集。

調用`AddNew`其`Open`成員 函數未調用的記錄集是非法的。 如果`CDBException`呼`AddNew`叫 無法附加到的紀錄集,則引發 。 您可以通過調用[CanAppend](#canappend)來確定記錄集是否可更新。

有關詳細資訊,請參閱以下文章:[記錄集:記錄集如何更新記錄 (ODBC)、](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)[記錄集:添加、更新和刪除記錄 (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)和事務[(ODBC)。](../../data/odbc/transaction-odbc.md)

### <a name="example"></a>範例

請參閱文章[「事務:在記錄集 (ODBC) 中執行事務](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)」。

## <a name="crecordsetcanappend"></a><a name="canappend"></a>C記錄集::可應用

確定以前打開的記錄集是否允許您添加新記錄。

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>傳回值

如果記錄集允許添加新記錄,則非零;否則 0。 `CanAppend`如果以唯讀身份打開記錄集,則返回 0。

## <a name="crecordsetcanbookmark"></a><a name="canbookmark"></a>CRecordset::CanBookmark

確定記錄集是否允許您使用書籤標記記錄。

```
BOOL CanBookmark() const;
```

### <a name="return-value"></a>傳回值

如果記錄集支援書籤,則非零;否則 0。

### <a name="remarks"></a>備註

此函數獨立於[Open](#open)`CRecordset::useBookmarks`成員函數的*dwOption*參數中的選項。 `CanBookmark`指示給定的 ODBC 驅動程式和游標類型是否支援書籤。 `CRecordset::useBookmarks`指示書籤是否可用,前提是書籤受支援。

> [!NOTE]
> 僅轉發記錄集不支援書籤。

有關書籤和記錄集導航的詳細資訊,請參閱[文章「記錄集:書籤和絕對位置 (ODBC)」](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[「記錄集:滾動 (ODBC)」。。](../../data/odbc/recordset-scrolling-odbc.md)

## <a name="crecordsetcancel"></a><a name="cancel"></a>C 記錄集::取消

請求數據源取消正在進行的非同步操作或從第二個線程取消進程。

```cpp
void Cancel();
```

### <a name="remarks"></a>備註

請注意,MFC ODBC 類不再使用非同步處理;要執行同色諾操作,必須直接呼叫 ODBC API`SQLSetConnectOption`函式 。 有關詳細資訊,請參閱*ODBC SDK 程式師指南*中的主題"非同步執行函數"

## <a name="crecordsetcancelupdate"></a><a name="cancelupdate"></a>C記錄集::取消更新

在調用[更新](#update)之前,取消由[編輯](#edit)或[AddNew](#addnew)操作引起的任何掛起更新。

```cpp
void CancelUpdate();
```

### <a name="remarks"></a>備註

> [!NOTE]
> 此成員函數不適用於使用批次的記錄集,因為此類紀錄集無法呼叫`Edit`或`AddNew`。 `Update` 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

如果啟用了自動臟欄位檢查,`CancelUpdate`則成員變數將還原到以前`Edit``AddNew`或 已調用的值;否則,任何值更改都將保留。 默認情況下,在打開記錄集時啟用自動欄位檢查。 要關閉它,必須在[Open](#open)`CRecordset::noDirtyFieldCheck`成員函數的*dwOptions*參數中指定 。

有關更新資料的詳細資訊,請參閱[記錄集:新增、更新和刪除記錄 (ODBC) 。](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

## <a name="crecordsetcanrestart"></a><a name="canrestart"></a>CRecordset::可以重新啟動

確定記錄集是否允許通過調用`Requery`成員函數重新啟動其查詢(刷新其記錄)。

```
BOOL CanRestart() const;
```

### <a name="return-value"></a>傳回值

允許重新查詢時非零;否則 0。

## <a name="crecordsetcanscroll"></a><a name="canscroll"></a>CRecordset::CanScroll

確定記錄集是否允許滾動。

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>傳回值

如果記錄集允許滾動,則非零;否則 0。

### <a name="remarks"></a>備註

有關滾動的詳細資訊,請參閱[文章"記錄集:滾動"(ODBC)。](../../data/odbc/recordset-scrolling-odbc.md)

## <a name="crecordsetcantransact"></a><a name="cantransact"></a>CRecordset::可以

確定記錄集是否允許事務。

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>傳回值

如果記錄集允許事務,則非零;否則 0。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱文章[事務 (ODBC)](../../data/odbc/transaction-odbc.md)。

## <a name="crecordsetcanupdate"></a><a name="canupdate"></a>CRecordset::可以更新

確定是否可以更新記錄集。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>傳回值

如果可以更新記錄集,則非零;否則 0。

### <a name="remarks"></a>備註

如果基礎資料來源是唯讀的,或者在打開記錄集時在*dwOptions*`CRecordset::readOnly`參數中 指定,則記錄集可能是唯讀的。

## <a name="crecordsetcheckrowseterror"></a><a name="checkrowseterror"></a>C記錄集::檢查羅塞特錯誤

呼叫 以處理記錄提取期間生成的錯誤。

```
virtual void CheckRowsetError(RETCODE nRetCode);
```

### <a name="parameters"></a>參數

*nRetCode*<br/>
ODBC API 函數傳回代碼。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

此虛擬成員函數處理提取記錄時發生的錯誤,並且在批量行提取期間非常有用。 您可能需要考慮重寫`CheckRowsetError`來實現您自己的錯誤處理。

`CheckRowsetError`在游標導航操作(如`Open`、`Requery`或`Move`任何操作)中自動呼叫。 它傳遞了ODBC API函`SQLExtendedFetch`數的返回值。 下表列出了*nRetCode*參數的可能值。

|nRetCode|描述|
|--------------|-----------------|
|SQL_SUCCESS|功能成功完成;沒有其他資訊可用。|
|SQL_SUCCESS_WITH_INFO|功能成功完成,可能出現非致命錯誤。 可以通過調`SQLError`用 獲得其他資訊。|
|SQL_NO_DATA_FOUND|已提取結果集中的所有行。|
|SQL_ERROR|功能失敗。 可以通過調`SQLError`用 獲得其他資訊。|
|SQL_INVALID_HANDLE|由於環境句柄、連接句柄或語句句柄無效,功能失敗。 這表示程式設計錯誤。 沒有來自`SQLError`的其他資訊。|
|SQL_STILL_EXECUTING|以非同步方式啟動的函數仍在執行中。 請注意,預設情況下,MFC 永遠不會將此值傳遞給`CheckRowsetError`。MFC將繼續調用`SQLExtendedFetch`,直到不再返回SQL_STILL_EXECUTING。|

有關的詳細資訊`SQLError`,請參閱 Windows SDK。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

## <a name="crecordsetclose"></a><a name="close"></a>CRecordset:關閉

關閉記錄集。

```
virtual void Close();
```

### <a name="remarks"></a>備註

處理為記錄集分配的 ODBC HSTMT 和框架分配的所有記憶體。 通常在調用`Close`後,如果C++記錄集物件是使用**new**分配的,則刪除該物件。

通話後可以`Open`再次呼叫`Close`。 這允許您重用記錄集物件。 另一種選擇是呼叫`Requery`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#17](../../mfc/codesnippet/cpp/crecordset-class_1.cpp)]

## <a name="crecordsetcrecordset"></a><a name="crecordset"></a>C 記錄集:CRecordset

建構 `CRecordset` 物件。

```
CRecordset(CDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>參數

*p 資料庫*<br/>
包含指向`CDatabase`物件的指標或值 NULL。 如果不是 NULL,`CDatabase`並且尚未呼叫`Open`物件的成員函數將其連接到資料源,則記錄集會嘗試在它`Open`自己的調用期間為您打開它。 如果傳遞 NULL,將`CDatabase`使用 使用 ClassWizard 派生記錄集類時指定的數據源資訊構造和連接物件。

### <a name="remarks"></a>備註

可以直接使用`CRecordset`或派生`CRecordset`應用程式 特定的類。 您可以使用 ClassWizard 派生記錄集類。

> [!NOTE]
> 派生類*必須*提供其自己的構造函數。 在派生類的構造函數中,調用構造函數`CRecordset::CRecordset`,將適當的參數傳遞給它。

將 NULL 傳遞給記錄集建構函數`CDatabase`,以便自動建構和連接物件。 這是一個有用的速記,不需要在構造記錄集之前構造和連接`CDatabase`物件。

### <a name="example"></a>範例

有關詳細資訊,請參閱[記錄集:為表格 (ODBC) 宣告類別的文章](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。

## <a name="crecordsetdelete"></a><a name="delete"></a>C記錄集::Delete

刪除目前記錄。

```
virtual void Delete();
```

### <a name="remarks"></a>備註

成功刪除後,記錄集的欄位數據成員將設置為 Null 值,您必須顯式呼叫其中`Move`一個函數才能移出已刪除的記錄。 一旦您移出已刪除的記錄,將無法返回到它。 如果數據源支援事務,則可以使`Delete`調用成為事務的一部分。 有關詳細資訊,請參閱文章[事務 (ODBC)](../../data/odbc/transaction-odbc.md)。

> [!NOTE]
> 如果已實現大量的批次提取,則無法呼叫`Delete`。 這將導致斷言失敗。 儘管類`CRecordset`不提供更新批量資料行的機制,但您可以使用 ODBC API 函數編`SQLSetPos`寫自己的函數 。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

> [!CAUTION]
> 記錄集必須是可備份的,並且調用`Delete`記錄集時必須有有效的記錄電流。否則,將發生錯誤。 例如,如果刪除記錄,但在再次呼叫`Delete`之前不捲動到新記錄,`Delete`則引發[CDBException](../../mfc/reference/cdbexception-class.md)。

與[AddNew](#addnew)與[Edit](#edit)`Delete`不同,呼叫 後不會呼叫[更新](#update)。 如果`Delete`調用失敗,欄位數據成員保持不變。

### <a name="example"></a>範例

此示例顯示在函數的幀上創建的記錄集。 該示例假定`m_dbCust`存在 ,類型`CDatabase`的成員 變數已連接到數據源。

[!code-cpp[NVC_MFCDatabase#18](../../mfc/codesnippet/cpp/crecordset-class_2.cpp)]

## <a name="crecordsetdobulkfieldexchange"></a><a name="dobulkfieldexchange"></a>C記錄集::DoBulkFieldExchange

調用以將數據從數據源到記錄集的大量數據行交換。 實現批量記錄欄位交換(批量 RFX)。

```
virtual void DoBulkFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件的指標。 框架已經設置了此物件,以指定欄位交換操作的上下文。

### <a name="remarks"></a>備註

實現批量行提取時,框架將調用此成員函數以自動將數據從數據源傳輸到記錄集物件。 `DoBulkFieldExchange`還將參數數據成員(如果有)綁定到 SQL 語句字串中的參數占位符,以便記錄集的選擇。

未實用大量的批次提取,則框架將呼叫[DoFieldExchange](#dofieldexchange)。 要實現大量的投量行提取,[Open](#open)必須在`CRecordset::useMultiRowFetch`Open 成員函數中指定*dwOptions*參數的選項。

> [!NOTE]
> `DoBulkFieldExchange`僅當使用派生自`CRecordset`的 類時才可用。 如果直接從`CRecordset`中 創建了記錄集物件,則必須調用[GetFieldValue](#getfieldvalue)成員函數來檢索數據。

批量記錄欄位交換 (批量 RFX) 類似於記錄欄位交換 (RFX)。 數據會自動從數據源傳輸到記錄集物件。 但是,`AddNew`您不能呼叫`Edit``Delete`、`Update`或將更改傳輸回資料來源。 類`CRecordset`當前不提供更新大量數據行的機制;因此,類不提供更新數據批量行的機制。但是,您可以使用 ODBC API 函數編寫`SQLSetPos`自己的函數 。

請注意,ClassWizard 不支援批量記錄欄位交換;因此,該類嚮導不支援批量記錄欄位交換。因此,您必須通過編寫`DoBulkFieldExchange`對批量 RFX 函數的調用來手動覆蓋。 有關這些函數的詳細資訊,請參閱主題[記錄欄位交換函數](../../mfc/reference/record-field-exchange-functions.md)。

如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。 有關相關資訊,請參閱文章[記錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)。

## <a name="crecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CRecordset::DoFieldExchange

調用 以在記錄集的欄位數據成員和數據源上的相應記錄之間交換數據(雙向)。 實現記錄欄位交換 (RFX)。

```
virtual void DoFieldExchange(CFieldExchange* pFX);
```

### <a name="parameters"></a>參數

*pFX*<br/>
指向[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)物件的指標。 框架已經設置了此物件,以指定欄位交換操作的上下文。

### <a name="remarks"></a>備註

未實現批量行提取時,框架將調用此成員函數,以在記錄集物件的欄位數據成員和數據源上的當前記錄的相應列之間自動交換數據。 `DoFieldExchange`還將參數數據成員(如果有)綁定到 SQL 語句字串中的參數占位符,以便記錄集的選擇。

如果實現了大量的批次提取,則框架將呼叫[DoBulkFieldExchange](#dobulkfieldexchange)。 要實現大量的投量行提取,[Open](#open)必須在`CRecordset::useMultiRowFetch`Open 成員函數中指定*dwOptions*參數的選項。

> [!NOTE]
> `DoFieldExchange`僅當使用派生自`CRecordset`的 類時才可用。 如果直接從`CRecordset`中 創建了記錄集物件,則必須調用[GetFieldValue](#getfieldvalue)成員函數來檢索數據。

欄位資料交換(稱為記錄欄位交換 (RFX) 在兩個方向上工作:從記錄集物件的欄位數據成員到數據源上記錄的欄位,以及從數據源上的記錄到記錄集物件。

`DoFieldExchange`對於派生的記錄集類,通常需要執行的唯一操作是使用 ClassWizard 創建類並指定欄位數據成員的名稱和數據類型。 您還可以向 ClassWizard 編寫的代碼添加代碼,以指定參數數據成員或動態處理綁定的任何列。 有關詳細資訊,請參閱[文章記錄集:動態綁定數據列 (ODBC)。](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

當您使用 ClassWizard 宣告的紀錄集類別時,精靈`DoFieldExchange`會為您編寫一個重寫,類似於以下範例:

[!code-cpp[NVC_MFCDatabase#19](../../mfc/codesnippet/cpp/crecordset-class_3.cpp)]

有關 RFX 函數的詳細資訊,請參閱主題[記錄欄位交換函數](../../mfc/reference/record-field-exchange-functions.md)。

有關 有關的進`DoFieldExchange`一步示例和詳細資訊,請參閱[文章記錄欄位交換:RFX 的工作原理](../../data/odbc/record-field-exchange-how-rfx-works.md)。 有關 RFX 的一般資訊,請參閱記錄[欄位交換](../../data/odbc/record-field-exchange-rfx.md)的文章 。

## <a name="crecordsetedit"></a><a name="edit"></a>CRecordset:編輯

允許更改當前記錄。

```
virtual void Edit();
```

### <a name="remarks"></a>備註

調用`Edit`後,可以通過直接重置欄位數據成員的值來更改它們。 當您隨後調用[Update](#update)成員函數以在數據源上保存更改時,操作將完成。

> [!NOTE]
> 如果已實現大量的批次提取,則無法呼叫`Edit`。 這將導致斷言失敗。 儘管類`CRecordset`不提供更新批量資料行的機制,但您可以使用 ODBC API 函數編`SQLSetPos`寫自己的函數 。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`Edit`保存記錄集的數據成員的值。 如果調用`Edit`,進行更改,然後再次調`Edit`用 ,記錄的值將還原到第`Edit`一次 調用之前的值。

在某些情況下,您可能希望透過使列為 Null(不包含任何資料)來更新列。 為此,請使用 TRUE 參數呼叫[SetFieldNull](#setfieldnull)以標記欄位 Null;這還會導致更新列。 如果希望將欄位寫入資料來源,即使其值未更改,請使用 TRUE 參數呼叫[SetFieldDirty。](#setfielddirty) 即使欄位的值為 Null,這也能起作用。

如果數據源支援事務,則可以使`Edit`調用成為事務的一部分。 請注意,在調用`Edit`之前和打開記錄集之後,應調用[CDatabase::BeginTrans。](../../mfc/reference/cdatabase-class.md#begintrans) 另請注意,調用[CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans)不能替代`Update`呼叫 來`Edit`完成操作。 有關事務的詳細資訊,請參閱類[CDatabase](../../mfc/reference/cdatabase-class.md)。

根據目前鎖定模式,更新的記錄可能會鎖定,`Edit`直到您呼`Update`叫或滾動到其他記錄,或者它可能僅`Edit`在調用期間鎖定。 您可以使用[SetLockingMode](#setlockingmode)更改鎖定模式。

如果在調用`Update`之前滾動到新記錄,則還原當前記錄的上一個值。 如果`CDBException`調`Edit`用 無法更新的記錄集或沒有當前記錄,則引發 A。

有關詳細資訊,請參閱[文章事務 (ODBC)](../../data/odbc/transaction-odbc.md)和[記錄集:鎖定記錄 (ODBC)。](../../data/odbc/recordset-locking-records-odbc.md)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#20](../../mfc/codesnippet/cpp/crecordset-class_4.cpp)]

## <a name="crecordsetflushresultset"></a><a name="flushresultset"></a>C 記錄集::刷新結果集

如果有多個結果集,則檢索預定義查詢(存儲過程)的下一個結果集。

```
BOOL FlushResultSet();
```

### <a name="return-value"></a>傳回值

如果要檢索更多結果集,則非零;否則 0。

### <a name="remarks"></a>備註

僅當當前結果`FlushResultSet`集中的游標完全完成時,才應調用。 請注意,當您通過調用檢索下一個結果集`FlushResultSet`時,游標在該結果集中無效;因此,當您通過調用檢索下一個結果集時,游標對該結果集無效。調用 後應調用[MoveNext](#movenext)成員`FlushResultSet`函數。

如果預定義的查詢使用輸出參數或輸入/輸出參數,則必須調用`FlushResultSet`直到`FALSE`返回 (值 0),才能獲取這些參數值。

`FlushResultSet`呼叫 ODBC`SQLMoreResults`API 函式 。 如果`SQLMoreResults`返回SQL_ERROR或SQL_INVALID_HANDLE,則`FlushResultSet`將引發異常。 有關的詳細資訊`SQLMoreResults`,請參閱 Windows SDK。

如果要調用`FlushResultSet`,則存儲過程需要具有綁定欄位。

### <a name="example"></a>範例

以下代碼假定該`COutParamRecordset`對像是`CRecordset`基於具有輸入參數和輸出參數的預定義查詢且具有多個結果集的派生物件。 請注意[DoFieldExchange](#dofieldexchange)覆蓋的結構。

[!code-cpp[NVC_MFCDatabase#21](../../mfc/codesnippet/cpp/crecordset-class_5.cpp)]

[!code-cpp[NVC_MFCDatabase#22](../../mfc/codesnippet/cpp/crecordset-class_6.cpp)]

## <a name="crecordsetgetbookmark"></a><a name="getbookmark"></a>CRecordset:取得書籤

獲取當前記錄的書籤值。

```cpp
void GetBookmark(CDBVariant& varBookmark);
```

### <a name="parameters"></a>參數

*瓦爾布克馬克*<br/>
對表示當前記錄上書籤的[CDBVariant](../../mfc/reference/cdbvariant-class.md)物件的引用。

### <a name="remarks"></a>備註

要確定記錄集是否支援書籤,請呼叫[CanBookmark](#canbookmark)。 要使書籤在受支援時可用,必須在[Open](#open)成員`CRecordset::useBookmarks`函數 的*dwOptions*參數中設置該選項。

> [!NOTE]
> 如果書籤不受支援或不可用,則調用`GetBookmark`將導致引發異常。 僅轉發記錄集不支援書籤。

`GetBookmark`將當前記錄的書籤值分配給`CDBVariant`物件。 要在移動到其他記錄後隨時返回到該記錄,請使用相應的`CDBVariant`物件調用[SetBookmark。](#setbookmark)

> [!NOTE]
> 某些記錄集操作后,書籤可能不再有效。 例如,如果調用`GetBookmark`後`Requery`跟 ,可能無法`SetBookmark`返回 使用的記錄。 呼叫[CDatabase:取得書籤持久性](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence),以檢查是否可以安全地`SetBookmark`呼叫 。

有關書籤和記錄集導航的詳細資訊,請參閱[文章「記錄集:書籤和絕對位置 (ODBC)」](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[「記錄集:滾動 (ODBC)」。。](../../data/odbc/recordset-scrolling-odbc.md)

## <a name="crecordsetgetdefaultconnect"></a><a name="getdefaultconnect"></a>C 記錄集::取得預設連線

已呼叫以取得預設連接字串。

```
virtual CString GetDefaultConnect();
```

### <a name="return-value"></a>傳回值

包含`CString`預設連線字串的 。

### <a name="remarks"></a>備註

框架呼叫此成員函數以獲取記錄集所基於的資料來源的預設連接字串。 ClassWizard 通過標識在 ClassWizard 中使用的相同數據源來獲取有關表和列的資訊,從而為您實現此函數。 在開發應用程式時,您可能會發現依賴此預設連接很方便。 但是,默認連接可能不適合應用程式的使用者。 如果是這種情況,您應該重新實現此函數,放棄 ClassWizard 的版本。 有關連接字串的詳細資訊,請參考文章[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)。

## <a name="crecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>C 記錄集:取得預設SQL

呼叫以取得要執行的預設 SQL 字串。

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>傳回值

包含`CString`預設 SQL 語句的 。

### <a name="remarks"></a>備註

框架呼叫此成員函數以獲取記錄集所基於的預設 SQL 語句。 這可能是表名稱或 SQL **SELECT**語句。

通過使用 ClassWizard 聲明記錄集類來間接定義預設 SQL 語句,ClassWizard 會為您執行此任務。

如果需要 SQL 語句字串供自己使用,請呼`GetSQL`叫 ,這將返回用於在打開記錄集記錄時使用的 SQL 語句。 您可以在類別的重寫中編輯預設 SQL 字`GetDefaultSQL`串 。 例如,可以使用**CALL**語句指定對預定義查詢的調用。 (但是請注意,如果編輯`GetDefaultSQL`,還需要`m_nFields`修改 以匹配數據源中的列數。

有關詳細資訊,請參閱[記錄集:為表格 (ODBC) 宣告類別的文章](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)。

> [!CAUTION]
> 如果框架無法標識表名稱、提供了多個表名稱或無法解釋**CALL**語句,則表名稱將為空。 請注意,使用**CALL**語句時,不得在大括弧和**CALL**關鍵字之間插入空格,也不應在 curly 大括弧之前或在**SELECT**語句中的**SELECT**關鍵字之前插入空白。

## <a name="crecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>C記錄集::取得場值

檢索目前記錄中的欄位資料。

```cpp
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

*lpsz名稱*<br/>
欄位的名稱。

*varValu*e 對將儲存欄位值的[CDBVariant](../../mfc/reference/cdbvariant-class.md)物件的引用。

*nFieldType*<br/>
欄位的 ODBC C 資料類型。 使用預設值 DEFAULT_FIELD_TYPE`GetFieldValue`強制 根據下表從 SQL 數據類型確定 C 資料類型。 否則,您可以直接指定數據類型或選擇相容的數據類型;例如,您可以將任何數據類型存儲在SQL_C_CHAR。

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

有關 ODBC 資料類型的詳細資訊,請參閱 Windows SDK 附錄 D 中的「SQL 資料類型」和「C 資料類型」主題。

*nIndex*<br/>
欄位的零基索引。

*strValue*<br/>
對[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件的引用,該物件將儲存轉換為文本的欄位值,而不考慮欄位的資料類型。

### <a name="remarks"></a>備註

您可以按名稱或索引查找欄位。 可以將欄位值儲存在`CDBVariant`物件或`CString`物件中。

如果已實現批量行提取,則當前記錄始終位於行集中的第一個記錄上。 要對`GetFieldValue`給定行集中的記錄使用,必須首先調用[SetRowsetCursorPosition](#setrowsetcursorposition)成員函數,以將游標移動到該行集中的所需行。 然後調用`GetFieldValue`該行。 要實現大量的投量行提取,[Open](#open)必須在`CRecordset::useMultiRowFetch`Open 成員函數中指定*dwOptions*參數的選項。

可用於`GetFieldValue`在運行時動態提取欄位,而不是在設計時靜態綁定欄位。 例如,如果直接從`CRecordset`中聲明記錄集物件,則必須`GetFieldValue`使用 來檢索欄位數據;如果已直接從中聲明記錄集物件。未實現記錄欄位交換 (RFX) 或批量記錄欄位交換 (Bulk RFX)。

> [!NOTE]
> 如果聲明記錄集物件而不派生於`CRecordset`,則不載入 ODBC 游標庫。 游標庫要求記錄集至少有一個綁定列;因此,該庫要求記錄集至少具有一個綁定列。但是,當您直接使用`CRecordset`時,不會綁定任何列。 成員函數[CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex)和[CDatabase::打開](../../mfc/reference/cdatabase-class.md#open)控制是否將載入游標庫。

`GetFieldValue`呼叫 ODBC`SQLGetData`API 函式 。 如果驅動程式輸出值SQL_NO_TOTAL欄位值的實際長度,則`GetFieldValue`引發異常。 有關的詳細資訊`SQLGetData`,請參閱 Windows SDK。

### <a name="example"></a>範例

以下範例代碼說明瞭直接從`GetFieldValue`中聲明的記錄集物件的調用`CRecordset`。

[!code-cpp[NVC_MFCDatabase#23](../../mfc/codesnippet/cpp/crecordset-class_7.cpp)]

> [!NOTE]
> 與`CDaoRecordset`DAO`CRecordset`類`SetFieldValue`不同,沒有成員函數。 如果直接從`CRecordset`創建物件,則該對象實際上是唯讀的。

如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

## <a name="crecordsetgetodbcfieldcount"></a><a name="getodbcfieldcount"></a>C記錄集::取得ODBC欄位計數

檢索記錄集物件中的欄位總數。

```
short GetODBCFieldCount() const;
```

### <a name="return-value"></a>傳回值

記錄集中的欄位數。

### <a name="remarks"></a>備註

有關創建記錄集的詳細資訊,請參閱[文章"記錄集:創建和關閉記錄集 "(ODBC)。](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

## <a name="crecordsetgetodbcfieldinfo"></a><a name="getodbcfieldinfo"></a>CRecordset::取得ODBC菲爾德資訊

獲取有關記錄集中的欄位的資訊。

```cpp
void GetODBCFieldInfo(
    LPCTSTR lpszName,
    CODBCFieldInfo& fieldinfo);

void GetODBCFieldInfo(
    short nIndex,
    CODBCFieldInfo& fieldinfo);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
欄位的名稱。

*菲爾德資訊*<br/>
對結構的`CODBCFieldInfo`引用。

*nIndex*<br/>
欄位的零基索引。

### <a name="remarks"></a>備註

函數的一個版本允許您按名稱查找欄位。 另一個版本允許您按索引查找欄位。

有關返回的信息的說明,請參閱[CODBCFieldInfo](../../mfc/reference/codbcfieldinfo-structure.md)結構。

有關創建記錄集的詳細資訊,請參閱[文章"記錄集:創建和關閉記錄集 "(ODBC)。](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

## <a name="crecordsetgetrecordcount"></a><a name="getrecordcount"></a>CRecordset:抓取記錄計數

確定記錄集的大小。

```
long GetRecordCount() const;
```

### <a name="return-value"></a>傳回值

記錄集中的記錄數;如果記錄集不包含任何記錄,則為 0;或 -1,如果無法確定記錄計數。

### <a name="remarks"></a>備註

> [!CAUTION]
> 記錄計數被保留為"高水位線",這是使用者在記錄中移動時記錄數量最多的記錄。 只有在使用者超出最後一條記錄后,才能知道記錄總數。 出於性能原因,當您調用`MoveLast`時,計數不會更新。 要自己計算記錄,請重複`MoveNext`呼叫`IsEOF`, 直到返回非零。 通過`CRecordset:AddNew`添加記錄並`Update`增加 計數;通過`CRecordset::Delete`刪除記錄可減少計數。

## <a name="crecordsetgetrowsetsize"></a><a name="getrowsetsize"></a>C記錄集::取得羅資料集大小

獲取要在給定提取期間檢索的行數的當前設置。

```
DWORD GetRowsetSize() const;
```

### <a name="return-value"></a>傳回值

給定提取期間要檢索的行數。

### <a name="remarks"></a>備註

如果使用批量行提取,則打開記錄集時的預設行集大小為 25;如果正在使用批量行提取,則打開記錄集時的默認行集大小為 25;否則,它是1。

要實現批量行提取,必須在[Open](#open)Open`CRecordset::useMultiRowFetch`成員函數的*dwOptions*參數中指定選項。 要變更列集大小的設定,請呼叫[SetRowsetSize](#setrowsetsize)。

如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

## <a name="crecordsetgetrowsfetched"></a><a name="getrowsfetched"></a>CRecordset::取得行

確定提取后實際檢索的記錄數。

```
DWORD GetRowsFetched() const;
```

### <a name="return-value"></a>傳回值

給定提取后從數據源檢索的行數。

### <a name="remarks"></a>備註

當您已實現批量行提取時,這非常有用。 行集大小通常指示將從提取中檢索多少行;因此,從提取中檢索的行數。但是,記錄集中的行總數也會影響將在行集中檢索的行數。 例如,如果記錄集有 10 條記錄,行集大小設置為 4,則`MoveNext`通過調用 遍歷記錄集將導致最終行集只有 2 條記錄。

要實現批量行提取,必須在[Open](#open)Open`CRecordset::useMultiRowFetch`成員函數的*dwOptions*參數中指定選項。 要指定行集大小,請呼叫[SetRowsetSize](#setrowsetsize)。

如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#24](../../mfc/codesnippet/cpp/crecordset-class_8.cpp)]

## <a name="crecordsetgetrowstatus"></a><a name="getrowstatus"></a>C記錄集:取得羅維狀態

獲取當前行集中行的狀態。

```
WORD GetRowStatus(WORD wRow) const;
```

### <a name="parameters"></a>參數

*wRow*<br/>
當前行集中行的基於一個位置。 此值的範圍可以從 1 到行集的大小。

### <a name="return-value"></a>傳回值

行的狀態值。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

`GetRowStatus`返回一個值,指示自上次從數據源檢索行以來行狀態的任何更改,或者未提取與*wRow*對應的行。 下表列出可能的傳回值。

|狀態值|描述|
|------------------|-----------------|
|SQL_ROW_SUCCESS|該行保持不變。|
|SQL_ROW_UPDATED|該行已更新。|
|SQL_ROW_DELETED|資料列已經刪除。|
|SQL_ROW_ADDED|該行已添加。|
|SQL_ROW_ERROR|由於錯誤,該行無法檢索。|
|SQL_ROW_NOROW|沒有對應於*wRow*的行。|

有關詳細資訊,請參閱 Windows SDK 中的`SQLExtendedFetch`ODBC API 功能。

## <a name="crecordsetgetstatus"></a><a name="getstatus"></a>CRecordset:取得狀態

確定記錄集中當前記錄的索引以及是否看到最後一條記錄。

```cpp
void GetStatus(CRecordsetStatus& rStatus) const;
```

### <a name="parameters"></a>參數

*rStatus*<br/>
`CRecordsetStatus` 物件的參考。 如需詳細資訊，請參閱「備註」一節。

### <a name="remarks"></a>備註

`CRecordset`嘗試跟蹤索引,但在某些情況下,這可能是不可能的。 有關說明,請參閱[GetRecordCount。](#getrecordcount)

結構`CRecordsetStatus`具有以下形式:

```cpp
struct CRecordsetStatus
{
    long m_lCurrentRecord;
    BOOL m_bRecordCountFinal;
};
```

的`CRecordsetStatus`兩個成員具有以下含義:

- `m_lCurrentRecord`包含記錄集中當前記錄的零基索引(如果已知)。 如果無法確定索引,則此成員包含AFX_CURRENT_RECORD_UNDEFINED (-2)。 如果`IsBOF`為 TRUE(空記錄集或嘗試在第一個記錄之前`m_lCurrentRecord`滾動 ),則設置為AFX_CURRENT_RECORD_BOF (-1)。 如果在第一個記錄上,則將其設置為 0,第二條記錄 1,等等。

- `m_bRecordCountFinal`如果已確定記錄集中的記錄總數,則非零。 通常,這必須通過從記錄集的開頭開始和調用`MoveNext``IsEOF`直到返回非零來實現。 如果此成員為零,則返回`GetRecordCount`的記錄計數(如果不是 -1)只是記錄的"高水位線"計數。

## <a name="crecordsetgetsql"></a><a name="getsql"></a>C記錄集::取得SQL

呼叫此成員函數獲取用於在打開記錄集時用於選擇記錄集記錄的 SQL 語句。

```
const CString& GetSQL() const;
```

### <a name="return-value"></a>傳回值

對**const**包含 SQL`CString`語句的的引用。

### <a name="remarks"></a>備註

這通常是 SQL **SELECT**語句。 返回的`GetSQL`字串是唯讀的。

傳`GetSQL`回的字串通常不同於您可能傳遞給*lpszSQL*參數中的記錄`Open`集到 成員函數的任何字串。 這是因為記錄集基於您傳遞給`Open`的內容、使用 ClassWizard 指定`m_strFilter`的內容`m_strSort`、在和資料成員中指定的內容以及您可能指定的任何參數構造了完整的 SQL 語句。 有關記錄集如何建構此 SQL 語句的詳細資訊,請參閱[記錄集:記錄集如何選擇記錄 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。

> [!NOTE]
> 僅在調用[Open](#open)後呼叫此成員函數。

## <a name="crecordsetgettablename"></a><a name="gettablename"></a>C 記錄集:抓取表名

獲取記錄集查詢所基於的 SQL 表的名稱。

```
const CString& GetTableName() const;
```

### <a name="return-value"></a>傳回值

如果**const**記錄集基於表`CString`, 則對 包含表名稱的 引用;否則,一個空字串。

### <a name="remarks"></a>備註

`GetTableName`僅當記錄集基於表,而不是多個表的聯接或預定義的查詢(存儲過程)時才有效。 該名稱是唯讀的。

> [!NOTE]
> 僅在調用[Open](#open)後呼叫此成員函數。

## <a name="crecordsetisbof"></a><a name="isbof"></a>記錄集::IsBOF

如果記錄集已定位在第一條記錄之前,則返回非零。 目前沒有記錄。

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>傳回值

如果記錄集不包含任何記錄,或者在第一個記錄之前向後滾動,則非零;否則 0。

### <a name="remarks"></a>備註

在從記錄滾動到記錄之前,請調用此成員函數,以瞭解您是否在記錄集的第一個記錄之前。 您還可以使用`IsBOF`一`IsEOF`起 確定記錄集是否包含任何記錄或為空。 呼叫 後`Open`立即 呼叫,如果記錄集不包含任何`IsBOF`記錄, 則傳回非零。當您打開至少具有一條記錄的記錄集時,第一個記錄是當前記錄,並`IsBOF`返回 0。

如果第一條記錄是當前記錄,而您調用`MovePrev``IsBOF`時,將隨後返回非零。 如果`IsBOF`返回非零,並且調`MovePrev`用 ,則會發生錯誤。 如果`IsBOF`返回非零,則當前記錄未定義,任何需要當前記錄的操作都將導致錯誤。

### <a name="example"></a>範例

本示例使用`IsBOF``IsEOF`並檢測記錄集的限制,因為代碼在兩個方向上滾動通過記錄集。

[!code-cpp[NVC_MFCDatabase#25](../../mfc/codesnippet/cpp/crecordset-class_9.cpp)]

## <a name="crecordsetisdeleted"></a><a name="isdeleted"></a>CRecordset:已刪除

確定目前記錄是否已刪除。

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>傳回值

如果記錄集位於已刪除的記錄上,則非零;否則 0。

### <a name="remarks"></a>備註

如果滾動到記錄並`IsDeleted`返回 TRUE(非零),則必須滾動到其他記錄,然後才能執行任何其他記錄集操作。

的結果`IsDeleted`取決於許多因素,例如記錄集類型、記錄集是否可更新、打開記錄集時是否`CRecordset::skipDeletedRecords`指定了選項、驅動程式是否打包已刪除的記錄以及是否有多個使用者。

有關`CRecordset::skipDeletedRecords`和驅動程式打包的詳細資訊,請參閱[打開](#open)成員函數。

> [!NOTE]
> 如果已實現批量行提取,則不應呼叫`IsDeleted`。 而是調用[GetRow 狀態](#getrowstatus)成員函數。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

## <a name="crecordsetiseof"></a><a name="iseof"></a>記錄集::IsEOF

如果記錄集位於最後一條記錄之後,則返回非零。 目前沒有記錄。

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>傳回值

如果記錄集不包含任何記錄,或者您滾動超過最後一條記錄,則為非零;否則 0。

### <a name="remarks"></a>備註

在從記錄滾動到記錄時調用此成員函數,以瞭解您是否超出了記錄集的最後一條記錄。 您還可以使用`IsEOF`來確定記錄集是否包含任何記錄或為空。 呼叫 後`Open`立即 呼叫,如果記錄集不包含任何`IsEOF`記錄, 則傳回非零。 當您打開至少具有一條記錄的記錄集時,第一個記錄是當前記錄,並`IsEOF`返回 0。

如果最後一條記錄是您調用`MoveNext`時的目前記錄`IsEOF`, 則隨後將返回非零。 如果`IsEOF`返回非零,並且調`MoveNext`用 ,則會發生錯誤。 如果`IsEOF`返回非零,則當前記錄未定義,任何需要當前記錄的操作都將導致錯誤。

### <a name="example"></a>範例

請參閱[IsBOF](#isbof)的範例。

## <a name="crecordsetisfielddirty"></a><a name="isfielddirty"></a>C記錄集::IsFieldDirty

確定自調用[Edit](#edit)或[AddNew](#addnew)以來是否更改了指定的欄位數據成員。

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
指向要檢查其狀態的欄位資料成員的指標,或 NULL 以確定任何欄位是否髒。

### <a name="return-value"></a>傳回值

如果指定的欄位資料成員自調用`AddNew``Edit`或 後已更改,則非零。否則 0。

### <a name="remarks"></a>備註

當對[Update](#update)成員`CRecordset`函數的呼叫(在`Edit`呼`AddNew`叫或之後)更新當前記錄時,所有髒欄位資料成員中的數據都將傳輸到資料來源上的記錄。

> [!NOTE]
> 此成員函數不適用於使用批量行提取的記錄集。 如果已實現批量行提取,則`IsFieldDirty`始終返回 FALSE 並將導致斷言失敗。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

呼叫`IsFieldDirty`將重置之前調用[SetFieldDirty](#setfielddirty)的影響,因為重新計算欄位的髒狀態。 `AddNew`在這種情況下,如果當前欄位值與偽 null 值不同,則欄位狀態設置為髒。 `Edit`在這種情況下,如果欄位值與緩存值不同,則欄位狀態設置為髒。

`IsFieldDirty`通過[多菲爾德交易所](#dofieldexchange)實施。

有關臟標誌的詳細資訊,請參閱[記錄集文章:記錄集如何選擇記錄 (ODBC)。](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

## <a name="crecordsetisfieldnull"></a><a name="isfieldnull"></a>C記錄集::IsFieldNull

如果目前記錄中的指定欄位為 Null(沒有值),則傳回非零。

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
指向要檢查其狀態的欄位資料成員的指標,或 NULL 以確定是否有任何欄位為 Null。

### <a name="return-value"></a>傳回值

如果指定的欄位資料成員標記為 Null,則非零;否則 0。

### <a name="remarks"></a>備註

呼叫此成員函數以確定記錄集的指定欄位資料成員是否已標記為 Null。 (在資料庫術語中,Null 表示"沒有值",並且與 C++ 中的 NULL 不同。如果欄位資料成員標記為 Null,則將其解釋為當前記錄的列,該列沒有值。

> [!NOTE]
> 此成員函數不適用於使用批量行提取的記錄集。 如果已實現批量行提取,則`IsFieldNull`始終返回 FALSE 並將導致斷言失敗。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`IsFieldNull`通過[多菲爾德交易所](#dofieldexchange)實施。

## <a name="crecordsetisfieldnullable"></a><a name="isfieldnullable"></a>C 記錄集::可欄位空

如果目前記錄中的指定欄位可以設置為 Null(沒有值),則傳回非零。

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
指向要檢查其狀態的欄位資料成員的指標,或 NULL 以確定是否可以將任何欄位設置為 Null 值。

### <a name="remarks"></a>備註

呼叫此成員函數以確定指定的欄位資料成員是否為"空"(可以設置為Null值;是否可以設置為Null值。"C++ NULL 與 Null 不同,在資料庫術語中,Null 表示"沒有值")。

> [!NOTE]
> 如果已實現大量的批次提取,則無法呼叫`IsFieldNullable`。 相反,調用[GetODBCFieldInfo](#getodbcfieldinfo)成員函數以確定欄位是否可以設置為 Null 值。 請注意,無論是否已實現大量的`GetODBCFieldInfo`行擷取,您始終都可以呼叫 。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

不能為空的欄位必須具有值。 如果在添加或更新記錄時嘗試將此類欄位設置為 Null,資料源將拒絕添加或更新,[更新](#update)將引發異常。 當您調用`Update`時,會出現異常,而不是調用[SetFieldNull](#setfieldnull)時。

對函數的第一個參數使用 NULL 將僅將函數`outputColumn`應用於欄位`param`,而不是欄位。 例如,呼叫

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

將僅`outputColumn`將欄位設定為 NULL;`param`欄位將不受影響。

要處理`param`欄位,必須提供要處理的`param`個人的實際位址,例如:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

這表示您不能將`param`所有欄位設定為 NULL,就像對欄位`outputColumn`一樣 。

`IsFieldNullable`通過[多菲爾德交易所](#dofieldexchange)實施。

## <a name="crecordsetisopen"></a><a name="isopen"></a>CRecordset::是開啟的

確定記錄集是否已打開。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果以前已調用記錄集物件的[打開](#open)或[重新查詢](#requery)成員函數,並且記錄集尚未關閉,則非零;否則 0。

## <a name="crecordsetm_hstmt"></a><a name="m_hstmt"></a>CRecordset::m_hstmt

包含與記錄集關聯的 HSTMT 類型的 ODBC 語句數據結構的句柄。

### <a name="remarks"></a>備註

對 ODBC 數據源的每個查詢都與 HSTMT 相關聯。

> [!CAUTION]
> 在調用`m_hstmt`[Open](#open)之前不要使用。

通常不需要直接訪問 HSTMT,但可能需要它才能直接執行 SQL 語句。 類`ExecuteSQL``CDatabase`的成員函數提供了使用`m_hstmt`的範例。

## <a name="crecordsetm_nfields"></a><a name="m_nfields"></a>CRecordset:m_nFields

包含記錄集類中的欄位數據成員數;即記錄集從數據源中選擇的列數。

### <a name="remarks"></a>備註

記錄集類的構造函數必須用正確的數位初始`m_nFields`化。 如果尚未實現批量行提取,ClassWizard 會當您使用它聲明記錄集類時為您編寫此初始化。 您也可以手動編寫。

框架使用此數位來管理欄位數據成員與數據源上當前記錄的相應列之間的交互。

> [!CAUTION]
> 此號碼必須對應於在使用`DoFieldExchange``DoBulkFieldExchange``CFieldExchange::outputColumn`參數 呼叫[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)時或之後註冊的「輸出列」數。

您可以動態綁定列,如文章「記錄集:動態綁定數據列」中所述。 如果這樣做,則必須增加 中的`m_nFields`計數,以反映動態綁定列`DoFieldExchange``DoBulkFieldExchange`或 成員函數中的 RFX 或批量 RFX 函數調用數。

有關詳細資訊,請參閱[文章"記錄集:動態綁定數據列 (ODBC)"](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)和[「記錄集:批量提取記錄」(ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

### <a name="example"></a>範例

請參閱記錄[欄位交換的文章:使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

## <a name="crecordsetm_nparams"></a><a name="m_nparams"></a>CRecordset:m_nParams

包含記錄集類中的參數數據成員數;即,使用記錄集的查詢傳遞的參數數。

### <a name="remarks"></a>備註

如果記錄集類具有任何參數數據成員,則類的構造函數必須用正確的數位初始`m_nParams`化。 預設值為`m_nParams`0 的值。 如果添加參數數據成員(必須手動添加),還必須在類構造函數中手動添加初始化,以反映參數數(參數數量必須至少與字串中的`m_strFilter``m_strSort`''占位元數相同)。

框架在參數化記錄集的查詢時使用此數位。

> [!CAUTION]
> 此編號必須對應於在呼叫[SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)中`DoFieldExchange`或`DoBulkFieldExchange`之後註冊的參數`CFieldExchange::param`值`CFieldExchange::outputParam`為`CFieldExchange::inoutParam`、 或的`CFieldExchange::inputParam`「參數」 的「參數」 數。

### <a name="example"></a>範例

  請參考[文章記錄集:參數化紀錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)與[紀錄欄位交換:使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

## <a name="crecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CRecordset:m_pDatabase

包含指向記錄集連接到數據來源`CDatabase`的物件的指標。

### <a name="remarks"></a>備註

此變數以兩種方式設置。 通常,在構造記錄集物件時,將`CDatabase`指標傳遞給已連接的物件。 如果改為傳遞 NULL,`CRecordset`則`CDatabase`為您 創建一個物件並連接它。 在這兩種情況下,`CRecordset`都在此變數中儲存指標。

通常,您不需要直接使用存儲在中的`m_pDatabase`指標。 但是,如果將自己的擴展寫入`CRecordset`,則可能需要使用指標。 例如,如果拋出自己的`CDBException`指標,則可能需要指標。 或者,如果需要使用同一`CDatabase`物件執行某些操作,例如運行事務、設置超時或調用`ExecuteSQL``CDatabase`類 的成員函數直接執行 SQL 語句,則可能需要它。

## <a name="crecordsetm_strfilter"></a><a name="m_strfilter"></a>CRecordset::m_strFilter

建構記錄集物件後,但在調用其成員`Open`函數之前,使用此資料成員存儲包含 SQL`CString` **WHERE**子句的 。

### <a name="remarks"></a>備註

記錄集使用此字串來約束(或篩選)它在`Open`或`Requery`調用期間選擇的記錄。 這對於選擇記錄子集非常有用,例如"位於加利福尼亞州的所有銷售人員"("州 + CA")。 **WHERE**子句的 ODBC SQL 語法是

`WHERE search-condition`

請注意,您沒有在字串中包含**WHERE**關鍵字。 框架提供它。

還可以通過將『占位符放入篩選器字串、在每個占位元的類中聲明參數數據成員以及在運行時將參數傳遞給記錄集來參數化。 這允許您在運行時建構篩選器。 有關詳細資訊,請參閱[記錄集:參數化記錄集 (ODBC)。](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

有關 SQL **WHERE**子句的詳細資訊,請參閱文章[SQL](../../data/odbc/sql.md)。 有關選擇和篩選記錄的詳細資訊,請參閱[文章"記錄集:篩選記錄"(ODBC)。](../../data/odbc/recordset-filtering-records-odbc.md)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#30](../../mfc/codesnippet/cpp/crecordset-class_12.cpp)]

## <a name="crecordsetm_strsort"></a><a name="m_strsort"></a>CRecordset:m_strSort

建構記錄集物件後,但在呼叫其成員`Open`函數之前,使用此資料成員儲存包含 SQL `CString` ORDER **BY**子句的 。

### <a name="remarks"></a>備註

記錄集使用此字串對它在`Open`或`Requery`調用期間選擇的記錄進行排序。 可以使用此功能對一個或多個列的記錄集進行排序。 **ORDER BY**子句的 ODBC SQL 語法是

`ORDER BY sort-specification [, sort-specification]...`

排序規範是整數或列名稱。 您還可以通過將「ASC」或「DESC」追加到排序字串中的列清單來指定遞增或降序(預設情況下順序是上升的)。 所選記錄首先按列出的第一列排序,然後按第二列排序,等等。 例如,您可以按姓氏先訂購"客戶"記錄集,然後按名字排序。 可以列出的列數取決於數據源。 有關詳細資訊,請參閱 Windows SDK。

請注意,您沒有在字串中包括**ORDER BY**關鍵字。 框架提供它。

有關 SQL 子句的詳細資訊,請參考文章[SQL](../../data/odbc/sql.md)。 有關對記錄進行排序的詳細資訊,請參閱[文章"記錄集:排序記錄"(ODBC)。](../../data/odbc/recordset-sorting-records-odbc.md)

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#31](../../mfc/codesnippet/cpp/crecordset-class_13.cpp)]

## <a name="crecordsetmove"></a><a name="move"></a>C 記錄集::移動

向前或向後移動記錄集中的當前記錄指標。

```
virtual void Move(
    long nRows,
    WORD wFetchType = SQL_FETCH_RELATIVE);
```

### <a name="parameters"></a>參數

*nRows*<br/>
要向前或向後移動的行數。 正值向前移動,接近記錄集的末尾。 負值向後移動,向起點移動。

*wFetchType*<br/>
確定將提取的`Move`行集。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

如果為*nRows*傳遞值`Move`0, 請刷新當前記錄;如果為 nRows 傳遞值為 0,則刷新當前記錄。`Move`將結束任何當前`AddNew``Edit`或模式,並在調`AddNew`用`Edit`之前 還原當前記錄的值。

> [!NOTE]
> 當您瀏覽記錄集時,不能跳過已刪除的記錄。 關於詳細資訊[,請參閱 CRecordset:已刪除](#isdeleted)。 使用`skipDeletedRecords`選項集`CRecordset`打開`Move`打開 的 時,斷言*nRows*參數是否為 0。 此行為可防止刷新由使用相同數據的其他用戶端應用程式刪除的行。 有關`skipDeletedRecords`的說明,請參閱[Open](#open)中的*dwOption*參數。

`Move`按行集重新置放記錄集。 基於*nRows*和*wFetchType*的值`Move`,獲取相應的行集,然後使該行中的第一個記錄集當前記錄。 如果尚未實現批量行提取,則行集大小始終為 1。 提取行集時,`Move`直接呼叫[CheckRowsetError](#checkrowseterror)成員函數來處理從提取中產生的任何錯誤。

根據您傳遞的值,`Move`等效於其他`CRecordset`成員 函數。 特別是 *,wFetchType*的值可能指示一個成員函數更直觀,並且通常是移動當前記錄的首選方法。

下表列出了*wFetchType*的`Move`可能值 ,該行集將基於*wFetchType*和*nRows*提取,以及任何對應於*wFetchType*的等效成員函數。

|wFetchType|擷取的列集|等效成員函數|
|----------------|--------------------|--------------------------------|
|SQL_FETCH_RELATIVE(預設值)|從當前行集中的第一行開始*nRows*行的行集。||
|SQL_FETCH_NEXT|下一個行集;*nRows*將被忽略。|[MoveNext](#movenext)|
|SQL_FETCH_PRIOR|上一個行集;*nRows*將被忽略。|[移動Prev](#moveprev)|
|SQL_FETCH_FIRST|記錄集中的第一個行集;*nRows*將被忽略。|[MoveFirst](#movefirst)|
|SQL_FETCH_LAST|記錄集中的最後一個完整行集;*nRows*將被忽略。|[移動上次](#movelast)|
|SQL_FETCH_ABSOLUTE|如果*nRows* > 0,則從記錄集的開頭開始*nRows*行的行集將從記錄集開始。 如果*nRows* < 0,則從記錄集末尾啟動*nRows*行的行集。 如果*nRows* = 0,則傳回檔案開頭 (BOF) 條件。|[設定絕對位置](#setabsoluteposition)|
|SQL_FETCH_BOOKMARK|從書籤值對應於*nRows*的行開始的行集。|[設定書籤](#setbookmark)|

> [!NOTE]
> 對於僅轉發記錄集,`Move`僅對*wFetchType*的值為 SQL_FETCH_NEXT有效。

> [!CAUTION]
> 如果`Move`記錄集沒有記錄,則調用將引發異常。 要確定記錄集是否有任何記錄,請致電[IsBOF](#isbof)和[IsEOF](#iseof)。

> [!NOTE]
> 如果捲軸紀錄集的開頭`IsBOF`或結尾 (或`IsEOF`傳回非零),則呼叫函`Move`數 可能會`CDBException`引發 。 例如,如果`IsEOF`返回非零,則`IsBOF`不返回,則`MoveNext`將引發異常,但不會`MovePrev`。

> [!NOTE]
> 如果在更新或`Move`添加當前記錄時調用,更新將丟失,而不會發出警告。

有關記錄集導航的詳細資訊,請參閱[文章"記錄集:滾動(ODBC)"](../../data/odbc/recordset-scrolling-odbc.md)和[「記錄集:書籤和絕對位置 (ODBC)」。。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。 有關相關資訊,請參閱 Windows SDK 中的`SQLExtendedFetch`ODBC API 功能。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#28](../../mfc/codesnippet/cpp/crecordset-class_14.cpp)]

## <a name="crecordsetmovefirst"></a><a name="movefirst"></a>C 記錄集::先移動

使第一行中的第一個記錄成為當前記錄。

```cpp
void MoveFirst();
```

### <a name="remarks"></a>備註

無論是否實現了批量行提取,這始終是記錄集中的第一個記錄。

打開記錄集后,不必`MoveFirst`立即調用。 此時,第一條記錄(如果有)自動是當前記錄。

> [!NOTE]
> 此成員函數對於僅轉發記錄集無效。

> [!NOTE]
> 當您瀏覽記錄集時,不能跳過已刪除的記錄。 有關詳細資訊,請參閱[IsDelete 成員](#isdeleted)函數。

> [!CAUTION]
> 如果記錄集沒有`Move`記錄,則調用任何函數都會引發異常。 要確定記錄集是否有任何紀錄,請呼叫`IsBOF`與`IsEOF`。

> [!NOTE]
> 如果在更新或添加當前記錄`Move`時調用任何函數,則更新將丟失,而不會發出警告。

有關記錄集導航的詳細資訊,請參閱[文章"記錄集:滾動(ODBC)"](../../data/odbc/recordset-scrolling-odbc.md)和[「記錄集:書籤和絕對位置 (ODBC)」。。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>範例

  請參閱[IsBOF](#isbof)的範例。

## <a name="crecordsetmovelast"></a><a name="movelast"></a>C 記錄集::移動上次

使最後一個完整行中的第一個記錄成為當前記錄。

```cpp
void MoveLast();
```

### <a name="remarks"></a>備註

如果尚未實現批量行提取,則記錄集的行集大小為 1,`MoveLast`因此 只需移動到記錄集中的最後一個記錄。

> [!NOTE]
> 此成員函數對於僅轉發記錄集無效。

> [!NOTE]
> 當您瀏覽記錄集時,不能跳過已刪除的記錄。 有關詳細資訊,請參閱[IsDelete 成員](#isdeleted)函數。

> [!CAUTION]
> 如果記錄集沒有`Move`記錄,則調用任何函數都會引發異常。 要確定記錄集是否有任何紀錄,請呼叫`IsBOF`與`IsEOF`。

> [!NOTE]
> 如果在更新或添加當前記錄`Move`時調用任何函數,則更新將丟失,而不會發出警告。

有關記錄集導航的詳細資訊,請參閱[文章"記錄集:滾動(ODBC)"](../../data/odbc/recordset-scrolling-odbc.md)和[「記錄集:書籤和絕對位置 (ODBC)」。。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>範例

  請參閱[IsBOF](#isbof)的範例。

## <a name="crecordsetmovenext"></a><a name="movenext"></a>C記錄集::移動下一個

使下一行中的第一個記錄成為當前記錄。

```cpp
void MoveNext();
```

### <a name="remarks"></a>備註

如果尚未實現批量行提取,則記錄集的行集大小為 1,`MoveNext`因此 只需移動到下一條記錄即可。

> [!NOTE]
> 當您瀏覽記錄集時,不能跳過已刪除的記錄。 有關詳細資訊,請參閱[IsDelete 成員](#isdeleted)函數。

> [!CAUTION]
> 如果記錄集沒有`Move`記錄,則調用任何函數都會引發異常。 要確定記錄集是否有任何紀錄,請呼叫`IsBOF`與`IsEOF`。

> [!NOTE]
> 還建議您在致電之前打電話`IsEOF``MoveNext`。 例如,如果滾動超過記錄集的末尾,則返回非零;如果`IsEOF`已滾動過去記錄集的末尾,則返回非零。後續調用`MoveNext`將引發異常。

> [!NOTE]
> 如果在更新或添加當前記錄`Move`時調用任何函數,則更新將丟失,而不會發出警告。

有關記錄集導航的詳細資訊,請參閱[文章"記錄集:滾動(ODBC)"](../../data/odbc/recordset-scrolling-odbc.md)和[「記錄集:書籤和絕對位置 (ODBC)」。。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>範例

  請參閱[IsBOF](#isbof)的範例。

## <a name="crecordsetmoveprev"></a><a name="moveprev"></a>C記錄集::MovePrev

使上一行中的第一個記錄成為當前記錄。

```cpp
void MovePrev();
```

### <a name="remarks"></a>備註

如果尚未實現批量行提取,則記錄集的行集大小為 1,`MovePrev`因此 只需移動到以前的記錄即可。

> [!NOTE]
> 此成員函數對於僅轉發記錄集無效。

> [!NOTE]
> 當您瀏覽記錄集時,不能跳過已刪除的記錄。 有關詳細資訊,請參閱[IsDelete 成員](#isdeleted)函數。

> [!CAUTION]
> 如果記錄集沒有`Move`記錄,則調用任何函數都會引發異常。 要確定記錄集是否有任何紀錄,請呼叫`IsBOF`與`IsEOF`。

> [!NOTE]
> 還建議您在致電之前打電話`IsBOF``MovePrev`。 例如,如果您在記錄集的開頭之前滾動過,`IsBOF`則返回非零;如果已滾動到記錄集的開頭,則返回非零。後續調用`MovePrev`將引發異常。

> [!NOTE]
> 如果在更新或添加當前記錄`Move`時調用任何函數,則更新將丟失,而不會發出警告。

有關記錄集導航的詳細資訊,請參閱[文章"記錄集:滾動(ODBC)"](../../data/odbc/recordset-scrolling-odbc.md)和[「記錄集:書籤和絕對位置 (ODBC)」。。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md) 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

### <a name="example"></a>範例

  請參閱[IsBOF](#isbof)的範例。

## <a name="crecordsetonsetoptions"></a><a name="onsetoptions"></a>CRecordset::開啟選項

呼叫以為指定的 ODBC 語句設定選項(在選擇時使用)。

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>參數

*hstmt*<br/>
待設置選項的 ODBC 語句的 HSTMT。

### <a name="remarks"></a>備註

呼叫`OnSetOptions`為指定的 ODBC 語句設定選項(在選擇時使用)。 框架呼叫此成員函數以設定記錄集的初始選項。 `OnSetOptions`確定數據源對可滾動游標和游標併發的支援,並相應地設置記錄集的選項。 (用於`OnSetOptions`選擇操作的`OnSetUpdateOptions`,用於更新操作。

覆蓋`OnSetOptions`以設置特定於驅動程式或數據源的選項。 例如,如果數據源支援打開獨佔訪問,則可以重寫`OnSetOptions`以利用該功能。

有關游標的詳細資訊,請參閱文章[ODBC](../../data/odbc/odbc-basics.md)。

## <a name="crecordsetonsetupdateoptions"></a><a name="onsetupdateoptions"></a>CRecordset::開啟更新選項

呼叫以為指定的 ODBC 語句設定選項(在更新時使用)。

```
virtual void OnSetUpdateOptions(HSTMT hstmt);
```

### <a name="parameters"></a>參數

*hstmt*<br/>
待設置選項的 ODBC 語句的 HSTMT。

### <a name="remarks"></a>備註

呼叫`OnSetUpdateOptions`為指定的 ODBC 語句設定選項(在更新時使用)。 框架在創建 HSTMT 以更新記錄集中的記錄後調用此成員函數。 (用於`OnSetOptions`選擇操作的`OnSetUpdateOptions`,用於更新操作。`OnSetUpdateOptions`確定數據源對可滾動游標和游標併發的支援,並相應地設置記錄集的選項。

在`OnSetUpdateOptions`使用該語句訪問資料庫之前,重寫以設置 ODBC 語句的選項。

有關游標的詳細資訊,請參閱文章[ODBC](../../data/odbc/odbc-basics.md)。

## <a name="crecordsetopen"></a><a name="open"></a>CRecordset::開啟

通過檢索表或執行記錄集表示的查詢來打開記錄集。

```
virtual BOOL Open(
    UINT nOpenType = AFX_DB_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    DWORD dwOptions = none);
```

### <a name="parameters"></a>參數

*N 開放類型*<br/>
接受預設值,AFX_DB_USE_DEFAULT_TYPE或使用的以下值之一`enum OpenType`:

- `CRecordset::dynaset`具有雙向滾動的記錄集。 記錄的成員身份和順序在打開記錄集時確定,但其他用戶對數據值所做的更改在提取操作後可見。 動態集也稱為鍵集驅動的記錄集。

- `CRecordset::snapshot`具有雙向滾動的靜態記錄集。 打開記錄集時確定記錄的成員身份和順序;提取記錄時確定數據值。 在關閉記錄集然後重新打開之前,其他使用者所做的更改不可見。

- `CRecordset::dynamic`具有雙向滾動的記錄集。 其他使用者對成員資格、排序和數據值所做的更改在提取操作後可見。 請注意,許多ODBC驅動程式不支援這種類型的記錄集。

- `CRecordset::forwardOnly`只具有前進滾動的唯讀記錄集。

   對於`CRecordset`,預設值`CRecordset::snapshot`為 。 默認值機制允許 VisualC++嚮導與具有不同預設值的`CRecordset`ODBC`CDaoRecordset`和 DAO 進行交互。

有關這些紀錄集類型的詳細資訊,請參閱文章[記錄集 (ODBC)](../../data/odbc/recordset-odbc.md)。 有關相關資訊,請參閱 Windows SDK 中的"使用塊和可滾動游標"一文。

> [!CAUTION]
> 如果不支援請求的類型,則框架將引發異常。

*lpszSQL*<br/>
包含以下的字串指標:

- NULL指標。

- 資料表的名稱。

- SQL **SELECT**語句(可選使用 SQL **WHERE**或**ORDER BY**子句)。

- 指定預先定義查詢名稱的**CALL**語句(儲存過程)。 請注意,不要在大括弧和**CALL**關鍵字之間插入空格。

有關此字串的詳細資訊,請參閱「[備註」](#remarks)部分下的表和 ClassWizard 角色的討論。

> [!NOTE]
> 結果集中的列順序必須與[DoFieldExchange](#dofieldexchange)或[DoBulkFieldExchange](#dobulkfieldexchange)函數覆蓋中的 RFX 或批量 RFX 函數調用的順序匹配。

*dwOptions*<br/>
可以指定下面列出的值組合的位掩碼。 其中一些是相互排斥的。 預設值為**none**。

- `CRecordset::none`未設置選項。 此參數值與所有其他值是互斥的。 預設情況下,可以使用[「編輯](#edit)」或[「刪除](#delete)」更新記錄集,並允許使用[AddNew](#addnew)追加新記錄。 高資料度取決於資料來源以及您指定的*nOpenType*選項。 批量添加的優化不可用。 不會實現批量行提取。 在記錄集導航期間,不會跳過已刪除的記錄。 書籤不可用。 實現了自動臟場檢查。

- `CRecordset::appendOnly`不允許`Edit``Delete`或記錄集上。 僅`AddNew`允許。 此選項與`CRecordset::readOnly`是互斥的。

- `CRecordset::readOnly`將記錄集設置為唯讀。 此選項與`CRecordset::appendOnly`是互斥的。

- `CRecordset::optimizeBulkAdd`使用準備好的 SQL 語句一次優化添加許多記錄。 僅當您不使用 ODBC API`SQLSetPos`函數 更新記錄集時,才適用。 第一個更新確定哪些欄位標記為髒。 此選項與`CRecordset::useMultiRowFetch`是互斥的。

- `CRecordset::useMultiRowFetch`實現批量行提取,以允許在單個提取操作中檢索多行。 這是一個高級功能,旨在提高性能;但是,類嚮導不支援批量記錄欄位交換。 此選項與`CRecordset::optimizeBulkAdd`是互斥的。 請注意,如果指定`CRecordset::useMultiRowFetch`,則該`CRecordset::noDirtyFieldCheck`選項 將自動打開(雙緩衝將不可用);在僅轉發記錄集上,該選項`CRecordset::useExtendedFetch`將自動打開。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

- `CRecordset::skipDeletedRecords`在瀏覽記錄集時跳過所有已刪除的記錄。 這將降低某些相對獲取的性能。 此選項在僅轉發記錄集上無效。 如果呼叫[「移動」](#move)將斷言*nRows*`CRecordset::skipDeletedRecords`參數設定為`Move`0,並且 選項集將斷言。 注意,`CRecordset::skipDeletedRecords`它類似於*驅動程式打包*,這意味著從記錄集中刪除已刪除的行。 但是,如果驅動程式打包記錄,則它將僅跳過您刪除的記錄;如果驅動程式包含記錄,則僅跳過您刪除的記錄。在記錄集打開時,它將不會跳過其他使用者刪除的記錄。 `CRecordset::skipDeletedRecords`將跳過其他使用者刪除的行。

- `CRecordset::useBookmarks`如果支援,可在記錄集中使用書籤。 書籤可減緩數據檢索速度,但提高了數據導航的性能。 在僅轉發記錄集上無效。 有關詳細資訊,請參閱[文章記錄集:書籤和絕對位置 (ODBC)。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- `CRecordset::noDirtyFieldCheck`關閉自動臟場檢查(雙緩衝)。 這將提高性能;但是,必須通過調用`SetFieldDirty`和`SetFieldNull`成員函數手動將欄位標記為髒。請注意,類`CRecordset`中的雙緩衝類似於`CDaoRecordset`類 中的雙緩衝。 但是,在`CRecordset`中,不能對單個字段啟用雙重緩衝;在 中,無法對單個字段啟用雙重緩衝。您可以為所有欄位啟用它,或者禁用它對所有欄位。 請注意,如果指定選項`CRecordset::useMultiRowFetch`, 則`CRecordset::noDirtyFieldCheck`將自動 開啟;如果指定選項,則將自動打開。但是,`SetFieldDirty``SetFieldNull`並且不能用於實現批量行提取的記錄集。

- `CRecordset::executeDirect`不要使用準備好的 SQL 語句。 為提高性能,如果永遠不會調用成員函數,`Requery`請指定此選項。

- `CRecordset::useExtendedFetch`實`SQLExtendedFetch`作`SQLFetch`而不是 。 這是為在僅轉發記錄集上實現批量行提取而設計的。 如果在僅轉發記錄集中`CRecordset::useMultiRowFetch`指定該選項,`CRecordset::useExtendedFetch`則將自動打開。

- `CRecordset::userAllocMultiRowBuffers`使用者將為數據分配存儲緩衝區。 如果要分配自己的存儲,`CRecordset::useMultiRowFetch`請使用此選項;否則,框架將自動分配必要的存儲。 有關詳細資訊,請參閱[記錄集:批次取得紀錄 (ODBC) 的文章](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。 請注意,不`CRecordset::userAllocMultiRowBuffers`指定`CRecordset::useMultiRowFetch`指定將導致斷言失敗。

### <a name="return-value"></a>傳回值

如果物件已成功打開`CRecordset`,則非零;否則 0 如果[CDatabase::打開](../../mfc/reference/cdatabase-class.md#open)(如果呼叫)返回 0。

### <a name="remarks"></a>備註

必須調用此成員函數才能運行由記錄集定義的查詢。 在調用`Open`之前,必須構造記錄集物件。

此記錄集與數據源的連接取決於在調用`Open`之前如何構造記錄集。 如果將[CDatabase](../../mfc/reference/cdatabase-class.md)物件傳遞給尚未連接到資料來源的記錄集建構函數,則此成員函數使用[GetDefaultConnect](#getdefaultconnect)嘗試打開資料庫物件。 如果將 NULL 傳遞給記錄集建構函數,則建構函數會為您建`CDatabase`構一個物件,`Open`並嘗試 連接資料庫物件。 有關在這些不同情況下關閉記錄集和連線的詳細資訊,請參閱[關閉](#close)。

> [!NOTE]
> 始終共用通過`CRecordset`對象訪問數據源。 與`CDaoRecordset`類別不同,`CRecordset`不能使用物件打開具有獨佔存取權限的資料來源。

調用`Open`查詢(通常是 SQL **SELECT**語句)時,會根據下表中顯示的條件選擇記錄。

|lpszSQL 參數的值|選取的紀錄由|範例|
|------------------------------------|----------------------------------------|-------------|
|NULL|返回`GetDefaultSQL`的字串。||
|SQL 表格名稱|表清單的所有列。 `DoFieldExchange` `DoBulkFieldExchange`|`"Customer"`|
|預先定義查詢 (儲存程序)名稱|要返回的查詢的列。|`"{call OverDueAccts}"`|
|**從**表列表中**選擇**欄清單|指定表中的指定欄位。|`"SELECT CustId, CustName FROM`<br /><br /> `Customer"`|

> [!CAUTION]
> 請注意,不要在 SQL 字串中插入額外的空白。 例如,如果在大括弧和**CALL**關鍵字之間插入空格,MFC 會將 SQL 字串誤解為表名並將其合併到**SELECT**語句中,這將導致引發異常。 同樣,如果預定義的查詢使用輸出參數,請不要在大括弧和『符號之間插入空格。 最後,不得在**CALL**語句中大括弧之前或**SELECT**語句中的**SELECT**關鍵字之前插入空格。

通常的程式是將 NULL`Open`傳遞給 。在這種情況下,`Open`呼叫[GetDefaultSQL](#getdefaultsql)。 如果使用派生`CRecordset`類,`GetDefaultSQL`則提供在 ClassWizard 中指定的表名稱。 您可以改為在`lpszSQL`參數中指定其他資訊。

無論您通過什麼,`Open`都會建構查詢的最終 SQL 字串(該字串可能將 SQL **WHERE**和`lpszSQL`**ORDER BY**子 句追加到您傳遞的字串中),然後執行查詢。 您可以通過呼叫[GetSQL](#getsql)`Open`在呼叫 後檢查建構的字串。 有關記錄集如何建構 SQL 語句和選擇紀錄的其他詳細資訊,請參閱[記錄集:記錄集如何選擇記錄 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)。

記錄集類的欄位數據成員綁定到選取資料的列。 如果返回任何記錄,則第一條記錄將成為當前記錄。

如果要為記錄集設置選項(如篩選器或排序),請在構造記錄集物件后但在調用`Open`之前指定這些選項。 如果要在紀錄集開啟後刷新記錄集中的記錄,請呼叫[重新查詢](#requery)。

有關詳細資訊(包括其他範例),請參閱[文章記錄集 (ODBC)](../../data/odbc/recordset-odbc.md)、[記錄集:記錄集如何選擇記錄 (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)和[記錄集:創建和關閉記錄集 (ODBC)。](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

### <a name="example"></a>範例

以下代碼示例顯示了不同形式的`Open`調用。

[!code-cpp[NVC_MFCDatabase#16](../../mfc/codesnippet/cpp/crecordset-class_15.cpp)]

## <a name="crecordsetrefreshrowset"></a><a name="refreshrowset"></a>C記錄集::刷新羅塞特

更新當前行集中行的數據和狀態。

```cpp
void RefreshRowset(
    WORD wRow,
    WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>參數

*wRow*<br/>
當前行集中行的基於一個位置。 此值的範圍可以從零到行集的大小。

*wLock 類型*<br/>
指示如何在刷新行后鎖定行的值。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

如果為*wRow*傳遞值為零,則行集中的每一行都將刷新。

要使用`RefreshRowset`,必須透過`CRecordset::useMulitRowFetch`在[Open](#open)成員函數中指定選項來實現大量的量行提取。

`RefreshRowset`呼叫 ODBC`SQLSetPos`API 函式 。 *wLockType*參數指定執行`SQLSetPos`後 行的鎖定狀態。 下表描述了*wLockType*的可能值。

|wLock 類型|描述|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE(預設值)|驅動程式或數據源可確保該行處於與調用之前`RefreshRowset`相同的鎖定或解鎖狀態。|
|SQL_LOCK_EXCLUSIVE|驅動程式或數據源專門鎖定行。 並非所有數據源都支援這種類型的鎖。|
|SQL_LOCK_UNLOCK|驅動程式或數據源解鎖該行。 並非所有數據源都支援這種類型的鎖。|

有關的詳細資訊`SQLSetPos`,請參閱 Windows SDK。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

## <a name="crecordsetrequery"></a><a name="requery"></a>C記錄集::重新查詢

重建(刷新)記錄集。

```
virtual BOOL Requery();
```

### <a name="return-value"></a>傳回值

如果成功重建記錄集,則非零;否則 0。

### <a name="remarks"></a>備註

如果返回任何記錄,則第一條記錄將成為當前記錄。

為了使記錄集反映您或其他使用者對數據源進行的添加和刪除,必須通過調用`Requery`來重新生成記錄集。 如果記錄集是動態集,它會自動反映您或其他使用者對其現有記錄(但不是添加)進行的更新。 如果記錄集是快照,則必須調用`Requery`以反映其他使用者的編輯以及添加和刪除。

對於動態集或快照,在您希望使用新篩選器`Requery`或排序或新參數值重建記錄集的任何時間調用。 通過將新值分配給`m_strFilter``m_strSort`和 之前`Requery`調用 ,設置新的篩選器或排序屬性。 通過在調用`Requery`之前將新值分配給參數數據成員來設置新參數。 如果篩選器和排序字串保持不變,則可以重用查詢,從而提高性能。

如果重建記錄集的嘗試失敗,記錄集將關閉。 在調用`Requery`之前,可以通過`CanRestart`調用成員函數確定是否可以重新查詢記錄集。 `CanRestart`不能保證會`Requery`成功。

> [!CAUTION]
> 只在`Requery`呼叫[Open](#open)後才能通話 。

### <a name="example"></a>範例

此示例重建記錄集以應用其他排序順序。

[!code-cpp[NVC_MFCDatabase#29](../../mfc/codesnippet/cpp/crecordset-class_16.cpp)]

## <a name="crecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>C記錄集::設定絕對位置

將記錄集放在與指定記錄編號對應的記錄上。

```cpp
void SetAbsolutePosition(long nRows);
```

### <a name="parameters"></a>參數

*nRows*<br/>
記錄集中當前記錄的一個基於的盤位位置。

### <a name="remarks"></a>備註

`SetAbsolutePosition`基於此位形位置移動當前記錄指標。

> [!NOTE]
> 此成員函數在僅轉發記錄集上無效。

對於 ODBC 記錄集,絕對位置設置為 1 是指記錄集中的第一個記錄;設置為 0 是指檔開始 (BOF) 位置。

還可以將負值傳遞給`SetAbsolutePosition`。 在這種情況下,記錄集的位置從記錄集的末尾計算。 例如,`SetAbsolutePosition( -1 )`將目前記錄指標移動到記錄集中的最後一個記錄。

> [!NOTE]
> 絕對位置不用作代理記錄編號。 書籤仍然是保留和返回到給定位置的推薦方式,因為刪除之前的記錄時記錄的位置會發生變化。 此外,如果再次重新創建記錄集,則無法保證給定記錄集具有相同的絕對位置,因為除非使用**ORDER BY**子句使用 SQL 語句創建記錄集中的單個記錄的順序不保證。

有關記錄集導航和書籤的詳細資訊,請參閱[文章"記錄集:滾動 (ODBC)"](../../data/odbc/recordset-scrolling-odbc.md)和[「記錄集:書籤和絕對位置 (ODBC)」。。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

## <a name="crecordsetsetbookmark"></a><a name="setbookmark"></a>CRecordset::設定書籤

在包含指定書籤的記錄上定位記錄集。

```cpp
void SetBookmark(const CDBVariant& varBookmark);
```

### <a name="parameters"></a>參數

*瓦爾布克馬克*<br/>
對包含特定記錄的書籤值的[CDBVariant](../../mfc/reference/cdbvariant-class.md)物件的引用。

### <a name="remarks"></a>備註

要確定記錄集是否支援書籤,請呼叫[CanBookmark](#canbookmark)。 要使書籤在受支援時可用,必須在[Open](#open)成員`CRecordset::useBookmarks`函數 的*dwOptions*參數中設置該選項。

> [!NOTE]
> 如果書籤不受支援或不可用,則調用`SetBookmark`將導致引發異常。 僅轉發記錄集不支援書籤。

若要首先檢索當前記錄的書籤,請調用[GetBookmark,](#getbookmark)這將書籤值`CDBVariant`保存到 物件。 稍後,您可以使用保存的書籤值調用`SetBookmark`該記錄。

> [!NOTE]
> 在某些記錄集操作后,應在調用`SetBookmark`之前檢查書籤持久性。 例如,如果檢索書籤,`GetBookmark`然後調`Requery`用 ,書籤可能不再有效。 呼叫[CDatabase:取得書籤持久性](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence),以檢查是否可以安全地`SetBookmark`呼叫 。

有關書籤和記錄集導航的詳細資訊,請參閱[文章「記錄集:書籤和絕對位置 (ODBC)」](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)和[「記錄集:滾動 (ODBC)」。。](../../data/odbc/recordset-scrolling-odbc.md)

## <a name="crecordsetsetfielddirty"></a><a name="setfielddirty"></a>C記錄集::設定欄位臟

將記錄集的欄位數據成員標記為已更改或未更改。

```cpp
void SetFieldDirty(void* pv, BOOL bDirty = TRUE);
```

### <a name="parameters"></a>參數

*光伏*<br/>
在記錄集或 NULL 中包含欄位資料成員的位址。 如果為 NULL,則記錄集中的所有欄位數據成員將被標記。 (C++ NULL 與資料庫術語中的 Null 不同,這意味著"沒有值"。

*bDirty*<br/>
如果欄位數據成員被標記為「臟」(已更改),則為 TRUE。 否則,如果欄位數據成員被標記為「乾淨」(未更改),則 FALSE。

### <a name="remarks"></a>備註

將欄位標記為未更改可確保欄位不會更新,並減少 SQL 流量。

> [!NOTE]
> 此成員函數不適用於使用批量行提取的記錄集。 如果已實現批量行提取,則`SetFieldDirty`將導致斷言失敗。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

框架標記已更改的欄位數據成員,以確保它們將由記錄欄位交換 (RFX) 機制寫入數據來源上的記錄。 變更欄位的值通常會自動將欄位設定髒,因此您很少需要調用`SetFieldDirty`自己,但有時您可能希望確保無論欄位資料成員中的哪個值如何,都會顯式更新或插入列。

> [!CAUTION]
> 只在呼叫[「編輯」](#edit)或[「新增 New」](#addnew)後才能呼叫此成員函數。

對函數的第一個參數使用 NULL 將僅將函數`outputColumn`應用於欄位`param`,而不是欄位。 例如,呼叫

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

將僅`outputColumn`將欄位設定為 NULL;`param`欄位將不受影響。

要處理`param`欄位,必須提供要處理的`param`個人的實際位址,例如:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

這表示您不能將`param`所有欄位設定為 NULL,就像對欄位`outputColumn`一樣 。

## <a name="crecordsetsetfieldnull"></a><a name="setfieldnull"></a>C記錄集::設定欄位無效

將記錄集的欄位資料成員標記為 Null(具體沒有值)或非 Null。

```cpp
void SetFieldNull(void* pv, BOOL bNull = TRUE);
```

### <a name="parameters"></a>參數

*光伏*<br/>
在記錄集或 NULL 中包含欄位資料成員的位址。 如果為 NULL,則記錄集中的所有欄位數據成員將被標記。 (C++ NULL 與資料庫術語中的 Null 不同,這意味著"沒有值"。

*bNull*<br/>
如果要將欄位數據成員標記為無值(空),則非零。 否則 0 如果欄位數據成員被標記為非 Null。

### <a name="remarks"></a>備註

將新記錄添加到記錄集時,所有欄位數據成員最初都設置為 Null 值,並標記為「臟」(已更改)。 從資料源檢索記錄時,其列要麼已有值,要麼為 Null。

> [!NOTE]
> 不要在使用批量行提取的記錄集中調用此成員函數。 如果已實現批量行提取,則調用`SetFieldNull`會導致斷言失敗。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

如果特別希望將當前記錄的欄位指定為沒有值,則使用*bNull*`SetFieldNull`設置為 TRUE 的調用將其標記為 Null。 如果欄位以前標記為 Null,現在您希望為其提供值,只需設置其新值即可。 不必刪除帶有`SetFieldNull`的 Null 標誌。 要確定是否允許此欄位為 Null,請呼`IsFieldNullable`叫 。

> [!CAUTION]
> 只在呼叫[「編輯」](#edit)或[「新增 New」](#addnew)後才能呼叫此成員函數。

對函數的第一個參數使用 NULL 將僅將函數`outputColumn`應用於欄位`param`,而不是欄位。 例如,呼叫

[!code-cpp[NVC_MFCDatabase#26](../../mfc/codesnippet/cpp/crecordset-class_10.cpp)]

將僅`outputColumn`將欄位設定為 NULL;`param`欄位將不受影響。

要處理`param`欄位,必須提供要處理的`param`個人的實際位址,例如:

[!code-cpp[NVC_MFCDatabase#27](../../mfc/codesnippet/cpp/crecordset-class_11.cpp)]

這表示您不能將`param`所有欄位設定為 NULL,就像對欄位`outputColumn`一樣 。

> [!NOTE]
> 將參數設定為 Null 時,`SetFieldNull`在打開 記錄集之前調用 會導致斷言。 在這種情況下,呼叫[SetParamNull](#setparamnull)。

`SetFieldNull`通過[多菲爾德交易所](#dofieldexchange)實施。

## <a name="crecordsetsetlockingmode"></a><a name="setlockingmode"></a>C 記錄集::設定鎖定模式

將鎖定模式設置為「樂觀」鎖定(預設)或「悲觀」鎖定。 確定如何鎖定記錄以進行更新。

```cpp
void SetLockingMode(UINT nMode);
```

### <a name="parameters"></a>參數

*nMode*<br/>
包含 以下值之一`enum LockMode`:

- `optimistic`樂觀鎖定僅在呼叫`Update`期間更新的記錄鎖定 。

- `pessimistic`悲觀鎖定在呼叫後立即`Edit`鎖定記錄,並將其鎖定`Update`, 直到呼叫完成或移動到新記錄。

### <a name="remarks"></a>備註

如果需要指定記錄集用於更新的兩個記錄鎖定策略中的哪一個,請調用此成員函數。 預設情況下,記錄集的鎖定模式為`optimistic`。 您可以將其更改為更謹慎的`pessimistic`鎖定策略。 在`SetLockingMode`建構並開啟紀錄集物件後,但在呼叫 之前`Edit`呼叫 呼叫 。

## <a name="crecordsetsetparamnull"></a><a name="setparamnull"></a>C 記錄集::SetParamNull

將參數標記為 Null(具體沒有值)或非 Null。

```cpp
void SetParamNull(
    int nIndex,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
參數之以零為起始的索引。

*bNull*<br/>
如果 TRUE(預設值),則參數將標記為 Null。 否則,參數將標記為非 Null。

### <a name="remarks"></a>備註

與[SetFieldNull](#setfieldnull)`SetParamNull`不同, 您可以在開啟記錄集之前呼叫。

`SetParamNull`通常用於預定義的查詢(存儲過程)。

## <a name="crecordsetsetrowsetcursorposition"></a><a name="setrowsetcursorposition"></a>C 記錄集::設定羅塞特游標位置

將游標移動到當前行集中的行。

```cpp
void SetRowsetCursorPosition(WORD wRow, WORD wLockType = SQL_LOCK_NO_CHANGE);
```

### <a name="parameters"></a>參數

*wRow*<br/>
當前行集中行的基於一個位置。 此值的範圍可以從 1 到行集的大小。

*wLock 類型*<br/>
指示如何在刷新行后鎖定行的值。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

實現批量行提取時,記錄由行集檢索,其中提取的行集中的第一條記錄是當前記錄。 為了在行集中對目前的紀錄進行另一個紀錄,請呼叫`SetRowsetCursorPosition`。 例如,您可以與`SetRowsetCursorPosition`[GetFieldValue](#getfieldvalue)成員函數結合使用,從記錄集的任何記錄中動態檢索數據。

要使用`SetRowsetCursorPosition`,必須透過在[Open](#open)成員函`CRecordset::useMultiRowFetch`數中指定*dwOptions*參數的選項來實現批量行提取。

`SetRowsetCursorPosition`呼叫 ODBC`SQLSetPos`API 函式 。 *wLockType*參數指定執行`SQLSetPos`後 行的鎖定狀態。 下表描述了*wLockType*的可能值。

|wLock 類型|描述|
|---------------|-----------------|
|SQL_LOCK_NO_CHANGE(預設值)|驅動程式或數據源可確保該行處於與調用之前`SetRowsetCursorPosition`相同的鎖定或解鎖狀態。|
|SQL_LOCK_EXCLUSIVE|驅動程式或數據源專門鎖定行。 並非所有數據源都支援這種類型的鎖。|
|SQL_LOCK_UNLOCK|驅動程式或數據源解鎖該行。 並非所有數據源都支援這種類型的鎖。|

有關的詳細資訊`SQLSetPos`,請參閱 Windows SDK。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

## <a name="crecordsetsetrowsetsize"></a><a name="setrowsetsize"></a>C 記錄集::設定羅塞特大小

指定您希望在提取期間檢索的記錄數。

```
virtual void SetRowsetSize(DWORD dwNewRowsetSize);
```

### <a name="parameters"></a>參數

*dwNewRowsetSize*<br/>
給定提取期間要檢索的行數。

### <a name="remarks"></a>備註

此虛擬成員函數指定在使用批量行提取時希望在單個提取期間檢索多少行。 要實現大量的批次提取,必須在[Open](#open)Open`CRecordset::useMultiRowFetch`成員函數的*dwOptions*參數中設定該選項。

> [!NOTE]
> 不`SetRowsetSize`實現批量行提取的調用將導致斷言失敗。

調用`SetRowsetSize``Open`之前調用以最初設置記錄集的行集大小。 實現批量行提取時的預設行集大小為 25。

> [!NOTE]
> 調用`SetRowsetSize`時要小心。 如果要手動分配數據的存儲(如中的`CRecordset::userAllocMultiRowBuffers``Open`dwOptions 參數的選項指定),則應檢查是否需要在`SetRowsetSize`調用 後,但在執行任何游標導航操作之前重新分配這些儲存緩衝區。

要取得列集大小的目前設定,請呼叫[GetRowsetSize](#getrowsetsize)。

如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

## <a name="crecordsetupdate"></a><a name="update"></a>CRecordset::更新

通過在數據源上`AddNew``Edit`保存 新的或編輯的數據來完成 或操作。

```
virtual BOOL Update();
```

### <a name="return-value"></a>傳回值

如果成功更新一條記錄,則非零;否則 0 如果沒有列更改。 如果未更新任何記錄,或者更新了多個記錄,則引發異常。 對於數據源上的任何其他故障,也會引發異常。

### <a name="remarks"></a>備註

呼叫['新增](#addnew)'或["編輯](#edit)"成員函數後呼叫此成員函數。 完成`AddNew``Edit`或操作需要此調用。

> [!NOTE]
> 如果已實現大量的批次提取,則無法呼叫`Update`。 這將導致斷言失敗。 儘管類`CRecordset`不提供更新批量資料行的機制,但您可以使用 ODBC API 函數編`SQLSetPos`寫自己的函數 。 如需大量資料列擷取的詳細資訊，請參閱 [資料錄集：擷取大量資料錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)一文。

`AddNew`並`Edit`準備一個編輯緩衝區,其中添加或編輯的數據被放置到數據源中。 `Update`保存數據。 只會更新標記為或檢測到已更改的欄位。

如果數據源支援事務,則可以將`Update`調用(及其相應的`AddNew``Edit`或調用)作為事務的一部分。 有關交易記錄的詳細資訊,請參閱文章[事務 (ODBC)](../../data/odbc/transaction-odbc.md)。

> [!CAUTION]
> 如果在未首先`Update`呼叫`AddNew``Edit`或 的情況下`Update`呼`CDBException`叫 , 則引發 。 如果呼叫`AddNew``Edit`或 ,必須在`Update``Move`呼叫操作之前或關閉記錄集或資料源連接之前呼叫。 否則,您的更改將丟失,恕不另行通知。

有關處理`Update`失敗的詳細資訊,請參閱[記錄集:記錄集如何更新記錄 (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)。

### <a name="example"></a>範例

請參閱文章[「事務:在記錄集 (ODBC) 中執行事務](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)」。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDatabase 類別](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordView 類別](../../mfc/reference/crecordview-class.md)
