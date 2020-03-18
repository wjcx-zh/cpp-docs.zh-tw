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
ms.openlocfilehash: 08fb2909a4fd2e5bda3dfc63d19224a515c7c699
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418794"
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
|[CDaoQueryDef::CDaoQueryDef](#cdaoquerydef)|建構 `CDaoQueryDef` 物件。 下一次呼叫 `Open` 或 `Create`，視您的需求而定。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDaoQueryDef：： Append](#append)|將 querydef 附加至資料庫的 QueryDefs 集合，做為已儲存的查詢。|
|[CDaoQueryDef::CanUpdate](#canupdate)|如果查詢可以更新資料庫，則傳回非零。|
|[CDaoQueryDef：： Close](#close)|關閉 querydef 物件。 當您C++完成時終結物件。|
|[CDaoQueryDef：： Create](#create)|建立基礎 DAO querydef 物件。 使用 querydef 做為暫存查詢，或呼叫 `Append` 將它儲存在資料庫中。|
|[CDaoQueryDef：： Execute](#execute)|執行 querydef 物件所定義的查詢。|
|[CDaoQueryDef：： GetConnect](#getconnect)|傳回與 querydef 相關聯的連接字串。 連接字串會識別資料來源。 （僅適用于 SQL 傳遞查詢，否則為空字串）。|
|[CDaoQueryDef::GetDateCreated](#getdatecreated)|傳回已儲存之查詢的建立日期。|
|[CDaoQueryDef::GetDateLastUpdated](#getdatelastupdated)|傳回上次更新已儲存查詢的日期。|
|[CDaoQueryDef::GetFieldCount](#getfieldcount)|傳回 querydef 所定義的欄位數目。|
|[CDaoQueryDef：： Issomapper.getfieldinfo](#getfieldinfo)|傳回查詢中所定義之指定欄位的相關資訊。|
|[CDaoQueryDef：： GetName](#getname)|傳回 querydef 的名稱。|
|[CDaoQueryDef::GetODBCTimeout](#getodbctimeout)|當執行 querydef 時，傳回 ODBC （適用于 ODBC 查詢）所使用的超時值。 這會決定要讓查詢的動作完成的時間長度。|
|[CDaoQueryDef：： GetParameterCount](#getparametercount)|傳回針對查詢定義的參數數目。|
|[CDaoQueryDef：： GetParameterInfo](#getparameterinfo)|傳回指定參數與查詢的相關資訊。|
|[CDaoQueryDef::GetParamValue](#getparamvalue)|將指定之參數的值傳回給查詢。|
|[CDaoQueryDef::GetRecordsAffected](#getrecordsaffected)|傳回受動作查詢影響的記錄數目。|
|[CDaoQueryDef::GetReturnsRecords](#getreturnsrecords)|如果 querydef 所定義的查詢傳回記錄，則傳回非零。|
|[CDaoQueryDef::GetSQL](#getsql)|傳回指定 querydef 所定義之查詢的 SQL 字串。|
|[CDaoQueryDef：： GetType](#gettype)|傳回查詢類型： delete、update、append、make 資料表等等。|
|[CDaoQueryDef：： IsOpen](#isopen)|如果 querydef 已開啟且可執行，則傳回非零。|
|[CDaoQueryDef：： Open](#open)|開啟儲存在資料庫 QueryDefs 集合中的現有 querydef。|
|[CDaoQueryDef::SetConnect](#setconnect)|針對 ODBC 資料來源上的 SQL 傳遞查詢設定連接字串。|
|[CDaoQueryDef：： SetName](#setname)|設定已儲存查詢的名稱，取代建立 querydef 時使用的名稱。|
|[CDaoQueryDef::SetODBCTimeout](#setodbctimeout)|設定在執行 querydef 時，ODBC （適用于 ODBC 查詢）所使用的超時值。|
|[CDaoQueryDef::SetParamValue](#setparamvalue)|將指定之參數的值設定為查詢。|
|[CDaoQueryDef::SetReturnsRecords](#setreturnsrecords)|指定 querydef 是否傳回記錄。 將此屬性設定為 TRUE 只對 SQL 傳遞查詢有效。|
|[CDaoQueryDef::SetSQL](#setsql)|設定 SQL 字串，指定 querydef 所定義的查詢。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDaoQueryDef：： m_pDAOQueryDef](#m_pdaoquerydef)|基礎 DAO querydef 物件之 OLE 介面的指標。|
|[CDaoQueryDef：： m_pDatabase](#m_pdatabase)|與 querydef 相關聯之 `CDaoDatabase` 物件的指標。 Querydef 可能會儲存在資料庫中。|

## <a name="remarks"></a>備註

Querydef 是一個資料存取物件，其中包含描述查詢的 SQL 語句及其屬性，例如「建立日期」和「ODBC 超時」。 您也可以建立暫存的 querydef 物件，而不儲存它們，但它很方便，而且更有效率，可將經常重複使用的查詢儲存在資料庫中。 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件會維護名為 QueryDefs 集合的集合，其中包含已儲存的 QueryDefs。

> [!NOTE]
>  DAO 資料庫類別與以開放式資料庫連接（ODBC）為基礎的 MFC 資料庫類別不同。 所有的 DAO 資料庫類別名稱都具有 "CDao" 前置詞。 您仍然可以使用 DAO 類別來存取 ODBC 資料來源。 一般而言，以 DAO 為基礎的 MFC 類別比以 ODBC 為基礎的 MFC 類別更有能力;以 DAO 為基礎的類別可以透過自己的資料庫引擎來存取資料，包括透過 ODBC 驅動程式。 以 DAO 為基礎的類別也支援資料定義語言（DDL）作業，例如透過類別加入資料表，而不需要直接呼叫 DAO。

## <a name="usage"></a>使用方式

使用 querydef 物件來處理現有已儲存的查詢，或建立新儲存的查詢或暫存查詢：

1. 在所有情況下，請先建立一個 `CDaoQueryDef` 物件，並提供該查詢所屬[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件的指標。

1. 然後根據您的需要執行下列動作：

   - 若要使用現有已儲存的查詢，請呼叫 querydef 物件的[Open](#open)成員函式，並提供已儲存查詢的名稱。

   - 若要建立新儲存的查詢，請呼叫 querydef 物件的[create](#create)成員函式，並提供查詢的名稱。 然後呼叫[Append](#append)來儲存查詢，方法是將它附加至資料庫的 QueryDefs 集合。 `Create` 將 querydef 置於開啟狀態，所以在呼叫 `Create` 之後，您就不會呼叫 `Open`。

   - 若要建立暫存的 querydef，請呼叫 `Create`。 針對查詢名稱傳遞空字串。 請不要呼叫 `Append`。

當您使用 querydef 物件完成時，請呼叫它的[Close](#close)成員函式;然後終結 querydef 物件。

> [!TIP]
>  建立已儲存的查詢最簡單的方式，就是建立它們，並使用 Microsoft Access 將其儲存在您的資料庫中。 然後您可以在 MFC 程式碼中開啟並使用它們。

## <a name="purposes"></a>用途

您可以將 querydef 物件用於下列任何一種用途：

- 建立 `CDaoRecordset` 物件

- 呼叫物件的 `Execute` 成員函式，直接執行動作查詢或 SQL 傳遞查詢

您可以將 querydef 物件用於任何類型的查詢，包括 select、action、交叉分析、刪除、更新、附加、建立資料表、資料定義、SQL 傳遞、等位和大量查詢。 查詢的類型取決於您提供的 SQL 語句內容。 如需查詢類型的詳細資訊，請參閱 `Execute` 和[GetType](#gettype)成員函式。 記錄集通常用於資料列傳回查詢，通常是使用**SELECT .。。FROM**關鍵字。 `Execute` 最常用於大量作業。 如需詳細資訊，請參閱[Execute](#execute) and [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

## <a name="querydefs-and-recordsets"></a>Querydefs 和記錄集

若要使用 querydef 物件來建立 `CDaoRecordset` 物件，您通常會如上面所述建立或開啟 querydef。 然後在呼叫[CDaoRecordset：： Open](../../mfc/reference/cdaorecordset-class.md#open)時，建立記錄集物件，並將指標傳遞至您的 querydef 物件。 您傳遞的 querydef 必須處於開啟狀態。 如需詳細資訊，請參閱類別[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

您無法使用 querydef 來建立記錄集（最常見的 querydef 用法），除非它處於開啟狀態。 藉由呼叫 `Open` 或 `Create`，讓 querydef 進入開啟狀態。

## <a name="external-databases"></a>外部資料庫

使用外部資料庫引擎的原生 SQL 方言時，我們慣用的是 Querydef 物件。 例如，您可以建立 Transact-SQL 查詢（在 Microsoft SQL Server 上使用），並將它儲存在 querydef 物件中。 當您需要使用不是以 Microsoft Jet 資料庫引擎為基礎的 SQL 查詢時，您必須提供指向外部資料源的連接字串。 具有有效連接字串的查詢會略過資料庫引擎，並將查詢直接傳遞到外部資料庫伺服器進行處理。

> [!TIP]
>  使用 ODBC 資料表的慣用方式，是將它們附加至 Microsoft Jet （。MDB）資料庫。

如需相關資訊，請參閱 DAO SDK 中的「QueryDef 物件」、「QueryDefs 集合」和「CdbDatabase 物件」主題。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDaoQueryDef`

## <a name="requirements"></a>需求

**標頭：** afxdao。h

##  <a name="append"></a>CDaoQueryDef：： Append

呼叫[create](#create)來建立新的 querydef 物件之後，請呼叫此成員函式。

```
virtual void Append();
```

### <a name="remarks"></a>備註

`Append` 會藉由將物件附加至資料庫的 QueryDefs 集合，將 querydef 儲存在資料庫中。 您可以將 querydef 當做暫存物件使用，而不需附加它，但如果您想要保存，您必須呼叫 `Append`。

如果您嘗試附加暫存的 querydef 物件，MFC 會擲回[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的例外狀況。

##  <a name="canupdate"></a>CDaoQueryDef::CanUpdate

呼叫這個成員函式來判斷您是否可以修改 querydef，例如變更其名稱或 SQL 字串。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>傳回值

如果您允許修改 querydef，則為非零值。否則為0。

### <a name="remarks"></a>備註

若有下列情況，您可以修改 querydef：

- 它不是以唯讀狀態的資料庫為基礎。

- 您擁有資料庫的 [更新] 許可權。

   這取決於您是否已執行安全性功能。 MFC 不提供安全性的支援;您必須藉由直接呼叫 DAO 或使用 Microsoft Access，自行執行。 請參閱 DAO 說明中的「許可權屬性」主題。

##  <a name="cdaoquerydef"></a>CDaoQueryDef::CDaoQueryDef

建構 `CDaoQueryDef` 物件。

```
CDaoQueryDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>參數

*pDatabase*<br/>
開啟的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件的指標。

### <a name="remarks"></a>備註

物件可以代表儲存在資料庫 QueryDefs 集合中的現有 querydef、要儲存在集合中的新查詢，或不儲存的暫存查詢。 下一步取決於 querydef 的類型：

- 如果物件代表現有的 querydef，請呼叫物件的[Open](#open)成員函式將它初始化。

- 如果物件代表要儲存的新 querydef，請呼叫物件的[Create](#create)成員函式。 這會將物件加入至資料庫的 QueryDefs 集合。 然後呼叫 `CDaoQueryDef` 成員函式，以設定物件的屬性。 最後，呼叫[Append](#append)。

- 如果物件代表暫存的 querydef （而不是儲存在資料庫中），請呼叫 `Create`，為查詢的名稱傳遞空字串。 呼叫 `Create`之後，直接設定其屬性來初始化 querydef。 請不要呼叫 `Append`。

若要設定 querydef 的屬性，您可以使用[SetName](#setname)、 [SetSQL](#setsql)、 [SetConnect](#setconnect)、 [SetODBCTimeout](#setodbctimeout)和[SetReturnsRecords](#setreturnsrecords)成員函式。

當您使用 querydef 物件完成時，請呼叫它的[Close](#close)成員函式。 如果您有 querydef 的指標，請使用**delete**運算子來摧毀C++物件。

##  <a name="close"></a>CDaoQueryDef：： Close

當您使用 querydef 物件完成時，請呼叫這個成員函式。

```
virtual void Close();
```

### <a name="remarks"></a>備註

關閉 querydef 會釋放基礎 DAO 物件，但不會損毀已儲存的 DAO querydef 物件C++或 `CDaoQueryDef` 物件。 這不同于[CDaoDatabase：:D eletequerydef](../../mfc/reference/cdaodatabase-class.md#deletequerydef)，它會從 DAO 中的資料庫 QueryDefs 集合中刪除 querydef （如果不是暫存的 querydef）。

##  <a name="create"></a>CDaoQueryDef：： Create

呼叫這個成員函式，以建立新儲存的查詢或新的暫存查詢。

```
virtual void Create(
    LPCTSTR lpszName = NULL,
    LPCTSTR lpszSQL = NULL);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
儲存在資料庫中之查詢的唯一名稱。 如需有關字串的詳細資訊，請參閱 DAO 說明中的「CreateQueryDef 方法」主題。 如果您接受預設值（空字串），則會建立暫存的 querydef。 這類查詢不會儲存在 QueryDefs 集合中。

*lpszSQL*<br/>
定義查詢的 SQL 字串。 如果您接受預設值 Null，您之後必須呼叫[SetSQL](#setsql)來設定字串。 在那之前，查詢是未定義的。 不過，您可以使用未定義的查詢來開啟記錄集;如需詳細資訊，請參閱備註。 您必須先定義 SQL 語句，才能將 querydef 附加至 QueryDefs 集合。

### <a name="remarks"></a>備註

如果您在*lpszName*中傳遞名稱，則可以呼叫[Append](#append) ，將 querydef 儲存在資料庫的 QueryDefs 集合中。 否則，物件是暫時的 querydef，而且不會儲存。 不論是哪一種情況，querydef 都處於開啟狀態，您可以使用它來建立[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件或呼叫 Querydef 的[Execute](#execute)成員函式。

如果您未在*lpszSQL*中提供 SQL 語句，則無法使用 `Execute` 執行查詢，但您可以使用它來建立記錄集。 在此情況下，MFC 會使用記錄集的預設 SQL 語句。

##  <a name="execute"></a>CDaoQueryDef：： Execute

呼叫這個成員函式以執行 querydef 物件所定義的查詢。

```
virtual void Execute(int nOptions = dbFailOnError);
```

### <a name="parameters"></a>參數

*nOptions*<br/>
決定查詢特性的整數。 如需相關資訊，請參閱 DAO 說明中的「執行方法」主題。 您可以使用位 OR 運算子（ **&#124;** ），將下列常數與此引數結合：

- `dbDenyWrite` 拒絕其他使用者的寫入權限。

- `dbInconsistent` 不一致的更新。

- `dbConsistent` 一致的更新。

- `dbSQLPassThrough` SQL 傳遞。 使 SQL 語句傳遞至 ODBC 資料庫以進行處理。

- `dbFailOnError` 預設值。 如果發生錯誤，則復原更新，並向使用者報告錯誤。

- 如果另一位使用者正在變更您正在編輯的資料，`dbSeeChanges` 會產生執行階段錯誤。

> [!NOTE]
>  如需「不一致」和「一致」詞彙的說明，請參閱 DAO [說明] 中的「執行方法」主題。

### <a name="remarks"></a>備註

以這種方式用於執行的 Querydef 物件，只能代表下列其中一種查詢類型：

- 動作查詢

- SQL 傳遞查詢

`Execute` 不適用於傳回記錄的查詢，例如 select 查詢。 `Execute` 通常用於大量作業查詢，例如**UPDATE**、 **INSERT**或**SELECT INTO**，或用於資料定義語言（DDL）作業。

> [!TIP]
>  使用 ODBC 資料來源的慣用方法是將資料表附加至 Microsoft Jet （。MDB）資料庫。 如需詳細資訊，請參閱 DAO 說明中的「使用 DAO 存取外部資料庫」主題。

呼叫 querydef 物件的[GetRecordsAffected](#getrecordsaffected)成員函式，以判斷受最近 `Execute` 呼叫影響的記錄數目。 例如，`GetRecordsAffected` 會傳回執行動作查詢時，刪除、更新或插入之記錄數目的相關資訊。 當串聯更新或刪除作用中時，傳回的計數不會反映相關資料表中的變更。

如果您同時包含 `dbInconsistent` 和 `dbConsistent`，或是不包含，則結果會是預設值 `dbInconsistent`。

`Execute` 不會傳回記錄集。 在選取記錄的查詢上使用 `Execute`，會導致 MFC 擲回[CDaoException](../../mfc/reference/cdaoexception-class.md)類型的例外狀況。

##  <a name="getconnect"></a>CDaoQueryDef：： GetConnect

呼叫這個成員函式，以取得與 querydef 資料來源相關聯的連接字串。

```
CString GetConnect();
```

### <a name="return-value"></a>傳回值

[CString](../../atl-mfc-shared/reference/cstringt-class.md) ，其中包含 querydef 的連接字串。

### <a name="remarks"></a>備註

此函數僅適用于 ODBC 資料來源和特定的 ISAM 驅動程式。 它不會與 Microsoft Jet （一起使用。MDB）資料庫;在此情況下，`GetConnect` 會傳回空字串。 如需詳細資訊，請參閱[SetConnect](#setconnect)。

> [!TIP]
>  使用 ODBC 資料表的慣用方式，是將它們附加至。MDB 資料庫。 如需詳細資訊，請參閱 DAO 說明中的「使用 DAO 存取外部資料庫」主題。

如需連接字串的詳細資訊，請參閱 DAO [說明] 中的 [連接屬性] 主題。

##  <a name="getdatecreated"></a>CDaoQueryDef::GetDateCreated

呼叫這個成員函式以取得建立 querydef 物件的日期。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>傳回值

[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，其中包含建立 querydef 的日期和時間。

### <a name="remarks"></a>備註

如需相關資訊，請參閱 DAO 說明中的「DateCreated，LastUpdated 屬性」主題。

##  <a name="getdatelastupdated"></a>CDaoQueryDef::GetDateLastUpdated

呼叫這個成員函式，以取得上一次更新 querydef 物件的日期，其中任何屬性變更時，例如其名稱、其 SQL 字串或其連接字串。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>傳回值

[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)物件，包含上一次更新 querydef 的日期和時間。

### <a name="remarks"></a>備註

如需相關資訊，請參閱 DAO 說明中的「DateCreated，LastUpdated 屬性」主題。

##  <a name="getfieldcount"></a>CDaoQueryDef::GetFieldCount

呼叫這個成員函式可抓取查詢中的欄位數目。

```
short GetFieldCount();
```

### <a name="return-value"></a>傳回值

查詢中定義的欄位數目。

### <a name="remarks"></a>備註

`GetFieldCount` 對於在 querydef 中的所有欄位進行迴圈時很有用。 基於此目的，請使用 `GetFieldCount` 搭配[issomapper.getfieldinfo](#getfieldinfo)。

##  <a name="getfieldinfo"></a>CDaoQueryDef：： Issomapper.getfieldinfo

呼叫這個成員函式可取得有關 querydef 中所定義欄位的各種資訊。

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
在 querydef 的 Fields 集合中，所需欄位以零為起始的索引，用於依索引查閱。

*fieldinfo*<br/>
傳回所要求資訊之 `CDaoFieldInfo` 物件的參考。

*dwInfoOptions*<br/>
指定要抓取之欄位的相關資訊的選項。 這裡列出可用的選項，以及它們會導致函式傳回的內容：

- AFX_DAO_PRIMARY_INFO （預設值）名稱、類型、大小、屬性

- AFX_DAO_SECONDARY_INFO 主要資訊加上：序數位置、必要、允許零長度、來源欄位、外部名稱、來源資料表、排序次序

- AFX_DAO_ALL_INFO 主要和次要資訊，加上：預設值、驗證文字、驗證規則

*lpszName*<br/>
包含所需欄位名稱的字串，用於依名稱查閱。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>備註

如需*fieldinfo*中所傳回信息的描述，請參閱[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。 此結構的成員與上述*dwInfoOptions*底下的描述性資訊相對應。 如果您要求一層資訊，您也可以取得任何先前的資訊層級。

##  <a name="getname"></a>CDaoQueryDef：： GetName

呼叫這個成員函式，以取得 querydef 所表示的查詢名稱。

```
CString GetName();
```

### <a name="return-value"></a>傳回值

查詢的名稱。

### <a name="remarks"></a>備註

[Querydef 名稱] 是唯一的使用者定義名稱。 如需有關 querydef 名稱的詳細資訊，請參閱 DAO 說明中的「名稱屬性」主題。

##  <a name="getodbctimeout"></a>CDaoQueryDef::GetODBCTimeout

呼叫這個成員函式，以在 ODBC 資料來源的查詢超時之前，取得目前的時間限制。

```
short GetODBCTimeout();
```

### <a name="return-value"></a>傳回值

查詢逾時之前的秒數。

### <a name="remarks"></a>備註

如需這項時間限制的詳細資訊，請參閱 DAO 說明中的「ODBCTimeout 屬性」主題。

> [!TIP]
>  使用 ODBC 資料表的慣用方式，是將它們附加至 Microsoft Jet （。MDB）資料庫。 如需詳細資訊，請參閱 DAO 說明中的「使用 DAO 存取外部資料庫」主題。

##  <a name="getparametercount"></a>CDaoQueryDef：： GetParameterCount

呼叫這個成員函式，以取出已儲存查詢中的參數數目。

```
short GetParameterCount();
```

### <a name="return-value"></a>傳回值

在查詢中定義的參數數目。

### <a name="remarks"></a>備註

`GetParameterCount` 對於在 querydef 中的所有參數進行迴圈時很有用。 基於此目的，請使用 `GetParameterCount` 搭配[GetParameterInfo](#getparameterinfo)。

如需相關資訊，請參閱 DAO 說明中的「參數物件」、「參數集合」和「參數宣告（SQL）」主題。

##  <a name="getparameterinfo"></a>CDaoQueryDef：： GetParameterInfo

呼叫這個成員函式，以取得在 querydef 中定義之參數的相關資訊。

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
以零為基底的參數集合中所需參數的索引，用於依索引查閱。

*paraminfo*<br/>
傳回所要求之資訊的[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)物件參考。

*dwInfoOptions*<br/>
指定要抓取之參數相關資訊的選項。 這裡會列出可用的選項，以及它會導致函式傳回的內容：

- AFX_DAO_PRIMARY_INFO （預設）名稱，輸入

*lpszName*<br/>
包含所需參數名稱的字串，用於依名稱查閱。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>備註

如需*paraminfo*中所傳回信息的描述，請參閱[CDaoParameterInfo](../../mfc/reference/cdaoparameterinfo-structure.md)結構。 此結構的成員與上述*dwInfoOptions*底下的描述性資訊相對應。

如需相關資訊，請參閱 DAO 說明中的「參數聲明（SQL）」主題。

##  <a name="getparamvalue"></a>CDaoQueryDef::GetParamValue

呼叫這個成員函式，以抓取在 querydef 的 Parameters 集合中所儲存之指定參數的目前值。

```
virtual COleVariant GetParamValue(LPCTSTR lpszName);
virtual COleVariant GetParamValue(int nIndex);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
您需要其值的參數名稱，用於依名稱查閱。

*nIndex*<br/>
在 querydef 的參數集合中，參數以零為起始的索引，用於依索引查閱。 您可以使用[GetParameterCount](#getparametercount)和[GetParameterInfo](#getparameterinfo)的呼叫來取得此值。

### <a name="return-value"></a>傳回值

[COleVariant](../../mfc/reference/colevariant-class.md)類別的物件，其中包含參數的值。

### <a name="remarks"></a>備註

您可以依名稱或其在集合中的序數位置來存取參數。

如需相關資訊，請參閱 DAO 說明中的「參數聲明（SQL）」主題。

##  <a name="getrecordsaffected"></a>CDaoQueryDef::GetRecordsAffected

呼叫這個成員函式，以判斷上次呼叫[執行](#execute)時所影響的記錄數目。

```
long GetRecordsAffected();
```

### <a name="return-value"></a>傳回值

受影響的記錄數目。

### <a name="remarks"></a>備註

當串聯更新或刪除作用中時，傳回的計數不會反映相關資料表中的變更。

如需相關資訊，請參閱 DAO 說明中的「RecordsAffected 屬性」主題。

##  <a name="getreturnsrecords"></a>CDaoQueryDef::GetReturnsRecords

呼叫這個成員函式，以判斷 querydef 是否以傳回記錄的查詢為基礎。

```
BOOL GetReturnsRecords();
```

### <a name="return-value"></a>傳回值

如果 querydef 是以傳回記錄的查詢為基礎，則為非零。否則為0。

### <a name="remarks"></a>備註

此成員函式僅用於 SQL 傳遞查詢。 如需 SQL 查詢的詳細資訊，請參閱[Execute](#execute)成員函式。 如需使用 SQL 傳遞查詢的詳細資訊，請參閱[SetReturnsRecords](#setreturnsrecords)成員函式。

如需相關資訊，請參閱 DAO 說明中的「ReturnsRecords 屬性」主題。

##  <a name="getsql"></a>CDaoQueryDef::GetSQL

呼叫這個成員函式來抓取 SQL 語句，以定義 querydef 所依據的查詢。

```
CString GetSQL();
```

### <a name="return-value"></a>傳回值

定義 querydef 所依據之查詢的 SQL 語句。

### <a name="remarks"></a>備註

接著，您可能會剖析關鍵字、資料表名稱等等的字串。

如需相關資訊，請參閱 DAO 說明中的「SQL 屬性」、「Microsoft Jet 資料庫引擎 SQL 和 ANSI SQL 的比較」和「以程式碼查詢資料庫」主題。

##  <a name="gettype"></a>CDaoQueryDef：： GetType

呼叫這個成員函式，以判斷 querydef 的查詢類型。

```
short GetType();
```

### <a name="return-value"></a>傳回值

Querydef 所定義之查詢的類型。 如需值，請參閱備註。

### <a name="remarks"></a>備註

當您建立 querydef 或呼叫現有的 querydef [SetSQL](#setsql)成員函式時，會使用您在 QUERYDEF 的 SQL 字串中指定的內容來設定查詢類型。 這個函數所傳回的查詢類型可以是下列其中一個值：

- `dbQSelect` 選取

- `dbQAction` 動作

- `dbQCrosstab` 交叉資料表

- `dbQDelete` 刪除

- `dbQUpdate` Update

- `dbQAppend` 附加

- `dbQMakeTable` 製作資料表

- `dbQDDL` 資料定義

- `dbQSQLPassThrough` 傳遞

- `dbQSetOperation` 聯集

- `dbQSPTBulk` 搭配 `dbQSQLPassThrough` 使用，以指定不會傳回記錄的查詢。

> [!NOTE]
>  若要建立 SQL 傳遞查詢，請不要設定 `dbSQLPassThrough` 常數。 當您建立 querydef 物件並設定連接字串時，Microsoft Jet 資料庫引擎會自動設定此項。

如需 SQL 字串的詳細資訊，請參閱[GetSQL](#getsql)。 如需查詢類型的詳細資訊，請參閱[Execute](#execute)。

##  <a name="isopen"></a>CDaoQueryDef：： IsOpen

呼叫這個成員函式，以判斷目前是否開啟 `CDaoQueryDef` 物件。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果 `CDaoQueryDef` 物件目前為開啟，則為非零。否則為0。

### <a name="remarks"></a>備註

Querydef 必須處於 [已開啟] 狀態，您才能使用它來呼叫[Execute](#execute)或來建立[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件。 若要將 querydef 放入開啟狀態呼叫，請[建立](#create)（適用于新的 querydef）或[開啟](#open)（適用于現有的 querydef）。

##  <a name="m_pdatabase"></a>CDaoQueryDef：： m_pDatabase

包含與 querydef 物件相關聯之[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件的指標。

### <a name="remarks"></a>備註

如果您需要直接存取資料庫，例如，若要取得資料庫集合中其他 querydef 或 recordset 物件的指標，請使用此指標。

##  <a name="m_pdaoquerydef"></a>CDaoQueryDef：： m_pDAOQueryDef

包含基礎 DAO querydef 物件之 OLE 介面的指標。

### <a name="remarks"></a>備註

這個指標是為了與其他類別的完整性和一致性而提供的。 不過，因為 MFC 會完全封裝 DAO querydefs，所以您不太可能需要它。 如果您使用它，請謹慎進行，特別是不要變更指標的值，除非您知道正在進行的動作。

##  <a name="open"></a>CDaoQueryDef：： Open

呼叫這個成員函式，以開啟先前儲存在資料庫 QueryDefs 集合中的 querydef。

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
字串，包含要開啟之已儲存的 querydef 名稱。 您可以使用[CString](../../atl-mfc-shared/reference/cstringt-class.md)。

### <a name="remarks"></a>備註

當 querydef 開啟之後，您就可以呼叫其[Execute](#execute)成員函式，或使用 querydef 來建立[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件。

##  <a name="setconnect"></a>CDaoQueryDef::SetConnect

呼叫這個成員函式，以設定 querydef 物件的連接字串。

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>參數

*lpszConnect*<br/>
字串，其中包含相關聯[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件的連接字串。

### <a name="remarks"></a>備註

連接字串是用來視需要將其他資訊傳遞至 ODBC 和特定的 ISAM 驅動程式。 它不會用於 Microsoft Jet （。MDB）資料庫。

> [!TIP]
>  使用 ODBC 資料表的慣用方式，是將它們附加至。MDB 資料庫。

在執行代表 ODBC 資料來源之 SQL 傳遞查詢的 querydef 之前，請使用 `SetConnect` 來設定連接字串，並呼叫[SetReturnsRecords](#setreturnsrecords)來指定查詢是否會傳回記錄。

如需連接字串的結構和連接字串元件範例的詳細資訊，請參閱 DAO 說明中的「連接屬性」主題。

##  <a name="setname"></a>CDaoQueryDef：： SetName

如果您想要變更非暫時性的 querydef 名稱，請呼叫這個成員函式。

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
字串，其中包含相關聯[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件中 nontemporary 查詢的新名稱。

### <a name="remarks"></a>備註

Querydef 名稱是唯一的使用者定義名稱。 您可以在將 querydef 物件附加至 QueryDefs 集合之前，呼叫 `SetName`。

##  <a name="setodbctimeout"></a>CDaoQueryDef::SetODBCTimeout

呼叫這個成員函式可在 ODBC 資料來源的查詢超時之前設定時間限制。

```
void SetODBCTimeout(short nODBCTimeout);
```

### <a name="parameters"></a>參數

*nODBCTimeout*<br/>
查詢逾時之前的秒數。

### <a name="remarks"></a>備註

這個成員函式可讓您覆寫連接的資料來源「超時」之前的預設秒數。 作業可能會因為網路存取問題、過多的查詢處理時間等等而超時。 如果您想要變更查詢超時值，請在使用此 querydef 執行查詢之前呼叫 `SetODBCTimeout`。 （當 ODBC 重複使用連接時，相同連接上所有用戶端的超時值都相同）。

查詢超時的預設值為60秒。

##  <a name="setparamvalue"></a>CDaoQueryDef::SetParamValue

呼叫這個成員函式，在執行時間設定 querydef 中的參數值。

```
virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
您想要設定其值的參數名稱。

*varValue*<br/>
要設定的值;請參閱備註。

*nIndex*<br/>
參數在 querydef 參數集合中的序數位置。 您可以使用[GetParameterCount](#getparametercount)和[GetParameterInfo](#getparameterinfo)的呼叫來取得此值。

### <a name="remarks"></a>備註

參數必須已經建立為 querydef 的 SQL 字串的一部分。 您可以依名稱或其在集合中的序數位置來存取參數。

指定要設定為 `COleVariant` 物件的值。 如需有關在 `COleVariant` 物件中設定所需值和類型的詳細資訊，請參閱類別[COleVariant](../../mfc/reference/colevariant-class.md)。

##  <a name="setreturnsrecords"></a>CDaoQueryDef::SetReturnsRecords

在設定 SQL 傳遞查詢至外部資料庫的過程中，呼叫這個成員函式。

```
void SetReturnsRecords(BOOL bReturnsRecords);
```

### <a name="parameters"></a>參數

*bReturnsRecords*<br/>
如果外部資料庫上的查詢傳回記錄，則傳遞 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

在這種情況下，您必須建立 querydef，並使用其他 `CDaoQueryDef` 成員函式來設定其屬性。 如需外部資料庫的說明，請參閱[SetConnect](#setconnect)。

##  <a name="setsql"></a>CDaoQueryDef::SetSQL

呼叫這個成員函式，以設定 querydef 執行的 SQL 語句。

```
void SetSQL(LPCTSTR lpszSQL);
```

### <a name="parameters"></a>參數

*lpszSQL*<br/>
包含完整 SQL 語句的字串，適合執行。 這個字串的語法取決於您的查詢所針對的 DBMS。 如需 Microsoft Jet 資料庫引擎中所使用語法的討論，請參閱 DAO 說明中的「在程式碼中建立 SQL 語句」主題。

### <a name="remarks"></a>備註

`SetSQL` 的典型用法是設定要在 SQL 傳遞查詢中使用的 querydef 物件。 （如需您的目標 DBMS 上的 SQL 傳遞查詢語法，請參閱 DBMS 的檔）。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoTableDef 類別](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoException 類別](../../mfc/reference/cdaoexception-class.md)
