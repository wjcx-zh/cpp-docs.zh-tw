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
ms.openlocfilehash: 260a4a38fcee8994d804267709c11279266d393c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376484"
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
|[C 資料庫:C 資料庫](#cdatabase)|建構 `CDatabase` 物件。 必須通過調用`OpenEx``Open`或 初始化物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 資料庫::開始轉換](#begintrans)|在連接的資料來源上啟動一個「事務」-`AddNew`對`Edit`類`Delete`的`Update`、成員函數`CRecordset`的一系列可逆調用。 數據源必須支援事務才能`BeginTrans`產生任何效果。|
|[C 資料庫::結合參數](#bindparameters)|允許您在調用`CDatabase::ExecuteSQL`之前綁定參數。|
|[C 資料庫::取消](#cancel)|從第二個線程取消非同步操作或進程。|
|[C 資料庫::可以](#cantransact)|如果數據源支援事務,則返回非零。|
|[C 資料庫::可以更新](#canupdate)|如果`CDatabase`對像是可向上的(不只讀的),則返回非零。|
|[C 資料庫:關閉](#close)|關閉數據源連接。|
|[C 資料庫::提交轉換](#committrans)|完成`BeginTrans`由啟動的事務。 事務中更改數據源的命令將執行。|
|[C 資料庫::執行SQL](#executesql)|執行 SQL 語句。 不返回任何數據記錄。|
|[C 資料庫::獲取書籤持久性](#getbookmarkpersistence)|標識書籤在記錄集物件上保留的操作。|
|[CDatabase::GetConnect](#getconnect)|傳回用於將物件連接到資料來源`CDatabase`的 ODBC 連接字串。|
|[C 資料庫::取得游標提交行為](#getcursorcommitbehavior)|標識在打開的記錄集物件上提交事務的效果。|
|[C 資料庫::取得游標回滾行為](#getcursorrollbackbehavior)|標識回滾事務對打開的記錄集對象的影響。|
|[C 資料庫::取得資料庫名稱](#getdatabasename)|返回目前正在使用的資料庫的名稱。|
|[C 資料庫::開啟](#isopen)|如果物件當前連接到數據源`CDatabase`,則返回非零。|
|[C 資料庫::開啟選項](#onsetoptions)|由框架調用以設置標準連接選項。 預設實現設置查詢超時值。 您可以通過調`SetQueryTimeout`用 來提前建立這些選項。|
|[C 資料庫::開啟](#open)|建立與數據源的連接(透過ODBC驅動程式)。|
|[C 資料庫::開啟Ex](#openex)|建立與數據源的連接(透過ODBC驅動程式)。|
|[C 資料庫::回滾](#rollback)|復原在當前事務期間所做的更改。 數據源返回到其以前狀態(如`BeginTrans`調用中定義的那樣)保持不變。|
|[C 資料庫::設定登入逾時](#setlogintimeout)|設置數據源連接嘗試超時後的秒數。|
|[C 資料庫::設定查詢逾時](#setquerytimeout)|設置資料庫查詢操作超時後的秒數。影響所有後續記錄集`Open``AddNew`、`Edit`調`Delete`用。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[C 資料庫::m_hdbc](#m_hdbc)|開啟資料庫連接 (ODBC) 連接到資料來源。 *HDBC*類型 。|

## <a name="remarks"></a>備註

數據源是由某些資料庫管理系統 (DBMS) 託管的數據的特定實例。 示例包括微軟 SQL 伺服器、微軟訪問、博蘭 dBASE 和 xBASE。 在應用程式中,一次可以`CDatabase`啟動一個或多個物件。

> [!NOTE]
> 如果使用資料存取物件 (DAO) 類別而不是開放資料庫連線 (ODBC) 類別,請使用類別[CDao 資料庫](../../mfc/reference/cdaodatabase-class.md)。 有關詳細資訊,請參閱文章[概述:資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。

要使用`CDatabase`,建`CDatabase`構 物件並調用`OpenEx`其成員 函數。 這將打開連接。 然後建構`CRecordset`物件以在連接的數據源上操作時,將記錄集構造函數傳遞給物件`CDatabase`的指標。 使用完連接後,調用`Close`成員函數並銷毀`CDatabase`物件。 `Close`關閉以前未關閉的任何記錄集。

關於的詳細資訊`CDatabase`,請參考[資料來源 (ODBC)](../../data/odbc/data-source-odbc.md)和[概述:資料庫程式設計](../../data/data-access-programming-mfc-atl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CDatabase`

## <a name="requirements"></a>需求

**標題:** afxdb.h

## <a name="cdatabasebegintrans"></a><a name="begintrans"></a>C 資料庫::開始轉換

調用此成員函數以開始具有連接的數據源的事務。

```
BOOL BeginTrans();
```

### <a name="return-value"></a>傳回值

如果呼叫成功且僅手動提交更改,則非零;否則 0。

### <a name="remarks"></a>備註

事務`AddNew``Edit``Delete``Update`由對`CRecordset`物件的 的一個或多個調用組成,以及對象的成員函數。 在開始事務之前,`CDatabase`對象必須透過呼`OpenEx`叫`Open`其 或成員函數連接到資料來源。 要結束事務,請致電[CommitTrans](#committrans)接受對資料源的所有更改(並執行這些更改),或調用[回滾](#rollback)以中止整個事務。 打開`BeginTrans`事務中涉及的任何記錄集並盡可能接近實際更新操作後調用。

> [!CAUTION]
> 根據您的 ODBC 驅動程式,在`BeginTrans`調用 之前打開記錄集可能會`Rollback`導致調用 時出現問題。 您應該檢查您正在使用的特定驅動程式。 例如,當使用 Microsoft ODBC 桌面驅動程式包 3.0 中包含的 Microsoft Access 驅動程式時,必須考慮 Jet 資料庫引擎的要求,即不應在具有打開游標的任何資料庫上開始事務。 在 MFC 資料庫類中,打開的`CRecordset`游標 表示打開的物件。 有關詳細資訊,請參閱[技術說明 68](../../mfc/tn068-performing-transactions-with-the-microsoft-access-7-odbc-driver.md)。

`BeginTrans`還可能鎖定伺服器上的數據記錄,具體取決於請求的併發和數據源的功能。 有關鎖定數據的資訊,請參閱[文章"記錄集:鎖定記錄"(ODBC)。](../../data/odbc/recordset-locking-records-odbc.md)

使用者定義的事務在文章[事務 (ODBC) 中解釋。](../../data/odbc/transaction-odbc.md)

`BeginTrans`建立可以回滾(反向)的事務序列的狀態。 要為回滾建立新狀態,請提交任何當前事務,然後再次呼叫`BeginTrans`。

> [!CAUTION]
> 再次`BeginTrans`調用而不調`CommitTrans`用`Rollback`或 是一個錯誤。

呼叫[CanTransact](#cantransact)成員函數以確定驅動程式是否支援給定資料庫的事務。 您還應呼叫[GetCursorCommitCommit行為](#getcursorcommitbehavior)和[GetCursorRollback行為,](#getcursorrollbackbehavior)以確定對遊標保留的支援。

有關交易記錄的詳細資訊,請參閱文章[事務 (ODBC)](../../data/odbc/transaction-odbc.md)。

### <a name="example"></a>範例

  請參閱文章[「事務:在記錄集 (ODBC) 中執行事務](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)」。

## <a name="cdatabasebindparameters"></a><a name="bindparameters"></a>C 資料庫::結合參數

在`BindParameters`調用[CDatabase::執行SQL](#executesql)之前需要綁定參數時,請覆蓋。

```
virtual void BindParameters(HSTMT hstmt);
```

### <a name="parameters"></a>參數

*hstmt*<br/>
要為其綁定參數的 ODBC 語句句柄。

### <a name="remarks"></a>備註

當您不需要存儲過程的結果集時,此方法非常有用。

在重寫中,調用`SQLBindParameters`和相關ODBC函數以綁定參數。 MFC`ExecuteSQL`在調用 之前調用 重寫。 你不需要打電話`SQLPrepare`。`ExecuteSQL`調用`SQLExecDirect`並銷毀*hstmt,* 它只使用一次。

## <a name="cdatabasecancel"></a><a name="cancel"></a>C 資料庫::取消

調用此成員函數請求數據源取消正在進行的非同步操作或從第二個線程取消進程。

```
void Cancel();
```

### <a name="remarks"></a>備註

請注意,MFC ODBC 類不再使用非同步處理;要執行非同步操作,必須直接呼叫 ODBC API 函數[SQLSetConnectOption](/sql/odbc/reference/syntax/sqlsetconnectoption-function)。 有關詳細資訊,請參閱[非同步執行](/sql/odbc/reference/develop-app/asynchronous-execution)。

## <a name="cdatabasecantransact"></a><a name="cantransact"></a>C 資料庫::可以

調用此成員函數以確定資料庫是否允許事務。

```
BOOL CanTransact() const;
```

### <a name="return-value"></a>傳回值

如果使用此`CDatabase`物件的記錄集允許事務,則非零;否則 0。

### <a name="remarks"></a>備註

有關交易記錄的資訊,請參閱文章事務[(ODBC)](../../data/odbc/transaction-odbc.md)。

## <a name="cdatabasecanupdate"></a><a name="canupdate"></a>C 資料庫::可以更新

調用此成員函數以確定`CDatabase`物件是否允許更新。

```
BOOL CanUpdate() const;
```

### <a name="return-value"></a>傳回值

如果物件允許更新`CDatabase`,則非零;否則 0,指示在`CDatabase`打開 物件時在*bReadOnly*中傳遞 TRUE,或者數據源本身是唯讀的。 如果對 ODBC API`SQLGetInfo`函數 的呼叫傳回 SQL_DATASOURCE_READ_ONLY回「y」,則數據來源是唯讀的。

### <a name="remarks"></a>備註

並非所有驅動程式都支援更新。

## <a name="cdatabasecdatabase"></a><a name="cdatabase"></a>C 資料庫:C 資料庫

建構 `CDatabase` 物件。

```
CDatabase();
```

### <a name="remarks"></a>備註

建構物件後,必須調用其`OpenEx``Open`或成員函數以建立與指定數據源的連接。

您可能會發現將`CDatabase`物件嵌入到文檔類中很方便。

### <a name="example"></a>範例

此示例說明瞭在`CDocument`派`CDatabase`生 類中的使用。

[!code-cpp[NVC_MFCDatabase#9](../../mfc/codesnippet/cpp/cdatabase-class_1.h)]

[!code-cpp[NVC_MFCDatabase#10](../../mfc/codesnippet/cpp/cdatabase-class_2.cpp)]

## <a name="cdatabaseclose"></a><a name="close"></a>C 資料庫:關閉

如果要斷開與數據源的連接,請調用此成員函數。

```
virtual void Close();
```

### <a name="remarks"></a>備註

在呼叫此成員函數之前,`CDatabase`必須關閉與物件關聯的任何記錄集。 因為`Close`不會破壞`CDatabase`物件,因此可以通過打開與同一數據源或其他數據源的新連接來重用該物件。

使用資料庫`AddNew`的所有`Edit`掛起或記錄集的語句都將被取消,並且所有掛起的事務都將回滾。 依賴於`CDatabase`物件的任何記錄集都處於未定義狀態。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#12](../../mfc/codesnippet/cpp/cdatabase-class_3.cpp)]

## <a name="cdatabasecommittrans"></a><a name="committrans"></a>C 資料庫::提交轉換

完成事務時調用此成員函數。

```
BOOL CommitTrans();
```

### <a name="return-value"></a>傳回值

如果已成功提交更新,則非零;否則 0。 如果`CommitTrans`失敗,資料源的狀態將未定義。 您必須檢查數據以確定其狀態。

### <a name="remarks"></a>備註

事務包括`AddNew`一系列`Edit``Delete``Update``CRecordset`對對物件的調用,以及以調用[BeginTrans](#begintrans)成員函數開頭的物件的成員函數。 `CommitTrans`提交事務。 默認情況下,將立即提交更新;因此,更新將立即提交。調用`BeginTrans`會導致更新的承諾延遲`CommitTrans`到調用。

在調用`CommitTrans`結束事務之前,可以調用[回滾](#rollback)成員函數以中止事務並將數據源保留為其原始狀態。 要開始新事務,請再次`BeginTrans`調用。

有關交易記錄的詳細資訊,請參閱文章[事務 (ODBC)](../../data/odbc/transaction-odbc.md)。

### <a name="example"></a>範例

  請參閱文章[「事務:在記錄集 (ODBC) 中執行事務](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)」。

## <a name="cdatabaseexecutesql"></a><a name="executesql"></a>C 資料庫::執行SQL

當您需要直接執行 SQL 命令時,請調用此成員函數。

```
void ExecuteSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>參數

*lpszSQL*<br/>
包含要執行的有效 SQL 指令的 null 連接端接字串的指標。 你可以傳遞一個[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>備註

將指令建立為 null 終止字串。 `ExecuteSQL`不返回數據記錄。 如果要對記錄操作,請使用記錄集物件。

數據源的大多數命令都通過記錄集物件發出,這些物件支援選擇資料、插入新記錄、刪除記錄和編輯記錄的命令。 但是,並非所有 ODBC 功能都由資料庫類別直接支援,因此有時您可能需要使用 進行直接 SQL 呼叫`ExecuteSQL`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#13](../../mfc/codesnippet/cpp/cdatabase-class_4.cpp)]

## <a name="cdatabasegetbookmarkpersistence"></a><a name="getbookmarkpersistence"></a>C 資料庫::獲取書籤持久性

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
|SQL_BP_CLOSE|書籤在`Requery`操作後有效。|
|SQL_BP_DELETE|行的書籤在該行`Delete`的操作后有效。|
|SQL_BP_DROP|書籤在`Close`操作後有效。|
|SQL_BP_SCROLL|書籤在任何`Move`操作后都有效。 這可輕鬆地識別記錄集上是否支援書籤，如 `CRecordset::CanBookmark` 所傳回的那樣。|
|SQL_BP_TRANSACTION|書籤在認可或回復異動之後有效。|
|SQL_BP_UPDATE|行的書籤在該行`Update`的操作后有效。|
|SQL_BP_OTHER_HSTMT|與一個記錄集物件相關聯的書籤在第二個記錄集上有效。|

有關此返回值的詳細資訊,請參閱 Windows SDK 中的`SQLGetInfo`ODBC API 功能。 有關書籤的詳細資訊,請參閱[文章"記錄集:書籤和絕對位置 "(ODBC)。](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

## <a name="cdatabasegetconnect"></a><a name="getconnect"></a>C 資料庫::取得連線

呼叫此成員函數以檢索呼叫`OpenEx`到`Open``CDatabase`或 將 物件連接到資料來源期間使用的連接字串。

```
const CString GetConnect() const;
```

### <a name="return-value"></a>傳回值

在`OpenEx`呼叫`Open`或已呼叫連接字串時包含連接字串的**const**[CString;](../../atl-mfc-shared/reference/cstringt-class.md)否則,一個空字串。

### <a name="remarks"></a>備註

有關如何建立連接字串的說明,請參閱[CDatabase::開啟](#open)。

## <a name="cdatabasegetcursorcommitbehavior"></a><a name="getcursorcommitbehavior"></a>C 資料庫::取得游標提交行為

呼叫此成員函數以確定[CommitTrans](#committrans)操作如何影響打開的記錄集物件上的遊標。

```
int GetCursorCommitBehavior() const;
```

### <a name="return-value"></a>傳回值

指示事務對打開的記錄集物件的影響的值。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

下表列出了 打開的記錄集的`GetCursorCommitBehavior`可能 返回值和相應的影響。

|傳回值|對 CRecordset 物件的影響|
|------------------|----------------------------------|
|SQL_CB_CLOSE|在`CRecordset::Requery`事務提交后立即調用。|
|SQL_CB_DELETE|在`CRecordset::Close`事務提交后立即調用。|
|SQL_CB_PRESERVE|正常地執行`CRecordset`操作。|

有關此返回值的詳細資訊,請參閱 Windows SDK 中的`SQLGetInfo`ODBC API 功能。 有關交易記錄的詳細資訊,請參閱文章[事務 (ODBC)](../../data/odbc/transaction-odbc.md)。

## <a name="cdatabasegetcursorrollbackbehavior"></a><a name="getcursorrollbackbehavior"></a>C 資料庫::取得游標回滾行為

調用此成員函數以確定[回滾](#rollback)操作如何影響打開的記錄集物件上的游標。

```
int GetCursorRollbackBehavior() const;
```

### <a name="return-value"></a>傳回值

指示事務對打開的記錄集物件的影響的值。 如需詳細資料，請參閱＜備註＞。

### <a name="remarks"></a>備註

下表列出了 打開的記錄集的`GetCursorRollbackBehavior`可能 返回值和相應的影響。

|傳回值|對 CRecordset 物件的影響|
|------------------|----------------------------------|
|SQL_CB_CLOSE|在`CRecordset::Requery`事務回滾后立即調用。|
|SQL_CB_DELETE|在`CRecordset::Close`事務回滾后立即調用。|
|SQL_CB_PRESERVE|正常地執行`CRecordset`操作。|

有關此返回值的詳細資訊,請參閱 Windows SDK 中的`SQLGetInfo`ODBC API 功能。 有關交易記錄的詳細資訊,請參閱文章[事務 (ODBC)](../../data/odbc/transaction-odbc.md)。

## <a name="cdatabasegetdatabasename"></a><a name="getdatabasename"></a>C 資料庫::取得資料庫名稱

調用此成員函數以檢索當前連接的資料庫的名稱(前提是數據源定義了名為"資料庫"的命名物件)。

```
CString GetDatabaseName() const;
```

### <a name="return-value"></a>傳回值

包含資料庫名稱的[CString(](../../atl-mfc-shared/reference/cstringt-class.md)如果成功);否則,空`CString`。

### <a name="remarks"></a>備註

這與或`OpenEx``Open`調用中指定的數據源名稱 (DSN) 不同。 返回`GetDatabaseName`的內容取決於 ODBC。 通常,資料庫是表的集合。 如果此實體具有名稱,`GetDatabaseName`則傳回它。

例如,您可能希望在標題中顯示此名稱。 如果從 ODBC 檢索名稱時發生`GetDatabaseName`錯誤,`CString`則傳回空 。

## <a name="cdatabaseisopen"></a><a name="isopen"></a>C 資料庫::開啟

呼叫此成員函數以確定`CDatabase`物件當前是否連接到資料源。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果物件當前已`CDatabase`連接,則非零;否則 0。

## <a name="cdatabasem_hdbc"></a><a name="m_hdbc"></a>C 資料庫::m_hdbc

包含 ODBC 資料源連接的公共句柄 - 「連接句柄」。

### <a name="remarks"></a>備註

通常,您無需直接訪問此成員變數。 相反,框架在調用`OpenEx``Open`或 時分配句柄。 當您呼叫`CDatabase`物件上的**delete**運算符時,框架將解分配句柄。 請注意,`Close`成員函數不會解分配句柄。

但是,在某些情況下,您可能需要直接使用該句柄。 例如,如果需要直接調用 ODBC API 函數,`CDatabase`而不是通過類 調用 ,則可能需要連接句柄作為參數傳遞。 請參閱下面的代碼示例。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#15](../../mfc/codesnippet/cpp/cdatabase-class_5.cpp)]

## <a name="cdatabaseonsetoptions"></a><a name="onsetoptions"></a>C 資料庫::開啟選項

當直接使用成員函數執行 SQL 語句`ExecuteSQL`時, 框架將呼叫此成員函數。

```
virtual void OnSetOptions(HSTMT hstmt);
```

### <a name="parameters"></a>參數

*hstmt*<br/>
正在為其設定選項的 ODBC 語句句柄。

### <a name="remarks"></a>備註

`CRecordset::OnSetOptions`也稱為此成員函數。

`OnSetOptions`設置登錄超時值。 如果以前對 和成員函`SetQueryTimeout`數 進行了調用`OnSetOptions`,則反映當前值;如果以前對 和成員函數進行了調用,則反映當前值。否則,它將設置預設值。

> [!NOTE]
> 在 MFC 4.2`OnSetOptions`之前,還將處理模式設置為 snychronous 或異步。 從 MFC 4.2 開始,所有操作都是同步的。 要執行非同步操作,必須直接呼叫 ODBC API`SQLSetPos`函式 。

不需要重寫`OnSetOptions`來更改超時值。 相反,要自定義查詢超時值,請在創建記錄`SetQueryTimeout`集之前調用;但是,為了自定義查詢超時值,請在創建記錄集之前調用。`OnSetOptions`將使用新值。 設置的值適用於所有記錄集或直接 SQL 調用的後續操作。

如果要`OnSetOptions`設置其他選項,則重寫。 重寫應在調用 ODBC `OnSetOptions` API`SQLSetStmtOption`函數 之前或之後調用基類。 按照框架的默認實現中所示的方法`OnSetOptions`操作。

## <a name="cdatabaseopen"></a><a name="open"></a>C 資料庫::開啟

調用此成員函數以初始化新構造`CDatabase`的物件。

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
指定資料來源名稱 – 透過 ODBC 管理員程式在 ODBC 註冊的名稱。 如果在*lpszConnect*中指定了 DSN 值(以\<"DSN+ 資料源>形式"),則不得在*lpszDSN*中再次指定它。 在這種情況下 *,lpszDSN*應為 NULL。 否則,如果要向使用者顯示數據源對話框,用戶可以在該對話方塊中選擇數據源,則可以傳遞 NULL。 有關詳細資訊,請參閱備註。

*b 獨家*<br/>
此版本的類庫不支援。 目前,如果此參數為 TRUE,斷言將失敗。 數據源始終以共用形式打開(非獨佔)。

*b 唯讀*<br/>
如果希望連接為唯讀,並且禁止對資料源的更新,則為 TRUE。 所有從屬記錄集都繼承此屬性。 預設值為 FALSE。

*lpszConnect*<br/>
指定連接字串。 連接字串串聯資訊,可能包括資料源名稱、數據源上有效的使用者 ID、使用者身份驗證字串(如果數據源需要密碼)和其他資訊。 整個連接字串必須由字串"ODBC;"預定。(大寫或小寫)。 "ODBC;"字串用於指示連接與 ODBC 資料源的連接;當類庫的未來版本可能支援非 ODBC 數據源時,這是為了向上相容。

*bUseCursorLib*<br/>
如果希望載入 ODBC 游標庫 DLL,則為 TRUE。 游標庫遮罩了基礎ODBC驅動程式的某些功能,從而有效地防止動態集的使用(如果驅動程式支援它們)。 載入游標庫時支援的唯一游標是靜態快照和僅轉發游標。 預設值為 TRUE。 如果計劃直接從`CRecordset`創建記錄集物件而不派生,則不應載入游標庫。

### <a name="return-value"></a>傳回值

如果連接成功,則非零;否則 0 如果使用者在顯示對話方塊時選擇" 取消" 在所有其他情況下,框架將引發異常。

### <a name="remarks"></a>備註

必須先初始化資料庫物件,然後才能使用它構造記錄集物件。

> [!NOTE]
> 呼叫[OpenEx](#openex)成員函數是連接到資料來源並初始化資料庫物件的首選方法。

如果`Open`呼叫中的參數不包含足夠的資訊來建立連接,ODBC 驅動程式將打開一個對話框,從使用者處獲取必要的資訊。 調用`Open`時,連接字串*lpszConnect*會私下存儲在`CDatabase`物件中,並且可以通過調用[GetConnect](#getconnect)成員函數來獲取。

如果需要,可以在調用`Open`之前打開自己的對話框,以便從使用者獲取資訊(如密碼),然後將該資訊添加到傳遞給的連接字串`Open`中。 或者,您可能希望保存傳遞的連接字串,以便在應用程式下次調用`Open``CDatabase`物件時重用它。

您還可以將連接字串用於多個級別的登錄授權(每個級別用於其他`CDatabase`物件),或傳輸其他特定於數據來源的資訊。 有關連接字串的詳細資訊,請參閱 Windows SDK 中的第 5 章。

例如,如果 DBMS 主機不可用,連接嘗試可能會超時。 如果連線嘗試失敗,`Open`則`CDBException`引發 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#14](../../mfc/codesnippet/cpp/cdatabase-class_6.cpp)]

## <a name="cdatabaseopenex"></a><a name="openex"></a>C 資料庫::開啟Ex

調用此成員函數以初始化新構造`CDatabase`的物件。

```
virtual BOOL OpenEx(
    LPCTSTR lpszConnectString,
    DWORD dwOptions = 0);
```

### <a name="parameters"></a>參數

*lpszConnectString*<br/>
指定 ODBC 連接字串。 這包括數據源名稱以及其他可選資訊,如使用者 ID 和密碼。 例如,"DSN=SQLServer_Source;UID_SA;PWD_abc123" 是一個可能的連接字串。 請注意,如果透過 NULL 的*lpszConnectString*,資料源對話框將提示使用者選擇資料來源。

*dwOptions*<br/>
指定以下值組合的位掩碼。 默認值為 0,這意味著資料庫將以寫入存取共用方式打開,不會載入 ODBC 游標庫 DLL,並且 ODBC 連接對話方塊僅在沒有足夠的資訊進行連接時才會顯示。

- `CDatabase::openExclusive`此版本的類庫不支援。 數據源始終以共用形式打開(非獨佔)。 目前,如果指定此選項,斷言將失敗。

- `CDatabase::openReadOnly`將數據源打開為唯讀。

- `CDatabase::useCursorLib`載入 ODBC 游標庫 DLL。 游標庫遮罩了基礎ODBC驅動程式的某些功能,從而有效地防止動態集的使用(如果驅動程式支援它們)。 載入游標庫時支援的唯一游標是靜態快照和僅轉發游標。 如果計劃直接從`CRecordset`創建記錄集物件而不派生,則不應載入游標庫。

- `CDatabase::noOdbcDialog`無論是否提供了足夠的連接資訊,請勿顯示 ODBC 連接對話方塊。

- `CDatabase::forceOdbcDialog`始終顯示 ODBC 連接對話方塊。

### <a name="return-value"></a>傳回值

如果連接成功,則非零;否則 0 如果使用者在顯示對話方塊時選擇" 取消" 在所有其他情況下,框架將引發異常。

### <a name="remarks"></a>備註

必須先初始化資料庫物件,然後才能使用它構造記錄集物件。

如果`OpenEx`呼叫中的*lpszConnectString*參數不包含足夠的資訊進行連接,則 ODBC 驅動程式將打開一個對話框,從使用者處獲取必要的資訊`CDatabase::noOdbcDialog`,`CDatabase::forceOdbcDialog`前提是您尚未設置 或位於*dwOptions*參數中。 呼叫`OpenEx`時,連接字串*lpszConnectString*會私下存儲在物件中`CDatabase`,並且可透過調用[GetConnect](#getconnect)成員函數獲得。

如果需要,可以在調用`OpenEx`之前打開自己的對話框,以便從使用者獲取資訊(如密碼),然後將該資訊添加到傳遞`OpenEx`給的連接字串中。 或者,您可能希望保存傳遞的連接字串,以便在應用程式下次調用`OpenEx``CDatabase`物件時重用它。

您還可以將連接字串用於多個級別的登錄授權(每個級別用於其他`CDatabase`物件),或傳輸其他特定於數據來源的資訊。 有關連接字串的詳細資訊,請參閱*ODBC 程式師參考*章的第 6 章。

例如,如果 DBMS 主機不可用,連接嘗試可能會超時。 如果連線嘗試失敗,`OpenEx`則`CDBException`引發 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCDatabase#11](../../mfc/codesnippet/cpp/cdatabase-class_7.cpp)]

## <a name="cdatabaserollback"></a><a name="rollback"></a>C 資料庫::回滾

呼叫此成員函數以撤銷在事務期間所做的更改。

```
BOOL Rollback();
```

### <a name="return-value"></a>傳回值

如果事務已成功沖銷,則非零;否則 0。 如果`Rollback`調用失敗,則數據源和事務狀態未定義。 如果`Rollback`返回 0,則必須檢查數據源以確定其狀態。

### <a name="remarks"></a>備註

自上次`CRecordset``AddNew``Edit` [BeginTrans](#begintrans)`Update`以來執行`Delete`的所有 、 和調用都將回滾到該調用時的狀態。

呼叫`Rollback`後,事務已結束,您必須再次調`BeginTrans`用 另一個事務。 調用`BeginTrans`之前當前的記錄在`Rollback`之後 再次成為當前記錄。

回滾后,回滾之前當前的記錄將保持最新狀態。 有關回滾後記錄集的狀態和數據源的詳細資訊,請參閱文章[事務 (ODBC)。](../../data/odbc/transaction-odbc.md)

### <a name="example"></a>範例

  請參閱文章[「事務:在記錄集 (ODBC) 中執行事務](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)」。

## <a name="cdatabasesetlogintimeout"></a><a name="setlogintimeout"></a>C 資料庫::設定登入逾時

調用此成員函數 (在呼`OpenEx`叫`Open`之前或—以覆寫資料源嘗試連接超時之前允許的預設秒數)。

```
void SetLoginTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>參數

*dw 秒*<br/>
連接嘗試超時之前要允許的秒數。

### <a name="remarks"></a>備註

例如,如果 DBMS 不可用,則連接嘗試可能會超時。 建構`SetLoginTimeout`未初始`CDatabase`化 的物件後,但在呼`OpenEx``Open`叫或之前呼叫 。

登錄超時的預設值為 15 秒。 並非所有數據源都支援指定登錄超時值的能力。 如果數據源不支援超時,您將獲得跟蹤輸出,但不會提供異常。 值 0 表示"無限"。

## <a name="cdatabasesetquerytimeout"></a><a name="setquerytimeout"></a>C 資料庫::設定查詢逾時

調用此成員函數以覆蓋預設秒數,以便在後續對連接的數據源超時的操作之前允許。

```
void SetQueryTimeout(DWORD dwSeconds);
```

### <a name="parameters"></a>參數

*dw 秒*<br/>
查詢嘗試超時之前要允許的秒數。

### <a name="remarks"></a>備註

操作可能會由於網路訪問問題、查詢處理時間過長等原因而超時。 如果要`SetQueryTimeout`更改查詢超時值,請先打開記錄集之前或調用記錄`AddNew``Update`集`Delete`的 或 成員函數之前調用。 該設置影響所有後續`Open``AddNew`的`Update`、`Delete`對與此`CDatabase`物件關聯的任何記錄集的調用。 打開後更改記錄集的查詢超時值不會更改記錄集的值。 例如,後續`Move`操作不使用新值。

查詢超時的預設值為 15 秒。 並非所有數據源都支援設置查詢超時值的能力。 如果將查詢超時值設置為 0,則不執行超時;如果將超時設置為 0,則不執行超時。與數據源的通信可能會停止回應。 此行為在開發期間可能很有用。 如果數據源不支援超時,您將獲得跟蹤輸出,但不會提供異常。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 類別](../../mfc/reference/crecordset-class.md)
