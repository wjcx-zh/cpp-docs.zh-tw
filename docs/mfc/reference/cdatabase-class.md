---
title: CDatabase 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: ee1503f49f0e60b24e0ef3a9c9631f039ad9355e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223105"
---
# <a name="cdatabase-class"></a>CDatabase 類別

表示資料來源的連接，您可以透過這個連接來操作資料來源。

## <a name="syntax"></a>語法

```
class CDatabase : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|Name|說明|
|----------|-----------------|
|[CDatabase：： CDatabase](#cdatabase)|建構 `CDatabase` 物件。 您必須呼叫或來初始化物件 `OpenEx` `Open` 。|

### <a name="public-methods"></a>公用方法

|Name|說明|
|----------|-----------------|
|[CDatabase：： BeginTrans](#begintrans)|`AddNew` `Edit` `Delete` `Update` `CRecordset` 在連接的資料來源上啟動「交易」，這是對類別的、、和成員函式的一系列可回復的呼叫。 資料來源必須支援交易， `BeginTrans` 才會有任何效果。|
|[CDatabase：： BindParameters](#bindparameters)|可讓您在呼叫之前系結參數 `CDatabase::ExecuteSQL` 。|
|[CDatabase：： Cancel](#cancel)|從第二個執行緒取消非同步作業或進程。|
|[CDatabase：： CanTransact](#cantransact)|如果資料來源支援交易，則傳回非零。|
|[CDatabase：： CanUpdate](#canupdate)|如果 `CDatabase` 物件可更新（非唯讀），則傳回非零。|
|[CDatabase：： Close](#close)|關閉資料來源連接。|
|[CDatabase：： CommitTrans](#committrans)|完成由開始的交易 `BeginTrans` 。 會執行改變數據源之交易中的命令。|
|[CDatabase：： ExecuteSQL](#executesql)|執行 SQL 語句。 不會傳回任何資料記錄。|
|[CDatabase：： GetBookmarkPersistence](#getbookmarkpersistence)|識別書簽在記錄集物件上保存的作業。|
|[CDatabase::GetConnect](#getconnect)|傳回用來將 `CDatabase` 物件連接至資料來源的 ODBC 連接字串。|
|[CDatabase：： GetCursorCommitBehavior](#getcursorcommitbehavior)|識別在開啟的記錄集物件上認可交易的效果。|
|[CDatabase：： GetCursorRollbackBehavior](#getcursorrollbackbehavior)|識別在開啟的記錄集物件上回複交易的效果。|
|[CDatabase：： GetDatabaseName](#getdatabasename)|傳回目前使用中的資料庫名稱。|
|[CDatabase：： IsOpen](#isopen)|如果 `CDatabase` 物件目前連接至資料來源，則傳回非零。|
|[CDatabase：： OnSetOptions](#onsetoptions)|由架構呼叫以設定標準連接選項。 預設的執行會設定查詢超時值。 您可以藉由呼叫，在一段時間前建立這些選項 `SetQueryTimeout` 。|
|[CDatabase：： Open](#open)|建立與資料來源的連接（透過 ODBC 驅動程式）。|
|[CDatabase：： Microsoft.office.interop.visio.documents.open](#openex)|建立與資料來源的連接（透過 ODBC 驅動程式）。|
|[CDatabase：： Rollback](#rollback)|反轉在目前交易期間所做的變更。 資料來源會回到其先前的狀態（如呼叫中所定義） `BeginTrans` ，不改變。|
|[CDatabase：： SetLoginTimeout](#setlogintimeout)|設定資料來源連接嘗試會超時的秒數。|
|[CDatabase：： SetQueryTimeout](#setquerytimeout)|設定資料庫查詢作業將會超時的秒數。會影響所有後續的記錄集 `Open` 、、 `AddNew` `Edit` 和 `Delete` 呼叫。|

### <a name="public-data-members"></a>公用資料成員

|Name|說明|
|----------|-----------------|
|[CDatabase：： m_hdbc](#m_hdbc)|資料來源的開放式資料庫連接（ODBC）連接控制碼。 輸入*HDBC*。|

## <a name="remarks"></a>備註

資料來源是某些資料庫管理系統（DBMS）主控的特定資料實例。 範例包括 Microsoft SQL Server、Microsoft Access、Borland dBASE 和 xBASE。 您 `CDatabase` 的應用程式中一次可以有一個或多個物件處於作用中狀態。

> [!NOTE]
> 如果您使用的是資料存取物件（DAO）類別，而不是開放式資料庫連接（ODBC）類別，請改用 [類別[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) ]。 如需詳細資訊，請參閱文章[總覽：資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。

若要使用 `CDatabase` ，請建立 `CDatabase` 物件並呼叫其成員函式 `OpenEx` 。 這會開啟連接。 當您接著 `CRecordset` 針對連接的資料來源進行作業時，請將物件的指標傳遞給記錄集的函式 `CDatabase` 。 當您使用連接完成時，請呼叫 `Close` 成員函式並終結 `CDatabase` 物件。 `Close`關閉先前尚未關閉的任何記錄集。

如需的詳細資訊 `CDatabase` ，請參閱[資料來源（ODBC）](../../data/odbc/data-source-odbc.md)和[總覽：資料庫程式設計](../../data/data-access-programming-mfc-atl.md)中的文章。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>需求

**標頭：** afxdb。h

## <a name="cdatabasebegintrans"></a><a name="begintrans"></a>CDatabase：： BeginTrans

呼叫這個成員函式，以使用已連接的資料來源來開始交易。

```
BOOL BeginTrans();
```

### <a name="return-value"></a>傳回值

如果呼叫成功，且只以手動方式認可變更，則為非零。否則為0。

### <a name="remarks"></a>備註

交易是由一或多個呼叫物件的 `AddNew` 、 `Edit` 、 `Delete` 和 `Update` 成員函式所組成 `CRecordset` 。 開始交易之前， `CDatabase` 物件必須已經藉由呼叫其或成員函式來連接到資料 `OpenEx` 源 `Open` 。 若要結束交易，請呼叫[CommitTrans](#committrans)以接受對資料來源所做的所有變更（並加以執行），或呼叫[Rollback](#rollback)以中止整個交易。 在 `BeginTrans` 您開啟與交易相關的任何記錄集，並盡可能接近實際的更新作業時呼叫。

> [!CAUTION]
> 根據您的 ODBC 驅動程式，在呼叫之前開啟記錄集， `BeginTrans` 可能會在呼叫時造成問題 `Rollback` 。 您應該檢查您所使用的特定驅動程式。 例如，使用 Microsoft ODBC 桌面驅動程式套件3.0 中包含的 Microsoft Access 驅動程式時，您必須考慮 Jet 資料庫引擎的需求，而不應在任何具有開啟資料指標的資料庫上開始交易。 在 MFC 資料庫類別中，開放式資料指標表示開啟的 `CRecordset` 物件。 如需詳細資訊，請參閱[技術提示 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md)。

`BeginTrans`可能也會鎖定伺服器上的資料記錄，視要求的並行和資料來源的功能而定。 如需有關鎖定資料的詳細資訊，請參閱[記錄集：鎖定記錄（ODBC）](../../data/odbc/recordset-locking-records-odbc.md)一文。

[交易（ODBC）](../../data/odbc/transaction-odbc.md)一文中會說明使用者定義的交易。

`BeginTrans`建立可回復交易順序的狀態（反轉）。 若要建立復原的新狀態，請認可任何目前的交易，然後 `BeginTrans` 再次呼叫。

> [!CAUTION]
> `BeginTrans`在沒有呼叫或的情況下再次呼叫 `CommitTrans` `Rollback` ，即為錯誤。

呼叫[CanTransact](#cantransact)成員函式，以判斷您的驅動程式是否支援給定資料庫的交易。 您也應該呼叫[GetCursorCommitBehavior](#getcursorcommitbehavior)和[GetCursorRollbackBehavior](#getcursorrollbackbehavior)來判斷資料指標保留的支援。

如需交易的詳細資訊，請參閱[交易（ODBC）](../../data/odbc/transaction-odbc.md)一文。

### <a name="example"></a>範例

  請參閱[交易：在記錄集中執行交易（ODBC）](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)一文。

## <a name="cdatabasebindparameters"></a><a name="bindparameters"></a>CDatabase：： BindParameters

`BindParameters`當您需要在呼叫[CDatabase：： ExecuteSQL](#executesql)之前先系結參數時，請覆寫。

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>參數

*hstmt*<br/>
您要系結參數的 ODBC 語句控制碼。

### <a name="remarks"></a>備註

當您不需要預存程式的結果集時，這個方法很有用。

在您的覆寫中，呼叫 `SQLBindParameters` 和相關的 ODBC 函式來系結參數。 在呼叫之前，MFC 會呼叫您的覆寫 `ExecuteSQL` 。 您不需要呼叫 `SQLPrepare` ; `ExecuteSQL` `SQLExecDirect` 會呼叫並終結*hstmt*，這只會使用一次。

## <a name="cdatabasecancel"></a><a name="cancel"></a>CDatabase：： Cancel

呼叫這個成員函式，要求資料來源取消進行中的非同步作業，或來自第二個執行緒的進程。

```cpp
void Cancel();
```

### <a name="remarks"></a>備註

請注意，MFC ODBC 類別不再使用非同步處理;若要執行非同步作業，您必須直接呼叫 ODBC API 函式[SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function)。 如需詳細資訊，請參閱[非同步執行](/sql/odbc/reference/develop-app/asynchronous-execution)。

## <a name="cdatabasecantransact"></a><a name="cantransact"></a>CDatabase：： CanTransact

呼叫這個成員函式，以判斷資料庫是否允許交易。

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>傳回值

如果使用這個物件的記錄集允許交易，則為非零， `CDatabase` 否則為0。

### <a name="remarks"></a>備註

如需交易的詳細資訊，請參閱[交易（ODBC）](../../data/odbc/transaction-odbc.md)一文。

## <a name="cdatabasecanupdate"></a><a name="canupdate"></a>CDatabase：： CanUpdate

呼叫這個成員函式，以判斷 `CDatabase` 物件是否允許更新。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>傳回值

如果 `CDatabase` 物件允許更新則為非零，否則為0，表示當您開啟*bReadOnly* `CDatabase` 物件或資料來源本身為唯讀時，在 bReadOnly 中傳遞 TRUE。 如果 SQL_DATASOURCE_READ_ONLY 的 ODBC API 函式的呼叫傳回 "y"，則資料來源為唯讀 `SQLGetInfo` 。

### <a name="remarks"></a>備註

並非所有的驅動程式都支援更新。

## <a name="cdatabasecdatabase"></a><a name="cdatabase"></a>CDatabase：： CDatabase

建構 `CDatabase` 物件。

```
CDatabase();
```

### <a name="remarks"></a>備註

在建立物件之後，您必須呼叫其 `OpenEx` 或成員函式， `Open` 以建立與指定之資料來源的連接。

您可能會發現，將物件內嵌 `CDatabase` 在檔類別中是很方便的方式。

### <a name="example"></a>範例

這個範例說明如何 `CDatabase` 在 `CDocument` 衍生類別中使用。

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

## <a name="cdatabaseclose"></a><a name="close"></a>CDatabase：： Close

如果您想要從資料來源中斷連接，請呼叫這個成員函式。

```
virtual void Close();
```

### <a name="remarks"></a>備註

您必須先關閉與物件相關聯的任何記錄集， `CDatabase` 再呼叫這個成員函式。 因為不 `Close` 會損毀 `CDatabase` 物件，所以您可以開啟與相同資料來源或不同資料來源的新連接，以重複使用物件。

所有使用資料庫的暫止 `AddNew` 或 `Edit` 記錄集語句都會取消，而且所有暫止的交易都會回復。 相依于物件的任何記錄集 `CDatabase` 都會保留未定義的狀態。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

## <a name="cdatabasecommittrans"></a><a name="committrans"></a>CDatabase：： CommitTrans

在完成交易時呼叫這個成員函式。

```
BOOL CommitTrans();
```

### <a name="return-value"></a>傳回值

如果已成功認可更新，則為非零。否則為0。 如果 `CommitTrans` 失敗，則資料來源的狀態為未定義。 您必須檢查資料以判斷其狀態。

### <a name="remarks"></a>備註

交易是由呼叫 BeginTrans 成員函式開始之 `AddNew` 物件的、 `Edit` 、 `Delete` 和 `Update` 成員函 `CRecordset` [BeginTrans](#begintrans)式所組成。 `CommitTrans`認可交易。 預設會立即認可更新;呼叫 `BeginTrans` 會使更新的認可延遲到 `CommitTrans` 呼叫為止。

在您呼叫 `CommitTrans` 來結束交易之前，您可以呼叫[Rollback](#rollback)成員函式來中止交易，並將資料來源保留在其原始狀態。 若要開始新的交易，請 `BeginTrans` 再次呼叫。

如需交易的詳細資訊，請參閱[交易（ODBC）](../../data/odbc/transaction-odbc.md)一文。

### <a name="example"></a>範例

  請參閱[交易：在記錄集中執行交易（ODBC）](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)一文。

## <a name="cdatabaseexecutesql"></a><a name="executesql"></a>CDatabase：： ExecuteSQL

當您需要直接執行 SQL 命令時，請呼叫這個成員函式。

```cpp
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>參數

*lpszSQL*<br/>
以 null 終止的字串指標，其中包含要執行的有效 SQL 命令。 您可以傳遞[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>備註

建立命令做為以 null 結束的字串。 `ExecuteSQL`不會傳回資料記錄。 如果您想要操作記錄，請改用記錄集物件。

您的資料來源的大部分命令都是透過記錄集物件來發行，而這些物件支援用於選取資料、插入新記錄、刪除記錄和編輯記錄的命令。 不過，並非所有的 ODBC 功能都是由資料庫類別直接支援，因此您有時可能需要對進行直接的 SQL 呼叫 `ExecuteSQL` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

## <a name="cdatabasegetbookmarkpersistence"></a><a name="getbookmarkpersistence"></a>CDatabase：： GetBookmarkPersistence

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
|SQL_BP_CLOSE|書簽在作業之後有效 `Requery` 。|
|SQL_BP_DELETE|資料列的書簽在該資料列的作業之後有效 `Delete` 。|
|SQL_BP_DROP|書簽在作業之後有效 `Close` 。|
|SQL_BP_SCROLL|書簽在任何作業之後都有效 `Move` 。 這可輕鬆地識別記錄集上是否支援書籤，如 `CRecordset::CanBookmark` 所傳回的那樣。|
|SQL_BP_TRANSACTION|書籤在認可或回復異動之後有效。|
|SQL_BP_UPDATE|資料列的書簽在該資料列的作業之後有效 `Update` 。|
|SQL_BP_OTHER_HSTMT|與一個記錄集物件相關聯的書籤在第二個記錄集上有效。|

如需此傳回值的詳細資訊，請參閱 Windows SDK 中的 ODBC API 函式 `SQLGetInfo` 。 如需書簽的詳細資訊，請參閱[記錄集：書簽和絕對位置（ODBC）](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)一文。

## <a name="cdatabasegetconnect"></a><a name="getconnect"></a>CDatabase：： GetConnect

呼叫這個成員函式，以抓取在呼叫 `OpenEx` 或將 `Open` `CDatabase` 物件連接至資料來源時所使用的連接字串。

```
const CString GetConnect() const;
```

### <a name="return-value"></a>傳回值

**`const`** 包含連接字串的[CString](../../atl-mfc-shared/reference/cstringt-class.md) （如果 `OpenEx` `Open` 已呼叫或）; 否則為空字串。

### <a name="remarks"></a>備註

如需如何建立連接字串的說明，請參閱[CDatabase：： Open](#open) 。

## <a name="cdatabasegetcursorcommitbehavior"></a><a name="getcursorcommitbehavior"></a>CDatabase：： GetCursorCommitBehavior

呼叫這個成員函式，以判斷[CommitTrans](#committrans)作業如何影響開啟之記錄集物件上的資料指標。

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>傳回值

值，指出交易對開啟的記錄集物件的影響。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

下表列出的可能傳回值 `GetCursorCommitBehavior` ，以及對開啟記錄集的對應效果。

|傳回值|對 CRecordset 物件的影響|
|------------------|----------------------------------|
|SQL_CB_CLOSE|`CRecordset::Requery`在交易認可之後立即呼叫。|
|SQL_CB_DELETE|`CRecordset::Close`在交易認可之後立即呼叫。|
|SQL_CB_PRESERVE|正常執行 `CRecordset` 作業。|

如需此傳回值的詳細資訊，請參閱 Windows SDK 中的 ODBC API 函式 `SQLGetInfo` 。 如需交易的詳細資訊，請參閱[交易（ODBC）](../../data/odbc/transaction-odbc.md)一文。

## <a name="cdatabasegetcursorrollbackbehavior"></a><a name="getcursorrollbackbehavior"></a>CDatabase：： GetCursorRollbackBehavior

呼叫這個成員函式，以判斷[復原](#rollback)作業如何影響開啟之記錄集物件上的資料指標。

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>傳回值

值，指出交易對開啟的記錄集物件的影響。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

下表列出的可能傳回值 `GetCursorRollbackBehavior` ，以及對開啟記錄集的對應效果。

|傳回值|對 CRecordset 物件的影響|
|------------------|----------------------------------|
|SQL_CB_CLOSE|`CRecordset::Requery`在交易回復之後立即呼叫。|
|SQL_CB_DELETE|`CRecordset::Close`在交易回復之後立即呼叫。|
|SQL_CB_PRESERVE|正常執行 `CRecordset` 作業。|

如需此傳回值的詳細資訊，請參閱 Windows SDK 中的 ODBC API 函式 `SQLGetInfo` 。 如需交易的詳細資訊，請參閱[交易（ODBC）](../../data/odbc/transaction-odbc.md)一文。

## <a name="cdatabasegetdatabasename"></a><a name="getdatabasename"></a>CDatabase：： GetDatabaseName

呼叫這個成員函式來抓取目前連接之資料庫的名稱（前提是資料來源定義了名為 "database" 的命名物件）。

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為包含資料庫名稱的[CString](../../atl-mfc-shared/reference/cstringt-class.md) ;否則為空的 `CString` 。

### <a name="remarks"></a>備註

這與或呼叫中指定的資料來源名稱（DSN）不同 `OpenEx` `Open` 。 傳回 `GetDatabaseName` 的內容取決於 ODBC。 一般而言，資料庫是資料表的集合。 如果此實體具有名稱， `GetDatabaseName` 則會傳回它。

例如，您可能想要在標題中顯示此名稱。 如果從 ODBC 抓取名稱時發生錯誤，則會傳回 `GetDatabaseName` 空的 `CString` 。

## <a name="cdatabaseisopen"></a><a name="isopen"></a>CDatabase：： IsOpen

呼叫這個成員函式，以判斷 `CDatabase` 物件目前是否已連接至資料來源。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果 `CDatabase` 目前已連線物件，則為非零，否則為0。

## <a name="cdatabasem_hdbc"></a><a name="m_hdbc"></a>CDatabase：： m_hdbc

包含 ODBC 資料來源連接的公用控制碼-「連接控制碼」。

### <a name="remarks"></a>備註

一般來說，您不需要直接存取這個成員變數。 相反地，當您呼叫或時，架構會配置控制碼 `OpenEx` `Open` 。 當您在物件上呼叫運算子時，架構會取消配置控制碼 **`delete`** `CDatabase` 。 請注意，成員函式不 `Close` 會解除配置控制碼。

不過，在某些情況下，您可能需要直接使用控制碼。 例如，如果您需要直接呼叫 ODBC API 函式，而不是透過類別 `CDatabase` ，您可能需要以參數的形式傳遞連接控制碼。 請參閱下面的程式碼範例。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

## <a name="cdatabaseonsetoptions"></a><a name="onsetoptions"></a>CDatabase：： OnSetOptions

當使用成員函式直接執行 SQL 語句時，架構會呼叫這個成員函式 `ExecuteSQL` 。

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>參數

*hstmt*<br/>
要設定之選項的 ODBC 語句控制碼。

### <a name="remarks"></a>備註

`CRecordset::OnSetOptions`也會呼叫這個成員函式。

`OnSetOptions`設定登入超時值。 如果先前已呼叫和成員函式 `SetQueryTimeout` ， `OnSetOptions` 會反映目前的值，否則會設定預設值。

> [!NOTE]
> 在 MFC 4.2 之前， `OnSetOptions` 也請將處理模式設定為 snychronous 或非同步。 從 MFC 4.2 開始，所有作業都是同步的。 若要執行非同步作業，您必須直接呼叫 ODBC API 函式 `SQLSetPos` 。

您不需要覆寫 `OnSetOptions` 來變更 timeout 值。 相反地，若要自訂查詢超時值，請 `SetQueryTimeout` 在建立記錄集之前呼叫， `OnSetOptions` 將會使用新的值。 設定的值會套用至所有記錄集或直接 SQL 呼叫的後續作業。

`OnSetOptions`如果您想要設定其他選項，請覆寫。 在 `OnSetOptions` 呼叫 ODBC API 函式之前或之後，您的覆寫應該呼叫基類 `SQLSetStmtOption` 。 請遵循架構的預設執行中所述的方法 `OnSetOptions` 。

## <a name="cdatabaseopen"></a><a name="open"></a>CDatabase：： Open

呼叫這個成員函式，以初始化新建立的 `CDatabase` 物件。

```
virtual BOOL Open(
    LPCTSTR lpszDSN,
    BOOL bExclusive = FALSE,
    BOOL bReadOnly = FALSE,
    LPCTSTR lpszConnect = _T("ODBC;"),
    BOOL bUseCursorLib = TRUE);
```

### <a name="parameters"></a>參數

*lpszDSN*<br/>
指定資料來源名稱，這是透過 ODBC 系統管理員程式向 ODBC 註冊的名稱。 如果*lpszConnect*中指定了 DSN 值（格式為 "DSN = \<data-source> "），則不得在*lpszDSN*中再次指定。 在此情況下， *lpszDSN*應該是 Null。 否則，如果您想要向使用者顯示 [資料來源] 對話方塊，讓使用者可以在其中選取資料來源，則可以傳遞 Null。 如需詳細資訊，請參閱備註。

*bExclusive*<br/>
在此版本的類別庫中不支援。 目前，如果此參數為 TRUE，判斷提示就會失敗。 資料來源一律會開啟為共用（非獨佔）。

*bReadOnly*<br/>
如果您想要讓連接成為唯讀，並禁止更新資料來源，則為 TRUE。 所有相依記錄集都會繼承這個屬性。 預設值為 FALSE。

*lpszConnect*<br/>
指定連接字串。 連接字串會串連資訊，可能包括資料來源名稱、資料來源上有效的使用者識別碼、使用者驗證字串（如果資料來源需要，則為密碼），以及其他資訊。 整個連接字串的前面必須加上 "ODBC;" 字串（大寫或小寫）。 "ODBC;" 字串是用來表示連接到 ODBC 資料來源;這是為了在類別庫的未來版本可能支援非 ODBC 資料來源時，提供最高階的相容性。

*bUseCursorLib*<br/>
如果您想要載入 ODBC 資料指標程式庫 DLL，則為 TRUE。 資料指標程式庫會遮罩基礎 ODBC 驅動程式的某些功能，有效地避免使用動態集（如果驅動程式支援的話）。 如果資料指標程式庫已載入，則唯一支援的資料指標為靜態快照集和順向資料指標。 預設值為 TRUE。 如果您計畫直接從建立記錄集物件 `CRecordset` ，而不從它衍生，您就不應該載入資料指標程式庫。

### <a name="return-value"></a>傳回值

如果成功連接，則為非零值;如果使用者在顯示對話方塊時選擇 [取消]，而要求提供更多連接資訊，則為0。 在所有其他情況下，架構會擲回例外狀況。

### <a name="remarks"></a>備註

您的資料庫物件必須先初始化，您才能使用它來建立記錄集物件。

> [!NOTE]
> 呼叫[microsoft.office.interop.visio.documents.open](#openex)成員函式是連接到資料來源並初始化資料庫物件的慣用方式。

如果您呼叫中的參數 `Open` 未包含足夠的資訊來進行連接，則 ODBC 驅動程式會開啟一個對話方塊，以取得使用者所需的資訊。 當您呼叫時 `Open` ，您的連接字串*lpszConnect*會私下儲存在物件中， `CDatabase` 而且可以藉由呼叫[GetConnect](#getconnect)成員函式來取得。

如有需要，您可以在呼叫之前開啟自己的對話方塊 `Open` ，以取得使用者的資訊（例如密碼），然後將該資訊新增至您傳遞給的連接字串 `Open` 。 或者，您可能想要儲存您傳遞的連接字串，讓您可以在下次應用程式呼叫物件時重複使用它 `Open` `CDatabase` 。

您也可以將連接字串用於多個層級的登入授權（分別用於不同的 `CDatabase` 物件）或傳達其他資料來源特定資訊。 如需連接字串的詳細資訊，請參閱 Windows SDK 中的第5章。

例如，如果 DBMS 主機無法使用，連接嘗試可能會超時。 如果連接嘗試失敗，則會擲回 `Open` `CDBException` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

## <a name="cdatabaseopenex"></a><a name="openex"></a>CDatabase：： Microsoft.office.interop.visio.documents.open

呼叫這個成員函式，以初始化新建立的 `CDatabase` 物件。

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>參數

*lpszConnectString*<br/>
指定 ODBC 連接字串。 這包括資料來源名稱以及其他選擇性資訊，例如使用者識別碼和密碼。 例如，"DSN = SQLServer_Source;UID = SA;PWD = abc123 "是可能的連接字串。 請注意，如果您針對*lpszConnectString*傳遞 Null，[資料來源] 對話方塊會提示使用者選取資料來源。

*dwOptions*<br/>
位元遮罩，指定下列值的組合。 預設值為0，表示資料庫將會開啟為具有寫入權限的共用，將不會載入 ODBC 資料指標程式庫 DLL，而且只有在沒有足夠的資訊可進行連接時，才會顯示 [ODBC 連接] 對話方塊。

- `CDatabase::openExclusive`在此版本的類別庫中不支援。 資料來源一律會開啟為共用（非獨佔）。 目前，如果您指定此選項，判斷提示就會失敗。

- `CDatabase::openReadOnly`以唯讀方式開啟資料來源。

- `CDatabase::useCursorLib`載入 ODBC 資料指標程式庫 DLL。 資料指標程式庫會遮罩基礎 ODBC 驅動程式的某些功能，有效地避免使用動態集（如果驅動程式支援的話）。 如果資料指標程式庫已載入，則唯一支援的資料指標為靜態快照集和順向資料指標。 如果您計畫直接從建立記錄集物件 `CRecordset` ，而不從它衍生，您就不應該載入資料指標程式庫。

- `CDatabase::noOdbcDialog`不論是否提供足夠的連接資訊，都不要顯示 [ODBC 連接] 對話方塊。

- `CDatabase::forceOdbcDialog`一律顯示 [ODBC 連接] 對話方塊。

### <a name="return-value"></a>傳回值

如果成功連接，則為非零值;如果使用者在顯示對話方塊時選擇 [取消]，而要求提供更多連接資訊，則為0。 在所有其他情況下，架構會擲回例外狀況。

### <a name="remarks"></a>備註

您的資料庫物件必須先初始化，您才能使用它來建立記錄集物件。

如果您呼叫中的*lpszConnectString*參數 `OpenEx` 未包含足夠的資訊來進行連接，則 ODBC 驅動程式會開啟一個對話方塊，以取得使用者所需的資訊，前提是您未在 `CDatabase::noOdbcDialog` `CDatabase::forceOdbcDialog` *dwOptions*參數中設定或。 當您呼叫時 `OpenEx` ，您的連接字串*lpszConnectString*會私下儲存在物件中， `CDatabase` 而且可以藉由呼叫[GetConnect](#getconnect)成員函式來取得。

如有需要，您可以在呼叫之前開啟自己的對話方塊 `OpenEx` ，以取得使用者的資訊（例如密碼），然後將該資訊新增至您傳遞給的連接字串 `OpenEx` 。 或者，您可能想要儲存您傳遞的連接字串，讓您可以在下次應用程式呼叫物件時重複使用它 `OpenEx` `CDatabase` 。

您也可以將連接字串用於多個層級的登入授權（分別用於不同的 `CDatabase` 物件）或傳達其他資料來源特定資訊。 如需連接字串的詳細資訊，請參閱 ODBC 程式設計*人員參考*中的第6章。

例如，如果 DBMS 主機無法使用，連接嘗試可能會超時。 如果連接嘗試失敗，則會擲回 `OpenEx` `CDBException` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

## <a name="cdatabaserollback"></a><a name="rollback"></a>CDatabase：： Rollback

呼叫這個成員函式可反轉交易期間所做的變更。

```
BOOL Rollback();
```

### <a name="return-value"></a>傳回值

如果成功反轉交易，則為非零;否則為0。 如果 `Rollback` 呼叫失敗，資料來源和交易狀態會是未定義的。 如果傳回 `Rollback` 0，您必須檢查資料來源以判斷其狀態。

### <a name="remarks"></a>備註

`CRecordset` `AddNew` `Edit` `Delete` 自上一次 BeginTrans 之後所執行的所有、、和 `Update` 呼叫都會回復至該呼叫時存在的狀態。 [BeginTrans](#begintrans)

呼叫之後， `Rollback` 交易就會結束，而且您必須 `BeginTrans` 針對另一個交易再次呼叫。 在您呼叫之前的最新記錄， `BeginTrans` 會在之後再次成為目前的記錄 `Rollback` 。

復原之後，在復原之前的最新記錄仍然是最新的。 如需有關復原後的記錄集狀態和資料來源的詳細資訊，請參閱[交易（ODBC）](../../data/odbc/transaction-odbc.md)一文。

### <a name="example"></a>範例

  請參閱[交易：在記錄集中執行交易（ODBC）](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)一文。

## <a name="cdatabasesetlogintimeout"></a><a name="setlogintimeout"></a>CDatabase：： SetLoginTimeout

在您呼叫或之前，請先呼叫這個成員函 `OpenEx` `Open` 式，以覆寫嘗試的資料來源連接逾時之前允許的預設秒數。

```cpp
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>參數

*dwSeconds*<br/>
連接嘗試超時之前允許的秒數。

### <a name="remarks"></a>備註

例如，如果 DBMS 無法使用，連接嘗試可能會超時。 在 `SetLoginTimeout` 您建立未初始化的 `CDatabase` 物件之後，但是在呼叫或之前呼叫 `OpenEx` `Open` 。

登入超時的預設值為15秒。 並非所有的資料來源都支援指定登入超時值的能力。 如果資料來源不支援 timeout，您會收到追蹤輸出，但不會取得例外狀況。 值為0表示「無限」。

## <a name="cdatabasesetquerytimeout"></a><a name="setquerytimeout"></a>CDatabase：： SetQueryTimeout

呼叫這個成員函式，以覆寫連接資料來源的後續作業超時前允許的預設秒數。

```cpp
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>參數

*dwSeconds*<br/>
查詢嘗試超時之前允許的秒數。

### <a name="remarks"></a>備註

作業可能會因為網路存取問題、過多的查詢處理時間等等而超時。 `SetQueryTimeout`在開啟記錄集之前，或在通話記錄集的之前呼叫 `AddNew` ， `Update` 或 `Delete` 如果您想要變更查詢超時值，則為成員函式。 設定會影響所有後續的 `Open` 、 `AddNew` 、 `Update` 和 `Delete` 呼叫與此物件相關聯的任何記錄集 `CDatabase` 。 在開啟後變更記錄集的查詢超時值，並不會變更記錄集的值。 例如，後續 `Move` 的作業不會使用新的值。

查詢超時的預設值為15秒。 並非所有的資料來源都支援設定查詢超時值的能力。 如果您將查詢超時值設定為0，就不會發生任何超時;與資料來源的通訊可能會停止回應。 這種行為在開發期間可能會很有用。 如果資料來源不支援 timeout，您會收到追蹤輸出，但不會取得例外狀況。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
