---
title: "CDaoRecordset 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- recordsets, types
- CDaoRecordset class
- records, CDaoRecordSet
ms.assetid: 2322067f-1027-4662-a5d7-aa2fc7488630
caps.latest.revision: 26
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
ms.openlocfilehash: 3d3d830a7d423a2653819e9cbf160538e486cfb0
ms.lasthandoff: 02/24/2017

---
# <a name="cdaorecordset-class"></a>CDaoRecordset 類別
表示選取自資料來源的資料錄集。  
  
## <a name="syntax"></a>語法  
  
```  
class CDaoRecordset : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CDaoRecordset::CDaoRecordset](#cdaorecordset)|建構 `CDaoRecordset` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDaoRecordset::AddNew](#addnew)|準備要加入新記錄。 呼叫[更新](#update)完成加入。|  
|[CDaoRecordset::CanAppend](#canappend)|傳回非零值，如果可以加入新的記錄，透過在資料錄集[AddNew](#addnew)成員函式。|  
|[CDaoRecordset::CanBookmark](#canbookmark)|傳回非零，如果資料錄集支援書籤。|  
|[CDaoRecordset::CancelUpdate](#cancelupdate)|取消任何暫止的更新，因為[編輯](#edit)或[AddNew](#addnew)作業。|  
|[CDaoRecordset::CanRestart](#canrestart)|傳回非零值如果[Requery](#requery)可以呼叫一次執行資料錄集的查詢。|  
|[CDaoRecordset::CanScroll](#canscroll)|傳回非零，如果您可以捲動資料錄。|  
|[CDaoRecordset::CanTransact](#cantransact)|傳回非零，如果資料來源支援交易。|  
|[CDaoRecordset::CanUpdate](#canupdate)|傳回非零值，如果可以更新資料錄集 （您可以新增、 更新或刪除記錄）。|  
|[CDaoRecordset::Close](#close)|關閉資料錄集。|  
|[CDaoRecordset::Delete](#delete)|刪除資料錄集目前的記錄。 在刪除之後，您必須明確地捲動至另一筆記錄。|  
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|呼叫之間交換資料 （在兩個方向） 的資料錄集的欄位資料成員和資料來源上對應的記錄。 實作 DAO 資料錄欄位交換 (DFX)。|  
|[CDaoRecordset::Edit](#edit)|準備變更為目前的記錄。 呼叫**更新**來完成編輯。|  
|[CDaoRecordset::FillCache](#fillcache)|填滿所有或部分的本機快取的資料錄集物件，包含從 ODBC 資料來源的資料。|  
|[CDaoRecordset::Find](#find)|首先下, 一步，找出特定的字串中符合指定的準則和讓該記錄的目前記錄的動態類型資料錄集的上一個或最後一個位置。|  
|[CDaoRecordset::FindFirst](#findfirst)|動態類型或快照集類型資料錄集滿足指定的準則，然後讓該記錄目前的記錄中，找出第一筆記錄。|  
|[CDaoRecordset::FindLast](#findlast)|動態類型或快照集類型資料錄集滿足指定的準則，然後讓該記錄目前的記錄中，找出最後一筆記錄。|  
|[CDaoRecordset::FindNext](#findnext)|動態類型或快照集類型資料錄集滿足指定的準則，然後讓該記錄目前的記錄中，找出下一筆記錄。|  
|[CDaoRecordset::FindPrev](#findprev)|動態類型或快照集類型資料錄集滿足指定的準則，然後讓該記錄目前的記錄中，找出前一筆記錄。|  
|[CDaoRecordset::GetAbsolutePosition](#getabsoluteposition)|傳回資料錄集物件的目前記錄的記錄數目。|  
|[CDaoRecordset::GetBookmark](#getbookmark)|傳回值，表示記錄上的書籤。|  
|[CDaoRecordset::GetCacheSize](#getcachesize)|傳回值，指定包含要在本機快取從 ODBC 資料來源之資料的動態類型資料錄集中的記錄數目。|  
|[CDaoRecordset::GetCacheStart](#getcachestart)|傳回值，指定要快取資料錄集中的第一筆記錄的書籤。|  
|[CDaoRecordset::GetCurrentIndex](#getcurrentindex)|傳回`CString`索引的資料表類型上使用包含索引的名稱最最近`CDaoRecordset`。|  
|[CDaoRecordset::GetDateCreated](#getdatecreated)|傳回的日期和時間的基礎基底資料表`CDaoRecordset`建立物件|  
|[CDaoRecordset::GetDateLastUpdated](#getdatelastupdated)|傳回的日期和時間的基底資料表基礎設計所做的最新變更`CDaoRecordset`物件。|  
|[CDaoRecordset::GetDefaultDBName](#getdefaultdbname)|傳回預設資料來源的名稱。|  
|[CDaoRecordset::GetDefaultSQL](#getdefaultsql)|呼叫以取得要執行的預設 SQL 字串。|  
|[CDaoRecordset::GetEditMode](#geteditmode)|傳回值，指出目前記錄的編輯功能的狀態。|  
|[CDaoRecordset::GetFieldCount](#getfieldcount)|傳回值，表示資料錄集中的欄位數目。|  
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|傳回資料錄集中的特定類型的欄位資訊。|  
|[CDaoRecordset::GetFieldValue](#getfieldvalue)|傳回資料錄集中的欄位的值。|  
|[CDaoRecordset::GetIndexCount](#getindexcount)|擷取基礎資料錄集的資料表中的索引數目。|  
|[CDaoRecordset::GetIndexInfo](#getindexinfo)|傳回各種索引的相關資訊。|  
|[CDaoRecordset::GetLastModifiedBookmark](#getlastmodifiedbookmark)|用來判斷最最近新增或更新記錄。|  
|[CDaoRecordset::GetLockingMode](#getlockingmode)|傳回值，表示在編輯期間就是作用中的鎖定類型。|  
|[CDaoRecordset::GetName](#getname)|傳回`CString`包含資料錄集的名稱。|  
|[CDaoRecordset::GetParamValue](#getparamvalue)|擷取目前儲存在基礎 DAOParameter 物件中的指定參數的值。|  
|[CDaoRecordset::GetPercentPosition](#getpercentposition)|傳回目前記錄的記錄總數的百分比的位置。|  
|[CDaoRecordset::GetRecordCount](#getrecordcount)|傳回資料錄集物件中存取的記錄數目。|  
|[CDaoRecordset::GetSQL](#getsql)|取得用來選取資料錄集的記錄的 SQL 字串。|  
|[CDaoRecordset::GetType](#gettype)|呼叫以判斷資料錄集類型︰ 資料表類型、 動態型別或快照集類型。|  
|[CDaoRecordset::GetValidationRule](#getvalidationrule)|傳回`CString`包含驗證資料輸入欄位的值。|  
|[CDaoRecordset::GetValidationText](#getvalidationtext)|擷取時，不符合驗證規則會顯示的文字。|  
|[CDaoRecordset::IsBOF](#isbof)|傳回非零，如果第一個資料錄之前已置於資料錄集。 沒有目前資料錄。|  
|[CDaoRecordset::IsDeleted](#isdeleted)|傳回非零，如果資料錄集位於已刪除的記錄。|  
|[CDaoRecordset::IsEOF](#iseof)|傳回非零，如果已位置之後的最後一個記錄的資料錄集。 沒有目前資料錄。|  
|[CDaoRecordset::IsFieldDirty](#isfielddirty)|傳回非零，如果目前的記錄中指定的欄位已變更。|  
|[CDaoRecordset::IsFieldNull](#isfieldnull)|傳回非零，如果目前的記錄中指定的欄位為 Null （具有任何值）。|  
|[CDaoRecordset::IsFieldNullable](#isfieldnullable)|傳回非零，如果目前的記錄中指定的欄位可以設定為 Null （具有任何值）。|  
|[CDaoRecordset::IsOpen](#isopen)|傳回非零值如果[開啟](#open)先前已經呼叫。|  
|[CDaoRecordset::Move](#move)|任一方向的目前資料錄來定位資料錄集為指定的記錄數。|  
|[CDaoRecordset::MoveFirst](#movefirst)|置於資料錄集的第一個記錄目前的記錄。|  
|[CDaoRecordset::MoveLast](#movelast)|目前的記錄置於資料錄集中的最後一筆記錄。|  
|[CDaoRecordset::MoveNext](#movenext)|置於資料錄集的下一個記錄目前的記錄。|  
|[CDaoRecordset::MovePrev](#moveprev)|置於資料錄集的上一個記錄目前的記錄。|  
|[Cdaorecordset:: Open](#open)|從資料表、 動態集或快照集建立新的資料錄集。|  
|[CDaoRecordset::Requery](#requery)|執行一次重新整理選取的資料錄的資料錄集的查詢。|  
|[CDaoRecordset::Seek](#seek)|尋找符合目前的索引並讓該記錄的目前記錄的指定的準則之索引的資料表類型資料錄集物件中的記錄。|  
|[CDaoRecordset::SetAbsolutePosition](#setabsoluteposition)|設定資料錄集物件的目前記錄的記錄數目。|  
|[CDaoRecordset::SetBookmark](#setbookmark)|資料錄集置於包含指定的書籤的記錄。|  
|[CDaoRecordset::SetCacheSize](#setcachesize)|設定值，指定包含要在本機快取從 ODBC 資料來源之資料的動態類型資料錄集中的記錄數目。|  
|[CDaoRecordset::SetCacheStart](#setcachestart)|設定值，指定要快取資料錄集中的第一筆記錄的書籤。|  
|[CDaoRecordset::SetCurrentIndex](#setcurrentindex)|設定索引的資料表類型資料錄集上呼叫。|  
|[CDaoRecordset::SetFieldDirty](#setfielddirty)|將目前記錄中指定的欄位標記為已變更。|  
|[CDaoRecordset::SetFieldNull](#setfieldnull)|設定指定之欄位的值為 Null （具有任何值） 是目前記錄中。|  
|[CDaoRecordset::SetFieldValue](#setfieldvalue)|資料錄集中設定欄位的值。|  
|[CDaoRecordset::SetFieldValueNull](#setfieldvaluenull)|設定為 Null 的資料錄集欄位的值。 （具有任何值）。|  
|[CDaoRecordset::SetLockingMode](#setlockingmode)|設定值，指出要置入效果，在編輯期間鎖定的類型。|  
|[CDaoRecordset::SetParamValue](#setparamvalue)|設定儲存在基礎 DAOParameter 物件中所指定參數的目前值|  
|[CDaoRecordset::SetParamValueNull](#setparamvaluenull)|設定目前的指定參數的值為 Null （具有任何值）。|  
|[CDaoRecordset::SetPercentPosition](#setpercentposition)|將目前記錄的位置設定為對應至資料錄集中的記錄總數的百分比表示的位置。|  
|[CDaoRecordset::Update](#update)|完成`AddNew`或**編輯**新增或編輯資料儲存在資料來源上的作業。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[M_bcheckcachefordirtyfields](#m_bcheckcachefordirtyfields)|包含旗標，指出是否欄位會自動標示為已變更。|  
|[CDaoRecordset::m_nFields](#m_nfields)|包含資料錄集類別中的欄位資料成員的數目和資料來源的資料錄集選取資料行數目。|  
|[CDaoRecordset::m_nParams](#m_nparams)|包含資料錄集類別中的參數資料成員的數目，與資料錄集的查詢中傳遞的參數數目|  
|[CDaoRecordset::m_pDAORecordset](#m_pdaorecordset)|基礎資料錄集物件的 DAO 介面指標。|  
|[CDaoRecordset::m_pDatabase](#m_pdatabase)|此結果集的來源資料庫。 包含一個指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件。|  
|[CDaoRecordset::m_strFilter](#m_strfilter)|包含用來建構 SQL 字串**其中**陳述式。|  
|[CDaoRecordset::m_strSort](#m_strsort)|包含用來建構 SQL 字串**ORDER BY**陳述式。|  
  
## <a name="remarks"></a>備註  
 稱為 「 資料錄集 」`CDaoRecordset`物件都在下列三種形式︰  
  
-   資料表類型的資料錄集代表可用來檢查、 加入、 變更或刪除單一資料庫資料表中記錄的基底資料表。  
  
-   動態類型資料錄集是可以有可更新的記錄查詢的結果。 這些資料錄集是一組可用來檢查、 加入、 變更或從基礎資料庫資料表或資料表刪除記錄的記錄。 動態類型資料錄集可包含從資料庫中的一個或多個資料表的欄位。  
  
-   快照集類型資料錄集是一組可用來尋找資料，或產生報表的資料錄的靜態複本。 這些資料錄集可以包含從資料庫中的一個或多個資料表的欄位，但無法更新。  
  
 資料錄集的每個表單都代表一組固定在開啟資料錄集時的記錄。 捲動資料錄集類型的資料表或動態類型的資料錄集內的記錄，其會反映之後開啟資料錄集時，其他使用者或應用程式中的其他資料錄集的記錄所做的變更。 （無法更新快照集類型的資料錄集）。您可以使用`CDaoRecordset`直接或衍生的應用程式特定資料錄集類別，從`CDaoRecordset`。 您可以︰  
  
-   捲動資料錄。  
  
-   設定索引，並使用資料錄快速尋找[搜尋](#seek)（資料表類型資料錄集只）。  
  
-   尋找根據字串比較的記錄: 「<",></",>\<="，"="」 > = 」，或 「 > 」 （動態類型和快照集類型資料錄集）。  
  
-   更新的記錄，並指定 （除了快照類型資料錄集） 的鎖定模式。  
  
-   篩選資料錄集，以限制它會從選取的可用資料來源的記錄。  
  
-   排序資料錄集。  
  
-   參數化的資料錄集的執行階段之前無法得知資訊來自訂其選項。  
  
 類別`CDaoRecordset`提供類似的類別介面`CRecordset`。 主要差異在於該類別`CDaoRecordset`透過資料存取物件 (DAO) 根據 OLE 存取資料。 類別`CRecordset`透過開放式資料庫連接 (ODBC) 和 ODBC 驅動程式存取該 DBMS DBMS。  
  
> [!NOTE]
>  DAO 資料庫類別所基礎開放式資料庫連接 (ODBC) 之 MFC 資料庫類別不同。 所有的 DAO 資料庫類別名稱有"CDao"前置詞。 您仍然可以使用 DAO 類別; 存取 ODBC 資料來源DAO 類別通常提供卓越的功能，因為它們專屬於 Microsoft Jet 資料庫引擎。  
  
 您可以使用`CDaoRecordset`直接或衍生自`CDaoRecordset`。 若要使用資料錄集類別，在任一情況下，開啟資料庫，並建構資料錄集物件，傳遞建構函式的指標，您`CDaoDatabase`物件。 您也可以建構`CDaoRecordset`物件，並可讓 MFC 建立暫存`CDaoDatabase`為您的物件。 然後呼叫資料錄集的[開啟](#open)成員函式，指定物件資料表類型的資料錄集、 動態類型資料錄集或快照集類型的資料錄集。 呼叫**開啟**從資料庫選取資料，並擷取第一筆記錄。  
  
 使用物件的成員函式和資料成員來捲動資料錄，並加以操作。 可用的作業取決於物件是資料表類型的資料錄集、 動態類型資料錄集或快照集類型的資料錄集，以及它是否可更新或唯讀狀態，這取決於資料庫或開放式資料庫連接 (ODBC) 資料來源的功能。 若要重新整理記錄可能會變更或自**開啟**呼叫，呼叫物件的[Requery](#requery)成員函式。 呼叫物件的**關閉**成員函式，並在您完成時終結物件。  
  
 `CDaoRecordset`DAO 資料錄欄位交換 (DFX) 來支援讀取和更新的記錄欄位會使用透過型別安全的 c + + 成員您`CDaoRecordset`或`CDaoRecordset`-衍生的類別。 您也可以實作在資料庫中的資料行的動態繫結，而不需使用 DFX 機制使用[GetFieldValue](#getfieldvalue)和[SetFieldValue](#setfieldvalue)。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 資料錄集物件 」。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDaoRecordset`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdao.h  
  
##  <a name="addnew"></a>CDaoRecordset::AddNew  
 呼叫此成員函式，將新記錄新增至資料表類型或動態類型的資料錄集。  
  
```  
virtual void AddNew();
```  
  
### <a name="remarks"></a>備註  
 記錄的欄位是一開始是 Null。 (在資料庫術語中，為 Null 」 有任何值 」 的方式，不與相同**NULL** c + + 中。)若要完成此作業，您必須呼叫[更新](#update)成員函式。 **更新**將變更儲存至資料來源。  
  
> [!CAUTION]
>  如果您編輯記錄，然後捲動至另一筆記錄，而不需呼叫**更新**，您的變更都會遺失，而不發出警告。  
  
 如果您新增記錄至動態類型的資料錄集藉由呼叫[AddNew](#addnew)，記錄會顯示在資料錄集，其中可看見任何新的基礎資料表中包含`CDaoRecordset`物件。  
  
 新記錄的位置取決於資料錄集類型︰  
  
-   動態類型中不保證資料錄集，插入新記錄的位置。 基於效能和並行存取與 Microsoft Jet 3.0 變更這個行為。 如果您的目標是要使新加入的記錄目前的記錄，取得上次修改的資料錄的書籤，並移至該書籤︰  
  
 [!code-cpp[NVC_MFCDatabase #&1;](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]  
  
-   資料表類型的資料錄集的指定索引，其適當的位置，在排序次序中會傳回記錄。 如果尚未指定任何索引，新的記錄會傳回資料錄集的結尾。  
  
 目前在使用之前的記錄`AddNew`保持最新。 如果您要變更新的記錄，且資料錄集支援書籤，呼叫[SetBookmark](#setbookmark)到基本的 DAO 資料錄集物件的 LastModified 屬性設定值所識別的書籤。 這是用於判斷加入一筆記錄中的計數器 （自動遞增） 欄位的值。 如需詳細資訊，請參閱[GetLastModifiedBookmark](#getlastmodifiedbookmark)。  
  
 如果資料庫支援交易，您可以讓您`AddNew`呼叫交易的一部分。 如需有關交易的詳細資訊，請參閱類別[CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)。 請注意，您應該呼叫[CDaoWorkspace::BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans)之前，先呼叫`AddNew`。  
  
 您不能呼叫`AddNew`資料錄集的[開啟](#open)尚未呼叫成員函式。 A`CDaoException`會擲回，如果您呼叫`AddNew`以無法附加資料錄集。 您可以判斷資料錄集是否可更新，藉由呼叫[CanAppend](#canappend)。  
  
 Framework 標記變更欄位資料成員，以確保它們會寫入資料來源上的資料錄的 DAO 資料錄欄位交換 (DFX) 機制。 一般來說，變更欄位的值欄位已變更會自動設定，因此您很少需要呼叫[SetFieldDirty](#setfielddirty) ，但是您有時候可能想要確保資料行將會明確地更新或插入不論什麼值是欄位資料成員中。 DFX 機制也會運用使用**虛擬 NULL**。 如需詳細資訊，請參閱[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
 如果未使用的雙重緩衝機制，然後變更欄位的值不會自動設定欄位為已變更。 在此情況下，它必須明確地設定欄位已變更。 中所包含的旗標[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制這項自動欄位檢查。  
  
> [!NOTE]
>  如果雙重緩衝的記錄 （也就是自動欄位啟用），則呼叫`CancelUpdate`會還原至之前的值的成員變數`AddNew`或**編輯**呼叫。  
  
 如需相關資訊，請參閱 「 AddNew 方法 」、 「 CancelUpdate 方法 」、 「 LastModified 屬性 」 和 「 EditMode 屬性 」 DAO 說明中的主題。  
  
##  <a name="canappend"></a>CDaoRecordset::CanAppend  
 呼叫此成員函式，以判斷是否先前開啟的資料錄集可讓您新增新的記錄，藉由呼叫[AddNew](#addnew)成員函式。  
  
```  
BOOL CanAppend() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果資料錄集允許加入新資料錄。否則為 0。 `CanAppend`如果您開啟為唯讀資料錄集時，就會傳回 0。  
  
### <a name="remarks"></a>備註  
 如需相關資訊，請參閱主題 DAO 說明中的 「 附加方法 」。  
  
##  <a name="canbookmark"></a>CDaoRecordset::CanBookmark  
 呼叫此成員函式，以判斷是否先前開啟的資料錄集可讓您個別地將標記記錄使用書籤。  
  
```  
BOOL CanBookmark();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果資料錄集支援書籤，否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您使用 Microsoft Jet 資料庫引擎資料表完全為基礎的資料錄集，可以使用書籤除了上標示為順向捲動資料錄集的快照集類型資料錄集。 其他資料庫產品 （外部的 ODBC 資料來源） 可能不支援書籤。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 Bookmarkable 屬性 」。  
  
##  <a name="cancelupdate"></a>CDaoRecordset::CancelUpdate  
 `CancelUpdate`成員函式會取消任何暫止的更新，因為[編輯](#edit)或[AddNew](#addnew)作業。  
  
```  
virtual void CancelUpdate();
```  
  
### <a name="remarks"></a>備註  
 例如，如果應用程式呼叫**編輯**或`AddNew`成員函式未呼叫和[更新](#update)，`CancelUpdate`取消之後所做的變更**編輯**或`AddNew`呼叫。  
  
> [!NOTE]
>  如果雙重緩衝的記錄 （也就是自動欄位啟用），則呼叫`CancelUpdate`會還原至之前的值的成員變數`AddNew`或**編輯**呼叫。  
  
 如果沒有任何**編輯**或`AddNew`作業暫止、`CancelUpdate`造成 MFC 擲回例外狀況。 呼叫[GetEditMode](#geteditmode)成員函式來判斷是否可以取消暫止作業。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 CancelUpdate 方法 」。  
  
##  <a name="canrestart"></a>CDaoRecordset::CanRestart  
 呼叫此成員函式，以判斷資料錄集是否允許重新啟動其查詢 （若要更新其記錄），藉由呼叫**Requery**成員函式。  
  
```  
BOOL CanRestart();
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零**Requery**可以呼叫來執行資料錄集的查詢，否則為 0。  
  
### <a name="remarks"></a>備註  
 不支援資料表類型的資料錄集**Requery**。  
  
 如果**Requery**是不受支援，呼叫[關閉](#close)然後[開啟](#open)重新整理資料。 您可以呼叫**Requery**來更新資料錄集物件的基礎參數查詢後已經變更的參數值。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 可重新啟動屬性 」。  
  
##  <a name="canscroll"></a>CDaoRecordset::CanScroll  
 呼叫此成員函式，以判斷是否允許捲動資料錄集。  
  
```  
BOOL CanScroll() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果您可以捲動資料錄，否則為 0，非零值。  
  
### <a name="remarks"></a>備註  
 如果您呼叫[開啟](#open)與**dbForwardOnly**，只可以向前捲動資料錄集。  
  
 如需相關資訊，請參閱主題 < 目前記錄指標使用 DAO 定位 」 DAO 說明中。  
  
##  <a name="cantransact"></a>CDaoRecordset::CanTransact  
 呼叫此成員函式，以判斷資料錄集是否允許交易。  
  
```  
BOOL CanTransact();
```  
  
### <a name="return-value"></a>傳回值  
 如果基礎資料來源支援交易，否則為 0，非零值。  
  
### <a name="remarks"></a>備註  
 如需相關資訊，請參閱主題 DAO 說明中的 「 交易屬性 」。  
  
##  <a name="canupdate"></a>CDaoRecordset::CanUpdate  
 呼叫此成員函式，以判斷是否可以更新資料錄集。  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果可以更新資料錄集 （新增、 更新和刪除記錄），否則為 0。  
  
### <a name="remarks"></a>備註  
 資料錄集可能是唯讀屬性，如果基礎資料來源是唯讀，或您指定**dbReadOnly**的`nOptions`何時呼叫[開啟](#open)資料錄集。  
  
 如需相關資訊，請參閱主題 < AddNew 方法 」、 「 編輯方法 」、 「 刪除方法 」、 「 更新方法 」 和 DAO 說明中的 「 可更新屬性 」。  
  
##  <a name="cdaorecordset"></a>CDaoRecordset::CDaoRecordset  
 建構 `CDaoRecordset` 物件。  
  
```  
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pDatabase`  
 包含一個指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件或值**NULL**。 如果不是**NULL**和`CDaoDatabase`物件的**開啟**尚未呼叫成員函式將它連接到資料來源、 資料錄集嘗試為您開啟在它自己[開啟](#open)呼叫。 如果您傳遞**NULL**、`CDaoDatabase`物件建構及連線，讓您使用您指定如果您衍生您的資料錄集類別，從資料來源資訊`CDaoRecordset`。  
  
### <a name="remarks"></a>備註  
 您可以使用`CDaoRecordset`直接衍生從應用程式特定類別或`CDaoRecordset`。 您可以使用類別來衍生資料錄集類別。  
  
> [!NOTE]
>  如果衍生`CDaoRecordset`類別中，您的衍生類別必須提供自己的建構函式。 在衍生類別的建構函式，呼叫建構函式`CDaoRecordset::CDaoRecordset`，沿著適當的參數傳遞給它。  
  
 傳遞**NULL**到您的資料錄集建構函式有`CDaoDatabase`物件建構，並為您自動連接。 這是不需要您建構，以及連線的有用捷徑`CDaoDatabase`之前建構資料錄集物件。 如果`CDaoDatabase`物件未開啟， [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)物件也會建立以供您使用的預設工作區。 如需詳細資訊，請參閱[CDaoDatabase::CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase)。  
  
##  <a name="close"></a>CDaoRecordset::Close  
 關閉`CDaoRecordset`物件會將它移除相關聯的資料庫中開啟資料錄集的集合。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 因為**關閉**不會終結`CDaoRecordset`物件時，您可以藉由呼叫重複使用該物件**開啟**上相同的資料來源或不同的資料來源。  
  
 所有暫止[AddNew](#addnew)或[編輯](#edit)陳述式會取消，且會回復所有暫止的交易。 如果您想要保留暫止的新增或編輯，呼叫[更新](#update)之前先呼叫**關閉**以每個資料錄集。  
  
 您可以呼叫**開啟**，然後再次呼叫**關閉**。 這可讓您重複使用資料錄集物件。 更好的替代方式是呼叫[Requery](#requery)、 的話。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 關閉方法 」。  
  
##  <a name="delete"></a>CDaoRecordset::Delete  
 呼叫此成員函式來刪除目前開啟的動態類型或類型的資料表資料錄集物件中的記錄。  
  
```  
virtual void Delete();
```  
  
### <a name="remarks"></a>備註  
 之後成功刪除資料錄集的欄位資料成員設為 Null 值，而且您必須明確呼叫其中一個資料錄集巡覽成員函式 ([移動](#move)，[搜尋](#seek)， [SetBookmark](#setbookmark)等等) 以將之移除刪除的記錄。 當您刪除記錄從資料錄集時，必須有目前的記錄資料錄集才能呼叫**刪除**; 否則 MFC 會擲回例外狀況。  
  
 **刪除**移除目前的記錄，並使其無法存取。 雖然您無法編輯，或使用已刪除的記錄，但它保持最新。 一旦您移到另一筆記錄，但您不能刪除的記錄目前一次。  
  
> [!CAUTION]
>  資料錄集必須是可更新，且必須有有效的記錄資料錄集中目前當您呼叫**刪除**。 例如，如果您刪除記錄，但不是會捲動到新的記錄才能呼叫**刪除**，**刪除**會擲回[CDaoException](../../mfc/reference/cdaoexception-class.md)。  
  
 如果您使用交易，而且您呼叫，您可以取消刪除記錄[CDaoWorkspace::Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback)成員函式。 如果基底資料表的主資料表中串聯刪除關聯性，刪除目前的記錄可能也會刪除外部索引資料表中的一個或多個記錄。 如需詳細資訊，請參閱 DAO 說明定義 「 串聯刪除 」。  
  
 不同於`AddNew`和**編輯**，呼叫**刪除**後面不是呼叫**更新**。  
  
 如需相關資訊，請參閱主題 < AddNew 方法 」、 「 編輯方法 」、 「 刪除方法 」、 「 更新方法 」 和 DAO 說明中的 「 可更新屬性 」。  
  
##  <a name="dofieldexchange"></a>CDaoRecordset::DoFieldExchange  
 架構會呼叫此成員函式自動之間交換資料的資料錄集物件的欄位資料成員和對應的資料行的資料來源上目前的記錄。  
  
```  
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```  
  
### <a name="parameters"></a>參數  
 `pFX`  
 包含一個指向`CDaoFieldExchange`物件。 架構會已經設定這個物件指定欄位的交換作業的內容。  
  
### <a name="remarks"></a>備註  
 如果有的話，資料錄集的選取範圍的 SQL 陳述式字串中的參數替代符號，它也繫結參數資料成員。 交換欄位資料，呼叫 DAO 資料錄欄位交換 (DFX)，可以雙向運作︰ 從資料來源上的記錄欄位的資料錄集物件的欄位資料成員和資料來源的資料錄集物件上的記錄。 如果您要動態繫結資料行，您不需要實作`DoFieldExchange`。  
  
 唯一的動作，您通常必須採取實作`DoFieldExchange`對於衍生資料錄集類別是使用類別建立類別，並指定欄位資料成員的名稱和資料型別。 您也可能會寫入指定的參數資料成員的類別精靈加入程式碼。 如果所有欄位都是動態繫結，此函式將會在非作用中，除非您指定的參數資料成員。  
  
 當您宣告類別衍生的資料錄集類別時，精靈會撰寫的覆寫`DoFieldExchange`，它會類似下列範例︰  
  
 [!code-cpp[NVC_MFCDatabase #&2;](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]  
  
##  <a name="edit"></a>CDaoRecordset::Edit  
 呼叫此成員函式允許您變更目前的記錄。  
  
```  
virtual void Edit();
```  
  
### <a name="remarks"></a>備註  
 一旦您呼叫**編輯**成員函式，目前的記錄欄位所做的變更會複製到複製緩衝區。 記錄進行必要的變更之後，請呼叫**更新**以儲存變更。 **編輯**儲存資料錄集的資料成員的值。 如果您呼叫**編輯**，進行變更，然後呼叫**編輯**同樣地，記錄的值會還原至原先的前面**編輯**呼叫。  
  
> [!CAUTION]
>  如果您編輯記錄，然後再執行任何作業，將移至另一筆記錄，但是未先呼叫**更新**，您的變更都會遺失，而不發出警告。 此外，如果您關閉資料錄集或父資料庫，則會捨棄您編輯過的記錄而不發出警告。  
  
 在某些情況下，您可能想要更新資料行，所以 Null （包含任何資料）。 若要這樣做，請呼叫`SetFieldNull`參數與**TRUE**標示的欄位為 Null; 這也會造成要更新的資料行。 如果您想要寫入至資料來源，即使沒有變更其值，請呼叫的欄位`SetFieldDirty`參數與**TRUE**。 就算欄位具有 Null 值。  
  
 Framework 標記變更欄位資料成員，以確保它們會寫入資料來源上的資料錄的 DAO 資料錄欄位交換 (DFX) 機制。 一般來說，變更欄位的值欄位已變更會自動設定，因此您很少需要呼叫[SetFieldDirty](#setfielddirty) ，但是您有時候可能想要確保資料行將會明確地更新或插入不論什麼值是欄位資料成員中。 DFX 機制也會運用使用**虛擬 NULL**。 如需詳細資訊，請參閱[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
 如果未使用的雙重緩衝機制，然後變更欄位的值不會自動設定欄位為已變更。 在此情況下，它必須明確地設定欄位已變更。 中所包含的旗標[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制這項自動欄位檢查。  
  
 當資料錄集物件要以保守模式鎖定在多使用者環境中時，記錄就會保持鎖定的時間**編輯**更新已完成之前使用。 如果在樂觀地鎖定資料錄集，記錄會鎖定及更新資料庫中之前，相較於預先編輯的記錄。 如果記錄有所變更，因為您呼叫**編輯**、**更新**作業將會失敗，而且 MFC 擲回例外狀況。 您可以變更的鎖定模式`SetLockingMode`。  
  
> [!NOTE]
>  在外部資料庫格式，例如 ODBC 和可安裝的 ISAM 一律使用開放式鎖定。  
  
 目前的記錄會保留目前在您呼叫後**編輯**。 若要呼叫**編輯**，必須是目前的記錄。 如果沒有目前的記錄或資料錄集未參考到開啟的資料表類型或動態類型資料錄集物件，就會發生例外狀況。 呼叫**編輯**造成`CDaoException`擲回下列條件︰  
  
-   沒有目前資料錄。  
  
-   資料錄集的資料庫處於唯讀狀態。  
  
-   記錄中的任何欄位不是可更新。  
  
-   資料錄集的資料庫已由其他使用者開啟進行獨佔使用。  
  
-   另一位使用者已鎖定頁面包含您的記錄。  
  
 如果資料來源支援交易，您可以將**編輯**呼叫交易的一部分。 請注意，您應該呼叫`CDaoWorkspace::BeginTrans`之前，先呼叫**編輯**並開啟資料錄集之後。 也請注意，呼叫`CDaoWorkspace::CommitTrans`不呼叫取代**更新**完成**編輯**作業。 如需有關交易的詳細資訊，請參閱類別`CDaoWorkspace`。  
  
 如需相關資訊，請參閱主題 < AddNew 方法 」、 「 編輯方法 」、 「 刪除方法 」、 「 更新方法 」 和 DAO 說明中的 「 可更新屬性 」。  
  
##  <a name="fillcache"></a>CDaoRecordset::FillCache  
 呼叫此成員函式快取的指定從資料錄集的記錄筆數。  
  
```  
void FillCache(
    long* pSize = NULL,  
    COleVariant* pBookmark = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pSize`  
 指定要填滿快取中的資料列數目。 如果您省略這個參數，值取決於基礎的 DAO 物件的 CacheSize 屬性設定。  
  
 `pBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md)指定書籤。 快取會從這個書籤所指示的記錄開始填滿。 如果您省略這個參數時，會自動填入從基礎的 DAO 物件的 CacheStart 屬性所指定的記錄快取。  
  
### <a name="remarks"></a>備註  
 快取改善擷取，或會提取資料，從遠端伺服器的應用程式的效能。 快取是在保存最新的資料，系統可能會要求一次在執行應用程式假設從伺服器擷取資料的本機記憶體中的空間。 要求資料時，Microsoft Jet 資料庫引擎的快取資料會先檢查而不是從伺服器所花費的時間加以擷取。 使用非 ODBC 資料來源上的快取的資料並無作用，因為資料不會儲存在快取。  
  
 您不必等到快取填滿記錄時加以擷取，您可以明確地填入快取隨時藉由呼叫`FillCache`成員函式。 這是更快的方法來填滿快取，因為`FillCache`提取多個資料錄一次而不是一個一次。 例如，顯示每個細分的記錄時，可以讓您的應用程式呼叫`FillCache`擷取記錄的下一步的細分。  
  
 使用資料錄集物件存取任何 ODBC 資料庫可以有本機快取。 若要建立快取，請開啟遠端資料來源的資料錄集物件，然後呼叫`SetCacheSize`和`SetCacheStart`資料錄集的成員函式。 如果`lSize`和*lBookmark*建立部分或全部超出所指定之範圍的範圍`SetCacheSize`和`SetCacheStart`，這個範圍之外的資料錄集的部分會被忽略，不會載入到快取。 如果`FillCache`要求比詳細的記錄會保留在遠端資料來源、 擷取剩餘的記錄，並擲回任何例外狀況。  
  
 從快取中的記錄不會反映所做的變更同時來源資料的其他使用者。  
  
 `FillCache`會擷取尚未快取的記錄。 若要強制更新的所有快取的資料，請呼叫`SetCacheSize`成員函式`lSize`參數等於 0，呼叫`SetCacheSize`再`lSize`參數等於快取大小您原先要求，並再呼叫`FillCache`。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 FillCache 方法 」。  
  
##  <a name="find"></a>CDaoRecordset::Find  
 呼叫此成員函式中使用比較運算子的動態或快照集類型資料錄集找出特定的字串。  
  
```  
virtual BOOL Find(
    long lFindType,  
    LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>參數  
 *lFindType*  
 值，表示尋找作業所需的類型。 可能值為：  
  
- **AFX_DAO_NEXT**尋找下一個比對字串的位置。  
  
- **AFX_DAO_PREV**尋找上一個比對字串的位置。  
  
- **AFX_DAO_FIRST**尋找比對字串的第一個位置。  
  
- **AFX_DAO_LAST**尋找比對字串的最後一個位置。  
  
 `lpszFilter`  
 字串運算式 (例如**其中**子句中的 SQL 陳述式，但沒有一字**其中**) 用來尋找資料錄。 例如:   
  
 [!code-cpp[NVC_MFCDatabase #&3;](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]  
  
### <a name="return-value"></a>傳回值  
 非零，如果相符的記錄找不到，否則為 0。  
  
### <a name="remarks"></a>備註  
 您可以找到第一個下, 一步上, 一個或最後一個執行個體的字串。 **尋找**是虛擬函式，因此您可以覆寫它，並加入您自己的實作。 `FindFirst`， `FindLast`， `FindNext`，和`FindPrev`成員函式呼叫**尋找**成員函式，因此您可以使用**尋找**來控制所有的尋找作業的行為。  
  
 若要尋找一筆記錄資料表類型的資料錄集，請呼叫[搜尋](#seek)成員函式。  
  
> [!TIP]
>  小一組記錄，更有效的**尋找**會。 一般而言，以及特別是在 ODBC 資料，最好是建立新的查詢來擷取您要的記錄。  
  
 如需相關資訊，請參閱本主題 「 FindFirst，FindLast FindNext，FindPrevious 方法 」 DAO 說明。  
  
##  <a name="findfirst"></a>CDaoRecordset::FindFirst  
 呼叫此成員函式，來尋找符合指定的條件的第一個記錄。  
  
```  
BOOL FindFirst(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>參數  
 `lpszFilter`  
 字串運算式 (例如**其中**子句中的 SQL 陳述式，但沒有一字**其中**) 用來尋找資料錄。  
  
### <a name="return-value"></a>傳回值  
 非零，如果相符的記錄找不到，否則為 0。  
  
### <a name="remarks"></a>備註  
 `FindFirst`成員函式開始搜尋的起點的資料錄集，並搜尋至資料錄集的結尾。  
  
 如果您想要包含所有您的搜尋 （不只是那些符合特定條件） 中的記錄所使用的是其中一項移動作業來記錄間移動。 若要尋找一筆記錄資料表類型的資料錄集，請呼叫`Seek`成員函式。  
  
 如果沒有找到符合準則的記錄，目前的記錄指標是不明，和`FindFirst`傳回零。 如果資料錄集包含多筆記錄符合準則，`FindFirst`找出第一次出現，`FindNext`找出下一個項目，依此類推。  
  
> [!CAUTION]
>  如果您編輯目前的記錄，請務必將變更儲存藉由呼叫**更新**成員函式，再移至另一筆記錄。 如果您移到另一筆記錄而未更新，您的變更會遺失，而不發出警告。  
  
 **尋找**成員函式搜尋的位置，以及下表中指定的方向︰  
  
|尋找作業|開始|搜尋方向|  
|---------------------|-----------|----------------------|  
|`FindFirst`|資料錄集的開頭|資料錄集的結尾|  
|`FindLast`|資料錄集的結尾|資料錄集的開頭|  
|`FindNext`|目前的記錄|資料錄集的結尾|  
|**FindPrevious**|目前的記錄|資料錄集的開頭|  
  
> [!NOTE]
>  當您呼叫`FindLast`，Microsoft Jet 資料庫引擎完整填入資料錄集才能開始搜尋，如果這不已經完成。 第一次搜尋可能花費超過後續的搜尋。  
  
 使用其中一種尋找作業不是呼叫相同**MoveFirst**或`MoveNext`，不過，這只是讓第一個或下一個記錄目前沒有指定的條件。 您可以依照移動作業的尋找作業。  
  
 使用尋找作業時，請記住下列︰  
  
-   如果**尋找**傳回非零值，未定義目前的記錄。 在此情況下，您必須將目前資料錄指標至有效的記錄。  
  
-   您不能使用順向捲動快照類型資料錄集的尋找作業。  
  
-   您應該使用美國日期格式 （月-日-年） 當您搜尋欄位中包含的日期，即使您不想要使用 Microsoft Jet 資料庫引擎; 美國版否則，相符的記錄可能找不到。  
  
-   當使用 ODBC 資料庫和大型的動態集，您可能會發現，使用 尋找作業變慢時，尤其是使用大型資料錄集。 您可以使用 SQL 查詢，以改善效能與自訂**ORDERBY**或**其中**子句、 參數查詢或**CDaoQuerydef**擷取指定的索引的記錄的物件。  
  
 如需相關資訊，請參閱本主題 「 FindFirst，FindLast FindNext，FindPrevious 方法 」 DAO 說明。  
  
##  <a name="findlast"></a>CDaoRecordset::FindLast  
 呼叫此成員函式，來尋找符合指定的條件的最後一筆記錄。  
  
```  
BOOL FindLast(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>參數  
 `lpszFilter`  
 字串運算式 (例如**其中**子句中的 SQL 陳述式，但沒有一字**其中**) 用來尋找資料錄。  
  
### <a name="return-value"></a>傳回值  
 非零，如果相符的記錄找不到，否則為 0。  
  
### <a name="remarks"></a>備註  
 `FindLast`成員函式開始搜尋的資料錄集結尾並向資料錄集的起始處向後搜尋。  
  
 如果您想要包含所有您的搜尋 （不只是那些符合特定條件） 中的記錄所使用的是其中一項移動作業來記錄間移動。 若要尋找一筆記錄資料表類型的資料錄集，請呼叫`Seek`成員函式。  
  
 如果沒有找到符合準則的記錄，目前的記錄指標是不明，和`FindLast`傳回零。 如果資料錄集包含多筆記錄符合準則，`FindFirst`找出第一次出現，`FindNext`找出下一個項目之後第一個項目，依此類推。  
  
> [!CAUTION]
>  如果您編輯目前的記錄，請確定您儲存變更，藉由呼叫**更新**成員函式，再移至另一筆記錄。 如果您移到另一筆記錄而未更新，您的變更會遺失，而不發出警告。  
  
 使用其中一種尋找作業不是呼叫相同**MoveFirst**或`MoveNext`，不過，這只是讓第一個或下一個記錄目前沒有指定的條件。 您可以依照移動作業的尋找作業。  
  
 使用尋找作業時，請記住下列︰  
  
-   如果**尋找**傳回非零值，未定義目前的記錄。 在此情況下，您必須將目前資料錄指標至有效的記錄。  
  
-   您不能使用順向捲動快照類型資料錄集的尋找作業。  
  
-   您應該使用美國日期格式 （月-日-年） 當您搜尋欄位中包含的日期，即使您不想要使用 Microsoft Jet 資料庫引擎; 美國版否則，相符的記錄可能找不到。  
  
-   當使用 ODBC 資料庫和大型的動態集，您可能會發現，使用 尋找作業變慢時，尤其是使用大型資料錄集。 您可以使用 SQL 查詢，以改善效能與自訂**ORDERBY**或**其中**子句、 參數查詢或**CDaoQuerydef**擷取指定的索引的記錄的物件。  
  
 如需相關資訊，請參閱本主題 「 FindFirst，FindLast FindNext，FindPrevious 方法 」 DAO 說明。  
  
##  <a name="findnext"></a>CDaoRecordset::FindNext  
 呼叫此成員函式，來尋找符合指定的條件下一筆記錄。  
  
```  
BOOL FindNext(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>參數  
 `lpszFilter`  
 字串運算式 (例如**其中**子句中的 SQL 陳述式，但沒有一字**其中**) 用來尋找資料錄。  
  
### <a name="return-value"></a>傳回值  
 非零，如果相符的記錄找不到，否則為 0。  
  
### <a name="remarks"></a>備註  
 `FindNext`成員函式開始搜尋在目前的記錄，並搜尋至資料錄集的結尾。  
  
 如果您想要包含所有您的搜尋 （不只是那些符合特定條件） 中的記錄所使用的是其中一項移動作業來記錄間移動。 若要尋找一筆記錄資料表類型的資料錄集，請呼叫`Seek`成員函式。  
  
 如果沒有找到符合準則的記錄，目前的記錄指標是不明，和`FindNext`傳回零。 如果資料錄集包含多筆記錄符合準則，`FindFirst`找出第一次出現，`FindNext`找出下一個項目，依此類推。  
  
> [!CAUTION]
>  如果您編輯目前的記錄，請確定您儲存變更，藉由呼叫**更新**成員函式，再移至另一筆記錄。 如果您移到另一筆記錄而未更新，您的變更會遺失，而不發出警告。  
  
 使用其中一種尋找作業不是呼叫相同**MoveFirst**或`MoveNext`，不過，這只是讓第一個或下一個記錄目前沒有指定的條件。 您可以依照移動作業的尋找作業。  
  
 使用尋找作業時，請記住下列︰  
  
-   如果**尋找**傳回非零值，未定義目前的記錄。 在此情況下，您必須將目前資料錄指標至有效的記錄。  
  
-   您不能使用順向捲動快照類型資料錄集的尋找作業。  
  
-   您應該使用美國日期格式 （月-日-年） 當您搜尋欄位中包含的日期，即使您不想要使用 Microsoft Jet 資料庫引擎; 美國版否則，相符的記錄可能找不到。  
  
-   當使用 ODBC 資料庫和大型的動態集，您可能會發現，使用 尋找作業變慢時，尤其是使用大型資料錄集。 您可以使用 SQL 查詢，以改善效能與自訂**ORDERBY**或**其中**子句、 參數查詢或**CDaoQuerydef**擷取指定的索引的記錄的物件。  
  
 如需相關資訊，請參閱本主題 「 FindFirst，FindLast FindNext，FindPrevious 方法 」 DAO 說明。  
  
##  <a name="findprev"></a>CDaoRecordset::FindPrev  
 呼叫此成員函式，來尋找符合指定的條件的上一個記錄。  
  
```  
BOOL FindPrev(LPCTSTR lpszFilter);
```  
  
### <a name="parameters"></a>參數  
 `lpszFilter`  
 字串運算式 (例如**其中**子句中的 SQL 陳述式，但沒有一字**其中**) 用來尋找資料錄。  
  
### <a name="return-value"></a>傳回值  
 非零，如果相符的記錄找不到，否則為 0。  
  
### <a name="remarks"></a>備註  
 `FindPrev`成員函式開始搜尋在目前的記錄，並向資料錄集的起始處會向後搜尋。  
  
 如果您想要包含所有您的搜尋 （不只是那些符合特定條件） 中的記錄所使用的是其中一項移動作業來記錄間移動。 若要尋找一筆記錄資料表類型的資料錄集，請呼叫`Seek`成員函式。  
  
 如果沒有找到符合準則的記錄，目前的記錄指標是不明，和`FindPrev`傳回零。 如果資料錄集包含多筆記錄符合準則，`FindFirst`找出第一次出現，`FindNext`找出下一個項目，依此類推。  
  
> [!CAUTION]
>  如果您編輯目前的記錄，請確定您儲存變更，藉由呼叫**更新**成員函式，再移至另一筆記錄。 如果您移到另一筆記錄而未更新，您的變更會遺失，而不發出警告。  
  
 使用其中一種尋找作業不是呼叫相同**MoveFirst**或`MoveNext`，不過，這只是讓第一個或下一個記錄目前沒有指定的條件。 您可以依照移動作業的尋找作業。  
  
 使用尋找作業時，請記住下列︰  
  
-   如果**尋找**傳回非零值，未定義目前的記錄。 在此情況下，您必須將目前資料錄指標至有效的記錄。  
  
-   您不能使用順向捲動快照類型資料錄集的尋找作業。  
  
-   您應該使用美國日期格式 （月-日-年） 當您搜尋欄位中包含的日期，即使您不想要使用 Microsoft Jet 資料庫引擎; 美國版否則，相符的記錄可能找不到。  
  
-   當使用 ODBC 資料庫和大型的動態集，您可能會發現，使用 尋找作業變慢時，尤其是使用大型資料錄集。 您可以使用 SQL 查詢，以改善效能與自訂**ORDERBY**或**其中**子句、 參數查詢或**CDaoQuerydef**擷取指定的索引的記錄的物件。  
  
 如需相關資訊，請參閱本主題 「 FindFirst，FindLast FindNext，FindPrevious 方法 」 DAO 說明。  
  
##  <a name="getabsoluteposition"></a>CDaoRecordset::GetAbsolutePosition  
 傳回資料錄集物件的目前記錄的記錄數目。  
  
```  
long GetAbsolutePosition();
```  
  
### <a name="return-value"></a>傳回值  
 從 0 到資料錄集中的記錄數目的整數。 對應至目前資料錄的資料錄集中的序數位置。  
  
### <a name="remarks"></a>備註  
 AbsolutePosition 屬性值之基礎的 DAO 物件的以零為起始。設定為 0，指的是資料錄集的第一個記錄。 您可以判斷資料錄集填入記錄數目，藉由呼叫[GetRecordCount](#getrecordcount)。 呼叫`GetRecordCount`可能需要一些時間，因為它必須存取所有的記錄，來判斷計數。  
  
 如果沒有目前資料錄，做為資料錄集時，沒有記錄時，會傳回 1。 刪除目前的記錄時，如果沒有定義 AbsolutePosition 屬性值，和 MFC 擲回例外狀況，如果它參考。 動態類型資料錄集，對於新的記錄會加入至序列的結尾。  
  
> [!NOTE]
>  這個屬性不是要做為代理的記錄數目。 書籤依然是建議的方法來保留並傳回指定的位置，而且是目前資料錄定位在所有類型的資料錄集物件的唯一方式。 特別是，指定記錄的位置時，變更會刪除它之前的記錄。 另外還有指定的記錄都有相同的絕對位置，如果因為無法保證除非則會以 SQL 陳述式來建立資料錄集內的個別記錄的順序重新重新建立資料錄集不保證**ORDERBY**子句。  
  
> [!NOTE]
>  此成員函式是僅適用於動態類型和快照集類型資料錄集。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 AbsolutePosition 屬性 」。  
  
##  <a name="getbookmark"></a>CDaoRecordset::GetBookmark  
 呼叫此成員函式，以取得特定的資料記錄中的書籤值。  
  
```  
COleVariant GetBookmark();
```  
  
### <a name="return-value"></a>傳回值  
 傳回值，表示目前資料錄的書籤。  
  
### <a name="remarks"></a>備註  
 當建立或開啟資料錄集物件時，其記錄的每個已經有唯一的書籤支援它們。 呼叫`CanBookmark`，判斷資料錄集是否支援書籤。  
  
 您可以藉由指定的書籤的值來儲存目前資料錄的書籤`COleVariant`物件。 若要快速回到該記錄在任何時候移動到不同的記錄之後，呼叫`SetBookmark`具有參數的值對應`COleVariant`物件。  
  
> [!NOTE]
>  呼叫[Requery](#requery)變更 DAO 書籤。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 書籤屬性 」。  
  
##  <a name="getcachesize"></a>CDaoRecordset::GetCacheSize  
 呼叫此成員函式，以取得快取的記錄數目。  
  
```  
long GetCacheSize();
```  
  
### <a name="return-value"></a>傳回值  
 值，指定包含要在本機快取從 ODBC 資料來源之資料的動態類型資料錄集中的記錄數目。  
  
### <a name="remarks"></a>備註  
 資料快取改善從遠端伺服器透過動態類型資料錄集物件中擷取資料的應用程式的效能。 快取在本機記憶體中保存最近從伺服器擷取的資料，系統會要求一次執行應用程式時的資料是空格。 要求資料時，Microsoft Jet 資料庫引擎的快取所要求的資料會先檢查而不是擷取從伺服器中，所花費的時間。 不是來自 ODBC 資料來源的資料不會儲存在快取中。  
  
 任何 ODBC 資料來源，例如附加的資料表可以有本機快取。  
  
 如需相關資訊，請參閱 DAO 說明主題 「 CacheSize CacheStart 屬性 」。  
  
##  <a name="getcachestart"></a>CDaoRecordset::GetCacheStart  
 呼叫此成員函式，以取得第一筆資料錄集快取中的書籤值。  
  
```  
COleVariant GetCacheStart();
```  
  
### <a name="return-value"></a>傳回值  
 A `COleVariant` ，指定快取資料錄集中的第一筆記錄的書籤。  
  
### <a name="remarks"></a>備註  
 Microsoft Jet 資料庫引擎會快取中，向要求快取範圍內的記錄，它會向伺服器要求快取範圍外的記錄。  
  
> [!NOTE]
>  從快取擷取的記錄不會反映所做的變更同時來源資料的其他使用者。  
  
 如需相關資訊，請參閱 DAO 說明主題 「 CacheSize CacheStart 屬性 」。  
  
##  <a name="getcurrentindex"></a>CDaoRecordset::GetCurrentIndex  
 呼叫此成員函式，以判斷目前正在使用中索引的資料表類型索引`CDaoRecordset`物件。  
  
```  
CString GetCurrentIndex();
```  
  
### <a name="return-value"></a>傳回值  
 A`CString`包含目前與資料表類型的資料錄集的使用中索引的名稱。 如果尚未設定任何索引，則傳回空字串。  
  
### <a name="remarks"></a>備註  
 此索引是資料表類型的資料錄集，排序記錄的基礎，而且會由[搜尋](#seek)成員函式來搜尋記錄。  
  
 A`CDaoRecordset`物件可以有一個以上的索引，但可以一次使用一個索引 (雖然[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)物件可能有多個定義的索引)。  
  
 如需相關資訊，請參閱主題 「 索引物件 」，並定義 DAO 說明中的 「 目前索引 」。  
  
##  <a name="getdatecreated"></a>CDaoRecordset::GetDateCreated  
 呼叫此成員函式擷取基底資料表的建立的時間與日期。  
  
```  
COleDateTime GetDateCreated();
```  
  
### <a name="return-value"></a>傳回值  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，其中包含基底資料表的建立的時間與日期。  
  
### <a name="remarks"></a>備註  
 日期和時間設定被衍生自基底資料表建立所在的電腦。  
  
 如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
##  <a name="getdatelastupdated"></a>CDaoRecordset::GetDateLastUpdated  
 呼叫此成員函式擷取結構描述上次更新的時間與日期。  
  
```  
COleDateTime GetDateLastUpdated();
```  
  
### <a name="return-value"></a>傳回值  
 A [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，其中包含上次更新基底資料表結構 （結構描述） 的時間與日期。  
  
### <a name="remarks"></a>備註  
 日期和時間設定被衍生自上次更新基底資料表結構 （結構描述） 的電腦。  
  
 如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。  
  
##  <a name="getdefaultdbname"></a>CDaoRecordset::GetDefaultDBName  
 呼叫此成員函式，來判斷這個資料錄集之資料庫的名稱。  
  
```  
virtual CString GetDefaultDBName();
```  
  
### <a name="return-value"></a>傳回值  
 A `CString` ，其中包含這個資料錄集衍生的來源資料庫的名稱與路徑。  
  
### <a name="remarks"></a>備註  
 如果建立資料錄集時，如果不是指向[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)，則此路徑會使用資料錄集所開啟的預設資料庫。 根據預設，此函數會傳回空字串。 如果類別是衍生新的資料錄集，從`CDaoRecordset`，它會為您建立此函式。  
  
 下列範例說明如何使用雙反斜線 (\\\\) 在字串中，會視需要正確解譯的字串。  
  
 [!code-cpp[NVC_MFCDatabase #&4;](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]  
  
##  <a name="getdefaultsql"></a>CDaoRecordset::GetDefaultSQL  
 架構會呼叫此成員函式，以取得資料錄集所依據的預設 SQL 陳述式。  
  
```  
virtual CString GetDefaultSQL();
```  
  
### <a name="return-value"></a>傳回值  
 A `CString` ，其中包含預設的 SQL 陳述式。  
  
### <a name="remarks"></a>備註  
 這可能是資料表名稱或 SQL**選取**陳述式。  
  
 間接定義預設的 SQL 陳述式藉由宣告類別精靈，您的資料錄集類別和類別精靈會為您執行這項工作。  
  
 如果您傳遞 null SQL 字串，以[開啟](#open)，則會呼叫此函數來判斷資料錄集的資料表名稱或 SQL。  
  
##  <a name="geteditmode"></a>CDaoRecordset::GetEditMode  
 呼叫此成員函式來判斷狀態的編輯，也就是下列值之一︰  
  
```  
short GetEditMode();
```  
  
### <a name="return-value"></a>傳回值  
 傳回值，指出目前記錄的編輯功能的狀態。  
  
### <a name="remarks"></a>備註  
  
|值|說明|  
|-----------|-----------------|  
|**dbEditNone**|沒有編輯作業正在進行中。|  
|**dbEditInProgress**|**編輯**被呼叫。|  
|**dbEditAdd**|`AddNew`已呼叫。|  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 EditMode 屬性 」。  
  
##  <a name="getfieldcount"></a>CDaoRecordset::GetFieldCount  
 呼叫此成員函式可擷取的數字 （資料行） 中定義的欄位資料錄集。  
  
```  
short GetFieldCount();
```  
  
### <a name="return-value"></a>傳回值  
 資料錄集中的欄位數目。  
  
### <a name="remarks"></a>備註  
 如需相關資訊，請參閱主題 DAO 說明中的 「 計數屬性 」。  
  
##  <a name="getfieldinfo"></a>CDaoRecordset::GetFieldInfo  
 呼叫此成員函式，以取得相關資料錄集中的欄位資訊。  
  
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
 參考[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。  
  
 `dwInfoOptions`  
 指定要擷取的資料錄集的相關資訊的選項。 這裡列出可用的選項以及它們會導致函式傳回。 為了達到最佳效能，擷取的資訊，您需要層的級︰  
  
- `AFX_DAO_PRIMARY_INFO`（預設值）屬性名稱、 類型、 大小  
  
- `AFX_DAO_SECONDARY_INFO`主要的資訊，加上︰ 序數位置，必要時，允許零長度、 定序順序，外部索引名稱、 來源欄位中，來源資料表  
  
- `AFX_DAO_ALL_INFO`主要和次要的資訊，加上︰ 預設值，驗證規則驗證文字  
  
 `lpszName`  
 欄位的名稱。  
  
### <a name="remarks"></a>備註  
 一個版本的函式可讓您查詢索引欄位。 另一個版本可讓您依名稱查閱欄位。  
  
 傳回資訊的說明，請參閱[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。 此結構具有成員資訊的描述中列出的項目所對應`dwInfoOptions`。 當您要求一個層級的資訊時，您會取得任何先前的層資訊。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 屬性屬性 」。  
  
##  <a name="getfieldvalue"></a>CDaoRecordset::GetFieldValue  
 呼叫此成員函式來擷取資料錄集中的資料。  
  
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
 包含欄位名稱的字串指標。  
  
 `varValue`  
 參考`COleVariant`物件，將儲存欄位的值。  
  
 `nIndex`  
 在資料錄集的欄位集合中，依索引查閱欄位的以零為起始索引。  
  
### <a name="return-value"></a>傳回值  
 兩個版本`GetFieldValue`的傳回值傳回[COleVariant](../../mfc/reference/colevariant-class.md)物件，其中包含欄位的值。  
  
### <a name="remarks"></a>備註  
 依名稱或序數位置，您可以查閱欄位。  
  
> [!NOTE]
>  它會呼叫其中一個使用這個成員函式版本更有效率`COleVariant`物件參考做為參數，而不是呼叫傳回的版本為`COleVariant`物件。 此函式的第二個版本會保留回溯相容性。  
  
 使用`GetFieldValue`和[SetFieldValue](#setfieldvalue)以動態方式在執行的階段而不是以靜態方式使用繫結資料行繫結欄位[DoFieldExchange](#dofieldexchange)機制。  
  
 `GetFieldValue`而`DoFieldExchange`機制可以結合以提升效能。 例如，使用`GetFieldValue`擷取值，您必須只在需要時，並指派該呼叫在介面中的 < 其他資訊 」 按鈕。  
  
 如需相關資訊，請參閱 「 欄位物件 」 和 「 值屬性 」 中 DAO 說明主題。  
  
##  <a name="getindexcount"></a>CDaoRecordset::GetIndexCount  
 呼叫此成員函式，來決定資料表類型的資料錄集的索引數目。  
  
```  
short GetIndexCount();
```  
  
### <a name="return-value"></a>傳回值  
 資料表類型的資料錄集的索引數目。  
  
### <a name="remarks"></a>備註  
 `GetIndexCount`可用於循環使用資料錄集中的所有索引。 針對該目的，使用`GetIndexCount`搭配[GetIndexInfo](#getindexinfo)。 如果您呼叫此成員函式在動態類型或快照集類型資料錄集時，MFC 會擲回例外狀況。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 屬性屬性 」。  
  
##  <a name="getindexinfo"></a>CDaoRecordset::GetIndexInfo  
 呼叫此成員函式，以取得不同的索引定義基礎資料錄集的基底資料表中的相關資訊。  
  
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
 參考[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構。  
  
 `dwInfoOptions`  
 指定要擷取索引的相關資訊的選項。 這裡列出可用的選項以及它們會導致函式傳回。 為了達到最佳效能，擷取的資訊，您需要層的級︰  
  
- `AFX_DAO_PRIMARY_INFO`（預設值）欄位名稱、 欄位資訊  
  
- `AFX_DAO_SECONDARY_INFO`主要的資訊，加上︰ 主要、 唯一、 叢集、 忽略 Null，必要時，外部  
  
- `AFX_DAO_ALL_INFO`主要和次要的資訊，加上︰ 相異計數  
  
 `lpszName`  
 依名稱查閱的索引物件的名稱指標。  
  
### <a name="remarks"></a>備註  
 一個版本的函式可讓您查詢的集合中位置的索引。 另一個版本可讓您依名稱查閱索引。  
  
 傳回資訊的說明，請參閱[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構。 此結構具有成員資訊的描述中列出的項目所對應`dwInfoOptions`。 當您要求一個層級的資訊時，您會取得任何先前的層資訊。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 屬性屬性 」。  
  
##  <a name="getlastmodifiedbookmark"></a>CDaoRecordset::GetLastModifiedBookmark  
 呼叫此成員函式擷取最最近新增或更新資料錄的書籤。  
  
```  
COleVariant GetLastModifiedBookmark();
```  
  
### <a name="return-value"></a>傳回值  
 A`COleVariant`包含書籤，指出最近加入或變更記錄。  
  
### <a name="remarks"></a>備註  
 當建立或開啟資料錄集物件時，其記錄的每個已經有唯一的書籤支援它們。 呼叫[GetBookmark](#getbookmark)決定資料錄集是否支援書籤。 如果資料錄集不支援書籤，`CDaoException`就會擲回。  
  
 當您新增一筆記錄時，它會出現在結尾的資料錄集，並不是目前的記錄。 若要讓新的記錄目前，呼叫`GetLastModifiedBookmark`，然後呼叫`SetBookmark`回到新加入的記錄。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 上次修改屬性 」。  
  
##  <a name="getlockingmode"></a>CDaoRecordset::GetLockingMode  
 呼叫此成員函式，以判斷鎖定資料錄集的作用中的型別。  
  
```  
BOOL GetLockingMode();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果鎖定的型別是封閉式，否則為 0，代表開放式記錄鎖定。  
  
### <a name="remarks"></a>備註  
 當您呼叫封閉式鎖定時作用中，包含您要編輯的資料錄的資料頁已鎖定[編輯](#edit)成員函式。 頁面已解除鎖定，當您呼叫[更新](#update)或[關閉](#close)成員函式或任何移動或尋找作業。  
  
 開放式鎖定是作用中時包含記錄的資料頁已鎖定，以更新記錄時，才**更新**成員函式。  
  
 當使用 ODBC 資料來源，總是開放式鎖定模式。  
  
 如需相關資訊，請參閱 「 LockEdits 屬性 」 和 「 鎖定行為在多使用者應用程式 」 DAO 說明中的主題。  
  
##  <a name="getname"></a>CDaoRecordset::GetName  
 呼叫此成員函式擷取的資料錄集的名稱。  
  
```  
CString GetName();
```  
  
### <a name="return-value"></a>傳回值  
 A`CString`包含資料錄集的名稱。  
  
### <a name="remarks"></a>備註  
 資料錄集的名稱必須以字母開頭，並可以包含最多 40 個字元。 它可以包含數字和底線字元，但不能包含標點符號或空格。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 名稱屬性 」。  
  
##  <a name="getparamvalue"></a>CDaoRecordset::GetParamValue  
 呼叫此成員函式擷取儲存在基礎 DAOParameter 物件中的指定參數的目前值。  
  
```  
virtual COleVariant GetParamValue(int nIndex);  
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 參數的基礎 DAOParameter 物件中的數字位置。  
  
 `lpszName`  
 您想將其值的參數名稱。  
  
### <a name="return-value"></a>傳回值  
 類別的物件[COleVariant](../../mfc/reference/colevariant-class.md) ，其中包含參數的值。  
  
### <a name="remarks"></a>備註  
 依名稱或數值位置的集合，您可以存取的參數。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 參數物件 」。  
  
##  <a name="getpercentposition"></a>CDaoRecordset::GetPercentPosition  
 使用動態類型或快照集類型資料錄集，如果您呼叫時`GetPercentPosition`之前完全填入資料錄集，是相對於存取由呼叫的記錄數目的移動量[GetRecordCount](#getrecordcount)。  
  
```  
float GetPercentPosition();
```  
  
### <a name="return-value"></a>傳回值  
 指出目前記錄中資料錄集的資料錄的百分比為基礎的資料錄集物件中的概略位置 0 和 100 之間的數字。  
  
### <a name="remarks"></a>備註  
 您可以移動至最後一筆記錄呼叫[MoveLast](#movelast)來完整母體擴展的所有資料錄集，但這可能需要很長一段時間。  
  
 您可以呼叫`GetPercentPosition`上的資料錄集物件的所有三種類型，包括沒有索引的資料表。 不過，您無法呼叫`GetPercentPosition`順向捲動快照集，或開啟外部資料庫傳遞查詢資料錄集。 如果沒有目前的記錄，或已刪除他目前的記錄，`CDaoException`就會擲回。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 PercentPosition 屬性 」。  
  
##  <a name="getrecordcount"></a>CDaoRecordset::GetRecordCount  
 呼叫此成員函式，以找出資料錄集的多少筆記錄被存取。  
  
```  
long GetRecordCount();
```  
  
### <a name="return-value"></a>傳回值  
 傳回資料錄集物件中存取的記錄數目。  
  
### <a name="remarks"></a>備註  
 `GetRecordCount`並不代表動態型別或快照集類型資料錄集包含多少筆記錄之前被存取的所有記錄。 這個成員函式呼叫可能需要很長一段時間才能完成。  
  
 存取最後一筆記錄後傳回的值會指出資料錄集中刪除記錄的總數。 若要強制存取最後一筆記錄，請呼叫`MoveLast`或`FindLast`資料錄集的成員函式。 您也可以使用 SQL 計數，以判斷您的查詢會傳回的記錄的近似數目。  
  
 為您的應用程式刪除記錄檔中的動態類型資料錄集，傳回值`GetRecordCount`會減少。 不過，其他使用者所刪除的記錄不會反映由`GetRecordCount`直到目前的記錄位於已刪除的記錄。 如果您執行的交易，會影響記錄計數和後續回復交易，`GetRecordCount`將不會反映實際的剩餘記錄數目。  
  
 值`GetRecordCount`從快照集類型的資料錄集不會受到基礎資料表中的變更。  
  
 值`GetRecordCount`資料表類型的資料錄集反映出資料表中記錄的近似數目和加入和刪除資料表記錄時立即影響。  
  
 沒有記錄的資料錄集傳回值為 0。 使用附加的資料表或 ODBC 資料庫時`GetRecordCount`一律會傳回 – 1。 呼叫**Requery**資料錄集的成員函式的值重設`GetRecordCount`就如同查詢也是重新執行。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 RecordCount 屬性 」。  
  
##  <a name="getsql"></a>CDaoRecordset::GetSQL  
 呼叫此成員函式，以取得用來開啟網頁時，請選取資料錄集的資料錄的 SQL 陳述式。  
  
```  
CString GetSQL() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A `CString` ，其中包含 SQL 陳述式。  
  
### <a name="remarks"></a>備註  
 這通常是 SQL**選取**陳述式。  
  
 所傳回的字串`GetSQL`通常不同於您可能會傳送到資料錄集的任何字串`lpszSQL`參數[開啟](#open)成員函式。 這是因為資料錄集建構完整的 SQL 陳述式，根據您傳遞至**開啟**類別精靈，以指定的內容，可能會指定在[m_strFilter](#m_strfilter)和[m_strSort](#m_strsort)資料成員。  
  
> [!NOTE]
>  只有在呼叫之後呼叫此成員函式**開啟**。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 SQL 屬性 」。  
  
##  <a name="gettype"></a>CDaoRecordset::GetType  
 開啟資料錄集來判斷資料錄集物件的型別之後呼叫此成員函式。  
  
```  
short GetType();
```  
  
### <a name="return-value"></a>傳回值  
 它有下列值，指出資料錄集類型︰  
  
- **dbOpenTable**資料表類型的資料錄集  
  
- **dbOpenDynaset**動態類型資料錄集  
  
- **dbOpenSnapshot**快照類型資料錄集  
  
### <a name="remarks"></a>備註  
 如需相關資訊，請參閱主題 DAO 說明中的 「 型別屬性 」。  
  
##  <a name="getvalidationrule"></a>CDaoRecordset::GetValidationRule  
 呼叫此成員函式，以判斷用來驗證資料的規則。  
  
```  
CString GetValidationRule();
```  
  
### <a name="return-value"></a>傳回值  
 A`CString`物件，其中包含驗證記錄中的資料，因為它已變更或加入至資料表的值。  
  
### <a name="remarks"></a>備註  
 此規則是以文字為基礎，並且每次變更基礎資料表時。 如果資料是不合法的 MFC 會擲回例外狀況。 傳回的錯誤訊息為基礎欄位物件，如果指定的驗證屬性的文字或運算式的基礎欄位物件所指定的文字。 您可以呼叫[GetValidationText](#getvalidationtext)以取得錯誤訊息的文字。  
  
 例如，需要的月份天數的記錄中的欄位可能的驗證規則例如 「 天 BETWEEN 1 到 31。 」  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 ValidationRule 屬性 」。  
  
##  <a name="getvalidationtext"></a>CDaoRecordset::GetValidationText  
 呼叫此成員函式擷取基礎欄位物件的驗證屬性的文字。  
  
```  
CString GetValidationText();
```  
  
### <a name="return-value"></a>傳回值  
 A`CString`物件，其中包含訊息時，系統會顯示欄位的值不符合驗證規則之基礎的欄位物件的文字。  
  
### <a name="remarks"></a>備註  
 如需相關資訊，請參閱主題 DAO 說明中的 「 驗證屬性 」。  
  
##  <a name="isbof"></a>CDaoRecordset::IsBOF  
 您從資料錄捲動記錄，以了解是否有發生第一筆資料錄集之前先呼叫此成員函式。  
  
```  
BOOL IsBOF() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果資料錄集不包含任何記錄，或是第一筆記錄中前, 向後捲動到非零值否則為 0。  
  
### <a name="remarks"></a>備註  
 您也可以呼叫`IsBOF`連同`IsEOF`來判斷資料錄集是否包含任何記錄，或為空白。 之後立即呼叫**開啟**，如果資料錄集不包含任何記錄，`IsBOF`傳回非零值。 當您開啟已至少一筆記錄的資料錄集時，第一筆記錄是目前的記錄和`IsBOF`傳回 0。  
  
 如果第一筆記錄是目前的記錄，而且您呼叫`MovePrev`，`IsBOF`後續將會傳回非零值。 如果`IsBOF`傳回非零，而且您呼叫`MovePrev`，會擲回例外狀況。 如果`IsBOF`傳回非零，目前的記錄會是未定義，以及任何需要目前記錄的動作將會造成擲回例外狀況。  
  
 上的特定方法的效果`IsBOF`和`IsEOF`設定︰  
  
-   呼叫**開啟**內部讓第一筆記錄中資料錄集目前的記錄藉由呼叫**MoveFirst**。 因此，呼叫**開啟**記錄原因的空集合上`IsBOF`和`IsEOF`傳回非零值。 (請參閱下列表格中的失敗行為**MoveFirst**或`MoveLast`呼叫。)  
  
-   所有成功尋找一筆記錄的移動作業會`IsBOF`和`IsEOF`傳回 0。  
  
-   `AddNew`後面接著呼叫**更新**會將新記錄的呼叫會導致`IsBOF`傳回 0，但是只有`IsEOF`已經為非零值。 狀態`IsEOF`一定會維持不變。 Microsoft Jet 資料庫引擎所定義，空的資料錄集目前的記錄指標是檔案的結尾，因此目前的記錄之後插入任何新記錄。  
  
-   任何**刪除**呼叫，即使它會移除資料錄集，唯一的剩餘記錄不會變更的值`IsBOF`或`IsEOF`。  
  
 下表顯示移動所允許的作業使用的不同組合`IsBOF` /  `IsEOF`。  
  
||MoveFirst、 MoveLast|MovePrev，<br /><br /> 移動< 0></ 0>|移動 0|MoveNext，<br /><br /> 移動 > 0|  
|------|-------------------------|-----------------------------|------------|-----------------------------|  
|`IsBOF`= 非零，<br /><br /> `IsEOF`=0|Allowed|例外狀況|例外狀況|Allowed|  
|`IsBOF`=0,<br /><br /> `IsEOF`= 非零值|Allowed|Allowed|例外狀況|例外狀況|  
|兩者都為非零|例外狀況|例外狀況|例外狀況|例外狀況|  
|這兩個 0|Allowed|Allowed|Allowed|Allowed|  
  
 允許在移動作業，並不表示作業已成功將尋找一筆記錄。 它僅表示允許嘗試執行指定的移動作業，而不會產生例外狀況。 值`IsBOF`和`IsEOF`成員函式可能因為嘗試移動而變更。  
  
 沒有找到一筆記錄的值的移動作業的效果`IsBOF`和`IsEOF`設定 下表所示。  
  
||IsBOF|IsEOF|  
|------|-----------|-----------|  
|**MoveFirst**，`MoveLast`|非零值|非零值|  
|**移動**0|無變更|無變更|  
|`MovePrev`, **Move**< 0></ 0>|非零值|無變更|  
|`MoveNext`, **Move** > 0|無變更|非零值|  
  
 如需相關資訊，請參閱本主題 「 BOF，EOF 屬性 」 DAO 說明中。  
  
##  <a name="isdeleted"></a>CDaoRecordset::IsDeleted  
 呼叫此成員函式，以判斷是否已刪除目前的記錄。  
  
```  
BOOL IsDeleted() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果資料錄集位於已刪除的記錄。否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您捲動至資料錄和`IsDeleted`傳回**TRUE** （非零），然後您必須捲動至另一筆記錄之前，您可以執行任何其他資料錄集作業。  
  
> [!NOTE]
>  您不需要檢查快照集或資料表類型的資料錄集內的記錄已刪除的狀態。 因為無法刪除記錄，從快照集，就不需要呼叫`IsDeleted`。 針對資料表類型的資料錄集，實際上會從資料錄集移除已刪除的記錄。 一旦記錄已刪除，是由另一位使用者，或在另一個資料錄集，您無法往回捲動至該記錄。 因此，就不需要呼叫`IsDeleted`。  
  
 當您刪除記錄時從動態集時，則會從資料錄集移除，您無法往回捲動至該記錄。 不過，如果中記錄動態集刪除由其他使用者或另一個相同的資料表為基礎的資料錄集中`IsDeleted`會傳回**TRUE**稍後捲動至該記錄。  
  
 如需相關資訊，請參閱 「 刪除方法 」、 「 LastModified 屬性 」 和 「 EditMode 屬性 」 DAO 說明中的主題。  
  
##  <a name="iseof"></a>CDaoRecordset::IsEOF  
 當您從資料錄捲動記錄，以了解您是否已超過最後一筆記錄的資料錄集已經呼叫此成員函式。  
  
```  
BOOL IsEOF() const;  
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果資料錄集不包含任何記錄，或是已經超過最後一筆記錄中。否則為 0。  
  
### <a name="remarks"></a>備註  
 您也可以呼叫`IsEOF`來判斷資料錄集是否包含任何記錄，或為空白。 之後立即呼叫**開啟**，如果資料錄集不包含任何記錄，`IsEOF`傳回非零值。 當您開啟已至少一筆記錄的資料錄集時，第一筆記錄是目前的記錄和`IsEOF`傳回 0。  
  
 如果最後一筆記錄是目前的記錄，當您呼叫`MoveNext`，`IsEOF`後續將會傳回非零值。 如果`IsEOF`傳回非零，而且您呼叫`MoveNext`，會擲回例外狀況。 如果`IsEOF`傳回非零，目前的記錄會是未定義，以及任何需要目前記錄的動作將會造成擲回例外狀況。  
  
 上的特定方法的效果`IsBOF`和`IsEOF`設定︰  
  
-   呼叫**開啟**內部讓第一筆記錄中資料錄集目前的記錄藉由呼叫**MoveFirst**。 因此，呼叫**開啟**記錄原因的空集合上`IsBOF`和`IsEOF`傳回非零值。 (請參閱下列表格中的失敗行為**MoveFirst**呼叫。)  
  
-   所有成功尋找一筆記錄的移動作業會`IsBOF`和`IsEOF`傳回 0。  
  
-   `AddNew`後面接著呼叫**更新**會將新記錄的呼叫會導致`IsBOF`傳回 0，但是只有`IsEOF`已經為非零值。 狀態`IsEOF`一定會維持不變。 Microsoft Jet 資料庫引擎所定義，空的資料錄集目前的記錄指標是檔案的結尾，因此目前的記錄之後插入任何新記錄。  
  
-   任何**刪除**呼叫，即使它會移除資料錄集，唯一的剩餘記錄不會變更的值`IsBOF`或`IsEOF`。  
  
 下表顯示移動所允許的作業使用的不同組合`IsBOF` /  `IsEOF`。  
  
||MoveFirst、 MoveLast|MovePrev，<br /><br /> 移動< 0></ 0>|移動 0|MoveNext，<br /><br /> 移動 > 0|  
|------|-------------------------|-----------------------------|------------|-----------------------------|  
|`IsBOF`= 非零，<br /><br /> `IsEOF`=0|Allowed|例外狀況|例外狀況|Allowed|  
|`IsBOF`=0,<br /><br /> `IsEOF`= 非零值|Allowed|Allowed|例外狀況|例外狀況|  
|兩者都為非零|例外狀況|例外狀況|例外狀況|例外狀況|  
|這兩個 0|Allowed|Allowed|Allowed|Allowed|  
  
 允許在移動作業，並不表示作業已成功將尋找一筆記錄。 它僅表示允許嘗試執行指定的移動作業，而不會產生例外狀況。 值`IsBOF`和`IsEOF`成員函式可能因為嘗試移動而變更。  
  
 沒有找到一筆記錄的值的移動作業的效果`IsBOF`和`IsEOF`設定 下表所示。  
  
||IsBOF|IsEOF|  
|------|-----------|-----------|  
|**MoveFirst**，`MoveLast`|非零值|非零值|  
|**移動**0|無變更|無變更|  
|`MovePrev`, **Move**< 0></ 0>|非零值|無變更|  
|`MoveNext`, **Move** > 0|無變更|非零值|  
  
 如需相關資訊，請參閱本主題 「 BOF，EOF 屬性 」 DAO 說明中。  
  
##  <a name="isfielddirty"></a>CDaoRecordset::IsFieldDirty  
 呼叫此成員函式來判斷指定的欄位資料成員的動態集是否已標示為 「 不正常 」 （變更）。  
  
```  
BOOL IsFieldDirty(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 您想要檢查其狀態的欄位資料成員的指標或**NULL**來判斷是否有任何欄位已變更。  
  
### <a name="return-value"></a>傳回值  
 非零，如果指定的欄位資料成員標記為已變更。否則為 0。  
  
### <a name="remarks"></a>備註  
 所有已變更的欄位資料成員中的資料會傳輸至記錄資料來源上呼叫更新目前的記錄時**更新**成員函式`CDaoRecordset`(到呼叫**編輯**或`AddNew`)。 具備這項知識，您可以採取進一步的步驟，例如取消旗標，將標記資料行，將不會寫入至資料來源，將欄位資料成員。  
  
 `IsFieldDirty`透過實作`DoFieldExchange`。  
  
##  <a name="isfieldnull"></a>CDaoRecordset::IsFieldNull  
 呼叫此成員函式，以判斷資料錄集的指定的欄位資料成員是否被標示為 Null。  
  
```  
BOOL IsFieldNull(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 您想要檢查其狀態的欄位資料成員的指標或**NULL**來決定的任何欄位都是 Null。  
  
### <a name="return-value"></a>傳回值  
 指定的欄位資料成員標示為 Null; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 (在資料庫術語中，為 Null 」 有任何值 」 的方式，不與相同**NULL** c + + 中。)如果欄位資料成員被標示為 Null，它會解譯為資料行的任何值是目前的記錄。  
  
> [!NOTE]
>  在某些情況下，使用`IsFieldNull`可能會沒有效率，，如下列程式碼範例所示︰  
  
 [!code-cpp[NVC_MFCDatabase #&5;](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]  
  
> [!NOTE]
>  如果您使用動態資料錄的繫結，而不需從衍生`CDaoRecordset`，務必使用**VT_NULL**範例所示。  
  
##  <a name="isfieldnullable"></a>CDaoRecordset::IsFieldNullable  
 呼叫此成員函式，以判斷指定的欄位資料成員是 「 null 」 （可以是設定為 Null 值。C + + **NULL**不是 Null，表示，在資料庫術語中，相同不擁有任何值 」)。  
  
```  
BOOL IsFieldNullable(void* pv);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 您想要檢查其狀態的欄位資料成員的指標或**NULL**來決定的任何欄位都是 Null。  
  
### <a name="return-value"></a>傳回值  
 指定的欄位資料成員可將 Null; 如果為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 不能是 Null 的欄位必須有值。 如果您嘗試將這類欄位設定為 Null，新增或更新一筆記錄時，資料來源會拒絕新增或更新，以及**更新**將會擲回例外狀況。 當您呼叫時，就會發生例外狀況**更新**，不會在您呼叫`SetFieldNull`。  
  
##  <a name="isopen"></a>CDaoRecordset::IsOpen  
 呼叫此成員函式，以判斷是否已開啟資料錄集。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零資料錄集物件的**開啟**或**Requery**先前呼叫成員函式和資料錄集尚未關閉，否則為 0。  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_bcheckcachefordirtyfields"></a>M_bcheckcachefordirtyfields  
 包含旗標，指出是否快取的欄位會自動標示為中途 （變更） 和 Null。  
  
### <a name="remarks"></a>備註  
 旗標的預設值為**TRUE**。 此資料成員中的設定會控制整個的雙重緩衝機制。 如果您將此旗標設定為**TRUE**，您可以關閉快取為基礎的欄位使用 DFX 機制。 如果您將此旗標設定為**FALSE**，您必須呼叫`SetFieldDirty`和`SetFieldNull`自己。  
  
 設定此資料成員，然後再呼叫**開啟**。 此機制是主要是為了方便使用。 效能可能會變慢因為雙重緩衝的欄位進行變更時。  
  
##  <a name="m_nfields"></a>CDaoRecordset::m_nFields  
 包含資料錄集類別中的欄位資料成員的數目和資料來源的資料錄集選取資料行數目。  
  
### <a name="remarks"></a>備註  
 資料錄集類別的建構函式必須初始化`m_nFields`靜態繫結的欄位數目正確。 當您使用宣告資料錄集類別時，ClassWizard 寫入這個初始化的。 您也可以撰寫它以手動方式。  
  
 架構會管理對應的資料行的資料來源上的目前記錄的欄位資料成員之間的互動，使用這個數字。  
  
> [!NOTE]
>  這個數字必須對應到登錄中的輸出資料行數目`DoFieldExchange`呼叫後`SetFieldType`參數**CDaoFieldExchange::outputColumn**。  
  
 您可以繫結資料行，以動態方式由種`CDaoRecordset::GetFieldValue`和`CDaoRecordset::SetFieldValue`。 如果您這樣做，您不需要遞增的計數中`m_nFields`以反映數目 DFX 函式呼叫中您`DoFieldExchange`成員函式。  
  
##  <a name="m_nparams"></a>CDaoRecordset::m_nParams  
 包含資料錄集類別中的參數資料成員的數目，與資料錄集的查詢中傳遞的參數數目。  
  
### <a name="remarks"></a>備註  
 如果您的資料錄集類別有任何參數資料成員，必須初始化類別的建構函式`m_nParams`及正確的數值。 值`m_nParams`預設值為 0。 如果您加入的參數資料成員 — 這是您必須手動執行 — 您也可以手動必須加入初始化類別建構函式，以反映的參數數目 (必須是至少一樣大的數目 ' 中的預留位置您**m_strFilter**或`m_strSort`字串)。  
  
 當它參數化資料錄集的查詢時，架構會使用這個數字。  
  
> [!NOTE]
>  這個數字必須對應到 「 參數 」 中登錄數目`DoFieldExchange`呼叫後`SetFieldType`參數**CFieldExchange::param**。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 參數物件 」。  
  
##  <a name="m_pdaorecordset"></a>CDaoRecordset::m_pDAORecordset  
 包含的 DAO 資料錄集物件基礎的 OLE 介面的指標`CDaoRecordset`物件。  
  
### <a name="remarks"></a>備註  
 如果您需要直接存取 DAO 介面，請使用這個指標。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 資料錄集物件 」。  
  
##  <a name="m_pdatabase"></a>CDaoRecordset::m_pDatabase  
 包含一個指向`CDaoDatabase`透過此資料錄集連接到資料來源的物件。  
  
### <a name="remarks"></a>備註  
 兩種方式設定這個變數。 一般而言，您將指標傳遞至已開啟`CDaoDatabase`物件建構資料錄集物件時。 如果您傳遞**NULL**反而**CDaoRecordset**建立`CDaoDatabase`物件，並將它開啟。 在任一情況下，`CDaoRecordset`指標儲存在此變數。  
  
 通常您會直接不必使用指標儲存在**m_pDatabase**。 如果您撰寫自己的延伸模組來`CDaoRecordset`，不過，您可能需要使用該指標。 例如，您可能需要將指標如果您擲回自己`CDaoException`(s)。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 資料庫物件 」。  
  
##  <a name="m_strfilter"></a>CDaoRecordset::m_strFilter  
 包含用來建構字串**其中**子句的 SQL 陳述式。  
  
### <a name="remarks"></a>備註  
 它不包含保留的字**其中**來篩選資料錄集。 使用此資料成員不適用於資料表類型的資料錄集。 使用**m_strFilter**開啟資料錄集，使用時，沒有任何作用`CDaoQueryDef`指標。  
  
 使用美國日期格式 （月-日-年） 當您篩選欄位中包含的日期，即使您不想要使用 Microsoft Jet 資料庫引擎; 美國版否則，如預期般，可能未篩選的資料。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 篩選條件屬性 」。  
  
##  <a name="m_strsort"></a>CDaoRecordset::m_strSort  
 包含字串，含有**ORDERBY**子句的 SQL 陳述式，而不需要的保留字**ORDERBY**。  
  
### <a name="remarks"></a>備註  
 您可以依據動態集和快照集類型資料錄集物件。  
  
 您無法排序資料表類型的資料錄集物件。 若要判斷資料表類型的資料錄集的排序次序，請呼叫[SetCurrentIndex](#setcurrentindex)。  
  
 使用`m_strSort`開啟資料錄集，使用時，沒有任何作用`CDaoQueryDef`指標。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 排序屬性 」。  
  
##  <a name="move"></a>CDaoRecordset::Move  
 呼叫此成員函式，來定位資料錄集`lRows`與目前記錄的記錄。  
  
```  
virtual void Move(long lRows);
```  
  
### <a name="parameters"></a>參數  
 `lRows`  
 向前或向後移動的記錄數目。 正值向前，移到資料錄集的結尾。 負數值後，移到開頭。  
  
### <a name="remarks"></a>備註  
 您可以在向前或向後移動。 `Move( 1 )`相當於`MoveNext`，和`Move( -1 )`相當於`MovePrev`。  
  
> [!CAUTION]
>  呼叫的任何**移動**函式擲回例外狀況，如果資料錄集沒有任何記錄。 一般情況下，請同時呼叫`IsBOF`和`IsEOF`之前移動作業，以判斷資料錄集是否有任何記錄。 在您呼叫後**開啟**或**Requery**，呼叫`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果您有捲動過去的開頭或結尾的資料錄集 (`IsBOF`或`IsEOF`傳回非零值)，呼叫**移動**會擲回`CDaoException`。  
  
> [!NOTE]
>  如果您呼叫任何**移動**函式時，目前的記錄更新或加入更新都會遺失，而不發出警告。  
  
 當您呼叫**移動**順向捲動快照集中，`lRows`參數必須是正整數值並不允許書籤，所以您可以繼續只。  
  
 若要讓第一次，最後下, 一步 或上一個記錄資料錄集中目前的記錄，呼叫**MoveFirst**， `MoveLast`， `MoveNext`，或`MovePrev`成員函式。  
  
 如需相關資訊，請參閱主題 < 移動方法 」 和 「 MoveFirst、 MoveLast、 MoveNext，MovePrevious 方法 「 DAO 說明中。  
  
##  <a name="movefirst"></a>CDaoRecordset::MoveFirst  
 呼叫此成員函式 （如果有的話），進行第一筆記錄中資料錄集目前的記錄。  
  
```  
void MoveFirst();
```  
  
### <a name="remarks"></a>備註  
 您不需要呼叫**MoveFirst**立即開啟資料錄集之後。 此時，第一筆記錄 （如果有的話） 會自動為目前的記錄。  
  
> [!CAUTION]
>  呼叫的任何**移動**函式擲回例外狀況，如果資料錄集沒有任何記錄。 一般情況下，請同時呼叫`IsBOF`和`IsEOF`之前移動作業，以判斷資料錄集是否有任何記錄。 在您呼叫後**開啟**或**Requery**，呼叫`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果您呼叫任何**移動**函式時，目前的記錄更新或加入更新都會遺失，而不發出警告。  
  
 使用**移動**記錄間移動而不套用條件的函式。 用於找出記錄動態類型或符合特定條件的快照集類型資料錄集物件中尋找作業。 若要尋找一筆記錄中的資料表類型的資料錄集物件，請呼叫`Seek`。  
  
 資料錄集是指資料表類型的資料錄集，如果移動會遵循資料表目前的索引。 您可以使用基本的 DAO 物件的索引屬性來設定目前的索引。 如果您未設定目前的索引，傳回的記錄順序是未定義。  
  
 如果您呼叫`MoveLast`根據 SQL 查詢或 querydef 資料錄集物件，在強制完成查詢和資料錄集物件會完全擴展。  
  
 您不能呼叫**MoveFirst**或`MovePrev`順向捲動快照集的成員函式。  
  
 若要移動的目前位置記錄集物件中特定數目的記錄向前或向後移動，呼叫**移動**。  
  
 如需相關資訊，請參閱主題 < 移動方法 」 和 「 MoveFirst、 MoveLast、 MoveNext，MovePrevious 方法 「 DAO 說明中。  
  
##  <a name="movelast"></a>CDaoRecordset::MoveLast  
 資料錄集目前的記錄中呼叫此成員函式進行最後一筆記錄 （如果有的話）。  
  
```  
void MoveLast();
```  
  
### <a name="remarks"></a>備註  
  
> [!CAUTION]
>  呼叫的任何**移動**函式擲回例外狀況，如果資料錄集沒有任何記錄。 一般情況下，請同時呼叫`IsBOF`和`IsEOF`之前移動作業，以判斷資料錄集是否有任何記錄。 在您呼叫後**開啟**或**Requery**，呼叫`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果您呼叫任何**移動**函式時，目前的記錄更新或加入更新都會遺失，而不發出警告。  
  
 使用**移動**記錄間移動而不套用條件的函式。 用於找出記錄動態類型或符合特定條件的快照集類型資料錄集物件中尋找作業。 若要尋找一筆記錄中的資料表類型的資料錄集物件，請呼叫`Seek`。  
  
 資料錄集是指資料表類型的資料錄集，如果移動會遵循資料表目前的索引。 您可以使用基本的 DAO 物件的索引屬性來設定目前的索引。 如果您未設定目前的索引，傳回的記錄順序是未定義。  
  
 如果您呼叫`MoveLast`根據 SQL 查詢或 querydef 資料錄集物件，在強制完成查詢和資料錄集物件會完全擴展。  
  
 若要移動的目前位置記錄集物件中特定數目的記錄向前或向後移動，呼叫**移動**。  
  
 如需相關資訊，請參閱主題 < 移動方法 」 和 「 MoveFirst、 MoveLast、 MoveNext，MovePrevious 方法 「 DAO 說明中。  
  
##  <a name="movenext"></a>CDaoRecordset::MoveNext  
 呼叫此成員函式，要在資料錄集目前的記錄中的下一筆記錄。  
  
```  
void MoveNext();
```  
  
### <a name="remarks"></a>備註  
 建議您呼叫`IsBOF`您嘗試將移至前一筆記錄之前。 呼叫`MovePrev`將會擲回`CDaoException`如果`IsBOF`傳回非零值，指出，您已捲第一筆記錄之前，還是沒有記錄所選取的資料錄集。  
  
> [!CAUTION]
>  呼叫的任何**移動**函式擲回例外狀況，如果資料錄集沒有任何記錄。 一般情況下，請同時呼叫`IsBOF`和`IsEOF`之前移動作業，以判斷資料錄集是否有任何記錄。 在您呼叫後**開啟**或**Requery**，呼叫`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果您呼叫任何**移動**函式時，目前的記錄更新或加入更新都會遺失，而不發出警告。  
  
 使用**移動**記錄間移動而不套用條件的函式。 用於找出記錄動態類型或符合特定條件的快照集類型資料錄集物件中尋找作業。 若要尋找一筆記錄中的資料表類型的資料錄集物件，請呼叫`Seek`。  
  
 資料錄集是指資料表類型的資料錄集，如果移動會遵循資料表目前的索引。 您可以使用基本的 DAO 物件的索引屬性來設定目前的索引。 如果您未設定目前的索引，傳回的記錄順序是未定義。  
  
 若要移動的目前位置記錄集物件中特定數目的記錄向前或向後移動，呼叫**移動**。  
  
 如需相關資訊，請參閱主題 < 移動方法 」 和 「 MoveFirst、 MoveLast、 MoveNext，MovePrevious 方法 「 DAO 說明中。  
  
##  <a name="moveprev"></a>CDaoRecordset::MovePrev  
 呼叫此成員函式，要在資料錄集目前的記錄中的前一筆記錄。  
  
```  
void MovePrev();
```  
  
### <a name="remarks"></a>備註  
 建議您呼叫`IsBOF`您嘗試將移至前一筆記錄之前。 呼叫`MovePrev`將會擲回`CDaoException`如果`IsBOF`傳回非零值，指出，您已捲第一筆記錄之前，還是沒有記錄所選取的資料錄集。  
  
> [!CAUTION]
>  呼叫的任何**移動**函式擲回例外狀況，如果資料錄集沒有任何記錄。 一般情況下，請同時呼叫`IsBOF`和`IsEOF`之前移動作業，以判斷資料錄集是否有任何記錄。 在您呼叫後**開啟**或**Requery**，呼叫`IsBOF`或`IsEOF`。  
  
> [!NOTE]
>  如果您呼叫任何**移動**函式時，目前的記錄更新或加入更新都會遺失，而不發出警告。  
  
 使用**移動**記錄間移動而不套用條件的函式。 用於找出記錄動態類型或符合特定條件的快照集類型資料錄集物件中尋找作業。 若要尋找一筆記錄中的資料表類型的資料錄集物件，請呼叫`Seek`。  
  
 資料錄集是指資料表類型的資料錄集，如果移動會遵循資料表目前的索引。 您可以使用基本的 DAO 物件的索引屬性來設定目前的索引。 如果您未設定目前的索引，傳回的記錄順序是未定義。  
  
 您不能呼叫**MoveFirst**或`MovePrev`順向捲動快照集的成員函式。  
  
 若要移動的目前位置記錄集物件中特定數目的記錄向前或向後移動，呼叫**移動**。  
  
 如需相關資訊，請參閱主題 < 移動方法 」 和 「 MoveFirst、 MoveLast、 MoveNext，MovePrevious 方法 「 DAO 說明中。  
  
##  <a name="open"></a>Cdaorecordset:: Open  
 您必須呼叫此成員函式擷取資料錄集的記錄。  
  
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
  
- **dbOpenSnapshot**雙向捲動的快照集類型資料錄集。  
  
 `lpszSQL`  
 字串指標，其中包含下列其中之一︰  
  
-   A **NULL**指標。  
  
-   一或多個 tabledefs 和/或 querydefs （以逗號分隔） 的名稱。  
  
-   SQL**選取**陳述式 (並選擇性地使用 SQL**其中**或**ORDERBY**子句)。  
  
-   傳遞的查詢。  
  
 `nOptions`  
 一或多個以下的選項。 預設值為 0。 可能的值如下：  
  
- **dbAppendOnly**您只可以附加新資料錄 （動態類型資料錄集只）。 此選項實際上是表示可能只有附加記錄。 MFC ODBC 資料庫類別具有僅附加選項，可允許擷取和附加的記錄。  
  
- **dbForwardOnly**資料錄集是順向捲動快照集。  
  
- **dbSeeChanges**另一位使用者會改變您正在編輯的資料產生例外狀況。  
  
- **dbDenyWrite**其他使用者無法修改或新增記錄。  
  
- **dbDenyRead**其他使用者無法檢視的記錄 (資料表類型 recordset)。  
  
- **dbReadOnly**只能檢視記錄，其他使用者可以修改這些指示。  
  
- **dbInconsistent** （動態類型資料錄集只） 允許不一致的更新。  
  
- **dbConsistent**只允許 （動態類型資料錄集只） 一致的更新。  
  
> [!NOTE]
>  常數**dbConsistent**和**dbInconsistent**是互斥的。 您可以使用其中一個或另一個，但不可同時指定的執行個體中**開啟**。  
  
 *pTableDef*  
 指標[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)物件。 此功能僅適用於資料表類型的資料錄集。 時使用此選項，`CDaoDatabase`指標用來建構`CDaoRecordset`不使用; 而是使用 tabledef 所在的資料庫。  
  
 *pQueryDef*  
 指標[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md)物件。 此功能僅適用於動態類型和快照集類型資料錄集。 時使用此選項，`CDaoDatabase`指標用來建構`CDaoRecordset`不使用; 而是使用 querydef 所在的資料庫。  
  
### <a name="remarks"></a>備註  
 然後再呼叫**開啟**，您必須建構資料錄集物件。 有幾個方式可做到這點：  
  
-   當您建構資料錄集物件時，請將指標傳遞至`CDaoDatabase`已經開啟的物件。  
  
-   當您建構資料錄集物件時，請將指標傳遞至`CDaoDatabase`未開啟的物件。 資料錄集開啟`CDaoDatabase`物件，但不是會關閉它時關閉資料錄集物件。  
  
-   當您建構資料錄集物件時，傳遞**NULL**指標。 資料錄集物件呼叫`GetDefaultDBName`取得 Microsoft Access 的名稱。若要開啟 MDB 檔案。 接著會開啟資料錄集`CDaoDatabase`物件並將它開啟，只要資料錄集已開啟。 當您呼叫**關閉**資料錄集，`CDaoDatabase`物件也會關閉。  
  
    > [!NOTE]
    >  資料錄集開啟時`CDaoDatabase`物件，則會以非獨佔存取的資料來源。  
  
 版本的**開啟**使用`lpszSQL`參數，開啟資料錄集後，您就可以擷取幾種方式中的記錄。 第一個選項是將 DFX 函式放在您`DoFieldExchange`。 第二個選項是使用動態繫結，藉由呼叫`GetFieldValue`成員函式。 單獨或組合，可以實作這些選項。 若將它們合併，您必須將 SQL 陳述式中自行在呼叫**開啟**。  
  
 當您使用第二版**開啟**您傳入其中`CDaoTableDef`物件時，產生的資料行會將可供您將透過繫結`DoFieldExchange`和 DFX 機制，及/或透過動態繫結`GetFieldValue`。  
  
> [!NOTE]
>  您可以在呼叫**開啟**使用`CDaoTableDef`資料表類型的資料錄集的物件。  
  
 當您使用的第三個版本**開啟**您傳入其中`CDaoQueryDef`物件，將會執行查詢，，然後產生的資料行會將可供您將透過繫結`DoFieldExchange`和 DFX 機制，及/或透過動態繫結`GetFieldValue`。  
  
> [!NOTE]
>  您可以在呼叫**開啟**使用`CDaoQueryDef`動態類型和快照集類型資料錄集物件。  
  
 第一個版本的**開啟**使用`lpszSQL`參數，記錄是下表顯示所選根據的準則。  
  
|`lpszSQL` 參數的值|取決於選取的記錄|範例|  
|--------------------------------------|----------------------------------------|-------------|  
|**NULL**|所傳回的字串`GetDefaultSQL`。||  
|一或多個 tabledefs 及/或 querydef 名稱的逗號分隔清單。|中的所有資料行表示`DoFieldExchange`。|`"Customer"`|  
|**選取**資料行清單**FROM**資料表清單|從指定的 tabledef(s) 和/或 querydef(s) 所指定資料行。|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|  
  
 一般程序是將**NULL**至**開啟**; 在此情況下，**開啟**呼叫`GetDefaultSQL`，類別精靈在建立時所產生的可覆寫成員函式`CDaoRecordset`-衍生的類別。 這個值會提供您在類別中指定的 tabledef(s) 和/或 querydef 名稱。 您可以指定中的其他資訊`lpszSQL`參數。  
  
 無論您傳遞，**開啟**建構查詢的最終 SQL 字串 (字串可能有 SQL**其中**和**ORDERBY**子句附加至`lpszSQL`字串傳遞給您)，然後執行查詢。 您可以藉由呼叫檢查建構的字串`GetSQL`之後呼叫**開啟**。  
  
 資料錄集類別的欄位資料成員會繫結至選取的資料的資料行。 如果傳回任何記錄，第一筆記錄會變成目前的記錄。  
  
 如果您想要設定資料錄集篩選或排序，例如設定`m_strSort`或**m_strFilter**建構資料錄集物件後，但您呼叫**開啟**。 如果您想要重新整理資料錄集之後的記錄資料錄集已經開啟，請呼叫**Requery**。  
  
 如果您呼叫**開啟**動態類型或快照集類型資料錄集，或如果資料來源指的是 SQL 陳述式或 tabledef，表示附加的資料表，您無法使用**dbOpenTable**類型引數; 如果您這樣做，MFC 會擲回例外狀況。 若要判斷 tabledef 物件是否表示附加的資料表，建立[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md)物件，然後呼叫其[GetConnect](../../mfc/reference/cdaotabledef-class.md#getconnect)成員函式。  
  
 使用**dbSeeChanges**旗標，如果您想要設陷在編輯或刪除相同的記錄時，另一位使用者或電腦上的另一個程式所做的變更。 例如，如果兩位使用者開始編輯同一筆記錄的第一個使用者呼叫**更新**成員函式會成功。 當**更新**第二個使用者，會呼叫`CDaoException`就會擲回。 同樣地，如果第二個使用者嘗試呼叫**刪除**刪除記錄，而且已經變更的第一位使用者，`CDaoException`就會發生。  
  
 一般而言，如果使用者取得這個`CDaoException`您的程式碼應該更新時，請重新整理欄位的內容，並擷取已修改的值。 如果正在刪除發生例外狀況，您的程式碼無法顯示新的記錄資料給使用者和訊息，指出最近已變更資料。 此時，您的程式碼可以要求確認，使用者仍想要刪除的記錄。  
  
> [!TIP]
>  使用順向捲動選項 ( **dbForwardOnly**) 來改善效能，當您的應用程式一段式資料錄集開啟 ODBC 資料來源。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 OpenRecordset 方法 」。  
  
##  <a name="requery"></a>CDaoRecordset::Requery  
 呼叫此成員函式可重建 （重新整理） 資料錄集。  
  
```  
virtual void Requery();
```  
  
### <a name="remarks"></a>備註  
 如果傳回任何記錄，第一筆記錄會變成目前的記錄。  
  
 為了讓資料錄集，以反映您或其他使用者對資料來源的刪除和新增項目，您必須重建資料錄集，藉由呼叫**Requery**。 動態資料錄集時，它會自動反映您或其他使用者對其現有的記錄 （但不是新增項目） 的更新。 如果資料錄集是快照集，您必須呼叫**Requery**以反映其他使用者，以及新增和刪除作業的編輯。  
  
 動態集或快照集，呼叫**Requery**每當您想要重建資料錄集使用參數值。 設定新的篩選或排序藉由設定[m_strFilter](#m_strfilter)和[m_strSort](#m_strsort)之前，先呼叫**Requery**。 設定新的參數指派新值給參數資料成員，然後再呼叫**Requery**。  
  
 如果嘗試重建資料錄集失敗，就會關閉資料錄集。 然後再呼叫**Requery**，您可以判斷是否可以藉由呼叫重新查詢資料錄集[CanRestart](#canrestart)成員函式。 `CanRestart`不保證**Requery**會成功。  
  
> [!CAUTION]
>  呼叫**Requery**之後才呼叫**開啟**。  
  
> [!NOTE]
>  呼叫[Requery](#requery)變更 DAO 書籤。  
  
 您不能呼叫**Requery**動態類型或快照集類型資料錄集如果呼叫上`CanRestart`傳回 0，也不可以使用該類型的資料表資料錄集。  
  
 如果兩個`IsBOF`和`IsEOF`傳回非零之後您呼叫, **Requery**，查詢未傳回任何記錄和資料錄集將包含任何資料。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 Requery 方法 」。  
  
##  <a name="seek"></a>CDaoRecordset::Seek  
 呼叫此成員函式以尋找符合指定的準則目前編製索引，並將該記錄目前的記錄之索引的資料表類型資料錄集物件中的記錄。  
  
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
 下列字串運算式的其中一個: 「<",></",>\<="，"=""> = 」，或 「 > 」。  
  
 `pKey1`  
 指標[COleVariant](../../mfc/reference/colevariant-class.md)其值會對應到索引中的第一個欄位。 必要項。  
  
 *pKey2*  
 指標`COleVariant`其值會對應到在索引中，第二個欄位，如果有的話。 預設為**NULL**。  
  
 *pKey3*  
 指標`COleVariant`其值會對應到在索引中，第三個欄位，如果有的話。 預設為**NULL**。  
  
 *pKeyArray*  
 Variant 的陣列指標。 陣列大小會對應到索引中的欄位數目。  
  
 *nKeys*  
 是對應到陣列，也就是在索引中的欄位數目的大小的整數。  
  
> [!NOTE]
>  請勿指定機碼中的萬用字元。 萬用字元會導致`Seek`傳回不相符的記錄。  
  
### <a name="return-value"></a>傳回值  
 非零，如果相符的記錄找不到，否則為 0。  
  
### <a name="remarks"></a>備註  
 使用第二個 （陣列） 版本的`Seek`處理或更多的四個欄位的索引。  
  
 `Seek`啟用高效能搜尋資料表類型的資料錄集的索引。 您必須藉由呼叫設定目前的索引`SetCurrentIndex`之前，先呼叫`Seek`。 如果索引識別非唯一索引鍵欄位或欄位，`Seek`找出符合準則的第一個記錄。 如果沒有設定索引，則會擲回例外狀況。  
  
 請注意，如果您不想要建立的 UNICODE 資料錄集，則`COleVariant`物件必須明確宣告 ANSI。 這可以經由使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)**形式的建構函式與`vtSrc`設`VT_BSTRT`(ANSI) 或使用**COleVariant**函式[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)**與`vtSrc`設為`VT_BSTRT`。  
  
 當您呼叫`Seek`，傳遞一個或多個索引鍵值和比較運算子 (「<",></",>\<="，"="」 > = 」，或 「 > 」)。 `Seek`搜尋指定的索引鍵欄位，並找出符合所指定準則的第一個記錄`lpszComparison`和`pKey1`。 找到之後，`Seek`傳回非零值，並讓目前的記錄。 如果`Seek`無法找出相符項目，`Seek`傳回零，且目前的記錄未定義。 當直接使用 DAO，您必須明確檢查 NoMatch 屬性。  
  
 如果`lpszComparison`為 「 = 」，「 > = 」，或 「 > 」，`Seek`開頭的索引。 如果`lpszComparison`是 「<" or=""> </"> <=",> </=",> `Seek`開始索引的結尾，並向後搜尋，除非有重複的索引項目結尾。 在此情況下，`Seek`開始重複的索引項目結尾的索引之間的任意項目。  
  
 那里沒有為目前的記錄，當您使用`Seek`。  
  
 若要尋找一筆記錄動態型別或符合特定條件的快照集類型資料錄集，使用 尋找作業。 若要包含的所有記錄，不只是那些滿足特定條件，用於移動作業記錄間移動。  
  
 您不能呼叫`Seek`上附加任何的資料表型別，因為必須開啟附加的資料表，做為動態類型或快照集類型資料錄集。 不過，如果您呼叫`CDaoDatabase::Open`直接開啟可安裝的 ISAM 資料庫，您可以呼叫`Seek`該資料庫中的資料表上雖然效能可能會變慢。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 搜尋方法 」。  
  
##  <a name="setabsoluteposition"></a>CDaoRecordset::SetAbsolutePosition  
 設定資料錄集物件的目前資料錄的相對的記錄數目。  
  
```  
void SetAbsolutePosition(long lPosition);
```  
  
### <a name="parameters"></a>參數  
 *lPosition*  
 對應至目前資料錄的資料錄集中的序數位置。  
  
### <a name="remarks"></a>備註  
 呼叫`SetAbsolutePosition`可讓您根據其序數位置中的動態類型或快照集類型資料錄集的特定記錄目前的記錄指標的位置。 您也可以藉由呼叫來判斷目前的記錄編號[GetAbsolutePosition](#getabsoluteposition)。  
  
> [!NOTE]
>  此成員函式是僅適用於動態類型和快照集類型資料錄集。  
  
 AbsolutePosition 屬性值之基礎的 DAO 物件的以零為起始。設定為 0，指的是資料錄集的第一個記錄。 將值設定為大於填入的記錄會造成 MFC 擲回例外狀況數目。 您可以判斷資料錄集填入記錄數目，藉由呼叫`GetRecordCount`成員函式。  
  
 刪除目前的記錄時，如果沒有定義 AbsolutePosition 屬性值，和 MFC 擲回例外狀況，如果它參考。 新的記錄會加入至序列的結尾。  
  
> [!NOTE]
>  這個屬性不是要做為代理的記錄數目。 書籤依然是建議的方法來保留並傳回指定的位置，而且是目前資料錄定位在所有類型的支援書籤的資料錄集物件的唯一方式。 特別是，指定記錄的位置時，變更會刪除它之前的記錄。 另外還有指定的記錄都有相同的絕對位置，如果因為無法保證除非則會以 SQL 陳述式來建立資料錄集內的個別記錄的順序重新重新建立資料錄集不保證**ORDERBY**子句。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 AbsolutePosition 屬性 」。  
  
##  <a name="setbookmark"></a>CDaoRecordset::SetBookmark  
 呼叫此成員函式，以包含指定的書籤的記錄上定位資料錄集。  
  
```  
void SetBookmark(COleVariant varBookmark);
```  
  
### <a name="parameters"></a>參數  
 `varBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md)物件，其中包含書籤值的特定記錄。  
  
### <a name="remarks"></a>備註  
 當建立或開啟資料錄集物件時，其記錄的每個已經有唯一的書籤。 您可以呼叫來擷取目前的資料錄的書籤`GetBookmark`和儲存的值`COleVariant`物件。 您可於稍後返回該記錄藉由呼叫`SetBookmark`使用已儲存的書籤值。  
  
> [!NOTE]
>  呼叫[Requery](#requery)變更 DAO 書籤。  
  
 請注意，如果您不想要建立的 UNICODE 資料錄集，則`COleVariant`物件必須明確宣告 ANSI。 這可以經由使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)**形式的建構函式與`vtSrc`設`VT_BSTRT`(ANSI) 或使用**COleVariant**函式[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)**與`vtSrc`設為`VT_BSTRT`。  
  
 如需相關資訊，請參閱 「 書籤屬性 」 和 Bookmarkable 屬性的主題 「 DAO 說明。  
  
##  <a name="setcachesize"></a>CDaoRecordset::SetCacheSize  
 呼叫此成員函式設定的快取的記錄數目。  
  
```  
void SetCacheSize(long lSize);
```  
  
### <a name="parameters"></a>參數  
 `lSize`  
 指定記錄的數目。 一般值為 100。 如果設定為 0 會關閉快取。 設定必須介於 5 到 1200年的記錄。 快取可能使用大量的記憶體。  
  
### <a name="remarks"></a>備註  
 快取在本機記憶體中保存最近從伺服器擷取的資料，系統會要求一次執行應用程式時的資料是空格。 資料快取改善從遠端伺服器透過動態類型資料錄集物件中擷取資料的應用程式的效能。 要求資料時，Microsoft Jet 資料庫引擎的快取所要求的資料會先檢查而不是擷取從伺服器中，所花費的時間。 不是來自 ODBC 資料來源的資料不會儲存在快取中。  
  
 任何 ODBC 資料來源，例如附加的資料表可以有本機快取。 若要建立快取，請開啟資料錄集物件從遠端資料來源，呼叫`SetCacheSize`和`SetCacheStart`成員函式，然後再呼叫`FillCache`成員函式或使用其中一項移動作業的逐步執行記錄。 `lSize`參數`SetCacheSize`成員函式可以根據您的應用程式可以一次使用的記錄數目。 例如，如果您使用資料錄集的資料來源顯示在畫面上，您可以傳遞`SetCacheSize``lSize`參數做為 20，一次顯示 20 筆記錄。  
  
 如需相關資訊，請參閱 DAO 說明主題 「 CacheSize CacheStart 屬性 」。  
  
##  <a name="setcachestart"></a>CDaoRecordset::SetCacheStart  
 呼叫此成員函式，來指定快取資料錄集中的第一筆記錄的書籤。  
  
```  
void SetCacheStart(COleVariant varBookmark);
```  
  
### <a name="parameters"></a>參數  
 `varBookmark`  
 A [COleVariant](../../mfc/reference/colevariant-class.md) ，指定快取資料錄集中的第一筆記錄的書籤。  
  
### <a name="remarks"></a>備註  
 您可以使用書籤值的任何記錄`varBookmark`參數`SetCacheStart`成員函式。 進行您想要與目前的記錄開始快取中，建立使用該記錄的書籤的記錄[SetBookmark](#setbookmark)，並將書籤值傳遞為參數`SetCacheStart`成員函式。  
  
 Microsoft Jet 資料庫引擎會快取中，向要求快取範圍內的記錄，它會向伺服器要求快取範圍外的記錄。  
  
 從快取擷取的記錄不會反映所做的變更同時來源資料的其他使用者。  
  
 若要強制更新的所有快取的資料，請將傳遞`lSize`參數`SetCacheSize`為 0 時，呼叫`SetCacheSize`一次您可以利用快取大小原先要求，並接著呼叫`FillCache`成員函式。  
  
 請注意，如果您不想要建立的 UNICODE 資料錄集，則`COleVariant`物件必須明確宣告 ANSI。 這可以經由使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)**形式的建構函式與`vtSrc`設`VT_BSTRT`(ANSI) 或使用**COleVariant**函式[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)**與`vtSrc`設為`VT_BSTRT`。  
  
 如需相關資訊，請參閱主題 CacheSize，CacheStart 屬性 「 DAO 說明。  
  
##  <a name="setcurrentindex"></a>CDaoRecordset::SetCurrentIndex  
 呼叫此成員函式設定資料表類型的資料錄集的索引。  
  
```  
void SetCurrentIndex(LPCTSTR lpszIndex);
```  
  
### <a name="parameters"></a>參數  
 `lpszIndex`  
 指標，其中包含要設定的索引名稱。  
  
### <a name="remarks"></a>備註  
 基底資料表中的記錄不儲存任何特定順序。 設定索引變更記錄從資料庫傳回的順序，但不會影響的記錄會儲存的順序。 指定的索引必須已經定義。 如果您嘗試使用不存在的索引物件，或當您呼叫未設定索引[搜尋](#seek)，MFC 會擲回例外狀況。  
  
 您可以藉由呼叫建立新的索引，資料表[CDaoTableDef::CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex)及附加至的基礎 tabledef 索引集合的新索引，藉由呼叫[CDaoTableDef::Append](../../mfc/reference/cdaotabledef-class.md#append)後, 再重新開啟資料錄集。  
  
 傳回資料表類型的資料錄集的記錄只依所定義的基礎 tabledef 索引。 若要排序其他順序的記錄，您可以開啟動態類型或快照集類型資料錄集使用的 SQL **ORDERBY**子句會儲存在[CDaoRecordset::m_strSort](#m_strsort)。  
  
 如需相關資訊，請參閱主題 「 索引物件 」，並定義 DAO 說明中的 「 目前索引 」。  
  
##  <a name="setfielddirty"></a>CDaoRecordset::SetFieldDirty  
 呼叫此成員函式，加上旗標為已變更或為未變更資料錄集的欄位資料成員。  
  
```  
void SetFieldDirty(
    void* pv,  
    BOOL bDirty = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 包含資料錄集中的欄位資料成員的地址或**NULL**。 如果**NULL**，資料錄集中的所有欄位資料成員會加上旗都標。 (C + + **NULL**不是 Null 相同資料庫術語而言，這表示 「 有任何值 」。)  
  
 `bDirty`  
 **TRUE**欄位資料成員是否被標示為 「 中途 」 （變更）。 否則**FALSE**欄位資料成員是否被標示為 「 清除 」 （未變更）。  
  
### <a name="remarks"></a>備註  
 標記成未變更的欄位，可確保不會更新欄位。  
  
 Framework 標記變更欄位資料成員，以確保它們會寫入資料來源上的資料錄的 DAO 資料錄欄位交換 (DFX) 機制。 一般來說，變更欄位的值欄位已變更會自動設定，因此您很少需要呼叫`SetFieldDirty`，但是您有時候可能想要確保資料行將會明確地更新或插入不論什麼值是欄位資料成員中。 DFX 機制也會運用使用**PSEUDONULL**。 如需詳細資訊，請參閱[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
 如果未使用的雙重緩衝機制，然後變更欄位的值不會自動設定欄位為已變更。 在此情況下，它必須明確地將該欄位設為已變更。 中所包含的旗標[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制這項自動欄位檢查。  
  
> [!NOTE]
>  呼叫此成員函式呼叫之後，才[編輯](#edit)或[AddNew](#addnew)。  
  
 使用**NULL**的函式的第一個引數會將函數套用至所有**outputColumn**欄位中不**param**欄位`CDaoFieldExchange`。 例如，呼叫  
  
 [!code-cpp[NVC_MFCDatabase #&6;](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]  
  
 集合只**outputColumn**欄位**NULL**;**param**欄位不會受到影響。  
  
 若要致力於**param**，您必須提供個別的實際位址**param**您想要使用，例如︰  
  
 [!code-cpp[NVC_MFCDatabase #&7;](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]  
  
 這表示您無法設定所有**param**欄位**NULL**，您可以使用如**outputColumn**欄位。  
  
 `SetFieldDirty`透過實作`DoFieldExchange`。  
  
##  <a name="setfieldnull"></a>CDaoRecordset::SetFieldNull  
 呼叫此成員函式，加上旗標的資料錄集為 Null （特別具有任何值） 或非 Null 的欄位資料成員。  
  
```  
void SetFieldNull(
    void* pv,  
    BOOL bNull = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `pv`  
 包含資料錄集中的欄位資料成員的地址或**NULL**。 如果**NULL**，資料錄集中的所有欄位資料成員會加上旗都標。 (C + + **NULL**不是 Null 相同資料庫術語而言，這表示 「 有任何值 」。)  
  
 `bNull`  
 如果將欄位資料成員標示為已不具有任何值 (Null) 為非零。 否則為 0，表示欄位資料成員會標示為非 Null。  
  
### <a name="remarks"></a>備註  
 `SetFieldNull`繫結中的欄位`DoFieldExchange`機制。  
  
 當您新增新的記錄至資料錄集時，所有欄位資料成員一開始會設為 Null 值，並標示為 「 中途 」 （變更）。 當您從資料來源擷取一筆記錄時，其資料行已經有值或都是 Null。 如果不是適當欄位設為 Null， [CDaoException](../../mfc/reference/cdaoexception-class.md)就會擲回。  
  
 如果您使用雙重緩衝機制，例如，如果您特別想要將目前記錄的欄位指定為沒有值，呼叫`SetFieldNull`與`bNull`設**TRUE**加上旗標為 Null。 如果先前已將某個欄位標記 Null，而且現在想要將其值，只要設定其新值。 您不需要移除 Null 旗標`SetFieldNull`。 若要判斷此欄位是否可為 Null，請呼叫[IsFieldNullable](#isfieldnullable)。  
  
 如果您不使用雙重緩衝機制，然後變更欄位的值不會自動設定欄位為中途和非 Null。 中途和非 Null，您必須特別設定的欄位。 中所包含的旗標[m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)控制這項自動欄位檢查。  
  
 DFX 機制會使用**PSEUDONULL**。 如需詳細資訊，請參閱[CDaoFieldExchange::m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)。  
  
> [!NOTE]
>  呼叫此成員函式呼叫之後，才[編輯](#edit)或[AddNew](#addnew)。  
  
 使用**NULL**函式的第一個引數只能套用函式的**outputColumn**欄位中不**param**欄位`CDaoFieldExchange`。 例如，呼叫  
  
 [!code-cpp[NVC_MFCDatabase #&8;](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]  
  
 集合只**outputColumn**欄位**NULL**;**param**欄位不會受到影響。  
  
##  <a name="setfieldvalue"></a>CDaoRecordset::SetFieldValue  
 呼叫此成員函式，若要設定的值 欄位中，依序數位置，或藉由變更字串的值。  
  
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
 包含欄位名稱的字串指標。  
  
 `varValue`  
 參考[COleVariant](../../mfc/reference/colevariant-class.md)物件，其中包含的欄位內容的值。  
  
 `nIndex`  
 整數，表示欄位的序數位置 （以零為起始） 的資料錄集的欄位集合中。  
  
 `lpszValue`  
 字串，包含值的欄位內容的指標。  
  
### <a name="remarks"></a>備註  
 使用`SetFieldValue`和[GetFieldValue](#getfieldvalue)以動態方式在執行的階段而不是以靜態方式使用繫結資料行繫結欄位[DoFieldExchange](#dofieldexchange)機制。  
  
 請注意，是否您沒有建立 UNICODE 資料錄集，您必須使用一種`SetFieldValue`不包含`COleVariant`參數，或`COleVariant`物件必須明確宣告 ANSI。 這可以經由使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)**形式的建構函式與`vtSrc`設`VT_BSTRT`(ANSI) 或使用**COleVariant**函式[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)**與`vtSrc`設為`VT_BSTRT`。  
  
 如需相關資訊，請參閱 「 欄位物件 」 和 「 值屬性 」 中 DAO 說明主題。  
  
##  <a name="setfieldvaluenull"></a>CDaoRecordset::SetFieldValueNull  
 呼叫此成員函式可將欄位設定為 Null 值。  
  
```  
void SetFieldValueNull(int nIndex);  
void SetFieldValueNull(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 在資料錄集中的以零為起始的索引查閱欄位的索引。  
  
 `lpszName`  
 依名稱查閱中的資料錄集欄位名稱。  
  
### <a name="remarks"></a>備註  
 C + + **NULL**不是 Null，表示，在資料庫術語中，相同 」 有任何值 」。  
  
 如需相關資訊，請參閱 「 欄位物件 」 和 「 值屬性 」 中 DAO 說明主題。  
  
##  <a name="setlockingmode"></a>CDaoRecordset::SetLockingMode  
 呼叫此成員函式設定的鎖定資料錄集類型。  
  
```  
void SetLockingMode(BOOL bPessimistic);
```  
  
### <a name="parameters"></a>參數  
 *bPessimistic*  
 旗標，指出鎖定的類型。  
  
### <a name="remarks"></a>備註  
 當您呼叫封閉式鎖定時作用中，包含您要編輯的記錄 2 K 頁面鎖定**編輯**成員函式。 頁面已解除鎖定，當您呼叫**更新**或**關閉**成員函式或任何移動或尋找作業。  
  
 開放式鎖定是作用中時包含記錄的 2 K 頁面鎖定與更新記錄時，才**更新**成員函式。  
  
 如果頁面已被鎖定，沒有其他使用者可以編輯在相同頁面上的記錄。 如果您呼叫`SetLockingMode`和傳遞非零值和另一位使用者已經有鎖定的頁面，當您呼叫時擲回例外狀況**編輯**。 其他使用者可以讀取鎖定分頁的資料。  
  
 如果您呼叫`SetLockingMode`具有零值和更新版本呼叫**更新**雖然分頁已由另一位使用者鎖定，就會發生例外狀況。 若要查看您記錄的另一位使用者所做的變更 （並捨棄變更），呼叫`SetBookmark`與目前資料錄的書籤值的成員函式。  
  
 當使用 ODBC 資料來源，總是開放式鎖定模式。  
  
##  <a name="setparamvalue"></a>CDaoRecordset::SetParamValue  
 呼叫此成員函式在執行階段資料錄集中設定的參數值。  
  
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
 參數的 recordset 的參數集合中數值位置。  
  
 `var`  
 若要設定; 值請參閱 < 備註 >。  
  
 `lpszName`  
 您想要設定其值的參數名稱。  
  
### <a name="remarks"></a>備註  
 參數必須有已建立資料錄集的 SQL 字串的一部分。 依名稱或其集合中的索引位置，您可以存取的參數。  
  
 指定要設定為值`COleVariant`物件。 如需有關設定所要的值，然後輸入您`COleVariant`物件，請參閱類別[COleVariant](../../mfc/reference/colevariant-class.md)。 請注意，如果您不想要建立的 UNICODE 資料錄集，則`COleVariant`物件必須明確宣告 ANSI。 這可以經由使用[COleVariant::COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** `lpszSrc` **，** `vtSrc` **)**形式的建構函式與`vtSrc`設`VT_BSTRT`(ANSI) 或使用**COleVariant**函式[SetString](../../mfc/reference/colevariant-class.md#setstring)**(** `lpszSrc` **，** `vtSrc` **)**與`vtSrc`設為`VT_BSTRT`。  
  
##  <a name="setparamvaluenull"></a>CDaoRecordset::SetParamValueNull  
 呼叫此成員函式將參數設定為 Null 值。  
  
```  
void SetParamValueNull(int nIndex);  
void SetParamValueNull(LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>參數  
 `nIndex`  
 在資料錄集中的以零為起始的索引查閱欄位的索引。  
  
 `lpszName`  
 依名稱查閱中的資料錄集欄位名稱。  
  
### <a name="remarks"></a>備註  
 C + + **NULL**不是 Null，表示，在資料庫術語中，相同 」 有任何值 」。  
  
##  <a name="setpercentposition"></a>CDaoRecordset::SetPercentPosition  
 呼叫此成員函式設定值，以變更目前的記錄中資料錄集的資料錄的百分比為基礎的資料錄集物件中的概略位置。  
  
```  
void SetPercentPosition(float fPosition);
```  
  
### <a name="parameters"></a>參數  
 *fPosition*  
 介於 0 與 100 之間的數字。  
  
### <a name="remarks"></a>備註  
 使用動態類型或快照集類型資料錄集時，先將資料填入資料錄集移到最後一個記錄才能呼叫`SetPercentPosition`。 如果您呼叫`SetPercentPosition`之前完全填入資料錄集，是相對於存取的值所指示的記錄數目的移動量[GetRecordCount](#getrecordcount)。 您可以移動至最後一筆記錄呼叫`MoveLast`。  
  
 一旦您呼叫`SetPercentPosition`，變成目前的值的約略位置記錄。  
  
> [!NOTE]
>  呼叫`SetPercentPosition`移動至資料錄集中指定的記錄目前的記錄不建議使用。 呼叫[SetBookmark](#setbookmark)成員函式。  
  
 如需相關資訊，請參閱主題 DAO 說明中的 「 PercentPosition 屬性 」。  
  
##  <a name="update"></a>CDaoRecordset::Update  
 呼叫此成員函式呼叫之後`AddNew`或**編輯**成員函式。  
  
```  
virtual void Update();
```  
  
### <a name="remarks"></a>備註  
 這個呼叫才可完成`AddNew`或**編輯**作業。  
  
 同時`AddNew`和**編輯**準備儲存至資料來源中的新增或編輯過的資料放在其中編輯緩衝區。 **更新**儲存資料。 只有這些欄位標記，或偵測到變更時都會更新。  
  
 如果資料來源支援交易，您可以將**更新**呼叫 (和其相對應`AddNew`或**編輯**呼叫) 交易的一部分。  
  
> [!CAUTION]
>  如果您呼叫**更新**但未先呼叫`AddNew`或**編輯**，**更新**會擲回`CDaoException`。 如果您呼叫`AddNew`或**編輯**，您必須呼叫**更新**之前先呼叫[MoveNext](#movenext)或關閉資料錄集或資料來源連接。 否則，您的變更都會遺失而不另行通知。  
  
 當資料錄集物件要以保守模式鎖定在多使用者環境中時，記錄就會保持鎖定的時間**編輯**更新已完成之前使用。 如果在樂觀地鎖定資料錄集，記錄會鎖定及更新資料庫中之前，相較於預先編輯的記錄。 如果記錄有所變更，因為您呼叫**編輯**、**更新**作業將會失敗，而且 MFC 擲回例外狀況。 您可以變更的鎖定模式`SetLockingMode`。  
  
> [!NOTE]
>  在外部資料庫格式，例如 ODBC 和可安裝的 ISAM 一律使用開放式鎖定。  
  
 如需相關資訊，請參閱 「 AddNew 方法 」、 「 CancelUpdate 方法 」、 「 刪除方法 」、 「 LastModified 屬性 」、 「 更新方法 」 和 DAO 說明中的 「 EditMode 屬性 」 的主題。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)   
 [CDaoWorkspace 類別](../../mfc/reference/cdaoworkspace-class.md)   
 [CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)   
 [CDaoQueryDef 類別](../../mfc/reference/cdaoquerydef-class.md)

