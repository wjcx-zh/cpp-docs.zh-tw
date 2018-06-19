---
title: CDatabase 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDatabase
- AFXDB/CDatabase
- AFXDB/CDatabase::CDatabase
- AFXDB/CDatabase::BeginTrans
- AFXDB/CDatabase::BindParameters
- AFXDB/CDatabase::Cancel
- AFXDB/CDatabase::CanTransact
- AFXDB/CDatabase::CanUpdate
- AFXDB/CDatabase::Close
- AFXDB/CDatabase::CommitTrans
- AFXDB/CDatabase::ExecuteSQL
- AFXDB/CDatabase::GetBookmarkPersistence
- AFXDB/CDatabase::GetConnect
- AFXDB/CDatabase::GetCursorCommitBehavior
- AFXDB/CDatabase::GetCursorRollbackBehavior
- AFXDB/CDatabase::GetDatabaseName
- AFXDB/CDatabase::IsOpen
- AFXDB/CDatabase::OnSetOptions
- AFXDB/CDatabase::Open
- AFXDB/CDatabase::OpenEx
- AFXDB/CDatabase::Rollback
- AFXDB/CDatabase::SetLoginTimeout
- AFXDB/CDatabase::SetQueryTimeout
- AFXDB/CDatabase::m_hdbc
dev_langs:
- C++
helpviewer_keywords:
- CDatabase [MFC], CDatabase
- CDatabase [MFC], BeginTrans
- CDatabase [MFC], BindParameters
- CDatabase [MFC], Cancel
- CDatabase [MFC], CanTransact
- CDatabase [MFC], CanUpdate
- CDatabase [MFC], Close
- CDatabase [MFC], CommitTrans
- CDatabase [MFC], ExecuteSQL
- CDatabase [MFC], GetBookmarkPersistence
- CDatabase [MFC], GetConnect
- CDatabase [MFC], GetCursorCommitBehavior
- CDatabase [MFC], GetCursorRollbackBehavior
- CDatabase [MFC], GetDatabaseName
- CDatabase [MFC], IsOpen
- CDatabase [MFC], OnSetOptions
- CDatabase [MFC], Open
- CDatabase [MFC], OpenEx
- CDatabase [MFC], Rollback
- CDatabase [MFC], SetLoginTimeout
- CDatabase [MFC], SetQueryTimeout
- CDatabase [MFC], m_hdbc
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb71b31fa3133b4e1b93564ef0b530cb20bb3dfc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375108"
---
# <a name="cdatabase-class"></a>CDatabase 類別
表示資料來源的連接，您可以透過這個連接來操作資料來源。  
  
## <a name="syntax"></a>語法  
  
```  
class CDatabase : public CObject  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDatabase::CDatabase](#cdatabase)|建構 `CDatabase` 物件。 您必須藉由呼叫初始化物件`OpenEx`或**開啟**。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDatabase::BeginTrans](#begintrans)|啟動 「 交易 」 — 一系列的回復呼叫`AddNew`，**編輯**，**刪除**，和**更新**類別成員函式`CRecordset`— 上連接的資料來源。 資料來源必須支援的交易**BeginTrans**才能發生效用。|  
|[CDatabase::BindParameters](#bindparameters)|可讓您將繫結參數，然後再呼叫`CDatabase::ExecuteSQL`。|  
|[CDatabase::Cancel](#cancel)|取消非同步作業或從第二個執行緒處理序。|  
|[CDatabase::CanTransact](#cantransact)|傳回非零，如果資料來源支援交易。|  
|[CDatabase::CanUpdate](#canupdate)|傳回非零，如果`CDatabase`是可更新的物件 （不唯讀）。|  
|[CDatabase::Close](#close)|關閉資料來源連接。|  
|[CDatabase::CommitTrans](#committrans)|完成開始異動**BeginTrans**。 在交易中改變資料來源的命令會執行。|  
|[Cdatabase:: Executesql](#executesql)|執行 SQL 陳述式。 會不傳回任何資料。|  
|[CDatabase::GetBookmarkPersistence](#getbookmarkpersistence)|識別保存書籤資料錄集物件的作業。|  
|[CDatabase::GetConnect](#getconnect)|傳回用來連接的 ODBC 連接字串`CDatabase`到資料來源的物件。|  
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|識別認可異動的開啟資料錄集物件上的效果。|  
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|識別開啟的資料錄集物件上回復交易的效果。|  
|[CDatabase::GetDatabaseName](#getdatabasename)|傳回目前使用中資料庫的名稱。|  
|[CDatabase::IsOpen](#isopen)|傳回非零，如果`CDatabase`物件目前連線至資料來源。|  
|[CDatabase::OnSetOptions](#onsetoptions)|由架構呼叫以設定標準的連接選項。 預設實作會設定查詢逾時值。 您可以藉由呼叫來建立這些選項，事先`SetQueryTimeout`。|  
|[CDatabase::Open](#open)|建立資料來源 （透過 ODBC 驅動程式） 的連接。|  
|[CDatabase::OpenEx](#openex)|建立資料來源 （透過 ODBC 驅動程式） 的連接。|  
|[CDatabase::Rollback](#rollback)|反轉目前交易期間所做的變更。 資料來源傳回至其先前的狀態，在定義**BeginTrans**呼叫時，不變。|  
|[CDatabase::SetLoginTimeout](#setlogintimeout)|設定之後資料來源的連接嘗試會逾時秒數。|  
|[CDatabase::SetQueryTimeout](#setquerytimeout)|設定資料庫之後的秒數查詢作業會逾時。會影響所有後續的資料錄集**開啟**， `AddNew`，**編輯**，和**刪除**呼叫。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDatabase::m_hdbc](#m_hdbc)|開啟資料庫連接 (ODBC) 資料來源的連接控制代碼。 型別**HDBC**。|  
  
## <a name="remarks"></a>備註  
 資料來源是資料的某些資料庫管理系統 (DBMS) 所裝載的特定執行個體。 範例包括 Microsoft SQL Server、 Microsoft Access、 Borland dBASE 和 xBASE。 您可以有一或多個`CDatabase`一次應用程式中作用中的物件。  
  
> [!NOTE]
>  如果您正在使用的資料存取物件 (DAO) 類別，而不是開放式資料庫連接 (ODBC) 類別，使用類別[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)改為。 如需詳細資訊，請參閱文章[概觀： 資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。  
  
 若要使用`CDatabase`，建構`CDatabase`物件並呼叫其`OpenEx`成員函式。 這會開啟連接。 當您然後建構`CRecordset`連接的資料來源上運作的物件傳遞的資料錄集建構函式的指標，您`CDatabase`物件。 當您完成使用連接時，呼叫**關閉**成員函式，並終結`CDatabase`物件。 **關閉**關閉任何先前未關閉的資料錄集。  
  
 如需有關`CDatabase`，請參閱文章[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)和[概觀： 資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDatabase`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxdb.h  
  
##  <a name="begintrans"></a>  CDatabase::BeginTrans  
 呼叫此成員函式，進而開始交易與連接的資料來源。  
  
```  
BOOL BeginTrans();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果呼叫成功，會認可變更，只以手動方式;否則便是 0。  
  
### <a name="remarks"></a>備註  
 交易是由所組成的一或多個呼叫`AddNew`，**編輯**，**刪除**，和**更新**的成員函式`CRecordset`物件。 開始交易之前,`CDatabase`物件必須具有已連接到資料來源藉由呼叫其`OpenEx`或**開啟**成員函式。 若要結束交易，呼叫[CommitTrans](#committrans)接受資料來源的所有變更 （及執行這些步驟），或呼叫[復原](#rollback)中止整個交易。 呼叫**BeginTrans**之後您開啟任何資料錄集參與異動的和做為接近實際更新作業越好。  
  
> [!CAUTION]
>  根據您的 ODBC 驅動程式，開啟資料錄集，然後再呼叫**BeginTrans**呼叫時可能會造成問題**復原**。 您應該檢查您使用特定驅動程式。 比方說，當 Microsoft ODBC Desktop Driver Pack 3.0 中包含的 Microsoft Access 驅動程式，您必須考慮 Jet 資料庫引擎的需求，您不應該開始已開啟的資料指標的任何資料庫上的交易。 在 MFC 資料庫類別中，開啟的資料指標表示開啟`CRecordset`物件。 如需詳細資訊，請參閱[技術提示 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md)。  
  
 **BeginTrans**在伺服器上，視要求的並行處理和資料來源的功能而定也可能會鎖定資料錄。 鎖定資料的相關資訊，請參閱文章[資料錄集： 鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)。  
  
 本文說明使用者定義交易[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
 **BeginTrans**建立的交易序列可以復原的狀態 （相反）。 若要建立的新狀態的回復，認可任何目前的交易，然後呼叫**BeginTrans**一次。  
  
> [!CAUTION]
>  呼叫**BeginTrans**一次而不需呼叫**CommitTrans**或**復原**是錯誤。  
  
 呼叫[CanTransact](#cantransact)成員函式來判斷您的驅動程式是否支援給定的資料庫交易。 您也應該呼叫[GetCursorCommitBehavior](#getcursorcommitbehavior)和[GetCursorRollbackBehavior](#getcursorrollbackbehavior)判斷要保留資料指標支援。  
  
 如需有關交易的詳細資訊，請參閱文章[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
### <a name="example"></a>範例  
  請參閱文章[交易： 資料錄集 (ODBC) 中執行異動](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
##  <a name="bindparameters"></a>  CDatabase::BindParameters  
 覆寫`BindParameters`當您需要繫結參數，然後再呼叫[cdatabase:: Executesql](#executesql)。  
  
```  
virtual void BindParameters(HSTMT hstmt);
```  
  
### <a name="parameters"></a>參數  
 `hstmt`  
 ODBC 陳述式控制代碼，您要將參數繫結。  
  
### <a name="remarks"></a>備註  
 這種方法時，您不需要將結果從預存程序設定。  
  
 在您的覆寫呼叫**SQLBindParameters**和相關的繫結參數的 ODBC 函數。 MFC 呼叫之前呼叫覆寫`ExecuteSQL`。 您不需要呼叫**SQLPrepare**;`ExecuteSQL`呼叫**SQLExecDirect**並終結**hstmt**，其中只有使用一次。  
  
##  <a name="cancel"></a>  CDatabase::Cancel  
 呼叫此成員函式，來要求資料來源取消非同步作業進行中的或從第二個執行緒的程序。  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>備註  
 請注意，MFC ODBC 類別不會再使用非同步處理。若要執行的非同步作業，您必須直接呼叫 ODBC API 函式[SQLSetConnectOption](https://msdn.microsoft.com/library/ms713564.aspx)。 如需詳細資訊，請參閱[非同步執行](https://msdn.microsoft.com/library/ms713563.aspx)Windows SDK 中。  
  
##  <a name="cantransact"></a>  CDatabase::CanTransact  
 呼叫此成員函式，以判斷資料庫是否允許交易。  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果使用這個資料錄集`CDatabase`物件允許交易; 否則為 0。  
  
### <a name="remarks"></a>備註  
 交易的相關資訊，請參閱文章[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="canupdate"></a>  CDatabase::CanUpdate  
 呼叫此成員函式，以判斷是否`CDatabase`物件可用來更新。  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果`CDatabase`物件可用來更新; 否則為 0，表示可能是您傳遞**TRUE**中`bReadOnly`開啟時`CDatabase`物件或資料來源本身是唯讀的。 資料來源是唯讀的呼叫 ODBC API 函式如果**SQLGetInfo**如**SQL_DATASOURCE_READ_ONLY**傳回"y"。  
  
### <a name="remarks"></a>備註  
 並非所有的驅動程式支援的更新。  
  
##  <a name="cdatabase"></a>  CDatabase::CDatabase  
 建構 `CDatabase` 物件。  
  
```  
CDatabase();
```  
  
### <a name="remarks"></a>備註  
 之後建構物件，您必須呼叫其`OpenEx`或**開啟**成員函式來建立指定之資料來源的連接。  
  
 您可能會發現很方便內嵌`CDatabase`文件類別中的物件。  
  
### <a name="example"></a>範例  
 這個範例說明使用`CDatabase`中`CDocument`-衍生的類別。  
  
 [!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]  
  
 [!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]  
  
##  <a name="close"></a>  CDatabase::Close  
 如果您想要從資料來源中斷連線，請呼叫此成員函式。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 您必須先關閉任何與相關聯的資料錄集`CDatabase`物件前呼叫此成員函式。 因為**關閉**將不會終結`CDatabase`物件，您可以藉由開啟相同的資料來源或不同的資料來源的新連接重複使用物件。  
  
 所有暫止`AddNew`或**編輯**使用資料庫的資料錄集的陳述式會取消，且所有擱置的交易都會回復。 相依於任何資料錄集`CDatabase`物件會處於未定義的狀態。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]  
  
##  <a name="committrans"></a>  CDatabase::CommitTrans  
 呼叫完成的交易之後此成員函式。  
  
```  
BOOL CommitTrans();
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果更新已成功認可。否則便是 0。 如果**CommitTrans**失敗，資料來源的狀態是未定義。 您必須檢查資料，以判斷它的狀態。  
  
### <a name="remarks"></a>備註  
 交易包含一系列的呼叫`AddNew`，**編輯**，**刪除**，和**更新**的成員函式`CRecordset`開頭的物件若要呼叫[BeginTrans](#begintrans)成員函式。 **CommitTrans**認可交易。 根據預設，更新已被認可立即;呼叫**BeginTrans**導致承諾的更新會延遲到**CommitTrans**呼叫。  
  
 直到您呼叫**CommitTrans**結束交易，您可以呼叫[復原](#rollback)中止交易，並將資料來源保留在其原始狀態的成員函式。 若要開始新交易，請呼叫**BeginTrans**一次。  
  
 如需有關交易的詳細資訊，請參閱文章[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
### <a name="example"></a>範例  
  請參閱文章[交易： 資料錄集 (ODBC) 中執行異動](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
##  <a name="executesql"></a>  Cdatabase:: Executesql  
 當您需要直接執行 SQL 命令時，請呼叫此成員函式。  
  
```  
void ExecuteSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>參數  
 `lpszSQL`  
 以 null 終止的字串包含有效的 SQL 命令執行的指標。 您可以傳遞[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>備註  
 以 null 終止字串建立的命令。 `ExecuteSQL` 不會傳回資料記錄。 如果您想要處理的記錄，請改為使用資料錄集物件。  
  
 大部分的資料來源的命令會發出透過資料錄集物件，以便選取資料、 插入新的記錄、 刪除資料錄，以及編輯記錄支援的命令。 不過，並非所有 ODBC 直接支援功能的資料庫類別中，因此有時候您可能需要進行直接 SQL 呼叫與`ExecuteSQL`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]  
  
##  <a name="getbookmarkpersistence"></a>  CDatabase::GetBookmarkPersistence  
 呼叫此成員函式，以判定在特定作業之後，記錄集物件上書籤的永續性。  
  
```  
DWORD GetBookmarkPersistence() const;  
```  
  
### <a name="return-value"></a>傳回值  
 位元遮罩，用於識別在記錄集物件上保存書籤所使用的作業。 如需詳細資料，請參閱＜備註＞。  
  
### <a name="remarks"></a>備註  
 例如，如果您呼叫 `CRecordset::GetBookmark`，然後呼叫 `CRecordset::Requery`，則從 `GetBookmark` 取得的書籤可能不再有效。 您應該先呼叫 `GetBookmarkPersistence`，然後再呼叫 `CRecordset::SetBookmark`。  
  
 下表列出可針對 `GetBookmarkPersistence` 的傳回值結合的位元遮罩值。  
  
|位元遮罩值|書籤永續性|  
|-------------------|--------------------------|  
|`SQL_BP_CLOSE`|書籤是之後有效**Requery**作業。|  
|`SQL_BP_DELETE`|資料列的書籤是之後有效**刪除**作業，該資料列。|  
|`SQL_BP_DROP`|書籤是之後有效**關閉**作業。|  
|`SQL_BP_SCROLL`|書籤之後會有效**移動**作業。 這可輕鬆地識別記錄集上是否支援書籤，如 `CRecordset::CanBookmark` 所傳回的那樣。|  
|`SQL_BP_TRANSACTION`|書籤在認可或回復異動之後有效。|  
|`SQL_BP_UPDATE`|資料列的書籤是之後有效**更新**作業，該資料列。|  
|`SQL_BP_OTHER_HSTMT`|與一個記錄集物件相關聯的書籤在第二個記錄集上有效。|  
  
 如需有關這個傳回值的詳細資訊，請參閱 ODBC API 函式**SQLGetInfo** Windows SDK 中。 如需書籤的詳細資訊，請參閱文章[資料錄集： 書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。  
  
##  <a name="getconnect"></a>  CDatabase::GetConnect  
 呼叫此成員函式擷取的呼叫期間所使用的連接字串`OpenEx`或`Open`連接`CDatabase`到資料來源的物件。  
  
```  
const CString GetConnect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A `const` [CString](../../atl-mfc-shared/reference/cstringt-class.md)包含連接字串，如果`OpenEx`或`Open`已呼叫; 否則為空字串。  
  
### <a name="remarks"></a>備註  
 請參閱[CDatabase::Open](#open)如需如何建立連接字串的說明。  
  
##  <a name="getcursorcommitbehavior"></a>  CDatabase::GetCursorCommitBehavior  
 呼叫此成員函式，以判斷如何[CommitTrans](#committrans)作業會影響資料指標在開啟資料錄集物件上的。  
  
```  
int GetCursorCommitBehavior() const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，表示開啟資料錄集物件上的交易的效果。 如需詳細資料，請參閱＜備註＞。  
  
### <a name="remarks"></a>備註  
 下表列出可能的傳回值，如`GetCursorCommitBehavior`而開啟的資料錄集對應的效果。  
  
|傳回值|CRecordset 物件上的效果|  
|------------------|----------------------------------|  
|`SQL_CB_CLOSE`|呼叫`CRecordset::Requery`緊接的交易認可。|  
|`SQL_CB_DELETE`|呼叫`CRecordset::Close`緊接的交易認可。|  
|`SQL_CB_PRESERVE`|繼續正常進行`CRecordset`作業。|  
  
 如需有關這個傳回值的詳細資訊，請參閱 ODBC API 函式**SQLGetInfo** Windows SDK 中。 如需有關交易的詳細資訊，請參閱文章[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="getcursorrollbackbehavior"></a>  CDatabase::GetCursorRollbackBehavior  
 呼叫此成員函式，以判斷如何[復原](#rollback)作業會影響資料指標在開啟資料錄集物件上的。  
  
```  
int GetCursorRollbackBehavior() const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，表示開啟資料錄集物件上的交易的效果。 如需詳細資料，請參閱＜備註＞。  
  
### <a name="remarks"></a>備註  
 下表列出可能的傳回值，如`GetCursorRollbackBehavior`而開啟的資料錄集對應的效果。  
  
|傳回值|CRecordset 物件上的效果|  
|------------------|----------------------------------|  
|`SQL_CB_CLOSE`|呼叫`CRecordset::Requery`緊接交易回復。|  
|`SQL_CB_DELETE`|呼叫`CRecordset::Close`緊接交易回復。|  
|`SQL_CB_PRESERVE`|繼續正常進行`CRecordset`作業。|  
  
 如需有關這個傳回值的詳細資訊，請參閱 ODBC API 函式**SQLGetInfo** Windows SDK 中。 如需有關交易的詳細資訊，請參閱文章[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="getdatabasename"></a>  CDatabase::GetDatabaseName  
 呼叫此成員函式 （前提是資料來源會定義具名的物件，稱為 「 資料庫 」） 擷取目前連接之資料庫的名稱。  
  
```  
CString GetDatabaseName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)如果成功，否則為包含資料庫名稱、 空白`CString`。  
  
### <a name="remarks"></a>備註  
 這不是資料來源名稱 (DSN) 中指定相同`OpenEx`或**開啟**呼叫。 什麼`GetDatabaseName`傳回取決於 ODBC。 一般而言，資料庫是資料表的集合。 如果此實體有名稱，`GetDatabaseName`它傳回。  
  
 您，例如，可以在標題中顯示此名稱。 如果發生錯誤時擷取的名稱，從 ODBC，`GetDatabaseName`傳回空**Cstring**。  
  
##  <a name="isopen"></a>  CDatabase::IsOpen  
 呼叫此成員函式，以判斷是否`CDatabase`物件目前連線至資料來源。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果`CDatabase`目前連接物件; 否則為 0。  
  
##  <a name="m_hdbc"></a>  CDatabase::m_hdbc  
 包含公用的 ODBC 資料來源連接控制代碼，「 連接控制代碼 」。  
  
### <a name="remarks"></a>備註  
 一般來說，就不需要直接存取此成員變數。 相反地，架構會配置控制代碼呼叫時`OpenEx`或**開啟**。 架構會呼叫時，取消配置控制代碼**刪除**運算子`CDatabase`物件。 請注意，**關閉**成員函式不會將它們取消配置的控制代碼。  
  
 不過，在某些情況下，您可能需要直接使用此控制代碼。 例如，如果您需要呼叫 ODBC API 函式直接而不是透過類別`CDatabase`，您可能需要連接控制代碼將做為參數傳遞。 下列程式碼範例，請參閱。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]  
  
##  <a name="onsetoptions"></a>  CDatabase::OnSetOptions  
 直接執行的 SQL 陳述式時，架構會呼叫此成員函式`ExecuteSQL`成員函式。  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>參數  
 `hstmt`  
 ODBC 陳述式控制代碼，設定選項。  
  
### <a name="remarks"></a>備註  
 `CRecordset::OnSetOptions` 也會呼叫此成員函式。  
  
 `OnSetOptions` 設定登入逾時值。 如果已有先前呼叫`SetQueryTimeout`成員函式，`OnSetOptions`會反映目前的值; 否則它會將預設值。  
  
> [!NOTE]
>  在 MFC 4.2 之前`OnSetOptions`也設定處理模式為任一 snychronous 或非同步。 從 MFC 4.2 開始，所有作業都都會同步。 若要執行非同步作業，您必須進行直接呼叫 ODBC API 函式**SQLSetPos**。  
  
 您不需要覆寫`OnSetOptions`變更逾時值。 相反地，若要自訂的查詢逾時值，請呼叫`SetQueryTimeout`再建立資料錄集。`OnSetOptions`將會使用新的值。 設定的值套用至所有資料錄集或直接 SQL 呼叫後續作業。  
  
 覆寫`OnSetOptions`如果您想要設定其他選項。 您的覆寫應該呼叫基底類別`OnSetOptions`之前或之後呼叫 ODBC API 函式**SQLSetStmtOption**。 請依照下列架構的預設實作中所述的方法`OnSetOptions`。  
  
##  <a name="open"></a>  CDatabase::Open  
 呼叫此成員函式，來初始化新建構`CDatabase`物件。  
  
```  
virtual BOOL Open(
    LPCTSTR lpszDSN,  
    BOOL bExclusive = FALSE,  
    BOOL bReadOnly = FALSE,  
    LPCTSTR lpszConnect = _T("ODBC;"),  
    BOOL bUseCursorLib = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `lpszDSN`  
 指定資料來源名稱，已登錄的名稱與 ODBC 透過 ODBC 管理員程式。 如果資料來源名稱值中指定了`lpszConnect`(形式"DSN =\<資料來源 > 」)，它不可指定一次在`lpszDSN`。 在此情況下，`lpszDSN`應該**NULL**。 否則，您可以傳遞**NULL**如果您想要對使用者顯示資料來源 對話方塊，使用者可在其中選取資料來源。 如需詳細資訊，請參閱 < 備註 >。  
  
 `bExclusive`  
 不支援這個版本的類別庫。 目前，判斷提示失敗，則此參數**TRUE**。 永遠開啟資料來源，以共用的 （不是唯一的）。  
  
 `bReadOnly`  
 **TRUE**如果您想連接處於唯讀模式，並禁止資料來源的更新。 所有相依的資料錄集繼承這個屬性。 預設值是**FALSE**。  
  
 `lpszConnect`  
 指定的連接字串。 連接字串串連的資訊，可能包括資料來源名稱、 有效的使用者識別碼上的資料來源、 使用者驗證的字串 （密碼，如果資料來源需要一個） 和其他資訊。 將整個連接字串必須加上字串"ODBC"。（大寫或小寫）。 「 ODBC 」; 字串會用來表示連接加入 ODBC 資料來源;當此方法的向上相容性的類別庫的未來版本可能會支援非 ODBC 資料來源。  
  
 `bUseCursorLib`  
 **TRUE**如果您想要載入的 ODBC 資料指標程式庫 DLL。 資料指標程式庫會遮罩某些功能的基礎的 ODBC 驅動程式，有效防止動態集的使用 （如果此驅動程式支援它們）。 只支援如果資料指標程式庫已載入的資料指標是靜態的快照集和順向資料指標。 預設值是**TRUE**。 如果您打算建立資料錄集物件，直接從`CRecordset`而不需衍生自它，您不可以載入資料指標程式庫。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已成功建立連接。否則為 0，如果使用者選擇時，取消顯示一個對話方塊，要求連線的詳細資訊。 在其他情況下，架構會擲回例外狀況。  
  
### <a name="remarks"></a>備註  
 必須初始化資料庫物件，您可以使用它來建構資料錄集物件。  
  
> [!NOTE]
>  呼叫[OpenEx](#openex)成員函式是連接到資料來源，並初始化您的資料庫物件的慣用的方法。  
  
 如果在參數您**開啟**呼叫未包含足夠的資訊來進行連接，ODBC 驅動程式會開啟對話方塊，以向使用者取得所需的資訊。 當您呼叫**開啟**，您的連接字串， `lpszConnect`，私下在儲存`CDatabase`物件，並可透過呼叫[GetConnect](#getconnect)成員函式。  
  
 如果您希望，您就可以開啟您自己的對話方塊中，才能呼叫**開啟**取得資訊與使用者，例如密碼，然後將該資訊 」 至連接字串傳遞給**開啟**。 或者您可能想要儲存連接字串，如此您就可以重複使用它的下一步，您傳遞時間應用程式呼叫**開啟**上`CDatabase`物件。  
  
 您也可以使用多個層級的登入授權 」 的連接字串 (每個不同`CDatabase`物件) 或傳遞其他資料來源特定的資訊。 如需有關連接字串的詳細資訊，請參閱 Windows SDK 中第 5 章。  
  
 很可能連線嘗試逾時的時候，例如 DBMS 主機無法使用時。 如果連接嘗試失敗，**開啟**會擲回`CDBException`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]  
  
##  <a name="openex"></a>  CDatabase::OpenEx  
 呼叫此成員函式，來初始化新建構`CDatabase`物件。  
  
```  
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,  
    DWORD dwOptions = 0);
```  
  
### <a name="parameters"></a>參數  
 `lpszConnectString`  
 指定 ODBC 連接字串。 這包括資料來源名稱，以及其他選擇性資訊，例如使用者識別碼和密碼。 例如，"DSN = SQLServer_Source;UID = SA。PWD = abc123"是可能的連接字串。 請注意，如果您傳遞**NULL**如`lpszConnectString`，資料來源 對話方塊會提示使用者選取的資料來源。  
  
 `dwOptions`  
 位元遮罩，指定下列值的組合。 預設值為 0，表示資料庫將會開啟以寫入存取權與共用，ODBC 資料指標程式庫 DLL 將不會載入，和 ODBC 連接對話方塊會顯示只有當沒有足夠的資訊來進行連接。  
  
- **CDatabase::openExclusive**類別庫的這個版本不支援。 永遠開啟資料來源，以共用的 （不是唯一的）。 目前，如果您指定這個選項，就會失敗判斷提示。  
  
- **CDatabase::openReadOnly**開啟資料來源，以唯讀狀態。  
  
- **CDatabase::useCursorLib**載入 ODBC 資料指標程式庫 DLL。 資料指標程式庫會遮罩某些功能的基礎的 ODBC 驅動程式，有效防止動態集的使用 （如果此驅動程式支援它們）。 只支援如果資料指標程式庫已載入的資料指標是靜態的快照集和順向資料指標。 如果您打算建立資料錄集物件，直接從`CRecordset`而不需衍生自它，您不可以載入資料指標程式庫。  
  
- **CDatabase::noOdbcDialog**不會顯示 ODBC 連線 對話方塊中，不論是否提供足夠的連接資訊。  
  
- **CDatabase::forceOdbcDialog**一律顯示 ODBC 連接對話方塊。  
  
### <a name="return-value"></a>傳回值  
 為非零，如果已成功建立連接。否則為 0，如果使用者選擇時，取消顯示一個對話方塊，要求連線的詳細資訊。 在其他情況下，架構會擲回例外狀況。  
  
### <a name="remarks"></a>備註  
 必須初始化資料庫物件，您可以使用它來建構資料錄集物件。  
  
 如果`lpszConnectString`參數中的您`OpenEx`呼叫未包含足夠的資訊來進行連接，ODBC 驅動程式會開啟對話方塊，以從使用者取得所需的資訊，提供您沒有設定**CDatabase::noOdbcDialog**或**CDatabase::forceOdbcDialog**中`dwOptions`參數。 當您呼叫`OpenEx`，您的連接字串， `lpszConnectString`，私下在儲存`CDatabase`物件，並可透過呼叫[GetConnect](#getconnect)成員函式。  
  
 如果您希望，您就可以開啟您自己的對話方塊中，才能呼叫`OpenEx`從使用者，例如密碼取得資訊，並將該資訊新增到連接字串傳遞給`OpenEx`。 或者您可能想要儲存連接字串，如此您就可以重複使用它的下一步，您傳遞時間應用程式呼叫`OpenEx`上`CDatabase`物件。  
  
 您也可以使用多個層級的登入授權 」 的連接字串 (每個不同`CDatabase`物件) 或傳遞其他資料來源特定的資訊。 如需連接字串的詳細資訊，請參閱 < 在第 6 章*ODBC 程式設計人員參考*。  
  
 很可能連線嘗試逾時的時候，例如 DBMS 主機無法使用時。 如果連接嘗試失敗，`OpenEx`會擲回`CDBException`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]  
  
##  <a name="rollback"></a>  CDatabase::Rollback  
 呼叫此成員函式可反轉交易期間所做的變更。  
  
```  
BOOL Rollback();
```  
  
### <a name="return-value"></a>傳回值  
 如果交易已成功取消; 非零，否則便是 0。 如果**復原**呼叫失敗，資料來源和交易狀態是未定義。 如果**復原**傳回 0，您必須檢查資料來源以判斷它的狀態。  
  
### <a name="remarks"></a>備註  
 所有`CRecordset` `AddNew`，**編輯**，**刪除**，和**更新**自上次執行的呼叫[BeginTrans](#begintrans)回復回到該呼叫時的狀態。  
  
 呼叫之後**復原**，交易已經結束，而且您必須呼叫**BeginTrans**再為另一個交易。 目前您在呼叫之前的記錄**BeginTrans**會變成目前的資料錄一次之後**復原**。  
  
 回復之後，復原之前的目前記錄會保留目前。 如需有關資料錄集和資料來源，在復原之後的狀態的詳細資訊，請參閱文章[異動 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
### <a name="example"></a>範例  
  請參閱文章[交易： 資料錄集 (ODBC) 中執行異動](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
##  <a name="setlogintimeout"></a>  CDatabase::SetLoginTimeout  
 呼叫此成員函式 — 之前先呼叫`OpenEx`或**開啟**— 若要覆寫預設允許的秒數之前嘗試的資料來源連接逾時。  
  
```  
void SetLoginTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>參數  
 `dwSeconds`  
 逾時之前嘗試連線所允許的秒數。  
  
### <a name="remarks"></a>備註  
 連接嘗試可能會逾時如果，比方說，DBMS 無法使用。 呼叫**SetLoginTimeout**建構初始化之後`CDatabase`物件，但您的呼叫之前`OpenEx`或**開啟**。  
  
 登入逾時的預設值是 15 秒。 並非所有的資料來源都支援指定的登入逾時值的能力。 如果資料來源不支援逾時，您會收到追蹤輸出，但未發生例外狀況。 值為 0 表示 「 無限 」。  
  
##  <a name="setquerytimeout"></a>  CDatabase::SetQueryTimeout  
 呼叫此成員函式，來覆寫預設允許後續作業連接的資料來源逾時之前的秒數。  
  
```  
void SetQueryTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>參數  
 `dwSeconds`  
 逾時可讓查詢嘗試之前的秒數。  
  
### <a name="remarks"></a>備註  
 由於網路存取問題、 過多的查詢處理時間，以及其他作業可能會逾時。 呼叫`SetQueryTimeout`之前開啟資料錄集，或在呼叫資料錄集的前`AddNew`，**更新**或**刪除**成員函式，如果您想要變更查詢逾時值。 此設定會影響所有後續**開啟**， `AddNew`，**更新**，和**刪除**呼叫任何與此相關聯的資料錄集`CDatabase`物件。 在開啟之後變更資料錄集的查詢逾時值不會變更資料錄集的值。 例如，後續**移動**作業不會使用新的值。  
  
 查詢逾時的預設值是 15 秒。 並非所有的資料來源都支援可設定查詢逾時值的功能。 如果您設定的查詢逾時值為 0 時，不會逾時，就會發生。與資料來源之間的通訊可能會停止回應。 在開發期間，此行為可能很有用的。 如果資料來源不支援逾時，您會收到追蹤輸出，但未發生例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)
