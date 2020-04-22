---
title: CDaoRecordset 類別
ms.date: 08/27/2018
f1_keywords:
- CDaoRecordset
- AFXDAO/CDaoRecordset
- AFXDAO/CDaoRecordset::CDaoRecordset
- AFXDAO/CDaoRecordset::AddNew
- AFXDAO/CDaoRecordset::CanAppend
- AFXDAO/CDaoRecordset::CanBookmark
- AFXDAO/CDaoRecordset::CancelUpdate
- AFXDAO/CDaoRecordset::CanRestart
- AFXDAO/CDaoRecordset::CanScroll
- AFXDAO/CDaoRecordset::CanTransact
- AFXDAO/CDaoRecordset::CanUpdate
- AFXDAO/CDaoRecordset::Close
- AFXDAO/CDaoRecordset::Delete
- AFXDAO/CDaoRecordset::DoFieldExchange
- AFXDAO/CDaoRecordset::Edit
- AFXDAO/CDaoRecordset::FillCache
- AFXDAO/CDaoRecordset::Find
- AFXDAO/CDaoRecordset::FindFirst
- AFXDAO/CDaoRecordset::FindLast
- AFXDAO/CDaoRecordset::FindNext
- AFXDAO/CDaoRecordset::FindPrev
- AFXDAO/CDaoRecordset::GetAbsolutePosition
- AFXDAO/CDaoRecordset::GetBookmark
- AFXDAO/CDaoRecordset::GetCacheSize
- AFXDAO/CDaoRecordset::GetCacheStart
- AFXDAO/CDaoRecordset::GetCurrentIndex
- AFXDAO/CDaoRecordset::GetDateCreated
- AFXDAO/CDaoRecordset::GetDateLastUpdated
- AFXDAO/CDaoRecordset::GetDefaultDBName
- AFXDAO/CDaoRecordset::GetDefaultSQL
- AFXDAO/CDaoRecordset::GetEditMode
- AFXDAO/CDaoRecordset::GetFieldCount
- AFXDAO/CDaoRecordset::GetFieldInfo
- AFXDAO/CDaoRecordset::GetFieldValue
- AFXDAO/CDaoRecordset::GetIndexCount
- AFXDAO/CDaoRecordset::GetIndexInfo
- AFXDAO/CDaoRecordset::GetLastModifiedBookmark
- AFXDAO/CDaoRecordset::GetLockingMode
- AFXDAO/CDaoRecordset::GetName
- AFXDAO/CDaoRecordset::GetParamValue
- AFXDAO/CDaoRecordset::GetPercentPosition
- AFXDAO/CDaoRecordset::GetRecordCount
- AFXDAO/CDaoRecordset::GetSQL
- AFXDAO/CDaoRecordset::GetType
- AFXDAO/CDaoRecordset::GetValidationRule
- AFXDAO/CDaoRecordset::GetValidationText
- AFXDAO/CDaoRecordset::IsBOF
- AFXDAO/CDaoRecordset::IsDeleted
- AFXDAO/CDaoRecordset::IsEOF
- AFXDAO/CDaoRecordset::IsFieldDirty
- AFXDAO/CDaoRecordset::IsFieldNull
- AFXDAO/CDaoRecordset::IsFieldNullable
- AFXDAO/CDaoRecordset::IsOpen
- AFXDAO/CDaoRecordset::Move
- AFXDAO/CDaoRecordset::MoveFirst
- AFXDAO/CDaoRecordset::MoveLast
- AFXDAO/CDaoRecordset::MoveNext
- AFXDAO/CDaoRecordset::MovePrev
- AFXDAO/CDaoRecordset::Open
- AFXDAO/CDaoRecordset::Requery
- AFXDAO/CDaoRecordset::Seek
- AFXDAO/CDaoRecordset::SetAbsolutePosition
- AFXDAO/CDaoRecordset::SetBookmark
- AFXDAO/CDaoRecordset::SetCacheSize
- AFXDAO/CDaoRecordset::SetCacheStart
- AFXDAO/CDaoRecordset::SetCurrentIndex
- AFXDAO/CDaoRecordset::SetFieldDirty
- AFXDAO/CDaoRecordset::SetFieldNull
- AFXDAO/CDaoRecordset::SetFieldValue
- AFXDAO/CDaoRecordset::SetFieldValueNull
- AFXDAO/CDaoRecordset::SetLockingMode
- AFXDAO/CDaoRecordset::SetParamValue
- AFXDAO/CDaoRecordset::SetParamValueNull
- AFXDAO/CDaoRecordset::SetPercentPosition
- AFXDAO/CDaoRecordset::Update
- AFXDAO/CDaoRecordset::m_bCheckCacheForDirtyFields
- AFXDAO/CDaoRecordset::m_nFields
- AFXDAO/CDaoRecordset::m_nParams
- AFXDAO/CDaoRecordset::m_pDAORecordset
- AFXDAO/CDaoRecordset::m_pDatabase
- AFXDAO/CDaoRecordset::m_strFilter
- AFXDAO/CDaoRecordset::m_strSort
helpviewer_keywords:
- CDaoRecordset [MFC], CDaoRecordset
- CDaoRecordset [MFC], AddNew
- CDaoRecordset [MFC], CanAppend
- CDaoRecordset [MFC], CanBookmark
- CDaoRecordset [MFC], CancelUpdate
- CDaoRecordset [MFC], CanRestart
- CDaoRecordset [MFC], CanScroll
- CDaoRecordset [MFC], CanTransact
- CDaoRecordset [MFC], CanUpdate
- CDaoRecordset [MFC], Close
- CDaoRecordset [MFC], Delete
- CDaoRecordset [MFC], DoFieldExchange
- CDaoRecordset [MFC], Edit
- CDaoRecordset [MFC], FillCache
- CDaoRecordset [MFC], Find
- CDaoRecordset [MFC], FindFirst
- CDaoRecordset [MFC], FindLast
- CDaoRecordset [MFC], FindNext
- CDaoRecordset [MFC], FindPrev
- CDaoRecordset [MFC], GetAbsolutePosition
- CDaoRecordset [MFC], GetBookmark
- CDaoRecordset [MFC], GetCacheSize
- CDaoRecordset [MFC], GetCacheStart
- CDaoRecordset [MFC], GetCurrentIndex
- CDaoRecordset [MFC], GetDateCreated
- CDaoRecordset [MFC], GetDateLastUpdated
- CDaoRecordset [MFC], GetDefaultDBName
- CDaoRecordset [MFC], GetDefaultSQL
- CDaoRecordset [MFC], GetEditMode
- CDaoRecordset [MFC], GetFieldCount
- CDaoRecordset [MFC], GetFieldInfo
- CDaoRecordset [MFC], GetFieldValue
- CDaoRecordset [MFC], GetIndexCount
- CDaoRecordset [MFC], GetIndexInfo
- CDaoRecordset [MFC], GetLastModifiedBookmark
- CDaoRecordset [MFC], GetLockingMode
- CDaoRecordset [MFC], GetName
- CDaoRecordset [MFC], GetParamValue
- CDaoRecordset [MFC], GetPercentPosition
- CDaoRecordset [MFC], GetRecordCount
- CDaoRecordset [MFC], GetSQL
- CDaoRecordset [MFC], GetType
- CDaoRecordset [MFC], GetValidationRule
- CDaoRecordset [MFC], GetValidationText
- CDaoRecordset [MFC], IsBOF
- CDaoRecordset [MFC], IsDeleted
- CDaoRecordset [MFC], IsEOF
- CDaoRecordset [MFC], IsFieldDirty
- CDaoRecordset [MFC], IsFieldNull
- CDaoRecordset [MFC], IsFieldNullable
- CDaoRecordset [MFC], IsOpen
- CDaoRecordset [MFC], Move
- CDaoRecordset [MFC], MoveFirst
- CDaoRecordset [MFC], MoveLast
- CDaoRecordset [MFC], MoveNext
- CDaoRecordset [MFC], MovePrev
- CDaoRecordset [MFC], Open
- CDaoRecordset [MFC], Requery
- CDaoRecordset [MFC], Seek
- CDaoRecordset [MFC], SetAbsolutePosition
- CDaoRecordset [MFC], SetBookmark
- CDaoRecordset [MFC], SetCacheSize
- CDaoRecordset [MFC], SetCacheStart
- CDaoRecordset [MFC], SetCurrentIndex
- CDaoRecordset [MFC], SetFieldDirty
- CDaoRecordset [MFC], SetFieldNull
- CDaoRecordset [MFC], SetFieldValue
- CDaoRecordset [MFC], SetFieldValueNull
- CDaoRecordset [MFC], SetLockingMode
- CDaoRecordset [MFC], SetParamValue
- CDaoRecordset [MFC], SetParamValueNull
- CDaoRecordset [MFC], SetPercentPosition
- CDaoRecordset [MFC], Update
- CDaoRecordset [MFC], m_bCheckCacheForDirtyFields
- CDaoRecordset [MFC], m_nFields
- CDaoRecordset [MFC], m_nParams
- CDaoRecordset [MFC], m_pDAORecordset
- CDaoRecordset [MFC], m_pDatabase
- CDaoRecordset [MFC], m_strFilter
- CDaoRecordset [MFC], m_strSort
ms.assetid: 2322067f-1027-4662-a5d7-aa2fc7488630
ms.openlocfilehash: 6a1475d1b0bc083cfd180ea5a211e752c973e2f8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754676"
---
# <a name="cdaorecordset-class"></a>CDaoRecordset 類別

表示選取自資料來源的資料錄集。

## <a name="syntax"></a>語法

```
class CDaoRecordset : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDao 記錄集::CDao 記錄集](#cdaorecordset)|建構 `CDaoRecordset` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDao 記錄集::新增新](#addnew)|準備添加新記錄。 調用[更新](#update)以完成添加。|
|[CDao 記錄集::可應用](#canappend)|如果可以通過[AddNew](#addnew)成員函數將新記錄添加到記錄集,則返回非零。|
|[CDao 記錄集::CanBookmark](#canbookmark)|如果記錄集支援書籤,則返回非零。|
|[CDao 記錄集::取消更新](#cancelupdate)|由於[編輯](#edit)或[添加新](#addnew)操作而取消任何掛起的更新。|
|[CDao 記錄集::可以重新啟動](#canrestart)|如果可以調用[Requery](#requery)再次運行記錄集的查詢,則返回非零。|
|[CDao 記錄集::CanScroll](#canscroll)|如果可以滾動瀏覽記錄,則返回非零。|
|[CDao 記錄集::可轉換](#cantransact)|如果數據源支援事務,則返回非零。|
|[CDao 記錄集::可以更新](#canupdate)|如果可以更新記錄集(可以添加、更新或刪除記錄),則返回非零。|
|[CDao 記錄集:關閉](#close)|關閉記錄集。|
|[CDao記錄集::Delete](#delete)|從記錄集中刪除當前記錄。 刪除後,必須顯式滾動到其他記錄。|
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|調用 以在記錄集的欄位數據成員和數據源上的相應記錄之間交換數據(雙向)。 實現 DAO 記錄欄位交換 (DFX)。|
|[CDaoRecordset:編輯](#edit)|準備對當前記錄的更改。 調用`Update`以完成編輯。|
|[CDao 記錄集::填充快取](#fillcache)|填滿包含來自 ODBC 資料來源資料的記錄集物件的全部或部分本地快取。|
|[CDao 記錄集:尋找](#find)|在動態集類型記錄集中查找特定字串的第一個、下一個、上一個或最後一個位置,該位置滿足指定的條件並使該記錄成為當前記錄。|
|[CDao 記錄集::尋找第一](#findfirst)|在動態集類型或快照類型記錄集中查找滿足指定條件並使該記錄成為當前記錄的第一個記錄。|
|[CDao 記錄集::尋找最後](#findlast)|在動態集類型或快照類型記錄集中查找滿足指定條件並使該記錄成為當前記錄的最後一條記錄。|
|[CDao 記錄集::尋找下一個](#findnext)|在動態集類型或快照類型記錄集中查找滿足指定條件並使該記錄成為當前記錄的下一個記錄。|
|[CDao記錄集::尋找Prev](#findprev)|在滿足指定條件並使該記錄成為當前記錄的動態集類型或快照類型記錄集中查找以前的記錄。|
|[CDao 記錄集:取得絕對位置](#getabsoluteposition)|返回記錄集物件的當前記錄的記錄編號。|
|[CDao 記錄集::取得書籤](#getbookmark)|返回表示記錄上的書籤的值。|
|[CDao 記錄集::取得快取大小](#getcachesize)|返回指定動態集類型記錄集中的記錄數的值,其中包含要從 ODBC 數據源本地緩存的數據。|
|[CDao 記錄集::取得快取開始](#getcachestart)|返回指定要緩存的記錄集中第一個記錄的書籤的值。|
|[CDao 記錄集::取得目前索引](#getcurrentindex)|傳`CString`回包含索引表`CDaoRecordset`型態 上最近使用的索引的名稱 。|
|[CDao 記錄集::取得日期建立](#getdatecreated)|傳回建立物件基礎的基表`CDaoRecordset`的日期和時間|
|[CDao 記錄集::取得更新日期](#getdatelastupdated)|返回對物件基礎表設計進行的最新更改的`CDaoRecordset`日期和時間。|
|[CDao 記錄集:取得預設 DB 名稱](#getdefaultdbname)|返回預設數據源的名稱。|
|[CDao 記錄集::取得預設SQL](#getdefaultsql)|呼叫以取得要執行的預設 SQL 字串。|
|[CDao 記錄集::取得編輯模式](#geteditmode)|返回指示當前記錄的編輯狀態的值。|
|[CDao記錄集::獲取菲爾德計數](#getfieldcount)|返回表示記錄集中的欄位數的值。|
|[CDaoRecordset:取得菲爾德資訊](#getfieldinfo)|返回有關記錄集中欄位的特定類型的資訊。|
|[CDao 記錄集:取得場值](#getfieldvalue)|返回記錄集中的欄位的值。|
|[CDao 記錄集:取得索引計數](#getindexcount)|檢索記錄集基礎表中的索引數。|
|[CDao 記錄集:取得索引資訊](#getindexinfo)|返回有關索引的各種資訊。|
|[CDao 記錄集::取得上次修改的書籤](#getlastmodifiedbookmark)|用於確定最近添加或更新的記錄。|
|[CDao 記錄集::取得鎖定模式](#getlockingmode)|返回指示編輯期間有效的鎖定類型的值。|
|[CDao 記錄集:取得名稱](#getname)|傳`CString`回紀錄集名稱的 。|
|[CDao 記錄集::取得帕拉姆價值](#getparamvalue)|檢索存儲在基礎 DAOParameter 物件中的指定參數的當前值。|
|[CDao 記錄集:取得百分比位置](#getpercentposition)|將當前記錄的位置作為記錄總數的百分比返回。|
|[CDao 記錄集::取得記錄計數](#getrecordcount)|返回在記錄集對象中訪問的記錄數。|
|[CDao 記錄集::取得SQL](#getsql)|取得用於選擇記錄集記錄的 SQL 字串。|
|[CDao 記錄集:取得類型](#gettype)|調用 以確定記錄集的類型:表類型、動態集類型或快照類型。|
|[CDao 記錄集::取得驗證規則](#getvalidationrule)|返回`CString`包含在輸入欄位中的數據時驗證數據的值。|
|[CDao 記錄集::取得認證文字](#getvalidationtext)|檢索不符合驗證規則時顯示的文本。|
|[CDao 記錄集:IsBOF](#isbof)|如果記錄集已定位在第一條記錄之前,則返回非零。 目前沒有記錄。|
|[CDao 記錄集:已刪除](#isdeleted)|如果記錄集位於已刪除的記錄上,則返回非零。|
|[CDao 記錄集::IsEOF](#iseof)|如果記錄集位於最後一條記錄之後,則返回非零。 目前沒有記錄。|
|[CDao 記錄集::IsfieldDirty](#isfielddirty)|如果當前記錄中的指定欄位已更改,則返回非零。|
|[CDao記錄集::IsfieldNull](#isfieldnull)|如果目前記錄中的指定欄位為 Null(沒有值),則傳回非零。|
|[CDao 記錄集::可欄位空](#isfieldnullable)|如果目前記錄中的指定欄位可以設置為 Null(沒有值),則傳回非零。|
|[CDao 記錄集::是開啟的](#isopen)|如果之前已調用[Open,](#open)則傳回非零。|
|[CDao 記錄集::移動](#move)|將記錄集定位為從當前記錄中的指定記錄數,以任一方向。|
|[CDao 記錄集::先移動](#movefirst)|將當前記錄定位到記錄集中的第一條記錄上。|
|[CDao 記錄集::移動上次](#movelast)|將當前記錄定位到記錄集中的最後一條記錄上。|
|[CDao 記錄集::移動下一個](#movenext)|將當前記錄定位到記錄集中的下一條記錄上。|
|[CDao記錄集::MovePrev](#moveprev)|在記錄集中的上一條記錄上定位當前記錄。|
|[CDao 記錄集::開啟](#open)|從表、動態集或快照創建新的記錄集。|
|[CDao 記錄集::重新查詢](#requery)|再次運行記錄集的查詢以刷新所選記錄。|
|[CDao 記錄集::尋找](#seek)|在索引的表類型記錄集物件中查找記錄,該物件滿足當前索引的指定條件,並使該記錄成為當前記錄。|
|[CDao 記錄集::設定絕對位置](#setabsoluteposition)|設置記錄集物件的當前記錄的記錄編號。|
|[CDao 記錄集::設定書籤](#setbookmark)|將記錄集放在包含指定書籤的記錄上。|
|[CDao 記錄集::設定快取大小](#setcachesize)|設置一個值,指定動態集類型記錄集中的記錄數,其中包含要從 ODBC 數據來源本地緩存的資料。|
|[CDao 記錄集::設定快取開始](#setcachestart)|設置指定要緩存的記錄集中第一個記錄的書籤的值。|
|[CDao 記錄集::設定目前索引](#setcurrentindex)|調用 以在表類型記錄集上設置索引。|
|[CDao 記錄集::設定欄位臟](#setfielddirty)|將目前記錄中的指定欄位標記為已更改。|
|[CDao 記錄集::SetFieldNull](#setfieldnull)|將目前記錄中指定欄位的值設定為 Null(沒有值)。|
|[CDao 記錄集::設定場值](#setfieldvalue)|在記錄集中設置欄位的值。|
|[CDao 記錄集:設定場值 Null](#setfieldvaluenull)|將記錄集中的欄位的值設定為 Null。 (沒有值)。|
|[CDao 記錄集::設定鎖定模式](#setlockingmode)|設置指示在編輯期間生效的鎖定類型的值。|
|[CDao 記錄集::SetParamValue](#setparamvalue)|設定儲存在基礎 DAO 參數物件的參數的目前值|
|[CDao 記錄集::SetParamValueNull](#setparamvaluenull)|將指定參數的當前值設定為 Null(沒有值)。|
|[CDao 記錄集::設定百分比位置](#setpercentposition)|將當前記錄的位置設置為對應於記錄集中記錄總數百分比的位置。|
|[CDao 記錄集::更新](#update)|通過在數據源上`AddNew``Edit`保存 新的或編輯的數據來完成 或操作。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDaoRecordset:m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|包含一個標誌,指示欄位是否自動標記為已更改。|
|[CDao 記錄集::m_nFields](#m_nfields)|包含記錄集類中的欄位數據成員數以及記錄組從資料源中選擇的欄數。|
|[CDao 記錄集::m_nParams](#m_nparams)|包含紀錄集類別中的參數資料成員數 ─ 使用紀錄集查詢傳遞的參數數|
|[CDao 記錄集::m_pDAORecordset](#m_pdaorecordset)|指向記錄集物件基礎的 DAO 介面的指標。|
|[CDao 記錄集::m_pDatabase](#m_pdatabase)|此結果集的源資料庫。 包含指向[CDao 資料庫](../../mfc/reference/cdaodatabase-class.md)物件的指標。|
|[CDao 記錄集::m_strFilter](#m_strfilter)|包含用於構造 SQL **WHERE**語句的字串。|
|[CDao 記錄集::m_strSort](#m_strsort)|包含用於建構 SQL **ORDER BY**語句的字串。|

## <a name="remarks"></a>備註

物件稱為「記錄集」,`CDaoRecordset`有以下三種形式可供選擇:

- 表類型記錄集表示一個基本表,可用於檢查、添加、更改或刪除單個資料庫表中的記錄。

- 動態集類型的記錄集是具有可更新記錄的查詢的結果。 這些記錄集是一組記錄,可用於檢查、添加、更改或刪除基礎資料庫表或表中的記錄。 Dynaset 類型記錄集可以包含資料庫中一個或多個表中的欄位。

- 快照類型記錄集是一組記錄的靜態副本,可用於查找數據或生成報表。 這些記錄集可以包含資料庫中一個或多個表的欄位,但不能更新。

記錄集的每種形式表示在打開記錄集時修復的一組記錄。 當您滾動到表類型記錄集中的記錄集或動態集類型記錄集中的記錄時,它反映在打開記錄集后對記錄所做的更改,由其他使用者或應用程式中的其他記錄集進行。 (無法更新快照類型的記錄集。可以直接使用`CDaoRecordset`或派生`CDaoRecordset`應用程式 特定的記錄集類。 您可以：

- 滾動記錄。

- 設置索引並使用[Seek](#seek)快速查找記錄(僅限表類型記錄集)。

- 根據字串比較查找記錄:「<」、"\""""*"、">"\<或">"(動態集類型和快照類型記錄集)。

- 更新記錄並指定鎖定模式(快照類型記錄集除外)。

- 篩選記錄集以約束它從數據源上可用的記錄中選擇哪些記錄。

- 對記錄集進行排序。

- 參數化記錄集,以自定義其選擇與在運行時之前不知道的資訊。

類`CDaoRecordset`提供類似於`CRecordset`類的介面。 主要區別是類`CDaoRecordset`通過基於 OLE 的數據訪問物件 (DAO) 訪問數據。 類`CRecordset`通過開放資料庫連接 (ODBC) 和該 DBMS 的 ODBC 驅動程式存取 DBMS。

> [!NOTE]
> DAO 資料庫類不同於基於開放資料庫連接 (ODBC) 的 MFC 資料庫類。 所有 DAO 資料庫類名稱都有「CDao」首碼。 您仍可以使用 DAO 類訪問 ODBC 資料來源;DAO 類通常提供卓越的功能,因為它們特定於 Microsoft Jet 資料庫引擎。

可以直接使用`CDaoRecordset`或派生類`CDaoRecordset`。 要在任一情況下使用記錄集類,請打開資料庫並構造記錄集物件,將構造函數傳遞給對象`CDaoDatabase`的指標。 您還可以建構物件`CDaoRecordset`,並讓 MFC 為`CDaoDatabase`您創建臨時 物件。 然後調用記錄集的[Open](#open)成員函數,指定對像是表類型的記錄集、動態集類型的記錄集還是快照類型的記錄集。 調用`Open`從資料庫中選擇數據並檢索第一條記錄。

使用物件的成員函數和數據成員滾動瀏覽記錄並對其進行操作。 可用的操作取決於物件是表類型記錄集、動態集類型記錄集還是快照類型記錄集,以及它是可更新還是只讀 - 這取決於資料庫或開放資料庫連接 (ODBC) 資料源的功能。 要刷新自`Open`調用以來可能已更改或添加的記錄,請調用物件的[重新查詢](#requery)成員函數。 調用物件的`Close`成員函數,並在物件完成時銷毀該函數。

`CDaoRecordset`使用 DAO 記錄欄位交換 (DFX) 支援透過類型安全`CDaoRecordset``CDaoRecordset`C++派生 類的成員讀取和更新記錄欄位。 您還可以使用[GetFieldValue](#getfieldvalue)和[SetFieldValue](#setfieldvalue)在資料庫中實現列的動態綁定,而無需使用 DFX 機制。

有關相關信息,請參閱 DAO 説明中的主題"記錄集物件"。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="cdaorecordsetaddnew"></a><a name="addnew"></a>CDao 記錄集::新增新

調用此成員函數以向表類型或動態集類型記錄集添加新記錄。

```
virtual void AddNew();
```

### <a name="remarks"></a>備註

記錄的欄位最初為空。 (在資料庫術語中,Null 表示"沒有值",並且與 C++ 中的 NULL 不同。要完成該操作,必須調用[Update](#update)成員函數。 `Update`將更改保存到數據源。

> [!CAUTION]
> 如果編輯記錄,然後滾動到另一條記錄而不調用`Update`,則更改將丟失,而不會發出警告。

如果通過調用[AddNew](#addnew)將記錄添加到動態集類型的記錄集中,則該記錄在記錄集中可見,並包含在基礎表中,其中`CDaoRecordset`任何新 物件都可以看到該記錄。

新紀錄的位置取決於紀錄集的類型:

- 在動態集類型的記錄集中,不保證插入新記錄的位置。 由於性能和併發性的原因,Microsoft Jet 3.0 會更改此行為。 如果目標是使新添加的記錄成為當前記錄,請取得上次修改記錄的書籤並移動到該書籤:

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- 在已為其指定索引的表類型記錄集中,記錄按排序順序以適當的位置返回。 如果未指定索引,則在記錄集的末尾返回新記錄。

使用`AddNew`前當前的記錄仍為當前記錄。 如果要使新記錄為當前,並且記錄集支援書籤,請將[SetBookmark](#setbookmark)調用基礎 DAO 記錄集物件的"上次修改"屬性設置標識的書籤。 這樣做對於確定添加記錄中計數器(自動增量)欄位的值非常有用。 有關詳細資訊,請參閱[獲取已修改的書籤](#getlastmodifiedbookmark)。

如果資料庫支援事務,則可以使`AddNew`調用成為事務的一部分。 有關事務的詳細資訊,請參閱類[CDao 工作區](../../mfc/reference/cdaoworkspace-class.md)。 請注意,在呼叫`AddNew`之前,應呼叫[CDao 工作區::開始轉換](../../mfc/reference/cdaoworkspace-class.md#begintrans)。

呼叫`AddNew`未呼叫其[Open](#open)成員函數的記錄集是非法的。 如果`CDaoException`呼`AddNew`叫 無法附加的紀錄集,則引發 。 您可以通過調用[CanAppend](#canappend)來確定記錄集是否可以更新。

框架標記已更改的欄位數據成員,以確保 DAO 記錄欄位交換 (DFX) 機制將它們寫入數據來源上的記錄。 變更欄位的值通常會自動將欄位設定為髒,因此您很少需要自己調用[SetFieldDirty,](#setfielddirty)但有時您可能希望確保無論欄位資料成員中的哪個值如何,都會顯式更新或插入列。 DFX 機制並使用**PSEUDO NULL**。 有關詳細資訊,請參閱[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用雙緩衝機制,則更改欄位的值不會自動將欄位設置為髒。 在這種情況下,必須顯式將欄位設置為髒。 [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的標誌控制此自動欄位檢查。

> [!NOTE]
> 如果記錄是雙緩衝的(即啟用了自動欄位檢查),則調用`CancelUpdate`將成員變數還原到以前`AddNew``Edit`或 已調用的值。

有關相關信息,請參閱 DAO 説明中的"添加新方法"、"取消更新方法"、"上次修改屬性"和"編輯模式屬性"的主題。

## <a name="cdaorecordsetcanappend"></a><a name="canappend"></a>CDao 記錄集::可應用

呼叫此成員函數以確定以前打開的記錄集是否允許您透過調用[AddNew](#addnew)成員函數添加新記錄。

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>傳回值

如果記錄集允許添加新記錄,則非零;否則 0。 `CanAppend`如果以唯讀身份打開記錄集,則返回 0。

### <a name="remarks"></a>備註

有關相關信息,請參閱 DAO 説明中的主題"附加方法"。

## <a name="cdaorecordsetcanbookmark"></a><a name="canbookmark"></a>CDao 記錄集::CanBookmark

呼叫此成員函數以確定以前打開的記錄集是否允許您使用書籤單獨標記記錄。

```
BOOL CanBookmark();
```

### <a name="return-value"></a>傳回值

如果記錄集支援書籤,則非零,否則為 0。

### <a name="remarks"></a>備註

如果完全基於 Microsoft Jet 資料庫引擎表使用記錄集,則可以使用書籤,但標記為僅轉發滾動記錄集的快照類型記錄組除外。 其他資料庫產品(外部ODBC資料來源)可能不支援書籤。

有關相關信息,請參閱 DAO 説明中的主題"可書籤屬性」。。

## <a name="cdaorecordsetcancelupdate"></a><a name="cancelupdate"></a>CDao 記錄集::取消更新

成員`CancelUpdate`函數將由於[編輯](#edit)或[AddNew](#addnew)操作而取消任何掛起的更新。

```
virtual void CancelUpdate();
```

### <a name="remarks"></a>備註

例如,如果應用程式調用`Edit``AddNew`或成員函數,但未調用[Update](#update) `CancelUpdate` ,則取消在`Edit``AddNew`調用或調用後所做的任何更改。

> [!NOTE]
> 如果記錄是雙緩衝的(即啟用了自動欄位檢查),則調用`CancelUpdate`將成員變數還原到以前`AddNew``Edit`或 已調用的值。

如果沒有`Edit`或`AddNew`操作掛起,`CancelUpdate`則會導致 MFC 引發異常。 調用[GetEditMode](#geteditmode)成員函數以確定是否存在可取消的掛起操作。

有關相關信息,請參閱 DAO 説明中的主題"取消更新方法」。。

## <a name="cdaorecordsetcanrestart"></a><a name="canrestart"></a>CDao 記錄集::可以重新啟動

調用此成員函數以確定記錄集是否允許通過調用`Requery`成員函數重新啟動其查詢(刷新其記錄)。

```
BOOL CanRestart();
```

### <a name="return-value"></a>傳回值

如果`Requery`可以調用非零,以便再次運行記錄集的查詢,否則為 0。

### <a name="remarks"></a>備註

表型態的紀錄集不`Requery`支援 。

如果`Requery`不受支援,則呼叫[「關閉](#close)」然後[打開](#open)以刷新資料。 在參數值`Requery`更改後,可以調用更新記錄集物件的基礎參數查詢。

有關相關信息,請參閱 DAO 説明中的主題"可重新啟動屬性」。

## <a name="cdaorecordsetcanscroll"></a><a name="canscroll"></a>CDao 記錄集::CanScroll

調用此成員函數以確定記錄集是否允許滾動。

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>傳回值

如果可以滾動瀏覽記錄,則為非零,否則為 0。

### <a name="remarks"></a>備註

如果使用 調用[「打開](#open)」,`dbForwardOnly`則記錄集只能向前滾動。

有關相關信息,請參閱 DAO 説明中的主題"使用 DAO 定位當前記錄指標"

## <a name="cdaorecordsetcantransact"></a><a name="cantransact"></a>CDao 記錄集::可轉換

調用此成員函數以確定記錄集是否允許事務。

```
BOOL CanTransact();
```

### <a name="return-value"></a>傳回值

如果基礎數據源支援事務,則非零,否則為 0。

### <a name="remarks"></a>備註

有關相關信息,請參閱 DAO 説明中的"交易屬性"主題。

## <a name="cdaorecordsetcanupdate"></a><a name="canupdate"></a>CDao 記錄集::可以更新

調用此成員函數以確定是否可以更新記錄集。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>傳回值

如果可以更新記錄集(添加、更新和刪除記錄),則非零,否則為 0。

### <a name="remarks"></a>備註

如果基礎資料來源是唯讀的,或者在調用記錄集[的 Open](#open)時為*nOptions*指定`dbReadOnly`,則記錄集可能是唯讀的。

有關相關信息,請參閱 DAO 説明中的"添加新方法"、"編輯方法"、"刪除方法"、"更新方法"和"可更新屬性"的主題。

## <a name="cdaorecordsetcdaorecordset"></a><a name="cdaorecordset"></a>CDao 記錄集::CDao 記錄集

建構 `CDaoRecordset` 物件。

```
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>參數

*p 資料庫*<br/>
包含指向[CDao 資料庫](../../mfc/reference/cdaodatabase-class.md)物件的指標或值 NULL。 如果不是 NULL,`CDaoDatabase`並且尚未呼叫`Open`物件的成員函數將其連接到資料源,則記錄集將嘗試在它自己的[Open](#open)呼叫期間為您打開它。 如果傳遞 NULL,`CDaoDatabase`則使用指定的數據源資訊(如果派生自`CDaoRecordset`的記錄集類)為建構和連接物件。

### <a name="remarks"></a>備註

可以直接使用`CDaoRecordset`或派生`CDaoRecordset`應用程式 特定的類。 您可以使用 ClassWizard 派生記錄集類。

> [!NOTE]
> 如果派生類`CDaoRecordset`,派生類必須提供其自己的構造函數。 在派生類的構造函數中,調用構造函數`CDaoRecordset::CDaoRecordset`,將適當的參數傳遞給它。

將 NULL 傳遞給記錄集建構函數`CDaoDatabase`,以便自動建構和連接物件。 這是一個有用的快捷方式,不需要在構造記錄集之前構造和連接`CDaoDatabase`物件。 如果`CDaoDatabase`物件未打開,也將為您創建一個使用預設工作區的[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件。 有關詳細資訊,請參閱[CDao 資料庫:cDao 資料庫](../../mfc/reference/cdaodatabase-class.md#cdaodatabase)。

## <a name="cdaorecordsetclose"></a><a name="close"></a>CDao 記錄集:關閉

關閉`CDaoRecordset`物件會將其從關聯資料庫中的打開記錄集的集合中刪除。

```
virtual void Close();
```

### <a name="remarks"></a>備註

因為`Close`不會破壞`CDaoRecordset`物件,因此可以通過`Open`調用 同一數據源或其他數據源來重用該物件。

所有掛起的[AddNew](#addnew)或[Edit](#edit)語句都將取消,並且所有掛起的事務都將回滾。 如果要保留掛起的添加或編輯,請先呼叫[「更新」,](#update)然後再`Close`呼叫 每個記錄集。

通話後可以`Open`再次呼叫`Close`。 這允許您重用記錄集物件。 如果可能,更好的選擇是呼叫[重新查詢](#requery)。

有關相關信息,請參閱 DAO 説明中的主題" 關閉方法"

## <a name="cdaorecordsetdelete"></a><a name="delete"></a>CDao記錄集::Delete

呼叫此成員函數以刪除打開動態集類型或表類型記錄集物件中的當前記錄。

```
virtual void Delete();
```

### <a name="remarks"></a>備註

成功刪除後,記錄集的欄位資料成員將設置為 Null 值,您必須顯式調用記錄集導航成員函數之一([移動](#move)、[查找](#seek)[、SetBookmark](#setbookmark)等),才能移出已刪除的記錄。 從記錄集中刪除記錄時,在調用`Delete`和之前,記錄集中必須存在當前記錄。否則,MFC會引發異常。

`Delete`刪除目前記錄並使其無法訪問。 儘管您無法編輯或使用已刪除的記錄,但它仍然是最新的。 但是,移動到其他記錄后,無法使已刪除的記錄再次成為當前記錄。

> [!CAUTION]
> 記錄集必須是可向上的,並且在調用`Delete`時記錄集中必須有有效的記錄電流。 例如,如果刪除記錄,但在再次呼叫`Delete`之前不捲動到新記錄,`Delete`則引發[CDaoException](../../mfc/reference/cdaoexception-class.md)。

如果使用事務並調用[CDao 工作區::回滾](../../mfc/reference/cdaoworkspace-class.md#rollback)成員函數,則可以取消刪除記錄。 如果基表是級聯刪除關係中的主錶,則刪除當前記錄還可以刪除外表中的一個或多個記錄。 有關詳細資訊,請參閱 DAO 説明中的定義「級聯刪除」。

與`AddNew``Edit`與不同`Delete`,呼叫後不呼叫`Update`。

有關相關信息,請參閱 DAO 説明中的"添加新方法"、"編輯方法"、"刪除方法"、"更新方法"和"可更新屬性"的主題。

## <a name="cdaorecordsetdofieldexchange"></a><a name="dofieldexchange"></a>CDao記錄集::DoFieldExchange

框架調用此成員函數以在記錄集物件的欄位數據成員和數據源上的當前記錄的相應列之間自動交換數據。

```
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>參數

*pFX*<br/>
包含指向`CDaoFieldExchange`物件的指標。 框架已經設置了此物件,以指定欄位交換操作的上下文。

### <a name="remarks"></a>備註

它還將參數數據成員(如果有)綁定到 SQL 語句字串中的參數占位符,以便記錄集的選擇。 欄位資料交換(稱為 DAO 記錄欄位交換 (DFX) 在兩個方向上工作:從記錄集物件的欄位數據成員到數據源上記錄的欄位,以及從數據源上的記錄到記錄集物件。 如果動態繫結列,則不需要實現`DoFieldExchange`。

`DoFieldExchange`對於派生的記錄集類,通常需要執行的唯一操作是使用 ClassWizard 創建類並指定欄位數據成員的名稱和數據類型。 您還可以向 ClassWizard 編寫的代碼添加代碼以指定參數數據成員。 如果要動態綁定所有欄位,除非指定參數資料成員,否則此函數將處於非活動狀態。

當您使用 ClassWizard 宣告的紀錄集類別時,精靈`DoFieldExchange`會為您編寫一個重寫,類似於以下範例:

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

## <a name="cdaorecordsetedit"></a><a name="edit"></a>CDaoRecordset:編輯

呼叫此成員函數以允許更改當前記錄。

```
virtual void Edit();
```

### <a name="remarks"></a>備註

調用`Edit`成員函數後,對當前記錄的欄位所做的更改將複製到複製緩衝區。 對記錄進行所需的更改後,調用`Update`以保存更改。 `Edit`保存記錄集的數據成員的值。 如果調用`Edit`,進行更改,然後再次調`Edit`用 ,記錄的值將還原到第`Edit`一次 調用之前的值。

> [!CAUTION]
> 如果編輯記錄,然後執行任何移動到另一個記錄而不首先調用`Update`的操作,則更改將丟失,而不會發出警告。 此外,如果關閉記錄集或父資料庫,則已編輯的記錄將被丟棄,而不會發出警告。

在某些情況下,您可能希望透過使列為 Null(不包含任何資料)來更新列。 為此,使用`SetFieldNull`TRUE 參數呼叫以標記欄位 Null;這還會導致更新列。 如果希望將欄位寫入資料來源,即使其值未更改,則使用 TRUE 參數`SetFieldDirty`呼叫 。 即使欄位的值為 Null,這也能起作用。

框架標記已更改的欄位數據成員,以確保 DAO 記錄欄位交換 (DFX) 機制將它們寫入數據來源上的記錄。 變更欄位的值通常會自動將欄位設定為髒,因此您很少需要自己調用[SetFieldDirty,](#setfielddirty)但有時您可能希望確保無論欄位資料成員中的哪個值如何,都會顯式更新或插入列。 DFX 機制並使用**PSEUDO NULL**。 有關詳細資訊,請參閱[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用雙緩衝機制,則更改欄位的值不會自動將欄位設置為髒。 在這種情況下,必須顯式將欄位設置為髒。 [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的標誌控制此自動欄位檢查。

當記錄集物件在多用戶環境中被悲觀鎖定時,記錄從使用到`Edit`更新完成時一直鎖定。 如果記錄集被樂觀地鎖定,則記錄將鎖定,並在資料庫中更新之前與預編輯的記錄進行比較。 如果記錄自調用`Edit`後已更改,`Update`則 操作將失敗,並且 MFC 會引發異常。 您可以使用 變更鎖定`SetLockingMode`模式 。

> [!NOTE]
> 樂觀鎖定始終用於外部資料庫格式,如 ODBC 和可安裝 ISAM。

調用`Edit`後,當前記錄保持最新。 要調用`Edit`,必須有當前記錄。 如果沒有當前記錄,或者記錄集不引用打開的表類型或動態集類型的記錄集物件,則會發生異常。 呼叫`Edit`會導致`CDaoException`在以下條件下引發 a:

- 目前沒有記錄。

- 資料庫或記錄集是唯讀的。

- 記錄中沒有欄位是可向上的。

- 資料庫或記錄集已打開,供其他用戶獨佔使用。

- 其他使用者已鎖定包含您的記錄的頁面。

如果數據源支援事務,則可以使`Edit`調用成為事務的一部分。 請注意,應在調用`CDaoWorkspace::BeginTrans``Edit`之前和打開記錄集之後進行調用。 另請注意,呼叫`CDaoWorkspace::CommitTrans`不能替代呼`Update`叫 來`Edit`完成操作 。 有關事務的詳細資訊,請參閱類`CDaoWorkspace`。

有關相關信息,請參閱 DAO 説明中的"添加新方法"、"編輯方法"、"刪除方法"、"更新方法"和"可更新屬性"的主題。

## <a name="cdaorecordsetfillcache"></a><a name="fillcache"></a>CDao 記錄集::填充快取

調用此成員函數以緩存記錄集中的指定數量的記錄。

```cpp
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>參數

*pSize*<br/>
指定要填充緩存的行數。 如果省略此參數,該值由基礎 DAO 物件的 CacheSize 屬性設置確定。

*pBookmark*<br/>
指定書籤的[COleVariant。](../../mfc/reference/colevariant-class.md) 緩存從此書籤指示的記錄開始填充。 如果省略此參數,則緩存將從基礎 DAO 物件的 CacheStart 屬性指示的記錄開始填充。

### <a name="remarks"></a>備註

快取提高了從遠端伺服器檢索或獲取數據的應用程式的性能。 快取是本地記憶體中的空間,它保存最近從伺服器獲取的數據,前提是在應用程式運行時可能會再次請求數據。 請求數據時,Microsoft Jet 資料庫引擎會首先檢查緩存的數據,而不是從伺服器獲取數據,這需要更多的時間。 在非 ODBC 數據來源使用數據快取不起作用,因為資料不會儲存在快取中。

您可以隨時透過調用`FillCache`成員函數來顯式填充緩存,而不是等待緩存在獲取記錄時填充這些記錄。 這是一種加快填充緩存的方法,因為`FillCache`一次獲取多個記錄,而不是一次獲取一條記錄。 例如,在顯示每個記錄螢幕時,您可以讓應用程式呼叫`FillCache`來獲取下一個記錄螢幕。

使用記錄集對象存取的任何ODBC資料庫都可以具有本地快取。 要建立緩存,請從遠端資料源打開記錄集物件,然後調用記錄集`SetCacheSize`的`SetCacheStart`和成員函數。 如果*lSize*和*lBookmark*創建的範圍部分或全部`SetCacheSize`超出`SetCacheStart`和 指定的範圍 ,則忽略此範圍之外的記錄集部分,並且不會載入到緩存中。 如果`FillCache`請求的記錄多於保留在遠程數據源中的記錄,則僅提取其餘記錄,並且不會引發異常。

從快取取得的記錄不會反映其他使用者同時對源資料所做的更改。

`FillCache`僅獲取尚未緩存的記錄。 要強制更新所有快取的資料,請呼叫具有等於`SetCacheSize`0*的 lSize*參數的成員函`SetCacheSize`數,再次呼叫*lSize*參數等於您最初請求的快`FillCache`取的大小,然後呼叫 。

有關相關信息,請參閱 DAO 説明中的主題"FillCache 方法"。

## <a name="cdaorecordsetfind"></a><a name="find"></a>CDao 記錄集:尋找

呼叫此成員函數,使用比較運算符在動態集或快照類型記錄集中查找特定字串。

```
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*L 尋找類型*<br/>
指示所需查找操作類型的值。 可能的值包括：

- AFX_DAO_NEXT查找匹配字串的下一個位置。

- AFX_DAO_PREV查找匹配字串的上一個位置。

- AFX_DAO_FIRST 查找匹配字串的第一個位置。

- AFX_DAO_LAST 查找匹配字串的最後一個位置。

*lpszFilter*<br/>
用於查找記錄的字串表達式(如 SQL 語句中的**WHERE**子句,沒有單詞**WHERE)。** 例如：

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>傳回值

如果找到匹配的記錄,則非零,否則為 0。

### <a name="remarks"></a>備註

您可以找到字串的第一個、下一個、上一個或最後一個實例。 `Find`是一個虛擬函數,因此您可以重寫它並添加您自己的實現。 `FindFirst` `FindLast` `FindNext` 、和 成員函數調用成員函數,因此可以使用`Find`來控制 所有 Find 操作的行為。 `FindPrev` `Find`

要在表類型記錄集中查找記錄,請調用[Seek](#seek)成員函數。

> [!TIP]
> 記錄集越小,效果就越大`Find`。 通常,尤其是使用 ODBC 數據時,最好創建一個新查詢,僅檢索所需的記錄。

有關相關信息,請參閱 DAO 説明中的主題"查找第一、查找最後、查找下一個、查找以前的方法」。。

## <a name="cdaorecordsetfindfirst"></a><a name="findfirst"></a>CDao 記錄集::尋找第一

調用此成員函數以查找與指定條件匹配的第一個記錄。

```
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*lpszFilter*<br/>
用於查找記錄的字串表達式(如 SQL 語句中的**WHERE**子句,沒有單詞**WHERE)。**

### <a name="return-value"></a>傳回值

如果找到匹配的記錄,則非零,否則為 0。

### <a name="remarks"></a>備註

`FindFirst`成員函數從記錄集的開頭開始搜索,然後搜索到記錄集的末尾。

如果要在搜索中包括所有記錄(而不僅僅是滿足特定條件的記錄),請使用 Move 操作之一從記錄移動到記錄。 要在表類型記錄集中查找記錄,請調用`Seek`成員函數。

如果未找到與條件匹配的記錄,則當前記錄指標未確定,並`FindFirst`返回零。 如果記錄集包含滿足條件的多個記錄,則`FindFirst`查找第一個匹配項`FindNext`, 找到下一個匹配項,等等。

> [!CAUTION]
> 如果編輯當前記錄,請確保在移動到其他記錄之前通過調用`Update`成員函數來保存更改。 如果不更新而移動到其他記錄,則更改將丟失,而不會發出警告。

成員`Find`函數從下表中指定的位置和方向進行搜尋:

|尋找操作|Begin|搜尋方向|
|---------------------|-----------|----------------------|
|`FindFirst`|記錄集開始|記錄集結束|
|`FindLast`|記錄集結束|記錄集開始|
|`FindNext`|目前記錄|記錄集結束|
|`FindPrevious`|目前記錄|記錄集開始|

> [!NOTE]
> 呼叫`FindLast`時,如果尚未完成搜索,則Microsoft Jet資料庫引擎在開始搜索之前將完全填充記錄集。 第一次搜索可能需要比後續搜索更長的時間。

使用 Find 操作之一與`MoveFirst``MoveNext`調用 或 不同,它只是使第一個或下一個記錄保持最新而不指定條件。 您可以使用「移動」操作執行「尋找」操作。

使用 Find 動作時,請記住以下事項:

- 如果`Find`返回非零,則不定義當前記錄。 在這種情況下,必須將當前記錄指標定位回有效記錄。

- 不能將「查找」操作與僅轉發滾動快照類型記錄集一起使用。

- 搜索包含日期的欄位時,即使您未使用 Microsoft Jet 資料庫引擎的美國版本,也應使用美國日期格式(月日年)。否則,可能無法找到匹配的記錄。

- 使用 ODBC 資料庫和大型動態集時,您可能會發現使用 Find 操作很慢,尤其是在使用大型記錄集時。 通過將 SQL 查詢與自訂**ORDERBY**或**WHERE**`CDaoQuerydef`子句、參數查詢或 檢索特定索引記錄的物件使用 SQL 查詢來提高性能。

有關相關信息,請參閱 DAO 説明中的主題"查找第一、查找最後、查找下一個、查找以前的方法」。。

## <a name="cdaorecordsetfindlast"></a><a name="findlast"></a>CDao 記錄集::尋找最後

調用此成員函數以查找與指定條件匹配的最後一條記錄。

```
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*lpszFilter*<br/>
用於查找記錄的字串表達式(如 SQL 語句中的**WHERE**子句,沒有單詞**WHERE)。**

### <a name="return-value"></a>傳回值

如果找到匹配的記錄,則非零,否則為 0。

### <a name="remarks"></a>備註

`FindLast`成員函數在記錄集的末尾開始搜索,然後向後搜索到記錄集的開頭。

如果要在搜索中包括所有記錄(而不僅僅是滿足特定條件的記錄),請使用 Move 操作之一從記錄移動到記錄。 要在表類型記錄集中查找記錄,請調用`Seek`成員函數。

如果未找到與條件匹配的記錄,則當前記錄指標未確定,並`FindLast`返回零。 如果記錄集包含滿足條件的多個記錄,則`FindFirst`查找第一個匹配項,`FindNext`查找第一次匹配項之後的下一個匹配項,等等。

> [!CAUTION]
> 如果編輯當前記錄,請確保在移動到其他記錄之前通過調用`Update`成員函數來保存更改。 如果不更新而移動到其他記錄,則更改將丟失,而不會發出警告。

使用 Find 操作之一與`MoveFirst``MoveNext`調用 或 不同,它只是使第一個或下一個記錄保持最新而不指定條件。 您可以使用「移動」操作執行「尋找」操作。

使用 Find 動作時,請記住以下事項:

- 如果`Find`返回非零,則不定義當前記錄。 在這種情況下,必須將當前記錄指標定位回有效記錄。

- 不能將「查找」操作與僅轉發滾動快照類型記錄集一起使用。

- 搜索包含日期的欄位時,即使您未使用 Microsoft Jet 資料庫引擎的美國版本,也應使用美國日期格式(月日年)。否則,可能無法找到匹配的記錄。

- 使用 ODBC 資料庫和大型動態集時,您可能會發現使用 Find 操作很慢,尤其是在使用大型記錄集時。 通過將 SQL 查詢與自訂**ORDERBY**或**WHERE**`CDaoQuerydef`子句、參數查詢或 檢索特定索引記錄的物件使用 SQL 查詢來提高性能。

有關相關信息,請參閱 DAO 説明中的主題"查找第一、查找最後、查找下一個、查找以前的方法」。。

## <a name="cdaorecordsetfindnext"></a><a name="findnext"></a>CDao 記錄集::尋找下一個

調用此成員函數以查找與指定條件匹配的下一個記錄。

```
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*lpszFilter*<br/>
用於查找記錄的字串表達式(如 SQL 語句中的**WHERE**子句,沒有單詞**WHERE)。**

### <a name="return-value"></a>傳回值

如果找到匹配的記錄,則非零,否則為 0。

### <a name="remarks"></a>備註

成員`FindNext`函數在當前記錄處開始搜索,然後搜索到記錄集的末尾。

如果要在搜索中包括所有記錄(而不僅僅是滿足特定條件的記錄),請使用 Move 操作之一從記錄移動到記錄。 要在表類型記錄集中查找記錄,請調用`Seek`成員函數。

如果未找到與條件匹配的記錄,則當前記錄指標未確定,並`FindNext`返回零。 如果記錄集包含滿足條件的多個記錄,則`FindFirst`查找第一個匹配項`FindNext`, 找到下一個匹配項,等等。

> [!CAUTION]
> 如果編輯當前記錄,請確保在移動到其他記錄之前通過調用`Update`成員函數來保存更改。 如果不更新而移動到其他記錄,則更改將丟失,而不會發出警告。

使用 Find 操作之一與`MoveFirst``MoveNext`調用 或 不同,它只是使第一個或下一個記錄保持最新而不指定條件。 您可以使用「移動」操作執行「尋找」操作。

使用 Find 動作時,請記住以下事項:

- 如果`Find`返回非零,則不定義當前記錄。 在這種情況下,必須將當前記錄指標定位回有效記錄。

- 不能將「查找」操作與僅轉發滾動快照類型記錄集一起使用。

- 搜索包含日期的欄位時,即使您未使用 Microsoft Jet 資料庫引擎的美國版本,也應使用美國日期格式(月日年)。否則,可能無法找到匹配的記錄。

- 使用 ODBC 資料庫和大型動態集時,您可能會發現使用 Find 操作很慢,尤其是在使用大型記錄集時。 通過將 SQL 查詢與自訂**ORDERBY**或**WHERE**`CDaoQuerydef`子句、參數查詢或 檢索特定索引記錄的物件使用 SQL 查詢來提高性能。

有關相關信息,請參閱 DAO 説明中的主題"查找第一、查找最後、查找下一個、查找以前的方法」。。

## <a name="cdaorecordsetfindprev"></a><a name="findprev"></a>CDao記錄集::尋找Prev

調用此成員函數以查找與指定條件匹配的上一條記錄。

```
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*lpszFilter*<br/>
用於查找記錄的字串表達式(如 SQL 語句中的**WHERE**子句,沒有單詞**WHERE)。**

### <a name="return-value"></a>傳回值

如果找到匹配的記錄,則非零,否則為 0。

### <a name="remarks"></a>備註

`FindPrev`成員函數在當前記錄處開始搜索,然後向後搜索到記錄集的開頭。

如果要在搜索中包括所有記錄(而不僅僅是滿足特定條件的記錄),請使用 Move 操作之一從記錄移動到記錄。 要在表類型記錄集中查找記錄,請調用`Seek`成員函數。

如果未找到與條件匹配的記錄,則當前記錄指標未確定,並`FindPrev`返回零。 如果記錄集包含滿足條件的多個記錄,則`FindFirst`查找第一個匹配項`FindNext`, 找到下一個匹配項,等等。

> [!CAUTION]
> 如果編輯當前記錄,請確保在移動到其他記錄之前通過調用`Update`成員函數來保存更改。 如果不更新而移動到其他記錄,則更改將丟失,而不會發出警告。

使用 Find 操作之一與`MoveFirst``MoveNext`調用 或 不同,它只是使第一個或下一個記錄保持最新而不指定條件。 您可以使用「移動」操作執行「尋找」操作。

使用 Find 動作時,請記住以下事項:

- 如果`Find`返回非零,則不定義當前記錄。 在這種情況下,必須將當前記錄指標定位回有效記錄。

- 不能將「查找」操作與僅轉發滾動快照類型記錄集一起使用。

- 搜索包含日期的欄位時,即使您未使用 Microsoft Jet 資料庫引擎的美國版本,也應使用美國日期格式(月日年)。否則,可能無法找到匹配的記錄。

- 使用 ODBC 資料庫和大型動態集時,您可能會發現使用 Find 操作很慢,尤其是在使用大型記錄集時。 通過將 SQL 查詢與自訂**ORDERBY**或**WHERE**`CDaoQuerydef`子句、參數查詢或 檢索特定索引記錄的物件使用 SQL 查詢來提高性能。

有關相關信息,請參閱 DAO 説明中的主題"查找第一、查找最後、查找下一個、查找以前的方法」。。

## <a name="cdaorecordsetgetabsoluteposition"></a><a name="getabsoluteposition"></a>CDao 記錄集:取得絕對位置

返回記錄集物件的當前記錄的記錄編號。

```
long GetAbsolutePosition();
```

### <a name="return-value"></a>傳回值

從 0 到記錄集中記錄數的整數。 對應於記錄集中當前記錄的盤位位置。

### <a name="remarks"></a>備註

基礎 DAO 物件的絕對位置屬性值是零基的;設置為 0 是指記錄集中的第一個記錄。 您可以通過調用[GetRecordCount](#getrecordcount)來確定記錄集中填充的記錄數。 調用`GetRecordCount`可能需要一些時間,因為它必須訪問所有記錄以確定計數。

如果沒有當前記錄,如記錄集中沒有記錄時,則返回 - 1。 如果刪除當前記錄,則不定義絕對位置屬性值,如果引用,MFC 將引發異常。 對於動態集類型的記錄集,新記錄將添加到序列的末尾。

> [!NOTE]
> 此屬性不用作代理記錄編號。 書籤仍然是保留和返回到給定位置的推薦方式,是跨所有類型的記錄集物件定位當前記錄的唯一方法。 特別是,當刪除給定記錄之前的記錄時,給定記錄的位置會發生變化。 如果再次重新創建記錄集,也不能保證給定記錄集具有相同的絕對位置,因為除非使用**ORDERBY**子句使用 SQL 語句創建記錄集中的單個記錄的順序不保證。

> [!NOTE]
> 此成員函數僅適用於動態集類型和快照類型記錄集。

有關相關信息,請參閱 DAO 説明中的「絕對位置屬性」 主題。

## <a name="cdaorecordsetgetbookmark"></a><a name="getbookmark"></a>CDao 記錄集::取得書籤

調用此成員函數以獲取特定記錄中的書籤值。

```
COleVariant GetBookmark();
```

### <a name="return-value"></a>傳回值

返回表示當前記錄上的書籤的值。

### <a name="remarks"></a>備註

創建或打開記錄集物件時,如果每個記錄支持它們,則其每個記錄已具有唯一的書籤。 調用`CanBookmark`以確定記錄集是否支援書籤。

通過將書籤的值分配給`COleVariant`物件,可以保存當前記錄的書籤。 要在移動到其他記錄后隨時快速返回到該記錄,請調用`SetBookmark`與`COleVariant`該 物件的值對應的參數。

> [!NOTE]
> 呼叫[重新查詢](#requery)會更改 DAO 書籤。

有關相關信息,請參閱 DAO 説明中的主題「書籤屬性」。

## <a name="cdaorecordsetgetcachesize"></a><a name="getcachesize"></a>CDao 記錄集::取得快取大小

調用此成員函數以獲取緩存的記錄數。

```
long GetCacheSize();
```

### <a name="return-value"></a>傳回值

指定動態集類型記錄集中的記錄數的值,其中包含要從 ODBC 資料來源本地快取的數據。

### <a name="remarks"></a>備註

數據快取提高了應用程式透過動態集類型記錄集物件從遠端伺服器檢索資料的性能。 快取是本地記憶體中的一個空間,用於保存最近從伺服器檢索的數據,如果應用程式運行時將再次請求數據。 請求數據時,Microsoft Jet 資料庫引擎首先檢查緩存中請求的數據,而不是從伺服器檢索數據,這需要更多的時間。 不來自 ODBC 資料來源的資料不會儲存在快取中。

任何 ODBC 資料來源(如附加的表)都可以具有本地快取。

有關相關信息,請參閱 DAO 説明中的主題「緩存大小、緩存啟動屬性」。

## <a name="cdaorecordsetgetcachestart"></a><a name="getcachestart"></a>CDao 記錄集::取得快取開始

調用此成員函數以獲取要快取的記錄集中第一個記錄的書籤值。

```
COleVariant GetCacheStart();
```

### <a name="return-value"></a>傳回值

指定`COleVariant`要緩存的記錄集中第一個記錄的書籤。

### <a name="remarks"></a>備註

Microsoft Jet 資料庫引擎從快取請求快取範圍內的記錄,並且請求伺服器在緩存範圍之外的記錄。

> [!NOTE]
> 從緩存中檢索的記錄不會反映其他用戶同時對源數據所做的更改。

有關相關信息,請參閱 DAO 説明中的主題「緩存大小、緩存啟動屬性」。

## <a name="cdaorecordsetgetcurrentindex"></a><a name="getcurrentindex"></a>CDao 記錄集::取得目前索引

調用此成員函數以確定索引表類型`CDaoRecordset`物件中當前使用的索引。

```
CString GetCurrentIndex();
```

### <a name="return-value"></a>傳回值

包含`CString`當前與表類型記錄集一起使用的索引的名稱。 如果未設置索引,則返回空字串。

### <a name="remarks"></a>備註

此索引是對表類型記錄集中的記錄排序的基礎,並且[由 Seek](#seek)成員函數用於查找記錄。

物件`CDaoRecordset`可以有多個索引,但一次只能使用一個索引(儘管[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)物件可能有多個索引定義)。

有關相關信息,請參閱 DAO 説明中的主題"索引物件"和定義"當前索引"。

## <a name="cdaorecordsetgetdatecreated"></a><a name="getdatecreated"></a>CDao 記錄集::取得日期建立

調用此成員函數以檢索創建基表的日期和時間。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>傳回值

包含創建基表的日期和時間的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件。

### <a name="remarks"></a>備註

日期和時間設置派生自創建基表的計算機。

有關相關信息,請參閱 DAO 説明中的主題"創建日期,上次更新的屬性"。

## <a name="cdaorecordsetgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDao 記錄集::取得更新日期

調用此成員函數以檢索架構上次更新的日期和時間。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>傳回值

包含上次更新基表結構(架構)的日期和時間的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件。

### <a name="remarks"></a>備註

日期和時間設置派生自上次更新基表結構(架構)的計算機。

有關相關信息,請參閱 DAO 説明中的主題"創建日期,上次更新的屬性"。

## <a name="cdaorecordsetgetdefaultdbname"></a><a name="getdefaultdbname"></a>CDao 記錄集:取得預設 DB 名稱

呼叫此成員函數以確定此記錄集的資料庫名稱。

```
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>傳回值

包含`CString`指定此紀錄的資料庫的路徑與名稱的 。

### <a name="remarks"></a>備註

如果創建記錄集時沒有指向[CDao 資料庫](../../mfc/reference/cdaodatabase-class.md)的指標,則記錄集使用此路徑來打開預設資料庫。 預設情況下,此函數返回一個空字串。 當 ClassWizard`CDaoRecordset`從 派生新的記錄集時,它將為您創建此函數。

下面的範例說明了在字串中使用雙反斜杠 (\\\\),這是正確解釋字串所需的。

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

## <a name="cdaorecordsetgetdefaultsql"></a><a name="getdefaultsql"></a>CDao 記錄集::取得預設SQL

框架呼叫此成員函數以獲取記錄集所基於的預設 SQL 語句。

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>傳回值

包含`CString`預設 SQL 語句的 。

### <a name="remarks"></a>備註

這可能是表名稱或 SQL **SELECT**語句。

通過使用 ClassWizard 聲明記錄集類來間接定義預設 SQL 語句,ClassWizard 會為您執行此任務。

如果將空 SQL 字串傳遞給[Open](#open),則呼叫此函數以確定記錄集的表名或 SQL。

## <a name="cdaorecordsetgeteditmode"></a><a name="geteditmode"></a>CDao 記錄集::取得編輯模式

呼叫此成員函數以確定編輯狀態,這是以下值之一:

```
short GetEditMode();
```

### <a name="return-value"></a>傳回值

返回指示當前記錄的編輯狀態的值。

### <a name="remarks"></a>備註

|值|描述|
|-----------|-----------------|
|`dbEditNone`|未正在進行編輯操作。|
|`dbEditInProgress`|`Edit` 已被呼叫。|
|`dbEditAdd`|`AddNew` 已被呼叫。|

有關相關信息,請參閱 DAO 説明中的主題"編輯模式屬性」。

## <a name="cdaorecordsetgetfieldcount"></a><a name="getfieldcount"></a>CDao記錄集::獲取菲爾德計數

調用此成員函數以檢索記錄集中定義的欄位(列)數。

```
short GetFieldCount();
```

### <a name="return-value"></a>傳回值

記錄集中的欄位數。

### <a name="remarks"></a>備註

有關相關信息,請參閱 DAO 説明中的主題"計數屬性」。。

## <a name="cdaorecordsetgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoRecordset:取得菲爾德資訊

調用此成員函數以獲取有關記錄集中的欄位的資訊。

```cpp
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
記錄集的「欄位」集合中預定義欄位的零基索引,用於按索引進行查找。

*菲爾德資訊*<br/>
對[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構的引用。

*dwInfoOptions*<br/>
指定有關要檢索的記錄集的資訊的選項。 此處列出了可用選項以及它們導致函數返回的內容。 為了獲得最佳性能,僅檢索所需的資訊級別:

- `AFX_DAO_PRIMARY_INFO`( 預設 )名稱、類型、大小、屬性

- `AFX_DAO_SECONDARY_INFO`主要資訊,加上:序號位置、必需位置、允許零長度、分詞順序、外名、原始欄位、源表

- `AFX_DAO_ALL_INFO`主要與輔助資訊,以及預設值、驗證規則、驗證文字

*lpsz名稱*<br/>
欄位的名稱。

### <a name="remarks"></a>備註

函數的一個版本允許您按索引查找欄位。 另一個版本允許您按名稱查找欄位。

有關返回的信息的說明,請參閱[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。 此結構的成員對應於*dwInfoOptions*描述中列出的資訊項。 當您在一個級別請求資訊時,您也獲取任何先前級別的資訊。

有關相關信息,請參閱 DAO 説明中的主題「屬性屬性」。

## <a name="cdaorecordsetgetfieldvalue"></a><a name="getfieldvalue"></a>CDao 記錄集:取得場值

調用此成員函數以檢索記錄集中的數據。

```
virtual void GetFieldValue(
    LPCTSTR lpszName,
    COleVariant& varValue);

virtual void GetFieldValue(
    int nIndex,
    COleVariant& varValue);

virtual COleVariant GetFieldValue(LPCTSTR lpszName);
virtual COleVariant GetFieldValue(int nIndex);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
指向包含欄位名稱的字串的指標。

*varValue*<br/>
對將儲存欄位`COleVariant`值的物件的引用。

*nIndex*<br/>
記錄集的「欄位」集合中欄位的零基索引,用於按索引查找。

### <a name="return-value"></a>傳回值

該值的`GetFieldValue`兩個版本返回包含欄位值的[COleVariant](../../mfc/reference/colevariant-class.md)物件。

### <a name="remarks"></a>備註

您可以按名稱或位形位置尋找欄位。

> [!NOTE]
> 調用此成員函數之一`COleVariant`以物件引用為參數,而不是調用`COleVariant`返回 物件的版本,效率更高。 為了向後相容性,將保留此函數的後一個版本。

使用`GetFieldValue`和[SetFieldValue](#setfieldvalue)在執行時動態綁定欄位,而不是使用[DoFieldExchange](#dofieldexchange)機制對列進行靜態綁定。

`GetFieldValue`和`DoFieldExchange`機制可以結合,以提高性能。 例如,用於`GetFieldValue`檢索僅按需需要的值,並將該調用分配給介面中的"更多資訊"按鈕。

有關相關信息,請參閱 DAO 説明中的「欄位物件」和「值屬性」主題。

## <a name="cdaorecordsetgetindexcount"></a><a name="getindexcount"></a>CDao 記錄集:取得索引計數

調用此成員函數以確定表類型記錄集中可用的索引數。

```
short GetIndexCount();
```

### <a name="return-value"></a>傳回值

表類型記錄集中的索引數。

### <a name="remarks"></a>備註

`GetIndexCount`可用於迴圈遍歷記錄集中的所有索引。 為此,請與`GetIndexCount`[GetIndexInfo](#getindexinfo)結合使用。 如果在動態集類型或快照類型記錄集上調用此成員函數,MFC 將引發異常。

有關相關信息,請參閱 DAO 説明中的主題「屬性屬性」。

## <a name="cdaorecordsetgetindexinfo"></a><a name="getindexinfo"></a>CDao 記錄集:取得索引資訊

調用此成員函數以獲取有關在記錄集基礎基表中定義的索引的各種資訊。

```cpp
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
表的 Index 集合中的零基索引,用於按數位位置查找。

*索引資訊*<br/>
對[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構的引用。

*dwInfoOptions*<br/>
指定要檢索的索引的資訊的選項。 此處列出了可用選項以及它們導致函數返回的內容。 為了獲得最佳性能,僅檢索所需的資訊級別:

- `AFX_DAO_PRIMARY_INFO`( 預設 )名稱、欄位資訊、欄位

- `AFX_DAO_SECONDARY_INFO`主要資訊,加上:主資訊、唯一資訊、群集、忽略 Null、必需、外國

- `AFX_DAO_ALL_INFO`主要和次要資訊,加上:不同的計數

*lpsz名稱*<br/>
指向索引物件名稱的指標,用於按名稱查找。

### <a name="remarks"></a>備註

函數的一個版本允許您按索引在集合中的位置查找索引。 另一個版本允許您按名稱查找索引。

有關返回的資訊的說明,請參閱[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構。 此結構的成員對應於*dwInfoOptions*描述中列出的資訊項。 當您在一個級別請求資訊時,您也獲取任何先前級別的資訊。

有關相關信息,請參閱 DAO 説明中的主題「屬性屬性」。

## <a name="cdaorecordsetgetlastmodifiedbookmark"></a><a name="getlastmodifiedbookmark"></a>CDao 記錄集::取得上次修改的書籤

調用此成員函數以檢索最近添加或更新的記錄的書籤。

```
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>傳回值

包含`COleVariant`指示最近添加或更改的記錄的書籤。

### <a name="remarks"></a>備註

創建或打開記錄集物件時,如果每個記錄支持它們,則其每個記錄已具有唯一的書籤。 調用[GetBookmark](#getbookmark)以確定記錄集是否支援書籤。 如果記錄集不支援書籤,則引發`CDaoException`。

添加記錄時,它將顯示在記錄集的末尾,而不是當前記錄。 要使新記錄成為當前記錄,請`GetLastModifiedBookmark`調用,然後`SetBookmark`調用以返回到新添加的記錄。

有關相關信息,請參閱 DAO 説明中的主題「上次修改屬性」。

## <a name="cdaorecordsetgetlockingmode"></a><a name="getlockingmode"></a>CDao 記錄集::取得鎖定模式

調用此成員函數以確定記錄集有效的鎖定類型。

```
BOOL GetLockingMode();
```

### <a name="return-value"></a>傳回值

如果鎖定類型為悲觀,則非零,否則為 0 表示樂觀記錄鎖定。

### <a name="remarks"></a>備註

當悲觀鎖定生效時,包含您正在編輯的記錄的數據頁在調用[Edit](#edit)成員函數後立即鎖定。 當您呼叫[「更新](#update)」或「[關閉](#close)」成員功能或任何「移動」或「尋找」操作時,頁面將解鎖。

當樂觀鎖定生效時,包含記錄的數據頁僅在使用`Update`成員函數更新記錄時鎖定。

使用 ODBC 數據源時,鎖定模式始終樂觀。

有關相關信息,請參閱 DAO 説明中的"鎖定屬性"和"多使用者應用程式中的鎖定行為"主題。

## <a name="cdaorecordsetgetname"></a><a name="getname"></a>CDao 記錄集:取得名稱

調用此成員函數以檢索記錄集的名稱。

```
CString GetName();
```

### <a name="return-value"></a>傳回值

包含`CString`記錄集的名稱。

### <a name="remarks"></a>備註

記錄集的名稱必須以字母開頭,最多只能包含 40 個字元。 它可以包括數位和下劃線字元,但不能包括標點符號或空格。

有關相關信息,請參閱 DAO 説明中的主題"名稱屬性"。

## <a name="cdaorecordsetgetparamvalue"></a><a name="getparamvalue"></a>CDao 記錄集::取得帕拉姆價值

呼叫此成員函數以檢索儲存在基礎 DAOParameter 物件中的指定參數的當前值。

```
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
參數在基礎 DAO 參數物件中的數值位置。

*lpsz名稱*<br/>
所需的值的參數的名稱。

### <a name="return-value"></a>傳回值

包含參數值的類[COleVariant](../../mfc/reference/colevariant-class.md)的物件。

### <a name="remarks"></a>備註

您可以按名稱或參數在集合中的數值位置訪問參數。

有關相關信息,請參閱 DAO 説明中的主題"參數物件"。

## <a name="cdaorecordsetgetpercentposition"></a><a name="getpercentposition"></a>CDao 記錄集:取得百分比位置

使用動態集類型或快照類型記錄集時,如果在完全填充記錄集之前調用`GetPercentPosition`,則移動量與調用[GetRecordCount](#getrecordcount)指示的訪問記錄數相關。

```
float GetPercentPosition();
```

### <a name="return-value"></a>傳回值

介於 0 和 100 之間的數位,該數位根據記錄集中記錄中記錄的百分比指示記錄集物件中當前記錄的大致位置。

### <a name="remarks"></a>備註

您可以通過調用[MoveLast](#movelast)來移動到最後一個記錄以完成所有記錄集的填充,但這可能需要大量時間。

您可以呼叫`GetPercentPosition`所有三種類型的記錄集物件,包括沒有索引的表。 但是,您不能調用僅`GetPercentPosition`轉發滾動快照,也不能調用從針對外部資料庫的傳遞查詢打開的記錄集上。 如果沒有當前記錄,或者他當前記錄已被刪除,則引發 a。 `CDaoException`

有關相關信息,請參閱 DAO 説明中的主題"百分比位置屬性」。。

## <a name="cdaorecordsetgetrecordcount"></a><a name="getrecordcount"></a>CDao 記錄集::取得記錄計數

調用此成員函數,瞭解已訪問的記錄集中的記錄數。

```
long GetRecordCount();
```

### <a name="return-value"></a>傳回值

返回在記錄集對象中訪問的記錄數。

### <a name="remarks"></a>備註

`GetRecordCount`不指示在已訪問所有記錄之前,動態集類型或快照類型記錄集中包含多少條記錄。 此成員函數調用可能需要大量時間才能完成。

訪問最後一條記錄後,返回值指示記錄集中未刪除記錄的總數。 要強制訪問最後一個記錄,請調用`MoveLast`記錄`FindLast`集的或成員函數。 您還可以使用 SQL 計數來確定查詢將返回的記錄的大致數量。

當應用程式刪除動態集類型記錄集中的記錄時,返回`GetRecordCount`值將減小。 但是,在將當前記錄定位到已刪除的記錄之前`GetRecordCount`,其他使用者刪除的記錄不會反映在該記錄上。 如果執行影響記錄計數的事務,然後回滾事務,`GetRecordCount`則不會反映剩餘記錄的實際數量。

`GetRecordCount`快照類型記錄集的值不受基礎表中的更改的影響。

表類型記錄`GetRecordCount`集的值反映表中記錄的近似數量,並且隨著表記錄的添加和刪除而立即受到影響。

沒有記錄的記錄集返回值 0。 使用附加的表或 ODBC`GetRecordCount`資料庫 時,始終返回 - 1。 在`Requery`記錄集中調用成員函數將重置的值`GetRecordCount`, 就像重新執行查詢一樣。

有關相關信息,請參閱 DAO 説明中的主題"記錄計數屬性」。。

## <a name="cdaorecordsetgetsql"></a><a name="getsql"></a>CDao 記錄集::取得SQL

呼叫此成員函數獲取用於在打開記錄集時用於選擇記錄集記錄的 SQL 語句。

```
CString GetSQL() const;
```

### <a name="return-value"></a>傳回值

包含`CString`SQL 語句的 。

### <a name="remarks"></a>備註

這通常是 SQL **SELECT**語句。

傳`GetSQL`回的字串通常不同於您可能傳遞給*lpszSQL*參數中的記錄集到[Open](#open)成員函數的任何字串。 這是因為記錄集基於您傳遞給`Open`的內容構建完整的 SQL 語句,以及您在m_strFilter中指定的內容以及[數據](#m_strfilter)成員[m_strSort。](#m_strsort)

> [!NOTE]
> 僅在調用`Open`後調用此成員函數。

有關相關信息,請參閱 DAO 説明中的主題"SQL 屬性」。。

## <a name="cdaorecordsetgettype"></a><a name="gettype"></a>CDao 記錄集:取得類型

打開記錄集後調用此成員函數以確定記錄集物件的類型。

```
short GetType();
```

### <a name="return-value"></a>傳回值

指示記錄集類型的以下值之一:

- `dbOpenTable`表型態記錄集

- `dbOpenDynaset`動態組態記錄集

- `dbOpenSnapshot`快照類型記錄集

### <a name="remarks"></a>備註

有關相關信息,請參閱 DAO 説明中的主題"類型屬性」。。

## <a name="cdaorecordsetgetvalidationrule"></a><a name="getvalidationrule"></a>CDao 記錄集::取得驗證規則

調用此成員函數以確定用於驗證數據的規則。

```
CString GetValidationRule();
```

### <a name="return-value"></a>傳回值

包含`CString`值的物件,用於在更改數據或添加到表中時驗證記錄中的數據。

### <a name="remarks"></a>備註

此規則基於文本,並在每次更改基礎表時應用。 如果數據不合法,MFC 將引發異常。 傳回的錯誤訊息是基礎欄位物件的驗證文本屬性的文本(如果指定)或基礎欄位物件的驗證規則屬性指定的表示式的文本。 您可以呼叫[Get驗證文本](#getvalidationtext)以取得錯誤訊息的文字。

例如,記錄中需要月份當天的欄位可能具有驗證規則,如"天與 1 和 31"。

有關相關信息,請參閱 DAO 説明中的主題"驗證規則屬性」。

## <a name="cdaorecordsetgetvalidationtext"></a><a name="getvalidationtext"></a>CDao 記錄集::取得認證文字

呼叫此成員函數以檢索基礎欄位物件的驗證文本屬性的文本。

```
CString GetValidationText();
```

### <a name="return-value"></a>傳回值

包含`CString`消息文本的物件,如果欄位的值不符合基礎欄位物件的驗證規則,則顯示該消息的文本。

### <a name="remarks"></a>備註

有關相關信息,請參閱 DAO 説明中的主題"驗證文本屬性」。。

## <a name="cdaorecordsetisbof"></a><a name="isbof"></a>CDao 記錄集:IsBOF

在從記錄滾動到記錄之前,請調用此成員函數,以瞭解您是否在記錄集的第一個記錄之前。

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>傳回值

如果記錄集不包含任何記錄,或者在第一個記錄之前向後滾動,則非零;否則 0。

### <a name="remarks"></a>備註

還可以一起`IsEOF`調`IsBOF`用 以確定記錄集是否包含任何記錄或為空。 呼叫 後`Open`立即 呼叫,如果記錄集不包含任何`IsBOF`記錄, 則傳回非零。 當您打開至少具有一條記錄的記錄集時,第一個記錄是當前記錄,並`IsBOF`返回 0。

如果第一條記錄是當前記錄,而您調用`MovePrev``IsBOF`時,將隨後返回非零。 如果`IsBOF`返回非零,並且調`MovePrev`用 ,將引發異常。 如果`IsBOF`返回非零,則當前記錄未定義,任何需要當前記錄的操作都將導致異常。

特定方法對`IsBOF``IsEOF`與設定的影響:

- 內部`Open*`調用通過調`MoveFirst`用 使記錄中的第一個記錄成為當前記錄。 因此,調用`Open`一組空的記錄`IsBOF`會導致`IsEOF`並返回非零。 (有關失敗`MoveFirst``MoveLast`或調用的行為,請參閱下表。

- 成功查找記錄的所有移動操作都會導致兩者`IsBOF``IsEOF`並返回 0。

- `AddNew`成功插入新記錄的`Update`調用後跟調用將`IsBOF`導致返回 0,但僅當已為非`IsEOF`零時 才會返回 0。 的狀態`IsEOF`將保持不變。 根據 Microsoft Jet 資料庫引擎的定義,空記錄集的當前記錄指標位於檔的末尾,因此在當前記錄之後插入任何新記錄。

- 任何`Delete`調用(即使它從記錄集中中刪除唯一的剩餘記錄)也不會更改`IsBOF``IsEOF`或的值。

此表顯示允許使用的不同組合的`IsBOF`/ `IsEOF`Move 操作。

||首先移動,移動最後|MovePrev,<br /><br /> 移動< 0|移動 0|移動下一個,<br /><br /> 移動> 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`*非零,<br /><br /> `IsEOF`=0|允許|例外狀況|例外狀況|允許|
|`IsBOF`=0,<br /><br /> `IsEOF`*非零|允許|允許|例外狀況|例外狀況|
|兩者均無零|例外狀況|例外狀況|例外狀況|例外狀況|
|兩者均為 0|允許|允許|允許|允許|

允許 Move 操作並不意味著操作將成功找到記錄。 它只是指示嘗試執行指定的 Move 操作是允許的,不會生成異常。 `IsBOF`和`IsEOF`成員函數的值可能會因嘗試行動而更改。

下表中顯示了未找到記錄對`IsBOF`和`IsEOF`和設定值的 Move 操作的效果。

||ISBOF|伊塞OF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|零|零|
|`Move` 0|沒有變更|沒有變更|
|`MovePrev`, `Move` < 0|零|沒有變更|
|`MoveNext`, `Move` > 0|沒有變更|零|

有關相關信息,請參閱 DAO 説明中的「BOF,EOF 屬性」主題。

## <a name="cdaorecordsetisdeleted"></a><a name="isdeleted"></a>CDao 記錄集:已刪除

呼叫此成員函數以確定當前記錄是否已被刪除。

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>傳回值

如果記錄集位於已刪除的記錄上,則非零;否則 0。

### <a name="remarks"></a>備註

如果滾動到記錄並`IsDeleted`返回 TRUE(非零),則必須滾動到其他記錄,然後才能執行任何其他記錄集操作。

> [!NOTE]
> 您無需檢查快照或表類型記錄集中的記錄的已刪除狀態。 由於無法從快照中刪除記錄,因此無需呼叫`IsDeleted`。 對於表類型的記錄集,刪除的記錄實際上將從記錄集中刪除。 一旦您、其他使用者或其他記錄集中刪除了記錄,您就無法回滾到該記錄。 因此,無需呼叫`IsDeleted`。

從動態集中刪除記錄時,該記錄將從記錄集中刪除,並且無法回滾到該記錄。 但是,如果動態集中的記錄被其他使用者刪除,或者基於同一表的另一個記錄集中刪除,則當您以後滾動到該`IsDeleted`記錄時,將返回 TRUE。

有關相關信息,請參閱 DAO 説明中的"刪除方法"、"上次修改屬性"和"編輯模式屬性"的主題。

## <a name="cdaorecordsetiseof"></a><a name="iseof"></a>CDao 記錄集::IsEOF

在從記錄滾動到記錄時調用此成員函數,以瞭解您是否超出了記錄集的最後一條記錄。

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>傳回值

如果記錄集不包含任何記錄,或者您滾動超過最後一條記錄,則為非零;否則 0。

### <a name="remarks"></a>備註

還可以調用`IsEOF`以確定記錄集是否包含任何記錄或為空。 呼叫 後`Open`立即 呼叫,如果記錄集不包含任何`IsEOF`記錄, 則傳回非零。 當您打開至少具有一條記錄的記錄集時,第一個記錄是當前記錄,並`IsEOF`返回 0。

如果最後一條記錄是您調用`MoveNext`時的目前記錄`IsEOF`, 則隨後將返回非零。 如果`IsEOF`返回非零,並且調`MoveNext`用 ,將引發異常。 如果`IsEOF`返回非零,則當前記錄未定義,任何需要當前記錄的操作都將導致異常。

特定方法對`IsBOF``IsEOF`與設定的影響:

- 內部`Open`調用通過調`MoveFirst`用 使記錄中的第一個記錄成為當前記錄。 因此,調用`Open`一組空的記錄`IsBOF`會導致`IsEOF`並返回非零。 (有關失敗`MoveFirst`呼叫的行為,請參閱下表。

- 成功查找記錄的所有移動操作都會導致兩者`IsBOF``IsEOF`並返回 0。

- `AddNew`成功插入新記錄的`Update`調用後跟調用將`IsBOF`導致返回 0,但僅當已為非`IsEOF`零時 才會返回 0。 的狀態`IsEOF`將保持不變。 根據 Microsoft Jet 資料庫引擎的定義,空記錄集的當前記錄指標位於檔的末尾,因此在當前記錄之後插入任何新記錄。

- 任何`Delete`調用(即使它從記錄集中中刪除唯一的剩餘記錄)也不會更改`IsBOF``IsEOF`或的值。

此表顯示允許使用的不同組合的`IsBOF`/ `IsEOF`Move 操作。

||首先移動,移動最後|MovePrev,<br /><br /> 移動< 0|移動 0|移動下一個,<br /><br /> 移動> 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`*非零,<br /><br /> `IsEOF`=0|允許|例外狀況|例外狀況|允許|
|`IsBOF`=0,<br /><br /> `IsEOF`*非零|允許|允許|例外狀況|例外狀況|
|兩者均無零|例外狀況|例外狀況|例外狀況|例外狀況|
|兩者均為 0|允許|允許|允許|允許|

允許 Move 操作並不意味著操作將成功找到記錄。 它只是指示嘗試執行指定的 Move 操作是允許的,不會生成異常。 `IsBOF`和`IsEOF`成員函數的值可能會由於嘗試的 Move 而改變。

下表中顯示了未找到記錄對`IsBOF`和`IsEOF`和設定值的 Move 操作的效果。

||ISBOF|伊塞OF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|零|零|
|`Move` 0|沒有變更|沒有變更|
|`MovePrev`, `Move` < 0|零|沒有變更|
|`MoveNext`, `Move` > 0|沒有變更|零|

有關相關信息,請參閱 DAO 説明中的「BOF,EOF 屬性」主題。

## <a name="cdaorecordsetisfielddirty"></a><a name="isfielddirty"></a>CDao 記錄集::IsfieldDirty

調用此成員函數以確定動態集的指定欄位數據成員是否已標記為「髒」(已更改)。

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
指向要檢查其狀態的欄位資料成員的指標,或 NULL 以確定任何欄位是否髒。

### <a name="return-value"></a>傳回值

如果指定的欄位數據成員標記為髒,則非零;否則 0。

### <a name="remarks"></a>備註

`Update`當對成員`CDaoRecordset`函數的調用(在`Edit`對`AddNew`或調用 後)更新當前記錄時,所有髒欄位數據成員中的數據都將傳輸到數據源上的記錄。 有了這些知識,您可以執行進一步步驟,例如取消標記欄位數據成員以標記列,以便不會將其寫入數據源。

`IsFieldDirty`通過`DoFieldExchange`。

## <a name="cdaorecordsetisfieldnull"></a><a name="isfieldnull"></a>CDao記錄集::IsfieldNull

呼叫此成員函數以確定記錄集的指定欄位資料成員是否已標記為 Null。

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
指向要檢查其狀態的欄位資料成員的指標,或 NULL 以確定是否有任何欄位為 Null。

### <a name="return-value"></a>傳回值

如果指定的欄位資料成員標記為 Null,則非零;否則 0。

### <a name="remarks"></a>備註

(在資料庫術語中,Null 表示"沒有值",並且與 C++ 中的 NULL 不同。如果欄位資料成員標記為 Null,則將其解釋為當前記錄的列,該列沒有值。

> [!NOTE]
> 在某些情況下,使用`IsFieldNull`效率可能很低,如下代碼示例所示:

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
> 如果使用動態記錄綁定,而不派生於`CDaoRecordset`,請確保使用VT_NULL如示例中所示。

## <a name="cdaorecordsetisfieldnullable"></a><a name="isfieldnullable"></a>CDao 記錄集::可欄位空

呼叫此成員函數以確定指定的欄位資料成員是否為"空"(可以設置為Null值;是否可以設置為Null值。"C++ NULL 與 Null 不同,在資料庫術語中,Null 表示"沒有值")。

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
指向要檢查其狀態的欄位資料成員的指標,或 NULL 以確定是否有任何欄位為 Null。

### <a name="return-value"></a>傳回值

如果指定的欄位資料成員可以為 Null,則非零;否則 0。

### <a name="remarks"></a>備註

不能為空的欄位必須具有值。 如果在添加或更新記錄時嘗試將此類欄位設置為 Null,資料源將拒絕添加或更新,`Update`並將引發異常。 當您調用`Update`時,則出現異常,而不是調`SetFieldNull`用 時出現。

## <a name="cdaorecordsetisopen"></a><a name="isopen"></a>CDao 記錄集::是開啟的

調用此成員函數以確定記錄集是否打開。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

以前已調用記錄集物件的`Open``Requery`或成員函數,並且記錄集尚未關閉,則非零;否則 0。

### <a name="remarks"></a>備註

## <a name="cdaorecordsetm_bcheckcachefordirtyfields"></a><a name="m_bcheckcachefordirtyfields"></a>CDaoRecordset:m_bCheckCacheForDirtyFields

包含一個標誌,指示快取的欄位是否自動標記為髒(更改)和 Null。

### <a name="remarks"></a>備註

標誌預設為 TRUE。 此數據成員中的設置控制整個雙緩衝機制。 如果將標誌設置為 TRUE,則可以使用 DFX 機制逐欄位關閉緩存。 如果將標誌設置為 FALSE,則必須調`SetFieldDirty`用`SetFieldNull`自己。

在調用`Open`之前設置此數據成員。 此機制主要是為了方便使用。 性能可能較慢,因為在進行更改時對欄位進行了雙重緩衝。

## <a name="cdaorecordsetm_nfields"></a><a name="m_nfields"></a>CDao 記錄集::m_nFields

包含記錄集類中的欄位數據成員數以及記錄組從資料源中選擇的欄數。

### <a name="remarks"></a>備註

記錄集類的構造函數必須用正確數量的靜態`m_nFields`綁定欄位進行初始化。 當您使用它聲明記錄集類時,ClassWizard 會為您編寫此初始化。 您也可以手動編寫。

框架使用此數位來管理欄位數據成員與數據源上當前記錄的相應列之間的交互。

> [!NOTE]
> 此編號必須對應於`DoFieldExchange``SetFieldType`使用`CDaoFieldExchange::outputColumn`參數調用 后註冊的輸出列數。

可以`CDaoRecordset::GetFieldValue`通過`CDaoRecordset::SetFieldValue`和動態綁定列。 如果這樣做,則不需要增加計數`m_nFields`以反映`DoFieldExchange`成員函數中的 DFX 函數調用數。

## <a name="cdaorecordsetm_nparams"></a><a name="m_nparams"></a>CDao 記錄集::m_nParams

包含記錄集類別中的參數資料成員數 - 記錄集查詢傳遞的參數數。

### <a name="remarks"></a>備註

如果記錄集類具有任何參數數據成員,則類的構造函數必須用正確的數位初始化*m_nParams。* *值m_nParams*預設值為 0。 如果添加參數資料成員(您必須手動執行),還必須在類構造函數中手動添加初始化,以反映參數數(參數數量必須至少與*m_strFilter*或*m_strSort*字串中的''占位符數相同)。

框架在參數化記錄集的查詢時使用此數位。

> [!NOTE]
> 此號碼必須對應於`DoFieldExchange``SetFieldType`使用`CFieldExchange::param`參數調用 後註冊的"參數"數。

有關相關信息,請參閱 DAO 説明中的主題"參數物件"。

## <a name="cdaorecordsetm_pdaorecordset"></a><a name="m_pdaorecordset"></a>CDao 記錄集::m_pDAORecordset

包含指向物件基礎的 DAO 記錄集物件的 OLE 介面的`CDaoRecordset`指標。

### <a name="remarks"></a>備註

如果需要直接訪問 DAO 介面,請使用此指標。

有關相關信息,請參閱 DAO 説明中的主題"記錄集物件"。

## <a name="cdaorecordsetm_pdatabase"></a><a name="m_pdatabase"></a>CDao 記錄集::m_pDatabase

包含指向記錄集連接到數據來源`CDaoDatabase`的物件的指標。

### <a name="remarks"></a>備註

此變數以兩種方式設置。 通常,在構造記錄集物件時,將`CDaoDatabase`指標傳遞給已打開的物件。 如果改為傳遞 NULL,`CDaoRecordset`則`CDaoDatabase`為您 創建一個物件並打開它。 在這兩種情況下,`CDaoRecordset`都在此變數中儲存指標。

通常,您不需要直接使用存儲在中的`m_pDatabase`指標。 但是,如果將自己的擴展寫入`CDaoRecordset`,則可能需要使用指標。 例如,如果拋出自己的`CDaoException`(s),則可能需要指標。

有關相關信息,請參閱 DAO 説明中的主題"資料庫物件"。

## <a name="cdaorecordsetm_strfilter"></a><a name="m_strfilter"></a>CDao 記錄集::m_strFilter

包含用於構造 SQL 語句的**WHERE**子句的字串。

### <a name="remarks"></a>備註

它不包括用於篩選記錄集的保留字**WHERE。** 此數據成員的使用不適用於表類型的記錄集。 使用`CDaoQueryDef`指標`m_strFilter`打開記錄集時,使用沒有任何效果。

篩選包含日期的欄位時,使用美國日期格式(月日年),即使您沒有使用 Microsoft Jet 資料庫引擎的美國版本;否則,數據可能無法按預期進行篩選。

有關相關信息,請參閱 DAO 説明中的主題"篩選屬性」。。

## <a name="cdaorecordsetm_strsort"></a><a name="m_strsort"></a>CDao 記錄集::m_strSort

包含 SQL 語句的**ORDERBY**子句的字串,而不保留單字**ORDERBY**。

### <a name="remarks"></a>備註

您可以對動態集和快照類型的記錄集物件進行排序。

不能對表類型記錄集物件進行排序。 要確定表類型記錄集的排序順序,請呼叫[SetCurrentIndex](#setcurrentindex)。

使用`CDaoQueryDef`指標打開記錄集時,使用*m_strSort*不起作用。

有關相關信息,請參閱 DAO 説明中的主題"排序屬性"。

## <a name="cdaorecordsetmove"></a><a name="move"></a>CDao 記錄集::移動

調用此成員函數以定位當前記錄中的記錄集*lRows*記錄。

```
virtual void Move(long lRows);
```

### <a name="parameters"></a>參數

*lRows*<br/>
要向前或向後移動的記錄數。 正值向前移動,接近記錄集的末尾。 負值向後移動,向起點移動。

### <a name="remarks"></a>備註

您可以向前或向後移動。 `Move( 1 )`等效於`MoveNext`與`Move( -1 )`等效於`MovePrev`。

> [!CAUTION]
> 如果記錄集沒有`Move`記錄,則調用任何函數都會引發異常。 通常,調用`IsBOF``IsEOF`Move 操作之前,以確定記錄集是否有任何記錄。 呼叫`Open``Requery`或 後,請`IsBOF`呼`IsEOF`叫或 。

> [!NOTE]
> 如果捲軸紀錄集的開頭`IsBOF`或結尾 (或`IsEOF`傳回非零),則呼`Move`叫`CDaoException`。

> [!NOTE]
> 如果在更新或添加當前記錄`Move`時調用任何函數,則更新將丟失,而不會發出警告。

當您調用`Move`僅轉發滾動快照時 *,lRows*參數必須是正整數,不允許使用書籤,因此您只能向前移動。

要在記錄中創建第一條、最後記錄、上一條或上一條記錄,請`MoveFirst`調用`MoveLast``MoveNext`、、`MovePrev`或成員函數。

有關相關信息,請參閱 DAO 説明中的「移動方法」和「移動第一、移動最後一個、移動下一個、移動上一個方法」的主題。

## <a name="cdaorecordsetmovefirst"></a><a name="movefirst"></a>CDao 記錄集::先移動

調用此成員函數以使記錄集中的第一個記錄(如果有)成為當前記錄。

```cpp
void MoveFirst();
```

### <a name="remarks"></a>備註

打開記錄集后,不必`MoveFirst`立即調用。 此時,第一條記錄(如果有)自動是當前記錄。

> [!CAUTION]
> 如果記錄集沒有`Move`記錄,則調用任何函數都會引發異常。 通常,調用`IsBOF``IsEOF`Move 操作之前,以確定記錄集是否有任何記錄。 呼叫`Open``Requery`或 後,請`IsBOF`呼`IsEOF`叫或 。

> [!NOTE]
> 如果在更新或添加當前記錄`Move`時調用任何函數,則更新將丟失,而不會發出警告。

使用`Move`函數在不應用條件的情況下從記錄移動到記錄。 使用 Find 操作尋找滿足特定條件的動態集類型或快照類型記錄集物件中的記錄。 要在表型態記錄集物件中尋找紀錄,請呼叫`Seek`。

如果記錄集引用表類型的記錄集,則移動遵循表的當前索引。 可以使用基礎 DAO 物件的 Index 屬性設置當前索引。 如果未設置當前索引,則未定義返回的記錄的順序。

如果基於`MoveLast`SQL 查詢或查詢def對記錄集物件進行調用,則強制完成查詢,並且記錄集物件已完全填充。

不能使用僅轉發`MoveFirst`滾`MovePrev`動 快照調用 或 成員函數。

要向前或向後移動記錄集物件中目前紀錄的位置特定數量的記錄,請呼叫`Move`。

有關相關信息,請參閱 DAO 説明中的「移動方法」和「移動第一、移動最後一個、移動下一個、移動上一個方法」的主題。

## <a name="cdaorecordsetmovelast"></a><a name="movelast"></a>CDao 記錄集::移動上次

調用此成員函數,使記錄中的最後一條記錄(如果有)成為當前記錄。

```cpp
void MoveLast();
```

### <a name="remarks"></a>備註

> [!CAUTION]
> 如果記錄集沒有`Move`記錄,則調用任何函數都會引發異常。 通常,調用`IsBOF``IsEOF`Move 操作之前,以確定記錄集是否有任何記錄。 呼叫`Open``Requery`或 後,請`IsBOF`呼`IsEOF`叫或 。

> [!NOTE]
> 如果在更新或添加當前記錄`Move`時調用任何函數,則更新將丟失,而不會發出警告。

使用`Move`函數在不應用條件的情況下從記錄移動到記錄。 使用 Find 操作尋找滿足特定條件的動態集類型或快照類型記錄集物件中的記錄。 要在表型態記錄集物件中尋找紀錄,請呼叫`Seek`。

如果記錄集引用表類型的記錄集,則移動遵循表的當前索引。 可以使用基礎 DAO 物件的 Index 屬性設置當前索引。 如果未設置當前索引,則未定義返回的記錄的順序。

如果基於`MoveLast`SQL 查詢或查詢def對記錄集物件進行調用,則強制完成查詢,並且記錄集物件已完全填充。

要向前或向後移動記錄集物件中目前紀錄的位置特定數量的記錄,請呼叫`Move`。

有關相關信息,請參閱 DAO 説明中的「移動方法」和「移動第一、移動最後一個、移動下一個、移動上一個方法」的主題。

## <a name="cdaorecordsetmovenext"></a><a name="movenext"></a>CDao 記錄集::移動下一個

調用此成員函數以使記錄集中的下一條記錄成為當前記錄。

```cpp
void MoveNext();
```

### <a name="remarks"></a>備註

建議您在嘗試移動到上一`IsBOF`條記錄之前調用。 呼叫`MovePrev`將`CDaoException`引發`IsBOF`if 傳回非零,指示您已在第一個記錄之前滾動,或者記錄集未選擇任何記錄。

> [!CAUTION]
> 如果記錄集沒有`Move`記錄,則調用任何函數都會引發異常。 通常,調用`IsBOF``IsEOF`Move 操作之前,以確定記錄集是否有任何記錄。 呼叫`Open``Requery`或 後,請`IsBOF`呼`IsEOF`叫或 。

> [!NOTE]
> 如果在更新或添加當前記錄`Move`時調用任何函數,則更新將丟失,而不會發出警告。

使用`Move`函數在不應用條件的情況下從記錄移動到記錄。 使用 Find 操作尋找滿足特定條件的動態集類型或快照類型記錄集物件中的記錄。 要在表型態記錄集物件中尋找紀錄,請呼叫`Seek`。

如果記錄集引用表類型的記錄集,則移動遵循表的當前索引。 可以使用基礎 DAO 物件的 Index 屬性設置當前索引。 如果未設置當前索引,則未定義返回的記錄的順序。

要向前或向後移動記錄集物件中目前紀錄的位置特定數量的記錄,請呼叫`Move`。

有關相關信息,請參閱 DAO 説明中的「移動方法」和「移動第一、移動最後一個、移動下一個、移動上一個方法」的主題。

## <a name="cdaorecordsetmoveprev"></a><a name="moveprev"></a>CDao記錄集::MovePrev

調用此成員函數以使記錄中以前的記錄成為當前記錄。

```cpp
void MovePrev();
```

### <a name="remarks"></a>備註

建議您在嘗試移動到上一`IsBOF`條記錄之前調用。 呼叫`MovePrev`將`CDaoException`引發`IsBOF`if 傳回非零,指示您已在第一個記錄之前滾動,或者記錄集未選擇任何記錄。

> [!CAUTION]
> 如果記錄集沒有`Move`記錄,則調用任何函數都會引發異常。 通常,調用`IsBOF``IsEOF`Move 操作之前,以確定記錄集是否有任何記錄。 呼叫`Open``Requery`或 後,請`IsBOF`呼`IsEOF`叫或 。

> [!NOTE]
> 如果在更新或添加當前記錄`Move`時調用任何函數,則更新將丟失,而不會發出警告。

使用`Move`函數在不應用條件的情況下從記錄移動到記錄。 使用 Find 操作尋找滿足特定條件的動態集類型或快照類型記錄集物件中的記錄。 要在表型態記錄集物件中尋找紀錄,請呼叫`Seek`。

如果記錄集引用表類型的記錄集,則移動遵循表的當前索引。 可以使用基礎 DAO 物件的 Index 屬性設置當前索引。 如果未設置當前索引,則未定義返回的記錄的順序。

不能使用僅轉發`MoveFirst`滾`MovePrev`動 快照調用 或 成員函數。

要向前或向後移動記錄集物件中目前紀錄的位置特定數量的記錄,請呼叫`Move`。

有關相關信息,請參閱 DAO 説明中的「移動方法」和「移動第一、移動最後一個、移動下一個、移動上一個方法」的主題。

## <a name="cdaorecordsetopen"></a><a name="open"></a>CDao 記錄集::開啟

必須調用此成員函數才能檢索記錄集的記錄。

```
virtual void Open(
    int nOpenType = AFX_DAO_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    int nOptions = 0);

virtual void Open(
    CDaoTableDef* pTableDef,
    int nOpenType = dbOpenTable,
    int nOptions = 0);

virtual void Open(
    CDaoQueryDef* pQueryDef,
    int nOpenType = dbOpenDynaset,
    int nOptions = 0);
```

### <a name="parameters"></a>參數

*N 開放類型*<br/>
下列其中一個值：

- `dbOpenDynaset`具有雙向滾動的動態集類型記錄集。 這是預設值。

- `dbOpenTable`具有雙向滾動的表類型記錄集。

- `dbOpenSnapshot`具有雙向滾動的快照類型記錄集。

*lpszSQL*<br/>
包含以下的字串指標:

- NULL指標。

- 一個或多個表def和/或查詢defs的名稱(逗號分隔)。

- SQL **SELECT**語句(可選使用 SQL **WHERE**或**ORDERBY**子句)。

- 傳遞查詢。

*n 選項*<br/>
下面列出的一個或多個選項。 預設值為 0。 可能的值如下：

- `dbAppendOnly`您只能追加新記錄(僅限動態設置類型記錄集)。 此選項表示實際上只能追加記錄。 MFC ODBC 資料庫類具有僅追加選項,允許檢索和追加記錄。

- `dbForwardOnly`記錄集是僅轉發滾動快照。

- `dbSeeChanges`如果其他使用者正在更改您正在編輯的數據,則產生異常。

- `dbDenyWrite`其他使用者無法修改或添加記錄。

- `dbDenyRead`其他用戶無法查看記錄(僅限表類型記錄集)。

- `dbReadOnly`您只能查看記錄;其他使用者可以修改它們。

- `dbInconsistent`允許不一致的更新(僅限動態集類型記錄集)。

- `dbConsistent`僅允許一致的更新(僅限動態集類型記錄集)。

> [!NOTE]
> 常量是`dbConsistent``dbInconsistent`互斥的。 您可以使用其中一個或另一個,但不能同時在給定實例中使用`Open`。

*pTableDef*<br/>
指向[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)物件的指標。 此版本僅適用於表類型的記錄集。 使用此選項時,`CDaoDatabase`不使用用於建構`CDaoRecordset`的指標;而是使用表def所在的資料庫。

*pQueryDef*<br/>
指向[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)物件的指標。 此版本僅適用於動態集類型和快照類型記錄集。 使用此選項時,`CDaoDatabase`不使用用於建構`CDaoRecordset`的指標;而是使用查詢def所在的資料庫。

### <a name="remarks"></a>備註

在調用`Open`之前,必須構造記錄集物件。 有幾個方式可做到這點：

- 構造記錄集物件時,將指標傳遞給已打開`CDaoDatabase`的物件。

- 構造記錄集物件時,將指標傳遞給未打開`CDaoDatabase`的物件。 記錄集將打開物件`CDaoDatabase`,但不會在記錄集物件關閉時關閉該物件。

- 建構記錄集物件時,傳遞 NULL 指標。 記錄集物件調用`GetDefaultDBName`以獲取 Microsoft Access 的名稱。要打開的 MDB 檔。 然後,記錄集打開物件`CDaoDatabase`,只要記錄集處於打開狀態,它就會保持打開狀態。 當您調用`Close`記錄集時`CDaoDatabase`, 物件也會關閉。

    > [!NOTE]
    >  當記錄集打開物件時`CDaoDatabase`,它將打開具有非獨佔訪問許可權的數據源。

對於使用`Open`*lpszSQL*參數的版本,一旦記錄集打開,您可以通過多種方式之一檢索記錄。 第一個選項是在您的`DoFieldExchange`中具有 DFX 函數。 第二個選項是通過調用`GetFieldValue`成員函數使用動態綁定。 這些選項可以單獨實現或組合實現。 如果它們合併在一起,您必須在呼叫 時自己傳遞 SQL`Open`語句 。

當您使用物件中`Open`傳遞位置的第二個`CDaoTableDef`版本 時,生成的列將可供`DoFieldExchange`您通過 DFX 機制綁定,和/或通過`GetFieldValue`動態綁定。

> [!NOTE]
> 只能使用物件`CDaoTableDef`對`Open`表類型的記錄集進行調用。

當您`Open`使用`CDaoQueryDef`在 物件中傳遞的位置的第三個版本時,將執行該查詢,並且生成的列將可供`DoFieldExchange`您通過 DFX 機制綁定,和/或通過`GetFieldValue`動態綁定。

> [!NOTE]
> 只能使用`CDaoQueryDef`物件調`Open`用 動態集類型和快照類型記錄集。

對於使用`lpszSQL`參數`Open`的第一個版本,將根據下表中顯示的條件選擇記錄。

|`lpszSQL` 參數的值|選取的紀錄由|範例|
|--------------------------------------|----------------------------------------|-------------|
|NULL|返回`GetDefaultSQL`的字串。||
|一個或多個表def和/或查詢def名稱的逗號分隔清單。|已從所有的`DoFieldExchange`欄位 。|`"Customer"`|
|**從**表列表中**選擇**欄清單|指定表def 和/或查詢def 的指定列。|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

通常的程式是將 NULL`Open`傳遞給 。在這種情況下,`Open`調`GetDefaultSQL`用 ,ClassWizard`CDaoRecordset`在創建 派生類時生成的可重寫成員函數。 此值提供在 ClassWizard 中指定的表def 和/或查詢def 名稱。 您可以改為在*lpszSQL*參數中指定其他資訊。

無論您透過什麼,`Open`都會建構查詢的最終 SQL 字串(該字串可能將 SQL **WHERE**和**ORDERBY**子句追加到您傳遞的*lpszSQL*字串上),然後執行查詢。 您可以通過呼`GetSQL``Open`叫 後呼叫 來檢查建構的字串。

記錄集類的欄位數據成員綁定到選取資料的列。 如果返回任何記錄,則第一條記錄將成為當前記錄。

如果要為紀錄集設定選項(如篩選器或排序)設定`m_strSort``m_strFilter`或 建構紀錄集物件之後,但在`Open`調用 之前設定 。 如果要在紀錄集開啟後刷新記錄集中的記錄,請呼叫`Requery`。

如果調用`Open`動態集類型或快照類型記錄集,或者數據源引用表示附加表的 SQL 語句或表def,則無法用於類型參數;如果資料來源引用的 SQL 語句或`dbOpenTable`表def 表示附加表,則無法用於類型參數;如果資料來源引用的 SQL 語句或表def 表示附加表,則無法用於類型參數。如果這樣做,MFC 會引發異常。 要確定 tabledef 物件是否表示附加的表,請建立[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)物件並調用其[GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect)成員函數。

如果要在`dbSeeChanges`編輯或刪除同一記錄時捕獲其他使用者或其他程式在電腦上所做的更改,請使用該標誌。 例如,如果兩個用戶開始編輯同一記錄,則調用`Update`成員函數的第一個使用者將成功。 當`Update`第二個使用者呼叫時,`CDaoException`將引發 。 同樣,如果第二個使用者嘗試呼叫`Delete`以刪除記錄,並且第一個使用者已更改該記錄,則會`CDaoException`發生 。

通常,如果使用者在更新時收到`CDaoException`此內容,則代碼應刷新欄位的內容並檢索新修改的值。 如果在刪除過程中出現異常,則代碼可能會向使用者顯示新的記錄數據,並顯示指示數據最近已更改的消息。 此時,您的代碼可以請求確認使用者仍希望刪除記錄。

> [!TIP]
> 當應用程式通過從 ODBC`dbForwardOnly`資料來源 開啟的記錄集進行單次傳遞時,使用僅轉發滾動選項( ) 來提高性能。

有關相關信息,請參閱 DAO 説明中的主題"打開記錄集方法」。

## <a name="cdaorecordsetrequery"></a><a name="requery"></a>CDao 記錄集::重新查詢

調用此成員函數以重建(刷新)記錄集。

```
virtual void Requery();
```

### <a name="remarks"></a>備註

如果返回任何記錄,則第一條記錄將成為當前記錄。

為了使記錄集反映您或其他使用者對數據源進行的添加和刪除,必須通過調用`Requery`來重新生成記錄集。 如果記錄集是動態集,它會自動反映您或其他使用者對其現有記錄(但不是添加)進行的更新。 如果記錄集是快照,則必須調用`Requery`以反映其他使用者的編輯以及添加和刪除。

對於動態集或快照,`Requery`請隨時呼叫要使用參數值重建記錄集。 在調用`Requery`[之前設置新的](#m_strfilter)篩選器或排序,m_strFilter和[m_strSort。](#m_strsort) 通過在調用`Requery`之前將新值分配給參數數據成員來設置新參數。

如果重建記錄集的嘗試失敗,記錄集將關閉。 在調用`Requery`之前,可以通過調用[CanRestart](#canrestart)成員函數來確定是否可以重新查詢記錄集。 `CanRestart`不能保證會`Requery`成功。

> [!CAUTION]
> 僅在`Requery`您致電`Open`后才能 致電。

> [!NOTE]
> 呼叫[重新查詢](#requery)會更改 DAO 書籤。

如果調用`Requery``CanRestart`返回 0,則不能調用動態集類型或快照類型記錄集,也不能在表類型記錄集中使用它。

如果兩`IsBOF``IsEOF`者 都和`Requery`調用 後返回非零,則查詢未返回任何記錄,並且記錄集將不包含任何數據。

有關相關信息,請參閱 DAO 説明中的"重新查詢方法"主題。

## <a name="cdaorecordsetseek"></a><a name="seek"></a>CDao 記錄集::尋找

調用此成員函數以查找索引表類型記錄集物件中的記錄,該物件滿足當前索引的指定條件,並使該記錄成為當前記錄。

```
BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKey1,
    COleVariant* pKey2 = NULL,
    COleVariant* pKey3 = NULL);

BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKeyArray,
    WORD nKeys);
```

### <a name="parameters"></a>參數

*lpsz比較*<br/>
以下字串表達式之一\<:"<"、"\""""\"""""">"或">"。

*pKey1*<br/>
指向[COleVariant 的](../../mfc/reference/colevariant-class.md)指標,其值對應於索引中的第一個字段。 必要。

*pKey2*<br/>
指向`COleVariant`其值對應於索引中的第二個字段(如果有)的指標。 預設值為 NULL。

*pKey3*<br/>
指向`COleVariant`其值對應於索引中的第三個字段(如果有)的指標。 預設值為 NULL。

*pKeyarray*<br/>
指向變數組的指標。 陣列大小對應於索引中的欄位數。

*N 鍵*<br/>
與陣列大小對應的整數,即索引中的欄位數。

> [!NOTE]
> 請勿在鍵中指定通配符。 通配符將導致`Seek`返回沒有匹配的記錄。

### <a name="return-value"></a>傳回值

如果找到匹配的記錄,則非零,否則為 0。

### <a name="remarks"></a>備註

使用第`Seek`二個(陣列)版本來處理四個或更多欄位的索引。

`Seek`支援在表類型的記錄集上搜索高性能索引。 在調用`SetCurrentIndex``Seek`之前,必須通過調用 來設置當前索引。 如果索引識別非唯一鍵欄位或欄位,`Seek`則查找滿足條件的第一個記錄。 如果不設置索引,將引發異常。

請注意,如果不創建 UNICODE 記錄集,則必須顯`COleVariant`式聲明 物件為 ANSI。 這可以透過[COleVariant:COlevariant(lpszSrc,](../../mfc/reference/colevariant-class.md#colevariant) ** ** *lpszSrc* **,** *vtSrc)***)** 形式的建構函數與*vtSrc*設定為`VT_BSTRT``COleVariant`(ANSI) 或使用 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) *(lpszSrc,* **,** *vtSrc)***)** 與*vtSrc*設定為`VT_BSTRT`。** **

呼叫`Seek`時 ,傳遞一個或多個鍵值和比較運算\<符 ("<"、"\"""""""""""">"或">")。 `Seek`搜尋指定的鍵欄位,並找到滿足*lpsz比較*和*pKey1*指定的條件的第一個記錄。 找到後,`Seek`傳回非零,並使該記錄成為目前的記錄。 如果`Seek`找不到符合項`Seek`, 則傳回零,並且目前記錄未定義。 直接使用 DAO 時,必須顯式檢查 NoMatch 屬性。

如果`lpszComparison`為"*"、">"或">",`Seek`則 從索引的開頭開始。 如果*lpsz比較*是"<"或"<`Seek`+", 則從索引的末尾開始,然後向後搜索,除非末尾有重複的索引條目。 在這種情況下,`Seek`從索引末尾的重複索引條目之間的任意條目開始。

使用`Seek`時不必有當前記錄。

要查找滿足特定條件的動態集類型或快照類型記錄集中的記錄,請使用 Find 操作。 要包括所有記錄,而不僅僅是滿足特定條件的記錄,請使用 Move 操作從記錄移動到記錄。

不能調用`Seek`任何類型的附加表,因為附加的表必須作為動態集類型或快照類型記錄集打開。 但是,如果您調用`CDaoDatabase::Open`直接打開可安裝的 ISAM 資料庫,則`Seek`可以調用 該資料庫中的表,儘管性能可能很慢。

有關相關信息,請參閱 DAO 説明中的主題"查找方法"

## <a name="cdaorecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a>CDao 記錄集::設定絕對位置

設置記錄集物件當前記錄的相對記錄編號。

```cpp
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>參數

*l定位*<br/>
對應於記錄集中當前記錄的盤位位置。

### <a name="remarks"></a>備註

通過`SetAbsolutePosition`調用,您可以根據當前記錄指標在動態集類型或快照類型記錄集中的位級位置定位到特定記錄。 您還可以透過調用[Get 絕對位置](#getabsoluteposition)來確定目前記錄編號。

> [!NOTE]
> 此成員函數僅適用於動態集類型和快照類型記錄集。

基礎 DAO 物件的絕對位置屬性值是零基的;設置為 0 是指記錄集中的第一個記錄。 設置大於填充記錄數的值會導致 MFC 引發異常。 您可以通過調`GetRecordCount`用 成員函數來確定記錄集中填充的記錄數。

如果刪除當前記錄,則不定義絕對位置屬性值,如果引用,MFC 將引發異常。 新記錄將添加到序列的末尾。

> [!NOTE]
> 此屬性不用作代理記錄編號。 書籤仍然是保留和返回到給定位置的推薦方式,是跨支援書籤的所有類型的記錄集物件定位當前記錄的唯一方法。 特別是,當刪除給定記錄之前的記錄時,給定記錄的位置會發生變化。 如果再次重新創建記錄集,也不能保證給定記錄集具有相同的絕對位置,因為除非使用**ORDERBY**子句使用 SQL 語句創建記錄集中的單個記錄的順序不保證。

有關相關信息,請參閱 DAO 説明中的「絕對位置屬性」 主題。

## <a name="cdaorecordsetsetbookmark"></a><a name="setbookmark"></a>CDao 記錄集::設定書籤

調用此成員函數將記錄集放置在包含指定書籤的記錄上。

```cpp
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>參數

*瓦爾布克馬克*<br/>
包含特定記錄的書籤值的[COleVariant](../../mfc/reference/colevariant-class.md)物件。

### <a name="remarks"></a>備註

創建或打開記錄集物件時,其每個記錄都已具有唯一的書籤。 可以通過調`GetBookmark`用 該值並將值`COleVariant`保存到 對象來檢索當前記錄的書籤。 稍後,可以使用保存的書籤值調用`SetBookmark`該記錄。

> [!NOTE]
> 呼叫[重新查詢](#requery)會更改 DAO 書籤。

請注意,如果不創建 UNICODE 記錄`COleVariant`集, 則必須顯式聲明該物件為 ANSI。 這可以透過[COleVariant:COlevariant(lpszSrc,](../../mfc/reference/colevariant-class.md#colevariant) ** ** *lpszSrc* **,** *vtSrc)***)** 形式的建構函數與*vtSrc*設定為`VT_BSTRT``COleVariant`(ANSI) 或使用 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) *(lpszSrc,* **,** *vtSrc)***)** 與*vtSrc*設定為`VT_BSTRT`。** **

有關相關信息,請參閱 DAO 説明中的「書籤屬性」和「可書籤屬性」 的主題。

## <a name="cdaorecordsetsetcachesize"></a><a name="setcachesize"></a>CDao 記錄集::設定快取大小

調用此成員函數以設置要快取的記錄數。

```cpp
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>參數

*lSize*<br/>
指定記錄數。 典型值為 100。 設置為 0 將關閉緩存。 設置必須介於 5 和 1200 條記錄之間。 緩存可能使用大量記憶體。

### <a name="remarks"></a>備註

快取是本地記憶體中的一個空間,用於保存最近從伺服器檢索的數據,如果應用程式運行時將再次請求數據。 數據快取提高了應用程式透過動態集類型記錄集物件從遠端伺服器檢索資料的性能。 請求數據時,Microsoft Jet 資料庫引擎首先檢查緩存中請求的數據,而不是從伺服器檢索數據,這需要更多的時間。 不來自 ODBC 資料來源的資料不會儲存在快取中。

任何 ODBC 資料來源(如附加的表)都可以具有本地快取。 要創建緩存,請從遠端資料源打開記錄集物件,調用`SetCacheSize`和`SetCacheStart`成員函數,然後調用`FillCache`成員函數或使用 Move 操作之一單步執行記錄。 成員函數的`SetCacheSize` *lSize*參數可以基於應用程式一次可以使用的記錄數。 例如,如果使用記錄集作為要顯示在螢幕上的數據的來源,則可以將`SetCacheSize`*lSize*參數傳遞為 20,以一次顯示 20 條記錄。

有關相關信息,請參閱 DAO 説明中的主題「緩存大小、緩存啟動屬性」。

## <a name="cdaorecordsetsetcachestart"></a><a name="setcachestart"></a>CDao 記錄集::設定快取開始

調用此成員函數以指定要緩存的記錄集中第一個記錄的書籤。

```cpp
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>參數

*瓦爾布克馬克*<br/>
指定要緩存的記錄集中第一個記錄的書籤的[COleVariant。](../../mfc/reference/colevariant-class.md)

### <a name="remarks"></a>備註

您可以使用`SetCacheStart`成員函數的*varBookmark*參數的任何記錄的書籤值。 使用當前記錄創建要啟動緩存的記錄,使用[SetBookmark](#setbookmark)為該記錄建立書籤,並將書籤值作為成員函`SetCacheStart`數的 參數傳遞。

Microsoft Jet 資料庫引擎從快取請求快取範圍內的記錄,並且請求伺服器在緩存範圍之外的記錄。

從緩存中檢索的記錄不會反映其他用戶同時對源數據所做的更改。

要強制更新所有緩存的數據,請傳遞`SetCacheSize`*lSize*參數為 0,`SetCacheSize`使用最初請求的緩存大小再次調用,`FillCache`然後調用 成員函數。

請注意,如果不創建 UNICODE 記錄`COleVariant`集, 則必須顯式聲明該物件為 ANSI。 這可以透過[COleVariant:COlevariant(lpszSrc,](../../mfc/reference/colevariant-class.md#colevariant) ** ** *lpszSrc* **,** *vtSrc)***)** 形式的建構函數與*vtSrc*設定為`VT_BSTRT``COleVariant`(ANSI) 或使用 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) *(lpszSrc,* **,** *vtSrc)***)** 與*vtSrc*設定為`VT_BSTRT`。** **

有關相關信息,請參閱 DAO 説明中的主題「緩存大小、緩存啟動屬性」。

## <a name="cdaorecordsetsetcurrentindex"></a><a name="setcurrentindex"></a>CDao 記錄集::設定目前索引

調用此成員函數以在表類型記錄集上設置索引。

```cpp
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>參數

*lpszIndex*<br/>
包含要設置的索引名稱的指標。

### <a name="remarks"></a>備註

基表中的記錄不會按任何特定順序存儲。 設置索引會更改從資料庫返回的記錄的順序,但不會影響記錄的存儲順序。 必須已定義指定的索引。 如果嘗試使用不存在的索引物件,或者在調用[Seek](#seek)時未設置索引,則 MFC 將引發異常。

您可以通過調用[CDaoTableDef::createIndex](../../mfc/reference/cdaotabledef-class.md#createindex)並將新索引追加到基礎表def的索引集合,通過調用[CDaoTableDef:::append,](../../mfc/reference/cdaotabledef-class.md#append)然後重新打開記錄集,為表創建新索引。

從表類型記錄集返回的記錄只能由為基礎表def定義的索引排序。 要按其他排序對記錄進行排序,可以使用存儲在[CDaoRecordset::m_strSort](#m_strsort)中的 SQL **ORDERBY**子句打開動態集類型或快照類型記錄集。

有關相關信息,請參閱 DAO 説明中的主題"索引物件"和定義"當前索引"。

## <a name="cdaorecordsetsetfielddirty"></a><a name="setfielddirty"></a>CDao 記錄集::設定欄位臟

呼叫此成員函數將記錄集的欄位數據成員標記為已更改或未更改。

```cpp
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>參數

*光伏*<br/>
在記錄集或 NULL 中包含欄位資料成員的位址。 如果為 NULL,則記錄集中的所有欄位數據成員將被標記。 (C++ NULL 與資料庫術語中的 Null 不同,這意味著"沒有值"。

*bDirty*<br/>
如果欄位數據成員被標記為「臟」(已更改),則為 TRUE。 否則,如果欄位數據成員被標記為「乾淨」(未更改),則 FALSE。

### <a name="remarks"></a>備註

將欄位標記為未更改可確保不更新該欄位。

框架標記已更改的欄位數據成員,以確保 DAO 記錄欄位交換 (DFX) 機制將它們寫入數據來源上的記錄。 變更欄位的值通常會自動將欄位設定髒,因此您很少需要調用`SetFieldDirty`自己,但有時您可能希望確保無論欄位資料成員中的哪個值如何,都會顯式更新或插入列。 DFX 機制還使用 PSEUDONULL。 有關詳細資訊,請參閱[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用雙緩衝機制,則更改欄位的值不會自動將欄位設置為髒。 在這種情況下,必須顯式將欄位設置為髒。 [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的標誌控制此自動欄位檢查。

> [!NOTE]
> 只在呼叫[「編輯」](#edit)或[「新增 New」](#addnew)後才能呼叫此成員函數。

將 NULL 用於函數的第一個參數將函數應用`outputColumn`於所有欄位,而不是將**的**`CDaoFieldExchange`欄位應用於 。 例如,呼叫

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

將僅`outputColumn`將欄位設定為 NULL;**參數**欄位將不受影響。

要處理**參數**,您必須提供要處理的單個**參數**的實際位址,例如:

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

這表示您不能將所有**參數**欄位設定為 NULL,就像對欄`outputColumn`位一樣 。

`SetFieldDirty`通過`DoFieldExchange`。

## <a name="cdaorecordsetsetfieldnull"></a><a name="setfieldnull"></a>CDao 記錄集::SetFieldNull

呼叫此成員函數將記錄集的欄位資料成員標記為 Null(具體沒有值)或非 Null。

```cpp
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>參數

*光伏*<br/>
在記錄集或 NULL 中包含欄位資料成員的位址。 如果為 NULL,則記錄集中的所有欄位數據成員將被標記。 (C++ NULL 與資料庫術語中的 Null 不同,這意味著"沒有值"。

*bNull*<br/>
如果要將欄位數據成員標記為無值(空),則非零。 否則 0 如果欄位數據成員被標記為非 Null。

### <a name="remarks"></a>備註

`SetFieldNull`用於在機制中綁定的`DoFieldExchange`欄位。

將新記錄添加到記錄集時,所有欄位數據成員最初都設置為 Null 值,並標記為「臟」(已更改)。 從資料源檢索記錄時,其列要麼已有值,要麼為 Null。 如果不適合使欄位為 Null,則引發[「CDaoException」。。](../../mfc/reference/cdaoexception-class.md)

例如,如果您正在使用雙緩衝機制,如果您特別希望將當前記錄的欄位指定為沒有值,則使用*bNull*設定為 TRUE`SetFieldNull`的呼叫將其標記為 Null。 如果欄位以前標記為 Null,現在您希望為其提供值,只需設置其新值即可。 不必刪除帶有`SetFieldNull`的 Null 標誌。 要確定此欄位是否允許為空,請呼叫[IsFieldable 。](#isfieldnullable)

如果不使用雙緩衝機制,則更改欄位的值不會自動將欄位設置為臟和非 Null。 您必須專門設定欄位臟和非 Null。 [m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的標誌控制此自動欄位檢查。

DFX 機制使用 PSEUDONULL。 有關詳細資訊,請參閱[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

> [!NOTE]
> 只在呼叫[「編輯」](#edit)或[「新增 New」](#addnew)後才能呼叫此成員函數。

將 NULL 用於函數的第一個參數將僅將函數`outputColumn`應用於欄位,而不是將**參數**欄位`CDaoFieldExchange`應用於 。 例如,呼叫

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

將僅`outputColumn`將欄位設定為 NULL;**參數**欄位將不受影響。

## <a name="cdaorecordsetsetfieldvalue"></a><a name="setfieldvalue"></a>CDao 記錄集::設定場值

呼叫此成員函數以按任位或更改字串的值設置欄位的值。

```
virtual void SetFieldValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetFieldValue(
    int nIndex,
    const COleVariant& varValue);

void SetFieldValue(
    LPCTSTR lpszName,
    LPCTSTR lpszValue);

void SetFieldValue(
    int nIndex,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
指向包含欄位名稱的字串的指標。

*varValue*<br/>
對包含欄位內容值的[COleVariant](../../mfc/reference/colevariant-class.md)物件的引用。

*nIndex*<br/>
表示記錄集「欄位」集合中欄位的整數(從零開始)。

*lpszValue*<br/>
指向包含欄位內容值的字串的指標。

### <a name="remarks"></a>備註

使用`SetFieldValue`和[GetFieldValue](#getfieldvalue)在執行時動態綁定欄位,而不是使用[DoFieldExchange](#dofieldexchange)機制對列進行靜態綁定。

請注意,如果不創建 UNICODE 記錄集,則必須使用`SetFieldValue``COleVariant`不包含 參數的 窗體,或者`COleVariant`必須顯式聲明 該物件 ANSI。 這可以透過[COleVariant:COlevariant(lpszSrc,](../../mfc/reference/colevariant-class.md#colevariant) ** ** *lpszSrc* **,** *vtSrc)***)** 形式的建構函數與*vtSrc*設定為`VT_BSTRT``COleVariant`(ANSI) 或使用 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) *(lpszSrc,* **,** *vtSrc)***)** 與*vtSrc*設定為`VT_BSTRT`。** **

有關相關信息,請參閱 DAO 説明中的「欄位物件」和「值屬性」主題。

## <a name="cdaorecordsetsetfieldvaluenull"></a><a name="setfieldvaluenull"></a>CDao 記錄集:設定場值 Null

呼叫此成員函數將欄位設定為 Null 值。

```cpp
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
記錄集中的欄位的索引,用於按零基索引查找。

*lpsz名稱*<br/>
記錄集中的欄位的名稱,用於按名稱查找。

### <a name="remarks"></a>備註

C++ NULL 與 Null 不同,在資料庫術語中,Null 表示"沒有值"。

有關相關信息,請參閱 DAO 説明中的「欄位物件」和「值屬性」主題。

## <a name="cdaorecordsetsetlockingmode"></a><a name="setlockingmode"></a>CDao 記錄集::設定鎖定模式

調用此成員函數以設置記錄集的鎖定類型。

```cpp
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>參數

*b:00*<br/>
指示鎖定類型的標誌。

### <a name="remarks"></a>備註

當悲觀鎖定生效時,包含您編輯的記錄的 2K 頁面在`Edit`調用 成員函數後立即鎖定。 當您調用`Update``Close`或成員函數或任何「移動」或「查找」操作時,頁面將解鎖。

當樂觀鎖定生效時,包含記錄的 2K 頁面僅`Update`在使用成員函數更新記錄時鎖定。

如果頁面被鎖定,則其他用戶無法編輯同一頁上的記錄。 如果調用`SetLockingMode`並傳遞非零值,而另一個使用者已鎖定頁面,則調`Edit`用 時將引發異常。 其他用戶可以從鎖定的頁面讀取數據。

如果使用零`SetLockingMode`值進行調用,並在頁面`Update`被 其他用戶鎖定時稍後調用,則會發生異常。 要查看其他使用者對記錄所做的更改(並丟失更改),請使用當前記錄的書籤值調`SetBookmark`用 成員函數。

使用 ODBC 數據源時,鎖定模式始終樂觀。

## <a name="cdaorecordsetsetparamvalue"></a><a name="setparamvalue"></a>CDao 記錄集::SetParamValue

調用此成員函數以在運行時在記錄集中設置參數的值。

```
virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);

virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
參數在查詢def的參數集合中的數值位置。

*var*<br/>
要設置的值;請參閱備註。

*lpsz名稱*<br/>
要設置其值的參數的名稱。

### <a name="remarks"></a>備註

參數必須已作為記錄集的 SQL 字串的一部分建立。 您可以按名稱或其集合中的索引位置訪問參數。

指定要設定為`COleVariant`物件的值。 有關物件`COleVariant`在物件中設定所需值和類型的資訊,請參閱類[COleVariant](../../mfc/reference/colevariant-class.md)。 請注意,如果不創建 UNICODE 記錄`COleVariant`集, 則必須顯式聲明該物件為 ANSI。 這可以透過[COleVariant:COlevariant(lpszSrc,](../../mfc/reference/colevariant-class.md#colevariant) ** ** *lpszSrc* **,** *vtSrc)***)** 形式的建構函數與*vtSrc*設定為`VT_BSTRT``COleVariant`(ANSI) 或使用 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) *(lpszSrc,* **,** *vtSrc)***)** 與*vtSrc*設定為`VT_BSTRT`。** **

## <a name="cdaorecordsetsetparamvaluenull"></a><a name="setparamvaluenull"></a>CDao 記錄集::SetParamValueNull

呼叫此成員函數將參數設定為 Null 值。

```cpp
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
記錄集中的欄位的索引,用於按零基索引查找。

*lpsz名稱*<br/>
記錄集中的欄位的名稱,用於按名稱查找。

### <a name="remarks"></a>備註

C++ NULL 與 Null 不同,在資料庫術語中,Null 表示"沒有值"。

## <a name="cdaorecordsetsetpercentposition"></a><a name="setpercentposition"></a>CDao 記錄集::設定百分比位置

調用此成員函數可設置一個值,該值根據記錄集中記錄中的記錄的百分比更改記錄集物件中當前記錄的大致位置。

```cpp
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>參數

*f 定位*<br/>
介於 0 與 100 之間的數字。

### <a name="remarks"></a>備註

使用動態集類型或快照類型記錄集時,首先通過在調用`SetPercentPosition`之前移動到最後一個記錄來填充記錄集。 如果在完全填充`SetPercentPosition`記錄集之前調用,則移動量與[GetRecordCount](#getrecordcount)的值指示的訪問記錄數相關。 您可以通過調`MoveLast`用 移動到最後一個記錄。

調用`SetPercentPosition`後,與該值對應的近似位置的記錄將成為當前記錄。

> [!NOTE]
> 不`SetPercentPosition`建議調用將當前記錄移動到記錄集中的特定記錄。 請改為調用[SetBookmark](#setbookmark)成員函數。

有關相關信息,請參閱 DAO 説明中的主題"百分比位置屬性」。。

## <a name="cdaorecordsetupdate"></a><a name="update"></a>CDao 記錄集::更新

調用`AddNew``Edit`或成員函數後調用此成員函數。

```
virtual void Update();
```

### <a name="remarks"></a>備註

完成`AddNew``Edit`或操作需要此調用。

`AddNew`並`Edit`準備一個編輯緩衝區,其中添加或編輯的數據被放置到數據源中。 `Update`保存數據。 只會更新標記為或檢測到已更改的欄位。

如果數據源支援事務,則可以將`Update`調用(及其相應的`AddNew``Edit`或調用)作為事務的一部分。

> [!CAUTION]
> 如果在未首先`Update`呼叫`AddNew``Edit`或 的情況下`Update`呼`CDaoException`叫 , 則引發 。 如果呼叫`AddNew``Edit`或,則必須`Update`在調用[MoveNext](#movenext)之前調用或關閉記錄集或數據源連接。 否則,您的更改將丟失,恕不另行通知。

當記錄集物件在多用戶環境中被悲觀鎖定時,記錄從使用到`Edit`更新完成時一直鎖定。 如果記錄集被樂觀地鎖定,則記錄將鎖定,並在資料庫中更新之前與預編輯的記錄進行比較。 如果記錄自調用`Edit`後已更改,`Update`則 操作將失敗,並且 MFC 會引發異常。 您可以使用 變更鎖定`SetLockingMode`模式 。

> [!NOTE]
> 樂觀鎖定始終用於外部資料庫格式,如 ODBC 和可安裝 ISAM。

有關相關信息,請參閱 DAO 説明中的"添加新方法"、"取消更新方法"、"刪除方法"、"上次修改屬性"、"更新方法"和"編輯模式屬性"的主題。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoWorkspace 類別](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)<br/>
