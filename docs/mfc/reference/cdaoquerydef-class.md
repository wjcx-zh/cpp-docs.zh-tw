---
title: CDaoQueryDef 類別
ms.date: 11/04/2016
f1_keywords:
- CDaoQueryDef
- AFXDAO/CDaoQueryDef
- AFXDAO/CDaoQueryDef::CDaoQueryDef
- AFXDAO/CDaoQueryDef::Append
- AFXDAO/CDaoQueryDef::CanUpdate
- AFXDAO/CDaoQueryDef::Close
- AFXDAO/CDaoQueryDef::Create
- AFXDAO/CDaoQueryDef::Execute
- AFXDAO/CDaoQueryDef::GetConnect
- AFXDAO/CDaoQueryDef::GetDateCreated
- AFXDAO/CDaoQueryDef::GetDateLastUpdated
- AFXDAO/CDaoQueryDef::GetFieldCount
- AFXDAO/CDaoQueryDef::GetFieldInfo
- AFXDAO/CDaoQueryDef::GetName
- AFXDAO/CDaoQueryDef::GetODBCTimeout
- AFXDAO/CDaoQueryDef::GetParameterCount
- AFXDAO/CDaoQueryDef::GetParameterInfo
- AFXDAO/CDaoQueryDef::GetParamValue
- AFXDAO/CDaoQueryDef::GetRecordsAffected
- AFXDAO/CDaoQueryDef::GetReturnsRecords
- AFXDAO/CDaoQueryDef::GetSQL
- AFXDAO/CDaoQueryDef::GetType
- AFXDAO/CDaoQueryDef::IsOpen
- AFXDAO/CDaoQueryDef::Open
- AFXDAO/CDaoQueryDef::SetConnect
- AFXDAO/CDaoQueryDef::SetName
- AFXDAO/CDaoQueryDef::SetODBCTimeout
- AFXDAO/CDaoQueryDef::SetParamValue
- AFXDAO/CDaoQueryDef::SetReturnsRecords
- AFXDAO/CDaoQueryDef::SetSQL
- AFXDAO/CDaoQueryDef::m_pDAOQueryDef
- AFXDAO/CDaoQueryDef::m_pDatabase
helpviewer_keywords:
- CDaoQueryDef [MFC], CDaoQueryDef
- CDaoQueryDef [MFC], Append
- CDaoQueryDef [MFC], CanUpdate
- CDaoQueryDef [MFC], Close
- CDaoQueryDef [MFC], Create
- CDaoQueryDef [MFC], Execute
- CDaoQueryDef [MFC], GetConnect
- CDaoQueryDef [MFC], GetDateCreated
- CDaoQueryDef [MFC], GetDateLastUpdated
- CDaoQueryDef [MFC], GetFieldCount
- CDaoQueryDef [MFC], GetFieldInfo
- CDaoQueryDef [MFC], GetName
- CDaoQueryDef [MFC], GetODBCTimeout
- CDaoQueryDef [MFC], GetParameterCount
- CDaoQueryDef [MFC], GetParameterInfo
- CDaoQueryDef [MFC], GetParamValue
- CDaoQueryDef [MFC], GetRecordsAffected
- CDaoQueryDef [MFC], GetReturnsRecords
- CDaoQueryDef [MFC], GetSQL
- CDaoQueryDef [MFC], GetType
- CDaoQueryDef [MFC], IsOpen
- CDaoQueryDef [MFC], Open
- CDaoQueryDef [MFC], SetConnect
- CDaoQueryDef [MFC], SetName
- CDaoQueryDef [MFC], SetODBCTimeout
- CDaoQueryDef [MFC], SetParamValue
- CDaoQueryDef [MFC], SetReturnsRecords
- CDaoQueryDef [MFC], SetSQL
- CDaoQueryDef [MFC], m_pDAOQueryDef
- CDaoQueryDef [MFC], m_pDatabase
ms.assetid: 9676a4a3-c712-44d4-8c5d-d1cc78288d3a
ms.openlocfilehash: 133746ff1e4a9453f9563347724a47855a8a3228
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368956"
---
# <a name="cdaoquerydef-class"></a>CDaoQueryDef 類別

表示查詢定義 (或 "querydef")，通常是儲存在資料庫中的定義。

## <a name="syntax"></a>語法

```
class CDaoQueryDef : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[道查詢Def::CDaoQueryDef](#cdaoquerydef)|建構 `CDaoQueryDef` 物件。 下一`Open`個`Create`電話 或 ,具體取決於您的需要。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDaoQueryDef:附加](#append)|將查詢def追加到資料庫的 QueryDefs 集合作為保存的查詢。|
|[CDaoQueryDef:可以更新](#canupdate)|如果查詢可以更新資料庫,則返回非零。|
|[CDaoQueryDef:關閉](#close)|關閉查詢def物件。 完成後,銷毀C++物件。|
|[CDaoQueryDef:建立](#create)|創建基礎 DAO 查詢def 物件。 將查詢def用作臨時查詢,或調用`Append`將其保存在資料庫中。|
|[CDaoQueryDef:執行](#execute)|執行查詢def物件定義的查詢。|
|[CDaoQueryDef:取得連線](#getconnect)|傳回與查詢def關聯的連接字串。 連接字串識別資料來源。 (僅適用於 SQL 傳遞查詢;否則為空字串。|
|[CDaoQueryDef:取得日期建立](#getdatecreated)|返回創建保存的查詢的日期。|
|[CDaoQueryDef:取得更新日期](#getdatelastupdated)|返回上次更新保存的查詢的日期。|
|[CDaoQueryDef:取得現場計數](#getfieldcount)|返回查詢def定義的欄位數。|
|[CDaoQueryDef:取得菲爾德資訊](#getfieldinfo)|返回有關在查詢中定義的指定欄位的資訊。|
|[CDaoQueryDef:取得名稱](#getname)|返回查詢def的名稱。|
|[CDaoQueryDef:取得ODBC時間](#getodbctimeout)|在執行查詢def時返回ODBC(用於ODBC查詢)使用的超時值。 這將確定允許查詢操作完成的時間。|
|[CDao 查詢Def:取得參數計數](#getparametercount)|返回為查詢定義的參數數。|
|[CDaoQueryDef:取得參數資訊](#getparameterinfo)|將有關指定參數的資訊返回給查詢。|
|[CDaoQueryDef:取得帕拉姆價值](#getparamvalue)|將指定參數的值返回給查詢。|
|[CDaoQueryDef:取得受影響的記錄](#getrecordsaffected)|返回受操作查詢影響的記錄數。|
|[CDaoQueryDef:取得退貨記錄](#getreturnsrecords)|如果查詢def 定義的查詢返回記錄,則返回非零。|
|[CDaoQueryDef:取得SQL](#getsql)|傳回指定查詢 def 定義的 SQL 字串。|
|[CDaoQueryDef:取得類型](#gettype)|返回查詢類型:刪除、更新、追加、製作表等。|
|[CDaoQueryDef:是開放的](#isopen)|如果查詢def處於打開狀態,則可以執行,則返回非零。|
|[CDaoQueryDef:開啟](#open)|打開存儲在資料庫的 QueryDefs 集合中的現有查詢def。|
|[CDaoQueryDef:設定連線](#setconnect)|設定 ODBC 資料來源上的 SQL 傳遞查詢的連接字串。|
|[CDaoQueryDef:set 名稱](#setname)|設定保存的查詢的名稱,在創建查詢def時替換正在使用的名稱。|
|[CDaoQueryDef:設定ODBC時間](#setodbctimeout)|設置執行查詢def時 ODBC(用於 ODBC 查詢)使用的超時值。|
|[CDaoQueryDef:setParam值](#setparamvalue)|將指定參數的值設置到查詢。|
|[CDao查詢Def:設定傳回記錄](#setreturnsrecords)|指定查詢def 是否返回記錄。 將此屬性設置為 TRUE 僅適用於 SQL 傳遞查詢。|
|[CDao查詢Def:SetSQL](#setsql)|設定指定查詢 def 定義的查詢的 SQL 字串。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDaoQueryDef:m_pDAOQueryDef](#m_pdaoquerydef)|指向基礎 DAO 查詢def 物件的 OLE 介面的指標。|
|[CDaoQueryDef:m_pDatabase](#m_pdatabase)|指向與查詢def`CDaoDatabase`關聯的對象的指標。 查詢def可能保存在資料庫中,也可能不保存在資料庫中。|

## <a name="remarks"></a>備註

查詢def是一個數據訪問物件,它包含描述查詢的SQL語句及其屬性,如"創建日期"和"ODBC超時"。 您還可以創建臨時查詢def物件而不保存它們,但將資料庫中常用重用的查詢保存起來很方便,而且效率更高。 [CDao資料庫](../../mfc/reference/cdaodatabase-class.md)物件維護一個集合,稱為 QueryDefs 集合,其中包含其保存的查詢defs。

> [!NOTE]
> DAO 資料庫類不同於基於開放資料庫連接 (ODBC) 的 MFC 資料庫類。 所有 DAO 資料庫類名稱都有「CDao」首碼。 您仍可以使用 DAO 類存取 ODBC 資料來源。 一般來說,基於 DAO 的 MFC 類比基於 ODBC 的 MFC 類更有能力;基於 DAO 的類可以通過自己的資料庫引擎訪問數據,包括透過 ODBC 驅動程式。 基於 DAO 的類還支援數據定義語言 (DDL) 操作,例如透過類添加表,而無需直接呼叫 DAO。

## <a name="usage"></a>使用量

使用查詢def物件處理現有儲存的查詢或建立新的儲存查詢或暫時查詢:

1. 在所有情況下,首先構造一個`CDaoQueryDef`物件,提供指向查詢所屬的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件的指標。

1. 然後執行以下操作,具體取決於所需內容:

   - 要使用現有的保存查詢,請調用查詢def物件的[Open](#open)成員函數,提供保存的查詢的名稱。

   - 要建立新的保存查詢,請調用查詢def物件的[「創建](#create)成員」函數,提供查詢的名稱。 然後調用[附加程式](#append),通過將查詢追加到資料庫的 QueryDefs 集合來保存查詢。 `Create`將查詢def置於開啟狀態,因此在呼叫`Create`後不呼`Open`叫 。

   - 要建立暫存查詢def,請呼`Create`叫 。 傳遞查詢名稱的空字串。 請不要呼叫 `Append`。

使用查詢def物件完成後,調用其Close成員函數;當使用查詢def物件完成時,調用其[Close](#close)成員函數。然後銷毀查詢def物件。

> [!TIP]
> 創建保存的查詢的最簡單方法是使用 Microsoft Access 創建這些查詢並將其存儲在資料庫中。 然後,您可以在 MFC 代碼中打開並使用它們。

## <a name="purposes"></a>目標

您可以將查詢def物件用於以下任何目的:

- 建立`CDaoRecordset`物件

- 呼叫物件`Execute`的成員函式直接執行操作查詢或 SQL 傳遞查詢

您可以將 querydef 物件用於任何類型的查詢,包括選擇、操作、交叉表、刪除、更新、追加、製作表、數據定義、SQL 傳遞、聯合和批量查詢。 查詢的類型由您提供的 SQL 語句的內容決定。 有關查詢類型的資訊,請參`Execute`閱和[GetType](#gettype)成員函數。 記錄集通常用於返回行的查詢,通常是使用**SELECT 的查詢。從**關鍵字。 `Execute`最常用於批量操作。 有關詳細資訊,請參閱[執行](#execute)與[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

## <a name="querydefs-and-recordsets"></a>查詢def及記錄集

要使用 querydef`CDaoRecordset`物件建立 物件,通常建立或打開查詢def,如上文所述。 然後構造一個記錄集物件,在調用[CDaoRecordset:::打開](../../mfc/reference/cdaorecordset-class.md#open)時,將指標傳遞給查詢def物件。 您傳遞的查詢def必須處於打開狀態。 有關詳細資訊,請參閱類[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

除非記錄def 處於打開狀態,否則不能使用 querydef 創建記錄集(查詢def 的最常用用途)。 通過調用`Open``Create`或將查詢def置於打開狀態。

## <a name="external-databases"></a>外部資料庫

查詢def對像是使用外部資料庫引擎的本機 SQL 方言的首選方法。 例如,您可以創建 Transact SQL 查詢(如在 Microsoft SQL Server 上使用),並將其存儲在查詢def 物件中。 當您需要不使用不基於 Microsoft Jet 資料庫引擎的 SQL 查詢時,必須提供指向外部資料來源的連接字串。 具有有效連接字串的查詢繞過資料庫引擎,並將查詢直接傳遞到外部資料庫伺服器進行處理。

> [!TIP]
> 使用 ODBC 表的首選方法是將它們附加到 Microsoft Jet (。MDB)資料庫。

有關相關信息,請參閱 DAO SDK 中的「查詢Def物件」、「查詢Defs集合」和「Cdb資料庫物件」的主題。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="cdaoquerydefappend"></a><a name="append"></a>CDaoQueryDef:附加

呼叫[Create](#create)後調用此成員函數以創建新的查詢def物件。

```
virtual void Append();
```

### <a name="remarks"></a>備註

`Append`通過將物件追加到資料庫的 QueryDefs 集合,將查詢def儲存在資料庫中。 可以將 querydef 用作臨時物件而不附加它,但如果希望它持久化,則必須`Append`呼叫 。

如果嘗試追加臨時查詢def物件,MFC將引發[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的異常。

## <a name="cdaoquerydefcanupdate"></a><a name="canupdate"></a>CDaoQueryDef:可以更新

呼叫此成員函數以確定是否可以修改查詢def,例如更改其名稱或 SQL 字串。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>傳回值

如果允許修改查詢def,則非零;否則 0。

### <a name="remarks"></a>備註

您可以變更查詢def,如果:

- 它不基於打開唯讀的資料庫。

- 您具有資料庫的更新許可權。

   這取決於您是否實現了安全功能。 MFC 不提供安全性支援;因此,MFC 不提供安全性支援。您必須透過直接調用 DAO 或使用 Microsoft Access 來實現它。 請參閱 DAO 説明中的主題"許可權屬性」。

## <a name="cdaoquerydefcdaoquerydef"></a><a name="cdaoquerydef"></a>道查詢Def::CDaoQueryDef

建構 `CDaoQueryDef` 物件。

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>參數

*p 資料庫*<br/>
指向打開的[CDao 資料庫](../../mfc/reference/cdaodatabase-class.md)物件的指標。

### <a name="remarks"></a>備註

該物件可以表示儲存在資料庫的 QueryDefs 集合中的現有查詢def、要存儲在集合中的新查詢或不儲存的臨時查詢。 下一步取決於查詢def的類型:

- 如果物件表示現有查詢def,請調用物件的[Open](#open)成員函數進行初始化。

- 如果物件表示要保存的新查詢def,請呼叫物件的[「創建](#create)成員」函數。 這會將物件添加到資料庫的 QueryDefs 集合中。 然後調用`CDaoQueryDef`成員函數來設置物件的屬性。 最後,呼叫[附錄](#append)。

- 如果物件表示臨時查詢def(不儲存在資料庫中),則調用`Create`,傳遞查詢名稱的空字串。 調用`Create`後,通過直接設置查詢屬性來初始化查詢def。 請不要呼叫 `Append`。

要設置查詢def的屬性,可以使用[SetODBCTimeout](#setodbctimeout)SetName、SetSQL、SetConnect、SetODBCTimeout 和[SetReturn記錄](#setreturnsrecords)[SetName](#setname)[SetSQL](#setsql)[SetConnect](#setconnect)成員函數。

完成查詢def物件後,調用其[Close](#close)成員函數。 如果有指向查詢def的指標,請使用**delete**運算符銷毀C++物件。

## <a name="cdaoquerydefclose"></a><a name="close"></a>CDaoQueryDef:關閉

使用查詢def物件完成後,調用此成員函數。

```
virtual void Close();
```

### <a name="remarks"></a>備註

關閉查詢def將釋放基礎 DAO 物件,但不會銷毀保存的 DAO`CDaoQueryDef`查詢def 物件 或C++物件。 這與[CDaoDatabase::DeleteQuery Def )](../../mfc/reference/cdaodatabase-class.md#deletequerydef)不同,後者從 DAO 中的資料庫的 QueryDefs 集合中刪除查詢def(如果不是臨時查詢def)。

## <a name="cdaoquerydefcreate"></a><a name="create"></a>CDaoQueryDef:建立

調用此成員函數以創建新的保存查詢或新的臨時查詢。

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
保存在資料庫中的查詢的唯一名稱。 有關字串的詳細資訊,請參閱 DAO 説明中的主題"創建查詢Def方法"。 如果接受預設值,則為空字串,將創建臨時查詢def。 此類查詢不會保存在查詢 Defs 集合中。

*lpszSQL*<br/>
定義查詢的 SQL 字串。 如果接受預設值 NULL,則必須稍後呼叫[SetSQL](#setsql)來設定字串。 在此之前,查詢未定義。 但是,您可以使用未定義的查詢打開記錄集;但是,您可以使用未定義的查詢打開記錄集。有關詳細資訊,請參閱備註。 必須先定義 SQL 語句,然後才能將查詢def追加到 QueryDefs 集合。

### <a name="remarks"></a>備註

如果在*lpszName*中傳遞名稱,則可以調用[附加程式](#append)以將查詢def儲存在資料庫的 QueryDefs 集合中。 否則,該對像是臨時查詢def,並且不保存。 在這兩種情況下,查詢def處於打開狀態,您可以使用它創建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件或調用查詢def的[「執行成員」](#execute)函數。

如果不在*lpszSQL*中提供 SQL 語句 ,`Execute`則無法執行查詢, 但可以使用它創建記錄集。 在這種情況下,MFC 使用記錄集的預設 SQL 語句。

## <a name="cdaoquerydefexecute"></a><a name="execute"></a>CDaoQueryDef:執行

調用此成員函數以運行由查詢def物件定義的查詢。

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>參數

*n 選項*<br/>
確定查詢特徵的整數。 有關相關信息,請參閱 DAO 説明中的主題"執行方法」。。 您可以使用位OR運算子 **(&#124;**) 來組合以下參數的常量:

- `dbDenyWrite`拒絕其他使用者的寫入許可權。

- `dbInconsistent`更新不一致。

- `dbConsistent`一致的更新。

- `dbSQLPassThrough`SQL 傳遞。 使 SQL 語句傳遞到 ODBC 資料庫進行處理。

- `dbFailOnError`默認值。 如果發生錯誤,回滾更新,並將錯誤報告給使用者。

- `dbSeeChanges`如果其他使用者正在更改正在編輯的數據,則生成運行時錯誤。

> [!NOTE]
> 有關術語「不一致」和「一致」的說明,請參閱 DAO 説明中的主題"執行方法」。。

### <a name="remarks"></a>備註

以這種方式用於執行的 Querydef 物件只能表示以下查詢類型之一:

- 操作查詢

- SQL 傳遞查詢

`Execute`不適用於返回記錄的查詢,例如選擇查詢。 `Execute`通常用於批量操作查詢,如**更新**、**插入**、或**SELECT 輸入**,或用於資料定義語言 (DDL) 操作。

> [!TIP]
> 使用 ODBC 資料來源的首選方法是將表附加到 Microsoft Jet (。MDB)資料庫。 有關詳細資訊,請參閱 DAO 説明中的主題"使用 DAO 訪問外部資料庫"

調用查詢def物件的[GetRecords 受影響的](#getrecordsaffected)成員函數,以`Execute`確定受最近調用影響的記錄數。 例如,`GetRecordsAffected`傳回有關在執行作業查詢時刪除、更新或插入的記錄數的資訊。 當級聯更新或刪除生效時,返回的計數不會反映相關表中的更改。

如果同時`dbInconsistent`包含`dbConsistent`與 ,或者如果同時包含兩者,則結果為`dbInconsistent`預設值 。

`Execute`不返回記錄集。 在`Execute`選擇記錄的查詢上使用會導致 MFC 引發[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的異常。

## <a name="cdaoquerydefgetconnect"></a><a name="getconnect"></a>CDaoQueryDef:取得連線

呼叫此成員函數獲取與查詢def的數據源關聯的連接字串。

```
CString GetConnect();
```

### <a name="return-value"></a>傳回值

包含查詢def的連接字串的[CString。](../../atl-mfc-shared/reference/cstringt-class.md)

### <a name="remarks"></a>備註

此功能僅與 ODBC 資料來源和某些 ISAM 驅動程式一起使用。 它不與微軟 Jet (.MDB)資料庫;在這種情況下,`GetConnect`傳回一個空字串。 有關詳細資訊,請參閱[設定連接](#setconnect)。

> [!TIP]
> 使用 ODBC 表的偏好選擇方法是將它們附加到 。MDB 資料庫。 有關詳細資訊,請參閱 DAO 説明中的主題"使用 DAO 訪問外部資料庫"

有關連接字串的資訊,請參閱 DAO 説明中的主題"連接屬性"

## <a name="cdaoquerydefgetdatecreated"></a><a name="getdatecreated"></a>CDaoQueryDef:取得日期建立

呼叫此成員函數以獲取創建查詢def物件的日期。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>傳回值

包含創建查詢def的日期和時間的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件。

### <a name="remarks"></a>備註

有關相關信息,請參閱 DAO 説明中的主題"創建日期,上次更新的屬性"。

## <a name="cdaoquerydefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoQueryDef:取得更新日期

呼叫此成員函數以取得查詢def物件上次更新的日期 - 更改其任何屬性(如其名稱、SQL 字串或連接字串)的日期。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>傳回值

包含查詢def上次更新的日期和時間的[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件。

### <a name="remarks"></a>備註

有關相關信息,請參閱 DAO 説明中的主題"創建日期,上次更新的屬性"。

## <a name="cdaoquerydefgetfieldcount"></a><a name="getfieldcount"></a>CDaoQueryDef:取得現場計數

調用此成員函數以檢索查詢中的欄位數。

```
short GetFieldCount();
```

### <a name="return-value"></a>傳回值

查詢中定義的欄位數。

### <a name="remarks"></a>備註

`GetFieldCount`可用於迴圈瀏覽查詢def中的所有欄位。 為此,請與`GetFieldCount`[GetFieldInfo](#getfieldinfo)結合使用。

## <a name="cdaoquerydefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoQueryDef:取得菲爾德資訊

調用此成員函數以獲取有關查詢def中定義的欄位的各種資訊。

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
查詢def的欄位集合中所需欄位的零基索引,用於按索引進行查找。

*菲爾德資訊*<br/>
對返回請求的信息`CDaoFieldInfo`的物件的引用。

*dwInfoOptions*<br/>
指定要檢索的欄位的資訊的選項。 此處列出可用的選項以及它們導致函數傳回的內容:

- AFX_DAO_PRIMARY_INFO(預設)名稱、類型、大小、屬性

- AFX_DAO_SECONDARY_INFO主要資訊加:序號位置、必需位置、允許零長度、源欄位、外名、源表、分門順序

- AFX_DAO_ALL_INFO主與輔助資訊加上:預設值、驗證文字、驗證規則

*lpsz名稱*<br/>
包含所需欄位名稱的字串,用於按名稱查找。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>備註

有關*在欄位資訊*中返回的資訊的說明,請參閱[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。 此結構的成員對應於上面*的 dwInfoOptions*下的描述性資訊。 如果您請求一級資訊,您也會得到任何以前的資訊級別。

## <a name="cdaoquerydefgetname"></a><a name="getname"></a>CDaoQueryDef:取得名稱

調用此成員函數以檢索查詢def 表示的查詢的名稱。

```
CString GetName();
```

### <a name="return-value"></a>傳回值

查詢的名稱。

### <a name="remarks"></a>備註

查詢def名稱是唯一的使用者定義名稱。 有關查詢定義名稱的詳細資訊,請參閱 DAO 説明中的主題" 名稱屬性"

## <a name="cdaoquerydefgetodbctimeout"></a><a name="getodbctimeout"></a>CDaoQueryDef:取得ODBC時間

呼叫此成員函數,在對 ODBC 數據源的查詢超時之前檢索當前時間限制。

```
short GetODBCTimeout();
```

### <a name="return-value"></a>傳回值

查詢逾時之前的秒數。

### <a name="remarks"></a>備註

有關此時間限制的資訊,請參閱 DAO 説明中的主題"ODBCTime 屬性"。

> [!TIP]
> 使用 ODBC 表的首選方法是將它們附加到 Microsoft Jet (。MDB)資料庫。 有關詳細資訊,請參閱 DAO 説明中的主題"使用 DAO 訪問外部資料庫"

## <a name="cdaoquerydefgetparametercount"></a><a name="getparametercount"></a>CDao 查詢Def:取得參數計數

調用此成員函數以檢索保存的查詢中的參數數。

```
short GetParameterCount();
```

### <a name="return-value"></a>傳回值

查詢中定義的參數數。

### <a name="remarks"></a>備註

`GetParameterCount`可用於迴圈瀏覽查詢def中的所有參數。 為此,請與`GetParameterCount`[GetparameterInfo](#getparameterinfo)結合使用。

有關相關資訊,請參閱 DAO 説明中的「參數物件」、「參數集合」和「參數聲明 (SQL)」主題。

## <a name="cdaoquerydefgetparameterinfo"></a><a name="getparameterinfo"></a>CDaoQueryDef:取得參數資訊

呼叫此成員函數以獲取有關查詢def中定義的參數的資訊。

```
void GetParameterInfo(
    int nIndex,
    CDaoParameterInfo& paraminfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetParameterInfo(
    LPCTSTR lpszName,
    CDaoParameterInfo& paraminfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
查詢def參數集合中所需參數的零基索引,用於按索引查找。

*帕拉姆福*<br/>
對返回請求的資訊的[CDao 參數 Info](../../mfc/reference/cdaoparameterinfo-structure.md)物件的引用。

*dwInfoOptions*<br/>
指定要檢索的參數的資訊的選項。 此處列出可用選項以及導致函數傳回的內容:

- AFX_DAO_PRIMARY_INFO(預設)名稱、類型

*lpsz名稱*<br/>
包含所需參數名稱的字串,用於按名稱查找。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>備註

有關*在參數資訊*中返回的資訊的說明,請參閱[CDao 參數資訊](../../mfc/reference/cdaoparameterinfo-structure.md)結構。 此結構的成員對應於上面*的 dwInfoOptions*下的描述性資訊。

有關相關資訊,請參閱 DAO 説明中的「參數聲明 (SQL)」主題。

## <a name="cdaoquerydefgetparamvalue"></a><a name="getparamvalue"></a>CDaoQueryDef:取得帕拉姆價值

呼叫此成員函數以檢索儲存在查詢def 參數集合中的指定參數的當前值。

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
需要其值的參數的名稱,用於按名稱查找。

*nIndex*<br/>
查詢def參數集合中參數的零基索引,用於按索引查找。 可以通過調用[GetparameterCount](#getparametercount)和[GetparameterInfo](#getparameterinfo)獲取此值。

### <a name="return-value"></a>傳回值

包含參數值的類[COleVariant](../../mfc/reference/colevariant-class.md)的物件。

### <a name="remarks"></a>備註

您可以按名稱或其在集合中的任位位置訪問參數。

有關相關資訊,請參閱 DAO 説明中的「參數聲明 (SQL)」主題。

## <a name="cdaoquerydefgetrecordsaffected"></a><a name="getrecordsaffected"></a>CDaoQueryDef:取得受影響的記錄

調用此成員函數以確定受上次調用[執行](#execute)的影響的記錄數。

```
long GetRecordsAffected();
```

### <a name="return-value"></a>傳回值

受影響的記錄數目。

### <a name="remarks"></a>備註

當級聯更新或刪除生效時,返回的計數不會反映相關表中的更改。

有關相關信息,請參閱 DAO 説明中的主題「記錄受影響的屬性」。

## <a name="cdaoquerydefgetreturnsrecords"></a><a name="getreturnsrecords"></a>CDaoQueryDef:取得退貨記錄

調用此成員函數以確定查詢def是否基於返回記錄的查詢。

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>傳回值

如果查詢def基於返回記錄的查詢,則非零;否則 0。

### <a name="remarks"></a>備註

此成員函數僅用於 SQL 傳遞查詢。 有關 SQL 查詢的詳細資訊,請參閱[執行](#execute)成員函數。 有關使用 SQL 直通查詢的詳細資訊,請參閱[SetReturnRecords](#setreturnsrecords)成員函數。

有關相關信息,請參閱 DAO 説明中的主題"返回記錄屬性」。。

## <a name="cdaoquerydefgetsql"></a><a name="getsql"></a>CDaoQueryDef:取得SQL

調用此成員函數以檢索定義查詢def所基於的查詢的 SQL 語句。

```
CString GetSQL();
```

### <a name="return-value"></a>傳回值

定義查詢def所基於的查詢的 SQL 語句。

### <a name="remarks"></a>備註

然後,您可能會解析關鍵字、表名等的字串。

有關相關資訊,請參閱 DAO 説明中的「SQL 屬性」、「Microsoft Jet 資料庫引擎 SQL 和 ANSI SQL 的比較」和「使用代碼中的 SQL 查詢資料庫」的主題。

## <a name="cdaoquerydefgettype"></a><a name="gettype"></a>CDaoQueryDef:取得類型

調用此成員函數以確定查詢def的查詢類型。

```
short GetType();
```

### <a name="return-value"></a>傳回值

查詢定義中的查詢類型。 有關值,請參閱備註。

### <a name="remarks"></a>備註

查詢類型由創建查詢def或調用現有查詢def的[SetSQL](#setsql)成員函數時在查詢def的 SQL 字串中指定的內容設置。 此函數傳回的查詢類型可以是以下值之一:

- `dbQSelect`選擇

- `dbQAction` 動作

- `dbQCrosstab`交叉選項卡

- `dbQDelete`刪除

- `dbQUpdate` Update

- `dbQAppend`附加

- `dbQMakeTable`製作台

- `dbQDDL`資料定義

- `dbQSQLPassThrough`直通

- `dbQSetOperation`聯盟

- `dbQSPTBulk``dbQSQLPassThrough`用於指定不返回記錄的查詢。

> [!NOTE]
> 要創建 SQL 傳遞查詢,請`dbSQLPassThrough`不要設置 常量。 當您創建查詢def物件並設置連接字串時,Microsoft Jet 資料庫引擎會自動設置此設置。

有關 SQL 字串的資訊,請參閱[GetSQL](#getsql)。 有關查詢類型的資訊,請參閱[執行](#execute)。

## <a name="cdaoquerydefisopen"></a><a name="isopen"></a>CDaoQueryDef:是開放的

調用此成員函數以確定`CDaoQueryDef`物件當前是否打開。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果物件當前處於`CDaoQueryDef`打開狀態,則非零;否則 0。

### <a name="remarks"></a>備註

在使用 querydef 呼叫[Execute](#execute)或建立[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件之前,查詢def必須處於打開狀態。 將查詢def放入打開狀態呼叫["創建](#create)"(對於新查詢def)或[Open(](#open)對於現有查詢def)。

## <a name="cdaoquerydefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoQueryDef:m_pDatabase

包含指向與查詢def物件關聯的[CDao資料庫](../../mfc/reference/cdaodatabase-class.md)物件的指標。

### <a name="remarks"></a>備註

如果需要直接訪問資料庫,請使用此指標,例如,獲取指向資料庫集合中其他查詢def或記錄集物件的指標。

## <a name="cdaoquerydefm_pdaoquerydef"></a><a name="m_pdaoquerydef"></a>CDaoQueryDef:m_pDAOQueryDef

包含指向基礎 DAO 查詢def 物件的 OLE 介面的指標。

### <a name="remarks"></a>備註

此指標提供是為了與其他類保持完整和一致。 但是,由於 MFC 相當完全封裝 DAO 查詢defs,因此不太可能需要它。 如果確實使用它,請謹慎操作,特別是,除非您知道自己在做什麼,否則不要更改指標的值。

## <a name="cdaoquerydefopen"></a><a name="open"></a>CDaoQueryDef:開啟

呼叫此成員函數以打開以前儲存在資料庫的 QueryDefs 集合中的查詢def。

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
包含要開啟的已儲存查詢def的名稱的字串。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>備註

查詢def開啟後,可以呼叫其[執行](#execute)成員函數或使用查詢def創建[CDaoRecordset 物件](../../mfc/reference/cdaorecordset-class.md)。

## <a name="cdaoquerydefsetconnect"></a><a name="setconnect"></a>CDaoQueryDef:設定連線

呼叫此成員函數以設定查詢def物件的連接字串。

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>參數

*lpszConnect*<br/>
包含關聯[CDao 資料庫](../../mfc/reference/cdaodatabase-class.md)物件的連接字串的字串。

### <a name="remarks"></a>備註

連接字串用於根據需要將其他資訊傳遞給 ODBC 和某些 ISAM 驅動程式。 它不用於微軟噴氣式飛機 (。MDB)資料庫。

> [!TIP]
> 使用 ODBC 表的偏好選擇方法是將它們附加到 。MDB 資料庫。

在執行表示對 ODBC 資料來源的 SQL 傳遞查詢的查詢def之前,請設定連接`SetConnect`字串並調用[SetReturnRecords](#setreturnsrecords)以指定查詢是否返回記錄。

有關連接字串結構和連接字串元件範例的詳細資訊,請參閱 DAO 説明中的主題"連接屬性"。

## <a name="cdaoquerydefsetname"></a><a name="setname"></a>CDaoQueryDef:set 名稱

如果要更改不臨時的查詢def的名稱,請調用此成員函數。

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
包含關聯[CDao 資料庫](../../mfc/reference/cdaodatabase-class.md)物件中非臨時查詢的新名稱的字串。

### <a name="remarks"></a>備註

查詢def名稱是唯一的、使用者定義的名稱。 您可以在將查詢`SetName`def物件追加到查詢Defs集合之前進行呼叫。

## <a name="cdaoquerydefsetodbctimeout"></a><a name="setodbctimeout"></a>CDaoQueryDef:設定ODBC時間

調用此成員函數以在對 ODBC 數據源的查詢超時之前設置時間限制。

```
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>參數

*nODBC逾時*<br/>
查詢逾時之前的秒數。

### <a name="remarks"></a>備註

此成員函數允許您在連接的數據源"超時"的後續操作之前覆蓋預設秒數。 操作可能會由於網路訪問問題、查詢處理時間過長等原因而超時。 如果要`SetODBCTimeout`更改查詢超時值,請在此查詢def執行查詢之前調用。 (當 ODBC 重用連接時,同一連接上的所有用戶端的超時值都相同。

查詢超時的預設值為60秒。

## <a name="cdaoquerydefsetparamvalue"></a><a name="setparamvalue"></a>CDaoQueryDef:setParam值

調用此成員函數以在運行時在查詢def中設置參數的值。

```
virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
要設置其值的參數的名稱。

*varValue*<br/>
要設置的值;請參閱備註。

*nIndex*<br/>
參數在查詢def的參數集合中的設置位置。 可以通過調用[GetparameterCount](#getparametercount)和[GetparameterInfo](#getparameterinfo)獲取此值。

### <a name="remarks"></a>備註

參數必須已作為查詢def SQL 字串的一部分建立。 您可以按名稱或其在集合中的任位位置訪問參數。

指定要設定為`COleVariant`物件的值。 有關物件`COleVariant`在物件中設定所需值和類型的資訊,請參閱類[COleVariant](../../mfc/reference/colevariant-class.md)。

## <a name="cdaoquerydefsetreturnsrecords"></a><a name="setreturnsrecords"></a>CDao查詢Def:設定傳回記錄

調用此成員函數,作為將 SQL 傳遞查詢設置為外部資料庫的過程的一部分。

```
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>參數

*b 回記錄*<br/>
如果外部資料庫上的查詢返回記錄,則傳遞 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

在這種情況下,必須創建查詢def並使用其他成員`CDaoQueryDef`函數設置其屬性。 有關外部資料庫的說明,請參閱[SetConnect](#setconnect)。

## <a name="cdaoquerydefsetsql"></a><a name="setsql"></a>CDao查詢Def:SetSQL

呼叫此成員函數以設定查詢def執行的 SQL 語句。

```
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>參數

*lpszSQL*<br/>
包含完整 SQL 語句的字串,適合執行。 此字串的語法取決於查詢所針對的 DBMS。 有關 Microsoft Jet 資料庫引擎中使用的語法的討論,請參閱 DAO 説明中的主題「在代碼中構建 SQL 語句」。。

### <a name="remarks"></a>備註

的典型用途`SetSQL`是設置查詢def物件以用於 SQL 傳遞查詢。 (有關目標 DBMS 上的 SQL 傳遞查詢的語法,請參閱 DBMS 的文檔。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoException 類別](../../mfc/reference/cdaoexception-class.md)
