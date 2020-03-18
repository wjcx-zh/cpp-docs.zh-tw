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
ms.openlocfilehash: 96118645aa656e97fcb93a0fd223045208ab03a3
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418787"
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
|[CDaoRecordset：： CDaoRecordset](#cdaorecordset)|建構 `CDaoRecordset` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDaoRecordset：： AddNew](#addnew)|準備加入新記錄。 呼叫[Update](#update)以完成新增。|
|[CDaoRecordset：： CanAppend](#canappend)|如果可以透過[AddNew](#addnew)成員函式將新記錄加入至記錄集，則傳回非零。|
|[CDaoRecordset：： CanBookmark](#canbookmark)|如果記錄集支援書簽，則傳回非零。|
|[CDaoRecordset：： CancelUpdate](#cancelupdate)|取消任何暫止的更新，因為[編輯](#edit)或[AddNew](#addnew)作業。|
|[CDaoRecordset：： CanRestart](#canrestart)|如果可以呼叫重新[查詢](#requery)以再次執行記錄集的查詢，則傳回非零。|
|[CDaoRecordset：： CanScroll](#canscroll)|如果您可以流覽記錄，則傳回非零。|
|[CDaoRecordset：： CanTransact](#cantransact)|如果資料來源支援交易，則傳回非零。|
|[CDaoRecordset：： CanUpdate](#canupdate)|如果可以更新記錄集，則傳回非零（您可以加入、更新或刪除記錄）。|
|[CDaoRecordset：： Close](#close)|關閉記錄集。|
|[CDaoRecordset：:D 刪除](#delete)|從記錄集刪除目前的記錄。 刪除之後，您必須明確地滾動到另一筆記錄。|
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|呼叫以在記錄集的欄位資料成員和資料來源上的對應記錄之間交換資料（雙向）。 實行 DAO 記錄欄位交換（DFX）。|
|[CDaoRecordset：： Edit](#edit)|準備目前記錄的變更。 呼叫 `Update` 以完成編輯。|
|[CDaoRecordset：： FillCache](#fillcache)|針對包含來自 ODBC 資料來源之資料的記錄集物件，填入全部或一部分的本機快取。|
|[CDaoRecordset：： Find](#find)|在符合指定準則並使其記錄目前記錄的動態集型別記錄集中，尋找特定字串的第一個、下一個、上一個或最後一個位置。|
|[CDaoRecordset：： FindFirst](#findfirst)|找出可滿足指定準則並使其記錄目前記錄的動態集類型或快照集類型記錄集中的第一筆記錄。|
|[CDaoRecordset：： FindLast](#findlast)|找出可滿足指定準則並使其記錄目前記錄的動態集型別或快照集型別記錄中的最後一筆記錄。|
|[CDaoRecordset：： FindNext](#findnext)|找出可滿足指定準則並使其記錄目前記錄的動態集類型或快照集類型記錄集中的下一筆記錄。|
|[CDaoRecordset：： FindPrev](#findprev)|尋找符合指定準則並使其記錄目前記錄的動態集類型或快照集類型記錄集中的上一個記錄。|
|[CDaoRecordset：： GetAbsolutePosition](#getabsoluteposition)|傳回記錄集物件的目前記錄號碼。|
|[CDaoRecordset：： GetBookmark](#getbookmark)|傳回值，表示記錄上的書簽。|
|[CDaoRecordset：： GetCacheSize](#getcachesize)|傳回值，指定包含要從 ODBC 資料來源本機快取之資料的動態集類型記錄集內的記錄數目。|
|[CDaoRecordset：： GetCacheStart](#getcachestart)|傳回值，指定要快取之記錄集中第一筆記錄的書簽。|
|[CDaoRecordset：： GetCurrentIndex](#getcurrentindex)|傳回 `CString`，其中包含最近在索引資料表類型 `CDaoRecordset`上使用的索引名稱。|
|[CDaoRecordset：： GetDateCreated](#getdatecreated)|傳回建立 `CDaoRecordset` 物件之基礎資料表的日期和時間|
|[CDaoRecordset：： GetDateLastUpdated](#getdatelastupdated)|傳回對 `CDaoRecordset` 物件之基表的設計所做的最新變更的日期和時間。|
|[CDaoRecordset：： GetDefaultDBName](#getdefaultdbname)|傳回預設資料來源的名稱。|
|[CDaoRecordset：： GetDefaultSQL](#getdefaultsql)|呼叫以取得要執行的預設 SQL 字串。|
|[CDaoRecordset：： GetEditMode](#geteditmode)|傳回值，指出目前記錄的編輯狀態。|
|[CDaoRecordset：： GetFieldCount](#getfieldcount)|傳回值，表示記錄集內的欄位數目。|
|[CDaoRecordset：： Issomapper.getfieldinfo](#getfieldinfo)|傳回有關記錄集中欄位的特定資訊類型。|
|[CDaoRecordset：： GetFieldValue](#getfieldvalue)|傳回記錄集中的欄位值。|
|[CDaoRecordset：： GetIndexCount](#getindexcount)|抓取記錄集基礎的資料表中的索引數目。|
|[CDaoRecordset：： GetIndexInfo](#getindexinfo)|傳回關於索引的各種資訊。|
|[CDaoRecordset：： GetLastModifiedBookmark](#getlastmodifiedbookmark)|用來判斷最近加入或更新的記錄。|
|[CDaoRecordset：： GetLockingMode](#getlockingmode)|傳回值，指出在編輯期間作用中的鎖定類型。|
|[CDaoRecordset：： GetName](#getname)|傳回包含記錄集名稱的 `CString`。|
|[CDaoRecordset：： GetParamValue](#getparamvalue)|抓取儲存在基礎 DAOParameter 物件中的指定參數目前的值。|
|[CDaoRecordset：： GetPercentPosition](#getpercentposition)|傳回目前記錄的位置，以記錄總數的百分比表示。|
|[CDaoRecordset：： GetRecordCount](#getrecordcount)|傳回在記錄集物件中存取的記錄數目。|
|[CDaoRecordset：： GetSQL](#getsql)|取得用來選取記錄集記錄的 SQL 字串。|
|[CDaoRecordset：： GetType](#gettype)|呼叫以判斷記錄集的類型：資料表類型、動態集型別或快照型別。|
|[CDaoRecordset：： GetValidationRule](#getvalidationrule)|傳回 `CString`，其中包含在輸入欄位時驗證資料的值。|
|[CDaoRecordset：： GetValidationText](#getvalidationtext)|抓取未滿足驗證規則時所顯示的文字。|
|[CDaoRecordset：： IsBOF](#isbof)|如果記錄集已放在第一筆記錄之前，則傳回非零。 沒有目前的記錄。|
|[CDaoRecordset：： IsDeleted](#isdeleted)|如果記錄集位於已刪除的記錄上，則傳回非零。|
|[CDaoRecordset：： IsEOF](#iseof)|如果記錄集已放在最後一筆記錄之後，則傳回非零。 沒有目前的記錄。|
|[CDaoRecordset：： IsFieldDirty](#isfielddirty)|如果目前記錄中指定的欄位已變更，則傳回非零。|
|[CDaoRecordset：： IsFieldNull](#isfieldnull)|如果目前記錄中的指定欄位為 Null （沒有值），則傳回非零。|
|[CDaoRecordset：： IsFieldNullable](#isfieldnullable)|如果目前記錄中的指定欄位可以設定為 Null （沒有值），則傳回非零。|
|[CDaoRecordset：： IsOpen](#isopen)|如果先前已呼叫[Open](#open) ，則傳回非零。|
|[CDaoRecordset：： Move](#move)|以任一方向將記錄集置於目前記錄中指定數目的記錄。|
|[CDaoRecordset：： MoveFirst](#movefirst)|將目前的記錄放置在記錄集的第一筆記錄上。|
|[CDaoRecordset：： MoveLast](#movelast)|將目前記錄置於記錄集的最後一筆記錄。|
|[CDaoRecordset：： MoveNext](#movenext)|將目前的記錄放置在記錄集的下一個記錄中。|
|[CDaoRecordset：： MovePrev](#moveprev)|將目前記錄放置在記錄集的上一個記錄中。|
|[CDaoRecordset：： Open](#open)|從資料表、動態集或快照建立新的記錄集。|
|[CDaoRecordset：： Requery](#requery)|再次執行記錄集的查詢，以重新整理選取的記錄。|
|[CDaoRecordset：： Seek](#seek)|找出索引資料表類型記錄集物件中的記錄，以滿足目前索引的指定準則，並讓該記錄成為目前的記錄。|
|[CDaoRecordset：： SetAbsolutePosition](#setabsoluteposition)|設定記錄集物件目前記錄的記錄號碼。|
|[CDaoRecordset：： SetBookmark](#setbookmark)|將記錄集置於包含指定書簽的記錄上。|
|[CDaoRecordset：： SetCacheSize](#setcachesize)|設定值，指定包含要從 ODBC 資料來源本機快取之資料的動態集類型記錄集內的記錄數目。|
|[CDaoRecordset：： SetCacheStart](#setcachestart)|設定值，指定要快取之記錄集中第一筆記錄的書簽。|
|[CDaoRecordset：： SetCurrentIndex](#setcurrentindex)|呼叫以設定資料表類型記錄集的索引。|
|[CDaoRecordset：： SetFieldDirty](#setfielddirty)|將目前記錄中指定的欄位標記為已變更。|
|[CDaoRecordset：： SetFieldNull](#setfieldnull)|將目前記錄中指定欄位的值設定為 Null （沒有值）。|
|[CDaoRecordset：： SetFieldValue](#setfieldvalue)|設定記錄集中的欄位值。|
|[CDaoRecordset：： SetFieldValueNull](#setfieldvaluenull)|將記錄集內的欄位值設定為 Null。 （沒有值）。|
|[CDaoRecordset：： SetLockingMode](#setlockingmode)|設定值，指出在編輯期間要使其生效的鎖定類型。|
|[CDaoRecordset：： SetParamValue](#setparamvalue)|設定儲存在基礎 DAOParameter 物件中的指定參數目前的值。|
|[CDaoRecordset：： SetParamValueNull](#setparamvaluenull)|將指定之參數的目前值設定為 Null （沒有值）。|
|[CDaoRecordset：： SetPercentPosition](#setpercentposition)|將目前記錄的位置設定為對應至記錄集內記錄總數百分比的位置。|
|[CDaoRecordset：： Update](#update)|藉由將新的或編輯過的資料儲存在資料來源上，完成 `AddNew` 或 `Edit` 作業。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDaoRecordset：： m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|包含旗標，指出欄位是否會自動標示為已變更。|
|[CDaoRecordset：： m_nFields](#m_nfields)|包含記錄集類別中的欄位資料成員數目，以及記錄集從資料來源選取的資料行數目。|
|[CDaoRecordset：： m_nParams](#m_nparams)|包含記錄集類別中的參數資料成員數目—與記錄集的查詢一起傳遞的參數數目|
|[CDaoRecordset：： m_pDAORecordset](#m_pdaorecordset)|記錄集物件基礎之 DAO 介面的指標。|
|[CDaoRecordset：： m_pDatabase](#m_pdatabase)|此結果集的源資料庫。 包含[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件的指標。|
|[CDaoRecordset：： m_strFilter](#m_strfilter)|包含用來建立 SQL **WHERE**語句的字串。|
|[CDaoRecordset：： m_strSort](#m_strsort)|包含用來建立 SQL **ORDER BY**語句的字串。|

## <a name="remarks"></a>備註

也稱為「記錄集」，`CDaoRecordset` 物件提供下列三種形式：

- 資料表類型記錄集代表一個基表，您可以用來檢查、加入、變更或刪除單一資料庫資料表中的記錄。

- 動態集型別記錄集是可更新記錄的查詢結果。 這些記錄集是一組記錄，您可以用來檢查、加入、變更或刪除基礎資料庫資料表或資料表中的記錄。 動態集型別記錄集可以包含資料庫中一個或多個資料表的欄位。

- 快照類型記錄集是一組記錄的靜態副本，您可以用來尋找資料或產生報表。 這些記錄集可以包含資料庫中一個或多個資料表的欄位，但無法更新。

每一種形式的記錄集都代表在記錄集開啟時固定的一組記錄。 當您滾動到資料表類型記錄集或動態集類型記錄集中的記錄時，它會反映在記錄集開啟之後，由其他使用者或應用程式中的其他記錄集所進行的記錄變更。 （無法更新快照集類型的記錄集）。您可以直接使用 `CDaoRecordset`，或從 `CDaoRecordset`衍生應用程式特定的記錄集類別。 您可以：

- 流覽記錄。

- 使用[Seek](#seek)來設定索引並快速尋找記錄（僅限資料表類型的記錄集）。

- 尋找以字串比較為基礎的記錄： "<"、"\<="、"="、"> =" 或 ">" （動態集型別和快照型別記錄集）。

- 更新記錄，並指定鎖定模式（快照集類型記錄集除外）。

- 篩選記錄集，以限制從資料來源可用的記錄中選取的記錄。

- 排序記錄集。

- 將記錄集參數化，以自訂在執行時間之前不知道的資訊。

類別 `CDaoRecordset` 提供類似類別 `CRecordset`的介面。 主要的差異在於，類別 `CDaoRecordset` 透過以 OLE 為基礎的資料存取物件（DAO）來存取資料。 類別 `CRecordset` 透過開放式資料庫連接（ODBC）和該 DBMS 的 ODBC 驅動程式來存取 DBMS。

> [!NOTE]
> DAO 資料庫類別與以開放式資料庫連接（ODBC）為基礎的 MFC 資料庫類別不同。 所有的 DAO 資料庫類別名稱都具有 "CDao" 前置詞。 您仍然可以使用 DAO 類別來存取 ODBC 資料來源。DAO 類別一般提供了絕佳的功能，因為它們是 Microsoft Jet 資料庫引擎特有的。

您可以直接使用 `CDaoRecordset`，或從 `CDaoRecordset`衍生類別。 若要在任一情況下使用記錄集類別，請開啟資料庫並建立記錄集物件，並將指標傳遞至您的 `CDaoDatabase` 物件。 您也可以建立 `CDaoRecordset` 物件，並讓 MFC 為您建立暫存的 `CDaoDatabase` 物件。 然後通話記錄集的[Open](#open)成員函式，指定物件是否為數據表類型記錄集、動態集類型記錄集或快照集類型記錄集。 呼叫 `Open` 會從資料庫中選取資料，並抓取第一筆記錄。

使用物件的成員函式和資料成員來逐一查看記錄，並對其進行操作。 可用的作業取決於物件是否為數據表類型記錄集、動態集類型記錄集或快照集類型記錄集，以及它是否可更新或唯讀，這取決於資料庫或開放式資料庫連接（ODBC）的功能。資料來源。 若要重新整理自 `Open` 呼叫之後可能已變更或新增的記錄，請呼叫物件的[Requery](#requery)成員函式。 呼叫物件的 `Close` 成員函式，並在完成時終結物件。

`CDaoRecordset` 使用 DAO 記錄欄位交換（DFX），透過 `CDaoRecordset` 或 `CDaoRecordset`衍生類別的型別安全C++成員來支援讀取和更新記錄欄位。 您也可以在資料庫中執行資料行的動態繫結，而不需要使用[GetFieldValue](#getfieldvalue)和[SetFieldValue](#setfieldvalue)的 DFX 機制。

如需相關資訊，請參閱 DAO 說明中的「記錄集物件」主題。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>需求

**標頭：** afxdao。h

##  <a name="addnew"></a>CDaoRecordset：： AddNew

呼叫這個成員函式，將新記錄加入至資料表類型或動態集類型記錄集。

```
virtual void AddNew();
```

### <a name="remarks"></a>備註

記錄的欄位一開始是 Null。 （在資料庫術語中，Null 表示「沒有值」，而且與中C++的 null 不同）。若要完成此作業，您必須呼叫[Update](#update)成員函式。 `Update` 會將您的變更儲存至資料來源。

> [!CAUTION]
>  如果您編輯記錄，然後在沒有呼叫 `Update`的情況下滾動到另一筆記錄，您的變更就會遺失而不會發出警告。

如果您藉由呼叫[AddNew](#addnew)，將記錄加入至動態集類型的記錄集，記錄就會顯示在記錄集內，而且會包含在基礎資料表中，而任何新的 `CDaoRecordset` 物件都可以看到它。

新記錄的位置取決於記錄集的類型：

- 在動態類型記錄集內，不保證會插入新記錄。 基於效能和並行的原因，此行為隨著 Microsoft Jet 3.0 而變更。 如果您的目標是要讓新加入的記錄成為目前的記錄，請取得上次修改記錄的書簽，並移至該書簽：

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- 在已指定索引的資料表類型記錄集內，記錄會在其適當位置以排序次序傳回。 如果未指定任何索引，就會在記錄集的結尾傳回新的記錄。

在您使用 `AddNew` 之前的記錄會保持為最新。 如果您想要將新記錄設為目前的，而且記錄集支援書簽，請將[SetBookmark](#setbookmark)呼叫至基礎 DAO 記錄集物件的 LastModified 屬性設定所識別的書簽。 這麼做適用于判斷已加入記錄中計數器（自動遞增）欄位的值。 如需詳細資訊，請參閱[GetLastModifiedBookmark](#getlastmodifiedbookmark)。

如果資料庫支援交易，您可以讓您的 `AddNew` 呼叫交易的一部分。 如需交易的詳細資訊，請參閱類別[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)。 請注意，在呼叫 `AddNew`之前，您應該先呼叫[CDaoWorkspace：： BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) 。

對於尚未呼叫[Open](#open)成員函式的記錄集，不合法地呼叫 `AddNew`。 如果您針對無法附加的記錄集呼叫 `AddNew`，則會擲回 `CDaoException`。 您可以藉由呼叫[CanAppend](#canappend)來判斷記錄集是否可更新。

架構會標示已變更的欄位資料成員，以確保 DAO 記錄欄位交換（DFX）機制會將它們寫入資料來源上的記錄。 變更欄位的值通常會自動將欄位設定為中途，因此您不常需要自行呼叫[SetFieldDirty](#setfielddirty) ，但有時您可能會想要確保不論欄位資料成員中的值為何，都會明確更新或插入資料行。 DFX 機制也會採用**虛擬 Null**的用法。 如需詳細資訊，請參閱[CDaoFieldExchange：： m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用雙重緩衝機制，則變更欄位的值時，不會自動將欄位設定為「中途」。 在此情況下，必須明確地將欄位設定為已變更。 包含在[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中的旗標會控制此自動欄位檢查。

> [!NOTE]
> 如果記錄是雙重緩衝（也就是啟用自動欄位檢查），則呼叫 `CancelUpdate` 會將成員變數還原至 `AddNew` 或 `Edit` 被呼叫之前所擁有的值。

如需相關資訊，請參閱 DAO 說明中的「AddNew 方法」、「CancelUpdate 方法」、「LastModified 屬性」和「EditMode 屬性」主題。

##  <a name="canappend"></a>CDaoRecordset：： CanAppend

呼叫這個成員函式，以判斷先前開啟的記錄集是否允許您藉由呼叫[AddNew](#addnew)成員函式來加入新的記錄。

```
BOOL CanAppend() const;
```

### <a name="return-value"></a>傳回值

如果記錄集允許加入新記錄，則為非零。否則為0。 如果您以唯讀方式開啟記錄集，`CanAppend` 將會傳回0。

### <a name="remarks"></a>備註

如需相關資訊，請參閱 DAO 說明中的「附加方法」主題。

##  <a name="canbookmark"></a>CDaoRecordset：： CanBookmark

呼叫這個成員函式，以判斷先前開啟的記錄集是否可讓您使用書簽個別標記記錄。

```
BOOL CanBookmark();
```

### <a name="return-value"></a>傳回值

如果記錄集支援書簽，則為非零，否則為0。

### <a name="remarks"></a>備註

如果您使用完全以 Microsoft Jet 資料庫引擎資料表為基礎的記錄集，則除了標示為順向滾動記錄集的快照集類型記錄集之外，您還可以使用書簽。 其他資料庫產品（外部 ODBC 資料來源）可能不支援書簽。

如需相關資訊，請參閱 DAO 說明中的「Bookmarkable 屬性」主題。

##  <a name="cancelupdate"></a>CDaoRecordset：： CancelUpdate

由於[編輯](#edit)或[AddNew](#addnew)作業，`CancelUpdate` 成員函式會取消任何暫止的更新。

```
virtual void CancelUpdate();
```

### <a name="remarks"></a>備註

例如，如果應用程式呼叫 `Edit` 或 `AddNew` 成員函式，但尚未呼叫[Update](#update)，`CancelUpdate` 會取消呼叫 `Edit` 或 `AddNew` 之後所做的任何變更。

> [!NOTE]
>  如果記錄是雙重緩衝（也就是啟用自動欄位檢查），則呼叫 `CancelUpdate` 會將成員變數還原至 `AddNew` 或 `Edit` 被呼叫之前所擁有的值。

如果沒有 `Edit` 或 `AddNew` 作業暫止，`CancelUpdate` 會導致 MFC 擲回例外狀況。 呼叫[GetEditMode](#geteditmode)成員函式，以判斷是否有可取消的暫止作業。

如需相關資訊，請參閱 DAO 說明中的「CancelUpdate 方法」主題。

##  <a name="canrestart"></a>CDaoRecordset：： CanRestart

呼叫這個成員函式，以判斷記錄集是否允許藉由呼叫 `Requery` 成員函式重新開機其查詢（以重新整理其記錄）。

```
BOOL CanRestart();
```

### <a name="return-value"></a>傳回值

如果可以呼叫 `Requery` 以重新執行記錄集的查詢，則為非零，否則為0。

### <a name="remarks"></a>備註

資料表類型的記錄集不支援 `Requery`。

如果不支援 `Requery`，請呼叫[Close](#close) ，然後[開啟](#open)以重新整理資料。 在參數值變更之後，您可以呼叫 `Requery` 來更新記錄集物件的基礎參數查詢。

如需相關資訊，請參閱 DAO 說明中的「可重新開機屬性」主題。

##  <a name="canscroll"></a>CDaoRecordset：： CanScroll

呼叫這個成員函式，以判斷記錄集是否允許滾動。

```
BOOL CanScroll() const;
```

### <a name="return-value"></a>傳回值

如果您可以流覽記錄，則為非零，否則為0。

### <a name="remarks"></a>備註

如果您使用 `dbForwardOnly`呼叫[Open](#open) ，記錄集只能向前復原。

如需相關資訊，請參閱 DAO 說明中的「使用 DAO 定位目前的記錄指標」主題。

##  <a name="cantransact"></a>CDaoRecordset：： CanTransact

呼叫這個成員函式，以判斷記錄集是否允許交易。

```
BOOL CanTransact();
```

### <a name="return-value"></a>傳回值

如果基礎資料來源支援交易，則為非零，否則為0。

### <a name="remarks"></a>備註

如需相關資訊，請參閱 DAO 說明中的「交易屬性」主題。

##  <a name="canupdate"></a>CDaoRecordset：： CanUpdate

呼叫這個成員函式，以判斷是否可以更新記錄集。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>傳回值

如果記錄集可以更新（加入、更新和刪除記錄），則為非零，否則為0。

### <a name="remarks"></a>備註

如果基礎資料來源為唯讀，或當您為記錄集呼叫[Open](#open)時，指定*nOptions* `dbReadOnly`，則記錄集可能是唯讀的。

如需相關資訊，請參閱 DAO 說明中的「AddNew 方法」、「編輯方法」、「刪除方法」、「更新方法」和「可更新屬性」主題。

##  <a name="cdaorecordset"></a>CDaoRecordset：： CDaoRecordset

建構 `CDaoRecordset` 物件。

```
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>參數

*pDatabase*<br/>
包含[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件的指標或 Null 值。 如果不是 Null，而且尚未呼叫 `CDaoDatabase` 物件的 `Open` 成員函式來將它連接到資料來源，記錄集就會在它自己的[open](#open)呼叫期間，嘗試為您開啟它。 如果您傳遞 Null，則會使用您在從 `CDaoRecordset`衍生記錄集類別時所指定的資料來源資訊，為您建立 `CDaoDatabase` 物件的結構並加以連接。

### <a name="remarks"></a>備註

您可以直接使用 `CDaoRecordset`，或從 `CDaoRecordset`衍生應用程式特定的類別。 您可以使用 ClassWizard 來衍生您的記錄集類別。

> [!NOTE]
>  如果您要衍生 `CDaoRecordset` 類別，則您的衍生類別必須提供自己的函式。 在衍生類別的函式中，呼叫 `CDaoRecordset::CDaoRecordset`的函式，並將適當的參數傳遞至該函數。

將 Null 傳遞至您的記錄集函式，以自動為您建立 `CDaoDatabase` 物件並為您連接。 這是很有用的快捷方式，您不需要在建立記錄集之前，先建立和連接 `CDaoDatabase` 物件。 如果未開啟 `CDaoDatabase` 物件，也會為您建立使用預設工作區的[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件。 如需詳細資訊，請參閱[CDaoDatabase：： CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase)。

##  <a name="close"></a>CDaoRecordset：： Close

關閉 `CDaoRecordset` 物件會從關聯資料庫中開啟的記錄集集合中移除它。

```
virtual void Close();
```

### <a name="remarks"></a>備註

因為 `Close` 不會摧毀 `CDaoRecordset` 物件，所以您可以在相同的資料來源或不同的資料來源上呼叫 `Open`，以重複使用物件。

所有暫止的[AddNew](#addnew)或[Edit](#edit)語句都會取消，而且所有暫止的交易都會回復。 如果您想要保留暫止的新增或編輯專案，請先呼叫[Update](#update) ，再呼叫每個記錄集的 `Close`。

呼叫 `Close`之後，您可以再次呼叫 `Open`。 這可讓您重複使用記錄集物件。 更好的替代方式是呼叫重新[查詢](#requery)（如果可能的話）。

如需相關資訊，請參閱 DAO 說明中的「關閉方法」主題。

##  <a name="delete"></a>CDaoRecordset：:D 刪除

呼叫這個成員函式，以刪除開放式動態集類型或資料表類型記錄集物件中的目前記錄。

```
virtual void Delete();
```

### <a name="remarks"></a>備註

成功刪除之後，記錄集的欄位資料成員會設定為 Null 值，而且您必須明確地呼叫其中一個記錄集導覽成員函式（[移動](#move)、[搜尋](#seek)、 [SetBookmark](#setbookmark)等等），才能移出已刪除的記錄。 當您從記錄集刪除記錄時，記錄集內必須有目前的記錄，才能呼叫 `Delete`;否則，MFC 會擲回例外狀況。

`Delete` 會移除目前的記錄，使其無法存取。 雖然您無法編輯或使用已刪除的記錄，但它仍然是最新的。 不過，一旦您移至另一筆記錄，就無法再次將刪除的記錄重新設為目前的。

> [!CAUTION]
>  記錄集必須是可更新的，而且當您呼叫 `Delete`時，記錄集內必須有有效的記錄。 例如，如果您刪除記錄，但在再次呼叫 `Delete` 之前，未滾動到新的記錄，`Delete` 會擲回[CDaoException](../../mfc/reference/cdaoexception-class.md)。

如果您使用交易，而且呼叫[CDaoWorkspace：： Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback)成員函式，則可以取消刪除記錄。 如果基表是串聯刪除關聯性中的主資料表，刪除目前記錄也可能會刪除外部資料表中的一或多個記錄。 如需詳細資訊，請參閱 DAO 說明中的「cascade 刪除」定義。

不同于 `AddNew` 和 `Edit`，對 `Delete` 的呼叫後面不會呼叫 `Update`。

如需相關資訊，請參閱 DAO 說明中的「AddNew 方法」、「編輯方法」、「刪除方法」、「更新方法」和「可更新屬性」主題。

##  <a name="dofieldexchange"></a>CDaoRecordset：:D oFieldExchange

架構會呼叫這個成員函式，在記錄集物件的欄位資料成員和資料來源上目前記錄的對應資料行之間，自動交換資料。

```
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>參數

*pFX*<br/>
包含 `CDaoFieldExchange` 物件的指標。 架構已經設定此物件來指定欄位交換作業的內容。

### <a name="remarks"></a>備註

它也會將您的參數資料成員（如果有的話）系結至記錄集選取之 SQL 語句字串中的參數預留位置。 欄位資料的交換（稱為 DAO 記錄欄位交換（DFX））可以雙向運作：從記錄集物件的欄位資料成員，到資料來源上記錄的欄位，以及從資料來源的記錄到記錄集物件。 如果您要動態地系結資料行，則不需要執行 `DoFieldExchange`。

執行衍生記錄集類別的 `DoFieldExchange` 時，您通常必須採取的動作是使用 ClassWizard 建立類別，並指定欄位資料成員的名稱和資料類型。 您也可以將程式碼新增至 ClassWizard 寫入的內容，以指定參數資料成員。 如果要動態系結所有欄位，除非您指定參數資料成員，否則此函式將會變成非作用中。

當您使用 ClassWizard 宣告您的衍生記錄集類別時，嚮導會為您撰寫 `DoFieldExchange` 的覆寫，如下列範例所示：

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

##  <a name="edit"></a>CDaoRecordset：： Edit

呼叫這個成員函式，以允許對目前記錄進行變更。

```
virtual void Edit();
```

### <a name="remarks"></a>備註

一旦您呼叫 `Edit` 成員函式，對目前記錄的欄位所做的變更會複製到複製緩衝區。 在您對記錄進行所需的變更之後，請呼叫 `Update` 來儲存您的變更。 `Edit` 儲存記錄集的資料成員值。 如果您呼叫 `Edit`、進行變更，然後再次呼叫 `Edit`，則記錄的值會還原為第一次 `Edit` 呼叫之前的內容。

> [!CAUTION]
>  如果您編輯記錄，然後執行任何移至另一筆記錄而不先呼叫 `Update`的作業，您的變更就會遺失而不發出警告。 此外，如果您關閉記錄集或父資料庫，就會捨棄已編輯的記錄而不發出警告。

在某些情況下，您可能想要將資料行設為 Null （不包含任何資料）來更新它。 若要這麼做，請使用 TRUE 的參數呼叫 `SetFieldNull`，將欄位標記為 Null;這也會導致更新資料行。 如果您想要將欄位寫入資料來源，即使其值尚未變更，請使用參數 TRUE 呼叫 `SetFieldDirty`。 即使欄位具有 Null 值，也可以這麼做。

架構會標示已變更的欄位資料成員，以確保 DAO 記錄欄位交換（DFX）機制會將它們寫入資料來源上的記錄。 變更欄位的值通常會自動將欄位設定為中途，因此您不常需要自行呼叫[SetFieldDirty](#setfielddirty) ，但有時您可能會想要確保不論欄位資料成員中的值為何，都會明確更新或插入資料行。 DFX 機制也會採用**虛擬 Null**的用法。 如需詳細資訊，請參閱[CDaoFieldExchange：： m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用雙重緩衝機制，則變更欄位的值時，不會自動將欄位設定為「中途」。 在此情況下，必須明確地將欄位設定為已變更。 包含在[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中的旗標會控制此自動欄位檢查。

當記錄集物件在多使用者環境中被搭配保守模式鎖定時，記錄會保持鎖定，直到使用 `Edit` 為止，直到更新完成為止。 如果記錄集是樂觀地鎖定的，則記錄會被鎖定，並在資料庫中更新之前，與預先編輯的記錄做比較。 如果記錄在您呼叫 `Edit`之後已變更，則 `Update` 作業會失敗，而且 MFC 會擲回例外狀況。 您可以使用 `SetLockingMode`變更鎖定模式。

> [!NOTE]
>  開放式鎖定一律用於外部資料庫格式，例如 ODBC 和可安裝的 ISAM。

呼叫 `Edit`之後，目前的記錄仍維持最新。 若要呼叫 `Edit`，必須要有目前的記錄。 如果沒有目前的記錄或記錄集未參考開放式資料表類型或動態集類型的記錄集物件，就會發生例外狀況。 呼叫 `Edit` 會導致在下列情況下擲回 `CDaoException`：

- 沒有目前的記錄。

- 資料庫或記錄集是唯讀的。

- 記錄中沒有任何欄位是可更新的。

- 資料庫或記錄集已開啟供其他使用者獨佔使用。

- 另一個使用者已鎖定包含您記錄的頁面。

如果資料來源支援交易，您可以讓 `Edit` 呼叫交易的一部分。 請注意，在呼叫 `Edit` 之前和記錄集開啟之後，您應該呼叫 `CDaoWorkspace::BeginTrans`。 另請注意，呼叫 `CDaoWorkspace::CommitTrans` 並不是呼叫 `Update` 來完成 `Edit` 作業的替代方案。 如需交易的詳細資訊，請參閱類別 `CDaoWorkspace`。

如需相關資訊，請參閱 DAO 說明中的「AddNew 方法」、「編輯方法」、「刪除方法」、「更新方法」和「可更新屬性」主題。

##  <a name="fillcache"></a>CDaoRecordset：： FillCache

呼叫這個成員函式可從記錄集快取指定的記錄數目。

```
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>參數

*pSize*<br/>
指定要填入快取的資料列數目。 如果您省略這個參數，此值是由基礎 DAO 物件的 CacheSize 屬性設定所決定。

*pBookmark*<br/>
指定書簽的[COleVariant](../../mfc/reference/colevariant-class.md) 。 快取會從這個書簽所指出的記錄開始填入。 如果您省略這個參數，就會從基礎 DAO 物件的 CacheStart 屬性所指示的記錄開始填入快取。

### <a name="remarks"></a>備註

快取可改善從遠端伺服器抓取或提取資料之應用程式的效能。 快取是本機記憶體中的空間，其中保存最近從伺服器提取的資料，假設在應用程式執行時可能會再次要求資料。 當要求資料時，Microsoft Jet 資料庫引擎會先檢查快取中的資料，而不是從伺服器提取它，這會花費更多時間。 在非 ODBC 資料來源上使用資料快取不會有任何作用，因為資料不會儲存在快取中。

您可以藉由呼叫 `FillCache` 成員函式，隨時明確填滿快取，而不是在提取記錄時等候快取填滿。 這是填滿快取的更快速方式，因為 `FillCache` 一次會提取數筆記錄，而不是一次一個。 例如，當顯示記錄的每個 screenful 時，您可以讓應用程式呼叫 `FillCache` 來提取下一筆記錄 screenful。

任何以記錄集物件存取的 ODBC 資料庫都可以有本機快取。 若要建立快取，請從遠端資料源開啟記錄集物件，然後呼叫 `SetCacheSize`，並 `SetCacheStart` 記錄集的成員函式。 如果*lSize*和*lBookmark*建立的範圍部分或完全超出 `SetCacheSize` 和 `SetCacheStart`所指定的範圍，則會忽略此範圍外的記錄集部分，而且不會載入快取中。 如果 `FillCache` 要求的記錄數超過遠端資料源中保留的數目，則只會提取剩餘的記錄，而且不會擲回任何例外狀況。

從快取提取的記錄不會反映其他使用者同時對來源資料所做的變更。

`FillCache` 只提取尚未快取的記錄。 若要強制更新所有快取的資料，請呼叫 `SetCacheSize` 成員函式，並將*lSize*參數設為0，並再次呼叫 `SetCacheSize`，並將*lSize*參數設定為等於您原先要求的快取大小，然後再呼叫 `FillCache`。

如需相關資訊，請參閱 DAO 說明中的「FillCache 方法」主題。

##  <a name="find"></a>CDaoRecordset：： Find

呼叫這個成員函式，以使用比較運算子來尋找動態集或快照集類型記錄集中的特定字串。

```
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*lFindType*<br/>
值，指出所需的尋找作業類型。 可能的值包括：

- AFX_DAO_NEXT 尋找相符字串的下一個位置。

- AFX_DAO_PREV 尋找相符字串的先前位置。

- AFX_DAO_FIRST 尋找相符字串的第一個位置。

- AFX_DAO_LAST 尋找相符字串的最後一個位置。

*lpszFilter*<br/>
用來尋找記錄的字串運算式（例如 SQL 語句中的**WHERE**子句，**其中**不含單字）。 例如，

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>傳回值

如果找到相符的記錄，則為非零，否則為0。

### <a name="remarks"></a>備註

您可以尋找字串的第一個、下一個、上一個或最後一個實例。 `Find` 是虛擬函式，因此您可以覆寫它，並加入您自己的實作為。 `FindFirst`、`FindLast`、`FindNext`和 `FindPrev` 成員函式會呼叫 `Find` 成員函式，因此您可以使用 `Find` 來控制所有尋找作業的行為。

若要找出資料表類型記錄集中的記錄，請呼叫[Seek](#seek)成員函式。

> [!TIP]
>  您擁有的一組記錄越小，`Find` 的效率就愈高。 一般來說，特別是使用 ODBC 資料時，最好是建立只抓取所需記錄的新查詢。

如需相關資訊，請參閱 DAO 說明中的「FindFirst，FindLast，FindNext，FindPrevious 方法」主題。

##  <a name="findfirst"></a>CDaoRecordset：： FindFirst

呼叫這個成員函式，以尋找符合指定條件的第一筆記錄。

```
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*lpszFilter*<br/>
用來尋找記錄的字串運算式（例如 SQL 語句中的**WHERE**子句，**其中**不含單字）。

### <a name="return-value"></a>傳回值

如果找到相符的記錄，則為非零，否則為0。

### <a name="remarks"></a>備註

`FindFirst` 成員函式會從記錄集的開頭開始搜尋，並搜尋到記錄集的結尾。

如果您想要在搜尋中包含所有記錄（而不只是符合特定條件的記錄），請使用其中一項移動作業，從記錄移至記錄。 若要找出資料表類型記錄集中的記錄，請呼叫 `Seek` 成員函式。

如果找不到符合準則的記錄，則無法確定目前的記錄指標，`FindFirst` 會傳回零。 如果記錄集包含一個以上符合準則的記錄，`FindFirst` 會找出第一個出現的專案，`FindNext` 找出下一個專案，依此類推。

> [!CAUTION]
>  如果您編輯目前的記錄，請務必先呼叫 `Update` 成員函式來儲存變更，然後再移至另一筆記錄。 如果您移至另一筆記錄而不更新，則會遺失您的變更，而不會出現警告。

`Find` 成員函式會從位置和下表所指定的方向進行搜尋：

|尋找作業|開始|搜尋方向|
|---------------------|-----------|----------------------|
|`FindFirst`|記錄集的開頭|記錄集結尾|
|`FindLast`|記錄集結尾|記錄集的開頭|
|`FindNext`|目前記錄|記錄集結尾|
|`FindPrevious`|目前記錄|記錄集的開頭|

> [!NOTE]
>  當您呼叫 `FindLast`時，Microsoft Jet 資料庫引擎會在開始搜尋之前，完全填入您的記錄集（如果尚未這麼做）。 第一次搜尋可能會比後續搜尋花費更長的時間。

不過，使用其中一個「尋找」作業和呼叫 `MoveFirst` 或 `MoveNext`不同，只是讓第一個或下一個記錄成為目前的，而不指定條件。 您可以遵循「尋找」作業來執行「移動」操作。

使用尋找作業時，請記住下列事項：

- 如果 `Find` 傳回非零值，則不會定義目前的記錄。 在此情況下，您必須將目前的記錄指標放回有效的記錄。

- 您不能將尋找作業與順向滾動快照集類型記錄集搭配使用。

- 當您搜尋包含日期的欄位時，您應該使用美國日期格式（月-日），即使您不使用 Microsoft Jet database engine 的美國版本也一樣。否則，可能找不到相符的記錄。

- 使用 ODBC 資料庫和大型的動態集時，您可能會發現使用「尋找」作業的速度很慢，特別是在使用大型記錄集時。 您可以使用 SQL 查詢搭配自訂**ORDERBY**或**WHERE**子句、參數查詢，或可抓取特定索引記錄的 `CDaoQuerydef` 物件，來改善效能。

如需相關資訊，請參閱 DAO 說明中的「FindFirst，FindLast，FindNext，FindPrevious 方法」主題。

##  <a name="findlast"></a>CDaoRecordset：： FindLast

呼叫這個成員函式，以尋找符合指定之條件的最後一筆記錄。

```
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*lpszFilter*<br/>
用來尋找記錄的字串運算式（例如 SQL 語句中的**WHERE**子句，**其中**不含單字）。

### <a name="return-value"></a>傳回值

如果找到相符的記錄，則為非零，否則為0。

### <a name="remarks"></a>備註

`FindLast` 成員函式會在記錄集的結尾開始搜尋，並向後搜尋記錄集的開頭。

如果您想要在搜尋中包含所有記錄（而不只是符合特定條件的記錄），請使用其中一項移動作業，從記錄移至記錄。 若要找出資料表類型記錄集中的記錄，請呼叫 `Seek` 成員函式。

如果找不到符合準則的記錄，則無法確定目前的記錄指標，`FindLast` 會傳回零。 如果記錄集包含一個以上符合準則的記錄，`FindFirst` 會找出第一個出現的專案，`FindNext` 找出第一次出現之後的下一個專案，依此類推。

> [!CAUTION]
>  如果您編輯目前的記錄，請務必先呼叫 `Update` 成員函式來儲存變更，然後再移至另一筆記錄。 如果您移至另一筆記錄而不更新，則會遺失您的變更，而不會出現警告。

不過，使用其中一個「尋找」作業和呼叫 `MoveFirst` 或 `MoveNext`不同，只是讓第一個或下一個記錄成為目前的，而不指定條件。 您可以遵循「尋找」作業來執行「移動」操作。

使用尋找作業時，請記住下列事項：

- 如果 `Find` 傳回非零值，則不會定義目前的記錄。 在此情況下，您必須將目前的記錄指標放回有效的記錄。

- 您不能將尋找作業與順向滾動快照集類型記錄集搭配使用。

- 當您搜尋包含日期的欄位時，您應該使用美國日期格式（月-日），即使您不使用 Microsoft Jet database engine 的美國版本也一樣。否則，可能找不到相符的記錄。

- 使用 ODBC 資料庫和大型的動態集時，您可能會發現使用「尋找」作業的速度很慢，特別是在使用大型記錄集時。 您可以使用 SQL 查詢搭配自訂**ORDERBY**或**WHERE**子句、參數查詢，或可抓取特定索引記錄的 `CDaoQuerydef` 物件，來改善效能。

如需相關資訊，請參閱 DAO 說明中的「FindFirst，FindLast，FindNext，FindPrevious 方法」主題。

##  <a name="findnext"></a>CDaoRecordset：： FindNext

呼叫這個成員函式，以尋找符合指定條件的下一筆記錄。

```
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*lpszFilter*<br/>
用來尋找記錄的字串運算式（例如 SQL 語句中的**WHERE**子句，**其中**不含單字）。

### <a name="return-value"></a>傳回值

如果找到相符的記錄，則為非零，否則為0。

### <a name="remarks"></a>備註

`FindNext` 成員函式會從目前的記錄開始搜尋，並在記錄集的結尾進行搜尋。

如果您想要在搜尋中包含所有記錄（而不只是符合特定條件的記錄），請使用其中一項移動作業，從記錄移至記錄。 若要找出資料表類型記錄集中的記錄，請呼叫 `Seek` 成員函式。

如果找不到符合準則的記錄，則無法確定目前的記錄指標，`FindNext` 會傳回零。 如果記錄集包含一個以上符合準則的記錄，`FindFirst` 會找出第一個出現的專案，`FindNext` 找出下一個專案，依此類推。

> [!CAUTION]
>  如果您編輯目前的記錄，請務必先呼叫 `Update` 成員函式來儲存變更，然後再移至另一筆記錄。 如果您移至另一筆記錄而不更新，則會遺失您的變更，而不會出現警告。

不過，使用其中一個「尋找」作業和呼叫 `MoveFirst` 或 `MoveNext`不同，只是讓第一個或下一個記錄成為目前的，而不指定條件。 您可以遵循「尋找」作業來執行「移動」操作。

使用尋找作業時，請記住下列事項：

- 如果 `Find` 傳回非零值，則不會定義目前的記錄。 在此情況下，您必須將目前的記錄指標放回有效的記錄。

- 您不能將尋找作業與順向滾動快照集類型記錄集搭配使用。

- 當您搜尋包含日期的欄位時，您應該使用美國日期格式（月-日），即使您不使用 Microsoft Jet database engine 的美國版本也一樣。否則，可能找不到相符的記錄。

- 使用 ODBC 資料庫和大型的動態集時，您可能會發現使用「尋找」作業的速度很慢，特別是在使用大型記錄集時。 您可以使用 SQL 查詢搭配自訂**ORDERBY**或**WHERE**子句、參數查詢，或可抓取特定索引記錄的 `CDaoQuerydef` 物件，來改善效能。

如需相關資訊，請參閱 DAO 說明中的「FindFirst，FindLast，FindNext，FindPrevious 方法」主題。

##  <a name="findprev"></a>CDaoRecordset：： FindPrev

呼叫這個成員函式，以尋找符合指定條件的上一個記錄。

```
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*lpszFilter*<br/>
用來尋找記錄的字串運算式（例如 SQL 語句中的**WHERE**子句，**其中**不含單字）。

### <a name="return-value"></a>傳回值

如果找到相符的記錄，則為非零，否則為0。

### <a name="remarks"></a>備註

`FindPrev` 成員函式會從目前的記錄開始搜尋，並向後搜尋記錄集的開頭。

如果您想要在搜尋中包含所有記錄（而不只是符合特定條件的記錄），請使用其中一項移動作業，從記錄移至記錄。 若要找出資料表類型記錄集中的記錄，請呼叫 `Seek` 成員函式。

如果找不到符合準則的記錄，則無法確定目前的記錄指標，`FindPrev` 會傳回零。 如果記錄集包含一個以上符合準則的記錄，`FindFirst` 會找出第一個出現的專案，`FindNext` 找出下一個專案，依此類推。

> [!CAUTION]
>  如果您編輯目前的記錄，請務必先呼叫 `Update` 成員函式來儲存變更，然後再移至另一筆記錄。 如果您移至另一筆記錄而不更新，則會遺失您的變更，而不會出現警告。

不過，使用其中一個「尋找」作業和呼叫 `MoveFirst` 或 `MoveNext`不同，只是讓第一個或下一個記錄成為目前的，而不指定條件。 您可以遵循「尋找」作業來執行「移動」操作。

使用尋找作業時，請記住下列事項：

- 如果 `Find` 傳回非零值，則不會定義目前的記錄。 在此情況下，您必須將目前的記錄指標放回有效的記錄。

- 您不能將尋找作業與順向滾動快照集類型記錄集搭配使用。

- 當您搜尋包含日期的欄位時，您應該使用美國日期格式（月-日），即使您不使用 Microsoft Jet database engine 的美國版本也一樣。否則，可能找不到相符的記錄。

- 使用 ODBC 資料庫和大型的動態集時，您可能會發現使用「尋找」作業的速度很慢，特別是在使用大型記錄集時。 您可以使用 SQL 查詢搭配自訂**ORDERBY**或**WHERE**子句、參數查詢，或可抓取特定索引記錄的 `CDaoQuerydef` 物件，來改善效能。

如需相關資訊，請參閱 DAO 說明中的「FindFirst，FindLast，FindNext，FindPrevious 方法」主題。

##  <a name="getabsoluteposition"></a>CDaoRecordset：： GetAbsolutePosition

傳回記錄集物件的目前記錄號碼。

```
long GetAbsolutePosition();
```

### <a name="return-value"></a>傳回值

從0到記錄集內記錄數目的整數。 對應至記錄集中目前記錄的序數位置。

### <a name="remarks"></a>備註

基礎 DAO 物件的 AbsolutePosition 屬性值是以零為基底;設定為0時，是指記錄集內的第一筆記錄。 您可以藉由呼叫[GetRecordCount](#getrecordcount)，判斷記錄集中的已填入記錄數目。 呼叫 `GetRecordCount` 可能需要一些時間，因為它必須存取所有記錄以判斷計數。

如果沒有目前的記錄，就像記錄集內沒有任何記錄時一樣，會傳回-1。 如果目前的記錄已刪除，則不會定義 AbsolutePosition 屬性值，而且 MFC 會在參考時擲回例外狀況。 若為動態集類型的記錄集，新記錄會新增至序列的結尾。

> [!NOTE]
>  這個屬性不適合當做代理記錄號碼使用。 書簽仍然是保留並返回指定位置的建議方式，而且是將目前記錄放置在所有記錄集物件類型上的唯一方法。 特別是，指定記錄的位置在刪除之前的記錄會變更。 如果重新建立記錄集，也不保證指定的記錄會有相同的絕對位置，因為記錄集內個別記錄的順序並不保證，除非使用**ORDERBY**子句以 SQL 語句建立。

> [!NOTE]
>  這個成員函式僅適用于動態集型別和快照型別記錄集。

如需相關資訊，請參閱 DAO 說明中的「AbsolutePosition 屬性」主題。

##  <a name="getbookmark"></a>CDaoRecordset：： GetBookmark

呼叫這個成員函式，以取得特定記錄中的書簽值。

```
COleVariant GetBookmark();
```

### <a name="return-value"></a>傳回值

傳回值，表示目前記錄上的書簽。

### <a name="remarks"></a>備註

建立或開啟記錄集物件時，它的每個記錄都已有唯一的書簽（如果支援的話）。 呼叫 `CanBookmark` 來判斷記錄集是否支援書簽。

您可以藉由將書簽的值指派給 `COleVariant` 物件，來儲存目前記錄的書簽。 若要在移至不同的記錄之後隨時快速返回該記錄，請呼叫 `SetBookmark`，並將參數對應至該 `COleVariant` 物件的值。

> [!NOTE]
>  呼叫重新[查詢](#requery)會變更 DAO 書簽。

如需相關資訊，請參閱 DAO 說明中的「書簽屬性」主題。

##  <a name="getcachesize"></a>CDaoRecordset：： GetCacheSize

呼叫這個成員函式以取得快取的記錄數目。

```
long GetCacheSize();
```

### <a name="return-value"></a>傳回值

值，指定包含要從 ODBC 資料來源本機快取之資料的動態集類型記錄集內的記錄數目。

### <a name="remarks"></a>備註

資料快取可改善應用程式的效能，這會透過動態集類型的記錄集物件，從遠端伺服器抓取資料。 快取是本機記憶體中的一個空間，其中保存最近從伺服器中取出的資料，因為在應用程式執行時，將會再次要求資料。 當要求資料時，Microsoft Jet 資料庫引擎會先檢查快取中是否有要求的資料，而不是從伺服器抓取它，這會花費更多時間。 不是來自 ODBC 資料來源的資料不會儲存在快取中。

任何 ODBC 資料來源（例如附加資料表）都可以有本機快取。

如需相關資訊，請參閱 DAO 說明中的「CacheSize，CacheStart 屬性」主題。

##  <a name="getcachestart"></a>CDaoRecordset：： GetCacheStart

呼叫這個成員函式，以取得要快取之記錄集中第一筆記錄的書簽值。

```
COleVariant GetCacheStart();
```

### <a name="return-value"></a>傳回值

`COleVariant`，指定要快取之記錄集中第一筆記錄的書簽。

### <a name="remarks"></a>備註

Microsoft Jet 資料庫引擎會向快取中的快取範圍要求記錄，並向伺服器要求快取範圍以外的記錄。

> [!NOTE]
>  從快取中取出的記錄不會反映其他使用者同時對來源資料所做的變更。

如需相關資訊，請參閱 DAO 說明中的「CacheSize，CacheStart 屬性」主題。

##  <a name="getcurrentindex"></a>CDaoRecordset：： GetCurrentIndex

呼叫這個成員函式，以判斷目前在索引資料表類型 `CDaoRecordset` 物件中使用的索引。

```
CString GetCurrentIndex();
```

### <a name="return-value"></a>傳回值

`CString`，其中包含目前與資料表類型記錄集搭配使用之索引的名稱。 如果未設定任何索引，則會傳回空字串。

### <a name="remarks"></a>備註

此索引是在資料表類型記錄集中排序記錄的基礎，而且會由[Seek](#seek)成員函式用來尋找記錄。

`CDaoRecordset` 物件可以有一個以上的索引，但一次只能使用一個索引（雖然[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)物件可能會在其上定義多個索引）。

如需相關資訊，請參閱 DAO 說明中的「索引物件」和「目前索引」的定義主題。

##  <a name="getdatecreated"></a>CDaoRecordset：： GetDateCreated

呼叫這個成員函式，以取得建立基表的日期和時間。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>傳回值

包含建立基表之日期和時間的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件。

### <a name="remarks"></a>備註

日期和時間設定是從建立基表的電腦衍生而來。

如需相關資訊，請參閱 DAO 說明中的「DateCreated，LastUpdated 屬性」主題。

##  <a name="getdatelastupdated"></a>CDaoRecordset：： GetDateLastUpdated

呼叫這個成員函式，以取得上次更新架構的日期和時間。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>傳回值

包含上次更新基表結構（架構）之日期和時間的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件。

### <a name="remarks"></a>備註

日期和時間設定是從上次更新基表結構（架構）的電腦衍生而來。

如需相關資訊，請參閱 DAO 說明中的「DateCreated，LastUpdated 屬性」主題。

##  <a name="getdefaultdbname"></a>CDaoRecordset：： GetDefaultDBName

呼叫這個成員函式，以判斷此記錄集的資料庫名稱。

```
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>傳回值

`CString`，其中包含衍生此記錄集之資料庫的路徑和名稱。

### <a name="remarks"></a>備註

如果建立的記錄集沒有[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)的指標，則記錄集會使用這個路徑來開啟預設資料庫。 根據預設，此函數會傳回空字串。 當 ClassWizard 從 `CDaoRecordset`衍生新的記錄集時，它會為您建立此函數。

下列範例說明如何在字串中使用雙反斜線（\\\\），這是要正確解讀字串所需的。

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

##  <a name="getdefaultsql"></a>CDaoRecordset：： GetDefaultSQL

架構會呼叫這個成員函式，以取得記錄集所依據的預設 SQL 語句。

```
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>傳回值

包含預設 SQL 語句的 `CString`。

### <a name="remarks"></a>備註

這可能是資料表名稱或 SQL **SELECT**語句。

您可以使用 ClassWizard 宣告您的記錄集類別，間接定義預設的 SQL 語句，而 ClassWizard 會為您執行這項工作。

如果您傳遞 null SQL 字串來[開啟](#open)，則會呼叫這個函式來判斷記錄集的資料表名稱或 SQL。

##  <a name="geteditmode"></a>CDaoRecordset：： GetEditMode

呼叫這個成員函式來判斷編輯的狀態，這是下列其中一個值：

```
short GetEditMode();
```

### <a name="return-value"></a>傳回值

傳回值，指出目前記錄的編輯狀態。

### <a name="remarks"></a>備註

|值|描述|
|-----------|-----------------|
|`dbEditNone`|沒有編輯作業正在進行中。|
|`dbEditInProgress`|`Edit` 已被呼叫。|
|`dbEditAdd`|`AddNew` 已被呼叫。|

如需相關資訊，請參閱 DAO 說明中的「EditMode 屬性」主題。

##  <a name="getfieldcount"></a>CDaoRecordset：： GetFieldCount

呼叫這個成員函式可抓取記錄集內定義的欄位（資料行）數目。

```
short GetFieldCount();
```

### <a name="return-value"></a>傳回值

記錄集中的欄位數目。

### <a name="remarks"></a>備註

如需相關資訊，請參閱 DAO 說明中的「計數屬性」主題。

##  <a name="getfieldinfo"></a>CDaoRecordset：： Issomapper.getfieldinfo

呼叫這個成員函式，以取得有關記錄集中之欄位的資訊。

```
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
記錄集的 Fields 集合中預先定義欄位之以零為起始的索引，用於依索引查閱。

*fieldinfo*<br/>
[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構的參考。

*dwInfoOptions*<br/>
指定要取得之記錄集相關資訊的選項。 這裡列出可用的選項，以及它們導致函式傳回的內容。 為了達到最佳效能，請只取出您需要的資訊層級：

- `AFX_DAO_PRIMARY_INFO` （預設值）名稱、類型、大小、屬性

- `AFX_DAO_SECONDARY_INFO` 的主要資訊，加上：序數位置、必要、允許零長度、排序次序、外部名稱、來源欄位、來源資料表

- `AFX_DAO_ALL_INFO` 主要和次要資訊，加上：預設值、驗證規則、驗證文字

*lpszName*<br/>
欄位的名稱。

### <a name="remarks"></a>備註

函數的其中一個版本可讓您依索引查閱欄位。 另一個版本可讓您依名稱查閱欄位。

如需所傳回信息的描述，請參閱[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。 此結構的成員會對應至*dwInfoOptions*的描述中所列的資訊專案。 當您要求某一層級的資訊時，您也會取得任何先前層級的資訊。

如需相關資訊，請參閱 DAO 說明中的「屬性屬性」主題。

##  <a name="getfieldvalue"></a>CDaoRecordset：： GetFieldValue

呼叫這個成員函式以抓取記錄集中的資料。

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

*lpszName*<br/>
包含欄位名稱之字串的指標。

*varValue*<br/>
`COleVariant` 物件的參考，將會儲存欄位的值。

*nIndex*<br/>
記錄集的 Fields 集合中欄位之以零為起始的索引，用於依索引查閱。

### <a name="return-value"></a>傳回值

傳回值的兩個 `GetFieldValue` 版本會傳回[COleVariant](../../mfc/reference/colevariant-class.md)物件，其中包含欄位的值。

### <a name="remarks"></a>備註

您可以依名稱或序數位置查閱欄位。

> [!NOTE]
>  呼叫這個成員函式的其中一個版本時，會採用 `COleVariant` 物件參考做為參數，而不是呼叫傳回 `COleVariant` 物件的版本，這樣會更有效率。 針對回溯相容性，會保留此函式的後置版本。

使用 `GetFieldValue` 和[SetFieldValue](#setfieldvalue) ，在執行時間以動態方式系結欄位，而不是使用[DoFieldExchange](#dofieldexchange)機制來靜態繫結資料行。

`GetFieldValue` 和 `DoFieldExchange` 機制可以結合在一起，以改善效能。 例如，您可以使用 `GetFieldValue` 來取出只需要隨選的值，並將該呼叫指派給介面中的 [詳細資訊] 按鈕。

如需相關資訊，請參閱 DAO 說明中的「欄位物件」和「值屬性」主題。

##  <a name="getindexcount"></a>CDaoRecordset：： GetIndexCount

呼叫這個成員函式，以判斷資料表類型記錄集上可用的索引數目。

```
short GetIndexCount();
```

### <a name="return-value"></a>傳回值

資料表類型記錄集中的索引數目。

### <a name="remarks"></a>備註

`GetIndexCount` 適用于迴圈查看記錄集中的所有索引。 基於此目的，請使用 `GetIndexCount` 搭配[GetIndexInfo](#getindexinfo)。 如果您在動態集型別或快照集型別記錄上呼叫這個成員函式，MFC 會擲回例外狀況。

如需相關資訊，請參閱 DAO 說明中的「屬性屬性」主題。

##  <a name="getindexinfo"></a>CDaoRecordset：： GetIndexInfo

呼叫這個成員函式，以取得有關記錄集基礎資料表中所定義之索引的各種資訊類型。

```
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
資料表的索引集合中以零為起始的索引，用於依數位位置查閱。

*indexinfo*<br/>
[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構的參考。

*dwInfoOptions*<br/>
指定要抓取之索引相關資訊的選項。 這裡列出可用的選項，以及它們導致函式傳回的內容。 為了達到最佳效能，請只取出您需要的資訊層級：

- `AFX_DAO_PRIMARY_INFO` （預設）名稱、欄位資訊、欄位

- `AFX_DAO_SECONDARY_INFO` 主要資訊，加上： Primary、Unique、叢集、IgnoreNulls、Required、Foreign

- `AFX_DAO_ALL_INFO` 主要和次要資訊，加上：相異計數

*lpszName*<br/>
索引物件名稱的指標，用於依名稱查閱。

### <a name="remarks"></a>備註

函式的其中一個版本可讓您依其在集合中的位置來查閱索引。 另一個版本可讓您依名稱查閱索引。

如需所傳回信息的描述，請參閱[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構。 此結構的成員會對應至*dwInfoOptions*的描述中所列的資訊專案。 當您要求某一層級的資訊時，您也會取得任何先前層級的資訊。

如需相關資訊，請參閱 DAO 說明中的「屬性屬性」主題。

##  <a name="getlastmodifiedbookmark"></a>CDaoRecordset：： GetLastModifiedBookmark

呼叫這個成員函式，以抓取最近新增或更新記錄的書簽。

```
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>傳回值

包含書簽的 `COleVariant`，指出最近新增或變更的記錄。

### <a name="remarks"></a>備註

建立或開啟記錄集物件時，它的每個記錄都已有唯一的書簽（如果支援的話）。 呼叫[GetBookmark](#getbookmark)來判斷記錄集是否支援書簽。 如果記錄集不支援書簽，則會擲回 `CDaoException`。

當您新增記錄時，它會出現在記錄集的結尾，而不是目前的記錄。 若要將新記錄設為目前，請呼叫 `GetLastModifiedBookmark`，然後呼叫 `SetBookmark` 以返回新加入的記錄。

如需相關資訊，請參閱 DAO 說明中的「LastModified 屬性」主題。

##  <a name="getlockingmode"></a>CDaoRecordset：： GetLockingMode

呼叫這個成員函式，以判斷記錄集的作用中鎖定類型。

```
BOOL GetLockingMode();
```

### <a name="return-value"></a>傳回值

如果鎖定的類型是封閉式，則為非零，如果是開放式記錄鎖定則為0。

### <a name="remarks"></a>備註

當封閉式鎖定生效時，只要呼叫[Edit](#edit)成員函式，就會鎖定包含所編輯記錄的資料頁面。 當您呼叫[Update](#update)或[Close](#close)成員函式或任何移動或尋找作業時，此頁面就會解除鎖定。

當開放式鎖定生效時，只有在使用 `Update` 成員函式更新記錄時，才會鎖定包含記錄的資料頁面。

使用 ODBC 資料來源時，鎖定模式一律是開放式的。

如需相關資訊，請參閱 DAO 說明中的「LockEdits 屬性」和「多使用者應用程式的鎖定行為」主題。

##  <a name="getname"></a>CDaoRecordset：： GetName

呼叫這個成員函式以抓取記錄集的名稱。

```
CString GetName();
```

### <a name="return-value"></a>傳回值

包含記錄集名稱的 `CString`。

### <a name="remarks"></a>備註

記錄集的名稱必須以字母開頭，且最多可包含40個字元。 它可以包含數位和底線字元，但不能包含標點符號或空格。

如需相關資訊，請參閱 DAO 說明中的「名稱屬性」主題。

##  <a name="getparamvalue"></a>CDaoRecordset：： GetParamValue

呼叫這個成員函式，以抓取基礎 DAOParameter 物件中所儲存之指定參數的目前值。

```
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
基礎 DAOParameter 物件中參數的數位位置。

*lpszName*<br/>
您想要其值的參數名稱。

### <a name="return-value"></a>傳回值

[COleVariant](../../mfc/reference/colevariant-class.md)類別的物件，其中包含參數的值。

### <a name="remarks"></a>備註

您可以依名稱或其在集合中的數位位置來存取參數。

如需相關資訊，請參閱 DAO 說明中的「參數物件」主題。

##  <a name="getpercentposition"></a>CDaoRecordset：： GetPercentPosition

使用動態集型別或快照集型別記錄集時，如果您在完全填入記錄集之前呼叫 `GetPercentPosition`，則移動量會相對於透過呼叫[GetRecordCount](#getrecordcount)所指出的存取記錄數目。

```
float GetPercentPosition();
```

### <a name="return-value"></a>傳回值

介於0和100之間的數位，表示記錄集物件中目前記錄的大約位置，以記錄集內的記錄百分比為基礎。

### <a name="remarks"></a>備註

您可以藉由呼叫[MoveLast](#movelast)來完成所有記錄集的填入，以移至最後一筆記錄，但這可能需要相當長的時間。

您可以在所有三種類型的記錄集物件上呼叫 `GetPercentPosition`，包括沒有索引的資料表。 不過，您無法在順向滾動快照集上，或在從對外部資料庫的傳遞查詢中開啟的記錄集上，呼叫 `GetPercentPosition`。 如果沒有目前的記錄，或他目前的記錄已刪除，則會擲回 `CDaoException`。

如需相關資訊，請參閱 DAO 說明中的「PercentPosition 屬性」主題。

##  <a name="getrecordcount"></a>CDaoRecordset：： GetRecordCount

呼叫這個成員函式可找出已存取記錄集中的多少筆記錄。

```
long GetRecordCount();
```

### <a name="return-value"></a>傳回值

傳回在記錄集物件中存取的記錄數目。

### <a name="remarks"></a>備註

`GetRecordCount` 不會指出有多少記錄包含在動態集類型或快照集類型的記錄集中，直到所有記錄都已存取為止。 這個成員函數呼叫可能需要相當長的時間才能完成。

一旦存取最後一筆記錄，傳回值就會指出記錄集中未刪除之記錄的總數。 若要強制存取最後一筆記錄，請通話記錄集的 `MoveLast` 或 `FindLast` 成員函式。 您也可以使用 SQL 計數來判斷查詢將傳回的大約記錄數目。

當您的應用程式刪除動態集型別記錄集中的記錄時，`GetRecordCount` 的傳回值會減少。 不過，除非目前的記錄位於已刪除的記錄，否則 `GetRecordCount` 不會反映其他使用者刪除的記錄。 如果您執行的交易會影響記錄計數，然後再回復交易，`GetRecordCount` 將不會反映剩餘記錄的實際數目。

快照集類型記錄集中 `GetRecordCount` 的值不會受到基礎資料表中的變更所影響。

資料表類型記錄集的 `GetRecordCount` 值會反映資料表中的大約記錄數目，並會在加入和刪除資料表記錄時立即受到影響。

沒有記錄的記錄集會傳回0值。 使用附加的資料表或 ODBC 資料庫時，`GetRecordCount` 一律會傳回-1。 在記錄集上呼叫 `Requery` 成員函式會重設 `GetRecordCount` 的值，就如同重新執行查詢一樣。

如需相關資訊，請參閱 DAO 說明中的「RecordCount 屬性」主題。

##  <a name="getsql"></a>CDaoRecordset：： GetSQL

呼叫這個成員函式，以取得在開啟記錄集的記錄時，用來選取它的 SQL 語句。

```
CString GetSQL() const;
```

### <a name="return-value"></a>傳回值

包含 SQL 語句的 `CString`。

### <a name="remarks"></a>備註

這通常會是 SQL **SELECT**語句。

`GetSQL` 所傳回的字串，通常與您在*lpszSQL*參數中傳遞給[Open](#open)成員函式的任何字串不相同。 這是因為記錄集會根據您傳遞給 `Open`的內容、您使用 ClassWizard 所指定的內容，以及您在[m_strFilter](#m_strfilter)和[m_strSort](#m_strsort)資料成員中指定的內容，來建立完整的 SQL 語句。

> [!NOTE]
>  只有在呼叫 `Open`之後，才呼叫這個成員函式。

如需相關資訊，請參閱 DAO 說明中的「SQL 屬性」主題。

##  <a name="gettype"></a>CDaoRecordset：： GetType

在開啟記錄集之後呼叫這個成員函式，以判斷記錄集物件的類型。

```
short GetType();
```

### <a name="return-value"></a>傳回值

下列其中一個值，表示記錄集的類型：

- `dbOpenTable` 資料表類型記錄集

- `dbOpenDynaset` 的動態集類型記錄集

- `dbOpenSnapshot` 快照類型記錄集

### <a name="remarks"></a>備註

如需相關資訊，請參閱 DAO 說明中的「類型屬性」主題。

##  <a name="getvalidationrule"></a>CDaoRecordset：： GetValidationRule

呼叫這個成員函式，以判斷用來驗證資料的規則。

```
CString GetValidationRule();
```

### <a name="return-value"></a>傳回值

`CString` 物件，其中包含值，可在記錄變更或加入至資料表時，驗證其中的資料。

### <a name="remarks"></a>備註

此規則是以文字為基礎，而且會在每次基礎資料表變更時套用。 如果資料不合法，則 MFC 會擲回例外狀況。 傳回的錯誤訊息是基礎欄位物件的 [內容] 屬性的文字（如果有指定），或是基礎欄位物件的 [ValidationRule] 屬性所指定之運算式的文字。 您可以呼叫[GetValidationText](#getvalidationtext)來取得錯誤訊息的文字。

例如，記錄中需要月份日期的欄位可能會有一項驗證規則，例如「在1到31之間的日期」。

如需相關資訊，請參閱 DAO 說明中的「ValidationRule 屬性」主題。

##  <a name="getvalidationtext"></a>CDaoRecordset：： GetValidationText

呼叫這個成員函式可抓取基礎欄位物件的 [內容] 屬性的文字。

```
CString GetValidationText();
```

### <a name="return-value"></a>傳回值

`CString` 物件，其中包含欄位的值不符合基礎欄位物件的驗證規則時所顯示的訊息文字。

### <a name="remarks"></a>備註

如需相關資訊，請參閱 DAO 說明中的「有效性屬性」主題。

##  <a name="isbof"></a>CDaoRecordset：： IsBOF

請先呼叫這個成員函式，然後再從記錄中進行滾動，以瞭解您是否已經在記錄集的第一筆記錄之前。

```
BOOL IsBOF() const;
```

### <a name="return-value"></a>傳回值

如果記錄集不包含任何記錄，或如果您在第一筆記錄之前向前滾動，則為非零。否則為0。

### <a name="remarks"></a>備註

您也可以呼叫 `IsBOF` 以及 `IsEOF`，以判斷記錄集是否包含任何記錄或是否為空白。 在您呼叫 `Open`之後，如果記錄集沒有包含任何記錄，`IsBOF` 會傳回非零值。 當您開啟至少有一筆記錄的記錄集時，第一筆記錄是目前的記錄，`IsBOF` 傳回0。

如果第一筆記錄是目前的記錄，而您呼叫 `MovePrev`，`IsBOF` 後續會傳回非零值。 如果 `IsBOF` 傳回非零值，而您呼叫 `MovePrev`，則會擲回例外狀況。 如果 `IsBOF` 傳回非零值，則表示目前的記錄未定義，而且任何需要目前記錄的動作都會導致例外狀況。

特定方法對 `IsBOF` 和 `IsEOF` 設定的影響：

- 在內部呼叫 `Open*` 會藉由呼叫 `MoveFirst`，使記錄集中的第一筆記錄成為目前的記錄。 因此，在空的記錄集上呼叫 `Open` 會導致 `IsBOF` 和 `IsEOF` 傳回非零值。 （請參閱下表以瞭解失敗的 `MoveFirst` 或 `MoveLast` 呼叫的行為）。

- 成功找到記錄的所有移動作業都會導致 `IsBOF` 和 `IsEOF` 都傳回0。

- `AddNew` 呼叫，後面接著可成功插入新記錄的 `Update` 呼叫，會導致 `IsBOF` 傳回0，但只有在 `IsEOF` 已為非零值時。 `IsEOF` 的狀態一定會保持不變。 如 Microsoft Jet 資料庫引擎所定義，空的記錄集目前的記錄指標位於檔案的結尾，因此任何新的記錄都會插入到目前的記錄之後。

- 任何 `Delete` 呼叫，即使它只會從記錄集移除剩餘的記錄，也不會變更 `IsBOF` 或 `IsEOF`的值。

下表顯示 `IsBOF`/ `IsEOF`的不同組合所允許的移動作業。

||MoveFirst、MoveLast|MovePrev<br /><br /> 移動 < 0|移動0|MoveNext<br /><br /> 移動 > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= 非零，<br /><br /> `IsEOF`=0|允許|例外狀況|例外狀況|允許|
|`IsBOF`=0,<br /><br /> `IsEOF`= 非零|允許|允許|例外狀況|例外狀況|
|兩者皆非零|例外狀況|例外狀況|例外狀況|例外狀況|
|兩者都是0|允許|允許|允許|允許|

允許移動作業並不表示作業會成功找出記錄。 它只會指出嘗試執行指定的移動作業，而不會產生例外狀況。 `IsBOF` 和 `IsEOF` 成員函式的值可能會因嘗試移動而變更。

下表顯示在 `IsBOF` 和 `IsEOF` 設定的值上找不到記錄的移動作業效果。

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|零下|零下|
|`Move` 0|沒有變更|沒有變更|
|`MovePrev`，`Move` < 0|零下|沒有變更|
|`MoveNext`，`Move` > 0|沒有變更|零下|

如需相關資訊，請參閱 DAO 說明中的 "BOF，EOF Properties" 主題。

##  <a name="isdeleted"></a>CDaoRecordset：： IsDeleted

呼叫這個成員函式，以判斷目前的記錄是否已刪除。

```
BOOL IsDeleted() const;
```

### <a name="return-value"></a>傳回值

如果記錄集位於已刪除的記錄上，則為非零。否則為0。

### <a name="remarks"></a>備註

如果您流覽至記錄，而 `IsDeleted` 傳回 TRUE （非零），則您必須先滾動到另一筆記錄，才能執行任何其他記錄集作業。

> [!NOTE]
>  您不需要檢查快照集或資料表類型記錄集中記錄的已刪除狀態。 因為無法從快照集刪除記錄，所以不需要呼叫 `IsDeleted`。 對於資料表類型的記錄集，已刪除的記錄實際上會從記錄集中移除。 一旦刪除了一筆記錄（不論是由您、另一個使用者或另一個記錄集），您就無法回復至該記錄。 因此，不需要呼叫 `IsDeleted`。

當您從動態集刪除記錄時，它會從記錄集中移除，而且您無法回復至該記錄。 不過，如果動態集內的記錄是由另一位使用者或另一個記錄集的相同資料表刪除，則當您稍後滾動至該記錄時，`IsDeleted` 會傳回 TRUE。

如需相關資訊，請參閱 DAO 說明中的「刪除方法」、「LastModified 屬性」和「EditMode 屬性」主題。

##  <a name="iseof"></a>CDaoRecordset：： IsEOF

當您從記錄中滾動記錄來呼叫這個成員函式，以瞭解您是否已超過記錄集的最後一筆記錄。

```
BOOL IsEOF() const;
```

### <a name="return-value"></a>傳回值

如果記錄集不包含任何記錄，或如果您已滾動到最後一筆記錄之外，則為非零。否則為0。

### <a name="remarks"></a>備註

您也可以呼叫 `IsEOF` 來判斷記錄集是否包含任何記錄或是否為空白。 在您呼叫 `Open`之後，如果記錄集沒有包含任何記錄，`IsEOF` 會傳回非零值。 當您開啟至少有一筆記錄的記錄集時，第一筆記錄是目前的記錄，`IsEOF` 傳回0。

當您呼叫 `MoveNext`時，如果最後一筆記錄是目前的記錄，`IsEOF` 後續會傳回非零值。 如果 `IsEOF` 傳回非零值，而您呼叫 `MoveNext`，則會擲回例外狀況。 如果 `IsEOF` 傳回非零值，則表示目前的記錄未定義，而且任何需要目前記錄的動作都會導致例外狀況。

特定方法對 `IsBOF` 和 `IsEOF` 設定的影響：

- 在內部呼叫 `Open` 會藉由呼叫 `MoveFirst`，使記錄集中的第一筆記錄成為目前的記錄。 因此，在空的記錄集上呼叫 `Open` 會導致 `IsBOF` 和 `IsEOF` 傳回非零值。 （請參閱下表以瞭解失敗 `MoveFirst` 呼叫的行為）。

- 成功找到記錄的所有移動作業都會導致 `IsBOF` 和 `IsEOF` 都傳回0。

- `AddNew` 呼叫，後面接著可成功插入新記錄的 `Update` 呼叫，會導致 `IsBOF` 傳回0，但只有在 `IsEOF` 已為非零值時。 `IsEOF` 的狀態一定會保持不變。 如 Microsoft Jet 資料庫引擎所定義，空的記錄集目前的記錄指標位於檔案的結尾，因此任何新的記錄都會插入到目前的記錄之後。

- 任何 `Delete` 呼叫，即使它只會從記錄集移除剩餘的記錄，也不會變更 `IsBOF` 或 `IsEOF`的值。

下表顯示 `IsBOF`/ `IsEOF`的不同組合所允許的移動作業。

||MoveFirst、MoveLast|MovePrev<br /><br /> 移動 < 0|移動0|MoveNext<br /><br /> 移動 > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= 非零，<br /><br /> `IsEOF`=0|允許|例外狀況|例外狀況|允許|
|`IsBOF`=0,<br /><br /> `IsEOF`= 非零|允許|允許|例外狀況|例外狀況|
|兩者皆非零|例外狀況|例外狀況|例外狀況|例外狀況|
|兩者都是0|允許|允許|允許|允許|

允許移動作業並不表示作業會成功找出記錄。 它只會指出嘗試執行指定的移動作業，而不會產生例外狀況。 `IsBOF` 和 `IsEOF` 成員函式的值可能會因嘗試移動而變更。

下表顯示在 `IsBOF` 和 `IsEOF` 設定的值上找不到記錄的移動作業效果。

||IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|零下|零下|
|`Move` 0|沒有變更|沒有變更|
|`MovePrev`，`Move` < 0|零下|沒有變更|
|`MoveNext`，`Move` > 0|沒有變更|零下|

如需相關資訊，請參閱 DAO 說明中的 "BOF，EOF Properties" 主題。

##  <a name="isfielddirty"></a>CDaoRecordset：： IsFieldDirty

呼叫這個成員函式，以判斷動態集的指定欄位資料成員是否已標示為「已變更」（已變更）。

```
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
您想要檢查其狀態之欄位資料成員的指標，或為 Null 以判斷是否有任何欄位已變更。

### <a name="return-value"></a>傳回值

如果指定的欄位資料成員標示為中途，則為非零;否則為0。

### <a name="remarks"></a>備註

當目前的記錄是透過呼叫 `CDaoRecordset` 的 `Update` 成員函式（在呼叫 `Edit` 或 `AddNew`之後）進行更新時，所有中途欄位資料成員中的資料都會傳送至資料來源上的記錄。 透過這種知識，您可以採取進一步的步驟，例如 unflagging 欄位資料成員，以標記資料行，使其不會寫入至資料來源。

`IsFieldDirty` 是透過 `DoFieldExchange`來執行。

##  <a name="isfieldnull"></a>CDaoRecordset：： IsFieldNull

呼叫這個成員函式，以判斷是否已將記錄集的指定欄位資料成員標示為 Null。

```
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
您想要檢查其狀態之欄位資料成員的指標，或為 Null 以判斷是否有任何欄位為 Null。

### <a name="return-value"></a>傳回值

如果指定的欄位資料成員標示為 Null，則為非零;否則為0。

### <a name="remarks"></a>備註

（在資料庫術語中，Null 表示「沒有值」，而且與中C++的 null 不同）。如果欄位資料成員標示為 Null，它會被視為目前記錄中沒有任何值的資料行。

> [!NOTE]
>  在某些情況下，使用 `IsFieldNull` 可能會沒有效率，如下列程式碼範例所示：

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
>  如果您使用動態記錄系結，而不是衍生自 `CDaoRecordset`，請務必使用 VT_Null，如範例中所示。

##  <a name="isfieldnullable"></a>CDaoRecordset：： IsFieldNullable

呼叫這個成員函式，以判斷指定的欄位資料成員是否為 "nullable" （可以設定為 Null 值;C++ Null 與 null 不同，在資料庫術語中，表示「沒有值」）。

```
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>參數

*pv*<br/>
您想要檢查其狀態之欄位資料成員的指標，或為 Null 以判斷是否有任何欄位為 Null。

### <a name="return-value"></a>傳回值

如果指定的欄位資料成員可以設為 Null，則為非零。否則為0。

### <a name="remarks"></a>備註

不可以是 Null 的欄位必須有值。 如果您嘗試在加入或更新記錄時，將這類欄位設定為 Null，則資料來源會拒絕新增或更新，而且 `Update` 將會擲回例外狀況。 當您呼叫 `Update`，而不是呼叫 `SetFieldNull`時，就會發生例外狀況。

##  <a name="isopen"></a>CDaoRecordset：： IsOpen

呼叫這個成員函式，以判斷記錄集是否已開啟。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果先前已通話記錄集物件的 `Open` 或 `Requery` 成員函式，而且尚未關閉記錄集，則為非零。否則為0。

### <a name="remarks"></a>備註

##  <a name="m_bcheckcachefordirtyfields"></a>CDaoRecordset：： m_bCheckCacheForDirtyFields

包含旗標，指出快取的欄位是否會自動標示為已變更（已變更）和 Null。

### <a name="remarks"></a>備註

旗標預設為 TRUE。 此資料成員中的設定會控制整個雙重緩衝機制。 如果您將旗標設定為 TRUE，就可以使用 DFX 機制，逐一關閉每個欄位的快取。 如果您將旗標設定為 FALSE，您必須呼叫 `SetFieldDirty` 並自行 `SetFieldNull`。

請先設定這個資料成員，再呼叫 `Open`。 這項機制主要是為了方便使用。 效能可能會變慢，因為在進行變更時，會將欄位的雙重緩衝處理。

##  <a name="m_nfields"></a>CDaoRecordset：： m_nFields

包含記錄集類別中的欄位資料成員數目，以及記錄集從資料來源選取的資料行數目。

### <a name="remarks"></a>備註

記錄集類別的函式必須使用正確的靜態系結欄位數目來初始化 `m_nFields`。 當您使用它來宣告記錄集類別時，ClassWizard 會為您寫入此初始化。 您也可以手動撰寫它。

架構會使用這個數位來管理欄位資料成員與資料來源上目前記錄之對應資料行之間的互動。

> [!NOTE]
>  這個數位必須對應至使用參數 `CDaoFieldExchange::outputColumn`呼叫 `SetFieldType` 之後，在 `DoFieldExchange` 中註冊的輸出資料行數目。

您可以透過 `CDaoRecordset::GetFieldValue` 和 `CDaoRecordset::SetFieldValue`，以動態方式系結資料行。 如果您這樣做，就不需要遞增 `m_nFields` 中的計數來反映 `DoFieldExchange` 成員函式中的 DFX 函式呼叫數目。

##  <a name="m_nparams"></a>CDaoRecordset：： m_nParams

包含記錄集類別中的參數資料成員數目，也就是與記錄集的查詢一起傳遞的參數數目。

### <a name="remarks"></a>備註

如果您的記錄集類別具有任何參數資料成員，則類別的函式必須使用正確的數位來初始化*m_nParams* 。 *M_nParams*的值預設為0。 如果您加入參數資料成員（必須手動執行），您也必須手動在類別的函式中加入初始化，以反映參數的數目（至少必須與*m_strFilter*或*m_strSort*字串中 ' ' 預留位置的數目一樣大）。

架構在參數化記錄集的查詢時，會使用這個數位。

> [!NOTE]
>  這個數位必須對應至使用參數 `CFieldExchange::param`呼叫 `SetFieldType` 之後，在 `DoFieldExchange` 中註冊的 "params" 數目。

如需相關資訊，請參閱 DAO 說明中的「參數物件」主題。

##  <a name="m_pdaorecordset"></a>CDaoRecordset：： m_pDAORecordset

包含 `CDaoRecordset` 物件基礎之 DAO 記錄集物件的 OLE 介面指標。

### <a name="remarks"></a>備註

如果您需要直接存取 DAO 介面，請使用此指標。

如需相關資訊，請參閱 DAO 說明中的「記錄集物件」主題。

##  <a name="m_pdatabase"></a>CDaoRecordset：： m_pDatabase

包含將記錄集連接到資料來源之 `CDaoDatabase` 物件的指標。

### <a name="remarks"></a>備註

這個變數是以兩種方式設定。 一般而言，當您在建立記錄集物件時，會將指標傳遞至已經開啟的 `CDaoDatabase` 物件。 如果您改為傳遞 Null，`CDaoRecordset` 會為您建立 `CDaoDatabase` 物件，並開啟它。 不論是哪一種情況，`CDaoRecordset` 都會將指標儲存在此變數中。

一般來說，您不需要直接使用儲存在 `m_pDatabase`中的指標。 不過，如果您將自己的延伸模組寫入 `CDaoRecordset`，您可能需要使用指標。 例如，如果您擲回自己的 `CDaoException`，就可能需要指標。

如需相關資訊，請參閱 DAO 說明中的「資料庫物件」主題。

##  <a name="m_strfilter"></a>CDaoRecordset：： m_strFilter

包含用來建立 SQL 語句之**WHERE**子句的字串。

### <a name="remarks"></a>備註

它不包含用來篩選記錄**集的保留**字。 使用此資料成員不適用於資料表類型的記錄集。 使用 `CDaoQueryDef` 指標開啟記錄集時，`m_strFilter` 不會有任何作用。

當您篩選包含日期的欄位時，即使您未使用 Microsoft Jet database engine 的美國版本，也請使用美國日期格式（月-日）。否則，可能無法如預期般篩選資料。

如需相關資訊，請參閱 DAO 說明中的「篩選屬性」主題。

##  <a name="m_strsort"></a>CDaoRecordset：： m_strSort

包含包含 SQL 語句之**orderby**子句的字串，但不含保留字**orderby**。

### <a name="remarks"></a>備註

您可以針對動態集型別和快照集類型的 recordset 物件進行排序。

您無法排序資料表類型記錄集物件。 若要判斷資料表類型記錄集的排序次序，請呼叫[SetCurrentIndex](#setcurrentindex)。

使用 `CDaoQueryDef` 指標開啟記錄集時， *m_strSort*不會有任何作用。

如需相關資訊，請參閱 DAO 說明中的「排序屬性」主題。

##  <a name="move"></a>CDaoRecordset：： Move

呼叫這個成員函式，從目前的記錄中定位記錄集的*lRows*記錄。

```
virtual void Move(long lRows);
```

### <a name="parameters"></a>參數

*lRows*<br/>
要向前或向後移動的記錄數目。 正值會往前移動到記錄集的結尾。 負數值會向後移動，朝一開始。

### <a name="remarks"></a>備註

您可以向前或向後移動。 `Move( 1 )` 相當於 `MoveNext`，而 `Move( -1 )` 相當於 `MovePrev`。

> [!CAUTION]
>  如果記錄集沒有任何記錄，呼叫任何 `Move` 函數都會擲回例外狀況。 一般來說，請同時呼叫 `IsBOF` 和 `IsEOF` 再進行移動作業，以判斷記錄集是否有任何記錄。 在您呼叫 `Open` 或 `Requery`之後，請呼叫 `IsBOF` 或 `IsEOF`。

> [!NOTE]
>  如果您已滾動記錄集的開頭或結尾（`IsBOF` 或 `IsEOF` 傳回非零值），則 `Move` 的呼叫會擲回 `CDaoException`。

> [!NOTE]
>  如果您在目前的記錄正在更新或新增時呼叫任何 `Move` 函式，更新就會遺失而不發出警告。

當您在順向滾動快照集上呼叫 `Move` 時， *lRows*參數必須是正整數且不允許書簽，因此您只能向前移動。

若要將記錄集內的第一個、最後一個、下一個或上一個記錄設為目前的記錄，請呼叫 `MoveFirst`、`MoveLast`、`MoveNext`或 `MovePrev` 成員函式。

如需相關資訊，請參閱 DAO 說明中的「Move 方法」和「MoveFirst、MoveLast、MoveNext、MovePrevious 方法」主題。

##  <a name="movefirst"></a>CDaoRecordset：： MoveFirst

呼叫這個成員函式，使記錄集內的第一筆記錄（如果有的話）成為目前的記錄。

```
void MoveFirst();
```

### <a name="remarks"></a>備註

開啟記錄集之後，您不需要立即呼叫 `MoveFirst`。 此時，第一筆記錄（如果有的話）會自動成為目前的記錄。

> [!CAUTION]
>  如果記錄集沒有任何記錄，呼叫任何 `Move` 函數都會擲回例外狀況。 一般來說，請同時呼叫 `IsBOF` 和 `IsEOF` 再進行移動作業，以判斷記錄集是否有任何記錄。 在您呼叫 `Open` 或 `Requery`之後，請呼叫 `IsBOF` 或 `IsEOF`。

> [!NOTE]
>  如果您在目前的記錄正在更新或新增時呼叫任何 `Move` 函式，更新就會遺失而不發出警告。

使用 `Move` 函式，在不套用條件的情況下，從記錄移至記錄。 使用尋找作業來尋找符合特定條件的動態集型別或快照型別記錄集物件中的記錄。 若要找出資料表類型記錄集物件中的記錄，請呼叫 `Seek`。

如果記錄集參考資料表類型記錄集，則移動會遵循資料表的目前索引。 您可以使用基礎 DAO 物件的 Index 屬性來設定目前的索引。 如果您未設定目前的索引，則傳回記錄的順序會是未定義的。

如果您在以 SQL 查詢或 querydef 為基礎的記錄集物件上呼叫 `MoveLast`，則會強制執行查詢，並完整填入記錄集物件。

您無法使用順向滾動快照集來呼叫 `MoveFirst` 或 `MovePrev` 成員函式。

若要將記錄集物件中目前記錄的位置，向前或向後移動特定數目的記錄，請呼叫 `Move`。

如需相關資訊，請參閱 DAO 說明中的「Move 方法」和「MoveFirst、MoveLast、MoveNext、MovePrevious 方法」主題。

##  <a name="movelast"></a>CDaoRecordset：： MoveLast

呼叫這個成員函式，將記錄集內的最後一筆記錄（如果有的話）設為目前的記錄。

```
void MoveLast();
```

### <a name="remarks"></a>備註

> [!CAUTION]
>  如果記錄集沒有任何記錄，呼叫任何 `Move` 函數都會擲回例外狀況。 一般來說，請同時呼叫 `IsBOF` 和 `IsEOF` 再進行移動作業，以判斷記錄集是否有任何記錄。 在您呼叫 `Open` 或 `Requery`之後，請呼叫 `IsBOF` 或 `IsEOF`。

> [!NOTE]
>  如果您在目前的記錄正在更新或新增時呼叫任何 `Move` 函式，更新就會遺失而不發出警告。

使用 `Move` 函式，在不套用條件的情況下，從記錄移至記錄。 使用尋找作業來尋找符合特定條件的動態集型別或快照型別記錄集物件中的記錄。 若要找出資料表類型記錄集物件中的記錄，請呼叫 `Seek`。

如果記錄集參考資料表類型記錄集，則移動會遵循資料表的目前索引。 您可以使用基礎 DAO 物件的 Index 屬性來設定目前的索引。 如果您未設定目前的索引，則傳回記錄的順序會是未定義的。

如果您在以 SQL 查詢或 querydef 為基礎的記錄集物件上呼叫 `MoveLast`，則會強制執行查詢，並完整填入記錄集物件。

若要將記錄集物件中目前記錄的位置，向前或向後移動特定數目的記錄，請呼叫 `Move`。

如需相關資訊，請參閱 DAO 說明中的「Move 方法」和「MoveFirst、MoveLast、MoveNext、MovePrevious 方法」主題。

##  <a name="movenext"></a>CDaoRecordset：： MoveNext

呼叫這個成員函式，使記錄集中的下一筆記錄成為目前的記錄。

```
void MoveNext();
```

### <a name="remarks"></a>備註

建議您在嘗試移至上一筆記錄之前，先呼叫 `IsBOF`。 如果 `IsBOF` 傳回非零值（表示您已經在第一筆記錄之前滾動，或記錄集未選取任何記錄），呼叫 `MovePrev` 將會擲回 `CDaoException`。

> [!CAUTION]
>  如果記錄集沒有任何記錄，呼叫任何 `Move` 函數都會擲回例外狀況。 一般來說，請同時呼叫 `IsBOF` 和 `IsEOF` 再進行移動作業，以判斷記錄集是否有任何記錄。 在您呼叫 `Open` 或 `Requery`之後，請呼叫 `IsBOF` 或 `IsEOF`。

> [!NOTE]
>  如果您在目前的記錄正在更新或新增時呼叫任何 `Move` 函式，更新就會遺失而不發出警告。

使用 `Move` 函式，在不套用條件的情況下，從記錄移至記錄。 使用尋找作業來尋找符合特定條件的動態集型別或快照型別記錄集物件中的記錄。 若要找出資料表類型記錄集物件中的記錄，請呼叫 `Seek`。

如果記錄集參考資料表類型記錄集，則移動會遵循資料表的目前索引。 您可以使用基礎 DAO 物件的 Index 屬性來設定目前的索引。 如果您未設定目前的索引，則傳回記錄的順序會是未定義的。

若要將記錄集物件中目前記錄的位置，向前或向後移動特定數目的記錄，請呼叫 `Move`。

如需相關資訊，請參閱 DAO 說明中的「Move 方法」和「MoveFirst、MoveLast、MoveNext、MovePrevious 方法」主題。

##  <a name="moveprev"></a>CDaoRecordset：： MovePrev

呼叫這個成員函式，將記錄集內的上一個記錄設為目前的記錄。

```
void MovePrev();
```

### <a name="remarks"></a>備註

建議您在嘗試移至上一筆記錄之前，先呼叫 `IsBOF`。 如果 `IsBOF` 傳回非零值（表示您已經在第一筆記錄之前滾動，或記錄集未選取任何記錄），呼叫 `MovePrev` 將會擲回 `CDaoException`。

> [!CAUTION]
>  如果記錄集沒有任何記錄，呼叫任何 `Move` 函數都會擲回例外狀況。 一般來說，請同時呼叫 `IsBOF` 和 `IsEOF` 再進行移動作業，以判斷記錄集是否有任何記錄。 在您呼叫 `Open` 或 `Requery`之後，請呼叫 `IsBOF` 或 `IsEOF`。

> [!NOTE]
>  如果您在目前的記錄正在更新或新增時呼叫任何 `Move` 函式，更新就會遺失而不發出警告。

使用 `Move` 函式，在不套用條件的情況下，從記錄移至記錄。 使用尋找作業來尋找符合特定條件的動態集型別或快照型別記錄集物件中的記錄。 若要找出資料表類型記錄集物件中的記錄，請呼叫 `Seek`。

如果記錄集參考資料表類型記錄集，則移動會遵循資料表的目前索引。 您可以使用基礎 DAO 物件的 Index 屬性來設定目前的索引。 如果您未設定目前的索引，則傳回記錄的順序會是未定義的。

您無法使用順向滾動快照集來呼叫 `MoveFirst` 或 `MovePrev` 成員函式。

若要將記錄集物件中目前記錄的位置，向前或向後移動特定數目的記錄，請呼叫 `Move`。

如需相關資訊，請參閱 DAO 說明中的「Move 方法」和「MoveFirst、MoveLast、MoveNext、MovePrevious 方法」主題。

##  <a name="open"></a>CDaoRecordset：： Open

您必須呼叫這個成員函式，才能取出記錄集的記錄。

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

*nOpenType*<br/>
下列其中一個值：

- `dbOpenDynaset` 具有雙向滾動的動態類型記錄集。 這是預設值。

- `dbOpenTable` 具有雙向滾動的資料表類型記錄集。

- `dbOpenSnapshot` 具有雙向滾動的快照類型記錄集。

*lpszSQL*<br/>
包含下列其中一項的字串指標：

- Null 指標。

- 一或多個 tabledefs 和/或 querydefs 的名稱（以逗號分隔）。

- SQL **SELECT**語句（選擇性地使用 sql **WHERE**或**ORDERBY**子句）。

- 傳遞查詢。

*nOptions*<br/>
下面列出一或多個選項。 預設值為 0。 可能的值如下：

- `dbAppendOnly` 您只能附加新記錄（僅限動態集類型的記錄集）。 此選項表示實際上可能只會附加記錄。 MFC ODBC 資料庫類別具有 [僅限附加] 選項，可讓您抓取和附加記錄。

- `dbForwardOnly` 記錄集是順向的滾動快照。

- 如果另一位使用者正在變更您正在編輯的資料，`dbSeeChanges` 會產生例外狀況。

- `dbDenyWrite` 其他使用者無法修改或加入記錄。

- `dbDenyRead` 其他使用者無法查看記錄（僅限資料表類型記錄集）。

- `dbReadOnly` 您只能查看記錄;其他使用者可以修改它們。

- 允許 `dbInconsistent` 不一致的更新（僅限動態集類型的記錄集）。

- 僅允許 `dbConsistent` 一致的更新（僅限動態集類型的記錄集）。

> [!NOTE]
>  `dbConsistent` 和 `dbInconsistent` 的常數是互斥的。 您可以在指定的 `Open`實例中使用其中一種，但不能同時使用。

*pTableDef*<br/>
[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)物件的指標。 此版本僅適用于資料表類型的記錄集。 使用此選項時，不會使用用來建立 `CDaoRecordset` 的 `CDaoDatabase` 指標;而是使用 tabledef 所在的資料庫。

*pQueryDef*<br/>
[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)物件的指標。 此版本僅適用于動態集型別和快照集類型的記錄集。 使用此選項時，不會使用用來建立 `CDaoRecordset` 的 `CDaoDatabase` 指標;而是使用 querydef 所在的資料庫。

### <a name="remarks"></a>備註

在呼叫 `Open`之前，您必須先建立記錄集物件。 有幾個方式可做到這點：

- 當您建立記錄集物件時，請將指標傳遞至已經開啟的 `CDaoDatabase` 物件。

- 當您建立記錄集物件時，請將指標傳遞至未開啟的 `CDaoDatabase` 物件。 記錄集會開啟 `CDaoDatabase` 物件，但當記錄集物件關閉時，不會將它關閉。

- 當您建立記錄集物件時，傳遞 Null 指標。 記錄集物件會呼叫 `GetDefaultDBName` 來取得 Microsoft Access 的名稱。要開啟的 MDB 檔案。 然後，記錄集就會開啟 `CDaoDatabase` 物件，只要記錄集已開啟，它就會保持開啟狀態。 當您通話記錄集上的 `Close` 時，`CDaoDatabase` 物件也會關閉。

    > [!NOTE]
    >  當記錄集開啟 `CDaoDatabase` 物件時，它會開啟具有非獨佔存取權的資料來源。

對於使用*lpszSQL*參數的 `Open` 版本，一旦記錄集開啟，您就可以使用數種方式的其中一種來捕獲記錄。 第一個選項是在您的 `DoFieldExchange`中擁有 DFX 函數。 第二個選項是藉由呼叫 `GetFieldValue` 成員函式來使用動態繫結。 這些選項可以單獨執行或結合。 如果兩者結合在一起，您就必須在 `Open`的呼叫上自行傳入 SQL 語句。

當您使用 `Open` 在其中傳入 `CDaoTableDef` 物件的第二個版本時，產生的資料行將可供您透過 `DoFieldExchange` 和 DFX 機制進行系結，以及（或）透過 `GetFieldValue`動態系結。

> [!NOTE]
>  您只能使用資料表類型記錄集的 `CDaoTableDef` 物件來呼叫 `Open`。

當您使用 `Open` 傳入 `CDaoQueryDef` 物件的第三個版本時，將會執行該查詢，而產生的資料行則可供您透過 `DoFieldExchange` 和 DFX 機制進行系結，以及/或透過 `GetFieldValue`動態系結。

> [!NOTE]
>  您只能使用動態集型別和快照型別記錄集的 `CDaoQueryDef` 物件來呼叫 `Open`。

對於使用 `lpszSQL` 參數的第一個 `Open` 版本，會根據下表所示的準則來選取記錄。

|`lpszSQL` 參數的值|選取的記錄取決於|範例|
|--------------------------------------|----------------------------------------|-------------|
|NULL|`GetDefaultSQL`傳回的字串。||
|一或多個 tabledefs 和/或 querydef 名稱的逗號分隔清單。|`DoFieldExchange`中表示的所有資料行。|`"Customer"`|
|從資料表清單**中** **選取**資料行清單|指定之 tabledef 和/或 querydef （s）中的指定資料行。|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

平常的程式是將 Null 傳遞給 `Open`。在這種情況下，`Open` 會呼叫 `GetDefaultSQL`，這是在建立 `CDaoRecordset`衍生的類別時，ClassWizard 會產生的可覆寫成員函式。 這個值會提供您在 ClassWizard 中指定的 tabledef （s）和/或 querydef 名稱。 您可以改為在*lpszSQL*參數中指定其他資訊。

無論您傳遞哪一個，`Open` 都會針對查詢建立最終的 SQL 字串（字串可能會在您傳遞的*lpszSQL*字串後面加**上 Sql WHERE**和**ORDERBY**子句），然後執行查詢。 呼叫 `Open`之後，您可以藉由呼叫 `GetSQL` 來檢查結構化的字串。

記錄集類別的欄位資料成員會系結至選取的資料行。 如果傳回任何記錄，第一筆記錄就會成為目前的記錄。

如果您想要設定記錄集的選項，例如篩選或排序，請在建立記錄集物件之後，但是在呼叫 `Open`之前，設定 `m_strSort` 或 `m_strFilter`。 如果您想要在記錄集已開啟之後重新整理記錄集中的記錄，請呼叫 `Requery`。

如果您在動態集類型或快照集類型的記錄集上呼叫 `Open`，或如果資料來源參考的是 SQL 語句或代表附加資料表的 tabledef，您就無法使用類型引數的 `dbOpenTable`。如果您這樣做，MFC 會擲回例外狀況。 若要判斷 tabledef 物件是否代表附加的資料表，請建立[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)物件，並呼叫其[GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect)成員函式。

如果您想要在編輯或刪除相同的記錄時，將其他使用者或電腦上的其他程式所做的變更補漏設為，請使用 `dbSeeChanges` 旗標。 例如，如果兩個使用者開始編輯相同的記錄，則呼叫 `Update` 成員函式的第一個使用者就會成功。 當第二個使用者呼叫 `Update` 時，就會擲回 `CDaoException`。 同樣地，如果第二個使用者嘗試呼叫 `Delete` 來刪除記錄，而且第一個使用者已經變更，就會發生 `CDaoException`。

一般而言，如果使用者在更新時取得此 `CDaoException`，則您的程式碼應該會重新整理欄位的內容，並抓取新修改的值。 如果例外狀況發生在刪除的過程中，您的程式碼可能會向使用者顯示新的記錄資料，以及指出資料最近已變更的訊息。 此時，您的程式碼可以要求確認使用者仍然想要刪除該記錄。

> [!TIP]
>  當您的應用程式透過從 ODBC 資料來源開啟的記錄集進行單一傳遞時，請使用順向滾動選項（`dbForwardOnly`）來改善效能。

如需相關資訊，請參閱 DAO 說明中的「Openrecordset) 方法」主題。

##  <a name="requery"></a>CDaoRecordset：： Requery

呼叫這個成員函式以重建（重新整理）記錄集。

```
virtual void Requery();
```

### <a name="remarks"></a>備註

如果傳回任何記錄，第一筆記錄就會成為目前的記錄。

為了讓記錄集反映您或其他使用者對資料來源所做的新增和刪除，您必須藉由呼叫 `Requery`來重建記錄集。 如果記錄集是動態集，它會自動反映您或其他使用者對其現有記錄（但不是新增專案）所做的更新。 如果記錄集是快照，您必須呼叫 `Requery` 以反映其他使用者的編輯，以及新增和刪除。

針對動態集或快照，每當您想要使用參數值重建記錄集時，都可以呼叫 `Requery`。 設定新的篩選或排序，方法是在呼叫 `Requery`之前，設定[m_strFilter](#m_strfilter)和[m_strSort](#m_strsort) 。 呼叫 `Requery`之前，請先將新值指派給參數資料成員，以設定新的參數。

如果重建記錄集的嘗試失敗，就會關閉記錄集。 在您呼叫 `Requery`之前，您可以藉由呼叫[CanRestart](#canrestart)成員函式來判斷是否可以重新查詢記錄集。 `CanRestart` 不保證 `Requery` 會成功。

> [!CAUTION]
>  只有在您呼叫 `Open`之後，才 `Requery` 呼叫。

> [!NOTE]
>  呼叫重新[查詢](#requery)會變更 DAO 書簽。

如果呼叫 `CanRestart` 傳回0，而且您不能在資料表類型記錄集上使用它，您就無法在動態集類型或快照集類型的記錄集上呼叫 `Requery`。

如果 `IsBOF` 和 `IsEOF` 在呼叫 `Requery`之後傳回非零值，則查詢不會傳回任何記錄，而且記錄集不會包含任何資料。

如需相關資訊，請參閱 DAO 說明中的「重新查詢方法」主題。

##  <a name="seek"></a>CDaoRecordset：： Seek

呼叫這個成員函式，以在索引資料表類型記錄集物件中尋找符合目前索引之指定準則的記錄，並將它記錄為目前的記錄。

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

*lpszComparison*<br/>
下列其中一個字串運算式： "<"、"\<="、"="、"> =" 或 ">"。

*pKey1*<br/>
[COleVariant](../../mfc/reference/colevariant-class.md)的指標，其值對應至索引中的第一個欄位。 必要。

*pKey2*<br/>
`COleVariant` 的指標，其值對應至索引中的第二個欄位（如果有的話）。 預設值為 Null。

*pKey3*<br/>
`COleVariant` 的指標，其值對應至索引中的第三個欄位（如果有的話）。 預設值為 Null。

*pKeyArray*<br/>
Variant 陣列的指標。 陣列大小會對應至索引中的欄位數目。

*nKeys*<br/>
對應于陣列大小的整數，也就是索引中的欄位數目。

> [!NOTE]
>  請勿在索引鍵中指定萬用字元。 萬用字元會導致 `Seek` 不傳回相符的記錄。

### <a name="return-value"></a>傳回值

如果找到相符的記錄，則為非零，否則為0。

### <a name="remarks"></a>備註

使用 `Seek` 的第二個（陣列）版本來處理四個或更多欄位的索引。

`Seek` 在資料表類型的記錄集上啟用高效能索引搜尋。 您必須先呼叫 `SetCurrentIndex` 來設定目前的索引，才能呼叫 `Seek`。 如果索引識別不唯一的索引鍵欄位或欄位，`Seek` 會尋找符合準則的第一筆記錄。 如果您未設定索引，則會擲回例外狀況。

請注意，如果您未建立 UNICODE 記錄集，`COleVariant` 物件必須明確宣告為 ANSI。 這可以藉由使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **（** *lpszSrc* **，** *vtSrc* **）** 形式的函式，並將*vtSrc*設定為 `VT_BSTRT` （ANSI），或使用 `COleVariant` 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) **（** *lpszSrc* **，** *vtSrc* **）** ，並將*vtSrc*設定為 `VT_BSTRT`來完成這項作業。

當您呼叫 `Seek`時，您會傳遞一或多個索引鍵值和比較運算子（"<"、"\<="、"="、"> =" 或 ">"）。 `Seek` 會搜尋指定的索引鍵欄位，並尋找符合*lpszComparison*和*pKey1*所指定準則的第一筆記錄。 找到之後，`Seek` 會傳回非零值，並使該記錄成為目前的。 如果 `Seek` 找不到相符的結果，`Seek` 會傳回零，而且目前的記錄未定義。 直接使用 DAO 時，您必須明確檢查 NoMatch 屬性。

如果 `lpszComparison` 是 "="、"> =" 或 ">"，`Seek` 會從索引的開頭開始。 如果*lpszComparison*是 "<" 或 "< ="，`Seek` 會從索引的結尾開始，並向後搜尋，除非結尾有重複的索引項目。 在此情況下，`Seek` 會從索引結尾處的重複索引項目中的任意專案開始。

當您使用 `Seek`時，不一定要有目前的記錄。

若要在符合特定條件的動態類型或快照集類型記錄集中尋找記錄，請使用尋找作業。 若要包含所有記錄，而不只是符合特定條件的記錄，請使用移動作業從記錄移至記錄。

您無法在任何型別的附加資料表上呼叫 `Seek`，因為附加資料表必須以動態集型別或快照集型別記錄檔的形式開啟。 不過，如果您呼叫 `CDaoDatabase::Open` 直接開啟可安裝的 ISAM 資料庫，您可以在該資料庫中的資料表上呼叫 `Seek`，但效能可能會變慢。

如需相關資訊，請參閱 DAO 說明中的「搜尋方法」主題。

##  <a name="setabsoluteposition"></a>CDaoRecordset：： SetAbsolutePosition

設定記錄集物件目前記錄的相對記錄號碼。

```
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>參數

*lPosition*<br/>
對應至記錄集中目前記錄的序數位置。

### <a name="remarks"></a>備註

呼叫 `SetAbsolutePosition` 可讓您根據其在動態集型別或快照集型別記錄集中的序數位置，將目前的記錄指標放到特定記錄。 您也可以藉由呼叫[GetAbsolutePosition](#getabsoluteposition)來判斷目前的記錄數目。

> [!NOTE]
>  這個成員函式僅適用于動態集型別和快照型別記錄集。

基礎 DAO 物件的 AbsolutePosition 屬性值是以零為基底;設定為0時，是指記錄集內的第一筆記錄。 設定大於填入記錄數目的值，會導致 MFC 擲回例外狀況。 您可以藉由呼叫 `GetRecordCount` 成員函式，判斷記錄集中的已填入記錄數目。

如果目前的記錄已刪除，則不會定義 AbsolutePosition 屬性值，而且 MFC 會在參考時擲回例外狀況。 新的記錄會新增至序列的結尾。

> [!NOTE]
>  這個屬性不適合當做代理記錄號碼使用。 書簽仍然是保留並返回指定位置的建議方式，而且是將目前記錄放置在支援書簽的所有記錄集物件類型上的唯一方法。 特別是，指定記錄的位置在刪除之前的記錄會變更。 如果重新建立記錄集，也不保證指定的記錄會有相同的絕對位置，因為記錄集內個別記錄的順序並不保證，除非使用**ORDERBY**子句以 SQL 語句建立。

如需相關資訊，請參閱 DAO 說明中的「AbsolutePosition 屬性」主題。

##  <a name="setbookmark"></a>CDaoRecordset：： SetBookmark

呼叫這個成員函式，將記錄集放在包含指定書簽的記錄上。

```
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>參數

*varBookmark*<br/>
包含特定記錄之書簽值的[COleVariant](../../mfc/reference/colevariant-class.md)物件。

### <a name="remarks"></a>備註

建立或開啟記錄集物件時，它的每個記錄都已經有唯一的書簽。 您可以藉由呼叫 `GetBookmark` 並將值儲存至 `COleVariant` 物件，來抓取目前記錄的書簽。 您稍後可以使用已儲存的書簽值來呼叫 `SetBookmark`，以返回該記錄。

> [!NOTE]
>  呼叫重新[查詢](#requery)會變更 DAO 書簽。

請注意，如果您不是建立 UNICODE 記錄集，則 `COleVariant` 物件必須明確宣告為 ANSI。 這可以藉由使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **（** *lpszSrc* **，** *vtSrc* **）** 形式的函式，並將*vtSrc*設定為 `VT_BSTRT` （ANSI），或使用 `COleVariant` 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) **（** *lpszSrc* **，** *vtSrc* **）** ，並將*vtSrc*設定為 `VT_BSTRT`來完成這項作業。

如需相關資訊，請參閱 DAO 說明中的 < 書簽屬性和 Bookmarkable 屬性主題。

##  <a name="setcachesize"></a>CDaoRecordset：： SetCacheSize

呼叫這個成員函式，以設定要快取的記錄數目。

```
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>參數

*lSize*<br/>
指定記錄的數目。 一般的值為100。 設定為0會關閉快取。 設定必須介於5到1200筆記錄之間。 快取可能會使用大量的記憶體。

### <a name="remarks"></a>備註

快取是本機記憶體中的一個空間，其中保存最近從伺服器中取出的資料，因為在應用程式執行時，將會再次要求資料。 資料快取可改善應用程式的效能，這會透過動態集類型的記錄集物件，從遠端伺服器抓取資料。 當要求資料時，Microsoft Jet 資料庫引擎會先檢查快取中是否有要求的資料，而不是從伺服器抓取它，這會花費更多時間。 不是來自 ODBC 資料來源的資料不會儲存在快取中。

任何 ODBC 資料來源（例如附加資料表）都可以有本機快取。 若要建立快取，請從遠端資料源開啟記錄集物件，呼叫 `SetCacheSize` 並 `SetCacheStart` 成員函式，然後呼叫 `FillCache` 成員函式，或使用其中一個移動作業逐步執行記錄。 `SetCacheSize` 成員函式的*lSize*參數可以根據您的應用程式一次可處理的記錄數目。 例如，如果您使用記錄集作為要在螢幕上顯示的資料來源，您可以將 `SetCacheSize` *lSize*參數傳遞為20，一次顯示20筆記錄。

如需相關資訊，請參閱 DAO 說明中的「CacheSize，CacheStart 屬性」主題。

##  <a name="setcachestart"></a>CDaoRecordset：： SetCacheStart

呼叫這個成員函式，以指定要快取之記錄集中第一筆記錄的書簽。

```
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>參數

*varBookmark*<br/>
[COleVariant](../../mfc/reference/colevariant-class.md) ，指定要快取之記錄集中第一筆記錄的書簽。

### <a name="remarks"></a>備註

您可以將任何記錄的書簽值用於 `SetCacheStart` 成員函式的*varBookmark*參數。 請使用目前的記錄來建立記錄，並以[SetBookmark](#setbookmark)為該記錄建立書簽，並傳遞書簽值做為 `SetCacheStart` 成員函式的參數。

Microsoft Jet 資料庫引擎會向快取中的快取範圍要求記錄，並向伺服器要求快取範圍以外的記錄。

從快取中取出的記錄不會反映其他使用者同時對來源資料所做的變更。

若要強制更新所有快取的資料，請將 `SetCacheSize` 的*lSize*參數傳遞為0，再以原先要求的快取大小再次呼叫 `SetCacheSize`，然後再呼叫 `FillCache` 成員函式。

請注意，如果您不是建立 UNICODE 記錄集，則 `COleVariant` 物件必須明確宣告為 ANSI。 這可以藉由使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **（** *lpszSrc* **，** *vtSrc* **）** 形式的函式，並將*vtSrc*設定為 `VT_BSTRT` （ANSI），或使用 `COleVariant` 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) **（** *lpszSrc* **，** *vtSrc* **）** ，並將*vtSrc*設定為 `VT_BSTRT`來完成這項作業。

如需相關資訊，請參閱 DAO 說明中的 < CacheStart 屬性 CacheSize 主題。

##  <a name="setcurrentindex"></a>CDaoRecordset：： SetCurrentIndex

呼叫這個成員函式可設定資料表類型記錄集的索引。

```
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>參數

*lpszIndex*<br/>
包含要設定之索引名稱的指標。

### <a name="remarks"></a>備註

基表中的記錄不會以任何特定順序儲存。 設定索引會變更從資料庫傳回的記錄順序，但不會影響記錄的儲存順序。 指定的索引必須已經定義。 如果您嘗試使用不存在的索引物件，或當您呼叫[Seek](#seek)時未設定索引，MFC 會擲回例外狀況。

您可以藉由呼叫[CDaoTableDef：： CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex)並將新索引附加至基礎 Tabledef 的索引集合，藉由呼叫[CDaoTableDef：： Append](../../mfc/reference/cdaotabledef-class.md#append)，然後重新開啟記錄集，來建立資料表的新索引。

從資料表類型記錄集傳回的記錄只能由針對基礎 tabledef 定義的索引進行排序。 若要以其他順序排序記錄，您可以使用儲存在[CDaoRecordset：： m_strSort](#m_strsort)中的 SQL **ORDERBY**子句來開啟動態集類型或快照集類型的記錄集。

如需相關資訊，請參閱 DAO 說明中的「索引物件」和「目前索引」的定義主題。

##  <a name="setfielddirty"></a>CDaoRecordset：： SetFieldDirty

呼叫這個成員函式，以將記錄集的欄位資料成員標示為已變更或保持不變。

```
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>參數

*pv*<br/>
包含記錄集內欄位資料成員的位址，或為 Null。 如果是 Null，則記錄集中的所有欄位資料成員都會加上旗標。 （C++ Null 與資料庫術語中的 null 不同，這表示「沒有任何值」）。

*bDirty*<br/>
如果欄位資料成員要標示為「已變更」，則為 TRUE。 如果欄位資料成員要標示為「清除」（未變更），則為 FALSE。

### <a name="remarks"></a>備註

將欄位標記為未變更可確保欄位不會更新。

架構會標示已變更的欄位資料成員，以確保 DAO 記錄欄位交換（DFX）機制會將它們寫入資料來源上的記錄。 變更欄位的值通常會自動將欄位設定為中途，因此您不常需要自行呼叫 `SetFieldDirty`，但有時您可能會想要確保不論欄位資料成員中的值為何，都會明確更新或插入資料行。 DFX 機制也會採用 PSEUDONull 的使用。 如需詳細資訊，請參閱[CDaoFieldExchange：： m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用雙重緩衝機制，則變更欄位的值時，不會自動將欄位設定為「中途」。 在此情況下，必須將欄位明確設定為已變更。 包含在[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中的旗標會控制此自動欄位檢查。

> [!NOTE]
>  只有在您呼叫了[Edit](#edit)或[AddNew](#addnew)之後，才會呼叫此成員函式。

針對函式的第一個引數使用 Null，會將函式套用至所有 `outputColumn` 欄位，而不是 `CDaoFieldExchange`中的**param**欄位。 例如，呼叫

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

只會將 `outputColumn` 欄位設定為 Null;**param**欄位不會受到影響。

若要使用**參數**，您必須提供您想要處理之個別**參數**的實際位址，例如：

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

這表示您無法將所有**param**欄位設定為 Null，就像您可以 `outputColumn` 欄位一樣。

`SetFieldDirty` 是透過 `DoFieldExchange`來執行。

##  <a name="setfieldnull"></a>CDaoRecordset：： SetFieldNull

呼叫這個成員函式，將記錄集的欄位資料成員標示為 Null （明確沒有值）或為非 Null。

```
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>參數

*pv*<br/>
包含記錄集內欄位資料成員的位址，或為 Null。 如果是 Null，則記錄集中的所有欄位資料成員都會加上旗標。 （C++ Null 與資料庫術語中的 null 不同，這表示「沒有任何值」）。

*bNull*<br/>
如果欄位資料成員要標示為沒有值，則為非零（Null）。 如果欄位資料成員要標記為非 Null，則為0。

### <a name="remarks"></a>備註

`SetFieldNull` 用於 `DoFieldExchange` 機制中系結的欄位。

當您將新記錄加入至記錄集時，所有欄位資料成員一開始都會設定為 Null 值，並標示為「已變更」。 當您從資料來源抓取記錄時，其資料行可能已經有值或為 Null。 如果不適合將欄位設為 Null，則會擲回[CDaoException](../../mfc/reference/cdaoexception-class.md) 。

如果您使用雙重緩衝機制，例如，如果您特別想要將目前記錄的欄位指定為不具有值，請呼叫 `SetFieldNull` 並將*bNull*設定為 TRUE，以將其標示為 Null。 如果欄位先前標記為 Null，而您現在想要為其指定值，只要設定其新值即可。 您不需要移除具有 `SetFieldNull`的 Null 旗標。 若要判斷欄位是否允許為 Null，請呼叫[IsFieldNullable](#isfieldnullable)。

如果您不是使用雙重緩衝機制，則變更欄位的值不會自動將欄位設定為 [已變更] 和 [非 Null]。 您必須明確地將欄位設定為 [已變更] 和 [非 Null]。 包含在[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中的旗標會控制此自動欄位檢查。

DFX 機制會採用 PSEUDONull 的使用。 如需詳細資訊，請參閱[CDaoFieldExchange：： m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

> [!NOTE]
>  只有在您呼叫了[Edit](#edit)或[AddNew](#addnew)之後，才會呼叫此成員函式。

針對函式的第一個引數使用 Null，只會將函式套用至 `outputColumn` 欄位，而不會套用 `CDaoFieldExchange`中的**參數**欄位。 例如，呼叫

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

只會將 `outputColumn` 欄位設定為 Null;**param**欄位不會受到影響。

##  <a name="setfieldvalue"></a>CDaoRecordset：： SetFieldValue

呼叫這個成員函式可依序數位置或變更字串的值，來設定欄位的值。

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

*lpszName*<br/>
包含欄位名稱之字串的指標。

*varValue*<br/>
包含欄位內容值之[COleVariant](../../mfc/reference/colevariant-class.md)物件的參考。

*nIndex*<br/>
整數，表示欄位在記錄集的 Fields 集合中的序數位置（以零為基底）。

*lpszValue*<br/>
包含欄位內容值之字串的指標。

### <a name="remarks"></a>備註

使用 `SetFieldValue` 和[GetFieldValue](#getfieldvalue) ，在執行時間以動態方式系結欄位，而不是使用[DoFieldExchange](#dofieldexchange)機制來靜態繫結資料行。

請注意，如果您不是建立 UNICODE 記錄集，則必須使用不包含 `COleVariant` 參數的 `SetFieldValue` 形式，否則 `COleVariant` 物件必須明確宣告為 ANSI。 這可以藉由使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **（** *lpszSrc* **，** *vtSrc* **）** 形式的函式，並將*vtSrc*設定為 `VT_BSTRT` （ANSI），或使用 `COleVariant` 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) **（** *lpszSrc* **，** *vtSrc* **）** ，並將*vtSrc*設定為 `VT_BSTRT`來完成這項作業。

如需相關資訊，請參閱 DAO 說明中的「欄位物件」和「值屬性」主題。

##  <a name="setfieldvaluenull"></a>CDaoRecordset：： SetFieldValueNull

呼叫這個成員函式，將欄位設定為 Null 值。

```
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
記錄集內欄位的索引，用於以零為基底的索引進行查閱。

*lpszName*<br/>
記錄集中的功能變數名稱，用於依名稱查閱。

### <a name="remarks"></a>備註

C++Null 與 Null 不同，在資料庫術語中，表示「沒有任何值」。

如需相關資訊，請參閱 DAO 說明中的「欄位物件」和「值屬性」主題。

##  <a name="setlockingmode"></a>CDaoRecordset：： SetLockingMode

呼叫這個成員函式可設定記錄集的鎖定類型。

```
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>參數

*bPessimistic*<br/>
表示鎖定類型的旗標。

### <a name="remarks"></a>備註

當封閉式鎖定生效時，當您呼叫 `Edit` 成員函式時，就會鎖定包含所編輯記錄的2K 頁面。 當您呼叫 `Update` 或 `Close` 成員函式或任何移動或尋找作業時，此頁面就會解除鎖定。

當開放式鎖定生效時，只有在使用 `Update` 成員函式更新記錄時，才會鎖定包含記錄的2K 頁面。

如果頁面已鎖定，則其他使用者都無法在相同頁面上編輯記錄。 如果您呼叫 `SetLockingMode` 並傳遞非零值，而另一個使用者已經鎖定頁面，則當您呼叫 `Edit`時，就會擲回例外狀況（exception）。 其他使用者可以從鎖定的頁面讀取資料。

如果您使用零值呼叫 `SetLockingMode`，並在稍後由另一位使用者鎖定頁面時呼叫 `Update`，則會發生例外狀況。 若要查看另一位使用者對記錄所做的變更（並捨棄您的變更），請使用目前記錄的書簽值來呼叫 `SetBookmark` 成員函式。

使用 ODBC 資料來源時，鎖定模式一律是開放式的。

##  <a name="setparamvalue"></a>CDaoRecordset：： SetParamValue

呼叫這個成員函式，在執行時間設定記錄集中的參數值。

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
參數在 querydef 參數集合中的數位位置。

*var*<br/>
要設定的值;請參閱備註。

*lpszName*<br/>
您想要設定其值的參數名稱。

### <a name="remarks"></a>備註

參數必須已經建立為記錄集的 SQL 字串的一部分。 您可以依名稱或其在集合中的索引位置來存取參數。

指定要設定為 `COleVariant` 物件的值。 如需有關在 `COleVariant` 物件中設定所需值和類型的詳細資訊，請參閱類別[COleVariant](../../mfc/reference/colevariant-class.md)。 請注意，如果您不是建立 UNICODE 記錄集，則 `COleVariant` 物件必須明確宣告為 ANSI。 這可以藉由使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) **（** *lpszSrc* **，** *vtSrc* **）** 形式的函式，並將*vtSrc*設定為 `VT_BSTRT` （ANSI），或使用 `COleVariant` 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) **（** *lpszSrc* **，** *vtSrc* **）** ，並將*vtSrc*設定為 `VT_BSTRT`來完成這項作業。

##  <a name="setparamvaluenull"></a>CDaoRecordset：： SetParamValueNull

呼叫這個成員函式，將參數設定為 Null 值。

```
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
記錄集內欄位的索引，用於以零為基底的索引進行查閱。

*lpszName*<br/>
記錄集中的功能變數名稱，用於依名稱查閱。

### <a name="remarks"></a>備註

C++Null 與 Null 不同，在資料庫術語中，表示「沒有任何值」。

##  <a name="setpercentposition"></a>CDaoRecordset：： SetPercentPosition

呼叫這個成員函式來設定值，以根據記錄集中記錄的百分比，變更記錄集物件中目前記錄的近似位置。

```
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>參數

*fPosition*<br/>
介於 0 與 100 之間的數字。

### <a name="remarks"></a>備註

當使用動態集類型或快照集類型記錄集時，請先移至最後一筆記錄來填入記錄集，然後再呼叫 `SetPercentPosition`。 如果您在完全填入記錄集之前呼叫 `SetPercentPosition`，則移動量會相對於所存取的記錄數目（如[GetRecordCount](#getrecordcount)的值所指示）。 您可以藉由呼叫 `MoveLast`，移至最後一筆記錄。

一旦您呼叫 `SetPercentPosition`，相對於該值之大約位置的記錄就會變成「最新」。

> [!NOTE]
>  不建議呼叫 `SetPercentPosition` 將目前的記錄移至記錄集內的特定記錄。 請改為呼叫[SetBookmark](#setbookmark)成員函式。

如需相關資訊，請參閱 DAO 說明中的「PercentPosition 屬性」主題。

##  <a name="update"></a>CDaoRecordset：： Update

呼叫 `AddNew` 或 `Edit` 成員函式之後，呼叫這個成員函式。

```
virtual void Update();
```

### <a name="remarks"></a>備註

這是完成 `AddNew` 或 `Edit` 作業所需的呼叫。

`AddNew` 和 `Edit` 準備一個編輯緩衝區，在其中放置加入或編輯的資料以儲存至資料來源。 `Update` 儲存資料。 只有標示或偵測到已變更的欄位才會更新。

如果資料來源支援交易，您可以在交易中進行 `Update` 呼叫（及其對應的 `AddNew` 或 `Edit` 呼叫）。

> [!CAUTION]
> 如果您在未先呼叫 `AddNew` 或 `Edit`的情況下呼叫 `Update`，`Update` 會擲回 `CDaoException`。 如果您呼叫 `AddNew` 或 `Edit`，您必須先呼叫 `Update`，然後才呼叫[MoveNext](#movenext)或關閉記錄集或資料來源連接。 否則，在沒有通知的情況下，您的變更就會遺失。

當記錄集物件在多使用者環境中被搭配保守模式鎖定時，記錄會保持鎖定，直到使用 `Edit` 為止，直到更新完成為止。 如果記錄集是樂觀地鎖定的，則記錄會被鎖定，並在資料庫中更新之前，與預先編輯的記錄做比較。 如果記錄在您呼叫 `Edit`之後已變更，則 `Update` 作業會失敗，而且 MFC 會擲回例外狀況。 您可以使用 `SetLockingMode`變更鎖定模式。

> [!NOTE]
> 開放式鎖定一律用於外部資料庫格式，例如 ODBC 和可安裝的 ISAM。

如需相關資訊，請參閱 DAO 說明中的「AddNew 方法」、「CancelUpdate 方法」、「刪除方法」、「LastModified 屬性」、「更新方法」和「EditMode 屬性」主題。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoWorkspace 類別](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)<br/>
