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
ms.openlocfilehash: 4a1026c6b652bc5141855670db3b1ee34e7974b9
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040271"
---
# <a name="cdaorecordset-class"></a>CDaoRecordset 類別

表示選取自資料來源的資料錄集。

## <a name="syntax"></a>語法

```cpp
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
|[CDaoRecordset：： AddNew](#addnew)|準備加入新的記錄。 呼叫 [Update](#update) 以完成新增。|
|[CDaoRecordset：： CanAppend](#canappend)|如果可以透過 [AddNew](#addnew) 成員函式將新記錄加入至記錄集，則傳回非零。|
|[CDaoRecordset：： CanBookmark](#canbookmark)|如果記錄集支援書簽，則傳回非零。|
|[CDaoRecordset：： CancelUpdate](#cancelupdate)|因為 [編輯](#edit) 或 [AddNew](#addnew) 作業而取消任何暫止的更新。|
|[CDaoRecordset：： CanRestart](#canrestart)|如果可以呼叫重新 [查詢](#requery) 以再次執行記錄集的查詢，則傳回非零值。|
|[CDaoRecordset：： CanScroll](#canscroll)|如果您可以滾動記錄，則傳回非零值。|
|[CDaoRecordset：： CanTransact](#cantransact)|如果資料來源支援交易，則傳回非零。|
|[CDaoRecordset：： CanUpdate](#canupdate)|如果可以更新記錄集，則傳回非零的 (您可以) 加入、更新或刪除記錄。|
|[CDaoRecordset：： Close](#close)|關閉記錄集。|
|[CDaoRecordset：:D elete](#delete)|從記錄集刪除目前的記錄。 您必須在刪除後明確地滾動到另一筆記錄。|
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|呼叫以雙向交換資料 (在記錄集的欄位資料成員和資料來源上的對應記錄之間) 。 將 DAO 記錄欄位交換 (DFX) 。|
|[CDaoRecordset：： Edit](#edit)|準備目前記錄的變更。 呼叫 `Update` 以完成編輯。|
|[CDaoRecordset：： FillCache](#fillcache)|針對包含來自 ODBC 資料來源之資料的記錄集物件，填滿全部或部分本機快取。|
|[CDaoRecordset：： Find](#find)|在符合指定準則的動態集型別記錄集中，找出特定字串的第一個、下一個、上一個或最後一個位置，並使其記錄目前的記錄。|
|[CDaoRecordset：： FindFirst](#findfirst)|找出動態集類型或快照集型別記錄集中的第一筆記錄，以滿足指定的準則，並使其記錄目前的記錄。|
|[CDaoRecordset：： FindLast](#findlast)|找出動態集類型或快照集類型記錄集內的最後一筆記錄，以符合指定的準則，並使其記錄目前的記錄。|
|[CDaoRecordset：： FindNext](#findnext)|在動態集類型或快照集類型記錄集中找出符合指定準則的下一筆記錄，並使其記錄目前的記錄。|
|[CDaoRecordset：： FindPrev](#findprev)|在擁有者類型或快照集類型的記錄集中，找出符合指定準則的前一筆記錄，並使其記錄目前的記錄。|
|[CDaoRecordset：： GetAbsolutePosition](#getabsoluteposition)|傳回記錄集物件目前記錄的記錄號碼。|
|[CDaoRecordset：： GetBookmark](#getbookmark)|傳回值，表示記錄上的書簽。|
|[CDaoRecordset：： GetCacheSize](#getcachesize)|傳回值，這個值會指定包含要從 ODBC 資料來源本機快取之資料的動態集型別記錄集內的記錄數目。|
|[CDaoRecordset：： GetCacheStart](#getcachestart)|傳回值，這個值會指定要快取之記錄集中第一筆記錄的書簽。|
|[CDaoRecordset：： GetCurrentIndex](#getcurrentindex)|傳回， `CString` 其中包含最近在索引資料表類型上使用的索引名稱 `CDaoRecordset` 。|
|[CDaoRecordset：： GetDateCreated](#getdatecreated)|傳回建立物件基礎資料表的日期和時間 `CDaoRecordset`|
|[CDaoRecordset：： GetDateLastUpdated](#getdatelastupdated)|傳回對物件基礎的基表設計進行最近變更的日期和時間 `CDaoRecordset` 。|
|[CDaoRecordset：： GetDefaultDBName](#getdefaultdbname)|傳回預設資料來源的名稱。|
|[CDaoRecordset：： >getdefaultsql](#getdefaultsql)|呼叫以取得要執行的預設 SQL 字串。|
|[CDaoRecordset：： GetEditMode](#geteditmode)|傳回值，這個值表示目前記錄的編輯狀態。|
|[CDaoRecordset：： GetFieldCount](#getfieldcount)|傳回值，表示記錄集內的欄位數目。|
|[CDaoRecordset：： Issomapper.getfieldinfo](#getfieldinfo)|傳回記錄集內欄位的特定類型資訊。|
|[CDaoRecordset：： GetFieldValue](#getfieldvalue)|傳回記錄集內欄位的值。|
|[CDaoRecordset：： GetIndexCount](#getindexcount)|抓取資料表中基礎記錄集的索引數目。|
|[CDaoRecordset：： GetIndexInfo](#getindexinfo)|傳回有關索引的各種資訊。|
|[CDaoRecordset：： GetLastModifiedBookmark](#getlastmodifiedbookmark)|用來決定最近新增或更新的記錄。|
|[CDaoRecordset：： GetLockingMode](#getlockingmode)|傳回值，這個值表示在編輯期間作用中的鎖定類型。|
|[CDaoRecordset：： GetName](#getname)|傳回， `CString` 其中包含記錄集的名稱。|
|[CDaoRecordset：： GetParamValue](#getparamvalue)|抓取儲存在基礎 DAOParameter 物件中之指定參數的目前值。|
|[CDaoRecordset：： GetPercentPosition](#getpercentposition)|傳回目前記錄的位置，以記錄總數的百分比表示。|
|[CDaoRecordset：： GetRecordCount](#getrecordcount)|傳回在記錄集物件中存取的記錄數目。|
|[CDaoRecordset：： GetSQL](#getsql)|取得用來選取記錄集記錄的 SQL 字串。|
|[CDaoRecordset：： GetType](#gettype)|呼叫以判斷記錄集的類型：資料表類型、動態集類型或快照集類型。|
|[CDaoRecordset：： GetValidationRule](#getvalidationrule)|傳回， `CString` 其中包含的值會在資料輸入欄位時驗證資料。|
|[CDaoRecordset：： GetValidationText](#getvalidationtext)|抓取未滿足驗證規則時所顯示的文字。|
|[CDaoRecordset：： IsBOF](#isbof)|如果記錄集已經定位於第一筆記錄之前，則傳回非零。 目前沒有記錄。|
|[CDaoRecordset：： IsDeleted](#isdeleted)|如果記錄集位於已刪除的記錄上，則傳回非零。|
|[CDaoRecordset：： IsEOF](#iseof)|如果記錄集已經定位於最後一筆記錄之後，則傳回非零。 目前沒有記錄。|
|[CDaoRecordset：： IsFieldDirty](#isfielddirty)|如果目前記錄中指定的欄位已變更，則傳回非零值。|
|[CDaoRecordset：： >isfieldnull](#isfieldnull)|如果目前記錄中指定的欄位為 Null (沒有值) ，則傳回非零值。|
|[CDaoRecordset：： IsFieldNullable](#isfieldnullable)|如果目前記錄中指定的欄位可以設定為 Null (沒有值) ，則傳回非零值。|
|[CDaoRecordset：： IsOpen](#isopen)|如果之前已呼叫 [Open](#open) ，則傳回非零。|
|[CDaoRecordset：： Move](#move)|將記錄集從目前記錄的任一個方向定位至指定數目的記錄。|
|[CDaoRecordset：： MoveFirst](#movefirst)|將目前的記錄放置在記錄集的第一筆記錄。|
|[CDaoRecordset：： MoveLast](#movelast)|將目前記錄置於記錄集的最後一筆記錄。|
|[CDaoRecordset：： MoveNext](#movenext)|將目前的記錄放在記錄集的下一筆記錄。|
|[CDaoRecordset：： MovePrev](#moveprev)|將目前記錄放在記錄集內的上一個記錄。|
|[CDaoRecordset：： Open](#open)|從資料表、動態集或快照集建立新的記錄集。|
|[CDaoRecordset：： Requery](#requery)|重新執行記錄集的查詢，以重新整理選取的記錄。|
|[CDaoRecordset：： Seek](#seek)|在索引的資料表類型記錄集物件中尋找符合目前索引之指定準則的記錄，並使其記錄目前的記錄。|
|[CDaoRecordset：： SetAbsolutePosition](#setabsoluteposition)|設定記錄集物件目前記錄的記錄號碼。|
|[CDaoRecordset：： SetBookmark](#setbookmark)|將記錄集放置於包含指定書簽的記錄上。|
|[CDaoRecordset：： SetCacheSize](#setcachesize)|設定值，這個值會指定動態集型別記錄集中的記錄數目，其中包含要從 ODBC 資料來源本機快取的資料。|
|[CDaoRecordset：： SetCacheStart](#setcachestart)|設定值，這個值會指定要快取之記錄集中第一筆記錄的書簽。|
|[CDaoRecordset：： SetCurrentIndex](#setcurrentindex)|呼叫以設定資料表類型記錄集的索引。|
|[CDaoRecordset：： SetFieldDirty](#setfielddirty)|將目前記錄中的指定欄位標示為已變更。|
|[CDaoRecordset：： SetFieldNull](#setfieldnull)|將目前記錄中指定之欄位的值設定為 Null (沒有值) 。|
|[CDaoRecordset：： SetFieldValue](#setfieldvalue)|設定記錄集內欄位的值。|
|[CDaoRecordset：： SetFieldValueNull](#setfieldvaluenull)|將記錄集中的欄位值設定為 Null。  (沒有值) 。|
|[CDaoRecordset：： SetLockingMode](#setlockingmode)|設定值，這個值表示在編輯期間要置於作用中的鎖定類型。|
|[CDaoRecordset：： SetParamValue](#setparamvalue)|設定儲存在基礎 DAOParameter 物件中指定之參數的目前值|
|[CDaoRecordset：： SetParamValueNull](#setparamvaluenull)|將指定之參數的目前值設定為 Null (沒有值) 。|
|[CDaoRecordset：： SetPercentPosition](#setpercentposition)|將目前記錄的位置設定為相對於記錄集內記錄總數百分比的位置。|
|[CDaoRecordset：： Update](#update)|藉 `AddNew` `Edit` 由將新的或已編輯的資料儲存在資料來源上，完成或作業。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDaoRecordset：： m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|包含旗標，指出欄位是否會自動標示為已變更。|
|[CDaoRecordset：： m_nFields](#m_nfields)|包含記錄集類別中的欄位資料成員數目，以及記錄集在資料來源中選取的資料行數目。|
|[CDaoRecordset：： m_nParams](#m_nparams)|包含記錄集類別中的參數資料成員數目-與記錄集查詢一起傳遞的參數數目。|
|[CDaoRecordset：： m_pDAORecordset](#m_pdaorecordset)|記錄集物件基礎的 DAO 介面指標。|
|[CDaoRecordset：： m_pDatabase](#m_pdatabase)|此結果集的源資料庫。 包含 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 物件的指標。|
|[CDaoRecordset：： m_strFilter](#m_strfilter)|包含用來建立 SQL **WHERE** 語句的字串。|
|[CDaoRecordset：： m_strSort](#m_strsort)|包含用來建立 SQL **ORDER BY** 語句的字串。|

## <a name="remarks"></a>備註

所謂的「記錄集」 `CDaoRecordset` 物件提供下列三種形式：

- 資料表類型記錄集代表一個基表，可讓您用來檢查、加入、變更或刪除單一資料庫資料表中的記錄。

- 動態集類型記錄集是可更新記錄的查詢結果。 這些記錄集是一組記錄，可讓您用來檢查、加入、變更或刪除基礎資料庫資料表或資料表中的記錄。 動態集類型記錄集可以包含資料庫中一個或多個資料表的欄位。

- 快照集類型記錄集是一組記錄的靜態複本，可供您用來尋找資料或產生報表。 這些記錄集可以包含資料庫中一個或多個資料表的欄位，但無法更新。

每一種形式的記錄集都代表在記錄集開啟時固定的一組記錄。 當您在資料表類型的記錄集或動態集型別記錄集中滾動至記錄時，它會反映在記錄集開啟後（由其他使用者或應用程式中的其他記錄集）所做的記錄變更。  (無法更新快照集類型的記錄集。 ) 您可以 `CDaoRecordset` 直接使用或從衍生應用程式特定的記錄集類別 `CDaoRecordset` 。 接著，您可以：

- 滾動記錄。

- 使用 [Seek](#seek) (資料表類型的記錄集，來設定索引並快速尋找記錄) 。

- 根據字串比較來尋找記錄：「<」、「 \<=", "=", "> =」或「>」 (動態集型別和快照集類型記錄集) 。

- 更新記錄並指定鎖定模式 (但快照集類型記錄集) 除外。

- 篩選記錄集，以限制它從資料來源可用的記錄中選取的記錄。

- 排序記錄集。

- 將記錄集參數化，以自訂在執行時間之前不知道的資訊。

類別 `CDaoRecordset` 會提供類似于類別的介面 `CRecordset` 。 主要的差異在於，類別會 `CDaoRecordset` 透過資料存取物件 (DAO) （以 OLE 為基礎）來存取資料。 類別 `CRecordset` 會透過開放式資料庫連接來存取 dbms (odbc) 和適用于該 dbms 的 odbc 驅動程式。

> [!NOTE]
> DAO 資料庫類別與以開放式資料庫連接 (ODBC) 為基礎的 MFC 資料庫類別不同。 所有 DAO 資料庫類別名稱都有 "CDao" 前置詞。 您仍然可以使用 DAO 類別來存取 ODBC 資料來源;DAO 類別通常會提供絕佳的功能，因為它們是 Microsoft Jet 資料庫引擎專屬的功能。

您可以直接使用 `CDaoRecordset` 或從衍生類別 `CDaoRecordset` 。 若要在任一情況下使用記錄集類別，請開啟資料庫並建立記錄集物件，並將指標傳遞至您的 `CDaoDatabase` 物件。 您也可以建立 `CDaoRecordset` 物件，並讓 MFC `CDaoDatabase` 為您建立暫存物件。 然後通話記錄集的 [Open](#open) 成員函式，指定物件是否為數據表類型的記錄集、動態集型別記錄集或快照集類型的記錄集。 呼叫會 `Open` 從資料庫中選取資料，並抓取第一筆記錄。

您可以使用物件的成員函式和資料成員，來滾動記錄並操作它們。 可用的作業取決於物件是否為數據表類型的記錄集、動態集類型記錄集或快照集類型的記錄集，以及它是否可更新或唯讀，這取決於資料庫的功能或 (ODBC) 資料來源的開放式資料庫連接。 若要重新整理自呼叫之後可能已變更或新增的記錄 `Open` ，請呼叫物件的 [Requery](#requery) 成員函式。 呼叫物件的成員函式 `Close` ，並在完成時終結物件。

`CDaoRecordset` 使用 DAO 記錄欄位交換 (DFX) ，透過 `CDaoRecordset` 或衍生類別的型別安全 c + + 成員，支援記錄欄位的讀取和更新 `CDaoRecordset` 。 您也可以在資料庫中執行資料行的動態系結，而不需要使用 [GetFieldValue](#getfieldvalue) 和 [SetFieldValue](#setfieldvalue)的 DFX 機制。

如需相關資訊，請參閱 DAO 說明中的「記錄集物件」主題。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>需求

**標頭：** afxdao。h

## <a name="cdaorecordsetaddnew"></a><a name="addnew"></a> CDaoRecordset：： AddNew

呼叫這個成員函式，將新記錄加入至資料表類型或動態集類型的記錄集。

```cpp
virtual void AddNew();
```

### <a name="remarks"></a>備註

記錄的欄位一開始是 Null。  (在資料庫術語中，Null 表示「沒有值」，且與 c + + 中的 Null 不同。 ) 若要完成作業，您必須呼叫 [Update](#update) 成員函式。 `Update` 將您的變更儲存至資料來源。

> [!CAUTION]
> 如果您編輯記錄，然後在不呼叫的情況下滾動到另一筆記錄 `Update` ，您的變更就會遺失，而不會發出警告

如果您藉由呼叫 [AddNew](#addnew)將記錄加入至動態集類型記錄集，記錄就會顯示在記錄集內，並包含在基礎資料表中，以供任何新 `CDaoRecordset` 物件看見。

新記錄的位置取決於記錄集的類型：

- 在不保證插入新記錄的動態集類型記錄集中。 此行為隨著 Microsoft Jet 3.0 而變更，以因應效能和並行的原因。 如果您的目標是要讓新加入的記錄成為目前的記錄，請取得上次修改記錄的書簽，並移至該書簽：

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- 在已指定索引的資料表類型記錄集內，會在排序次序中以適當的位置傳回記錄。 如果未指定任何索引，就會在記錄集的結尾傳回新的記錄。

使用之前的記錄會 `AddNew` 保持最新狀態。 如果您想要讓新記錄成為目前的記錄，且記錄集支援書簽，請呼叫 [SetBookmark](#setbookmark) 至基礎 DAO 記錄集物件的 LastModified 屬性設定所識別的書簽。 這樣做很適合用來判斷計數器的值 (自動遞增) 加入的記錄中的欄位。 如需詳細資訊，請參閱 [GetLastModifiedBookmark](#getlastmodifiedbookmark)。

如果資料庫支援交易，您可以將 `AddNew` 呼叫部分進行交易。 如需交易的詳細資訊，請參閱類別 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)。 請注意，您應該先呼叫 [CDaoWorkspace：： BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) ，然後再呼叫 `AddNew` 。

呼叫尚未呼叫 Open 成員函式的記錄集是不合法的 `AddNew` 。 [Open](#open) `CDaoException`如果您呼叫 `AddNew` 無法附加的記錄集，就會擲回。 您可以藉由呼叫 [CanAppend](#canappend)來判斷記錄集是否可更新。

此架構會標記變更的欄位資料成員，以確保 DAO 記錄欄位交換 (DFX) 機制將這些成員寫入資料來源的記錄。 變更欄位的值時，通常會自動將欄位設定為自動變更，因此您不需要自行呼叫 [SetFieldDirty](#setfielddirty) ，但有時可能會想要確保不論欄位資料成員中的值為何，都會明確更新或插入資料行。 DFX 機制也會採用 **虛擬 Null**的使用。 如需詳細資訊，請參閱 [CDaoFieldExchange：： m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用雙重緩衝機制，則變更欄位的值不會自動將欄位設定為中途。 在此情況下，必須明確地設定欄位變更。 [M_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的旗標會控制此自動欄位檢查。

> [!NOTE]
> 如果記錄是雙重緩衝的 (也就是說，自動欄位檢查已啟用) ，則呼叫 `CancelUpdate` 會將成員變數還原至 `AddNew` 呼叫之前或 `Edit` 被呼叫的值。

如需相關資訊，請參閱 DAO 說明中的「AddNew 方法」、「CancelUpdate 方法」、「LastModified 屬性」和「EditMode 屬性」主題。

## <a name="cdaorecordsetcanappend"></a><a name="canappend"></a> CDaoRecordset：： CanAppend

呼叫這個成員函式來判斷先前開啟的記錄集是否可讓您藉由呼叫 [AddNew](#addnew) 成員函式來加入新的記錄。

```cpp
BOOL CanAppend() const;
```

### <a name="return-value"></a>傳回值

如果記錄集允許加入新的記錄，則為非零。否則為0。 `CanAppend` 如果您將記錄集開啟為唯讀，則會傳回0。

### <a name="remarks"></a>備註

如需相關資訊，請參閱 DAO 說明中的「附加方法」主題。

## <a name="cdaorecordsetcanbookmark"></a><a name="canbookmark"></a> CDaoRecordset：： CanBookmark

呼叫這個成員函式來判斷先前開啟的記錄集是否可讓您使用書簽來個別標記記錄。

```cpp
BOOL CanBookmark();
```

### <a name="return-value"></a>傳回值

如果記錄集支援書簽，則為非零，否則為0。

### <a name="remarks"></a>備註

如果您使用完全以 Microsoft Jet database engine 資料表為基礎的記錄集，則可以使用書簽，除了標示為順向滾動記錄集的快照集類型記錄集之外。  (外部 ODBC 資料來源的其他資料庫產品) 可能不支援書簽。

如需相關資訊，請參閱 DAO 說明中的「Bookmarkable 屬性」主題。

## <a name="cdaorecordsetcancelupdate"></a><a name="cancelupdate"></a> CDaoRecordset：： CancelUpdate

由於編輯或 AddNew 作業的緣故，此 `CancelUpdate` 成員[Edit](#edit)函式[AddNew](#addnew)會取消任何暫止的更新。

```cpp
virtual void CancelUpdate();
```

### <a name="remarks"></a>備註

例如，如果應用程式呼叫或成員函式， `Edit` `AddNew` 但未呼叫 [Update](#update)，則會 `CancelUpdate` 取消在呼叫或之後所做的任何變更 `Edit` `AddNew` 。

> [!NOTE]
> 如果記錄是雙重緩衝的 (也就是說，自動欄位檢查已啟用) ，則呼叫 `CancelUpdate` 會將成員變數還原至 `AddNew` 呼叫之前或 `Edit` 被呼叫的值。

如果沒有或作業 `Edit` `AddNew` 暫止，則 `CancelUpdate` 會導致 MFC 擲回例外狀況。 呼叫 [GetEditMode](#geteditmode) 成員函式，以判斷是否有可取消的暫止作業。

如需相關資訊，請參閱 DAO 說明中的「CancelUpdate 方法」主題。

## <a name="cdaorecordsetcanrestart"></a><a name="canrestart"></a> CDaoRecordset：： CanRestart

呼叫此成員函式，以判斷記錄集是否允許重新開機查詢 (，藉由呼叫成員函式來重新整理其記錄) `Requery` 。

```cpp
BOOL CanRestart();
```

### <a name="return-value"></a>傳回值

如果 `Requery` 可以呼叫以再次執行記錄集的查詢，則為非零，否則為0。

### <a name="remarks"></a>備註

不支援資料表類型的記錄集 `Requery` 。

如果 `Requery` 不受支援，請呼叫 [Close](#close) ，然後 [開啟](#open) 以重新整理資料。 `Requery`當參數值變更之後，您可以呼叫來更新記錄集物件的基礎參數查詢。

如需相關資訊，請參閱 DAO 說明中的「可重新開機的屬性」主題。

## <a name="cdaorecordsetcanscroll"></a><a name="canscroll"></a> CDaoRecordset：： CanScroll

呼叫這個成員函式，以判斷記錄集是否允許滾動。

```cpp
BOOL CanScroll() const;
```

### <a name="return-value"></a>傳回值

如果您可以滾動記錄，則為非零，否則為0。

### <a name="remarks"></a>備註

如果您呼叫 [Open](#open) with `dbForwardOnly` ，記錄集只能向前滾動。

如需相關資訊，請參閱 DAO 說明中的「使用 DAO 定位目前的記錄指標」主題。

## <a name="cdaorecordsetcantransact"></a><a name="cantransact"></a> CDaoRecordset：： CanTransact

呼叫這個成員函式，以判斷記錄集是否允許交易。

```cpp
BOOL CanTransact();
```

### <a name="return-value"></a>傳回值

如果基礎資料來源支援交易則為非零，否則為0。

### <a name="remarks"></a>備註

如需相關資訊，請參閱 DAO 說明中的「交易屬性」主題。

## <a name="cdaorecordsetcanupdate"></a><a name="canupdate"></a> CDaoRecordset：： CanUpdate

呼叫這個成員函式，以判斷是否可以更新記錄集。

```cpp
BOOL CanUpdate() const;
```

### <a name="return-value"></a>傳回值

如果可以更新記錄集 (新增、更新和刪除記錄) ，則為非零，否則為0。

### <a name="remarks"></a>備註

如果基礎資料來源是唯讀的，或是 `dbReadOnly` 當您針對記錄集呼叫[Open](#open)時指定*nOptions* ，則記錄集可能是唯讀的。

如需相關資訊，請參閱 DAO 說明中的「AddNew 方法」、「編輯方法」、「刪除方法」、「更新方法」和「可更新的屬性」主題。

## <a name="cdaorecordsetcdaorecordset"></a><a name="cdaorecordset"></a> CDaoRecordset：： CDaoRecordset

建構 `CDaoRecordset` 物件。

```cpp
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>參數

*pDatabase*<br/>
包含 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 物件的指標或 Null 值。 如果不是 Null，而且尚未 `CDaoDatabase` 呼叫物件的成員函式 `Open` 來將它連接到資料來源，則記錄集會在自己的 [開啟](#open) 呼叫期間，嘗試為您開啟。 如果您傳遞 Null，則 `CDaoDatabase` 會使用您所指定的資料來源資訊，為您建立物件，並將其連接到 `CDaoRecordset` 。

### <a name="remarks"></a>備註

您可以直接使用 `CDaoRecordset` 或從衍生特定的應用程式類別 `CDaoRecordset` 。 您可以使用 ClassWizard 來衍生您的記錄集類別。

> [!NOTE]
> 如果您衍生 `CDaoRecordset` 類別，您的衍生類別必須提供自己的函式。 在衍生類別的函式中，呼叫函式 `CDaoRecordset::CDaoRecordset` ，並將適當的參數傳遞給它。

將 Null 傳遞至您的記錄集函式，以 `CDaoDatabase` 自動為您建立並連線物件。 這是很有用的快捷方式，您不需要在建立記錄集之前，先建立並連接 `CDaoDatabase` 物件。 如果 `CDaoDatabase` 物件未開啟，也會為您建立一個使用預設工作區的 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 物件。 如需詳細資訊，請參閱 [CDaoDatabase：： CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase)。

## <a name="cdaorecordsetclose"></a><a name="close"></a> CDaoRecordset：： Close

關閉 `CDaoRecordset` 物件會從關聯資料庫中開啟的記錄集集合中移除它。

```cpp
virtual void Close();
```

### <a name="remarks"></a>備註

由於不 `Close` 會終結 `CDaoRecordset` 物件，因此您可以 `Open` 在相同的資料來源或不同的資料來源上呼叫來重複使用物件。

所有暫止的 [AddNew](#addnew) 或 [Edit](#edit) 語句都會取消，而且所有暫止的交易都會回復。 如果您想要保留暫止的新增或編輯[Update](#update) ，請在呼叫 `Close` 每個記錄集之前呼叫 Update。

您可以 `Open` 在呼叫之後再呼叫一次 `Close` 。 這可讓您重複使用記錄集物件。 更好的替代方式是呼叫重新 [查詢](#requery)（如果可能的話）。

如需相關資訊，請參閱 DAO 說明中的「關閉方法」主題。

## <a name="cdaorecordsetdelete"></a><a name="delete"></a> CDaoRecordset：:D elete

呼叫這個成員函式，以刪除開放式動態集型別或資料表類型記錄集物件中的目前記錄。

```cpp
virtual void Delete();
```

### <a name="remarks"></a>備註

成功刪除之後，記錄集的欄位資料成員會設定為 Null 值，而且您必須明確地呼叫其中一個記錄集導覽成員函式 ( [move](#move)、 [Seek](#seek)、 [SetBookmark](#setbookmark)等) ，才能移出已刪除的記錄。 當您從記錄集刪除記錄時，在呼叫之前，記錄集中必須有目前的記錄，否則 MFC 會擲回 `Delete` 例外狀況。

`Delete` 移除目前的記錄，使其無法存取。 雖然您無法編輯或使用已刪除的記錄，但它仍保持最新狀態。 不過，一旦您移至另一筆記錄，就無法再次將刪除的記錄設為最新。

> [!CAUTION]
> 記錄集必須是可更新的，且當您呼叫時，記錄集內必須要有有效的最新記錄 `Delete` 。 例如，如果您刪除記錄，但未在呼叫之前先滾動至新記錄，則會擲 `Delete` 回 `Delete` [CDaoException](../../mfc/reference/cdaoexception-class.md)。

如果您使用交易，並呼叫 [CDaoWorkspace：： Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) 成員函式，則可以取消刪除記錄。 如果基表是 cascade delete 關聯性中的主資料表，則刪除目前的記錄可能也會刪除外部資料表中的一或多個記錄。 如需詳細資訊，請參閱 DAO 說明中的「串聯刪除」定義。

與 `AddNew` 和不同的 `Edit` 是，的呼叫 `Delete` 後面不是的呼叫 `Update` 。

如需相關資訊，請參閱 DAO 說明中的「AddNew 方法」、「編輯方法」、「刪除方法」、「更新方法」和「可更新的屬性」主題。

## <a name="cdaorecordsetdofieldexchange"></a><a name="dofieldexchange"></a> CDaoRecordset：:D oFieldExchange

架構會呼叫這個成員函式，在記錄集物件的欄位資料成員和資料來源上的目前記錄對應資料行之間自動交換資料。

```cpp
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>參數

*.Pfx*<br/>
包含物件的指標 `CDaoFieldExchange` 。 架構已經設定此物件來指定欄位交換作業的內容。

### <a name="remarks"></a>備註

它也會將您的參數資料成員（如果有的話）系結至記錄集選取專案的 SQL 語句字串中的參數預留位置。 欄位資料的交換（稱為 DAO 記錄欄位交換 (DFX) ）可以雙向運作：從記錄集物件的欄位資料成員，到資料來源上記錄的欄位，以及從資料來源的記錄到記錄集物件。 如果您要動態地系結資料行，就不需要執行 `DoFieldExchange` 。

您通常必須採取的唯一動作，就 `DoFieldExchange` 是使用 ClassWizard 建立類別，並指定欄位資料成員的名稱和資料類型。 您也可以將程式碼加入至 ClassWizard 寫入以指定參數資料成員。 如果所有欄位都要動態系結，除非您指定參數資料成員，否則此函式將為非使用中。

當您使用 ClassWizard 宣告衍生的記錄集類別時，嚮導會為您撰寫的覆寫 `DoFieldExchange` ，類似于下列範例：

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

## <a name="cdaorecordsetedit"></a><a name="edit"></a> CDaoRecordset：： Edit

呼叫這個成員函式，以允許變更目前的記錄。

```cpp
virtual void Edit();
```

### <a name="remarks"></a>備註

一旦您呼叫成員函式，就會將對 `Edit` 目前記錄欄位所做的變更複製到複製緩衝區。 在對記錄進行想要的變更之後，請呼叫 `Update` 以儲存您的變更。 `Edit` 儲存記錄集之資料成員的值。 如果您呼叫 `Edit` ，請進行變更，然後再呼叫 `Edit` 一次，記錄的值就會還原成第一次呼叫之前的值 `Edit` 。

> [!CAUTION]
> 如果您編輯記錄，然後執行任何移動到另一筆記錄的作業，而不需要先呼叫 `Update` ，您的變更就會遺失，而不會發出警告。 此外，如果您關閉記錄集或父資料庫，則會捨棄已編輯的記錄而不發出警告。

在某些情況下，您可能會想要藉由將資料行設為 Null (不包含任何資料) 來更新資料行。 若要這樣做，請 `SetFieldNull` 使用 TRUE 的參數將欄位標示為 Null，這也會導致資料行更新。 如果您想要將欄位寫入資料來源，即使其值未變更，請 `SetFieldDirty` 使用 TRUE 的參數來呼叫。 即使此欄位的值為 Null，也可以運作。

此架構會標記變更的欄位資料成員，以確保 DAO 記錄欄位交換 (DFX) 機制將這些成員寫入資料來源的記錄。 變更欄位的值時，通常會自動將欄位設定為自動變更，因此您不需要自行呼叫 [SetFieldDirty](#setfielddirty) ，但有時可能會想要確保不論欄位資料成員中的值為何，都會明確更新或插入資料行。 DFX 機制也會採用 **虛擬 Null**的使用。 如需詳細資訊，請參閱 [CDaoFieldExchange：： m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用雙重緩衝機制，則變更欄位的值不會自動將欄位設定為中途。 在此情況下，必須明確地設定欄位變更。 [M_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的旗標會控制此自動欄位檢查。

當記錄集物件在多使用者環境中搭配保守模式鎖定時，記錄會保持鎖定， `Edit` 直到更新完成為止。 如果記錄集是樂觀地鎖定的，則會在資料庫中更新記錄之前，先鎖定記錄，並與預先編輯的記錄進行比較。 如果自呼叫之後記錄已變更 `Edit` ，則作業 `Update` 會失敗，且 MFC 會擲回例外狀況。 您可以使用變更鎖定模式 `SetLockingMode` 。

> [!NOTE]
> 開放式鎖定一律用於外部資料庫格式，例如 ODBC 和可安裝的 ISAM。

呼叫之後，目前的記錄仍保持為最新狀態 `Edit` 。 若要呼叫 `Edit` ，必須有目前的記錄。 如果沒有目前的記錄或記錄集未參考開啟的資料表類型或動態集型別記錄集物件，就會發生例外狀況。 呼叫 `Edit` 會導致在 `CDaoException` 下列情況下擲回：

- 目前沒有記錄。

- 資料庫或記錄集是唯讀的。

- 記錄中沒有任何欄位可以更新。

- 已開啟資料庫或記錄集，供另一位使用者獨佔使用。

- 另一位使用者已鎖定包含您記錄的頁面。

如果資料來源支援交易，您可以將 `Edit` 呼叫部分進行交易。 請注意，您應該在 `CDaoWorkspace::BeginTrans` 呼叫 `Edit` 和記錄集開啟之前呼叫。 另請注意，呼叫不是 `CDaoWorkspace::CommitTrans` 呼叫來完成作業的替代方案 `Update` `Edit` 。 如需交易的詳細資訊，請參閱類別 `CDaoWorkspace` 。

如需相關資訊，請參閱 DAO 說明中的「AddNew 方法」、「編輯方法」、「刪除方法」、「更新方法」和「可更新的屬性」主題。

## <a name="cdaorecordsetfillcache"></a><a name="fillcache"></a> CDaoRecordset：： FillCache

呼叫這個成員函式，從記錄集快取指定的記錄數目。

```cpp
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>參數

*pSize*<br/>
指定要在快取中填入的資料列數目。 如果您省略這個參數，此值是由基礎 DAO 物件的 CacheSize 屬性設定所決定。

*pBookmark*<br/>
[COleVariant](../../mfc/reference/colevariant-class.md) ，指定書簽。 快取會從這個書簽指出的記錄開始填滿。 如果您省略此參數，則會從基礎 DAO 物件的 CacheStart 屬性所指出的記錄開始填滿快取。

### <a name="remarks"></a>備註

快取可改善從遠端伺服器抓取或提取資料的應用程式效能。 快取是本機記憶體中的空間，用來保存最近從伺服器提取的資料，並假設資料可能會在應用程式執行時再次要求。 當要求資料時，Microsoft Jet 資料庫引擎會先檢查快取中的資料，而不是從伺服器提取快取，這需要更多時間。 在非 ODBC 資料來源上使用資料快取沒有任何作用，因為資料不會儲存在快取中。

您可以藉由呼叫成員函式，隨時明確地填滿快取，而不是在提取記錄時等待快取填滿 `FillCache` 。 這是較快填滿快取的方式，因為會一次 `FillCache` 提取數筆記錄，而不是一次提取一個記錄。 例如，在顯示記錄的每個 screenful 時，您可以讓應用程式呼叫 `FillCache` 提取下一 screenful 的記錄。

任何使用記錄集物件存取的 ODBC 資料庫都可以有本機快取。 若要建立快取，請從遠端資料源開啟記錄集物件，然後呼叫 `SetCacheSize` 記錄集的和成員函式 `SetCacheStart` 。 如果 *lSize* 和 *lBookmark* 建立的範圍是在和指定的範圍之外 `SetCacheSize` ，則 `SetCacheStart` 會忽略此範圍外的記錄集部分，而不會載入到快取中。 如果 `FillCache` 要求的記錄比保留在遠端資料源中多，則只會提取剩餘的記錄，而且不會擲回例外狀況。

從快取提取的記錄不會反映其他使用者同時對來源資料所做的變更。

`FillCache` 只提取尚未快取的記錄。 若要強制更新所有快取的資料，請 `SetCacheSize` 使用等於0的 *lSize* 參數呼叫成員函式， `SetCacheSize` 並使用等於您原先要求之快取大小的 *lSize* 參數再次呼叫，然後再呼叫 `FillCache` 。

如需相關資訊，請參閱 DAO 說明中的「FillCache 方法」主題。

## <a name="cdaorecordsetfind"></a><a name="find"></a> CDaoRecordset：： Find

使用比較運算子呼叫這個成員函式，以找出動態集型別或快照集類型記錄集內的特定字串。

```cpp
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*lFindType*<br/>
值，表示所需的尋找作業類型。 可能的值包括：

- AFX_DAO_NEXT 尋找相符字串的下一個位置。

- AFX_DAO_PREV 尋找相符字串先前的位置。

- AFX_DAO_FIRST 尋找相符字串的第一個位置。

- AFX_DAO_LAST 尋找相符字串的最後一個位置。

*lpszFilter*<br/>
字串運算式 (像是 SQL 語句中的 **WHERE** 子句，而不是 **) 用** 來尋找記錄的單字。 例如：

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>傳回值

如果找到相符的記錄，則為非零，否則為0。

### <a name="remarks"></a>備註

您可以找到字串的第一個、下一個、上一個或最後一個實例。 `Find` 是虛擬函式，因此您可以覆寫它，並新增您自己的實作為。 `FindFirst`、 `FindLast` 、和成員函式 `FindNext` `FindPrev` 會呼叫成員函式 `Find` ，因此您可以使用 `Find` 來控制所有尋找作業的行為。

若要在資料表類型的記錄集中找出記錄，請呼叫 [Seek](#seek) 成員函式。

> [!TIP]
> 您擁有的記錄集越小，就越有效 `Find` 。 一般而言，特別是在 ODBC 資料中，最好是建立一個只抓取您所要記錄的新查詢。

如需相關資訊，請參閱 DAO 說明中的「FindFirst、FindLast、FindNext、FindPrevious 方法」主題。

## <a name="cdaorecordsetfindfirst"></a><a name="findfirst"></a> CDaoRecordset：： FindFirst

呼叫這個成員函式，以尋找符合指定條件的第一筆記錄。

```cpp
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*lpszFilter*<br/>
字串運算式 (像是 SQL 語句中的 **WHERE** 子句，而不是 **) 用** 來尋找記錄的單字。

### <a name="return-value"></a>傳回值

如果找到相符的記錄，則為非零，否則為0。

### <a name="remarks"></a>備註

成員函式會 `FindFirst` 從記錄集的開頭開始搜尋，並搜尋到記錄集的結尾。

如果您想要在搜尋中包含所有記錄 (而不只是符合特定條件的記錄) 使用其中一個移動作業從記錄移至記錄。 若要在資料表類型的記錄集中找出記錄，請呼叫成員函式 `Seek` 。

如果找不到符合準則的記錄，則不會確定目前的記錄指標，而會傳回 `FindFirst` 零。 如果記錄集包含超過一筆符合準則的記錄，則會找 `FindFirst` 出第一個出現的專案，找出下一個出現的專案， `FindNext` 依此類推。

> [!CAUTION]
> 如果您編輯目前的記錄，請務必先呼叫成員函式來儲存變更， `Update` 然後再移至另一筆記錄。 如果您移至另一筆記錄而不進行更新，您的變更就會遺失，而不會發出警告

成員函式會 `Find` 從位置和下表中指定的方向進行搜尋：

|尋找作業|開始|搜尋方向|
|---------------------|-----------|----------------------|
|`FindFirst`|記錄集的開頭|記錄集結尾|
|`FindLast`|記錄集結尾|記錄集的開頭|
|`FindNext`|目前記錄|記錄集結尾|
|`FindPrevious`|目前記錄|記錄集的開頭|

> [!NOTE]
> 當您呼叫時， `FindLast` Microsoft Jet 資料庫引擎會在開始搜尋之前完整填入記錄集（如果尚未這麼做）。 第一個搜尋可能需要比後續搜尋更長的時間。

使用其中一個尋找作業與呼叫或不同， `MoveFirst` `MoveNext` 它只會在不指定條件的情況下，讓第一個或下一個記錄成為最新的。 您可以依照「尋找」作業進行移動作業。

使用「尋找」作業時，請記住下列事項：

- 如果傳回 `Find` 非零值，則不會定義目前的記錄。 在此情況下，您必須將目前的記錄指標放回有效的記錄。

- 您無法使用具有順向滾動快照集類型記錄集的尋找作業。

- 當您搜尋包含日期的欄位時，您應該使用美國日期格式 (月-日) ，即使您不是使用美國版本的 Microsoft Jet database engine 也是一樣。否則，可能找不到相符的記錄。

- 使用 ODBC 資料庫和大型動態集時，您可能會發現使用尋找作業很慢，特別是在處理大型記錄集時。 您可以使用 SQL 查詢搭配自訂的 **ORDERBY** 或 **WHERE** 子句、參數查詢，或抓取 `CDaoQuerydef` 特定索引記錄的物件，來改善效能。

如需相關資訊，請參閱 DAO 說明中的「FindFirst、FindLast、FindNext、FindPrevious 方法」主題。

## <a name="cdaorecordsetfindlast"></a><a name="findlast"></a> CDaoRecordset：： FindLast

呼叫這個成員函式，以尋找符合指定條件的最後一筆記錄。

```cpp
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*lpszFilter*<br/>
字串運算式 (像是 SQL 語句中的 **WHERE** 子句，而不是 **) 用** 來尋找記錄的單字。

### <a name="return-value"></a>傳回值

如果找到相符的記錄，則為非零，否則為0。

### <a name="remarks"></a>備註

成員函式會 `FindLast` 在記錄集的結尾開始搜尋，並向後搜尋記錄集的開頭。

如果您想要在搜尋中包含所有記錄 (而不只是符合特定條件的記錄) 使用其中一個移動作業從記錄移至記錄。 若要在資料表類型的記錄集中找出記錄，請呼叫成員函式 `Seek` 。

如果找不到符合準則的記錄，則不會確定目前的記錄指標，而會傳回 `FindLast` 零。 如果記錄集包含多個符合準則的記錄，則會找出第一個出現的專案，找出第一次出現之後的下一個專案 `FindFirst` `FindNext` ，依此類推。

> [!CAUTION]
> 如果您編輯目前的記錄，請務必先呼叫成員函式來儲存變更， `Update` 然後再移至另一筆記錄。 如果您移至另一筆記錄而不進行更新，您的變更就會遺失，而不會發出警告

使用其中一個尋找作業與呼叫或不同， `MoveFirst` `MoveNext` 它只會在不指定條件的情況下，讓第一個或下一個記錄成為最新的。 您可以依照「尋找」作業進行移動作業。

使用「尋找」作業時，請記住下列事項：

- 如果傳回 `Find` 非零值，則不會定義目前的記錄。 在此情況下，您必須將目前的記錄指標放回有效的記錄。

- 您無法使用具有順向滾動快照集類型記錄集的尋找作業。

- 當您搜尋包含日期的欄位時，您應該使用美國日期格式 (月-日) ，即使您不是使用美國版本的 Microsoft Jet database engine 也是一樣。否則，可能找不到相符的記錄。

- 使用 ODBC 資料庫和大型動態集時，您可能會發現使用尋找作業很慢，特別是在處理大型記錄集時。 您可以使用 SQL 查詢搭配自訂的 **ORDERBY** 或 **WHERE** 子句、參數查詢，或抓取 `CDaoQuerydef` 特定索引記錄的物件，來改善效能。

如需相關資訊，請參閱 DAO 說明中的「FindFirst、FindLast、FindNext、FindPrevious 方法」主題。

## <a name="cdaorecordsetfindnext"></a><a name="findnext"></a> CDaoRecordset：： FindNext

呼叫這個成員函式，以找出符合指定條件的下一筆記錄。

```cpp
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*lpszFilter*<br/>
字串運算式 (像是 SQL 語句中的 **WHERE** 子句，而不是 **) 用** 來尋找記錄的單字。

### <a name="return-value"></a>傳回值

如果找到相符的記錄，則為非零，否則為0。

### <a name="remarks"></a>備註

成員函式會 `FindNext` 在目前的記錄開始搜尋，並搜尋到記錄集的結尾。

如果您想要在搜尋中包含所有記錄 (而不只是符合特定條件的記錄) 使用其中一個移動作業從記錄移至記錄。 若要在資料表類型的記錄集中找出記錄，請呼叫成員函式 `Seek` 。

如果找不到符合準則的記錄，則不會確定目前的記錄指標，而會傳回 `FindNext` 零。 如果記錄集包含超過一筆符合準則的記錄，則會找 `FindFirst` 出第一個出現的專案，找出下一個出現的專案， `FindNext` 依此類推。

> [!CAUTION]
> 如果您編輯目前的記錄，請務必先呼叫成員函式來儲存變更， `Update` 然後再移至另一筆記錄。 如果您移至另一筆記錄而不進行更新，您的變更就會遺失，而不會發出警告

使用其中一個尋找作業與呼叫或不同， `MoveFirst` `MoveNext` 它只會在不指定條件的情況下，讓第一個或下一個記錄成為最新的。 您可以依照「尋找」作業進行移動作業。

使用「尋找」作業時，請記住下列事項：

- 如果傳回 `Find` 非零值，則不會定義目前的記錄。 在此情況下，您必須將目前的記錄指標放回有效的記錄。

- 您無法使用具有順向滾動快照集類型記錄集的尋找作業。

- 當您搜尋包含日期的欄位時，您應該使用美國日期格式 (月-日) ，即使您不是使用美國版本的 Microsoft Jet database engine 也是一樣。否則，可能找不到相符的記錄。

- 使用 ODBC 資料庫和大型動態集時，您可能會發現使用尋找作業很慢，特別是在處理大型記錄集時。 您可以使用 SQL 查詢搭配自訂的 **ORDERBY** 或 **WHERE** 子句、參數查詢，或抓取 `CDaoQuerydef` 特定索引記錄的物件，來改善效能。

如需相關資訊，請參閱 DAO 說明中的「FindFirst、FindLast、FindNext、FindPrevious 方法」主題。

## <a name="cdaorecordsetfindprev"></a><a name="findprev"></a> CDaoRecordset：： FindPrev

呼叫這個成員函式，以找出符合指定條件的前一筆記錄。

```cpp
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>參數

*lpszFilter*<br/>
字串運算式 (像是 SQL 語句中的 **WHERE** 子句，而不是 **) 用** 來尋找記錄的單字。

### <a name="return-value"></a>傳回值

如果找到相符的記錄，則為非零，否則為0。

### <a name="remarks"></a>備註

成員函式會 `FindPrev` 在目前的記錄開始搜尋，並向後搜尋記錄集的開頭。

如果您想要在搜尋中包含所有記錄 (而不只是符合特定條件的記錄) 使用其中一個移動作業從記錄移至記錄。 若要在資料表類型的記錄集中找出記錄，請呼叫成員函式 `Seek` 。

如果找不到符合準則的記錄，則不會確定目前的記錄指標，而會傳回 `FindPrev` 零。 如果記錄集包含超過一筆符合準則的記錄，則會找 `FindFirst` 出第一個出現的專案，找出下一個出現的專案， `FindNext` 依此類推。

> [!CAUTION]
> 如果您編輯目前的記錄，請務必先呼叫成員函式來儲存變更， `Update` 然後再移至另一筆記錄。 如果您移至另一筆記錄而不進行更新，您的變更就會遺失，而不會發出警告

使用其中一個尋找作業與呼叫或不同， `MoveFirst` `MoveNext` 它只會在不指定條件的情況下，讓第一個或下一個記錄成為最新的。 您可以依照「尋找」作業進行移動作業。

使用「尋找」作業時，請記住下列事項：

- 如果傳回 `Find` 非零值，則不會定義目前的記錄。 在此情況下，您必須將目前的記錄指標放回有效的記錄。

- 您無法使用具有順向滾動快照集類型記錄集的尋找作業。

- 當您搜尋包含日期的欄位時，您應該使用美國日期格式 (月-日) ，即使您不是使用美國版本的 Microsoft Jet database engine 也是一樣。否則，可能找不到相符的記錄。

- 使用 ODBC 資料庫和大型動態集時，您可能會發現使用尋找作業很慢，特別是在處理大型記錄集時。 您可以使用 SQL 查詢搭配自訂的 **ORDERBY** 或 **WHERE** 子句、參數查詢，或抓取 `CDaoQuerydef` 特定索引記錄的物件，來改善效能。

如需相關資訊，請參閱 DAO 說明中的「FindFirst、FindLast、FindNext、FindPrevious 方法」主題。

## <a name="cdaorecordsetgetabsoluteposition"></a><a name="getabsoluteposition"></a> CDaoRecordset：： GetAbsolutePosition

傳回記錄集物件目前記錄的記錄號碼。

```cpp
long GetAbsolutePosition();
```

### <a name="return-value"></a>傳回值

從0到記錄集內記錄數目的整數。 對應于記錄集中目前記錄的序數位置。

### <a name="remarks"></a>備註

基礎 DAO 物件的 AbsolutePosition 屬性值是以零為基底;設定為0時，是指記錄集內的第一筆記錄。 您可以藉由呼叫 [GetRecordCount](#getrecordcount)來判斷記錄集內填入的記錄數目。 呼叫 `GetRecordCount` 可能需要一些時間，因為它必須存取所有記錄來判斷計數。

如果沒有目前的記錄，當記錄集內沒有任何記錄時，就會傳回-1。 如果刪除目前的記錄，則不會定義 AbsolutePosition 屬性值，而且 MFC 會在參考它時擲回例外狀況。 若為動態集類型記錄集，新的記錄會加入至順序的結尾。

> [!NOTE]
> 這個屬性並非用來做為代理記錄號碼。 書簽仍是保留並返回指定位置的建議方式，而且是在所有記錄集物件類型上放置目前記錄的唯一方式。 尤其是，在刪除記錄 (s) 之前，指定記錄的位置會變更。 如果重新建立記錄集，也不保證指定的記錄會有相同的絕對位置，因為在記錄集內個別記錄的順序，除非使用 **ORDERBY** 子句來建立 SQL 語句。

> [!NOTE]
> 這個成員函式僅適用于動態集型別和快照集類型的記錄集。

如需相關資訊，請參閱 DAO 說明中的「AbsolutePosition 屬性」主題。

## <a name="cdaorecordsetgetbookmark"></a><a name="getbookmark"></a> CDaoRecordset：： GetBookmark

呼叫這個成員函式，以取得特定記錄中的書簽值。

```cpp
COleVariant GetBookmark();
```

### <a name="return-value"></a>傳回值

傳回值，表示目前記錄上的書簽。

### <a name="remarks"></a>備註

建立或開啟記錄集物件時，它的每個記錄都已有唯一的書簽（如果支援的話）。 呼叫 `CanBookmark` 以判斷記錄集是否支援書簽。

您可以將書簽的值指派給物件，以儲存目前記錄的書簽 `COleVariant` 。 若要在移至不同的記錄之後隨時快速返回該記錄，請 `SetBookmark` 使用對應至該物件值的參數進行呼叫 `COleVariant` 。

> [!NOTE]
> 呼叫重新 [查詢](#requery) 會變更 DAO 書簽。

如需相關資訊，請參閱 DAO 說明中的「書簽屬性」主題。

## <a name="cdaorecordsetgetcachesize"></a><a name="getcachesize"></a> CDaoRecordset：： GetCacheSize

呼叫此成員函式以取得快取的記錄數目。

```cpp
long GetCacheSize();
```

### <a name="return-value"></a>傳回值

值，指定包含要從 ODBC 資料來源本機快取之資料的動態集型別記錄集內的記錄數目。

### <a name="remarks"></a>備註

資料快取可改善應用程式的效能，此應用程式會透過動態集類型的記錄集物件，從遠端伺服器抓取資料。 當應用程式正在執行時，快取是本機記憶體中的一個空間，可保存最近從伺服器中取出的資料。 當要求資料時，Microsoft Jet 資料庫引擎會先檢查快取中是否有要求的資料，而不是從伺服器中抓取，這需要更多時間。 不是來自 ODBC 資料來源的資料，並不會儲存在快取中。

任何 ODBC 資料來源（如附加資料表）都可以有本機快取。

如需相關資訊，請參閱 DAO 說明中的「CacheSize、CacheStart 屬性」主題。

## <a name="cdaorecordsetgetcachestart"></a><a name="getcachestart"></a> CDaoRecordset：： GetCacheStart

呼叫這個成員函式，以取得要快取之記錄集中第一筆記錄的書簽值。

```cpp
COleVariant GetCacheStart();
```

### <a name="return-value"></a>傳回值

`COleVariant`，指定要快取之記錄集中第一筆記錄的書簽。

### <a name="remarks"></a>備註

Microsoft Jet 資料庫引擎會從快取中要求快取範圍內的記錄，而且會向伺服器要求快取範圍之外的記錄。

> [!NOTE]
> 從快取取出的記錄不會反映其他使用者同時對來源資料所做的變更。

如需相關資訊，請參閱 DAO 說明中的「CacheSize、CacheStart 屬性」主題。

## <a name="cdaorecordsetgetcurrentindex"></a><a name="getcurrentindex"></a> CDaoRecordset：： GetCurrentIndex

呼叫這個成員函式，以判斷索引資料表類型物件中目前正在使用的索引 `CDaoRecordset` 。

```cpp
CString GetCurrentIndex();
```

### <a name="return-value"></a>傳回值

， `CString` 其中包含目前與資料表類型記錄集搭配使用之索引的名稱。 如果未設定任何索引，則傳回空字串。

### <a name="remarks"></a>備註

此索引是在資料表類型記錄集中排序記錄的基礎，而且 [Seek](#seek) 成員函式會使用此索引來尋找記錄。

一個 `CDaoRecordset` 物件可以有一個以上的索引，但是一次只能使用一個索引 (雖然 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) 物件可能會在其) 上定義多個索引。

如需相關資訊，請參閱 DAO 說明中的「索引物件」和定義「目前索引」主題。

## <a name="cdaorecordsetgetdatecreated"></a><a name="getdatecreated"></a> CDaoRecordset：： GetDateCreated

呼叫這個成員函式，以取得建立基表的日期和時間。

```cpp
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>傳回值

[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，其中包含建立基表的日期和時間。

### <a name="remarks"></a>備註

日期和時間設定是衍生自基表建立所在的電腦。

如需相關資訊，請參閱 DAO 說明中的「DateCreated、LastUpdated 屬性」主題。

## <a name="cdaorecordsetgetdatelastupdated"></a><a name="getdatelastupdated"></a> CDaoRecordset：： GetDateLastUpdated

呼叫此成員函式，以取得上次更新架構的日期和時間。

```cpp
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>傳回值

[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，包含上一次更新架構)  (架構的日期和時間。

### <a name="remarks"></a>備註

日期和時間設定是衍生自基礎資料表結構 (架構) 上次更新的電腦。

如需相關資訊，請參閱 DAO 說明中的「DateCreated、LastUpdated 屬性」主題。

## <a name="cdaorecordsetgetdefaultdbname"></a><a name="getdefaultdbname"></a> CDaoRecordset：： GetDefaultDBName

呼叫這個成員函式，以判斷此記錄集的資料庫名稱。

```cpp
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>傳回值

`CString`，其中包含從中衍生此記錄集之資料庫的路徑和名稱。

### <a name="remarks"></a>備註

如果建立記錄集時沒有指向 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)的指標，記錄集會使用這個路徑來開啟預設資料庫。 根據預設，此函數會傳回空字串。 當 ClassWizard 從衍生新的記錄集時 `CDaoRecordset` ，會為您建立此函式。

下列範例說明如何在字串中使用雙反斜線 (\\ \\) ，如同正確解讀字串所需。

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

## <a name="cdaorecordsetgetdefaultsql"></a><a name="getdefaultsql"></a> CDaoRecordset：： >getdefaultsql

架構會呼叫這個成員函式，以取得記錄集所依據的預設 SQL 語句。

```cpp
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>傳回值

`CString`包含預設 SQL 語句的。

### <a name="remarks"></a>備註

這可能是資料表名稱或 SQL **SELECT** 語句。

您可以使用 ClassWizard 宣告您的記錄集類別，以間接定義預設 SQL 語句，ClassWizard 會為您執行這項工作。

如果您傳遞 null SQL 字串來 [開啟](#open)，則會呼叫此函式來判斷記錄集的資料表名稱或 SQL。

## <a name="cdaorecordsetgeteditmode"></a><a name="geteditmode"></a> CDaoRecordset：： GetEditMode

呼叫這個成員函式來判斷編輯的狀態，也就是下列其中一個值：

```cpp
short GetEditMode();
```

### <a name="return-value"></a>傳回值

傳回值，這個值表示目前記錄的編輯狀態。

### <a name="remarks"></a>備註

|值|描述|
|-----------|-----------------|
|`dbEditNone`|沒有進行中的編輯作業。|
|`dbEditInProgress`|`Edit` 已被呼叫。|
|`dbEditAdd`|`AddNew` 已被呼叫。|

如需相關資訊，請參閱 DAO 說明中的「EditMode 屬性」主題。

## <a name="cdaorecordsetgetfieldcount"></a><a name="getfieldcount"></a> CDaoRecordset：： GetFieldCount

呼叫這個成員函式，以抓取在記錄集中定義 (資料行) 的欄位數目。

```cpp
short GetFieldCount();
```

### <a name="return-value"></a>傳回值

記錄集中的欄位數目。

### <a name="remarks"></a>備註

如需相關資訊，請參閱 DAO 說明中的「計數屬性」主題。

## <a name="cdaorecordsetgetfieldinfo"></a><a name="getfieldinfo"></a> CDaoRecordset：： Issomapper.getfieldinfo

呼叫這個成員函式，以取得記錄集內欄位的相關資訊。

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
記錄集之 Fields 集合中預先定義之欄位以零為起始的索引，用於依索引查閱。

*fieldinfo*<br/>
[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構的參考。

*dwInfoOptions*<br/>
指定要取得之記錄集相關資訊的選項。 這裡會列出可用的選項，以及這些選項會導致函式傳回的內容。 為了達到最佳效能，請只取出您需要的資訊層級：

- `AFX_DAO_PRIMARY_INFO` (預設) 名稱、類型、大小、屬性

- `AFX_DAO_SECONDARY_INFO` 主要資訊，加上：序數位置、必要、允許零長度、排序次序、外部名稱、來源欄位、來源資料表

- `AFX_DAO_ALL_INFO` 主要和次要資訊，加上：預設值、驗證規則、驗證文字

*lpszName*<br/>
欄位的名稱。

### <a name="remarks"></a>備註

其中一個版本的函數可讓您依索引查閱欄位。 另一個版本可讓您依名稱查閱欄位。

如需所傳回信息的描述，請參閱 [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) 結構。 此結構具有對應至 *dwInfoOptions*描述中所列之資訊專案的成員。 當您要求某個層級的資訊時，您也會取得任何先前層級的資訊。

如需相關資訊，請參閱 DAO 說明中的「屬性屬性」主題。

## <a name="cdaorecordsetgetfieldvalue"></a><a name="getfieldvalue"></a> CDaoRecordset：： GetFieldValue

呼叫這個成員函式，以抓取記錄集中的資料。

```cpp
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
`COleVariant`將儲存欄位值之物件的參考。

*nIndex*<br/>
以零為基底的索引，這是記錄集之 Fields 集合中的欄位，用於依索引查閱。

### <a name="return-value"></a>傳回值

傳回值的兩個版本 `GetFieldValue` 會傳回包含欄位值的 [COleVariant](../../mfc/reference/colevariant-class.md) 物件。

### <a name="remarks"></a>備註

您可以依名稱或序數位置來查閱欄位。

> [!NOTE]
> 更有效率的方式是呼叫此成員函式的其中一個版本，此成員函式會採用 `COleVariant` 物件參考做為參數，而不是呼叫傳回物件的版本 `COleVariant` 。 這個函式的第二個版本是為了回溯相容性而保留。

使用 `GetFieldValue` 和 [SetFieldValue](#setfieldvalue) 可在執行時間以動態方式系結欄位，而不是使用 [DoFieldExchange](#dofieldexchange) 機制來靜態系結資料行。

`GetFieldValue` 而且 `DoFieldExchange` 可以結合機制來改善效能。 例如，您可以使用 `GetFieldValue` 來取出您只需要視需要的值，並將該呼叫指派給介面中的 [詳細資訊] 按鈕。

如需相關資訊，請參閱 DAO 說明中的「欄位物件」和「值屬性」主題。

## <a name="cdaorecordsetgetindexcount"></a><a name="getindexcount"></a> CDaoRecordset：： GetIndexCount

呼叫這個成員函式，以判斷資料表類型記錄集上可用的索引數目。

```cpp
short GetIndexCount();
```

### <a name="return-value"></a>傳回值

資料表類型記錄集內的索引數目。

### <a name="remarks"></a>備註

`GetIndexCount` 適用于迴圈查看記錄集中的所有索引。 基於這個目的，請 `GetIndexCount` 與 [GetIndexInfo](#getindexinfo)搭配使用。 如果您在動態集類型或快照集類型的記錄集上呼叫這個成員函式，MFC 會擲回例外狀況。

如需相關資訊，請參閱 DAO 說明中的「屬性屬性」主題。

## <a name="cdaorecordsetgetindexinfo"></a><a name="getindexinfo"></a> CDaoRecordset：： GetIndexInfo

呼叫這個成員函式，以取得有關基礎資料表中定義之索引的各種資訊，這些資訊是在記錄集基礎資料表中定義的。

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
以零為基底的索引，在資料表的索引集合中，以數位位置查閱。

*indexinfo*<br/>
[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構的參考。

*dwInfoOptions*<br/>
選項，可指定要取得之索引的相關資訊。 這裡會列出可用的選項，以及這些選項會導致函式傳回的內容。 為了達到最佳效能，請只取出您需要的資訊層級：

- `AFX_DAO_PRIMARY_INFO` (預設) 名稱、欄位資訊、欄位

- `AFX_DAO_SECONDARY_INFO` 主要資訊，再加上： Primary、Unique、叢集、IgnoreNulls、Required、Foreign

- `AFX_DAO_ALL_INFO` 主要和次要資訊，加上：相異計數

*lpszName*<br/>
索引物件名稱的指標，用於依名稱查閱。

### <a name="remarks"></a>備註

其中一個版本的函式可讓您依索引在集合中的位置來查閱索引。 另一個版本可讓您依名稱查閱索引。

如需所傳回信息的描述，請參閱 [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) 結構。 此結構具有對應至 *dwInfoOptions*描述中所列之資訊專案的成員。 當您要求某個層級的資訊時，您也會取得任何先前層級的資訊。

如需相關資訊，請參閱 DAO 說明中的「屬性屬性」主題。

## <a name="cdaorecordsetgetlastmodifiedbookmark"></a><a name="getlastmodifiedbookmark"></a> CDaoRecordset：： GetLastModifiedBookmark

呼叫這個成員函式，以抓取最近新增或更新之記錄的書簽。

```cpp
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>傳回值

， `COleVariant` 包含表示最近新增或變更之記錄的書簽。

### <a name="remarks"></a>備註

建立或開啟記錄集物件時，它的每個記錄都已有唯一的書簽（如果支援的話）。 呼叫 [GetBookmark](#getbookmark) ，以判斷記錄集是否支援書簽。 如果記錄集不支援書簽， `CDaoException` 則會擲回。

當您加入記錄時，它會出現在記錄集的結尾，而不是目前的記錄。 若要使新記錄成為目前的，請呼叫 `GetLastModifiedBookmark` ，然後呼叫 `SetBookmark` 以返回新加入的記錄。

如需相關資訊，請參閱 DAO 說明中的「LastModified 屬性」主題。

## <a name="cdaorecordsetgetlockingmode"></a><a name="getlockingmode"></a> CDaoRecordset：： GetLockingMode

呼叫這個成員函式，以判斷記錄集的作用中鎖定類型。

```cpp
BOOL GetLockingMode();
```

### <a name="return-value"></a>傳回值

如果鎖定的型別是封閉式的，則為非零，否則為開放式記錄鎖定的0。

### <a name="remarks"></a>備註

當封閉式鎖定生效時，當您呼叫 [編輯](#edit) 成員函式時，會立即鎖定包含您正在編輯之記錄的資料頁面。 當您呼叫 [Update](#update) 或 [Close](#close) 成員函式或任何移動或尋找作業時，此頁面就會解除鎖定。

當開放式鎖定生效時，只有在使用成員函式來更新記錄時，才會鎖定包含記錄的資料頁面 `Update` 。

使用 ODBC 資料來源時，鎖定模式一律為開放式。

如需相關資訊，請參閱 DAO 說明中的「LockEdits 屬性」和「在多使用者應用程式中鎖定行為」主題。

## <a name="cdaorecordsetgetname"></a><a name="getname"></a> CDaoRecordset：： GetName

呼叫此成員函式，以取得記錄集的名稱。

```cpp
CString GetName();
```

### <a name="return-value"></a>傳回值

， `CString` 其中包含記錄集的名稱。

### <a name="remarks"></a>備註

記錄集的名稱必須以字母開頭，且最多可包含40個字元。 它可以包含數位和底線字元，但不能包含標點符號或空格。

如需相關資訊，請參閱 DAO 說明中的「名稱屬性」主題。

## <a name="cdaorecordsetgetparamvalue"></a><a name="getparamvalue"></a> CDaoRecordset：： GetParamValue

呼叫這個成員函式，以抓取基礎 DAOParameter 物件中所儲存之指定參數的目前值。

```cpp
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
基礎 DAOParameter 物件中參數的數位位置。

*lpszName*<br/>
您需要其值的參數名稱。

### <a name="return-value"></a>傳回值

[COleVariant](../../mfc/reference/colevariant-class.md)類別的物件，其中包含參數的值。

### <a name="remarks"></a>備註

您可以依名稱或在集合中的數位位置來存取參數。

如需相關資訊，請參閱 DAO 說明中的「參數物件」主題。

## <a name="cdaorecordsetgetpercentposition"></a><a name="getpercentposition"></a> CDaoRecordset：： GetPercentPosition

當您使用動態集類型或快照集類型的記錄集時，如果您在 `GetPercentPosition` 完全填入記錄集之前呼叫，則移動量會相對於呼叫 [GetRecordCount](#getrecordcount)所指定的存取記錄數目。

```cpp
float GetPercentPosition();
```

### <a name="return-value"></a>傳回值

介於0和100之間的數位，表示記錄集物件中目前記錄的大約位置（以記錄集內記錄的百分比為基礎）。

### <a name="remarks"></a>備註

您可以藉由呼叫 [MoveLast](#movelast) 來完成所有記錄集的人口，以移至最後一筆記錄，但這可能需要很長的時間。

您可以呼叫 `GetPercentPosition` 所有三種類型的記錄集物件，包括沒有索引的資料表。 不過，您無法 `GetPercentPosition` 在順向滾動快照集上呼叫，或在針對外部資料庫從傳遞查詢開啟的記錄集上呼叫。 如果沒有目前的記錄，或已刪除目前的記錄， `CDaoException` 則會擲回。

如需相關資訊，請參閱 DAO 說明中的「PercentPosition 屬性」主題。

## <a name="cdaorecordsetgetrecordcount"></a><a name="getrecordcount"></a> CDaoRecordset：： GetRecordCount

呼叫此成員函式，以找出已存取記錄集內的多少筆記錄。

```cpp
long GetRecordCount();
```

### <a name="return-value"></a>傳回值

傳回在記錄集物件中存取的記錄數目。

### <a name="remarks"></a>備註

`GetRecordCount` 在所有記錄都被存取之前，不表示動態集類型或快照集類型記錄集包含多少筆記錄。 此成員函式呼叫可能需要相當長的時間才能完成。

一旦存取最後一筆記錄，傳回值就會指出記錄集中刪除的記錄總數。 若要強制存取最後一筆記錄，請呼叫 `MoveLast` 記錄集的或成員函式 `FindLast` 。 您也可以使用 SQL 計數來判斷查詢將傳回的近似記錄數目。

當您的應用程式刪除動態集型別記錄集中的記錄時，的傳回值會 `GetRecordCount` 減少。 不過， `GetRecordCount` 在目前的記錄定位至已刪除的記錄之前，不會反映其他使用者刪除的記錄。 如果您執行的交易會影響記錄計數，然後再回復交易， `GetRecordCount` 將不會反映實際的剩餘記錄數目。

當 `GetRecordCount` 基礎資料表中的變更不會影響快照集類型記錄集的值。

`GetRecordCount`資料表類型記錄集的值會反映資料表中大約的記錄數目，並且會在加入和刪除資料表記錄時立即受到影響。

沒有記錄的記錄集會傳回值0。 使用附加的資料表或 ODBC 資料庫時， `GetRecordCount` 一律會傳回-1。 `Requery`在記錄集上呼叫成員函式，會將的值重設 `GetRecordCount` 為，就像重新執行查詢一樣。

如需相關資訊，請參閱 DAO 說明中的「RecordCount 屬性」主題。

## <a name="cdaorecordsetgetsql"></a><a name="getsql"></a> CDaoRecordset：： GetSQL

呼叫這個成員函式，以取得在開啟記錄集時用來選取記錄集的 SQL 語句。

```cpp
CString GetSQL() const;
```

### <a name="return-value"></a>傳回值

`CString`包含 SQL 語句的。

### <a name="remarks"></a>備註

這通常會是 SQL **SELECT** 語句。

所傳回的字串 `GetSQL` 通常會與您在 *>lpszsql* 參數中傳遞至記錄集的任何字串不同，以 [開啟](#open) 成員函式。 這是因為記錄集會根據您傳遞給的內容 `Open` 、您以 ClassWizard 指定的內容，以及您在 [m_strFilter](#m_strfilter) 中指定的內容和 [m_strSort](#m_strsort) 資料成員，來建立完整的 SQL 語句。

> [!NOTE]
> 只有在呼叫之後，才呼叫這個成員函式 `Open` 。

如需相關資訊，請參閱 DAO 說明中的「SQL 屬性」主題。

## <a name="cdaorecordsetgettype"></a><a name="gettype"></a> CDaoRecordset：： GetType

請在開啟記錄集之後呼叫這個成員函式，以判斷記錄集物件的型別。

```cpp
short GetType();
```

### <a name="return-value"></a>傳回值

下列其中一個值，表示記錄集的類型：

- `dbOpenTable` 資料表類型記錄集

- `dbOpenDynaset` 動態集類型記錄集

- `dbOpenSnapshot` 快照集類型記錄集

### <a name="remarks"></a>備註

如需相關資訊，請參閱 DAO 說明中的「類型屬性」主題。

## <a name="cdaorecordsetgetvalidationrule"></a><a name="getvalidationrule"></a> CDaoRecordset：： GetValidationRule

呼叫這個成員函式來判斷用來驗證資料的規則。

```cpp
CString GetValidationRule();
```

### <a name="return-value"></a>傳回值

`CString`物件，其中包含的值會在記錄變更或加入至資料表時驗證其資料。

### <a name="remarks"></a>備註

這是以文字為基礎的規則，而且會在每次變更基礎資料表時套用。 如果資料不是合法的，MFC 會擲回例外狀況。 傳回的錯誤訊息是基礎欄位物件（如有指定）的 [文字] 屬性的文字，或是基礎欄位物件的 [ValidationRule] 屬性所指定的運算式文字。 您可以呼叫 [GetValidationText](#getvalidationtext) 來取得錯誤訊息的文字。

例如，記錄中的欄位若需要月份的日期，可能會有驗證規則，例如「DAY BETWEEN 1 AND 31」。

如需相關資訊，請參閱 DAO 說明中的「ValidationRule 屬性」主題。

## <a name="cdaorecordsetgetvalidationtext"></a><a name="getvalidationtext"></a> CDaoRecordset：： GetValidationText

呼叫這個成員函式，以抓取基礎欄位物件的 [文字] 屬性的文字。

```cpp
CString GetValidationText();
```

### <a name="return-value"></a>傳回值

`CString`物件，其中包含當欄位值不符合基礎欄位物件的驗證規則時，所顯示之訊息的文字。

### <a name="remarks"></a>備註

如需相關資訊，請參閱 DAO 說明中的「文本保護屬性」主題。

## <a name="cdaorecordsetisbof"></a><a name="isbof"></a> CDaoRecordset：： IsBOF

先呼叫這個成員函式，然後再從記錄中移動到記錄，以瞭解您是否已經離開記錄集的第一筆記錄。

```cpp
BOOL IsBOF() const;
```

### <a name="return-value"></a>傳回值

如果記錄集未包含任何記錄，或如果您在第一筆記錄之前向前滾動，則為非零。否則為0。

### <a name="remarks"></a>備註

您也可以 `IsBOF` 與一起呼叫 `IsEOF` ，以判斷記錄集是否包含任何記錄或空白。 在呼叫之後 `Open` ，如果記錄集沒有包含任何記錄，則會傳回 `IsBOF` 非零值。 當您開啟至少有一筆記錄的記錄集時，第一筆記錄是目前的記錄，並傳回 `IsBOF` 0。

如果第一個記錄是目前的記錄，而且您呼叫 `MovePrev` ， `IsBOF` 將會傳回非零值。 如果傳回 `IsBOF` 非零值，而且您呼叫，則會擲回 `MovePrev` 例外狀況。 如果傳回 `IsBOF` 非零值，則表示目前的記錄未定義，而且任何需要目前記錄的動作都會導致例外狀況。

特定方法對 `IsBOF` 和設定的影響 `IsEOF` ：

- 在 `Open*` 內部呼叫，會呼叫，讓記錄集中的第一個記錄成為目前的記錄 `MoveFirst` 。 因此， `Open` 在一組空的記錄上呼叫會導致 `IsBOF` 和傳回 `IsEOF` 非零值。  (請參閱下表，以瞭解失敗 `MoveFirst` 或呼叫的行為 `MoveLast` 。 ) 

- 成功找到記錄的所有移動作業都會導致 `IsBOF` ，並傳回 `IsEOF` 0。

- `AddNew`接著，呼叫會 `Update` 成功插入新的記錄，會導致傳回 `IsBOF` 0，但只有在已 `IsEOF` 為非零值時才會傳回。 的狀態 `IsEOF` 一律會維持不變。 如同 Microsoft Jet 資料庫引擎所定義，空記錄集的目前記錄指標位於檔案結尾，因此任何新記錄都會插入目前的記錄之後。

- 任何 `Delete` 呼叫，即使它只從記錄集移除剩下的記錄，也不會變更或的值 `IsBOF` `IsEOF` 。

下表顯示允許的移動作業具有不同的組合 `IsBOF` /  `IsEOF` 。

|State|MoveFirst、MoveLast|MovePrev<br /><br /> 移動 < 0|移動0|MoveNext<br /><br /> 移動 > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= 非零，<br /><br /> `IsEOF`=0|允許|例外狀況|例外狀況|允許|
|`IsBOF`=0,<br /><br /> `IsEOF`= 非零|允許|允許|例外狀況|例外狀況|
|兩個非零|例外狀況|例外狀況|例外狀況|例外狀況|
|兩者都是0|允許|允許|允許|允許|

允許移動作業不表示作業會成功找到記錄。 它只會指出是否允許嘗試執行指定的移動作業，而且不會產生例外狀況。 和成員函式的值 `IsBOF` `IsEOF` 可能會因為嘗試移動的結果而變更。

在下表中，不會在值和設定上找到記錄的移動作業效果 `IsBOF` `IsEOF` 如下所示。

|Operations|IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|零|零|
|`Move` 0|沒有變更|沒有變更|
|`MovePrev`， `Move` < 0|零|沒有變更|
|`MoveNext`， `Move` > 0|沒有變更|零|

如需相關資訊，請參閱 DAO 說明中的「BOF、EOF 屬性」主題。

## <a name="cdaorecordsetisdeleted"></a><a name="isdeleted"></a> CDaoRecordset：： IsDeleted

呼叫這個成員函式，以判斷是否已刪除目前的記錄。

```cpp
BOOL IsDeleted() const;
```

### <a name="return-value"></a>傳回值

如果記錄集位於已刪除的記錄上，則為非零;否則為0。

### <a name="remarks"></a>備註

如果您滾動至記錄並傳回 `IsDeleted` TRUE (非零) ，您必須先滾動至另一筆記錄，才能執行任何其他記錄集作業。

> [!NOTE]
> 您不需要檢查快照集或資料表類型記錄集中的記錄已刪除狀態。 因為無法從快照集刪除記錄，所以不需要呼叫 `IsDeleted` 。 針對資料表類型記錄集，已刪除的記錄實際上會從記錄集移除。 一旦刪除記錄之後，您、另一個使用者或另一個記錄集，您就無法回復到該記錄。 因此，不需要呼叫 `IsDeleted` 。

當您從動態集刪除記錄時，它會從記錄集移除，而且您無法回復至該記錄。 但是，如果動態集內的記錄是由另一位使用者或在另一個以相同資料表為基礎的記錄集刪除，則 `IsDeleted` 當您稍後滾動至該記錄時，將會傳回 TRUE。

如需相關資訊，請參閱 DAO 說明中的「刪除方法」、「LastModified 屬性」和「EditMode 屬性」主題。

## <a name="cdaorecordsetiseof"></a><a name="iseof"></a> CDaoRecordset：： IsEOF

當您從記錄中滾動至記錄，以瞭解您是否已超出記錄集的最後一筆記錄時，請呼叫此成員函式。

```cpp
BOOL IsEOF() const;
```

### <a name="return-value"></a>傳回值

如果記錄集未包含任何記錄，或您已結束超過最後一筆記錄，則為非零。否則為0。

### <a name="remarks"></a>備註

您也可以呼叫 `IsEOF` 來判斷記錄集是否包含任何記錄或空白。 在呼叫之後 `Open` ，如果記錄集沒有包含任何記錄，則會傳回 `IsEOF` 非零值。 當您開啟至少有一筆記錄的記錄集時，第一筆記錄是目前的記錄，並傳回 `IsEOF` 0。

當您呼叫時，如果最後一筆記錄是目前的記錄 `MoveNext` ， `IsEOF` 則會傳回非零值。 如果傳回 `IsEOF` 非零值，而且您呼叫，則會擲回 `MoveNext` 例外狀況。 如果傳回 `IsEOF` 非零值，則表示目前的記錄未定義，而且任何需要目前記錄的動作都會導致例外狀況。

特定方法對 `IsBOF` 和設定的影響 `IsEOF` ：

- 在 `Open` 內部呼叫，會呼叫，讓記錄集中的第一個記錄成為目前的記錄 `MoveFirst` 。 因此， `Open` 在一組空的記錄上呼叫會導致 `IsBOF` 和傳回 `IsEOF` 非零值。  (請參閱下表，以取得失敗呼叫的行為 `MoveFirst` 。 ) 

- 成功找到記錄的所有移動作業都會導致 `IsBOF` ，並傳回 `IsEOF` 0。

- `AddNew`接著，呼叫會 `Update` 成功插入新的記錄，會導致傳回 `IsBOF` 0，但只有在已 `IsEOF` 為非零值時才會傳回。 的狀態 `IsEOF` 一律會維持不變。 如同 Microsoft Jet 資料庫引擎所定義，空記錄集的目前記錄指標位於檔案結尾，因此任何新記錄都會插入目前的記錄之後。

- 任何 `Delete` 呼叫，即使它只從記錄集移除剩下的記錄，也不會變更或的值 `IsBOF` `IsEOF` 。

下表顯示允許的移動作業具有不同的組合 `IsBOF` /  `IsEOF` 。

|State|MoveFirst、MoveLast|MovePrev<br /><br /> 移動 < 0|移動0|MoveNext<br /><br /> 移動 > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= 非零，<br /><br /> `IsEOF`=0|允許|例外狀況|例外狀況|允許|
|`IsBOF`=0,<br /><br /> `IsEOF`= 非零|允許|允許|例外狀況|例外狀況|
|兩個非零|例外狀況|例外狀況|例外狀況|例外狀況|
|兩者都是0|允許|允許|允許|允許|

允許移動作業不表示作業會成功找到記錄。 它只會指出是否允許嘗試執行指定的移動作業，而且不會產生例外狀況。 和成員函式的值 `IsBOF` `IsEOF` 可能會因為嘗試移動的結果而變更。

在下表中，不會在值和設定上找到記錄的移動作業效果 `IsBOF` `IsEOF` 如下所示。

|Operations|IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|零|零|
|`Move` 0|沒有變更|沒有變更|
|`MovePrev`， `Move` < 0|零|沒有變更|
|`MoveNext`， `Move` > 0|沒有變更|零|

如需相關資訊，請參閱 DAO 說明中的「BOF、EOF 屬性」主題。

## <a name="cdaorecordsetisfielddirty"></a><a name="isfielddirty"></a> CDaoRecordset：： IsFieldDirty

呼叫這個成員函式，以判斷是否已將動態集的指定欄位資料成員標示為「已變更」 () 變更。

```cpp
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
您要檢查其狀態的欄位資料成員指標，或 Null 以判斷是否有任何欄位有變更。

### <a name="return-value"></a>傳回值

如果指定的欄位資料成員標示為已變更，則為非零。否則為0。

### <a name="remarks"></a>備註

當 `Update` `CDaoRecordset` 呼叫或) 呼叫 (的成員函式更新目前的記錄時，所有中途欄位資料成員中的資料都會傳送到資料來源的記錄 `Edit` `AddNew` 。 透過這種知識，您可以採取進一步的步驟，例如 unflagging 欄位資料成員以標示資料行，使其不會寫入資料來源中。

`IsFieldDirty` 是透過來執行 `DoFieldExchange` 。

## <a name="cdaorecordsetisfieldnull"></a><a name="isfieldnull"></a> CDaoRecordset：： >isfieldnull

呼叫這個成員函式，以判斷記錄集的指定欄位資料成員是否已標記為 Null。

```cpp
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
您要檢查其狀態的欄位資料成員指標，或 Null 以判斷是否有任何欄位為 Null。

### <a name="return-value"></a>傳回值

如果指定的欄位資料成員標記為 Null，則為非零;否則為0。

### <a name="remarks"></a>備註

 (在資料庫術語中，Null 表示「沒有值」，且與 c + + 中的 Null 不同。 ) 如果欄位資料成員標記為 Null，則會將它解釋為沒有值的目前記錄的資料行。

> [!NOTE]
> 在某些情況下，使用 `IsFieldNull` 可能沒有效率，如下列程式碼範例所示：

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
> 如果您使用動態記錄系結，而不是衍生自 `CDaoRecordset` ，請務必使用 VT_Null，如範例所示。

## <a name="cdaorecordsetisfieldnullable"></a><a name="isfieldnullable"></a> CDaoRecordset：： IsFieldNullable

呼叫這個成員函式，以判斷指定的欄位資料成員是否為 "nullable" (可以設定為 Null 值;C + + Null 與 Null 不同，這在資料庫術語中表示「沒有值」 ) 。

```cpp
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>參數

*光伏*<br/>
您要檢查其狀態的欄位資料成員指標，或 Null 以判斷是否有任何欄位為 Null。

### <a name="return-value"></a>傳回值

如果指定的欄位資料成員可以設為 Null，則為非零;否則為0。

### <a name="remarks"></a>備註

不可以是 Null 的欄位必須有值。 如果您在新增或更新記錄時嘗試將這類欄位設定為 Null，資料來源會拒絕加法或 update，且 `Update` 將擲回例外狀況。 當您呼叫時，當 `Update` 您呼叫時，不會發生例外狀況 `SetFieldNull` 。

## <a name="cdaorecordsetisopen"></a><a name="isopen"></a> CDaoRecordset：： IsOpen

呼叫此成員函式，以判斷是否已開啟記錄集。

```cpp
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果 `Open` 之前已通話記錄集物件或成員函式 `Requery` ，而且尚未關閉記錄集，則為非零，否則為0。

### <a name="remarks"></a>備註

## <a name="cdaorecordsetm_bcheckcachefordirtyfields"></a><a name="m_bcheckcachefordirtyfields"></a> CDaoRecordset：： m_bCheckCacheForDirtyFields

包含旗標，指出快取的欄位是否會自動標示為中途 (變更) 和 Null。

### <a name="remarks"></a>備註

旗標的預設值為 TRUE。 此資料成員中的設定會控制整個雙重緩衝機制。 如果您將旗標設為 TRUE，您可以使用 DFX 機制，依欄位逐一關閉快取。 如果您將旗標設定為 FALSE，則必須呼叫 `SetFieldDirty` 和您 `SetFieldNull` 自己。

請先設定此資料成員，然後再呼叫 `Open` 。 這項機制主要是為了方便使用。 效能可能會較慢，因為進行變更時，會對欄位進行雙重緩衝處理。

## <a name="cdaorecordsetm_nfields"></a><a name="m_nfields"></a> CDaoRecordset：： m_nFields

包含記錄集類別中的欄位資料成員數目，以及記錄集在資料來源中選取的資料行數目。

### <a name="remarks"></a>備註

記錄集類別的函式必須 `m_nFields` 使用正確的靜態系結欄位數目進行初始化。 當您使用 ClassWizard 來宣告記錄集類別時，會為您寫入此初始化。 您也可以手動撰寫。

架構會使用此數位來管理欄位資料成員與資料來源上目前記錄之對應資料行之間的互動。

> [!NOTE]
> 此數目必須對應至 `DoFieldExchange` 使用參數呼叫之後，在中註冊的輸出資料行數目 `SetFieldType` `CDaoFieldExchange::outputColumn` 。

您可以使用和，以動態方式系結資料行 `CDaoRecordset::GetFieldValue` `CDaoRecordset::SetFieldValue` 。 如果您這麼做，就不需要在中遞增計數， `m_nFields` 以反映成員函式中的 DFX 函式呼叫數目 `DoFieldExchange` 。

## <a name="cdaorecordsetm_nparams"></a><a name="m_nparams"></a> CDaoRecordset：： m_nParams

包含記錄集類別中的參數資料成員數目—與記錄集查詢一起傳遞的參數數目。

### <a name="remarks"></a>備註

如果您的記錄集類別具有任何參數資料成員，則類別的函式必須使用正確的數位來初始化 *m_nParams* 。 *M_nParams*的值預設為0。 如果您加入的參數資料成員是必須手動完成的作業，您也必須在類別的函式中手動加入初始化，以反映參數的數目 (其必須至少與您 *m_strFilter* 中的 ' ' 預留位置數目相同，或) *m_strSort* 字串。

在參數化記錄集的查詢時，架構會使用這個數位。

> [!NOTE]
> 此數位必須對應至 `DoFieldExchange` 使用參數呼叫之後，在中註冊的 "params" 數目 `SetFieldType` `CFieldExchange::param` 。

如需相關資訊，請參閱 DAO 說明中的「參數物件」主題。

## <a name="cdaorecordsetm_pdaorecordset"></a><a name="m_pdaorecordset"></a> CDaoRecordset：： m_pDAORecordset

包含物件之 DAO 記錄集物件的 OLE 介面指標 `CDaoRecordset` 。

### <a name="remarks"></a>備註

如果您需要直接存取 DAO 介面，請使用此指標。

如需相關資訊，請參閱 DAO 說明中的「記錄集物件」主題。

## <a name="cdaorecordsetm_pdatabase"></a><a name="m_pdatabase"></a> CDaoRecordset：： m_pDatabase

包含物件的指標， `CDaoDatabase` 該物件是記錄集連接到資料來源的物件。

### <a name="remarks"></a>備註

這個變數的設定方式有兩種。 一般來說， `CDaoDatabase` 當您在建立記錄集物件時，會將指標傳遞至已開啟的物件。 如果您改為傳遞 Null，則 `CDaoRecordset` `CDaoDatabase` 會為您建立物件，並將它開啟。 在任一種情況下，都會 `CDaoRecordset` 將指標儲存在此變數中。

一般來說，您不會直接需要使用儲存在中的指標 `m_pDatabase` 。 但是，如果您將自己的延伸模組寫入至 `CDaoRecordset` ，您可能需要使用指標。 例如，如果您擲回自己的 (s) ，您可能需要指標 `CDaoException` 。

如需相關資訊，請參閱 DAO 說明中的「資料庫物件」主題。

## <a name="cdaorecordsetm_strfilter"></a><a name="m_strfilter"></a> CDaoRecordset：： m_strFilter

包含用來建立 SQL 語句之 **WHERE** 子句的字串。

### <a name="remarks"></a>備註

它不包含用來篩選記錄 **集的保留** 字。 使用這個資料成員並不適用于資料表類型的記錄集。 使用 `m_strFilter` 指標開啟記錄集時，不會有任何作用 `CDaoQueryDef` 。

當您篩選包含日期的欄位時，請使用美國日期格式 (月-日) ，即使您不是使用美國版本的 Microsoft Jet database engine 也是一樣。否則，可能不會如預期般篩選資料。

如需相關資訊，請參閱 DAO 說明中的「篩選屬性」主題。

## <a name="cdaorecordsetm_strsort"></a><a name="m_strsort"></a> CDaoRecordset：： m_strSort

包含字串，其中包含 SQL 語句的 **orderby** 子句，但不含保留的單字 **ORDERBY**。

### <a name="remarks"></a>備註

您可以針對動態集和快照集類型的記錄集物件進行排序。

您無法排序資料表類型的記錄集物件。 若要判斷資料表類型記錄集的排序次序，請呼叫 [SetCurrentIndex](#setcurrentindex)。

使用指標開啟記錄集時，使用 *m_strSort* 不會有任何作用 `CDaoQueryDef` 。

如需相關資訊，請參閱 DAO 說明中的「排序屬性」主題。

## <a name="cdaorecordsetmove"></a><a name="move"></a> CDaoRecordset：： Move

呼叫這個成員函式，將記錄集 *lRows* 記錄定位於目前的記錄。

```cpp
virtual void Move(long lRows);
```

### <a name="parameters"></a>參數

*lRows*<br/>
向前或向後移動的記錄數目。 正值朝記錄集的結尾往前移動。 負數值會朝一開始向前移動。

### <a name="remarks"></a>備註

您可以向前或向後移動。 `Move( 1 )` 相當於 `MoveNext` ，且 `Move( -1 )` 相當於 `MovePrev` 。

> [!CAUTION]
> 如果記錄集沒有記錄，則呼叫任何函數會擲回 `Move` 例外狀況。 一般來說，在移動作業 `IsBOF` 之前呼叫和， `IsEOF` 以判斷記錄集是否有任何記錄。 在您呼叫 `Open` 或之後 `Requery` ，請呼叫 `IsBOF` 或 `IsEOF` 。

> [!NOTE]
> 如果您已經在記錄集的開頭或結尾處滾動 ( `IsBOF` 或傳回非零的) ，則會擲回 `IsEOF` `Move` 的呼叫 `CDaoException` 。

> [!NOTE]
> 如果您在 `Move` 目前的記錄正在更新或加入時呼叫任何函式，更新就會遺失，而不會發出警告。

當您 `Move` 在順向滾動快照集上呼叫時， *lRows* 參數必須是正整數，而且不允許書簽，因此您只能向前移動。

若要將記錄集內的第一個、最後一個、最後一個或最後一筆記錄設為目前的記錄，請呼叫 `MoveFirst` 、 `MoveLast` 、 `MoveNext` 或成員函式 `MovePrev` 。

如需相關資訊，請參閱 DAO 說明中的「移動方法」和「MoveFirst、MoveLast、MoveNext、MovePrevious 方法」主題。

## <a name="cdaorecordsetmovefirst"></a><a name="movefirst"></a> CDaoRecordset：： MoveFirst

呼叫這個成員函式，讓記錄集內的第一筆記錄 (（如果有任何) 目前的記錄）。

```cpp
void MoveFirst();
```

### <a name="remarks"></a>備註

開啟記錄集之後，您就不需要 `MoveFirst` 立即呼叫。 屆時，如果有任何) 自動成為目前的記錄，則第一筆記錄 (。

> [!CAUTION]
> 如果記錄集沒有記錄，則呼叫任何函數會擲回 `Move` 例外狀況。 一般來說，在移動作業 `IsBOF` 之前呼叫和， `IsEOF` 以判斷記錄集是否有任何記錄。 在您呼叫 `Open` 或之後 `Requery` ，請呼叫 `IsBOF` 或 `IsEOF` 。

> [!NOTE]
> 如果您在 `Move` 目前的記錄正在更新或加入時呼叫任何函式，更新就會遺失，而不會發出警告。

使用函式 `Move` 從記錄移至記錄，而不套用條件。 您可以使用尋找作業，在符合特定條件的動態集類型或快照集類型的記錄集物件中尋找記錄。 若要找出資料表類型記錄集物件中的記錄，請呼叫 `Seek` 。

如果記錄集參考資料表類型的記錄集，則會在資料表的目前索引之後移動。 您可以使用基礎 DAO 物件的 Index 屬性來設定目前的索引。 如果您未設定目前的索引，傳回記錄的順序會是未定義的。

如果您是根據 `MoveLast` SQL 查詢或 querydef 來通話記錄集物件，則會強制執行查詢完成，且會完整填入記錄集物件。

您無法使用順 `MoveFirst` 向滾動快照集來呼叫或 `MovePrev` 成員函式。

若要將記錄集物件中目前記錄的位置，向前或向後移動特定的記錄數目，請呼叫 `Move` 。

如需相關資訊，請參閱 DAO 說明中的「移動方法」和「MoveFirst、MoveLast、MoveNext、MovePrevious 方法」主題。

## <a name="cdaorecordsetmovelast"></a><a name="movelast"></a> CDaoRecordset：： MoveLast

呼叫這個成員函式，以便在記錄集內的任何) 記錄目前的記錄時，將最後一筆記錄 (。

```cpp
void MoveLast();
```

### <a name="remarks"></a>備註

> [!CAUTION]
> 如果記錄集沒有記錄，則呼叫任何函數會擲回 `Move` 例外狀況。 一般來說，在移動作業 `IsBOF` 之前呼叫和， `IsEOF` 以判斷記錄集是否有任何記錄。 在您呼叫 `Open` 或之後 `Requery` ，請呼叫 `IsBOF` 或 `IsEOF` 。

> [!NOTE]
> 如果您在 `Move` 目前的記錄正在更新或加入時呼叫任何函式，更新就會遺失，而不會發出警告。

使用函式 `Move` 從記錄移至記錄，而不套用條件。 您可以使用尋找作業，在符合特定條件的動態集類型或快照集類型的記錄集物件中尋找記錄。 若要找出資料表類型記錄集物件中的記錄，請呼叫 `Seek` 。

如果記錄集參考資料表類型的記錄集，則會在資料表的目前索引之後移動。 您可以使用基礎 DAO 物件的 Index 屬性來設定目前的索引。 如果您未設定目前的索引，傳回記錄的順序會是未定義的。

如果您是根據 `MoveLast` SQL 查詢或 querydef 來通話記錄集物件，則會強制執行查詢完成，且會完整填入記錄集物件。

若要將記錄集物件中目前記錄的位置，向前或向後移動特定的記錄數目，請呼叫 `Move` 。

如需相關資訊，請參閱 DAO 說明中的「移動方法」和「MoveFirst、MoveLast、MoveNext、MovePrevious 方法」主題。

## <a name="cdaorecordsetmovenext"></a><a name="movenext"></a> CDaoRecordset：： MoveNext

呼叫這個成員函式，讓記錄集中的下一筆記錄成為目前的記錄。

```cpp
void MoveNext();
```

### <a name="remarks"></a>備註

建議您先呼叫， `IsBOF` 然後再嘗試移至先前的記錄。 `MovePrev`如果傳回非零，則的呼叫將會擲回 `CDaoException` `IsBOF` ，表示您已在第一筆記錄之前滾動，或記錄集未選取任何記錄。

> [!CAUTION]
> 如果記錄集沒有記錄，則呼叫任何函數會擲回 `Move` 例外狀況。 一般來說，在移動作業 `IsBOF` 之前呼叫和， `IsEOF` 以判斷記錄集是否有任何記錄。 在您呼叫 `Open` 或之後 `Requery` ，請呼叫 `IsBOF` 或 `IsEOF` 。

> [!NOTE]
> 如果您在 `Move` 目前的記錄正在更新或加入時呼叫任何函式，更新就會遺失，而不會發出警告。

使用函式 `Move` 從記錄移至記錄，而不套用條件。 您可以使用尋找作業，在符合特定條件的動態集類型或快照集類型的記錄集物件中尋找記錄。 若要找出資料表類型記錄集物件中的記錄，請呼叫 `Seek` 。

如果記錄集參考資料表類型的記錄集，則會在資料表的目前索引之後移動。 您可以使用基礎 DAO 物件的 Index 屬性來設定目前的索引。 如果您未設定目前的索引，傳回記錄的順序會是未定義的。

若要將記錄集物件中目前記錄的位置，向前或向後移動特定的記錄數目，請呼叫 `Move` 。

如需相關資訊，請參閱 DAO 說明中的「移動方法」和「MoveFirst、MoveLast、MoveNext、MovePrevious 方法」主題。

## <a name="cdaorecordsetmoveprev"></a><a name="moveprev"></a> CDaoRecordset：： MovePrev

呼叫這個成員函式，讓記錄集內的前一筆記錄成為目前的記錄。

```cpp
void MovePrev();
```

### <a name="remarks"></a>備註

建議您先呼叫， `IsBOF` 然後再嘗試移至先前的記錄。 `MovePrev`如果傳回非零，則的呼叫將會擲回 `CDaoException` `IsBOF` ，表示您已在第一筆記錄之前滾動，或記錄集未選取任何記錄。

> [!CAUTION]
> 如果記錄集沒有記錄，則呼叫任何函數會擲回 `Move` 例外狀況。 一般來說，在移動作業 `IsBOF` 之前呼叫和， `IsEOF` 以判斷記錄集是否有任何記錄。 在您呼叫 `Open` 或之後 `Requery` ，請呼叫 `IsBOF` 或 `IsEOF` 。

> [!NOTE]
> 如果您在 `Move` 目前的記錄正在更新或加入時呼叫任何函式，更新就會遺失，而不會發出警告。

使用函式 `Move` 從記錄移至記錄，而不套用條件。 您可以使用尋找作業，在符合特定條件的動態集類型或快照集類型的記錄集物件中尋找記錄。 若要找出資料表類型記錄集物件中的記錄，請呼叫 `Seek` 。

如果記錄集參考資料表類型的記錄集，則會在資料表的目前索引之後移動。 您可以使用基礎 DAO 物件的 Index 屬性來設定目前的索引。 如果您未設定目前的索引，傳回記錄的順序會是未定義的。

您無法使用順 `MoveFirst` 向滾動快照集來呼叫或 `MovePrev` 成員函式。

若要將記錄集物件中目前記錄的位置，向前或向後移動特定的記錄數目，請呼叫 `Move` 。

如需相關資訊，請參閱 DAO 說明中的「移動方法」和「MoveFirst、MoveLast、MoveNext、MovePrevious 方法」主題。

## <a name="cdaorecordsetopen"></a><a name="open"></a> CDaoRecordset：： Open

您必須呼叫此成員函式，才能取得記錄集的記錄。

```cpp
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

- `dbOpenDynaset` 具有雙向滾動的動態集類型記錄集。 此為預設值。

- `dbOpenTable` 具有雙向滾動的資料表類型記錄集。

- `dbOpenSnapshot` 具有雙向滾動的快照集類型記錄集。

*>lpszsql*<br/>
字串指標，其中包含下列其中一項：

- Null 指標。

- 一或多個 tabledefs 和/或 querydefs (逗號分隔) 的名稱。

- SQL **SELECT** 語句 (選擇性地搭配 sql **WHERE** 或 **ORDERBY** 子句) 。

- 傳遞查詢。

*nOptions*<br/>
下列一或多個選項。 預設值為 0。 可能值如下所示：

- `dbAppendOnly` 您只能將新的記錄附加 (動態集類型記錄集) 。 此選項表示記錄可能只會附加。 MFC ODBC 資料庫類別具有僅限附加選項，可讓您抓取和附加記錄。

- `dbForwardOnly` 記錄集是順向滾動快照集。

- `dbSeeChanges` 如果有其他使用者變更您正在編輯的資料，則產生例外狀況。

- `dbDenyWrite` 其他使用者無法修改或加入記錄。

- `dbDenyRead` 其他使用者無法只)  (資料表類型的記錄集來查看記錄。

- `dbReadOnly` 您只能查看記錄;其他使用者可以修改它們。

- `dbInconsistent` 只)  (的動態集類型記錄集，允許不一致的更新。

- `dbConsistent` 只有)  (動態集類型記錄集，才允許一致的更新。

> [!NOTE]
> 常數 `dbConsistent` 和 `dbInconsistent` 都是互斥的。 您可以使用其中一個，但不能同時使用指定的實例 `Open` 。

*pTableDef*<br/>
[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)物件的指標。 此版本僅對資料表類型記錄集有效。 使用這個選項時， `CDaoDatabase` 不會使用用來建立的指標， `CDaoRecordset` 而是使用 tabledef 所在的資料庫。

*pQueryDef*<br/>
[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)物件的指標。 此版本僅適用于動態集型別和快照集類型的記錄集。 使用這個選項時， `CDaoDatabase` 不會使用用來建立的指標，而是會 `CDaoRecordset` 使用該位置所在的資料庫。

### <a name="remarks"></a>備註

在呼叫之前 `Open` ，您必須先建立記錄集物件。 有幾個方式可做到這點：

- 當您建立記錄集物件時，請將指標傳遞至 `CDaoDatabase` 已開啟的物件。

- 當您建立記錄集物件時，請將指標傳遞至 `CDaoDatabase` 未開啟的物件。 記錄集會開啟 `CDaoDatabase` 物件，但在記錄集物件關閉時不會將它關閉。

- 當您建立記錄集物件時，請傳遞 Null 指標。 記錄集物件會呼叫 `GetDefaultDBName` 以取得 Microsoft Access 的名稱。要開啟的 MDB 檔案。 然後，當記錄集開啟時，記錄集會開啟 `CDaoDatabase` 物件，並讓它保持開啟。 當您在 `Close` 記錄集上呼叫時，該 `CDaoDatabase` 物件也會關閉。

    > [!NOTE]
    >  當記錄集開啟 `CDaoDatabase` 物件時，它會開啟具有非獨佔存取權的資料來源。

針對 `Open` 使用 *>lpszsql* 參數的版本，一旦記錄集開啟之後，您就可以使用數種方式來取得記錄。 第一個選項是在中具有 DFX 函數 `DoFieldExchange` 。 第二個選項是藉由呼叫成員函式來使用動態繫結 `GetFieldValue` 。 這些選項可以個別或合併方式來執行。 如果結合了，您就必須在的呼叫上自行傳遞 SQL 語句 `Open` 。

當您使用傳遞物件的第二個版本時 `Open` `CDaoTableDef` ，產生的資料行將可供您透過 `DoFieldExchange` 和 DFX 機制進行系結，以及/或透過動態繫結 `GetFieldValue` 。

> [!NOTE]
> 您只能 `Open` 使用 `CDaoTableDef` 資料表類型記錄集的物件來呼叫。

當您使用傳遞物件的第三個版本時， `Open` `CDaoQueryDef` 該查詢將會執行，而且產生的資料行將可供您透過 `DoFieldExchange` 和 DFX 機制進行系結，以及/或透過動態繫結 `GetFieldValue` 。

> [!NOTE]
> 您只能 `Open` 使用 `CDaoQueryDef` 動態集型別和快照集類型記錄集的物件來呼叫。

若是使用參數的第一個版本 `Open` `lpszSQL` ，則會根據下表所示的準則來選取記錄。

|`lpszSQL` 參數的值|選取的記錄取決於|範例|
|--------------------------------------|----------------------------------------|-------------|
|NULL|所傳回的字串 `GetDefaultSQL` 。||
|一或多個 tabledefs 和/或 querydef 名稱的逗號分隔清單。|中表示的所有資料行 `DoFieldExchange` 。|`"Customer"`|
|從資料表清單**中****選取**資料行清單|指定之 tabledef (s) 和/或 querydef (s 的指定資料行) 。|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

一般的程式是傳遞 Null 給， `Open` 在此情況下，會 `Open` 呼叫 `GetDefaultSQL` ，這是在建立衍生類別時，ClassWizard 所產生的可覆寫成員函式 `CDaoRecordset` 。 此值會提供您在 ClassWizard 中指定)  (的 tabledef (s) 和/或 querydef 名稱。 您可以改為在 *>lpszsql* 參數中指定其他資訊。

無論您傳遞的 `Open` 是什麼， (字串的查詢都可以有 Sql **WHERE** 和 **ORDERBY** 子句附加到您傳遞的 *>lpszsql* 字串) 然後執行查詢。 您可以在呼叫之後呼叫來檢查已建立的字串 `GetSQL` `Open` 。

記錄集類別的欄位資料成員會系結至所選資料的資料行。 如果傳回任何記錄，則第一筆記錄會成為目前的記錄。

如果您想要設定記錄集的選項，例如篩選或排序，請在 `m_strSort` 您建立 `m_strFilter` 記錄集物件之後，但在呼叫之前，設定或 `Open` 。 如果您想要在記錄集已經開啟之後重新整理記錄集內的記錄，請呼叫 `Requery` 。

如果您 `Open` 在動態集類型或快照集類型的記錄集上呼叫，或如果資料來源參考了表示附加資料表的 SQL 語句或 tabledef，您就不能使用 `dbOpenTable` 做為型別引數; 如果這樣做，MFC 會擲回例外狀況。 若要判斷 tabledef 物件是否代表附加的資料表，請建立 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) 物件，並呼叫其 [GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect) 成員函式。

`dbSeeChanges`如果您想要在編輯或刪除相同的記錄時，將其他使用者或電腦上其他程式所做的變更補漏陷，請使用旗標。 例如，如果兩位使用者開始編輯相同的記錄，則呼叫成員函式的第一個使用者會 `Update` 成功。 當 `Update` 第二位使用者呼叫時，會擲回 `CDaoException` 。 同樣地，如果第二位使用者嘗試呼叫 `Delete` 來刪除記錄，而且第一個使用者已經變更， `CDaoException` 就會發生。

一般而言，如果使用者在 `CDaoException` 更新時取得此值，您的程式碼應該重新整理欄位的內容，並取得新修改的值。 如果刪除程式中發生例外狀況，您的程式碼可能會向使用者顯示新的記錄資料，並顯示一則訊息，指出資料最近已變更。 此時，您的程式碼可以要求使用者仍然想要刪除記錄的確認。

> [!TIP]
> `dbForwardOnly`當您的應用程式透過從 ODBC 資料來源開啟的記錄集進行單一傳遞時，請使用順向滾動選項 () 來改善效能。

如需相關資訊，請參閱 DAO 說明中的「OpenRecordset 方法」主題。

## <a name="cdaorecordsetrequery"></a><a name="requery"></a> CDaoRecordset：： Requery

呼叫此成員函式以重建記錄集)  (重新整理。

```cpp
virtual void Requery();
```

### <a name="remarks"></a>備註

如果傳回任何記錄，則第一筆記錄會成為目前的記錄。

為了讓記錄集反映您或其他使用者對資料來源所做的新增和刪除動作，您必須藉由呼叫來重建記錄集 `Requery` 。 如果記錄集是動態集，則會自動反映您或其他使用者對其現有記錄所做的更新， (但不是新增) 。 如果記錄集是快照集，您必須呼叫 `Requery` 以反映其他使用者的編輯，以及新增和刪除。

如果是動態集或快照集，請 `Requery` 在您想要使用參數值重建記錄集時呼叫。 設定新的篩選準則或排序，方法是在呼叫之前設定 [m_strFilter](#m_strfilter) 和 [m_strSort](#m_strsort) `Requery` 。 在呼叫之前，先將新值指派給參數資料成員，以設定新的參數 `Requery` 。

如果重建記錄集的嘗試失敗，就會關閉記錄集。 在呼叫之前 `Requery` ，您可以藉由呼叫 [CanRestart](#canrestart) 成員函式來判斷是否可以重新查詢記錄集。 `CanRestart` 不保證 `Requery` 會成功。

> [!CAUTION]
> `Requery`只有在呼叫之後才呼叫 `Open` 。

> [!NOTE]
> 呼叫重新 [查詢](#requery) 會變更 DAO 書簽。

`Requery`如果呼叫傳回0，您就無法在動態集類型或快照集類型的記錄集上呼叫，也不能 `CanRestart` 在資料表類型的記錄集上使用它。

如果 `IsBOF` 在呼叫之後，和都傳回 `IsEOF` 非零 `Requery` ，則查詢不會傳回任何記錄，而且記錄集不會包含任何資料。

如需相關資訊，請參閱 DAO 說明中的「重新查詢方法」主題。

## <a name="cdaorecordsetseek"></a><a name="seek"></a> CDaoRecordset：： Seek

呼叫這個成員函式，以在索引的資料表類型記錄集物件中尋找符合目前索引之指定準則的記錄，並將其記錄為目前的記錄。

```cpp
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
下列其中一個字串運算式：「<」、「 \<=", "=", "> =」或「>」。

*pKey1*<br/>
[COleVariant](../../mfc/reference/colevariant-class.md)的指標，其值會對應至索引中的第一個欄位。 必要。

*pKey2*<br/>
的指標 `COleVariant` ，其值會對應至索引中的第二個欄位（如果有的話）。 預設值為 Null。

*pKey3*<br/>
的指標 `COleVariant` ，其值會對應至索引中的第三個欄位（如果有的話）。 預設值為 Null。

*pKeyArray*<br/>
變數陣列的指標。 陣列大小會對應到索引中的欄位數目。

*nKeys*<br/>
對應至陣列大小的整數，也就是索引中的欄位數目。

> [!NOTE]
> 請勿在索引鍵中指定萬用字元。 萬用字元會導致 `Seek` 沒有傳回相符的記錄。

### <a name="return-value"></a>傳回值

如果找到相符的記錄，則為非零，否則為0。

### <a name="remarks"></a>備註

使用第二個 (陣列) 版本 `Seek` 來處理四個欄位或更多欄位的索引。

`Seek` 在資料表類型記錄集上啟用高效能索引搜尋。 您必須在呼叫之前呼叫，以設定目前的索引 `SetCurrentIndex` `Seek` 。 如果索引識別非唯一的索引鍵欄位，則 `Seek` 會尋找符合準則的第一筆記錄。 如果您未設定索引，則會擲回例外狀況。

請注意，如果您未建立 UNICODE 記錄集，則 `COleVariant` 物件必須明確宣告為 ANSI。 這可以藉由使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) ** (** *lpszSrc* **、** *vtSrc* **) **形式的函式，將*vtSrc*設定為 `VT_BSTRT` (ANSI) 或使用 `COleVariant` 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) ** (** *lpszSrc* **，** *vtSrc* **) **並將*vtSrc*設定為 `VT_BSTRT` 。

當您呼叫時 `Seek` ，會傳遞一個或多個索引鍵值和比較運算子 ( "<"、" \<=", "=", "> =" 或 ">" ) 。 `Seek` 搜尋指定的索引鍵欄位，並找出滿足 *lpszComparison* 和 *pKey1*所指定準則的第一筆記錄。 一旦找到， `Seek` 就會傳回非零，並使該記錄成為最新的。 如果 `Seek` 找不到相符項，則會傳回 `Seek` 零，而且目前的記錄未定義。 直接使用 DAO 時，您必須明確檢查 NoMatch 屬性。

如果 `lpszComparison` 為 "="、">=" 或 ">"，則會從 `Seek` 索引的開頭開始。 如果 *lpszComparison* 是 "<" 或 "<="，則會 `Seek` 從索引的結尾開始，然後向後搜尋，除非結尾有重複的索引項目。 在此情況下，會從 `Seek` 索引結尾的重複索引項目中的任意專案開始。

當您使用時，不一定要有目前的記錄 `Seek` 。

若要在符合特定條件的動態集類型或快照集類型記錄集中找出記錄，請使用尋找作業。 若要包含所有記錄，而不只是滿足特定條件的記錄，請使用移動作業從記錄移至記錄。

您無法 `Seek` 在任何型別的附加資料表上呼叫，因為附加的資料表必須以動態集類型或快照集類型記錄集的形式開啟。 但是，如果您呼叫 `CDaoDatabase::Open` 直接開啟可安裝的 ISAM 資料庫，您可以在 `Seek` 該資料庫中的資料表上呼叫，不過效能可能會很慢。

如需相關資訊，請參閱 DAO 說明中的「搜尋方法」主題。

## <a name="cdaorecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a> CDaoRecordset：： SetAbsolutePosition

設定記錄集物件目前記錄的相對記錄號碼。

```cpp
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>參數

*lPosition*<br/>
對應于記錄集中目前記錄的序數位置。

### <a name="remarks"></a>備註

呼叫可 `SetAbsolutePosition` 讓您根據其在動態集類型或快照集類型記錄集中的序數位置，將目前的記錄指標定位至特定記錄。 您也可以藉由呼叫 [GetAbsolutePosition](#getabsoluteposition)來判斷目前的記錄號碼。

> [!NOTE]
> 這個成員函式僅適用于動態集型別和快照集類型的記錄集。

基礎 DAO 物件的 AbsolutePosition 屬性值是以零為基底;設定為0時，是指記錄集內的第一筆記錄。 如果設定的值大於填入的記錄數目，就會導致 MFC 擲回例外狀況。 您可以藉由呼叫成員函式來判斷記錄集內填入的記錄數目 `GetRecordCount` 。

如果刪除目前的記錄，則不會定義 AbsolutePosition 屬性值，而且 MFC 會在參考它時擲回例外狀況。 新記錄會新增至序列結尾。

> [!NOTE]
> 這個屬性並非用來做為代理記錄號碼。 書簽仍是保留並返回指定位置的建議方式，而且是在支援書簽的所有記錄集物件類型上放置目前記錄的唯一方式。 尤其是，在刪除記錄 (s) 之前，指定記錄的位置會變更。 如果重新建立記錄集，也不保證指定的記錄會有相同的絕對位置，因為在記錄集內個別記錄的順序，除非使用 **ORDERBY** 子句來建立 SQL 語句。

如需相關資訊，請參閱 DAO 說明中的「AbsolutePosition 屬性」主題。

## <a name="cdaorecordsetsetbookmark"></a><a name="setbookmark"></a> CDaoRecordset：： SetBookmark

呼叫這個成員函式，將記錄集放置於包含指定書簽的記錄上。

```cpp
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>參數

*varBookmark*<br/>
包含特定記錄之書簽值的 [COleVariant](../../mfc/reference/colevariant-class.md) 物件。

### <a name="remarks"></a>備註

建立或開啟記錄集物件時，它的每個記錄都已經有唯一的書簽。 您可以呼叫 `GetBookmark` 並將值儲存至物件，以抓取目前記錄的書簽 `COleVariant` 。 您稍後可以 `SetBookmark` 使用已儲存的書簽值來呼叫，以返回該記錄。

> [!NOTE]
> 呼叫重新 [查詢](#requery) 會變更 DAO 書簽。

請注意，如果您未建立 UNICODE 記錄集，則 `COleVariant` 物件必須明確宣告為 ANSI。 這可以藉由使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) ** (** *lpszSrc* **、** *vtSrc* **) **形式的函式，將*vtSrc*設定為 `VT_BSTRT` (ANSI) 或使用 `COleVariant` 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) ** (** *lpszSrc* **，** *vtSrc* **) **並將*vtSrc*設定為 `VT_BSTRT` 。

如需相關資訊，請參閱 DAO 說明中的「書簽屬性」和「Bookmarkable 屬性」主題。

## <a name="cdaorecordsetsetcachesize"></a><a name="setcachesize"></a> CDaoRecordset：： SetCacheSize

呼叫這個成員函式，以設定要快取的記錄數目。

```cpp
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>參數

*lSize*<br/>
指定記錄的數目。 一般的值是100。 設定為0會關閉快取。 設定必須介於5到1200筆記錄之間。 快取可能會使用大量的記憶體。

### <a name="remarks"></a>備註

當應用程式正在執行時，快取是本機記憶體中的一個空間，可保存最近從伺服器中取出的資料。 資料快取可改善應用程式的效能，此應用程式會透過動態集類型的記錄集物件，從遠端伺服器抓取資料。 當要求資料時，Microsoft Jet 資料庫引擎會先檢查快取中是否有要求的資料，而不是從伺服器中抓取，這需要更多時間。 不是來自 ODBC 資料來源的資料，並不會儲存在快取中。

任何 ODBC 資料來源（如附加資料表）都可以有本機快取。 若要建立快取，請從遠端資料源開啟記錄集物件，呼叫 `SetCacheSize` 和 `SetCacheStart` 成員函式，然後呼叫成員函式， `FillCache` 或使用其中一個移動作業來逐步執行記錄。 成員函式的 *lSize* 參數 `SetCacheSize` 可以根據您的應用程式可以一次處理的記錄數目。 例如，如果您使用記錄集做為要在螢幕上顯示的資料來源，您可以將 `SetCacheSize` *lSize* 參數傳遞為20，一次顯示20筆記錄。

如需相關資訊，請參閱 DAO 說明中的「CacheSize、CacheStart 屬性」主題。

## <a name="cdaorecordsetsetcachestart"></a><a name="setcachestart"></a> CDaoRecordset：： SetCacheStart

呼叫這個成員函式，以指定要快取之記錄集中第一筆記錄的書簽。

```cpp
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>參數

*varBookmark*<br/>
[COleVariant](../../mfc/reference/colevariant-class.md) ，指定要快取之記錄集中第一筆記錄的書簽。

### <a name="remarks"></a>備註

您可以針對成員函式的 *varBookmark* 參數，使用任何記錄的書簽值 `SetCacheStart` 。 建立您想要使用目前記錄來啟動快取的記錄、使用 [SetBookmark](#setbookmark)為該記錄建立書簽，然後傳遞書簽值做為成員函式的參數 `SetCacheStart` 。

Microsoft Jet 資料庫引擎會從快取中要求快取範圍內的記錄，而且會向伺服器要求快取範圍之外的記錄。

從快取取出的記錄不會反映其他使用者同時對來源資料所做的變更。

若要強制更新所有快取的資料，請將的 *lSize* 參數傳遞 `SetCacheSize` 為0，然後 `SetCacheSize` 以您原先要求的快取大小再次呼叫，然後再呼叫成員函式 `FillCache` 。

請注意，如果您未建立 UNICODE 記錄集，則 `COleVariant` 物件必須明確宣告為 ANSI。 這可以藉由使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) ** (** *lpszSrc* **、** *vtSrc* **) **形式的函式，將*vtSrc*設定為 `VT_BSTRT` (ANSI) 或使用 `COleVariant` 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) ** (** *lpszSrc* **，** *vtSrc* **) **並將*vtSrc*設定為 `VT_BSTRT` 。

如需相關資訊，請參閱 DAO 說明中的主題 CacheSize、CacheStart 屬性（property）。

## <a name="cdaorecordsetsetcurrentindex"></a><a name="setcurrentindex"></a> CDaoRecordset：： SetCurrentIndex

呼叫這個成員函式，以設定資料表類型記錄集的索引。

```cpp
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>參數

*lpszIndex*<br/>
指標，包含要設定之索引的名稱。

### <a name="remarks"></a>備註

基表中的記錄不會以任何特定順序儲存。 設定索引會變更從資料庫傳回的記錄順序，但不會影響記錄的儲存順序。 必須已定義指定的索引。 如果您嘗試使用不存在的索引物件，或當您呼叫 [Seek](#seek)時未設定索引，MFC 會擲回例外狀況。

您可以藉由呼叫 [CDaoTableDef：： CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) ，並將新索引附加至基礎 tabledef 的 index 集合，藉由呼叫 [CDaoTableDef：： Append](../../mfc/reference/cdaotabledef-class.md#append)，然後重新開啟記錄集，來為數據表建立新的索引。

從資料表類型記錄集傳回的記錄只能由針對基礎 tabledef 所定義的索引來排序。 若要以其他順序排序記錄，您可以使用儲存在[CDaoRecordset：： m_strSort](#m_strsort)中的 SQL **ORDERBY**子句來開啟動態集類型或快照集類型的記錄集。

如需相關資訊，請參閱 DAO 說明中的「索引物件」和定義「目前索引」主題。

## <a name="cdaorecordsetsetfielddirty"></a><a name="setfielddirty"></a> CDaoRecordset：： SetFieldDirty

呼叫這個成員函式，將記錄集的欄位資料成員標記為已變更或未變更。

```cpp
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>參數

*光伏*<br/>
包含記錄集的欄位資料成員位址或 Null。 如果是 Null，則記錄集內的所有欄位資料成員都會加上旗標。 在資料庫術語中， (c + + Null 與 Null 不同，這表示「沒有值」。) 

*bDirty*<br/>
如果欄位資料成員要標示為「中途」 () 變更，則為 TRUE。 否則，如果欄位資料成員要標示為「清除」 (未變更) ，則為 FALSE。

### <a name="remarks"></a>備註

將欄位標示為未變更可確保欄位不會更新。

此架構會標記變更的欄位資料成員，以確保 DAO 記錄欄位交換 (DFX) 機制將這些成員寫入資料來源的記錄。 變更欄位的值時，通常會自動將欄位設定為自動變更，因此您不需要 `SetFieldDirty` 自行呼叫，但有時候您可能會想要確保不論欄位資料成員中的值為何，都會明確更新或插入資料行。 DFX 機制也採用 PSEUDONull 的使用。 如需詳細資訊，請參閱 [CDaoFieldExchange：： m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

如果未使用雙重緩衝機制，則變更欄位的值不會自動將欄位設定為中途。 在此情況下，必須將欄位明確設定為中途。 [M_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的旗標會控制此自動欄位檢查。

> [!NOTE]
> 只有在您呼叫 [Edit](#edit) 或 [AddNew](#addnew)之後，才呼叫這個成員函式。

針對函式的第一個引數使用 Null，會將函數套用至中的所有 `outputColumn` 欄位，而不是中的 **param** 欄位 `CDaoFieldExchange` 。 例如，呼叫

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

只會將 `outputColumn` 欄位設定為 Null; **param** 欄位將不會受到影響。

若要使用 **參數**，您必須提供您想要處理之個別 **參數** 的實際位址，例如：

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

這表示您無法將所有的 **參數** 欄位都設定為 Null，就像您可以使用 `outputColumn` 欄位一樣。

`SetFieldDirty` 是透過來執行 `DoFieldExchange` 。

## <a name="cdaorecordsetsetfieldnull"></a><a name="setfieldnull"></a> CDaoRecordset：： SetFieldNull

呼叫這個成員函式，將記錄集的欄位資料成員標記為 Null (明確地說沒有值) 或非 Null。

```cpp
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>參數

*光伏*<br/>
包含記錄集的欄位資料成員位址或 Null。 如果是 Null，則記錄集內的所有欄位資料成員都會加上旗標。 在資料庫術語中， (c + + Null 與 Null 不同，這表示「沒有值」。) 

*bNull*<br/>
如果欄位資料成員要標示為沒有值 (Null) ，則為非零。 否則，如果欄位資料成員要標示為非 Null，則為0。

### <a name="remarks"></a>備註

`SetFieldNull` 用於機制中系結的欄位 `DoFieldExchange` 。

當您將新記錄加入至記錄集時，所有欄位資料成員一開始都會設定為 Null 值，並標示為「已變更」 () 變更。 當您從資料來源抓取記錄時，其資料行可能已經有值或為 Null。 如果不適合讓欄位成為 Null，則會擲回 [CDaoException](../../mfc/reference/cdaoexception-class.md) 。

如果您要使用雙重緩衝機制，例如，如果您特別想要將目前記錄的欄位指定為沒有值，請 `SetFieldNull` 使用 *bNull* 設為 TRUE，將其標示為 Null。 如果欄位先前標示為 Null，而您現在想要為它指定值，只要設定新的值即可。 您不需要移除的 Null 旗標 `SetFieldNull` 。 若要判斷欄位是否允許為 Null，請呼叫 [IsFieldNullable](#isfieldnullable)。

如果您不是使用雙重緩衝機制，則變更欄位的值不會自動將欄位設定為中途和非 Null。 您必須特別將欄位變更為非 Null。 [M_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)中包含的旗標會控制此自動欄位檢查。

DFX 機制會採用 PSEUDONull 的使用。 如需詳細資訊，請參閱 [CDaoFieldExchange：： m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。

> [!NOTE]
> 只有在您呼叫 [Edit](#edit) 或 [AddNew](#addnew)之後，才呼叫這個成員函式。

針對函式的第一個引數使用 Null，只會將函數套用至 `outputColumn` 中的欄位，而不會套用至中的 **param** 欄位 `CDaoFieldExchange` 。 例如，呼叫

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

只會將 `outputColumn` 欄位設定為 Null; **param** 欄位將不會受到影響。

## <a name="cdaorecordsetsetfieldvalue"></a><a name="setfieldvalue"></a> CDaoRecordset：： SetFieldValue

呼叫這個成員函式，以依序數位置或變更字串的值，設定欄位的值。

```cpp
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
[COleVariant](../../mfc/reference/colevariant-class.md)物件的參考，其中包含欄位內容的值。

*nIndex*<br/>
整數，代表欄位在記錄集的欄位集合中的序數位置， (以零為基礎的) 。

*lpszValue*<br/>
包含欄位內容值的字串指標。

### <a name="remarks"></a>備註

使用 `SetFieldValue` 和 [GetFieldValue](#getfieldvalue) 可在執行時間以動態方式系結欄位，而不是使用 [DoFieldExchange](#dofieldexchange) 機制來靜態系結資料行。

請注意，如果您未建立 UNICODE 記錄集，則必須使用不 `SetFieldValue` 包含參數的格式 `COleVariant` ，否則 `COleVariant` 物件必須明確宣告為 ANSI。 這可以藉由使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) ** (** *lpszSrc* **、** *vtSrc* **) **形式的函式，將*vtSrc*設定為 `VT_BSTRT` (ANSI) 或使用 `COleVariant` 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) ** (** *lpszSrc* **，** *vtSrc* **) **並將*vtSrc*設定為 `VT_BSTRT` 。

如需相關資訊，請參閱 DAO 說明中的「欄位物件」和「值屬性」主題。

## <a name="cdaorecordsetsetfieldvaluenull"></a><a name="setfieldvaluenull"></a> CDaoRecordset：： SetFieldValueNull

呼叫這個成員函式，將欄位設定為 Null 值。

```cpp
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
記錄集內欄位的索引，用於以零為基底的索引查閱。

*lpszName*<br/>
記錄集中的功能變數名稱，用於依名稱查閱。

### <a name="remarks"></a>備註

C + + Null 與 Null 不同，它在資料庫術語中表示「沒有值」。

如需相關資訊，請參閱 DAO 說明中的「欄位物件」和「值屬性」主題。

## <a name="cdaorecordsetsetlockingmode"></a><a name="setlockingmode"></a> CDaoRecordset：： SetLockingMode

呼叫此成員函式可設定記錄集的鎖定類型。

```cpp
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>參數

*bPessimistic*<br/>
表示鎖定類型的旗標。

### <a name="remarks"></a>備註

當封閉式鎖定生效時，包含您正在編輯之記錄的2K 頁面會在您呼叫成員函式時立即鎖定 `Edit` 。 當您呼叫 `Update` 或成員函式 `Close` 或任何移動或尋找作業時，此頁面就會解除鎖定。

當開放式鎖定生效時，只有在使用成員函式來更新記錄時，才會鎖定包含記錄的2K 頁面 `Update` 。

如果頁面已鎖定，其他使用者就無法在相同頁面上編輯記錄。 如果您呼叫 `SetLockingMode` 並傳遞非零值，而另一位使用者已經鎖定該頁面，則當您呼叫時，會擲回例外狀況 `Edit` 。 其他使用者可以從鎖定的頁面讀取資料。

如果您 `SetLockingMode` 使用零值進行呼叫，並在稍後呼叫 `Update` 另一位使用者鎖定頁面時呼叫，就會發生例外狀況。 若要查看其他使用者對記錄所做的變更 (並遺失) 的變更，請 `SetBookmark` 使用目前記錄的書簽值呼叫成員函式。

使用 ODBC 資料來源時，鎖定模式一律為開放式。

## <a name="cdaorecordsetsetparamvalue"></a><a name="setparamvalue"></a> CDaoRecordset：： SetParamValue

呼叫這個成員函式，在執行時間設定記錄集內的參數值。

```cpp
virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);

virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
參數在 querydef 的 Parameters 集合中的數位位置。

*無 功*<br/>
要設定的值;請參閱備註。

*lpszName*<br/>
您要設定其值的參數名稱。

### <a name="remarks"></a>備註

參數必須已建立為記錄集 SQL 字串的一部分。 您可以依名稱或在集合中的索引位置來存取參數。

指定要設定為物件的值 `COleVariant` 。 如需在物件中設定所需值與類型的相關資訊 `COleVariant` ，請參閱類別 [COleVariant](../../mfc/reference/colevariant-class.md)。 請注意，如果您未建立 UNICODE 記錄集，則 `COleVariant` 物件必須明確宣告為 ANSI。 這可以藉由使用[COleVariant：： COleVariant](../../mfc/reference/colevariant-class.md#colevariant) ** (** *lpszSrc* **、** *vtSrc* **) **形式的函式，將*vtSrc*設定為 `VT_BSTRT` (ANSI) 或使用 `COleVariant` 函數[SetString](../../mfc/reference/colevariant-class.md#setstring) ** (** *lpszSrc* **，** *vtSrc* **) **並將*vtSrc*設定為 `VT_BSTRT` 。

## <a name="cdaorecordsetsetparamvaluenull"></a><a name="setparamvaluenull"></a> CDaoRecordset：： SetParamValueNull

呼叫這個成員函式，將參數設定為 Null 值。

```cpp
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
記錄集內欄位的索引，用於以零為基底的索引查閱。

*lpszName*<br/>
記錄集中的功能變數名稱，用於依名稱查閱。

### <a name="remarks"></a>備註

C + + Null 與 Null 不同，它在資料庫術語中表示「沒有值」。

## <a name="cdaorecordsetsetpercentposition"></a><a name="setpercentposition"></a> CDaoRecordset：： SetPercentPosition

呼叫這個成員函式來設定值，這個值會根據記錄集內記錄的百分比，變更記錄集物件中目前記錄的近似位置。

```cpp
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>參數

*fPosition*<br/>
介於 0 與 100 之間的數字。

### <a name="remarks"></a>備註

使用動態集類型或快照集類型的記錄集時，請先移至最後一個記錄來填入記錄集，然後再呼叫 `SetPercentPosition` 。 如果您在 `SetPercentPosition` 完全填入記錄集之前呼叫，則移動量會相對於所存取的記錄數目（以 [GetRecordCount](#getrecordcount)的值表示）。 您可以藉由呼叫來移至最後一筆記錄 `MoveLast` 。

一旦呼叫之後 `SetPercentPosition` ，對應于該值之近似位置的記錄就會變成最新的。

> [!NOTE]
> `SetPercentPosition`不建議將目前的記錄移到記錄集內的特定記錄。 請改為呼叫 [SetBookmark](#setbookmark) 成員函式。

如需相關資訊，請參閱 DAO 說明中的「PercentPosition 屬性」主題。

## <a name="cdaorecordsetupdate"></a><a name="update"></a> CDaoRecordset：： Update

呼叫或成員函式之後，呼叫這個成員函式 `AddNew` `Edit` 。

```cpp
virtual void Update();
```

### <a name="remarks"></a>備註

需要此呼叫才能完成 `AddNew` 或 `Edit` 操作。

`AddNew`和都 `Edit` 準備一個編輯緩衝區，其中新增或編輯的資料會儲存到資料來源。 `Update` 儲存資料。 只有標示或偵測到已變更的欄位才會更新。

如果資料來源支援交易，您可以將 `Update` 呼叫 (，並將其對應 `AddNew` 或 `Edit` 呼叫) 交易的一部分。

> [!CAUTION]
> 如果您在 `Update` 未先呼叫或的情況下呼叫，則會擲回 `AddNew` `Edit` `Update` `CDaoException` 。 如果您呼叫 `AddNew` 或 `Edit` ，您必須先呼叫， `Update` 然後再呼叫 [MoveNext](#movenext) 或關閉記錄集或資料來源連接。 否則，您的變更就會遺失，而不會發出通知。

當記錄集物件在多使用者環境中搭配保守模式鎖定時，記錄會保持鎖定， `Edit` 直到更新完成為止。 如果記錄集是樂觀地鎖定的，則會在資料庫中更新記錄之前，先鎖定記錄，並與預先編輯的記錄進行比較。 如果自呼叫之後記錄已變更 `Edit` ，則作業 `Update` 會失敗，且 MFC 會擲回例外狀況。 您可以使用變更鎖定模式 `SetLockingMode` 。

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
