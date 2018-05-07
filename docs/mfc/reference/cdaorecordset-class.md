---
title: CDaoRecordset 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 603cd1658af417dfbb7f2d8aa8022275e866a706
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
|[CDaoRecordset::CDaoRecordset](#cdaorecordset)|建構 `CDaoRecordset` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDaoRecordset::AddNew](#addnew)|準備新增新的記錄。 呼叫[更新](#update)完成加入。|  
|[CDaoRecordset::CanAppend](#canappend)|傳回非零，如果新的記錄可以加入至資料錄集透過[AddNew](#addnew)成員函式。|  
|[CDaoRecordset::CanBookmark](#canbookmark)|傳回非零，如果資料錄集支援書籤。|  
|[CDaoRecordset::CancelUpdate](#cancelupdate)|取消任何暫止的更新，因為[編輯](#edit)或[AddNew](#addnew)作業。|  
|[CDaoRecordset::CanRestart](#canrestart)|傳回非零，如果[Requery](#requery)可以呼叫一次執行資料錄集的查詢。|  
|[CDaoRecordset::CanScroll](#canscroll)|傳回非零，如果可以捲動記錄。|  
|[CDaoRecordset::CanTransact](#cantransact)|傳回非零，如果資料來源支援交易。|  
|[CDaoRecordset::CanUpdate](#canupdate)|傳回非零，如果可以更新資料錄集 （您可以新增、 更新或刪除記錄）。|  
|[CDaoRecordset::Close](#close)|關閉資料錄集。|  
|[CDaoRecordset::Delete](#delete)|從資料錄集刪除目前的記錄。 在刪除之後，您必須明確地捲動至另一筆記錄。|  
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|呼叫以交換資料 （在兩個方向） 之間的資料錄集的欄位資料成員和資料來源上對應的記錄。 實作 DAO 資料錄欄位交換 (DFX)。|  
|[CDaoRecordset::Edit](#edit)|準備變更目前的記錄。 呼叫**更新**完成編輯。|  
|[CDaoRecordset::FillCache](#fillcache)|填滿所有或部分資料錄集物件，其中包含 ODBC 資料來源中的本機快取。|  
|[CDaoRecordset::Find](#find)|找出第一個下, 一步 上, 一個或最後一個符合指定的準則和記錄目前的記錄會動態類型資料錄集中的特定字串的位置。|  
|[CDaoRecordset::FindFirst](#findfirst)|動態類型或快照集型別資料錄集符合指定的準則和記錄的目前記錄的進行中，找出第一筆記錄。|  
|[CDaoRecordset::FindLast](#findlast)|動態類型或快照集型別資料錄集符合指定的準則和記錄的目前記錄的進行中，找出最後一筆記錄。|  
|[CDaoRecordset::FindNext](#findnext)|動態類型或快照集型別資料錄集符合指定的準則和記錄的目前記錄的進行中，找出下一筆記錄。|  
|[CDaoRecordset::FindPrev](#findprev)|動態類型或快照集型別資料錄集符合指定的準則和記錄的目前記錄的進行中，找出上一筆記錄。|  
|[CDaoRecordset::GetAbsolutePosition](#getabsoluteposition)|傳回資料錄集物件的目前記錄的記錄數目。|  
|[CDaoRecordset::GetBookmark](#getbookmark)|傳回值，表示記錄上的書籤。|  
|[CDaoRecordset::GetCacheSize](#getcachesize)|傳回值，包含要在本機快取從 ODBC 資料來源之資料的動態類型資料錄集中指定的記錄數目。|  
|[CDaoRecordset::GetCacheStart](#getcachestart)|傳回值，指定要快取資料錄集中的第一筆記錄的書籤。|  
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|傳回`CString`索引的資料表類型上包含的索引名稱最最近用`CDaoRecordset`。|  
|[CDaoRecordset::GetDateCreated](#getdatecreated)|傳回基礎基底資料表的日期和時間`CDaoRecordset`建立物件|  
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|傳回的日期和時間的基底資料表基礎設計所做的最新變更`CDaoRecordset`物件。|  
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|傳回預設資料來源的名稱。|  
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|呼叫以取得要執行的預設 SQL 字串。|  
|[CDaoRecordset::GetEditMode](#geteditmode)|傳回值，指出目前的記錄為編輯的狀態。|  
|[CDaoRecordset::GetFieldCount](#getfieldcount)|傳回值，表示資料錄集中的欄位數目。|  
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|傳回資料錄集中的特定類型的欄位資訊。|  
|[CDaoRecordset::GetFieldValue](#getfieldvalue)|傳回資料錄集中的欄位的值。|  
|[CDaoRecordset::GetIndexCount](#getindexcount)|擷取基礎資料錄集的資料表中的索引數目。|  
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|傳回的各種索引的相關資訊。|  
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|用來判斷最最近新增或更新記錄。|  
|[CDaoRecordset::GetLockingMode](#getlockingmode)|傳回值，指出在編輯期間就是作用中的鎖定類型。|  
|[CDaoRecordset::GetName](#getname)|傳回`CString`包含資料錄集的名稱。|  
|[CDaoRecordset::GetParamValue](#getparamvalue)|擷取儲存在基礎 DAOParameter 物件中的指定參數的目前值。|  
|[CDaoRecordset::GetPercentPosition](#getpercentposition)|傳回目前記錄的記錄總數的百分比的位置。|  
|[CDaoRecordset::GetRecordCount](#getrecordcount)|傳回資料錄集物件中存取的記錄的數目。|  
|[CDaoRecordset::GetSQL](#getsql)|取得用來選取記錄以供資料錄集的 SQL 字串。|  
|[CDaoRecordset::GetType](#gettype)|呼叫以判斷資料錄集類型： 資料表類型、 動態類型或快照集類型。|  
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|傳回`CString`包含會驗證資料，因為它輸入欄位的值。|  
|[CDaoRecordset::GetValidationText](#getvalidationtext)|擷取時，不符合驗證規則會顯示的文字。|  
|[CDaoRecordset::IsBOF](#isbof)|傳回非零，如果已在第一個資料錄之前維持資料錄集。 沒有目前記錄。|  
|[CDaoRecordset::IsDeleted](#isdeleted)|傳回非零，如果資料錄集位於已刪除的記錄。|  
|[CDaoRecordset::IsEOF](#iseof)|傳回非零，如果已位置之後的最後一筆記錄的資料錄集。 沒有目前記錄。|  
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|傳回非零，如果目前的記錄中指定的欄位已變更。|  
|[CDaoRecordset::IsFieldNull](#isfieldnull)|傳回非零，如果目前的記錄中的指定的欄位為 Null （具有沒有值）。|  
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|傳回非零，如果目前的記錄中指定的欄位可以設定為 Null （具有沒有值）。|  
|[CDaoRecordset::IsOpen](#isopen)|傳回非零，如果[開啟](#open)先前已經呼叫。|  
|[CDaoRecordset::Move](#move)|從任一方向中目前的記錄，到指定的記錄數目定位資料錄集。|  
|[CDaoRecordset::MoveFirst](#movefirst)|置於資料錄集中的第一個記錄目前的記錄。|  
|[CDaoRecordset::MoveLast](#movelast)|置於筆資料錄集中目前的記錄。|  
|[CDaoRecordset::MoveNext](#movenext)|置於資料錄集的下一個記錄目前的記錄。|  
|[CDaoRecordset::MovePrev](#moveprev)|置於資料錄集中的上一個記錄目前的記錄。|  
|[Cdaorecordset:: Open](#open)|從資料表、 動態集或快照集建立新的資料錄集。|  
|[CDaoRecordset::Requery](#requery)|會執行一次重新整理選取的資料錄的資料錄集的查詢。|  
|[CDaoRecordset::Seek](#seek)|尋找符合指定之準則的目前索引和記錄的目前記錄的可索引的資料表類型的資料錄集物件中的記錄。|  
|[CDaoRecordset::SetAbsolutePosition](#setabsoluteposition)|設定資料錄集物件的目前記錄的記錄數目。|  
|[CDaoRecordset::SetBookmark](#setbookmark)|資料錄集置於包含指定的書籤的記錄。|  
|[CDaoRecordset::SetCacheSize](#setcachesize)|設定值，包含要在本機快取從 ODBC 資料來源之資料的動態類型資料錄集中指定的記錄數目。|  
|[CDaoRecordset::SetCacheStart](#setcachestart)|設定值，指定要快取資料錄集中的第一筆記錄的書籤。|  
|[CDaoRecordset::SetCurrentIndex](#setcurrentindex)|設定索引的資料表類型的資料錄集上呼叫。|  
|[CDaoRecordset::SetFieldDirty](#setfielddirty)|將目前的記錄中指定的欄位標示為已變更。|  
|[CDaoRecordset::SetFieldNull](#setfieldnull)|設定指定之欄位的值為 Null （具有沒有值） 是目前記錄中。|  
|[CDaoRecordset::SetFieldValue](#setfieldvalue)|資料錄集中設定欄位的值。|  
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|設定為 Null 的資料錄集欄位的值。 （具有沒有值）。|  
|[CDaoRecordset::SetLockingMode](#setlockingmode)|設定值，指出將放入效果，在編輯期間鎖定的類型。|  
|[CDaoRecordset::SetParamValue](#setparamvalue)|設定儲存在基礎 DAOParameter 物件中的指定參數的目前值|  
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|設定指定之參數的目前值為 Null （具有沒有值）。|  
|[CDaoRecordset::SetPercentPosition](#setpercentposition)|將目前記錄的位置設定為對應至資料錄集中的記錄總數的百分比表示的位置。|  
|[CDaoRecordset::Update](#update)|完成`AddNew`或**編輯**藉由將新的或編輯資料儲存在資料來源上的作業。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[M_bcheckcachefordirtyfields](#m_bcheckcachefordirtyfields)|包含旗標，指出是否欄位會自動標示為已變更。|  
|[CDaoRecordset::m_nFields](#m_nfields)|包含資料錄集類別中的欄位資料成員的數目和資料來源的資料錄集選取資料行數目。|  
|[CDaoRecordset::m_nParams](#m_nparams)|包含資料錄集類別中的參數資料成員的數目，與資料錄集的查詢傳遞的參數數目|  
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|基礎資料錄集物件 DAO 介面的指標。|  
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|此結果集的來源資料庫。 包含的指標[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件。|  
|[CDaoRecordset::m_strFilter](#m_strfilter)|包含字串，用來建構 SQL**其中**陳述式。|  
|[CDaoRecordset::m_strSort](#m_strsort)|包含字串，用來建構 SQL **ORDER BY**陳述式。|  
  
## <a name="remarks"></a>備註  
 又稱為 「 資料錄集 」`CDaoRecordset`物件都在下列三種形式：  
  
-   資料表類型的資料錄集代表基底資料表可用來檢查、 新增、 變更或刪除單一資料庫資料表中的記錄。  
  
-   動態類型的資料錄集是可以有可更新的記錄查詢的結果。 這些資料錄集是一組可用來檢查、 新增、 變更或從基礎資料庫資料表或資料表刪除記錄的記錄。 動態類型的資料錄集可包含從資料庫中的一個或多個資料表的欄位。  
  
-   快照集類型的資料錄集是一組可用來尋找資料，或產生報表記錄的靜態複本。 這些資料錄集可包含從資料庫中的一個或多個資料表的欄位，但無法更新。  
  
 資料錄集的每個表單代表一組固定在開啟資料錄集時的記錄。 當您捲動資料錄集類型的資料表或動態類型的資料錄集內的記錄時，它會反映記錄之後開啟資料錄集時，其他使用者或應用程式中的其他資料錄集所做的變更。 （無法更新快照集類型的資料錄集）。您可以使用`CDaoRecordset`直接或衍生的應用程式特定資料錄集類別，從`CDaoRecordset`。 您可以：  
  
-   捲動記錄。  
  
-   設定索引，並使用記錄快速尋找[搜尋](#seek)（資料表類型的資料錄集只）。  
  
-   尋找字串比較為基礎的記錄:"<"，"\<="，"="、"> ="，或">"（動態類型和快照集類型的資料錄集）。  
  
-   更新的記錄，並指定 （除了快照集類型的資料錄集） 的鎖定模式。  
  
-   篩選資料錄集來限制它會從選取的可用資料來源的記錄。  
  
-   排序資料錄集。  
  
-   參數化資料錄集，直到執行階段不知道的資訊來自訂其選項。  
  
 類別`CDaoRecordset`提供類似的類別介面`CRecordset`。 主要差異是該類別`CDaoRecordset`透過資料存取物件 (DAO) 為基礎 OLE 存取資料。 類別`CRecordset`DBMS 透過開放式資料庫連接 (ODBC) 和 ODBC 驅動程式存取該 DBMS。  
  
> [!NOTE]
>  DAO 資料庫類別是不同的基礎上開放式資料庫連接 (ODBC) 之 MFC 資料庫類別。 所有的 DAO 資料庫類別名稱有"CDao"前置詞。 您仍然可以使用 DAO 類別; 存取 ODBC 資料來源因為它們是 Microsoft Jet 資料庫引擎的特定 DAO 類別通常會提供更好的功能。  
  
 您可以使用`CDaoRecordset`直接或衍生自`CDaoRecordset`。 若要使用資料錄集類別在任一情況下，開啟資料庫，並建構資料錄集物件，傳遞建構函式的指標，您`CDaoDatabase`物件。 您也可以建構`CDaoRecordset`物件，並可讓 MFC 建立暫存`CDaoDatabase`為您的物件。 然後呼叫資料錄集的[開啟](#open)成員函式，指定物件是否為資料表類型的資料錄集、 動態類型的資料錄集或快照集類型的資料錄集。 呼叫**開啟**選取資料庫中的資料，並擷取第一筆記錄。  
  
 使用物件的成員函式和資料成員來捲動記錄，並在其上運作。 可用的作業取決於物件是資料表類型的資料錄集、 動態類型的資料錄集或快照集類型的資料錄集，以及它是否可更新或唯讀狀態，這取決於資料庫或開放式資料庫連接 (ODBC) 的功能資料來源。 若要重新整理記錄，可能會變更或加入之後**開啟**呼叫，呼叫物件的[Requery](#requery)成員函式。 呼叫物件的**關閉**成員函式，並終結物件，當您完成使用它。  
  
 `CDaoRecordset` 透過型別安全的 c + + 成員使用，以支援讀取和更新記錄欄位的 DAO 資料錄欄位交換 (DFX) 您`CDaoRecordset`或`CDaoRecordset`-衍生的類別。 您也可以實作在資料庫中的資料行的動態繫結，而不使用 DFX 機制使用[GetFieldValue](#getfieldvalue)和[SetFieldValue](#setfieldvalue)。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 資料錄集物件 」。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoRecordset`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdao.h  
  
##  <a name="addnew"></a>  CDaoRecordset::AddNew  
 呼叫此成員函式，將新記錄新增至類型的資料表或動態類型的資料錄集。  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>備註  
 記錄的欄位是一開始為 Null。 (在資料庫詞彙中，Null 表示不擁有任何值 」，而且不是相同**NULL** c + + 中。)若要完成此作業，您必須呼叫[更新](#update)成員函式。 **更新**將您的變更儲存至資料來源。  
  
> [!CAUTION]
>  如果您編輯記錄，然後捲動至另一筆記錄，而不會呼叫**更新**，您的變更都會遺失，而不發出警告。  
  
 如果您將記錄加入動態類型的資料錄集藉由呼叫[AddNew](#addnew)，記錄會顯示在資料錄集並包含基礎的資料表，其中會變得可見的任何新的`CDaoRecordset`物件。  
  
 新的記錄的位置取決於資料錄集的類型：  
  
-   動態類型中不保證資料錄集，插入新記錄的位置。 變更與 Microsoft Jet 3.0 的效能和並行存取原因而發生此行為。 如果您的目標是要使新加入的記錄目前的記錄時，取得上次修改記錄的書籤，並移至該書籤：  
  
 [!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]  
  
-   資料表類型的資料錄集到指定的索引，其適當的位置，在排序次序中，會傳回記錄。 如果尚未指定任何索引，會傳回新的記錄結尾的資料錄集。  
  
 目前在使用之前的記錄`AddNew`保持最新。 如果您想要使新的記錄的目前資料錄集支援書籤，呼叫[SetBookmark](#setbookmark)到 [LastModified] 屬性設定的基本的 DAO 資料錄集物件所識別的書籤。 這樣做很有用來判斷加入一筆記錄中的計數器 （自動遞增） 欄位的值。 如需詳細資訊，請參閱[GetLastModifiedBookmark](#getlastmodifiedbookmark)。  
  
 如果資料庫支援交易，您可以讓您`AddNew`呼叫交易的一部分。 如需有關交易的詳細資訊，請參閱類別[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)。 請注意，您應該呼叫[CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans)之前先呼叫`AddNew`。  
  
 不合法呼叫`AddNew`資料錄集其[開啟](#open)尚未呼叫成員函式。 A`CDaoException`如果您呼叫會擲回`AddNew`以無法附加資料錄集。 您可以判斷資料錄集是否可更新，藉由呼叫[CanAppend](#canappend)。  
  
 Framework 標記變更欄位資料成員，以確保它們將寫入至資料來源上記錄的 DAO 資料錄欄位交換 (DFX) 機制。 一般來說，變更欄位的值欄位已變更都會自動設定，因此您很少需要呼叫[SetFieldDirty](#setfielddirty)自己，不過您有時可能會想要確認資料行就是明確更新或插入無論哪些值是將欄位資料成員中。 DFX 機制也會採用使用**虛擬 NULL**。 如需詳細資訊，請參閱[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
 如果未使用的雙重緩衝機制，然後將變更欄位的值不會自動設定欄位已變更。 在此情況下，它必須明確設定的欄位已變更。 中所包含的旗標[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制這項自動欄位檢查。  
  
> [!NOTE]
>  如果雙重緩衝的記錄 （也就是欄位自動檢查已啟用），呼叫`CancelUpdate`之前的值將會還原成員變數`AddNew`或**編輯**呼叫。  
  
 如需相關資訊，請參閱主題 < AddNew 方法 >、 < CancelUpdate 方法 」、 「 LastModified 屬性 」 和 DAO [說明] 中的 「 EditMode 屬性 」。  
  
##  <a name="canappend"></a>  CDaoRecordset::CanAppend  
 呼叫此成員函式，以判斷是否有先前開啟的資料錄集允許您新增新的記錄，藉由呼叫[AddNew](#addnew)成員函式。  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果資料錄集允許加入新的記錄。否則便是 0。 `CanAppend` 如果您開啟為唯讀資料錄集時，就會傳回 0。  
  
### <a name="remarks"></a>備註  
 如需相關資訊，請參閱主題 < 附加方法 >，DAO [說明] 中。  
  
##  <a name="canbookmark"></a>  CDaoRecordset::CanBookmark  
 呼叫此成員函式，以判斷是否有先前開啟的資料錄集允許您將個別標記記錄使用書籤。  
  
```  
BOOL CanBookmark();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果資料錄集支援書籤，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您使用 Microsoft Jet 資料庫引擎資料表完全為基礎的資料錄集時，可以使用書籤以外上標示為順向捲動資料錄集的快照集型別資料錄集。 其他資料庫產品 （外部的 ODBC 資料來源） 可能不支援書籤。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 < Bookmarkable 屬性 >。  
  
##  <a name="cancelupdate"></a>  CDaoRecordset::CancelUpdate  
 `CancelUpdate`成員函式會取消任何暫止的更新，因為[編輯](#edit)或[AddNew](#addnew)作業。  
  
```  
virtual void CancelUpdate();
```  
  
### <a name="remarks"></a>備註  
 例如，如果應用程式呼叫**編輯**或`AddNew`成員函式，而且不具有稱為[更新](#update)，`CancelUpdate`取消之後所做的任何變更**編輯**或`AddNew`呼叫。  
  
> [!NOTE]
>  如果雙重緩衝的記錄 （也就是欄位自動檢查已啟用），呼叫`CancelUpdate`之前的值將會還原成員變數`AddNew`或**編輯**呼叫。  
  
 如果沒有任何**編輯**或`AddNew`作業暫止、`CancelUpdate`導致 MFC 擲回例外狀況。 呼叫[GetEditMode](#geteditmode)成員函式來判斷是否可以取消暫止作業。  
  
 如需相關資訊，請參閱主題 < CancelUpdate 方法 >，DAO [說明] 中。  
  
##  <a name="canrestart"></a>  CDaoRecordset::CanRestart  
 呼叫此成員函式，以判斷資料錄集是否允許重新啟動其查詢 （若要更新其記錄），藉由呼叫**Requery**成員函式。  
  
```  
BOOL CanRestart();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果**Requery**可以呼叫來執行資料錄集的查詢，一次，否則為 0。  
  
### <a name="remarks"></a>備註  
 不支援類型的資料表資料錄集**Requery**。  
  
 如果**Requery**是不受支援，呼叫[關閉](#close)然後[開啟](#open)重新整理資料。 您可以呼叫**Requery**來更新資料錄集物件的基礎參數查詢之後已變更的參數值。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 可重新啟動屬性 」。  
  
##  <a name="canscroll"></a>  CDaoRecordset::CanScroll  
 呼叫此成員函式，以判斷是否允許捲動資料錄集。  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果您可以捲動資料錄，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您呼叫[開啟](#open)與**dbForwardOnly**，只可以向前捲動資料錄集。  
  
 如需相關資訊，請參閱主題"定位目前記錄指標使用 DAO"DAO [說明] 中。  
  
##  <a name="cantransact"></a>  CDaoRecordset::CanTransact  
 呼叫此成員函式，以判斷資料錄集是否允許交易。  
  
```  
BOOL CanTransact();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果基礎資料來源支援交易，否則為 0。  
  
### <a name="remarks"></a>備註  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 交易屬性 」。  
  
##  <a name="canupdate"></a>  CDaoRecordset::CanUpdate  
 呼叫此成員函式可判斷是否可以更新資料錄集。  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果可以更新資料錄集 （新增、 更新和刪除記錄），否則為 0。  
  
### <a name="remarks"></a>備註  
 資料錄集可能會處於唯讀模式，如果基礎資料來源是唯讀的或者如果指定**dbReadOnly**如`nOptions`呼叫時[開啟](#open)資料錄集。  
  
 如需相關資訊，請參閱主題 < AddNew 方法 >、 < 編輯方法 >、 < 刪除方法 >、 < 更新方法 > 和 DAO [說明] 中的 「 可更新屬性 」。  
  
##  <a name="cdaorecordset"></a>  CDaoRecordset::CDaoRecordset  
 建構 `CDaoRecordset` 物件。  
  
```  
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pDatabase`  
 包含的指標[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件或值**NULL**。 如果沒有**NULL**和`CDaoDatabase`物件的**開啟**尚未呼叫成員函式將它連接到資料來源，資料錄集會嘗試為您開啟自己期間[開啟](#open)呼叫。 如果您要傳入**NULL**、`CDaoDatabase`物件已建構和使用您指定如果您衍生您的資料錄集類別，從資料來源資訊為您連接`CDaoRecordset`。  
  
### <a name="remarks"></a>備註  
 您可以使用`CDaoRecordset`直接或衍生的特定應用程式類別，從`CDaoRecordset`。 您可以使用類別來衍生資料錄集類別。  
  
> [!NOTE]
>  如果您衍生`CDaoRecordset`類別，衍生類別必須提供自己的建構函式。 在衍生類別的建構函式，呼叫建構函式`CDaoRecordset::CDaoRecordset`，傳遞給它來沿著適當的參數。  
  
 傳遞**NULL**到您的資料錄集建構函式有`CDaoDatabase`物件建構，並為您自動連接。 這是不需要的建構，並連接的有用捷徑`CDaoDatabase`之前建構資料錄集物件。 如果`CDaoDatabase`物件未開啟， [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)也會為您使用的預設工作區建立物件。 如需詳細資訊，請參閱[CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase)。  
  
##  <a name="close"></a>  CDaoRecordset::Close  
 關閉`CDaoRecordset`物件它從集合中移除的開啟資料錄集相關聯的資料庫中。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 因為**關閉**將不會終結`CDaoRecordset`物件，您可以藉由呼叫重複使用物件**開啟**在相同的資料來源或不同的資料來源。  
  
 所有暫止[AddNew](#addnew)或[編輯](#edit)取消陳述式之後，並且所有暫止的交易會回復。 如果您想要保留暫止的加入或編輯版本，呼叫[更新](#update)之前先呼叫**關閉**以每個資料錄集。  
  
 您可以呼叫**開啟**呼叫之後，再次**關閉**。 這可讓您重複使用資料錄集物件。 較佳替代方式是呼叫[Requery](#requery)如果可能。  
  
 如需相關資訊，請參閱主題 < 關閉方法 >，DAO [說明] 中。  
  
##  <a name="delete"></a>  CDaoRecordset::Delete  
 呼叫此成員函式來刪除目前開啟的動態類型或類型的資料表資料錄集物件中的記錄。  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>備註  
 之後成功刪除資料錄集的欄位資料成員都會設定為 Null 值，而您必須明確呼叫其中一個資料錄集瀏覽成員函式 ([移動](#move)，[搜尋](#seek)， [SetBookmark](#setbookmark)，依此類推) 才能移出已刪除的記錄。 當您刪除的記錄從資料錄集時，必須有目前的記錄資料錄集中才能呼叫**刪除**; 否則 MFC 會擲回的例外狀況。  
  
 **刪除**移除目前的記錄，並使其無法存取。 雖然您無法編輯，或使用已刪除的記錄，則仍會保持目前。 一旦您移到另一筆記錄，不過，您不能刪除的記錄目前一次。  
  
> [!CAUTION]
>  資料錄集必須是可更新而且必須有有效的記錄資料錄集中目前當您呼叫**刪除**。 例如，如果您刪除記錄，但不是會捲動到新的記錄才能呼叫**刪除**同樣地，**刪除**會擲回[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
 如果您使用交易，而呼叫，您可以取消刪除記錄[CDaoWorkspace::Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback)成員函式。 如果基底資料表主資料表中串聯刪除關聯性，刪除目前的記錄可能也會刪除外部索引資料表中的一個或多個記錄。 如需詳細資訊，請參閱 DAO 說明定義 」 串聯刪除 」。  
  
 不同於`AddNew`和**編輯**，呼叫**刪除**後面沒有接呼叫**更新**。  
  
 如需相關資訊，請參閱主題 < AddNew 方法 >、 < 編輯方法 >、 < 刪除方法 >、 < 更新方法 > 和 DAO [說明] 中的 「 可更新屬性 」。  
  
##  <a name="dofieldexchange"></a>  CDaoRecordset::DoFieldExchange  
 架構會呼叫此成員函式，來自動交換的資料錄集物件的欄位資料成員和對應的資料行的資料來源上目前的記錄之間的資料。  
  
```  
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 包含的指標`CDaoFieldExchange`物件。 架構會有設定好這個物件來指定欄位的交換作業的內容。  
  
### <a name="remarks"></a>備註  
 它也會繫結參數資料成員，如果有的話，資料錄集的選取範圍的 SQL 陳述式字串中參數預留位置。 交換欄位資料，呼叫 DAO 資料錄欄位交換 (DFX)，適用於雙向： 從資料錄集物件的欄位資料成員的資料來源上的記錄欄位和資料來源的資料錄集物件上的記錄。 如果您要動態地繫結資料行，您不需要實作`DoFieldExchange`。  
  
 唯一的動作，您通常必須採取來實作`DoFieldExchange`為您衍生的資料錄集類別是使用 ClassWizard 建立類別，並指定欄位資料成員的名稱和資料型別。 您也可以加入程式碼 ClassWizard 寫入指定的參數資料成員。 如果所有欄位都是動態繫結，此函式將會在非使用中，除非您指定的參數資料成員。  
  
 當您宣告 ClassWizard 類別衍生的資料錄集時，精靈會撰寫的覆寫`DoFieldExchange`，這會類似下列範例：  
  
 [!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]  
  
##  <a name="edit"></a>  CDaoRecordset::Edit  
 呼叫此成員函式，以允許變更目前的記錄。  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>備註  
 一旦呼叫**編輯**成員函式，目前的記錄欄位所做的變更會複製到複製緩衝區。 您對記錄所需的變更之後，請呼叫**更新**以儲存變更。 **編輯**儲存資料錄集的資料成員的值。 如果您呼叫**編輯**，進行變更，然後呼叫**編輯**同樣地，記錄的值就會還原至原本在第一個**編輯**呼叫。  
  
> [!CAUTION]
>  如果您編輯記錄，然後再執行任何作業，會移至另一筆記錄，而不會第一個呼叫**更新**，您的變更都會遺失，而不發出警告。 此外，如果您關閉資料錄集或父資料庫，則會捨棄您已編輯的記錄而不發出警告。  
  
 在某些情況下，您可能想要更新的資料行，讓您為 Null （包含任何資料）。 若要這樣做，請呼叫`SetFieldNull`和參數**TRUE**標示欄位為 Null; 這也會導致要更新的資料行。 如果您要寫入至資料來源，即使其值未經變更，請呼叫欄位`SetFieldDirty`和參數**TRUE**。 就算欄位具有 Null 值。  
  
 Framework 標記變更欄位資料成員，以確保它們將寫入至資料來源上記錄的 DAO 資料錄欄位交換 (DFX) 機制。 一般來說，變更欄位的值欄位已變更都會自動設定，因此您很少需要呼叫[SetFieldDirty](#setfielddirty)自己，不過您有時可能會想要確認資料行就是明確更新或插入無論哪些值是將欄位資料成員中。 DFX 機制也會採用使用**虛擬 NULL**。 如需詳細資訊，請參閱[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
 如果未使用的雙重緩衝機制，然後將變更欄位的值不會自動設定欄位已變更。 在此情況下，它必須明確設定的欄位已變更。 中所包含的旗標[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制這項自動欄位檢查。  
  
 當在多使用者環境中要以保守模式鎖定資料錄集物件時，記錄就會保持鎖定的時間**編輯**更新已完成之前使用。 如果樂觀地鎖定資料錄集時，記錄會鎖定及更新至資料庫之前，相較於編輯前記錄。 如果記錄已變更，因為您呼叫**編輯**、**更新**作業將會失敗，MFC 會擲回例外狀況。 您可以變更鎖定模式與`SetLockingMode`。  
  
> [!NOTE]
>  外部資料庫格式，例如 ODBC 和可安裝的 ISAM 一定會用於開放式鎖定。  
  
 目前的記錄會保留目前之後呼叫**編輯**。 若要呼叫**編輯**，必須是目前的記錄。 如果沒有目前的記錄或資料錄集未參考到開啟的資料表類型或動態類型資料錄集物件，就會發生例外狀況。 呼叫**編輯**導致`CDaoException`在下列情況下擲回：  
  
-   沒有目前記錄。  
  
-   資料錄集的資料庫是唯讀的。  
  
-   記錄中的任何欄位不進行更新。  
  
-   資料錄集的資料庫已由其他使用者開啟專用。  
  
-   另一位使用者已鎖定包含您的記錄的頁面。  
  
 如果資料來源支援交易，您可以進行**編輯**呼叫交易的一部分。 請注意，您應該呼叫`CDaoWorkspace::BeginTrans`之前先呼叫**編輯**及開啟資料錄集之後。 也請注意，呼叫`CDaoWorkspace::CommitTrans`並非用於呼叫的替代做法**更新**完成**編輯**作業。 如需有關交易的詳細資訊，請參閱類別`CDaoWorkspace`。  
  
 如需相關資訊，請參閱主題 < AddNew 方法 >、 < 編輯方法 >、 < 刪除方法 >、 < 更新方法 > 和 DAO [說明] 中的 「 可更新屬性 」。  
  
##  <a name="fillcache"></a>  CDaoRecordset::FillCache  
 呼叫此成員函式可快取指定的資料錄集的記錄數目。  
  
```  
void FillCache(
    long* pSize = NULL,  
    COleVariant* pBookmark = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pSize`  
 指定要填滿快取中的資料列數目。 如果您省略這個參數時，值會取決於基礎的 DAO 物件的 CacheSize 屬性設定。  
  
 `pBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md)指定書籤。 快取填滿此書籤所指定的記錄從開始。 如果您省略這個參數時，會自動填入從 CacheStart 屬性之基礎的 DAO 物件所指定的記錄開始快取。  
  
### <a name="remarks"></a>備註  
 快取改善擷取，或會提取資料，從遠端伺服器的應用程式的效能。 快取中保存最近假設，資料將可能會要求一次執行應用程式時從伺服器擷取資料的本機記憶體是空間。 當要求資料時，Microsoft Jet 資料庫引擎的快取資料會先檢查而不是擷取從伺服器中，花費的時間。 使用非 ODBC 資料來源上的快取的資料沒有任何作用，因為資料不會儲存在快取。  
  
 而非等待它們提取填滿記錄快取，您可以明確地填入快取隨時藉由呼叫`FillCache`成員函式。 這是更快的方法，以填滿快取，因為`FillCache`提取多個資料錄一次而非一次。 例如，顯示每個藥記錄的時，您可以讓應用程式呼叫`FillCache`擷取記錄的下一步的細分。  
  
 使用資料錄集物件存取的任何 ODBC 資料庫可以有本機快取。 若要建立快取，從遠端資料來源中，開啟資料錄集物件，然後呼叫`SetCacheSize`和`SetCacheStart`資料錄集的成員函式。 如果`lSize`和*lBookmark*建立一個範圍超出所指定的範圍中的部分或全部`SetCacheSize`和`SetCacheStart`，在這個範圍之外的資料錄集的部分會被忽略，且不會載入至快取。 如果`FillCache`要求比詳細的記錄會保留在遠端資料來源、 提取其餘的記錄，並擲回任何例外狀況。  
  
 從快取中的記錄不會反映其他使用者同時進行的來源資料的變更。  
  
 `FillCache` 會擷取尚未快取的記錄。 若要強制更新的所有快取的資料，呼叫`SetCacheSize`成員函式`lSize`參數等於 0，呼叫`SetCacheSize`再次`lSize`參數等於快取大小您原先要求，，然後再呼叫`FillCache`.  
  
 如需相關資訊，請參閱主題 < FillCache 方法 >，DAO [說明] 中。  
  
##  <a name="find"></a>  CDaoRecordset::Find  
 呼叫此成員函式，來尋找特定的字串中使用比較運算子的動態集或快照集型別資料錄集。  
  
```  
virtual BOOL Find(
    long lFindType,  
    LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>參數  
 *lFindType*  
 值，指出所需的尋找作業的類型。 可能值為：  
  
- **AFX_DAO_NEXT**尋找下一個位置的比對的字串。  
  
- **AFX_DAO_PREV**尋找上一個比對字串的位置。  
  
- **AFX_DAO_FIRST**尋找比對字串的第一個位置。  
  
- **AFX_DAO_LAST**尋找比對字串的最後一個位置。  
  
 `lpszFilter`  
 字串運算式 (例如**其中**子句中的 SQL 陳述式，但沒有字**其中**) 用來尋找資料錄。 例如:   
  
 [!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]  
  
### <a name="return-value"></a>傳回值  
 非零，如果相符記錄找到，否則為 0。  
  
### <a name="remarks"></a>備註  
 您可以找到第一個下, 一步，字串的上一個或最後一個執行個體。 **尋找**是虛擬函式，因此您可以覆寫它，並新增您自己的實作。 `FindFirst`， `FindLast`， `FindNext`，和`FindPrev`成員函式呼叫**尋找**成員函式，因此您可以使用**尋找**控制所有尋找作業的行為.  
  
 若要尋找記錄中的資料表類型的資料錄集，請呼叫[搜尋](#seek)成員函式。  
  
> [!TIP]
>  小一組記錄，更有效**尋找**會。 一般而言，而且特別是在 ODBC 資料，最好是建立新的查詢來擷取您要的記錄。  
  
 如需相關資訊，請參閱本主題"FindFirst，FindLast，FindNext，FindPrevious 方法 」 DAO 說明。  
  
##  <a name="findfirst"></a>  CDaoRecordset::FindFirst  
 呼叫此成員函式可尋找符合指定的條件的第一個記錄。  
  
```  
BOOL FindFirst(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>參數  
 `lpszFilter`  
 字串運算式 (例如**其中**子句中的 SQL 陳述式，但沒有字**其中**) 用來尋找資料錄。  
  
### <a name="return-value"></a>傳回值  
 非零，如果相符記錄找到，否則為 0。  
  
### <a name="remarks"></a>備註  
 `FindFirst`成員函式開始搜尋的起點的資料錄集，並搜尋至資料錄集的結尾。  
  
 如果您想要包含所有您的搜尋 （不只是那些符合特定條件） 中的記錄所使用的是其中一個移動作業來移動記錄記錄。 若要尋找記錄中的資料表類型的資料錄集，請呼叫`Seek`成員函式。  
  
 如果沒有找到符合準則的記錄，則是不明，目前的記錄指標和`FindFirst`傳回零。 如果資料錄集包含多個符合準則的記錄`FindFirst`找出第一個，`FindNext`找出下一個項目，依此類推。  
  
> [!CAUTION]
>  如果您編輯目前的記錄，請務必將變更儲存藉由呼叫**更新**成員函式，然後才能移到另一筆記錄。 如果您未將移至另一筆記錄更新，您變更都會遺失而不發出警告。  
  
 **尋找**成員函式搜尋從位置，並在下表中指定的方向：  
  
|尋找作業|開始|搜尋方向|  
|---------------------|-----------|----------------------|  
|`FindFirst`|資料錄集的開頭|資料錄集的結尾|  
|`FindLast`|資料錄集的結尾|資料錄集的開頭|  
|`FindNext`|目前的記錄|資料錄集的結尾|  
|**FindPrevious**|目前的記錄|資料錄集的開頭|  
  
> [!NOTE]
>  當您呼叫`FindLast`，Microsoft Jet 資料庫引擎完整填入資料錄集之前從搜尋中，如果這不已經完成。 第一次搜尋可能會超過後續的搜尋。  
  
 使用其中一種尋找作業不是呼叫相同**MoveFirst**或`MoveNext`，不過，這只是讓第一個或下一個記錄目前未指定條件。 您可以遵循移動作業的尋找作業。  
  
 使用 尋找作業時，請記住下列：  
  
-   如果**尋找**傳回非零，未定義目前的記錄。 在此情況下，您必須將目前的記錄指標，回到有效的記錄。  
  
-   您不能使用順向捲動快照集類型的資料錄集的尋找作業。  
  
-   您應該使用美國日期格式 （月-日-年） 當您搜尋欄位包含日期，即使您不想要使用 Microsoft Jet 資料庫引擎的美國版本否則，相符的記錄可能不到。  
  
-   當使用 ODBC 資料庫和大型動態集，您可能會發現使用尋找作業是降低，尤其是使用大型的資料錄集。 您可以使用 SQL 查詢，以改善效能與自訂**ORDERBY**或**其中**子句、 參數查詢或**CDaoQuerydef**擷取特定的物件索引的記錄。  
  
 如需相關資訊，請參閱本主題"FindFirst，FindLast，FindNext，FindPrevious 方法 」 DAO 說明。  
  
##  <a name="findlast"></a>  CDaoRecordset::FindLast  
 呼叫此成員函式可尋找符合指定的條件的最後一個記錄。  
  
```  
BOOL FindLast(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>參數  
 `lpszFilter`  
 字串運算式 (例如**其中**子句中的 SQL 陳述式，但沒有字**其中**) 用來尋找資料錄。  
  
### <a name="return-value"></a>傳回值  
 非零，如果相符記錄找到，否則為 0。  
  
### <a name="remarks"></a>備註  
 `FindLast`成員函式開始在資料錄集結尾搜尋以及向資料錄集的起始處，向後搜尋。  
  
 如果您想要包含所有您的搜尋 （不只是那些符合特定條件） 中的記錄所使用的是其中一個移動作業來移動記錄記錄。 若要尋找記錄中的資料表類型的資料錄集，請呼叫`Seek`成員函式。  
  
 如果沒有找到符合準則的記錄，則是不明，目前的記錄指標和`FindLast`傳回零。 如果資料錄集包含多個符合準則的記錄`FindFirst`找出第一個，`FindNext`找出下一個出現之後第一個出現項目，依此類推。  
  
> [!CAUTION]
>  如果您編輯目前的記錄，請確定您儲存變更，藉由呼叫**更新**成員函式，然後才能移到另一筆記錄。 如果您未將移至另一筆記錄更新，您變更都會遺失而不發出警告。  
  
 使用其中一種尋找作業不是呼叫相同**MoveFirst**或`MoveNext`，不過，這只是讓第一個或下一個記錄目前未指定條件。 您可以遵循移動作業的尋找作業。  
  
 使用 尋找作業時，請記住下列：  
  
-   如果**尋找**傳回非零，未定義目前的記錄。 在此情況下，您必須將目前的記錄指標，回到有效的記錄。  
  
-   您不能使用順向捲動快照集類型的資料錄集的尋找作業。  
  
-   您應該使用美國日期格式 （月-日-年） 當您搜尋欄位包含日期，即使您不想要使用 Microsoft Jet 資料庫引擎的美國版本否則，相符的記錄可能不到。  
  
-   當使用 ODBC 資料庫和大型動態集，您可能會發現使用尋找作業是降低，尤其是使用大型的資料錄集。 您可以使用 SQL 查詢，以改善效能與自訂**ORDERBY**或**其中**子句、 參數查詢或**CDaoQuerydef**擷取特定的物件索引的記錄。  
  
 如需相關資訊，請參閱本主題"FindFirst，FindLast，FindNext，FindPrevious 方法 」 DAO 說明。  
  
##  <a name="findnext"></a>  CDaoRecordset::FindNext  
 呼叫此成員函式可尋找符合指定的條件的下一個記錄。  
  
```  
BOOL FindNext(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>參數  
 `lpszFilter`  
 字串運算式 (例如**其中**子句中的 SQL 陳述式，但沒有字**其中**) 用來尋找資料錄。  
  
### <a name="return-value"></a>傳回值  
 非零，如果相符記錄找到，否則為 0。  
  
### <a name="remarks"></a>備註  
 `FindNext`成員函式開始在目前的記錄搜尋，並搜尋至資料錄集的結尾。  
  
 如果您想要包含所有您的搜尋 （不只是那些符合特定條件） 中的記錄所使用的是其中一個移動作業來移動記錄記錄。 若要尋找記錄中的資料表類型的資料錄集，請呼叫`Seek`成員函式。  
  
 如果沒有找到符合準則的記錄，則是不明，目前的記錄指標和`FindNext`傳回零。 如果資料錄集包含多個符合準則的記錄`FindFirst`找出第一個，`FindNext`找出下一個項目，依此類推。  
  
> [!CAUTION]
>  如果您編輯目前的記錄，請確定您儲存變更，藉由呼叫**更新**成員函式，然後才能移到另一筆記錄。 如果您未將移至另一筆記錄更新，您變更都會遺失而不發出警告。  
  
 使用其中一種尋找作業不是呼叫相同**MoveFirst**或`MoveNext`，不過，這只是讓第一個或下一個記錄目前未指定條件。 您可以遵循移動作業的尋找作業。  
  
 使用 尋找作業時，請記住下列：  
  
-   如果**尋找**傳回非零，未定義目前的記錄。 在此情況下，您必須將目前的記錄指標，回到有效的記錄。  
  
-   您不能使用順向捲動快照集類型的資料錄集的尋找作業。  
  
-   您應該使用美國日期格式 （月-日-年） 當您搜尋欄位包含日期，即使您不想要使用 Microsoft Jet 資料庫引擎的美國版本否則，相符的記錄可能不到。  
  
-   當使用 ODBC 資料庫和大型動態集，您可能會發現使用尋找作業是降低，尤其是使用大型的資料錄集。 您可以使用 SQL 查詢，以改善效能與自訂**ORDERBY**或**其中**子句、 參數查詢或**CDaoQuerydef**擷取特定的物件索引的記錄。  
  
 如需相關資訊，請參閱本主題"FindFirst，FindLast，FindNext，FindPrevious 方法 」 DAO 說明。  
  
##  <a name="findprev"></a>  CDaoRecordset::FindPrev  
 呼叫此成員函式可尋找符合指定的條件的上一個記錄。  
  
```  
BOOL FindPrev(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>參數  
 `lpszFilter`  
 字串運算式 (例如**其中**子句中的 SQL 陳述式，但沒有字**其中**) 用來尋找資料錄。  
  
### <a name="return-value"></a>傳回值  
 非零，如果相符記錄找到，否則為 0。  
  
### <a name="remarks"></a>備註  
 `FindPrev`成員函式開始在目前的記錄搜尋，並向後搜尋向起始處的資料錄集。  
  
 如果您想要包含所有您的搜尋 （不只是那些符合特定條件） 中的記錄所使用的是其中一個移動作業來移動記錄記錄。 若要尋找記錄中的資料表類型的資料錄集，請呼叫`Seek`成員函式。  
  
 如果沒有找到符合準則的記錄，則是不明，目前的記錄指標和`FindPrev`傳回零。 如果資料錄集包含多個符合準則的記錄`FindFirst`找出第一個，`FindNext`找出下一個項目，依此類推。  
  
> [!CAUTION]
>  如果您編輯目前的記錄，請確定您儲存變更，藉由呼叫**更新**成員函式，然後才能移到另一筆記錄。 如果您未將移至另一筆記錄更新，您變更都會遺失而不發出警告。  
  
 使用其中一種尋找作業不是呼叫相同**MoveFirst**或`MoveNext`，不過，這只是讓第一個或下一個記錄目前未指定條件。 您可以遵循移動作業的尋找作業。  
  
 使用 尋找作業時，請記住下列：  
  
-   如果**尋找**傳回非零，未定義目前的記錄。 在此情況下，您必須將目前的記錄指標，回到有效的記錄。  
  
-   您不能使用順向捲動快照集類型的資料錄集的尋找作業。  
  
-   您應該使用美國日期格式 （月-日-年） 當您搜尋欄位包含日期，即使您不想要使用 Microsoft Jet 資料庫引擎的美國版本否則，相符的記錄可能不到。  
  
-   當使用 ODBC 資料庫和大型動態集，您可能會發現使用尋找作業是降低，尤其是使用大型的資料錄集。 您可以使用 SQL 查詢，以改善效能與自訂**ORDERBY**或**其中**子句、 參數查詢或**CDaoQuerydef**擷取特定的物件索引的記錄。  
  
 如需相關資訊，請參閱本主題"FindFirst，FindLast，FindNext，FindPrevious 方法 」 DAO 說明。  
  
##  <a name="getabsoluteposition"></a>  CDaoRecordset::GetAbsolutePosition  
 傳回資料錄集物件的目前記錄的記錄數目。  
  
```  
long GetAbsolutePosition();
```  
  
### <a name="return-value"></a>傳回值  
 從 0 到資料錄集中的記錄數目的整數。 對應至目前的記錄資料錄集中的序數位置。  
  
### <a name="remarks"></a>備註  
 基本的 DAO 物件 AbsolutePosition 屬性值以零為起始。設定為 0，是指資料錄集中的第一個記錄。 您可以判斷資料錄集中填入記錄數目，藉由呼叫[GetRecordCount](#getrecordcount)。 呼叫`GetRecordCount`可能需要一些時間，因為它必須存取所有的記錄，來判斷計數。  
  
 如果沒有目前記錄，做為資料錄集，沒有記錄時，會傳回 1。 如果目前的記錄會被刪除，未定義 AbsolutePosition 屬性值，和 MFC 擲回例外狀況，如果它參考。 動態類型的資料錄集，針對新的記錄會加入至序列的結尾。  
  
> [!NOTE]
>  這個屬性不是要做為 surrogate 資料錄數目。 書籤仍保留並傳回指定位置的建議的方式，而目前的記錄放在所有類型的資料錄集物件的唯一方式。 特別是，指定記錄的位置時，變更會刪除在它前面的記錄。 也沒有指定的記錄會有相同的絕對位置，如果資料錄集時都會重新建立一次資料錄集內的個別記錄的順序不保證除非它以使用 SQL 陳述式建立，因為不保證**ORDERBY**子句。  
  
> [!NOTE]
>  此成員函式無效，僅適用於動態類型和快照集類型的資料錄集。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 < AbsolutePosition 屬性 >。  
  
##  <a name="getbookmark"></a>  CDaoRecordset::GetBookmark  
 呼叫此成員函式，以取得特定的資料記錄中的書籤值。  
  
```  
COleVariant GetBookmark();
```  
  
### <a name="return-value"></a>傳回值  
 傳回值，表示目前資料錄的書籤。  
  
### <a name="remarks"></a>備註  
 當建立或開啟資料錄集物件時，其記錄的每個已經有唯一的書籤支援它們。 呼叫`CanBookmark`來判斷資料錄集是否支援書籤。  
  
 您可以藉由指定的書籤的值儲存目前的資料錄的書籤`COleVariant`物件。 若要快速回到該記錄隨時移動到不同記錄之後，呼叫`SetBookmark`具有參數的值對應`COleVariant`物件。  
  
> [!NOTE]
>  呼叫[Requery](#requery)變更 DAO 書籤。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 書籤屬性 」。  
  
##  <a name="getcachesize"></a>  CDaoRecordset::GetCacheSize  
 呼叫此成員函式可取得的快取的記錄數目。  
  
```  
long GetCacheSize();
```  
  
### <a name="return-value"></a>傳回值  
 值，包含要在本機快取從 ODBC 資料來源之資料的動態類型資料錄集中指定的記錄數目。  
  
### <a name="remarks"></a>備註  
 資料快取可改善應用程式從遠端伺服器，透過動態類型資料錄集物件擷取資料的效能。 快取中保存最近從伺服器擷取的資料將會要求一次在執行應用程式資料的本機記憶體是一個空格。 當要求資料時，Microsoft Jet 資料庫引擎的快取要求的資料會先檢查而不是擷取從伺服器中，花費的時間。 不是來自 ODBC 資料來源的資料不會儲存在快取中。  
  
 任何 ODBC 資料來源，例如附加的資料表，可以在本機快取。  
  
 如需相關資訊，請參閱 DAO 說明主題 「 CacheSize CacheStart 屬性 」。  
  
##  <a name="getcachestart"></a>  CDaoRecordset::GetCacheStart  
 呼叫此成員函式可取得快取資料錄集的第一個記錄的書籤值。  
  
```  
COleVariant GetCacheStart();
```  
  
### <a name="return-value"></a>傳回值  
 A `COleVariant` ，指定要快取資料錄集中的第一筆記錄的書籤。  
  
### <a name="remarks"></a>備註  
 Microsoft Jet 資料庫引擎會從快取中，要求快取範圍內的記錄，它會向伺服器要求快取範圍外的記錄。  
  
> [!NOTE]
>  從快取擷取的記錄不會反映其他使用者同時進行的來源資料的變更。  
  
 如需相關資訊，請參閱 DAO 說明主題 「 CacheSize CacheStart 屬性 」。  
  
##  <a name="getcurrentindex"></a>  CDaoRecordset::GetCurrentIndex  
 呼叫此成員函式，以判斷目前正在使用中索引的資料表類型索引`CDaoRecordset`物件。  
  
```  
CString GetCurrentIndex();
```  
  
### <a name="return-value"></a>傳回值  
 A`CString`包含目前與資料表類型的資料錄集的使用中索引的名稱。 如果已不設定任何索引，則傳回空字串。  
  
### <a name="remarks"></a>備註  
 此索引是資料表類型的資料錄集，排序記錄的基礎，而且會由[搜尋](#seek)成員函式來找出記錄。  
  
 A`CDaoRecordset`物件可以有一個以上的索引，但可以一次使用一個索引 (雖然[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)物件可能會有多個定義的索引)。  
  
 如需相關資訊，請參閱本主題 「 索引物件 」，DAO 說明中的 「 目前索引 」 的定義。  
  
##  <a name="getdatecreated"></a>  CDaoRecordset::GetDateCreated  
 呼叫此成員函式可擷取基底資料表的建立的時間和日期。  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>傳回值  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，其中包含的日期和時間建立基底資料表。  
  
### <a name="remarks"></a>備註  
 日期和時間設定被衍生自基底資料表建立所在的電腦。  
  
 如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
##  <a name="getdatelastupdated"></a>  CDaoRecordset::GetDateLastUpdated  
 呼叫此成員函式可擷取的日期和時間，上次更新結構描述。  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>傳回值  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，其中包含的日期和時間，上次更新基底資料表結構 （結構描述）。  
  
### <a name="remarks"></a>備註  
 日期和時間設定被衍生自上次更新的基底資料表結構 （結構描述） 的電腦。  
  
 如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
##  <a name="getdefaultdbname"></a>  CDaoRecordset::GetDefaultDBName  
 呼叫此成員函式，來判斷這個資料錄集之資料庫的名稱。  
  
```  
virtual CString GetDefaultDBName();
```  
  
### <a name="return-value"></a>傳回值  
 A `CString` ，其中包含這個資料錄集衍生之資料庫的名稱與路徑。  
  
### <a name="remarks"></a>備註  
 如果建立資料錄集時，如果指標不[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)，則此路徑會使用資料錄集所開啟的預設資料庫。 根據預設，此函數會傳回空字串。 當 ClassWizard 衍生新的資料錄集，從`CDaoRecordset`，它會為您建立此函式。  
  
 下列範例說明使用雙反斜線 (\\\\) 在字串中，會視需要正確解譯的字串。  
  
 [!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]  
  
##  <a name="getdefaultsql"></a>  CDaoRecordset::GetDefaultSQL  
 架構會呼叫此成員函式，以取得資料錄集所依據的預設 SQL 陳述式。  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>傳回值  
 A `CString` ，其中包含預設的 SQL 陳述式。  
  
### <a name="remarks"></a>備註  
 這可能是資料表名稱或 SQL**選取**陳述式。  
  
 間接定義預設的 SQL 陳述式藉由宣告 ClassWizard，資料錄集類別和 ClassWizard 會為您執行這項工作。  
  
 如果您傳遞 null SQL 字串，以[開啟](#open)，則會呼叫此函數，若要判斷您的資料錄集的資料表名稱或 SQL。  
  
##  <a name="geteditmode"></a>  CDaoRecordset::GetEditMode  
 呼叫此成員函式來判斷狀態的編輯，也就是下列值之一：  
  
```  
short GetEditMode();
```  
  
### <a name="return-value"></a>傳回值  
 傳回值，指出目前的記錄為編輯的狀態。  
  
### <a name="remarks"></a>備註  
  
|值|描述|  
|-----------|-----------------|  
|**dbEditNone**|沒有編輯作業正在進行中。|  
|**dbEditInProgress**|**編輯**已呼叫。|  
|**dbEditAdd**|`AddNew` 已呼叫。|  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 < EditMode 屬性 >。  
  
##  <a name="getfieldcount"></a>  CDaoRecordset::GetFieldCount  
 呼叫此成員函式可擷取的資料錄集中定義的欄位 （資料行） 數目。  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>傳回值  
 資料錄集中的欄位數目。  
  
### <a name="remarks"></a>備註  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 計數屬性 」。  
  
##  <a name="getfieldinfo"></a>  CDaoRecordset::GetFieldInfo  
 呼叫此成員函式可取得有關資料錄集中的欄位。  
  
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
 `nIndex`  
 預先定義的欄位在資料錄集的欄位集合中，查閱索引以零為起始的索引。  
  
 `fieldinfo`  
 若要參考[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。  
  
 `dwInfoOptions`  
 指定的資料錄集擷取的相關資訊的選項。 這裡列出可用的選項以及它們會導致此函數傳回。 為了達到最佳效能，擷取的您所需要資訊層的級：  
  
- `AFX_DAO_PRIMARY_INFO` （預設值）名稱、 類型、 大小屬性  
  
- `AFX_DAO_SECONDARY_INFO` 主要的資訊，加上： 序數位置，所需，允許零長度、 定序順序，外部索引名稱、 來源欄位中，來源資料表  
  
- `AFX_DAO_ALL_INFO` 主要和次要的資訊，加上： 預設值，驗證規則驗證文字  
  
 `lpszName`  
 欄位的名稱。  
  
### <a name="remarks"></a>備註  
 一個版本的函式可讓您依索引查閱欄位。 另一個版本可讓您依名稱查閱欄位。  
  
 如需傳回的資訊的說明，請參閱[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。 此結構具有資訊上面所列的描述中的項目所對應的成員`dwInfoOptions`。 當您要求一個層級的資訊時，您會取得任何先前的層的資訊。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 屬性屬性 」。  
  
##  <a name="getfieldvalue"></a>  CDaoRecordset::GetFieldValue  
 呼叫此成員函式可擷取的資料錄集中的資料。  
  
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
 `lpszName`  
 包含的欄位名稱的字串指標。  
  
 `varValue`  
 若要參考`COleVariant`物件將會儲存欄位的值。  
  
 `nIndex`  
 在資料錄集的欄位集合中，依索引查閱欄位以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 兩個版本`GetFieldValue`的傳回值傳回[COleVariant](../../mfc/reference/colevariant-class.md)物件，其中包含欄位的值。  
  
### <a name="remarks"></a>備註  
 您可以查閱欄位，依名稱或序數位置。  
  
> [!NOTE]
>  它會呼叫其中一個會採用此成員函式版本更有效率`COleVariant`物件參考為參數，而不是呼叫傳回的版本`COleVariant`物件。 此函式的第二個版本會保留回溯相容性。  
  
 使用`GetFieldValue`和[SetFieldValue](#setfieldvalue)以動態方式在執行的階段而不是以靜態方式使用的繫結資料行繫結欄位[DoFieldExchange](#dofieldexchange)機制。  
  
 `GetFieldValue` 和`DoFieldExchange`機制可以進行合併以改善效能。 例如，使用`GetFieldValue`擷取值，您需要只依需求，並指派該呼叫在介面中的 [更多資訊] 5d 按鈕。  
  
 如需相關資訊，請參閱 「 欄位物件 」 和 DAO [說明] 中的 < 值屬性 > 主題。  
  
##  <a name="getindexcount"></a>  CDaoRecordset::GetIndexCount  
 呼叫此成員函式，來判斷資料表類型的資料錄集上可用的索引數目。  
  
```  
short GetIndexCount();
```  
  
### <a name="return-value"></a>傳回值  
 資料表類型的資料錄集中的索引數目。  
  
### <a name="remarks"></a>備註  
 `GetIndexCount` 可用於逐一查看資料錄集中的所有索引。 基於這個目的，使用`GetIndexCount`搭配[GetIndexInfo](#getindexinfo)。 如果您呼叫此成員函式在動態類型或快照集類型的資料錄集時，MFC 會擲回例外狀況。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 屬性屬性 」。  
  
##  <a name="getindexinfo"></a>  CDaoRecordset::GetIndexInfo  
 呼叫此成員函式，以取得各種索引定義基礎資料錄集的基底資料表中相關的資訊。  
  
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
 `nIndex`  
 為數值位置查閱資料表的索引集合中以零為起始的索引。  
  
 `indexinfo`  
 若要參考[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構。  
  
 `dwInfoOptions`  
 指定的索引來擷取的相關資訊的選項。 這裡列出可用的選項以及它們會導致此函數傳回。 為了達到最佳效能，擷取的您所需要資訊層的級：  
  
- `AFX_DAO_PRIMARY_INFO` （預設值）欄位名稱 欄位資訊  
  
- `AFX_DAO_SECONDARY_INFO` 主要的資訊，加上： 主要、 Unique、 叢集、 忽略 Null，有需要，外部  
  
- `AFX_DAO_ALL_INFO` 主要和次要的資訊，加上： 相異計數量  
  
 `lpszName`  
 依名稱查閱索引物件的名稱指標。  
  
### <a name="remarks"></a>備註  
 一個版本的函式可讓您查詢的集合中位置的索引。 另一個版本可讓您依名稱查閱索引。  
  
 如需傳回的資訊的說明，請參閱[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構。 此結構具有資訊上面所列的描述中的項目所對應的成員`dwInfoOptions`。 當您要求一個層級的資訊時，您會取得任何先前的層的資訊。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 屬性屬性 」。  
  
##  <a name="getlastmodifiedbookmark"></a>  CDaoRecordset::GetLastModifiedBookmark  
 呼叫此成員函式可擷取最最近加入或已更新資料錄的書籤。  
  
```  
COleVariant GetLastModifiedBookmark();
```  
  
### <a name="return-value"></a>傳回值  
 A`COleVariant`包含書籤，指出最近新增或變更記錄。  
  
### <a name="remarks"></a>備註  
 當建立或開啟資料錄集物件時，其記錄的每個已經有唯一的書籤支援它們。 呼叫[GetBookmark](#getbookmark)決定資料錄集是否支援書籤。 如果資料錄集不支援書籤、`CDaoException`就會擲回。  
  
 當您新增一筆記錄時，它會出現在資料錄集時，結尾，並不是目前的記錄。 若要讓新的記錄目前，呼叫`GetLastModifiedBookmark`，然後呼叫`SetBookmark`回到新加入的記錄。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 < LastModified 屬性 >。  
  
##  <a name="getlockingmode"></a>  CDaoRecordset::GetLockingMode  
 呼叫此成員函式，來決定鎖定資料錄集的作用中的類型。  
  
```  
BOOL GetLockingMode();
```  
  
### <a name="return-value"></a>傳回值  
 如果鎖定的類型是封閉式，非零，否則為 0，代表開放式記錄鎖定。  
  
### <a name="remarks"></a>備註  
 當您呼叫封閉式鎖定時作用中，包含您要編輯的資料錄的資料頁面鎖定[編輯](#edit)成員函式。 當您呼叫時，已解除鎖定頁面[更新](#update)或[關閉](#close)成員函式或任何移動或尋找作業。  
  
 開放式鎖定是作用中時包含資料錄的資料頁已鎖定以更新記錄時，才**更新**成員函式。  
  
 當使用 ODBC 資料來源，是一律開放式鎖定的模式。  
  
 如需相關資訊，請參閱 「 LockEdits 屬性 」 和 「 鎖定行為在多使用者應用程式 」 DAO [說明] 中的主題。  
  
##  <a name="getname"></a>  CDaoRecordset::GetName  
 呼叫此成員函式可擷取的資料錄集的名稱。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>傳回值  
 A`CString`包含資料錄集的名稱。  
  
### <a name="remarks"></a>備註  
 資料錄集的名稱必須以字母開頭，而且可以包含最多 40 個字元。 它可以包含數字和底線字元，但是不能包含標點符號或空格。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 名稱屬性 」。  
  
##  <a name="getparamvalue"></a>  CDaoRecordset::GetParamValue  
 呼叫此成員函式可擷取目前儲存在基礎 DAOParameter 物件中的指定參數的值。  
  
```  
virtual COleVariant GetParamValue(int nIndex);  
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 數值參數的位置基礎 DAOParameter 物件中。  
  
 `lpszName`  
 您想將其值的參數名稱。  
  
### <a name="return-value"></a>傳回值  
 類別的物件[COleVariant](../../mfc/reference/colevariant-class.md) ，其中包含參數的值。  
  
### <a name="remarks"></a>備註  
 您可以依名稱或集合中其數值位置來存取參數。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 參數物件 」。  
  
##  <a name="getpercentposition"></a>  CDaoRecordset::GetPercentPosition  
 使用動態類型或快照集類型的資料錄集，如果您呼叫時`GetPercentPosition`之前完全填入資料錄集，是相對於存取由呼叫的記錄數目的移動量[GetRecordCount](#getrecordcount).  
  
```  
float GetPercentPosition();
```  
  
### <a name="return-value"></a>傳回值  
 指出目前記錄中的記錄資料錄集的百分比為基礎的資料錄集物件中的概略位置 0 和 100 之間的數字。  
  
### <a name="remarks"></a>備註  
 您可以將移到最後一個記錄藉由呼叫[MoveLast](#movelast)以完整母體擴展的所有資料錄集，但這可能需要很長的時間。  
  
 您可以呼叫`GetPercentPosition`上的資料錄集物件的所有三種類型，包括無索引的資料表。 不過，您不能呼叫`GetPercentPosition`順向捲動快照集，或對外部資料庫的傳遞查詢從開啟的資料錄集。 如果沒有目前的記錄，或已刪除他目前的記錄，`CDaoException`就會擲回。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 < PercentPosition 屬性 >。  
  
##  <a name="getrecordcount"></a>  CDaoRecordset::GetRecordCount  
 呼叫此成員函式，以找出資料錄集中的多少筆記錄被存取。  
  
```  
long GetRecordCount();
```  
  
### <a name="return-value"></a>傳回值  
 傳回資料錄集物件中存取的記錄的數目。  
  
### <a name="remarks"></a>備註  
 `GetRecordCount` 不表示中動態類型或快照集類型的資料錄集所包含的多少筆記錄，直到被存取的所有記錄。 此成員函式呼叫可能需要大量的時間才能完成。  
  
 存取最後一筆記錄後傳回的值會指出未刪除資料錄集中的記錄總數。 若要強制執行存取最後一筆記錄，請呼叫`MoveLast`或`FindLast`資料錄集的成員函式。 您也可以使用 SQL 計數來判斷您的查詢會傳回的記錄的近似數目。  
  
 您的應用程式刪除記錄檔中的動態類型資料錄集，傳回的值為`GetRecordCount`會減少。 不過，其他使用者所刪除的記錄不會反映由`GetRecordCount`直到目前記錄位於已刪除的記錄。 如果您執行的交易，會影響記錄計數和後續回復交易，`GetRecordCount`將不會反映剩餘記錄的實際數目。  
  
 值`GetRecordCount`的基礎資料表中的變更不會影響從快照集類型的資料錄集。  
  
 值`GetRecordCount`資料表類型的資料錄集反映出資料表中記錄的大約數目和新增及刪除資料表會記錄時立即影響。  
  
 沒有記錄的資料錄集傳回值為 0。 使用附加的資料表或 ODBC 資料庫時`GetRecordCount`一定會傳回-1。 呼叫**Requery**資料錄集的成員函式的值重設`GetRecordCount`就如同查詢是重新執行。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 < RecordCount 屬性 >。  
  
##  <a name="getsql"></a>  CDaoRecordset::GetSQL  
 呼叫此成員函式可取得用來選取資料錄集的記錄，當開啟時的 SQL 陳述式。  
  
```  
CString GetSQL() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A `CString` ，其中包含 SQL 陳述式。  
  
### <a name="remarks"></a>備註  
 這通常是 SQL**選取**陳述式。  
  
 所傳回的字串`GetSQL`通常不同於您可能有傳送中資料錄集到的任何字串`lpszSQL`參數[開啟](#open)成員函式。 這是因為資料錄集建構完整的 SQL 陳述式，根據您傳遞給**開啟**ClassWizard，與指定的內容，您可能必須以指定的內容[m_strFilter](#m_strfilter)和[m_strSort](#m_strsort)資料成員。  
  
> [!NOTE]
>  只有在呼叫之後呼叫此成員函式**開啟**。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 SQL 屬性 」。  
  
##  <a name="gettype"></a>  CDaoRecordset::GetType  
 開啟資料錄集來判斷資料錄集物件的型別之後呼叫此成員函式。  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>傳回值  
 下列一個值，指出資料錄集類型：  
  
- **dbOpenTable**資料表類型的資料錄集  
  
- **dbOpenDynaset**動態類型的資料錄集  
  
- **dbOpenSnapshot**快照集類型的資料錄集  
  
### <a name="remarks"></a>備註  
 如需相關資訊，請參閱主題 DAO [說明] 中的 < 型別屬性 >。  
  
##  <a name="getvalidationrule"></a>  CDaoRecordset::GetValidationRule  
 呼叫此成員函式可判斷用來驗證資料的規則。  
  
```  
CString GetValidationRule();
```  
  
### <a name="return-value"></a>傳回值  
 A`CString`物件，其中包含值，會驗證記錄中的資料，因為它已變更或加入至資料表。  
  
### <a name="remarks"></a>備註  
 此規則是以文字為基礎，而且會套用基礎資料表變更每個階段。 如果資料不是合法的 MFC 會擲回例外狀況。 基礎欄位物件，如果指定，驗證文字屬性的文字或文字的基礎欄位物件的驗證規則屬性所指定的運算式傳回的錯誤訊息。 您可以呼叫[GetValidationText](#getvalidationtext)來取得錯誤訊息的文字。  
  
 例如，需要的月份天數的記錄中的欄位可能有的驗證規則例如"天 BETWEEN 1 到 31。 」  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 < 驗證規則屬性 >。  
  
##  <a name="getvalidationtext"></a>  CDaoRecordset::GetValidationText  
 呼叫此成員函式可擷取的文字基礎的欄位物件的驗證屬性。  
  
```  
CString GetValidationText();
```  
  
### <a name="return-value"></a>傳回值  
 A`CString`物件，其中包含訊息時，系統會顯示欄位的值不符合驗證規則之基礎的欄位物件的文字。  
  
### <a name="remarks"></a>備註  
 如需相關資訊，請參閱主題 DAO [說明] 中的 < 驗證文字屬性 >。  
  
##  <a name="isbof"></a>  CDaoRecordset::IsBOF  
 您從資料錄捲動記錄，以了解是否有消失之前的資料錄集的第一個記錄之前，請呼叫此成員函式。  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果資料錄集不包含任何記錄，或有逆向之前第一筆記錄中;否則便是 0。  
  
### <a name="remarks"></a>備註  
 您也可以呼叫`IsBOF`連同`IsEOF`來判斷資料錄集是否包含任何記錄，或為空白。 之後立即呼叫**開啟**，如果資料錄集不包含任何記錄，`IsBOF`傳回非零值。 當您開啟具有至少一個資料錄的資料錄集時，第一筆記錄是目前的記錄和`IsBOF`傳回 0。  
  
 如果第一筆記錄是目前的記錄，而且您呼叫`MovePrev`，`IsBOF`後續會傳回非零值。 如果`IsBOF`傳回非零，而且您呼叫`MovePrev`，擲回例外狀況。 如果`IsBOF`傳回非零，目前的記錄為未定義，並需要目前記錄的任何動作將會導致例外狀況。  
  
 上的特定方法的效果`IsBOF`和`IsEOF`設定：  
  
-   呼叫**開啟**內部讓第一筆記錄中的資料錄集的目前記錄呼叫**MoveFirst**。 因此，呼叫**開啟**記錄原因的空集合上`IsBOF`和`IsEOF`傳回非零值。 (請參閱下表中的失敗行為**MoveFirst**或`MoveLast`呼叫。)  
  
-   所有成功找出一筆記錄的移動作業會造成同時`IsBOF`和`IsEOF`傳回 0。  
  
-   `AddNew`後面接著呼叫**更新**成功插入新記錄的呼叫會導致`IsBOF`傳回 0，但是只有`IsEOF`已經為非零值。 狀態`IsEOF`一定會維持不變。 Microsoft Jet 資料庫引擎所定義，空的資料錄集的目前的記錄指標是檔案的結尾，因此目前的記錄後面插入新的記錄。  
  
-   任何**刪除**呼叫，即使在移除資料錄集，唯一的剩餘記錄不會變更的值`IsBOF`或`IsEOF`。  
  
 下表顯示移動所允許的作業使用的不同組合`IsBOF` /  `IsEOF`。  
  
||MoveFirst、 MoveLast|MovePrev，<br /><br /> 移動 < 0|移動 0|MoveNext，<br /><br /> 移動 > 0|  
|------|-------------------------|-----------------------------|------------|-----------------------------|  
|`IsBOF`= 是非零值，<br /><br /> `IsEOF`=0|Allowed|例外|例外|Allowed|  
|`IsBOF`=0,<br /><br /> `IsEOF`= 為非零，|Allowed|Allowed|例外|例外|  
|兩者都為非零，|例外|例外|例外|例外|  
|這兩個 0|Allowed|Allowed|Allowed|Allowed|  
  
 允許在移動操作並不表示作業將會成功找到某筆記錄。 此外，它只會指出可以嘗試執行指定的移動作業，而且不會產生例外狀況。 值`IsBOF`和`IsEOF`成員函式可能會因為嘗試的移動而變更。  
  
 沒有找到的值為一筆記錄的移動作業的效果`IsBOF`和`IsEOF`設定 下表所示。  
  
||IsBOF|IsEOF|  
|------|-----------|-----------|  
|**MoveFirst**， `MoveLast`|為非零，|為非零，|  
|**移動**0|沒有變更|沒有變更|  
|`MovePrev`**移動**< 0|為非零，|沒有變更|  
|`MoveNext`**移動**> 0|沒有變更|為非零，|  
  
 如需相關資訊，請參閱本主題 「 BOF，EOF 屬性 」 DAO [說明] 中。  
  
##  <a name="isdeleted"></a>  CDaoRecordset::IsDeleted  
 呼叫此成員函式，以判斷是否已刪除目前的記錄。  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果資料錄集位於已刪除的記錄。否則便是 0。  
  
### <a name="remarks"></a>備註  
 當您捲動至記錄和`IsDeleted`傳回**TRUE** （非零），然後您必須捲動至另一筆記錄之前，您可以執行任何其他資料錄集作業。  
  
> [!NOTE]
>  您不需要檢查已刪除的狀態的快照集或資料表類型的資料錄集中的記錄。 因為無法刪除記錄，從快照集，所以不需要呼叫`IsDeleted`。 針對資料表類型的資料錄集，實際上會從資料錄集移除已刪除的記錄。 一旦記錄已刪除，由您、 其他使用者時，或在另一個資料錄集，您無法捲動至該記錄。 因此，沒有不需要呼叫`IsDeleted`。  
  
 當您刪除資料錄從動態集時，會從資料錄集移除，您不能捲動至該記錄。 不過，如果中的記錄動態集會刪除另一位使用者或在另一個資料錄集根據相同的資料表中`IsDeleted`會傳回**TRUE**稍後捲動至該記錄。  
  
 如需相關資訊，請參閱主題 < 刪除方法 」、 「 LastModified 屬性 」 和 DAO [說明] 中的 「 EditMode 屬性 」。  
  
##  <a name="iseof"></a>  CDaoRecordset::IsEOF  
 當您從資料錄捲動記錄，以了解是否您已經超過資料錄集的最後一筆記錄，請呼叫此成員函式。  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果資料錄集不包含任何記錄，或如果您已經超過上一筆記錄中;否則便是 0。  
  
### <a name="remarks"></a>備註  
 您也可以呼叫`IsEOF`來判斷資料錄集是否包含任何記錄，或為空白。 之後立即呼叫**開啟**，如果資料錄集不包含任何記錄，`IsEOF`傳回非零值。 當您開啟具有至少一個資料錄的資料錄集時，第一筆記錄是目前的記錄和`IsEOF`傳回 0。  
  
 如果最後一筆記錄是目前的記錄，當您呼叫`MoveNext`，`IsEOF`後續會傳回非零值。 如果`IsEOF`傳回非零，而且您呼叫`MoveNext`，擲回例外狀況。 如果`IsEOF`傳回非零，目前的記錄為未定義，並需要目前記錄的任何動作將會導致例外狀況。  
  
 上的特定方法的效果`IsBOF`和`IsEOF`設定：  
  
-   呼叫**開啟**內部讓第一筆記錄中的資料錄集的目前記錄呼叫**MoveFirst**。 因此，呼叫**開啟**記錄原因的空集合上`IsBOF`和`IsEOF`傳回非零值。 (請參閱下表中的失敗行為**MoveFirst**呼叫。)  
  
-   所有成功找出一筆記錄的移動作業會造成同時`IsBOF`和`IsEOF`傳回 0。  
  
-   `AddNew`後面接著呼叫**更新**成功插入新記錄的呼叫會導致`IsBOF`傳回 0，但是只有`IsEOF`已經為非零值。 狀態`IsEOF`一定會維持不變。 Microsoft Jet 資料庫引擎所定義，空的資料錄集的目前的記錄指標是檔案的結尾，因此目前的記錄後面插入新的記錄。  
  
-   任何**刪除**呼叫，即使在移除資料錄集，唯一的剩餘記錄不會變更的值`IsBOF`或`IsEOF`。  
  
 下表顯示移動所允許的作業使用的不同組合`IsBOF` /  `IsEOF`。  
  
||MoveFirst、 MoveLast|MovePrev，<br /><br /> 移動 < 0|移動 0|MoveNext，<br /><br /> 移動 > 0|  
|------|-------------------------|-----------------------------|------------|-----------------------------|  
|`IsBOF`= 是非零值，<br /><br /> `IsEOF`=0|Allowed|例外|例外|Allowed|  
|`IsBOF`=0,<br /><br /> `IsEOF`= 為非零，|Allowed|Allowed|例外|例外|  
|兩者都為非零，|例外|例外|例外|例外|  
|這兩個 0|Allowed|Allowed|Allowed|Allowed|  
  
 允許在移動操作並不表示作業將會成功找到某筆記錄。 此外，它只會指出可以嘗試執行指定的移動作業，而且不會產生例外狀況。 值`IsBOF`和`IsEOF`成員函式可能會因為嘗試的移動而變更。  
  
 沒有找到的值為一筆記錄的移動作業的效果`IsBOF`和`IsEOF`設定 下表所示。  
  
||IsBOF|IsEOF|  
|------|-----------|-----------|  
|**MoveFirst**， `MoveLast`|為非零，|為非零，|  
|**移動**0|沒有變更|沒有變更|  
|`MovePrev`**移動**< 0|為非零，|沒有變更|  
|`MoveNext`**移動**> 0|沒有變更|為非零，|  
  
 如需相關資訊，請參閱本主題 「 BOF，EOF 屬性 」 DAO [說明] 中。  
  
##  <a name="isfielddirty"></a>  CDaoRecordset::IsFieldDirty  
 呼叫此成員函式，以判斷是否動態集的指定的欄位資料成員已標示為 「 有所變更 」 （變更）。  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 您想要檢查其狀態的欄位資料成員的指標或**NULL**來判斷是否有任何欄位已變更。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果指定的欄位資料成員標示為中途。否則便是 0。  
  
### <a name="remarks"></a>備註  
 所有已變更的欄位資料成員中的資料會傳輸記錄資料來源上呼叫更新目前的記錄時**更新**成員函式`CDaoRecordset`(呼叫**編輯**或`AddNew`)。 使用這項知識，您可以採取進一步的步驟，例如取消旗標來標示資料行，因此將不會寫入至資料來源的欄位資料成員。  
  
 `IsFieldDirty` 透過實作`DoFieldExchange`。  
  
##  <a name="isfieldnull"></a>  CDaoRecordset::IsFieldNull  
 呼叫此成員函式，以判斷資料錄集的指定的欄位資料成員是否已標註為 Null。  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 您想要檢查其狀態的欄位資料成員的指標或**NULL**來判斷是否有任何欄位的 Null。  
  
### <a name="return-value"></a>傳回值  
 指定的欄位資料成員會標示為 Null; 如果為非零否則便是 0。  
  
### <a name="remarks"></a>備註  
 (在資料庫詞彙中，Null 表示不擁有任何值 」，而且不是相同**NULL** c + + 中。)如果欄位資料成員被標示為 Null，則會將它解譯為資料行的任何值是目前的記錄。  
  
> [!NOTE]
>  在某些情況下，使用`IsFieldNull`可能會沒有效率，，如下列程式碼範例所示：  
  
 [!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]  
  
> [!NOTE]
>  如果您使用動態記錄繫結，而不需從衍生`CDaoRecordset`，務必使用**VT_NULL**中範例所示。  
  
##  <a name="isfieldnullable"></a>  CDaoRecordset::IsFieldNullable  
 呼叫以判斷指定的欄位資料成員是否為"null"（可以是設定為 Null 值; 此成員函式C + + **NULL**不是 Null，表示，在資料庫詞彙中，相同不擁有任何值 」)。  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 您想要檢查其狀態的欄位資料成員的指標或**NULL**來判斷是否有任何欄位的 Null。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果指定的欄位資料成員可以設為 Null。否則便是 0。  
  
### <a name="remarks"></a>備註  
 不能是 Null 的欄位必須有值。 如果您嘗試將這類欄位設定為 Null，在加入或更新記錄時，資料來源會拒絕的新增或更新，以及**更新**將會擲回例外狀況。 當您呼叫時，就會發生例外狀況**更新**，不會在您呼叫`SetFieldNull`。  
  
##  <a name="isopen"></a>  CDaoRecordset::IsOpen  
 呼叫此成員函式，以判斷是否開啟資料錄集。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果資料錄集物件的**開啟**或**Requery**先前呼叫成員函式和資料錄集尚未關閉; 否則為 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_bcheckcachefordirtyfields"></a>  M_bcheckcachefordirtyfields  
 包含旗標，指出是否快取的欄位會自動標示為中途 （變更） 和 Null。  
  
### <a name="remarks"></a>備註  
 旗標預設值為**TRUE**。 此資料成員中的設定會控制整個的雙重緩衝機制。 如果您將旗標設定為**TRUE**，您可以關閉使用 DFX 機制欄位的欄位為基礎的快取。 如果您將旗標設定為**FALSE**，您必須呼叫`SetFieldDirty`和`SetFieldNull`自己。  
  
 設定此資料成員，然後再呼叫**開啟**。 這項機制是主要目的是為了方便使用。 效能可能會變慢因為雙重緩衝的欄位進行變更時。  
  
##  <a name="m_nfields"></a>  CDaoRecordset::m_nFields  
 包含資料錄集類別中的欄位資料成員的數目和資料來源的資料錄集選取資料行數目。  
  
### <a name="remarks"></a>備註  
 資料錄集類別的建構函式必須初始化`m_nFields`與正確的靜態繫結的欄位數目。 當您使用它來宣告資料錄集類別 ClassWizard 會寫入您這類初始化。 您也可以撰寫它以手動方式。  
  
 架構會使用這個數字來管理的欄位資料成員與對應的資料行的資料來源上目前的記錄之間的互動。  
  
> [!NOTE]
>  這個數字必須對應到登錄中的輸出資料行數目`DoFieldExchange`呼叫之後`SetFieldType`搭配參數**CDaoFieldExchange::outputColumn**。  
  
 您可以繫結的資料行動態的方式`CDaoRecordset::GetFieldValue`和`CDaoRecordset::SetFieldValue`。 如果您這樣做，您不需要遞增計數`m_nFields`以反映的 DFX 函式呼叫您`DoFieldExchange`成員函式。  
  
##  <a name="m_nparams"></a>  CDaoRecordset::m_nParams  
 包含資料錄集類別中的參數資料成員的數目，與資料錄集的查詢傳遞的參數數目。  
  
### <a name="remarks"></a>備註  
 如果您的資料錄集類別有任何參數的資料成員，該類別的建構函式必須初始化`m_nParams`以正確的數字。 值`m_nParams`預設值為 0。 如果您加入的參數資料成員 — 您必須手動執行這 — 您也可以手動必須加入初始化類別建構函式，以反映參數的數目 (必須是至少一樣大的數目 ' 中的預留位置您**m_strFilter**或`m_strSort`字串)。  
  
 當它參數化資料錄集的查詢，架構會使用這個數字。  
  
> [!NOTE]
>  此號碼必須符合的 「 參數 」 中登錄數目`DoFieldExchange`呼叫之後`SetFieldType`搭配參數**CFieldExchange::param**。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 參數物件 」。  
  
##  <a name="m_pdaorecordset"></a>  CDaoRecordset::m_pDAORecordset  
 包含的 DAO 資料錄集物件基礎的 OLE 介面的指標`CDaoRecordset`物件。  
  
### <a name="remarks"></a>備註  
 如果您需要直接存取 DAO 介面，請使用這個指標。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 資料錄集物件 」。  
  
##  <a name="m_pdatabase"></a>  CDaoRecordset::m_pDatabase  
 包含的指標`CDaoDatabase`透過此資料錄集連接到資料來源的物件。  
  
### <a name="remarks"></a>備註  
 兩種方式設定這個變數。 一般而言，您將指標傳遞至已開啟`CDaoDatabase`物件建構資料錄集物件時。 如果您要傳入**NULL**反而**CDaoRecordset**建立`CDaoDatabase`為您的物件，並開啟它。 在任一情況下，`CDaoRecordset`儲存在此變數的指標。  
  
 通常您會不直接需要使用中儲存的指標**m_pDatabase**。 如果您要撰寫您自己的擴充功能`CDaoRecordset`，不過，您可能需要使用指標。 例如，您可能需要將指標如果您擲回自己`CDaoException`(s)。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 資料庫物件 」。  
  
##  <a name="m_strfilter"></a>  CDaoRecordset::m_strFilter  
 包含用來建構字串**其中**SQL 陳述式的子句。  
  
### <a name="remarks"></a>備註  
 它不包含保留的字**其中**來篩選資料錄集。 使用此資料成員不是適用於資料表類型的資料錄集。 使用**m_strFilter**開啟資料錄集，使用時有任何作用`CDaoQueryDef`指標。  
  
 使用美國日期格式 （月-日-年） 時，即使您不想要使用 Microsoft Jet 資料庫引擎的美國版本篩選出包含日期欄位否則，如預期般，可能未篩選的資料。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 < 篩選屬性 >。  
  
##  <a name="m_strsort"></a>  CDaoRecordset::m_strSort  
 包含字串，包含**ORDERBY**子句的 SQL 陳述式，而不保留字**ORDERBY**。  
  
### <a name="remarks"></a>備註  
 您可以依據動態和快照集類型的資料錄集物件。  
  
 您無法排序資料表類型的資料錄集物件。 若要判斷資料表類型的資料錄集的排序次序，請呼叫[SetCurrentIndex](#setcurrentindex)。  
  
 使用`m_strSort`開啟資料錄集，使用時有任何作用`CDaoQueryDef`指標。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 「 排序屬性 」。  
  
##  <a name="move"></a>  CDaoRecordset::Move  
 呼叫此成員函式，來定位資料錄集`lRows`與目前記錄的記錄。  
  
```  
virtual void Move(long lRows);
```  
  
### <a name="parameters"></a>參數  
 `lRows`  
 向前或向後移動的記錄數目。 正值向前，移到資料錄集的結尾。 負數值移動，朝的開頭。  
  
### <a name="remarks"></a>備註  
 您可以在向前或向後移動。 `Move( 1 )` 相當於`MoveNext`，和`Move( -1 )`相當於`MovePrev`。  
  
> [!CAUTION]
>  呼叫上述任一**移動**函式擲回例外狀況，如果資料錄集不有任何記錄。 一般情況下，呼叫`IsBOF`和`IsEOF`之前移動作業，以判斷資料錄集是否有任何記錄。 在您呼叫後**開啟**或**Requery**，呼叫`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果您有捲動過去的開頭或結尾的資料錄集 (`IsBOF`或`IsEOF`傳回非零)，呼叫**移動**會擲回`CDaoException`。  
  
> [!NOTE]
>  如果您呼叫任何**移動**函式時，目前的記錄更新或加入更新都將遺失，而不發出警告。  
  
 當您呼叫**移動**順向捲動快照集中，`lRows`參數必須是正整數，而且不允許書籤，以便您可以向前移動只。  
  
 若要讓 first、 last 下, 一步，或上一個記錄資料錄集中目前的記錄，呼叫**MoveFirst**， `MoveLast`， `MoveNext`，或`MovePrev`成員函式。  
  
 如需相關資訊，請參閱主題 < 移動方法 」 和 「 MoveFirst、 MoveLast、 MoveNext，MovePrevious 方法 」 DAO [說明] 中。  
  
##  <a name="movefirst"></a>  CDaoRecordset::MoveFirst  
 呼叫此成員函式 （如果有的話），請在第一筆資料錄集中目前的記錄。  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>備註  
 您不需要呼叫**MoveFirst**立即開啟資料錄集之後。 此時，第一筆記錄 （如果有的話） 會自動為目前的記錄。  
  
> [!CAUTION]
>  呼叫上述任一**移動**函式擲回例外狀況，如果資料錄集不有任何記錄。 一般情況下，呼叫`IsBOF`和`IsEOF`之前移動作業，以判斷資料錄集是否有任何記錄。 在您呼叫後**開啟**或**Requery**，呼叫`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果您呼叫任何**移動**函式時，目前的記錄更新或加入更新都將遺失，而不發出警告。  
  
 使用**移動**記錄從移動而不套用條件的函式。 使用動態類型或符合特定條件的快照集類型的資料錄集物件中尋找記錄的尋找作業。 若要尋找記錄中的資料表類型的資料錄集物件，請呼叫`Seek`。  
  
 資料錄集參考的資料表類型的資料錄集時，如果移動會遵循資料表目前的索引。 您可以使用基本的 DAO 物件的索引屬性，來設定目前的索引。 如果您未設定目前的索引，傳回記錄的順序會是未定義。  
  
 如果您呼叫`MoveLast`根據 SQL 查詢或 querydef 資料錄集物件，在強制完成查詢和資料錄集物件會完全擴展。  
  
 您不能呼叫**MoveFirst**或`MovePrev`使用順向捲動快照集的成員函式。  
  
 若要移動的目前位置記錄中的資料錄集物件特定的數字的記錄向前或向後，呼叫**移動**。  
  
 如需相關資訊，請參閱主題 < 移動方法 」 和 「 MoveFirst、 MoveLast、 MoveNext，MovePrevious 方法 」 DAO [說明] 中。  
  
##  <a name="movelast"></a>  CDaoRecordset::MoveLast  
 呼叫此成員函式進行最後一筆記錄 （如果有的話） 中資料錄集目前的記錄。  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>備註  
  
> [!CAUTION]
>  呼叫上述任一**移動**函式擲回例外狀況，如果資料錄集不有任何記錄。 一般情況下，呼叫`IsBOF`和`IsEOF`之前移動作業，以判斷資料錄集是否有任何記錄。 在您呼叫後**開啟**或**Requery**，呼叫`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果您呼叫任何**移動**函式時，目前的記錄更新或加入更新都將遺失，而不發出警告。  
  
 使用**移動**記錄從移動而不套用條件的函式。 使用動態類型或符合特定條件的快照集類型的資料錄集物件中尋找記錄的尋找作業。 若要尋找記錄中的資料表類型的資料錄集物件，請呼叫`Seek`。  
  
 資料錄集參考的資料表類型的資料錄集時，如果移動會遵循資料表目前的索引。 您可以使用基本的 DAO 物件的索引屬性，來設定目前的索引。 如果您未設定目前的索引，傳回記錄的順序會是未定義。  
  
 如果您呼叫`MoveLast`根據 SQL 查詢或 querydef 資料錄集物件，在強制完成查詢和資料錄集物件會完全擴展。  
  
 若要移動的目前位置記錄中的資料錄集物件特定的數字的記錄向前或向後，呼叫**移動**。  
  
 如需相關資訊，請參閱主題 < 移動方法 」 和 「 MoveFirst、 MoveLast、 MoveNext，MovePrevious 方法 」 DAO [說明] 中。  
  
##  <a name="movenext"></a>  CDaoRecordset::MoveNext  
 呼叫此成員函式，要在資料錄集的目前記錄中的下一筆記錄。  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>備註  
 建議您呼叫`IsBOF`您嘗試將移至前一筆記錄之前。 呼叫`MovePrev`將會擲回`CDaoException`如果`IsBOF`傳回非零值，指出或是您有已捲動第一筆記錄之前，沒有記錄所選取的資料錄集。  
  
> [!CAUTION]
>  呼叫上述任一**移動**函式擲回例外狀況，如果資料錄集不有任何記錄。 一般情況下，呼叫`IsBOF`和`IsEOF`之前移動作業，以判斷資料錄集是否有任何記錄。 在您呼叫後**開啟**或**Requery**，呼叫`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果您呼叫任何**移動**函式時，目前的記錄更新或加入更新都將遺失，而不發出警告。  
  
 使用**移動**記錄從移動而不套用條件的函式。 使用動態類型或符合特定條件的快照集類型的資料錄集物件中尋找記錄的尋找作業。 若要尋找記錄中的資料表類型的資料錄集物件，請呼叫`Seek`。  
  
 資料錄集參考的資料表類型的資料錄集時，如果移動會遵循資料表目前的索引。 您可以使用基本的 DAO 物件的索引屬性，來設定目前的索引。 如果您未設定目前的索引，傳回記錄的順序會是未定義。  
  
 若要移動的目前位置記錄中的資料錄集物件特定的數字的記錄向前或向後，呼叫**移動**。  
  
 如需相關資訊，請參閱主題 < 移動方法 」 和 「 MoveFirst、 MoveLast、 MoveNext，MovePrevious 方法 」 DAO [說明] 中。  
  
##  <a name="moveprev"></a>  CDaoRecordset::MovePrev  
 呼叫此成員函式，要在資料錄集的目前記錄中的上一筆記錄。  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>備註  
 建議您呼叫`IsBOF`您嘗試將移至前一筆記錄之前。 呼叫`MovePrev`將會擲回`CDaoException`如果`IsBOF`傳回非零值，指出或是您有已捲動第一筆記錄之前，沒有記錄所選取的資料錄集。  
  
> [!CAUTION]
>  呼叫上述任一**移動**函式擲回例外狀況，如果資料錄集不有任何記錄。 一般情況下，呼叫`IsBOF`和`IsEOF`之前移動作業，以判斷資料錄集是否有任何記錄。 在您呼叫後**開啟**或**Requery**，呼叫`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果您呼叫任何**移動**函式時，目前的記錄更新或加入更新都將遺失，而不發出警告。  
  
 使用**移動**記錄從移動而不套用條件的函式。 使用動態類型或符合特定條件的快照集類型的資料錄集物件中尋找記錄的尋找作業。 若要尋找記錄中的資料表類型的資料錄集物件，請呼叫`Seek`。  
  
 資料錄集參考的資料表類型的資料錄集時，如果移動會遵循資料表目前的索引。 您可以使用基本的 DAO 物件的索引屬性，來設定目前的索引。 如果您未設定目前的索引，傳回記錄的順序會是未定義。  
  
 您不能呼叫**MoveFirst**或`MovePrev`使用順向捲動快照集的成員函式。  
  
 若要移動的目前位置記錄中的資料錄集物件特定的數字的記錄向前或向後，呼叫**移動**。  
  
 如需相關資訊，請參閱主題 < 移動方法 」 和 「 MoveFirst、 MoveLast、 MoveNext，MovePrevious 方法 」 DAO [說明] 中。  
  
##  <a name="open"></a>  Cdaorecordset:: Open  
 您必須呼叫此成員函式，來擷取資料錄集的記錄。  
  
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
 `nOpenType`  
 下列其中一個值：  
  
- **dbOpenDynaset**雙向捲動的動態類型資料錄集。 這是預設值。  
  
- **dbOpenTable**雙向捲動資料表類型資料錄集。  
  
- **dbOpenSnapshot**雙向捲動的快照集型別資料錄集。  
  
 `lpszSQL`  
 字串指標，包含下列其中之一：  
  
-   A **NULL**指標。  
  
-   一或多個 tabledefs 及/或 querydefs （以逗號分隔） 的名稱。  
  
-   SQL**選取**陳述式 (並選擇性地使用 SQL**其中**或**ORDERBY**子句)。  
  
-   傳遞的查詢。  
  
 `nOptions`  
 一或多個以下的選項。 預設值為 0。 可能的值如下：  
  
- **dbAppendOnly**只可以新增新的記錄 （動態類型資料錄集只）。 此選項表示常值可能只會附加記錄。 MFC ODBC 資料庫類別具有僅附加選項，可允許擷取和附加的記錄。  
  
- **dbForwardOnly**資料錄集是順向捲動快照集。  
  
- **dbSeeChanges**產生例外狀況，如果另一位使用者正在變更您正在編輯的資料。  
  
- **dbDenyWrite**其他使用者無法修改或新增記錄。  
  
- **dbDenyRead**其他使用者無法檢視的記錄 （資料表類型的資料錄集只）。  
  
- **dbReadOnly**只能檢視記錄; 其他使用者可以修改它們。  
  
- **dbInconsistent** （動態類型資料錄集只） 允許不一致的更新。  
  
- **dbConsistent**僅允許 （動態類型資料錄集只） 一致更新。  
  
> [!NOTE]
>  常數**dbConsistent**和**dbInconsistent**互為獨佔模式。 您可以使用其中一種，但不是能同時指定的執行個體中**開啟**。  
  
 *pTableDef*  
 指標[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)物件。 此功能僅適用於資料表類型的資料錄集。 時使用此選項，`CDaoDatabase`指標用來建構`CDaoRecordset`不使用; 相反地，使用 tabledef 所在的資料庫。  
  
 *pQueryDef*  
 指標[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)物件。 這個版本是僅適用於動態類型和快照集型別資料錄集。 時使用此選項，`CDaoDatabase`指標用來建構`CDaoRecordset`不使用; 相反地，使用 querydef 所在的資料庫。  
  
### <a name="remarks"></a>備註  
 然後再呼叫**開啟**，您必須建構資料錄集物件。 有幾個方式可做到這點：  
  
-   當您建構資料錄集物件時，傳遞指標`CDaoDatabase`已經開啟的物件。  
  
-   當您建構資料錄集物件時，傳遞指標`CDaoDatabase`不是開啟的物件。 資料錄集開啟`CDaoDatabase`物件，但不是會關閉它時關閉資料錄集物件。  
  
-   當您建構資料錄集物件時，傳遞**NULL**指標。 資料錄集物件呼叫`GetDefaultDBName`取得 Microsoft Access 的名稱。若要開啟 MDB 檔。 然後會開啟資料錄集`CDaoDatabase`物件，並讓它開啟，只要資料錄集已開啟。 當您呼叫**關閉**資料錄集，`CDaoDatabase`物件也會關閉。  
  
    > [!NOTE]
    >  資料錄集開啟時`CDaoDatabase`物件，則會以非獨佔存取的資料來源。  
  
 版本的**開啟**使用`lpszSQL`參數，資料錄集開啟之後，您就可以擷取在數種方式之一的記錄。 第一個選項是 DFX 函式在您`DoFieldExchange`。 第二個選項是使用動態繫結呼叫`GetFieldValue`成員函式。 這些選項可以個別或合併實作。 若將它們合併，您必須先通過 SQL 陳述式中自行呼叫**開啟**。  
  
 當您使用的第二個版本**開啟**您傳入其中`CDaoTableDef`物件，產生的資料行可供您透過繫結`DoFieldExchange`和 DFX 機制和/或透過動態繫結`GetFieldValue`。  
  
> [!NOTE]
>  您只可以呼叫**開啟**使用`CDaoTableDef`資料表類型的資料錄集物件。  
  
 當您使用的第三個版本**開啟**您傳入其中`CDaoQueryDef`物件，將會執行查詢，，和產生的資料行可供您透過繫結`DoFieldExchange`和 DFX 機制，及 （或動態地繫結)透過`GetFieldValue`。  
  
> [!NOTE]
>  您只可以呼叫**開啟**使用`CDaoQueryDef`動態類型和快照集類型的資料錄集物件。  
  
 第一個版本**開啟**使用`lpszSQL`參數時，記錄會根據選取下表所示的準則。  
  
|`lpszSQL` 參數的值|取決於選取的記錄|範例|  
|--------------------------------------|----------------------------------------|-------------|  
|**NULL**|所傳回的字串`GetDefaultSQL`。||  
|一或多個 tabledefs 及/或 querydef 名稱的逗號分隔清單。|中的所有資料行表示`DoFieldExchange`。|`"Customer"`|  
|**選取**資料行清單**FROM**資料表清單|從指定的 tabledef(s) 及/或 querydef(s) 所指定資料行。|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|  
  
 一般的程序會傳遞**NULL**至**開啟**; 在此情況下，**開啟**呼叫`GetDefaultSQL`，ClassWizard 會產生建立時的可覆寫成員函式`CDaoRecordset`-衍生的類別。 這個值會提供您在 類別精靈中指定的 tabledef(s) 及/或 querydef 名稱。 您可以改為指定中的其他資訊`lpszSQL`參數。  
  
 無論您將傳遞，**開啟**建構查詢的最終 SQL 字串 (這個字串可能有 SQL**其中**和**ORDERBY**子句附加至`lpszSQL`字串傳遞），然後執行查詢。 您可以藉由呼叫檢查建構的字串`GetSQL`之後呼叫**開啟**。  
  
 資料錄集類別的欄位資料成員的資料行之選取的資料繫結。 如果傳回任何記錄，第一筆記錄會變成目前的記錄。  
  
 如果您想要設定的資料錄集篩選或排序，例如選項設定`m_strSort`或**m_strFilter**建構資料錄集物件之後，但在呼叫之前**開啟**。 如果您想要重新整理資料錄集之後的記錄資料錄集已經開啟，請呼叫**Requery**。  
  
 如果您呼叫**開啟**動態類型或快照集類型的資料錄集，或如果資料來源指的是 SQL 陳述式或 tabledef 表示附加的資料表，您不能使用**dbOpenTable**類型引數。如果您這樣做，MFC 會擲回例外狀況。 若要判斷 tabledef 物件是否表示附加的資料表，請建立[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)物件並呼叫其[GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect)成員函式。  
  
 使用**dbSeeChanges**旗標，如果您想要編輯或刪除相同的記錄時，另一位使用者或電腦上的其他程式所做的變更的設陷。 例如，如果兩位使用者開始編輯同一筆記錄，若要呼叫的第一個使用者**更新**成員函式會成功。 當**更新**第二個使用者，會呼叫`CDaoException`就會擲回。 同樣地，如果第二個使用者嘗試呼叫**刪除**刪除記錄，而且已經變更的第一位使用者， `CDaoException` ，就會發生。  
  
 一般而言，如果使用者取得這個`CDaoException`同時更新，您的程式碼應該重新整理欄位的內容，並擷取已修改的值。 正在刪除，發生例外狀況，您的程式碼可以顯示新的記錄資料給使用者和訊息，指出最近已變更的資料。 此時，您的程式碼可以要求確認，使用者仍然想要刪除的記錄。  
  
> [!TIP]
>  使用順向捲動選項 ( **dbForwardOnly**) 來改善效能，當您的應用程式的資料錄集在單一行程中，開啟 ODBC 資料來源。  
  
 如需相關資訊，請參閱主題 < OpenRecordset 方法 >，DAO [說明] 中。  
  
##  <a name="requery"></a>  CDaoRecordset::Requery  
 呼叫此成員函式，以重建 （重新整理） 資料錄集。  
  
```  
virtual void Requery();
```  
  
### <a name="remarks"></a>備註  
 如果傳回任何記錄，第一筆記錄會變成目前的記錄。  
  
 為了讓資料錄集，以反映您或其他使用者對資料來源的刪除和新增項目，您必須重建資料錄集，藉由呼叫**Requery**。 如果資料錄集是動態集，它會自動反映您或其他使用者對其現有的記錄 （但不是新增項目） 的更新。 如果資料錄集是快照集，您必須呼叫**Requery**以反映其他使用者，以及新增和刪除的編輯。  
  
 動態集或快照集，請呼叫**Requery**每當您想要重建資料錄集使用參數值。 設定新的篩選或排序藉由設定[m_strFilter](#m_strfilter)和[m_strSort](#m_strsort)之前先呼叫**Requery**。 設定新的參數指派新值給參數資料成員，然後再呼叫**Requery**。  
  
 如果嘗試重建資料錄集失敗，就會關閉資料錄集。 之前先呼叫**Requery**，您可以判斷是否可以藉由呼叫重新查詢資料錄集[CanRestart](#canrestart)成員函式。 `CanRestart` 不保證**Requery**會成功。  
  
> [!CAUTION]
>  呼叫**Requery**之後才呼叫**開啟**。  
  
> [!NOTE]
>  呼叫[Requery](#requery)變更 DAO 書籤。  
  
 您不能呼叫**Requery**動態類型或如果呼叫的快照集型別資料錄集上`CanRestart`傳回 0，也不可以使用該類型的資料表資料錄集。  
  
 如果兩個`IsBOF`和`IsEOF`之後呼叫傳回非零**Requery**，查詢未傳回任何記錄和資料錄集將會包含任何資料。  
  
 如需相關資訊，請參閱主題 < 重新查詢方法 >，DAO [說明] 中。  
  
##  <a name="seek"></a>  CDaoRecordset::Seek  
 呼叫此成員函式，來尋找符合目前的指定的準則的索引，並將該記錄目前的記錄索引的資料表類型的資料錄集物件中的記錄。  
  
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
 `lpszComparison`  
 下列字串運算式的其中一個:"<"，"\<="，"="、"> ="，或 「 > 」。  
  
 `pKey1`  
 指標[COleVariant](../../mfc/reference/colevariant-class.md)其值會對應到索引中的第一個欄位。 必要。  
  
 *pKey2*  
 指標`COleVariant`其值會對應到在索引中，第二個欄位，如果有的話。 預設為**NULL**。  
  
 *pKey3*  
 指標`COleVariant`其值會對應到在索引中，第三個欄位，如果有的話。 預設為**NULL**。  
  
 *pKeyArray*  
 Variant 的陣列指標。 陣列大小會對應至索引中的欄位數目。  
  
 *nKeys*  
 對應到陣列，這是在索引中的欄位數目的大小的整數。  
  
> [!NOTE]
>  請勿指定機碼中的萬用字元。 萬用字元會導致`Seek`傳回沒有相符的記錄。  
  
### <a name="return-value"></a>傳回值  
 非零，如果相符記錄找到，否則為 0。  
  
### <a name="remarks"></a>備註  
 使用第二個 （陣列） 版本的`Seek`處理以上的四個欄位的索引。  
  
 `Seek` 啟用高效能的索引搜尋作業類型的資料表資料錄集。 您必須設定目前的索引，藉由呼叫`SetCurrentIndex`之前先呼叫`Seek`。 如果索引找出非唯一索引鍵欄位或欄位，`Seek`找出符合準則的第一個記錄。 如果您未設定索引，則會擲回例外狀況。  
  
 請注意，如果您不想要建立的 UNICODE 資料錄集，則`COleVariant`物件必須明確宣告為 ANSI。 這可以經由使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)** 表單的建構函式與`vtSrc`設`VT_BSTRT`(ANSI) 或使用**COleVariant**函式[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)** 與`vtSrc`設`VT_BSTRT`。  
  
 當您呼叫`Seek`，您傳遞一個或多個索引鍵的值和比較運算子 ("<"，"\<="，"="、"> ="，或 「 > 」)。 `Seek` 搜尋指定的索引鍵欄位，並找出符合所指定之準則的第一個記錄`lpszComparison`和`pKey1`。 找到之後，`Seek`傳回非零值，並使該記錄的目前。 如果`Seek`無法找出相符項目，`Seek`傳回零，且目前的記錄未定義。 當直接使用 DAO，您必須明確檢查 NoMatch 屬性。  
  
 如果`lpszComparison`是"="、"> ="，或">"，`Seek`開頭的索引。 如果`lpszComparison`是"<"或"< ="，`Seek`開始索引結尾，且會在向後搜尋，除非有重複的索引項目結尾。 在此情況下，`Seek`開始索引結尾處的重複的索引項目之間的任意項目。  
  
 那里不需要是目前的記錄，當您使用`Seek`。  
  
 若要尋找記錄中的動態類型或符合特定條件的快照集型別資料錄集，使用 尋找作業。 若要包含所有記錄，不是只有滿足特定條件，可以使用 移動作業來移動記錄記錄。  
  
 您不能呼叫`Seek`上任何附加資料表類型，因為附加的資料表，必須先為動態類型或快照集類型的資料錄集。 不過，如果您呼叫`CDaoDatabase::Open`直接開啟可安裝的 ISAM 資料庫，您可以呼叫`Seek`該資料庫中的資料表上雖然效能可能會變慢。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 < 搜尋方法 >。  
  
##  <a name="setabsoluteposition"></a>  CDaoRecordset::SetAbsolutePosition  
 設定資料錄集物件的目前記錄中相對的記錄數目。  
  
```  
void SetAbsolutePosition(long lPosition);
```  
  
### <a name="parameters"></a>參數  
 *lPosition*  
 對應至目前的記錄資料錄集中的序數位置。  
  
### <a name="remarks"></a>備註  
 呼叫`SetAbsolutePosition`可讓您根據其序數位置中的動態類型或快照集類型的資料錄集的特定記錄目前的記錄指標的位置。 您也可以藉由呼叫來判斷目前的記錄編號[GetAbsolutePosition](#getabsoluteposition)。  
  
> [!NOTE]
>  此成員函式無效，僅適用於動態類型和快照集類型的資料錄集。  
  
 基本的 DAO 物件 AbsolutePosition 屬性值以零為起始。設定為 0，是指資料錄集中的第一個記錄。 將值設定為大於填入的記錄原因 MFC 擲回例外狀況數目。 您可以判斷資料錄集中填入記錄數目，藉由呼叫`GetRecordCount`成員函式。  
  
 如果目前的記錄會被刪除，未定義 AbsolutePosition 屬性值，和 MFC 擲回例外狀況，如果它參考。 新的記錄會加入至序列的結尾。  
  
> [!NOTE]
>  這個屬性不是要做為 surrogate 資料錄數目。 書籤仍保留並傳回指定位置的建議的方式，而目前的記錄放在所有類型的支援書籤的資料錄集物件的唯一方式。 特別是，指定記錄的位置時，變更會刪除在它前面的記錄。 也沒有指定的記錄會有相同的絕對位置，如果資料錄集時都會重新建立一次資料錄集內的個別記錄的順序不保證除非它以使用 SQL 陳述式建立，因為不保證**ORDERBY**子句。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 < AbsolutePosition 屬性 >。  
  
##  <a name="setbookmark"></a>  CDaoRecordset::SetBookmark  
 呼叫此成員函式可包含指定的書籤的記錄上放置資料錄集。  
  
```  
void SetBookmark(COleVariant varBookmark);
```  
  
### <a name="parameters"></a>參數  
 `varBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md)物件，其中包含書籤值的特定記錄。  
  
### <a name="remarks"></a>備註  
 當建立或開啟資料錄集物件時，其記錄的每個已經有唯一的書籤。 您可以藉由呼叫擷取目前的資料錄的書籤`GetBookmark`和儲存的值`COleVariant`物件。 您可以稍後返回該記錄藉由呼叫`SetBookmark`使用已儲存的書籤值。  
  
> [!NOTE]
>  呼叫[Requery](#requery)變更 DAO 書籤。  
  
 請注意，如果您不想要建立的 UNICODE 資料錄集，則`COleVariant`物件必須明確宣告為 ANSI。 這可以經由使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)** 表單的建構函式與`vtSrc`設`VT_BSTRT`(ANSI) 或使用**COleVariant**函式[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)** 與`vtSrc`設`VT_BSTRT`。  
  
 如需相關資訊，請參閱 「 書籤屬性 」 和 Bookmarkable 屬性"DAO [說明] 中。  
  
##  <a name="setcachesize"></a>  CDaoRecordset::SetCacheSize  
 呼叫此成員函式，可以設定要快取的記錄數目。  
  
```  
void SetCacheSize(long lSize);
```  
  
### <a name="parameters"></a>參數  
 `lSize`  
 指定記錄的數目。 典型值為 100。 如果設定為 0 會關閉快取。 設定必須介於 5 到 1200年的記錄。 快取可能使用大量的記憶體。  
  
### <a name="remarks"></a>備註  
 快取中保存最近從伺服器擷取的資料將會要求一次在執行應用程式資料的本機記憶體是一個空格。 資料快取可改善應用程式從遠端伺服器，透過動態類型資料錄集物件擷取資料的效能。 當要求資料時，Microsoft Jet 資料庫引擎的快取要求的資料會先檢查而不是擷取從伺服器中，花費的時間。 不是來自 ODBC 資料來源的資料不會儲存在快取中。  
  
 任何 ODBC 資料來源，例如附加的資料表，可以在本機快取。 若要建立快取，開啟資料錄集物件，從遠端資料來源，呼叫`SetCacheSize`和`SetCacheStart`成員函式，然後再呼叫`FillCache`成員函式或使用其中一種移動作業步驟記錄。 `lSize`參數`SetCacheSize`成員函式可以根據您的應用程式可以處理一次的記錄數目。 例如，如果您使用資料錄集的資料來源顯示在畫面上，您可以傳遞`SetCacheSize``lSize`參數為 20，一次顯示 20 的記錄。  
  
 如需相關資訊，請參閱 DAO 說明主題 「 CacheSize CacheStart 屬性 」。  
  
##  <a name="setcachestart"></a>  CDaoRecordset::SetCacheStart  
 呼叫此成員函式可指定要快取資料錄集中的第一筆記錄的書籤。  
  
```  
void SetCacheStart(COleVariant varBookmark);
```  
  
### <a name="parameters"></a>參數  
 `varBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md) ，指定要快取資料錄集中的第一筆記錄的書籤。  
  
### <a name="remarks"></a>備註  
 您可以使用書籤值的任何記錄`varBookmark`參數`SetCacheStart`成員函式。 請的記錄您想要啟動快取與目前的記錄，建立書籤在對該記錄使用[SetBookmark](#setbookmark)，並將書籤值傳遞做為參數`SetCacheStart`成員函式。  
  
 Microsoft Jet 資料庫引擎會從快取中，要求快取範圍內的記錄，它會向伺服器要求快取範圍外的記錄。  
  
 從快取擷取的記錄不會反映其他使用者同時進行的來源資料的變更。  
  
 若要強制更新的所有快取的資料，請傳遞`lSize`參數`SetCacheSize`為 0 時，呼叫`SetCacheSize`再次快取的大小與您原先要求，，然後呼叫`FillCache`成員函式。  
  
 請注意，如果您不想要建立的 UNICODE 資料錄集，則`COleVariant`物件必須明確宣告為 ANSI。 這可以經由使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)** 表單的建構函式與`vtSrc`設`VT_BSTRT`(ANSI) 或使用**COleVariant**函式[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)** 與`vtSrc`設`VT_BSTRT`。  
  
 如需相關資訊，請參閱主題 CacheSize，CacheStart 屬性 」 DAO 說明。  
  
##  <a name="setcurrentindex"></a>  CDaoRecordset::SetCurrentIndex  
 呼叫此成員函式，來設定資料表類型的資料錄集的索引。  
  
```  
void SetCurrentIndex(LPCTSTR lpszIndex);
```  
  
### <a name="parameters"></a>參數  
 `lpszIndex`  
 指標，包含要設定索引的名稱。  
  
### <a name="remarks"></a>備註  
 基底資料表中的記錄不儲存任何特定順序。 設定索引變更的資料庫中，從傳回的記錄順序，但不會影響的記錄會儲存的順序。 必須已定義指定的索引。 如果您嘗試使用不存在的索引物件，或當您呼叫時未設定索引[搜尋](#seek)，MFC 會擲回的例外狀況。  
  
 您可以藉由呼叫建立新的索引，資料表[CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex)及附加至基礎 tabledef 的索引集合的新索引，藉由呼叫[CDaoTableDef::Append](../../mfc/reference/cdaotabledef-class.md#append)，和然後重新開啟資料錄集。  
  
 記錄所傳回的資料表類型的資料錄集只依所定義的基礎 tabledef 索引。 若要排序其他順序的記錄，您可以開啟動態類型或使用 SQL 的快照集型別資料錄集**ORDERBY**子句儲存在[CDaoRecordset::m_strSort](#m_strsort)。  
  
 如需相關資訊，請參閱本主題 「 索引物件 」，DAO 說明中的 「 目前索引 」 的定義。  
  
##  <a name="setfielddirty"></a>  CDaoRecordset::SetFieldDirty  
 呼叫此成員函式加上旗標為已變更或為未變更的資料錄集欄位資料成員。  
  
```  
void SetFieldDirty(
    void* pv,  
    BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 包含資料錄集中的欄位資料成員的位址或**NULL**。 如果**NULL**，資料錄集中的所有欄位資料成員會加上旗都標。 (C + + **NULL**不是 Null 相同資料庫術語而言，這表示 「 有任何值 」。)  
  
 `bDirty`  
 **TRUE**欄位資料成員是否被標示為 「 中途 」 （變更）。 否則**FALSE**欄位資料成員是否被標示為 「 清除 」 （不變）。  
  
### <a name="remarks"></a>備註  
 標記成未變更的欄位，可確保不會更新欄位。  
  
 Framework 標記變更欄位資料成員，以確保它們將寫入至資料來源上記錄的 DAO 資料錄欄位交換 (DFX) 機制。 一般來說，變更欄位的值欄位已變更都會自動設定，因此您很少需要呼叫`SetFieldDirty`自己，不過您有時可能會想要確保的資料行會明確地更新或插入不論何種值存在於欄位資料成員。 DFX 機制也會採用使用**PSEUDONULL**。 如需詳細資訊，請參閱[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
 如果未使用的雙重緩衝機制，然後將變更欄位的值不會自動設定欄位已變更。 在此情況下，它必須明確設定為已變更的欄位。 中所包含的旗標[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制這項自動欄位檢查。  
  
> [!NOTE]
>  呼叫此成員函式，只有具有呼叫後[編輯](#edit)或[AddNew](#addnew)。  
  
 使用**NULL**的函式的第一個引數會將函數套用至所有**outputColumn**欄位，不**param**中欄位`CDaoFieldExchange`。 例如，呼叫  
  
 [!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]  
  
 集合只有**outputColumn**欄位**NULL**;**param**欄位不會受到影響。  
  
 用於**param**，您必須提供個別的實際位址**param**想要使用，例如：  
  
 [!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]  
  
 這表示您不能設定所有**param**欄位**NULL**，您可以使用如**outputColumn**欄位。  
  
 `SetFieldDirty` 透過實作`DoFieldExchange`。  
  
##  <a name="setfieldnull"></a>  CDaoRecordset::SetFieldNull  
 呼叫此成員函式可為 Null （特別具有沒有值） 或非 Null 的資料錄集欄位資料成員的旗標。  
  
```  
void SetFieldNull(
    void* pv,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 包含資料錄集中的欄位資料成員的位址或**NULL**。 如果**NULL**，資料錄集中的所有欄位資料成員會加上旗都標。 (C + + **NULL**不是 Null 相同資料庫術語而言，這表示 「 有任何值 」。)  
  
 `bNull`  
 非零，如果將欄位資料成員會標示為不具有任何值 (Null)。 否則為 0，表示欄位資料成員會標示為非 Null。  
  
### <a name="remarks"></a>備註  
 `SetFieldNull` 用於在繫結的欄位`DoFieldExchange`機制。  
  
 當您將新的記錄加入資料錄集時，所有的欄位資料成員會一開始設定為 Null 值，並標示為 「 中途 」 （變更）。 當您從資料來源擷取記錄時，其資料行可能是已有的值或 Null。 如果不是適用於將欄位設為 Null， [CDaoException](../../mfc/reference/cdaoexception-class.md)就會擲回。  
  
 如果您使用雙重緩衝機制，例如，如果您特別想要將目前記錄的欄位指定為沒有值，呼叫`SetFieldNull`與`bNull`設**TRUE**加上旗標為 Null。 如果先前標示欄位 Null，而且現在想要提供一個值，直接將新的值。 您沒有移除 Null 旗標與`SetFieldNull`。 若要判斷此欄位是否可為 Null，請呼叫[IsFieldNullable](#isfieldnullable)。  
  
 如果您未使用的雙重緩衝機制，然後將變更欄位的值不會自動設定欄位為已變更且非 Null。 具體而言，已變更且非 Null，您必須設定欄位。 中所包含的旗標[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制這項自動欄位檢查。  
  
 DFX 機制採用使用**PSEUDONULL**。 如需詳細資訊，請參閱[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
> [!NOTE]
>  呼叫此成員函式，只有具有呼叫後[編輯](#edit)或[AddNew](#addnew)。  
  
 使用**NULL**函式的第一個引數只能套用函式的**outputColumn**欄位，不**param**中欄位`CDaoFieldExchange`。 例如，呼叫  
  
 [!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]  
  
 集合只有**outputColumn**欄位**NULL**;**param**欄位不會受到影響。  
  
##  <a name="setfieldvalue"></a>  CDaoRecordset::SetFieldValue  
 呼叫此成員函式可設定的值 欄位中，依序數位置，或藉由變更字串的值。  
  
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
 `lpszName`  
 包含的欄位名稱的字串指標。  
  
 `varValue`  
 若要參考[COleVariant](../../mfc/reference/colevariant-class.md)物件，其中包含的欄位內容的值。  
  
 `nIndex`  
 整數，表示欄位的序數位置 （以零為起始） 的資料錄集的欄位集合中。  
  
 `lpszValue`  
 字串，包含值的欄位內容的指標。  
  
### <a name="remarks"></a>備註  
 使用`SetFieldValue`和[GetFieldValue](#getfieldvalue)以動態方式在執行的階段而不是以靜態方式使用的繫結資料行繫結欄位[DoFieldExchange](#dofieldexchange)機制。  
  
 請注意，是否您不會建立 UNICODE 資料錄集，您必須使用一種`SetFieldValue`不包含`COleVariant`參數，或`COleVariant`物件必須明確宣告為 ANSI。 這可以經由使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)** 表單的建構函式與`vtSrc`設`VT_BSTRT`(ANSI) 或使用**COleVariant**函式[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)** 與`vtSrc`設`VT_BSTRT`。  
  
 如需相關資訊，請參閱 「 欄位物件 」 和 DAO [說明] 中的 < 值屬性 > 主題。  
  
##  <a name="setfieldvaluenull"></a>  CDaoRecordset::SetFieldValueNull  
 呼叫此成員函式可將欄位設為 Null 值。  
  
```  
void SetFieldValueNull(int nIndex);  
void SetFieldValueNull(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 在資料錄集中的以零為起始的索引查閱欄位的索引。  
  
 `lpszName`  
 依名稱查閱中的資料錄集的欄位名稱。  
  
### <a name="remarks"></a>備註  
 C + + **NULL**不是 Null，表示，在資料庫詞彙中，相同 「 有任何值 」。  
  
 如需相關資訊，請參閱 「 欄位物件 」 和 DAO [說明] 中的 < 值屬性 > 主題。  
  
##  <a name="setlockingmode"></a>  CDaoRecordset::SetLockingMode  
 呼叫此成員函式可設定的鎖定資料錄集類型。  
  
```  
void SetLockingMode(BOOL bPessimistic);
```  
  
### <a name="parameters"></a>參數  
 *bPessimistic*  
 表示鎖定類型的旗標。  
  
### <a name="remarks"></a>備註  
 當您呼叫封閉式鎖定時作用中，包含您要編輯的資料錄的 2k 頁面鎖定**編輯**成員函式。 當您呼叫時，已解除鎖定頁面**更新**或**關閉**成員函式或任何移動或尋找作業。  
  
 開放式鎖定是作用中時包含記錄的 2k 頁面鎖定與正在更新記錄時，才**更新**成員函式。  
  
 如果鎖定頁面時，沒有其他使用者可以編輯在相同頁面上的記錄。 如果您呼叫`SetLockingMode`並傳遞非零值，和另一位使用者已經有 [鎖定] 頁面上，當您呼叫時，會擲回例外狀況**編輯**。 其他使用者可以讀取鎖定的頁面資料。  
  
 如果您呼叫`SetLockingMode`與零值及更新版本呼叫**更新**頁面由另一個使用者鎖定時，發生例外狀況。 若要看到對您的記錄另一位使用者所做的變更 （並中斷您的變更），請呼叫`SetBookmark`目前記錄的書籤值的成員函式。  
  
 當使用 ODBC 資料來源，是一律開放式鎖定的模式。  
  
##  <a name="setparamvalue"></a>  CDaoRecordset::SetParamValue  
 呼叫此成員函式在執行階段資料錄集中設定參數的值。  
  
```  
virtual void SetParamValue(
    int nIndex,  
    const COleVariant& varValue);

 
virtual void SetParamValue(
    LPCTSTR lpszName,  
    const COleVariant& varValue);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 數值參數的位置 querydef 參數集合中。  
  
 `var`  
 要設定; 的值請參閱 < 備註 >。  
  
 `lpszName`  
 您想要設定其值的參數名稱。  
  
### <a name="remarks"></a>備註  
 參數必須有已建立為資料錄集的 SQL 字串的一部分。 依名稱或它在集合中的索引位置，您可以存取的參數。  
  
 指定要設定為值`COleVariant`物件。 如需設定的所需的值和類型資訊您`COleVariant`物件，請參閱類別[COleVariant](../../mfc/reference/colevariant-class.md)。 請注意，如果您不想要建立的 UNICODE 資料錄集，則`COleVariant`物件必須明確宣告為 ANSI。 這可以經由使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)** 表單的建構函式與`vtSrc`設`VT_BSTRT`(ANSI) 或使用**COleVariant**函式[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)** 與`vtSrc`設`VT_BSTRT`。  
  
##  <a name="setparamvaluenull"></a>  CDaoRecordset::SetParamValueNull  
 呼叫此成員函式將參數設定為 Null 值。  
  
```  
void SetParamValueNull(int nIndex);  
void SetParamValueNull(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 在資料錄集中的以零為起始的索引查閱欄位的索引。  
  
 `lpszName`  
 依名稱查閱中的資料錄集的欄位名稱。  
  
### <a name="remarks"></a>備註  
 C + + **NULL**不是 Null，表示，在資料庫詞彙中，相同 「 有任何值 」。  
  
##  <a name="setpercentposition"></a>  CDaoRecordset::SetPercentPosition  
 呼叫此成員函式設定值，以變更目前的記錄中的記錄資料錄集的百分比為基礎的資料錄集物件中的概略位置。  
  
```  
void SetPercentPosition(float fPosition);
```  
  
### <a name="parameters"></a>參數  
 *fPosition*  
 介於 0 與 100 之間的數字。  
  
### <a name="remarks"></a>備註  
 當使用動態類型或快照集類型的資料錄集，先將資料填入資料錄集移到最後一個記錄才能呼叫`SetPercentPosition`。 如果您呼叫`SetPercentPosition`之前完全填入資料錄集，是相對於存取的值所指定的記錄數目的移動量[GetRecordCount](#getrecordcount)。 您可以將移到最後一個記錄藉由呼叫`MoveLast`。  
  
 一旦呼叫`SetPercentPosition`，變成目前的值的近似位置記錄。  
  
> [!NOTE]
>  呼叫`SetPercentPosition`移動至資料錄集中指定的記錄目前的記錄不建議使用。 呼叫[SetBookmark](#setbookmark)成員函式。  
  
 如需相關資訊，請參閱主題 DAO [說明] 中的 < PercentPosition 屬性 >。  
  
##  <a name="update"></a>  CDaoRecordset::Update  
 呼叫此成員函式呼叫之後`AddNew`或**編輯**成員函式。  
  
```  
virtual void Update();
```  
  
### <a name="remarks"></a>備註  
 此呼叫，才能完成`AddNew`或**編輯**作業。  
  
 同時`AddNew`和**編輯**準備編輯緩衝區，用來放置新增或編輯過的資料儲存到資料來源。 **更新**儲存資料。 只有這些欄位標記，或偵測到變更時都會更新。  
  
 如果資料來源支援交易，您可以進行**更新**呼叫 (和其相對應`AddNew`或**編輯**呼叫) 交易的一部分。  
  
> [!CAUTION]
>  如果您呼叫**更新**但未先呼叫`AddNew`或**編輯**，**更新**會擲回`CDaoException`。 如果您呼叫`AddNew`或**編輯**，您必須呼叫**更新**之前先呼叫[MoveNext](#movenext)或關閉資料錄集或資料來源連接。 否則，您的變更都會遺失而不另行通知。  
  
 當在多使用者環境中要以保守模式鎖定資料錄集物件時，記錄就會保持鎖定的時間**編輯**更新已完成之前使用。 如果樂觀地鎖定資料錄集時，記錄會鎖定及更新至資料庫之前，相較於編輯前記錄。 如果記錄已變更，因為您呼叫**編輯**、**更新**作業將會失敗，MFC 會擲回例外狀況。 您可以變更鎖定模式與`SetLockingMode`。  
  
> [!NOTE]
>  外部資料庫格式，例如 ODBC 和可安裝的 ISAM 一定會用於開放式鎖定。  
  
 如需相關資訊，請參閱主題 < AddNew 方法 >、 < CancelUpdate 方法 >、"Delete 方法 」、 「 LastModified 屬性 」，< 更新方法 > 和 DAO [說明] 中的 「 EditMode 屬性 」。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoWorkspace 類別](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)
