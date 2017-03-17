---
title: "CDatabase 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- database classes [C++], ODBC
- MFC [C++], ODBC
- ODBC [C++], CDatabase class
- ODBC database class
- database connections [C++], CDatabase class
- CDatabase class
ms.assetid: bd0de70a-e3c3-4441-bcaa-bbf434426ca8
caps.latest.revision: 24
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
ms.openlocfilehash: a14025d712f09bef2b6b749d46cac1b1371fd4e3
ms.lasthandoff: 02/24/2017

---
# <a name="cdatabase-class"></a>CDatabase 類別
表示資料來源的連接，您可以透過這個連接來操作資料來源。  
  
## <a name="syntax"></a>語法  
  
```  
class CDatabase : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CDatabase::CDatabase](#cdatabase)|建構 `CDatabase` 物件。 您必須藉由呼叫初始化物件`OpenEx`或**開啟**。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDatabase::BeginTrans](#begintrans)|啟動 「 交易 」: 「 一系列的回復呼叫`AddNew`，**編輯**，**刪除**，和**更新**類別成員函式`CRecordset`â €"連接的資料來源上。 資料來源必須支援交易**BeginTrans**有任何效果。|  
|[CDatabase::BindParameters](#bindparameters)|可讓您繫結參數，然後再呼叫`CDatabase::ExecuteSQL`。|  
|[CDatabase::Cancel](#cancel)|取消非同步作業或從第二個執行緒的處理序。|  
|[CDatabase::CanTransact](#cantransact)|傳回非零，如果資料來源支援交易。|  
|[CDatabase::CanUpdate](#canupdate)|傳回非零值如果`CDatabase`是可更新的物件 （非唯讀狀態）。|  
|[CDatabase::Close](#close)|關閉資料來源連接。|  
|[CDatabase::CommitTrans](#committrans)|完成交易開始時**BeginTrans**。 在交易中改變資料來源的命令會執行。|  
|[CDatabase::ExecuteSQL](#executesql)|執行 SQL 陳述式。 會不傳回任何資料。|  
|[CDatabase::GetBookmarkPersistence](#getbookmarkpersistence)|識別書籤保存資料錄集物件的作業。|  
|[Getconnect](#getconnect)|傳回用來連接的 ODBC 連接字串`CDatabase`到資料來源物件。|  
|[CDatabase::GetCursorCommitBehavior](#getcursorcommitbehavior)|識別的認可交易，以開啟資料錄集物件上的效果。|  
|[CDatabase::GetCursorRollbackBehavior](#getcursorrollbackbehavior)|識別在開啟資料錄集物件上回復交易的效果。|  
|[CDatabase::GetDatabaseName](#getdatabasename)|傳回目前使用中資料庫的名稱。|  
|[CDatabase::IsOpen](#isopen)|傳回非零值如果`CDatabase`物件目前連接至資料來源。|  
|[CDatabase::OnSetOptions](#onsetoptions)|設定標準的連接選項的架構所呼叫。 預設實作會設定查詢逾時值。 您可以藉由呼叫建立這些事先`SetQueryTimeout`。|  
|[CDatabase::Open](#open)|建立資料來源 （透過 ODBC 驅動程式） 的連線。|  
|[CDatabase::OpenEx](#openex)|建立資料來源 （透過 ODBC 驅動程式） 的連線。|  
|[CDatabase::Rollback](#rollback)|反轉目前交易期間所做的變更。 在定義資料來源會傳回其先前的狀態， **BeginTrans**呼叫時，不會更改。|  
|[CDatabase::SetLoginTimeout](#setlogintimeout)|設定之後，資料來源的連接嘗試會逾時秒數。|  
|[CDatabase::SetQueryTimeout](#setquerytimeout)|設定資料庫之後的秒數查詢作業會逾時。 會影響所有後續的資料錄集**開啟**， `AddNew`，**編輯**，和**刪除**呼叫。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|說明|  
|----------|-----------------|  
|[CDatabase::m_hdbc](#m_hdbc)|開啟資料庫連接 (ODBC) 資料來源的連接控制代碼。 型別**HDBC**。|  
  
## <a name="remarks"></a>備註  
 資料來源是資料的某些資料庫管理系統 (DBMS) 所裝載的特定執行個體。 範例包括 Microsoft SQL Server、 Microsoft Access、 Borland dBASE 和 xBASE。 您可以有一或多個`CDatabase`一次應用程式中使用中的物件。  
  
> [!NOTE]
>  如果您正在使用的資料存取物件 (DAO) 類別，而不是開放式資料庫連接 (ODBC) 類別，使用類別[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)改。 如需詳細資訊，請參閱文章[概觀︰ 資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。  
  
 若要使用`CDatabase`，建構`CDatabase`物件，然後呼叫其`OpenEx`成員函式。 這會開啟連接。 當您然後建構`CRecordset`物件來連接的資料來源，操作資料錄集建構函式將指標傳遞至您`CDatabase`物件。 當您完成使用連接時，呼叫**關閉**成員函式，並摧毀`CDatabase`物件。 **關閉**關閉先前未關閉任何資料錄集。  
  
 如需詳細資訊`CDatabase`，請參閱文章[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)和[概觀︰ 資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CDatabase`  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxdb.h  
  
##  <a name="begintrans"></a>CDatabase::BeginTrans  
 呼叫此成員函式，來連接的資料來源的交易。  
  
```  
BOOL BeginTrans();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果呼叫成功，而且在認可變更僅以手動方式;否則為 0。  
  
### <a name="remarks"></a>備註  
 交易是組成一或多個呼叫`AddNew`，**編輯**，**刪除**，和**更新**的成員函式`CRecordset`物件。 開始交易之前,`CDatabase`物件必須有已連結至資料來源藉由呼叫其`OpenEx`或**開啟**成員函式。 若要結束交易，呼叫[CommitTrans](#committrans)來接受資料來源的所有變更 （以及執行這些步驟），或呼叫[回復](#rollback)中止整個交易。 呼叫**BeginTrans**開啟交易中涉及任何資料錄集並做為接近實際更新作業越好。  
  
> [!CAUTION]
>  根據您的 ODBC 驅動程式，開啟資料錄集，然後再呼叫**BeginTrans**呼叫時可能會造成問題**回復**。 您應該檢查您正在使用的特定驅動程式。 例如，在使用 Microsoft ODBC Desktop Driver Pack 3.0 中包含的 Microsoft Access 驅動程式時，必須負責 Jet 資料庫引擎的需求，您不可以是任何已開啟的資料指標的資料庫上的交易。 在 MFC 資料庫類別中，開啟的資料指標表示開啟`CRecordset`物件。 如需詳細資訊，請參閱[技術提示 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md)。  
  
 **BeginTrans**也可能會鎖定資料記錄在伺服器上，根據要求的並行處理和資料來源的功能。 鎖定資料的相關資訊，請參閱文章[資料錄集︰ 鎖定資料錄 (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)。  
  
 在本文會說明使用者定義交易[交易 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
 **BeginTrans**建立的交易順序可以復原的狀態 （反向）。 若要建立的新狀態的回復，認可任何目前的交易，然後呼叫**BeginTrans**一次。  
  
> [!CAUTION]
>  呼叫**BeginTrans**一次而不需呼叫**CommitTrans**或**回復**時發生。  
  
 呼叫[CanTransact](#cantransact)成員函式來判斷您的驅動程式是否支援給定的資料庫交易。 您也應該呼叫[GetCursorCommitBehavior](#getcursorcommitbehavior)和[GetCursorRollbackBehavior](#getcursorrollbackbehavior)判斷要保留資料指標支援。  
  
 如需有關交易的詳細資訊，請參閱文章[交易 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
### <a name="example"></a>範例  
  請參閱文章[交易︰ 資料錄集 (ODBC) 中執行交易](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
##  <a name="bindparameters"></a>CDatabase::BindParameters  
 覆寫`BindParameters`當您需要繫結參數，然後再呼叫[CDatabase::ExecuteSQL](#executesql)。  
  
```  
virtual void BindParameters(HSTMT hstmt);
```  
  
### <a name="parameters"></a>參數  
 `hstmt`  
 ODBC 陳述式控制代碼，您要繫結參數。  
  
### <a name="remarks"></a>備註  
 這種方法時，您不需要將結果從預存程序設定。  
  
 在您的覆寫呼叫**SQLBindParameters**和相關的繫結參數的 ODBC 函數。 MFC 呼叫之前呼叫覆寫`ExecuteSQL`。 您不需要呼叫**SQLPrepare**;`ExecuteSQL`呼叫**SQLExecDirect**並終結**hstmt**，這只能使用一次。  
  
##  <a name="cancel"></a>CDatabase::Cancel  
 呼叫此成員函式，來要求資料來源取消非同步作業進行中的或從第二個執行緒的處理序。  
  
```  
void Cancel();
```  
  
### <a name="remarks"></a>備註  
 請注意，MFC ODBC 類別不會再使用非同步處理。若要執行的非同步作業，您必須直接呼叫 ODBC API 函式[SQLSetConnectOption](https://msdn.microsoft.com/library/ms713564.aspx)。 如需詳細資訊，請參閱[非同步執行](https://msdn.microsoft.com/library/ms713563.aspx)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="cantransact"></a>CDatabase::CanTransact  
 呼叫此成員函式，來判斷資料庫是否允許交易。  
  
```  
BOOL CanTransact() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零資料錄集使用此`CDatabase`物件允許交易，否則為 0。  
  
### <a name="remarks"></a>備註  
 交易的相關資訊，請參閱文章[交易 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="canupdate"></a>CDatabase::CanUpdate  
 呼叫此成員函式，以判斷是否`CDatabase`物件允許更新。  
  
```  
BOOL CanUpdate() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零`CDatabase`物件可讓更新; 否則為 0，表示該您傳遞**TRUE**中`bReadOnly`當您開啟`CDatabase`物件或資料來源本身是唯讀的。 資料來源是唯讀的 ODBC API 函式呼叫**SQLGetInfo**的**SQL_DATASOURCE_READ_ONLY**傳回"y"。  
  
### <a name="remarks"></a>備註  
 並非所有驅動程式支援的更新。  
  
##  <a name="cdatabase"></a>CDatabase::CDatabase  
 建構 `CDatabase` 物件。  
  
```  
CDatabase();
```  
  
### <a name="remarks"></a>備註  
 之後建構物件，您必須呼叫其`OpenEx`或**開啟**成員函式來建立指定的資料來源的連接。  
  
 您可能會發現很方便內嵌`CDatabase`文件類別中的物件。  
  
### <a name="example"></a>範例  
 此範例說明如何使用`CDatabase`中`CDocument`-衍生的類別。  
  
 [!code-cpp[NVC_MFCDatabase #&9;](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]  
  
 [!code-cpp[NVC_MFCDatabase #&10;](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]  
  
##  <a name="close"></a>CDatabase::Close  
 如果您想要從資料來源中斷連接，請呼叫此成員函式。  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>備註  
 您必須先關閉任何相關聯的資料錄集`CDatabase`物件之前呼叫此成員函式。 因為**關閉**不會終結`CDatabase`物件時，您可以藉由開啟相同的資料來源或不同的資料來源的新連接重複使用該物件。  
  
 所有暫止`AddNew`或**編輯**使用資料庫資料錄集的陳述式會取消，且會回復所有暫止的交易。 相依於任何資料錄集`CDatabase`物件會處於未定義的狀態。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase #&12;](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]  
  
##  <a name="committrans"></a>CDatabase::CommitTrans  
 呼叫此成員函式，完成交易的步驟。  
  
```  
BOOL CommitTrans();
```  
  
### <a name="return-value"></a>傳回值  
 非零，如果更新都已成功認可。否則為 0。 如果**CommitTrans**失敗，資料來源的狀態是未定義。 您必須檢查資料，以判斷它的狀態。  
  
### <a name="remarks"></a>備註  
 交易是組成一系列的呼叫`AddNew`，**編輯**，**刪除**，和**更新**的成員函式`CRecordset`物件呼叫開始[BeginTrans](#begintrans)成員函式。 **CommitTrans**認可交易。 根據預設，會更新認可立即;呼叫**BeginTrans**造成承諾的更新延遲到**CommitTrans**呼叫。  
  
 直到您呼叫**CommitTrans**結束交易，您可以呼叫[回復](#rollback)成員函式來中止交易，並將資料來源留在原來的狀態。 若要開始新交易，請呼叫**BeginTrans**一次。  
  
 如需有關交易的詳細資訊，請參閱文章[交易 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
### <a name="example"></a>範例  
  請參閱文章[交易︰ 資料錄集 (ODBC) 中執行交易](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
##  <a name="executesql"></a>CDatabase::ExecuteSQL  
 當您需要直接執行 SQL 命令時，請呼叫此成員函式。  
  
```  
void ExecuteSQL(LPCTSTR lpszSQL);
```  
  
### <a name="parameters"></a>參數  
 `lpszSQL`  
 以 null 終止的字串，包含有效的 SQL 命令執行的指標。 您可以傳遞[CString](../../atl-mfc-shared/reference/cstringt-class.md)。  
  
### <a name="remarks"></a>備註  
 建立命令以 null 終止字串。 `ExecuteSQL`不會傳回資料記錄。 如果您想要操作的記錄，請改為使用資料錄集物件。  
  
 大部分的資料來源的命令發出到資料錄集物件，選取資料、 將新記錄插入、 刪除資料錄，和編輯資料錄支援命令。 不過，並非所有 ODBC 直接支援功能的資料庫類別中，因此有時候您可能需要進行直接 SQL 呼叫與`ExecuteSQL`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase #&13;](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]  
  
##  <a name="getbookmarkpersistence"></a>CDatabase::GetBookmarkPersistence  
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
|`SQL_BP_DELETE`|之後的資料列的書籤無效**刪除**該資料列上的作業。|  
|`SQL_BP_DROP`|書籤是之後有效**關閉**作業。|  
|`SQL_BP_SCROLL`|書籤之後是有效**移動**作業。 這可輕鬆地識別記錄集上是否支援書籤，如 `CRecordset::CanBookmark` 所傳回的那樣。|  
|`SQL_BP_TRANSACTION`|書籤在認可或回復異動之後有效。|  
|`SQL_BP_UPDATE`|之後的資料列的書籤無效**更新**該資料列上的作業。|  
|`SQL_BP_OTHER_HSTMT`|與一個記錄集物件相關聯的書籤在第二個記錄集上有效。|  
  
 如需此傳回值的詳細資訊，請參閱 ODBC API 函式**SQLGetInfo**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需書籤的詳細資訊，請參閱文章[資料錄集︰ 書籤和絕對位置 (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)。  
  
##  <a name="getconnect"></a>Getconnect  
 呼叫此成員函式擷取的呼叫期間所用的連接字串`OpenEx`或`Open`連線`CDatabase`到資料來源物件。  
  
```  
const CString GetConnect() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A `const` [CString](../../atl-mfc-shared/reference/cstringt-class.md)包含連接字串，如果`OpenEx`或`Open`已被呼叫，否則為空字串。  
  
### <a name="remarks"></a>備註  
 請參閱[CDatabase::Open](#open)如需如何建立連接字串的說明。  
  
##  <a name="getcursorcommitbehavior"></a>CDatabase::GetCursorCommitBehavior  
 呼叫此成員函式，以判斷如何[CommitTrans](#committrans)作業會影響資料指標開啟資料錄集物件上的。  
  
```  
int GetCursorCommitBehavior() const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，表示開啟資料錄集物件上的交易的效果。 如需詳細資料，請參閱＜備註＞。  
  
### <a name="remarks"></a>備註  
 下表列出可能的傳回值為`GetCursorCommitBehavior`而開啟的記錄集上對應的效果。  
  
|傳回值|CRecordset 物件上的效果|  
|------------------|----------------------------------|  
|`SQL_CB_CLOSE`|呼叫`CRecordset::Requery`緊接的交易認可。|  
|`SQL_CB_DELETE`|呼叫`CRecordset::Close`緊接的交易認可。|  
|`SQL_CB_PRESERVE`|繼續正常進行`CRecordset`作業。|  
  
 如需此傳回值的詳細資訊，請參閱 ODBC API 函式**SQLGetInfo**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需有關交易的詳細資訊，請參閱文章[交易 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="getcursorrollbackbehavior"></a>CDatabase::GetCursorRollbackBehavior  
 呼叫此成員函式，以判斷如何[回復](#rollback)作業會影響資料指標開啟資料錄集物件上的。  
  
```  
int GetCursorRollbackBehavior() const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，表示開啟資料錄集物件上的交易的效果。 如需詳細資料，請參閱＜備註＞。  
  
### <a name="remarks"></a>備註  
 下表列出可能的傳回值為`GetCursorRollbackBehavior`而開啟的記錄集上對應的效果。  
  
|傳回值|CRecordset 物件上的效果|  
|------------------|----------------------------------|  
|`SQL_CB_CLOSE`|呼叫`CRecordset::Requery`緊接交易回復。|  
|`SQL_CB_DELETE`|呼叫`CRecordset::Close`緊接交易回復。|  
|`SQL_CB_PRESERVE`|繼續正常進行`CRecordset`作業。|  
  
 如需此傳回值的詳細資訊，請參閱 ODBC API 函式**SQLGetInfo**中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需有關交易的詳細資訊，請參閱文章[交易 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
##  <a name="getdatabasename"></a>CDatabase::GetDatabaseName  
 呼叫此成員函式 （前提是資料來源會定義具名的物件稱為 「 資料庫 」），擷取目前連接之資料庫的名稱。  
  
```  
CString GetDatabaseName() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md)如果成功，否則為包含資料庫名稱、 空白`CString`。  
  
### <a name="remarks"></a>備註  
 這不是資料來源名稱 (DSN) 中指定相同`OpenEx`或**開啟**呼叫。 什麼`GetDatabaseName`傳回取決於 ODBC。 一般而言，資料庫是資料表的集合。 如果此實體有名稱，`GetDatabaseName`將它傳回。  
  
 您可能，比方說，要在標題中顯示此名稱。 如果發生錯誤時從 ODBC 擷取名稱`GetDatabaseName`會傳回空白**Cstring**。  
  
##  <a name="isopen"></a>CDatabase::IsOpen  
 呼叫此成員函式，以判斷是否`CDatabase`物件目前連接至資料來源。  
  
```  
BOOL IsOpen() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果為非零`CDatabase`目前連接物件; 否則為 0。  
  
##  <a name="m_hdbc"></a>CDatabase::m_hdbc  
 -包含公用的 ODBC 資料來源連接控制代碼 」 的 「 連接控制代碼 」。  
  
### <a name="remarks"></a>備註  
 一般來說，就不需要直接存取此成員變數。 相反地，架構會配置控制代碼呼叫時`OpenEx`或**開啟**。 當您呼叫 framework 解除配置控制代碼**刪除**運算子`CDatabase`物件。 請注意，**關閉**成員函式不解除配置控制代碼。  
  
 不過，在某些情況下，您可能需要直接使用的控制代碼。 例如，如果您需要呼叫 ODBC API 函式直接而不是透過類別`CDatabase`，您可能需要連接控制代碼將做為參數傳遞。 請參閱下列程式碼範例。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase #&15;](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]  
  
##  <a name="onsetoptions"></a>CDatabase::OnSetOptions  
 直接執行的 SQL 陳述式時，架構會呼叫此成員函式`ExecuteSQL`成員函式。  
  
```  
virtual void OnSetOptions(HSTMT hstmt);
```  
  
### <a name="parameters"></a>參數  
 `hstmt`  
 ODBC 陳述式控制代碼，設定選項。  
  
### <a name="remarks"></a>備註  
 `CRecordset::OnSetOptions`也會呼叫此成員函式。  
  
 `OnSetOptions`設定登入逾時值。 如果已有先前呼叫`SetQueryTimeout`成員函式，`OnSetOptions`會反映目前的值; 否則它會設定預設值。  
  
> [!NOTE]
>  在 MFC 4.2 之前`OnSetOptions`任一 snychronous 或非同步，也設定處理模式。 從 MFC 4.2 開始，所有作業都都會同步。 若要執行的非同步作業，您必須進行直接呼叫 ODBC API 函式**SQLSetPos**。  
  
 您不需要覆寫`OnSetOptions`變更逾時值。 相反地，若要自訂的查詢逾時值，請呼叫`SetQueryTimeout`之前建立資料錄集。`OnSetOptions`會使用新的值。 設定的值適用於所有資料錄集或直接 SQL 呼叫上的後續作業。  
  
 覆寫`OnSetOptions`如果您想要設定其他選項。 覆寫應該呼叫基底類別`OnSetOptions`之前或之後呼叫 ODBC API 函式**SQLSetStmtOption**。 請依照下列架構的預設實作中所述的方法`OnSetOptions`。  
  
##  <a name="open"></a>CDatabase::Open  
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
 指定資料來源名稱: 「 使用 ODBC 登錄透過 ODBC 管理員程式的名稱。 如果在指定資料來源名稱值`lpszConnect`(格式 」 DSN =\<資料來源 > 」)，它不得指定再次在`lpszDSN`。 在此情況下，`lpszDSN`應該**NULL**。 否則，您可以傳遞**NULL**如果您想要顯示給使用者，使用者可在其中選取資料來源的資料來源 對話方塊。 如需詳細資訊，請參閱 < 備註 >。  
  
 `bExclusive`  
 不支援這個版本的類別庫。 目前，判斷提示失敗如果這個參數是**TRUE**。 永遠開啟資料來源，以共用的 （不是唯一的）。  
  
 `bReadOnly`  
 **TRUE**如果您想要成為唯讀，並禁止更新資料來源的連接。 所有相依的資料錄集繼承這個屬性。 預設值是**FALSE**。  
  
 `lpszConnect`  
 指定的連接字串。 連接字串串連資訊，可能會包含資料來源名稱、 有效的使用者識別碼的資料來源、 使用者驗證字串 （密碼，如果資料來源需要一個），以及其他資訊。 將整個連接字串必須加上字串"ODBC"。（大寫或小寫）。 「 ODBC 」; 字串會用來指出連接至 ODBC 資料來源。這是向上相容性的類別庫的未來版本可能會支援非 ODBC 資料來源時。  
  
 `bUseCursorLib`  
 **TRUE**如果您想要載入的 ODBC 資料指標程式庫 DLL。 資料指標程式庫會遮罩某些功能的基礎的 ODBC 驅動程式，有效防止動態集的使用 （如果驅動程式支援它們）。 只支援如果資料指標程式庫已載入的資料指標是靜態的快照集和順向資料指標。 預設值是**TRUE**。 如果您打算建立資料錄集物件，直接從`CRecordset`而不需從它衍生，您應該載入資料指標程式庫。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功建立連線。否則為 0，如果使用者選擇取消時顯示對話方塊，詢問連線的詳細資訊。 在其他情況下，架構會擲回例外狀況。  
  
### <a name="remarks"></a>備註  
 您可以使用它來建構資料錄集物件之前，必須先初始化您的資料庫物件。  
  
> [!NOTE]
>  呼叫[OpenEx](#openex)成員函式是連接到資料來源，並初始化您的資料庫物件的慣用的方法。  
  
 如果在參數您**開啟**呼叫未包含足夠的資訊來進行連接，ODBC 驅動程式會開啟對話方塊，以向使用者取得必要的資訊。 當您呼叫**開啟**，連接字串， `lpszConnect`，儲存在非公開`CDatabase`物件，並可透過呼叫[GetConnect](#getconnect)成員函式。  
  
 如果您希望，您就可以開啟您自己的對話方塊中，才能呼叫**開啟**取得資訊的使用者，例如密碼，然後將該資訊 」 到連接字串傳遞給**開啟**。 或者您可能想要的連接字串，如此您就可以重複使用它的下一步，您將節省的時間應用程式會呼叫**開啟**上`CDatabase`物件。  
  
 您也可以使用的連接字串的多個層級的登入授權 (各適用於不同`CDatabase`物件) 或傳遞其他資料來源特定的資訊。 如需連接字串的詳細資訊，請參閱第 5 章中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 就可以連線嘗試逾時的時候，比方說，DBMS 主機無法使用時。 如果連線嘗試失敗，**開啟**會擲回`CDBException`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase #&14;](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]  
  
##  <a name="openex"></a>CDatabase::OpenEx  
 呼叫此成員函式，來初始化新建構`CDatabase`物件。  
  
```  
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,  
    DWORD dwOptions = 0);
```  
  
### <a name="parameters"></a>參數  
 `lpszConnectString`  
 指定 ODBC 連接字串。 這包括資料來源名稱，以及其他選擇性資訊，例如使用者 ID 和密碼。 例如，「 DSN = SQLServer_Source;UID = SA;PWD = abc123"是可能的連接字串。 請注意，如果您傳遞**NULL**的`lpszConnectString`，資料來源 對話方塊會提示使用者選取的資料來源。  
  
 `dwOptions`  
 位元遮罩，指定下列值的組合。 預設值為 0，表示資料庫將會開啟做為共用的寫入權限，ODBC 資料指標程式庫 DLL 將不會載入，以及 ODBC 連接對話方塊在沒有足夠的資訊來進行連接時，才會顯示。  
  
- **CDatabase::openExclusive**不支援這個版本的類別庫。 永遠開啟資料來源，以共用的 （不是唯一的）。 目前，如果您指定這個選項，就會失敗判斷提示。  
  
- **CDatabase::openReadOnly**開啟為唯讀的資料來源。  
  
- **CDatabase::useCursorLib**載入 ODBC 資料指標程式庫 DLL。 資料指標程式庫會遮罩某些功能的基礎的 ODBC 驅動程式，有效防止動態集的使用 （如果驅動程式支援它們）。 只支援如果資料指標程式庫已載入的資料指標是靜態的快照集和順向資料指標。 如果您打算建立資料錄集物件，直接從`CRecordset`而不需從它衍生，您應該載入資料指標程式庫。  
  
- **CDatabase::noOdbcDialog**不會顯示 ODBC 連接 對話方塊中，不論是否提供足夠的連接資訊。  
  
- **CDatabase::forceOdbcDialog**永遠顯示 ODBC 連接對話方塊。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已成功建立連線。否則為 0，如果使用者選擇取消時顯示對話方塊，詢問連線的詳細資訊。 在其他情況下，架構會擲回例外狀況。  
  
### <a name="remarks"></a>備註  
 您可以使用它來建構資料錄集物件之前，必須先初始化您的資料庫物件。  
  
 如果`lpszConnectString`參數在您`OpenEx`呼叫未包含足夠的資訊來進行連接，ODBC 驅動程式會開啟對話方塊，從使用者取得必要的資訊，提供您還沒有設定**CDatabase::noOdbcDialog**或**CDatabase::forceOdbcDialog**中`dwOptions`參數。 當您呼叫`OpenEx`，連接字串， `lpszConnectString`，儲存在非公開`CDatabase`物件，並可透過呼叫[GetConnect](#getconnect)成員函式。  
  
 如果您希望，您就可以開啟您自己的對話方塊中，才能呼叫`OpenEx`來自使用者的密碼，例如取得資訊，然後將該資訊新增至連接字串傳遞給`OpenEx`。 或者您可能想要的連接字串，如此您就可以重複使用它的下一步，您將節省的時間應用程式會呼叫`OpenEx`上`CDatabase`物件。  
  
 您也可以使用的連接字串的多個層級的登入授權 (各適用於不同`CDatabase`物件) 或傳遞其他資料來源特定的資訊。 如需連接字串的詳細資訊，請參閱在第 6 章*ODBC 程式設計人員參考*。  
  
 就可以連線嘗試逾時的時候，比方說，DBMS 主機無法使用時。 如果連線嘗試失敗，`OpenEx`會擲回`CDBException`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCDatabase #&11;](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]  
  
##  <a name="rollback"></a>CDatabase::Rollback  
 呼叫此成員函式，若要反轉交易期間所做的變更。  
  
```  
BOOL Rollback();
```  
  
### <a name="return-value"></a>傳回值  
 已成功取消交易; 如果為非零否則為 0。 如果**回復**呼叫失敗，資料來源和交易的狀態是未定義。 如果**回復**傳回 0，您必須檢查資料來源，以判斷其狀態。  
  
### <a name="remarks"></a>備註  
 所有`CRecordset``AddNew`，**編輯**，**刪除**，和**更新**自上次執行的呼叫[BeginTrans](#begintrans)回復到該呼叫當時的狀態。  
  
 在呼叫之後**回復**、 交易結束後，您必須呼叫**BeginTrans**再次用於另一個交易。 目前您在呼叫之前的記錄**BeginTrans**會變成目前的記錄一次之後**回復**。  
  
 回復之後，復原之前為目前的記錄保持最新。 資料錄集和資料來源，在復原之後的狀態相關的詳細資訊，請參閱文章[交易 (ODBC)](../../data/odbc/transaction-odbc.md)。  
  
### <a name="example"></a>範例  
  請參閱文章[交易︰ 資料錄集 (ODBC) 中執行交易](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)。  
  
##  <a name="setlogintimeout"></a>CDatabase::SetLoginTimeout  
 呼叫此成員函式 â €"之前先呼叫`OpenEx`或**開啟**â €"來源連接逾時覆寫預設嘗試進行的資料之前所允許的秒數。  
  
```  
void SetLoginTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>參數  
 `dwSeconds`  
 逾時的連線嘗試前允許的秒數。  
  
### <a name="remarks"></a>備註  
 連接嘗試可能逾時如果，比方說，DBMS 無法使用。 呼叫**SetLoginTimeout**您建構初始化之後`CDatabase`物件，但您的呼叫之前`OpenEx`或**開啟**。  
  
 登入逾時的預設值為 15 秒。 並非所有的資料來源支援讓您指定的登入逾時值。 如果資料來源不支援逾時，您可以取得追蹤輸出，但不是例外狀況。 值為 0 表示 「 無限 」。  
  
##  <a name="setquerytimeout"></a>CDatabase::SetQueryTimeout  
 呼叫此成員函式，來覆寫預設連接的資料來源逾時的後續操作前允許的秒數。  
  
```  
void SetQueryTimeout(DWORD dwSeconds);
```  
  
### <a name="parameters"></a>參數  
 `dwSeconds`  
 逾時可讓查詢嘗試之前的秒數。  
  
### <a name="remarks"></a>備註  
 由於網路存取問題、 過多的查詢處理時間等作業可能會逾時。 呼叫`SetQueryTimeout`開啟資料錄集之前或在呼叫資料錄集的前`AddNew`，**更新**或**刪除**成員函式，如果您想要變更查詢逾時值。 此設定會影響所有後續**開啟**， `AddNew`，**更新**，和**刪除**呼叫任何與此相關聯的資料錄集`CDatabase`物件。 在開啟之後變更資料錄集的查詢逾時值不會變更資料錄集的值。 例如，後續**移動**作業不會使用新的值。  
  
 查詢逾時的預設值為 15 秒。 並非所有的資料來源支援可設定查詢逾時值的功能。 如果您設定查詢逾時值為 0，就會發生不會逾時;與資料來源之間的通訊可能會停止回應。 在開發期間，這種行為可能很有用的。 如果資料來源不支援逾時，您可以取得追蹤輸出，但不是例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 [CObject 類別](../../mfc/reference/cobject-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CRecordset 類別](../../mfc/reference/crecordset-class.md)

