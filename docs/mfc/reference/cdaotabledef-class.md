---
title: CDaoTableDef 類別
ms.date: 11/04/2016
f1_keywords:
- CDaoTableDef
- AFXDAO/CDaoTableDef
- AFXDAO/CDaoTableDef::CDaoTableDef
- AFXDAO/CDaoTableDef::Append
- AFXDAO/CDaoTableDef::CanUpdate
- AFXDAO/CDaoTableDef::Close
- AFXDAO/CDaoTableDef::Create
- AFXDAO/CDaoTableDef::CreateField
- AFXDAO/CDaoTableDef::CreateIndex
- AFXDAO/CDaoTableDef::DeleteField
- AFXDAO/CDaoTableDef::DeleteIndex
- AFXDAO/CDaoTableDef::GetAttributes
- AFXDAO/CDaoTableDef::GetConnect
- AFXDAO/CDaoTableDef::GetDateCreated
- AFXDAO/CDaoTableDef::GetDateLastUpdated
- AFXDAO/CDaoTableDef::GetFieldCount
- AFXDAO/CDaoTableDef::GetFieldInfo
- AFXDAO/CDaoTableDef::GetIndexCount
- AFXDAO/CDaoTableDef::GetIndexInfo
- AFXDAO/CDaoTableDef::GetName
- AFXDAO/CDaoTableDef::GetRecordCount
- AFXDAO/CDaoTableDef::GetSourceTableName
- AFXDAO/CDaoTableDef::GetValidationRule
- AFXDAO/CDaoTableDef::GetValidationText
- AFXDAO/CDaoTableDef::IsOpen
- AFXDAO/CDaoTableDef::Open
- AFXDAO/CDaoTableDef::RefreshLink
- AFXDAO/CDaoTableDef::SetAttributes
- AFXDAO/CDaoTableDef::SetConnect
- AFXDAO/CDaoTableDef::SetName
- AFXDAO/CDaoTableDef::SetSourceTableName
- AFXDAO/CDaoTableDef::SetValidationRule
- AFXDAO/CDaoTableDef::SetValidationText
- AFXDAO/CDaoTableDef::m_pDAOTableDef
- AFXDAO/CDaoTableDef::m_pDatabase
helpviewer_keywords:
- CDaoTableDef [MFC], CDaoTableDef
- CDaoTableDef [MFC], Append
- CDaoTableDef [MFC], CanUpdate
- CDaoTableDef [MFC], Close
- CDaoTableDef [MFC], Create
- CDaoTableDef [MFC], CreateField
- CDaoTableDef [MFC], CreateIndex
- CDaoTableDef [MFC], DeleteField
- CDaoTableDef [MFC], DeleteIndex
- CDaoTableDef [MFC], GetAttributes
- CDaoTableDef [MFC], GetConnect
- CDaoTableDef [MFC], GetDateCreated
- CDaoTableDef [MFC], GetDateLastUpdated
- CDaoTableDef [MFC], GetFieldCount
- CDaoTableDef [MFC], GetFieldInfo
- CDaoTableDef [MFC], GetIndexCount
- CDaoTableDef [MFC], GetIndexInfo
- CDaoTableDef [MFC], GetName
- CDaoTableDef [MFC], GetRecordCount
- CDaoTableDef [MFC], GetSourceTableName
- CDaoTableDef [MFC], GetValidationRule
- CDaoTableDef [MFC], GetValidationText
- CDaoTableDef [MFC], IsOpen
- CDaoTableDef [MFC], Open
- CDaoTableDef [MFC], RefreshLink
- CDaoTableDef [MFC], SetAttributes
- CDaoTableDef [MFC], SetConnect
- CDaoTableDef [MFC], SetName
- CDaoTableDef [MFC], SetSourceTableName
- CDaoTableDef [MFC], SetValidationRule
- CDaoTableDef [MFC], SetValidationText
- CDaoTableDef [MFC], m_pDAOTableDef
- CDaoTableDef [MFC], m_pDatabase
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
ms.openlocfilehash: 61e16ef2998f2b807e96368973711dfdb31dcc45
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223118"
---
# <a name="cdaotabledef-class"></a>CDaoTableDef 類別

表示儲存的基底資料表或附加資料表定義。

## <a name="syntax"></a>語法

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|Name|說明|
|----------|-----------------|
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|建構 `CDaoTableDef` 物件。|

### <a name="public-methods"></a>公用方法

|Name|說明|
|----------|-----------------|
|[CDaoTableDef：： Append](#append)|將新的資料表加入至資料庫。|
|[CDaoTableDef::CanUpdate](#canupdate)|如果可以更新資料表，則傳回非零（您可以修改欄位或資料表屬性的定義）。|
|[CDaoTableDef：： Close](#close)|關閉開啟的 tabledef。|
|[CDaoTableDef：： Create](#create)|建立可使用[Append](#append)新增至資料庫的資料表。|
|[CDaoTableDef::CreateField](#createfield)|呼叫以建立資料表的欄位。|
|[CDaoTableDef：： CreateIndex](#createindex)|呼叫以建立資料表的索引。|
|[CDaoTableDef：:D eleteField](#deletefield)|呼叫以從資料表中刪除欄位。|
|[CDaoTableDef：:D eleteIndex](#deleteindex)|呼叫以從資料表中刪除索引。|
|[CDaoTableDef：： GetAttributes](#getattributes)|傳回值，指出物件的一或多個特性 `CDaoTableDef` 。|
|[CDaoTableDef：： GetConnect](#getconnect)|傳回值，提供資料表來源的相關資訊。|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|傳回建立物件基礎資料表的日期和時間 `CDaoTableDef` 。|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|傳回對基表設計進行最近變更的日期和時間。|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|傳回值，表示資料表中的欄位數目。|
|[CDaoTableDef：： Issomapper.getfieldinfo](#getfieldinfo)|傳回資料表中欄位的特定類型資訊。|
|[CDaoTableDef::GetIndexCount](#getindexcount)|傳回資料表的索引數目。|
|[CDaoTableDef：： GetIndexInfo](#getindexinfo)|傳回資料表索引的特定類型資訊。|
|[CDaoTableDef：： GetName](#getname)|傳回資料表的使用者定義名稱。|
|[CDaoTableDef：： GetRecordCount](#getrecordcount)|傳回資料表中的記錄數目。|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|傳回值，指定源資料庫中附加資料表的名稱。|
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|傳回值，這個值會在欄位變更或加入至資料表時，驗證欄位中的資料。|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|傳回值，指定當欄位物件的值不符合指定的驗證規則時，您的應用程式所顯示的訊息文字。|
|[CDaoTableDef：： IsOpen](#isopen)|如果資料表已開啟，則傳回非零。|
|[CDaoTableDef：： Open](#open)|開啟儲存在資料庫 TableDef's 集合中的現有 tabledef。|
|[CDaoTableDef::RefreshLink](#refreshlink)|更新附加資料表的連接資訊。|
|[CDaoTableDef：： SetAttributes](#setattributes)|設定值，指出物件的一或多個特性 `CDaoTableDef` 。|
|[CDaoTableDef::SetConnect](#setconnect)|設定值，提供資料表來源的相關資訊。|
|[CDaoTableDef：： SetName](#setname)|設定資料表的名稱。|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|設定值，指定源資料庫中附加資料表的名稱。|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|設定值，在欄位變更或加入至資料表時，驗證其資料。|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|設定值，指定當欄位物件的值不符合指定的驗證規則時，您的應用程式所顯示的訊息文字。|

### <a name="public-data-members"></a>公用資料成員

|Name|說明|
|----------|-----------------|
|[CDaoTableDef：： m_pDAOTableDef](#m_pdaotabledef)|Tabledef 物件基礎之 DAO 介面的指標。|
|[CDaoTableDef：： m_pDatabase](#m_pdatabase)|此資料表的源資料庫。|

## <a name="remarks"></a>備註

每個 DAO 資料庫物件都會維護一個名為 TableDefs 的集合，其中包含所有已儲存的 DAO tabledef 物件。

您可以使用物件來運算元據表定義 `CDaoTableDef` 。 例如，您可以：

- 檢查資料庫中任何本機、附加或外部資料表的欄位和索引結構。

- 呼叫 `SetConnect` 附加資料表的和成員函式 `SetSourceTableName` ，並使用成員函式 `RefreshLink` 來更新附加資料表的連接。

- 呼叫成員函式 `CanUpdate` ，以判斷您是否可以編輯資料表中的欄位定義。

- 使用 `GetValidationRule` 和和 `SetValidationRule` `GetValidationText` 和成員函式，取得或設定驗證條件 `SetValidationText` 。

- 使用 `Open` 成員函式來建立資料表-、動態集型或快照型別 `CDaoRecordset` 物件。

    > [!NOTE]
    >  DAO 資料庫類別與以開放式資料庫連接（ODBC）為基礎的 MFC 資料庫類別不同。 所有的 DAO 資料庫類別名稱都具有 "CDao" 前置詞。 您仍然可以使用 DAO 類別來存取 ODBC 資料來源。DAO 類別一般提供了絕佳的功能，因為它們是 Microsoft Jet 資料庫引擎特有的。

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>若要使用 tabledef 物件來處理現有的資料表或建立新的資料表

1. 在所有情況下，請先建立 `CDaoTableDef` 物件，並提供指向資料表所屬之[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件的指標。

1. 然後根據您的需要執行下列動作：

   - 若要使用現有已儲存的資料表，請呼叫 tabledef 物件的[Open](#open)成員函式，並提供已儲存資料表的名稱。

   - 若要建立新的資料表，請呼叫 tabledef 物件的[create](#create)成員函式，並提供資料表的名稱。 呼叫[CreateField](#createfield)和[CreateIndex](#createindex) ，將欄位和索引加入至資料表。

   - 呼叫[Append](#append)以儲存資料表，方法是將它附加至資料庫的 TableDefs 集合。 `Create`將 tabledef 置於開啟狀態，因此在呼叫之後， `Create` 您不會呼叫 `Open` 。

        > [!TIP]
        >  建立已儲存的資料表最簡單的方式，就是建立它們，並使用 Microsoft Access 將其儲存在您的資料庫中。 然後您可以在 MFC 程式碼中開啟並使用它們。

若要使用您已開啟或建立的 tabledef 物件，請建立並開啟 `CDaoRecordset` 物件，並在 `dbOpenTable` *nOpenType*參數中指定具有值的 tabledef 名稱。

若要使用 tabledef 物件來建立 `CDaoRecordset` 物件，您通常會如上面所述建立或開啟 tabledef，然後在您呼叫[CDaoRecordset：： open](../../mfc/reference/cdaorecordset-class.md#open)時，將指標傳遞給您的 tabledef 物件，然後再建立記錄集物件。 您傳遞的 tabledef 必須處於開啟狀態。 如需詳細資訊，請參閱類別[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

當您使用 tabledef 物件完成時，請呼叫它的[Close](../../mfc/reference/cdaorecordset-class.md#close)成員函式;然後終結 tabledef 物件。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>需求

**標頭：** afxdao。h

## <a name="cdaotabledefappend"></a><a name="append"></a>CDaoTableDef：： Append

呼叫[create](#create)來建立新的 tabledef 物件以將 tabledef 儲存在資料庫中之後，呼叫這個成員函式。

```
virtual void Append();
```

### <a name="remarks"></a>備註

函式會將物件附加至資料庫的 TableDefs 集合。 您可以使用 tabledef 做為暫存物件，並在定義它時不要附加它，但如果您想要儲存並使用它，則必須呼叫 `Append` 。

> [!NOTE]
> 如果您嘗試附加未命名的 tabledef （包含 null 或空字串），則 MFC 會擲回例外狀況。

如需相關資訊，請參閱 DAO 說明中的「附加方法」主題。

## <a name="cdaotabledefcanupdate"></a><a name="canupdate"></a>CDaoTableDef::CanUpdate

呼叫這個成員函式，以判斷是否可以變更物件基礎的資料表定義 `CDaoTableDef` 。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>傳回值

如果資料表結構（架構）可以修改（加入或刪除欄位和索引），則為非零，否則為0。

### <a name="remarks"></a>備註

根據預設，可以更新物件基礎的新建立資料表 `CDaoTableDef` ，而 `CDaoTableDef` 無法更新物件的基礎附加資料表。 `CDaoTableDef`即使產生的記錄集不是可更新的，物件也可能是可更新的。

如需相關資訊，請參閱 DAO 說明中的「可更新屬性」主題。

## <a name="cdaotabledefcdaotabledef"></a><a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef

建構 `CDaoTableDef` 物件。

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>參數

*pDatabase*<br/>
[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件的指標。

### <a name="remarks"></a>備註

在建立物件之後，您必須呼叫[Create](#create)或[Open](#open)成員函式。 當您完成物件時，您必須呼叫它的[Close](#close)成員函式，並終結 `CDaoTableDef` 物件。

## <a name="cdaotabledefclose"></a><a name="close"></a>CDaoTableDef：： Close

呼叫這個成員函式，以關閉並釋放 tabledef 物件。

```
virtual void Close();
```

### <a name="remarks"></a>備註

通常在呼叫之後 `Close` ，如果 tabledef 物件是以配置，則您會將它刪除 **`new`** 。

呼叫之後，您可以再次呼叫[Open](#open) `Close` 。 這可讓您重複使用 tabledef 物件。

如需相關資訊，請參閱 DAO 說明中的「關閉方法」主題。

## <a name="cdaotabledefcreate"></a><a name="create"></a>CDaoTableDef：： Create

呼叫這個成員函式來建立新儲存的資料表。

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
包含資料表名稱之字串的指標。

*lAttributes*<br/>
對應至 tabledef 物件所代表之資料表特性的值。 您可以使用位 OR 來結合下列任何常數：

|持續性|說明|
|--------------|-----------------|
|`dbAttachExclusive`|對於使用 Microsoft Jet 資料庫引擎的資料庫，表示資料表是已開啟供獨佔使用的附加資料表。|
|`dbAttachSavePWD`|對於使用 Microsoft Jet database engine 的資料庫，表示附加資料表的使用者識別碼和密碼會與連接資訊一併儲存。|
|`dbSystemObject`|表示資料表是 Microsoft Jet 資料庫引擎所提供的系統資料表。|
|`dbHiddenObject`|表示資料表是 Microsoft Jet 資料庫引擎所提供的隱藏資料表。|

*lpszSrcTable*<br/>
包含來源資料表名稱之字串的指標。 根據預設，此值會初始化為 Null。

*lpszConnect*<br/>
包含預設連接字串之字串的指標。 根據預設，此值會初始化為 Null。

### <a name="remarks"></a>備註

命名為 tabledef 之後，您就可以呼叫[Append](#append) ，將 tabledef 儲存在資料庫的 TableDefs 集合中。 呼叫之後 `Append` ，tabledef 會處於開啟狀態，而您可以使用它來建立[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件。

如需相關資訊，請參閱 DAO 說明中的「CreateTableDef 方法」主題。

## <a name="cdaotabledefcreatefield"></a><a name="createfield"></a>CDaoTableDef::CreateField

呼叫這個成員函式，將欄位加入至資料表。

```cpp
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
字串運算式的指標，指定此欄位的名稱。

*nType*<br/>
值，指出欄位的資料類型。 此設定可以是下列其中一個值：

|類型|大小 (位元組)|說明|
|----------|--------------------|-----------------|
|`dbBoolean`|1 個位元組|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|貨幣（ [COleCurrency](../../mfc/reference/colecurrency-class.md)）|
|`dbSingle`|4|FLOAT|
|`dbDouble`|8|double|
|`dbDate`|8|日期/時間（ [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)）|
|`dbText`|1 - 255|文字（ [CString](../../atl-mfc-shared/reference/cstringt-class.md)）|
|`dbLongBinary`|0|長二進位（OLE 物件）、 [CLongBinary](../../mfc/reference/clongbinary-class.md)或[CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|備忘錄（ [CString](../../atl-mfc-shared/reference/cstringt-class.md)）|

*lSize*<br/>
值，指出包含文字之欄位的大小上限（以位元組為單位），或包含文字或數值之欄位的固定大小。 所有文字欄位都會忽略*lSize*參數。

*lAttributes*<br/>
值，對應至欄位的特性，而且可以使用位 OR 結合。

|持續性|說明|
|--------------|-----------------|
|`dbFixedField`|欄位大小是固定的（數值欄位的預設值）。|
|`dbVariableField`|[欄位大小] 為 [變數] （僅限文字欄位）。|
|`dbAutoIncrField`|新記錄的域值會自動遞增為不能變更的唯一長整數。 僅支援 Microsoft Jet 資料庫資料表。|
|`dbUpdatableField`|域值可以變更。|
|`dbDescending`|欄位是以遞減（Z-A 或 100-0）順序排序（僅適用于索引物件的 Fields 集合中的欄位物件）。 如果您省略此常數，則會以遞增（a-z 或 0-100）順序（預設值）排序欄位。|

*fieldinfo*<br/>
[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構的參考。

### <a name="remarks"></a>備註

`DAOField`會建立（ole）物件，並將其附加至 `DAOTableDef` （ole）物件的 Fields 集合。 除了用來檢查物件屬性之外，您也可以使用 `CDaoFieldInfo` 來建立 tabledef 中建立新欄位的輸入參數。 的第一個版本較 `CreateField` 容易使用，但如果您想要更精細的控制，您可以使用第二個版本的 `CreateField` ，它會採用 `CDaoFieldInfo` 參數。

如果您使用 `CreateField` 接受參數的版本 `CDaoFieldInfo` ，您必須仔細設定結構的下列每個成員 `CDaoFieldInfo` ：

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

的其餘成員 `CDaoFieldInfo` 應設定為**0**、FALSE 或空字串（適用于該成員），否則 `CDaoException` 可能會發生。

如需相關資訊，請參閱 DAO 說明中的「CreateField 方法」主題。

## <a name="cdaotabledefcreateindex"></a><a name="createindex"></a>CDaoTableDef：： CreateIndex

呼叫此函式可將索引加入至資料表。

```cpp
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>參數

*indexinfo*<br/>
[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構的參考。

### <a name="remarks"></a>備註

索引會指定從資料庫資料表存取記錄的順序，以及是否接受重複的記錄。 索引也提供有效率的資料存取。

您不需要建立資料表的索引，但是在大型、未編制索引的資料表中，存取特定記錄或建立記錄集可能需要很長的時間。 另一方面，建立太多索引會使更新、附加和刪除作業變慢，因為所有索引都會自動更新。 當您決定要建立哪些索引時，請考慮這些因素。

`CDaoIndexInfo`必須設定下列結構的成員：

- `m_strName`必須提供名稱。

- `m_pFieldInfos`必須指向結構的陣列 `CDaoIndexFieldInfo` 。

- `m_nFields`必須指定結構陣列中的欄位數目 `CDaoFieldInfo` 。

如果設定為 FALSE，則會忽略其餘成員。 此外，在 `m_lDistinctCount` 建立索引時，會忽略該成員。

## <a name="cdaotabledefdeletefield"></a><a name="deletefield"></a>CDaoTableDef：:D eleteField

呼叫此成員函式以移除欄位，並使其無法存取。

```cpp
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
字串運算式的指標，這是現有欄位的名稱。

*nIndex*<br/>
資料表之以零為基底的欄位集合中，用於依索引查閱的欄位索引。

### <a name="remarks"></a>備註

您可以在尚未附加至資料庫的新物件上，或當[CanUpdate](#canupdate)傳回非零值時，使用這個成員函式。

如需相關資訊，請參閱 DAO 說明中的「刪除方法」主題。

## <a name="cdaotabledefdeleteindex"></a><a name="deleteindex"></a>CDaoTableDef：:D eleteIndex

呼叫這個成員函式可刪除基礎資料表中的索引。

```cpp
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
字串運算式的指標，這是現有索引的名稱。

*nIndex*<br/>
在資料庫之以零為基底的 TableDefs 集合中，索引物件的陣列索引，用於依索引查閱。

### <a name="remarks"></a>備註

您可以在尚未附加到資料庫的新物件上，或當[CanUpdate](#canupdate)傳回非零值時，使用這個成員函式。

如需相關資訊，請參閱 DAO 說明中的「刪除方法」主題。

## <a name="cdaotabledefgetattributes"></a><a name="getattributes"></a>CDaoTableDef：： GetAttributes

對於 `CDaoTableDef` 物件，傳回值會指定物件所代表之資料表的特性 `CDaoTableDef` ，而且可以是這些常數的總和：

```
long GetAttributes();
```

### <a name="return-value"></a>傳回值

傳回值，指出物件的一或多個特性 `CDaoTableDef` 。

### <a name="remarks"></a>備註

|持續性|說明|
|--------------|-----------------|
|`dbAttachExclusive`|對於使用 Microsoft Jet 資料庫引擎的資料庫，表示資料表是已開啟供獨佔使用的附加資料表。|
|`dbAttachSavePWD`|對於使用 Microsoft Jet database engine 的資料庫，表示附加資料表的使用者識別碼和密碼會與連接資訊一併儲存。|
|`dbSystemObject`|表示資料表是 Microsoft Jet 資料庫引擎所提供的系統資料表。|
|`dbHiddenObject`|表示資料表是 Microsoft Jet 資料庫引擎所提供的隱藏資料表。|
|`dbAttachedTable`|表示資料表是來自非 ODBC 資料庫（例如 Paradox 資料庫）的附加資料表。|
|`dbAttachedODBC`|表示資料表是 ODBC 資料庫的附加資料表，例如 Microsoft SQL Server。|

系統資料表是 Microsoft Jet 資料庫引擎所建立的資料表，可包含各種內部資訊。

隱藏資料表是為了暫時使用 Microsoft Jet 資料庫引擎所建立的資料表。

如需相關資訊，請參閱 DAO 說明中的「屬性屬性」主題。

## <a name="cdaotabledefgetconnect"></a><a name="getconnect"></a>CDaoTableDef：： GetConnect

呼叫這個成員函式，以取得資料來源的連接字串。

```
CString GetConnect();
```

### <a name="return-value"></a>傳回值

`CString`物件，包含資料表的路徑和資料庫類型。

### <a name="remarks"></a>備註

對於 `CDaoTableDef` 代表附加資料表的物件， `CString` 物件是由一或兩個部分（資料庫類型規範和資料庫的路徑）所組成。

下表所示的路徑是包含資料庫檔案之目錄的完整路徑，而且前面必須加上識別碼 "DATABASE ="。 在某些情況下（如同 Microsoft Jet 和 Microsoft Excel 資料庫），特定的檔案名會包含在資料庫路徑引數中。

[CDaoTableDef：： SetConnect](#setconnect)中的資料表會顯示可能的資料庫類型及其對應的資料庫規範和路徑：

對於 Microsoft Jet 資料庫基表，規範是空字串（""）。

如果需要密碼但未提供，則在第一次存取資料表時，ODBC 驅動程式會顯示登入對話方塊，如果連接已關閉並重新開啟，則會再次出現。 如果附加資料表具有 `dbAttachSavePWD` 屬性，當重新開啟資料表時，就不會出現登入提示。

如需相關資訊，請參閱 DAO 說明中的「連接屬性」主題。

## <a name="cdaotabledefgetdatecreated"></a><a name="getdatecreated"></a>CDaoTableDef::GetDateCreated

呼叫此函式可決定建立物件之基礎資料表的日期和時間 `CDaoTableDef` 。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>傳回值

值，其中包含建立物件基礎資料表的日期和時間 `CDaoTableDef` 。

### <a name="remarks"></a>備註

日期和時間設定是從基表建立或上次更新的電腦衍生而來。 在多使用者環境中，使用者應該直接從檔案伺服器取得這些設定，以避免不一致的情況;也就是說，所有用戶端都應該使用「標準」時間來源，也許是從一部伺服器。

如需相關資訊，請參閱 DAO 說明中的「DateCreated，LastUpdated 屬性」主題。

## <a name="cdaotabledefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated

呼叫此函式可判斷 `CDaoTableDef` 上次更新物件之資料表的日期和時間。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>傳回值

值，其中包含 `CDaoTableDef` 上次更新物件之資料表的日期和時間。

### <a name="remarks"></a>備註

日期和時間設定是從基表建立或上次更新的電腦衍生而來。 在多使用者環境中，使用者應該直接從檔案伺服器取得這些設定，以避免不一致的情況;也就是說，所有用戶端都應該使用「標準」時間來源，也許是從一部伺服器。

如需相關資訊，請參閱 DAO 說明中的「DateCreated，LastUpdated 屬性」主題。

## <a name="cdaotabledefgetfieldcount"></a><a name="getfieldcount"></a>CDaoTableDef::GetFieldCount

呼叫這個成員函式，以抓取資料表中所定義的欄位數目。

```
short GetFieldCount();
```

### <a name="return-value"></a>傳回值

資料表中的欄位數目。

### <a name="remarks"></a>備註

如果其值為0，則集合中沒有任何物件。

如需相關資訊，請參閱 DAO 說明中的「計數屬性」主題。

## <a name="cdaotabledefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoTableDef：： Issomapper.getfieldinfo

呼叫這個成員函式可取得有關 tabledef 中所定義欄位的各種資訊。

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
資料表之以零為基底的欄位集合中，欄位物件的索引，用於依索引查閱。

*fieldinfo*<br/>
[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構的參考。

*dwInfoOptions*<br/>
指定要抓取之欄位的相關資訊的選項。 這裡列出可用的選項，以及它們會導致函式傳回的內容：

- `AFX_DAO_PRIMARY_INFO`預設名稱、類型、大小、屬性。 使用此選項可達到最快的效能。

- `AFX_DAO_SECONDARY_INFO`主要資訊，加上：序數位置、必要、允許零長度、排序次序、外部名稱、來源欄位、來源資料表

- `AFX_DAO_ALL_INFO`主要和次要資訊，加上：驗證規則、驗證文字、預設值

*lpszName*<br/>
欄位物件名稱的指標，用於依名稱查閱。 名稱是最多64個字元的字串，可唯一命名欄位。

### <a name="remarks"></a>備註

函數的其中一個版本可讓您依索引查閱欄位。 另一個版本可讓您依名稱查閱欄位。

如需所傳回信息的描述，請參閱[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。 此結構的成員會對應至*dwInfoOptions*的描述中所列的資訊專案。 當您要求某一層級的資訊時，您也會取得任何先前層級的資訊。

如需相關資訊，請參閱 DAO 說明中的「屬性屬性」主題。

## <a name="cdaotabledefgetindexcount"></a><a name="getindexcount"></a>CDaoTableDef::GetIndexCount

呼叫這個成員函式可取得資料表的索引數目。

```
short GetIndexCount();
```

### <a name="return-value"></a>傳回值

資料表的索引數目。

### <a name="remarks"></a>備註

如果其值為0，則集合中沒有任何索引。

如需相關資訊，請參閱 DAO 說明中的「計數屬性」主題。

## <a name="cdaotabledefgetindexinfo"></a><a name="getindexinfo"></a>CDaoTableDef：： GetIndexInfo

呼叫這個成員函式可取得有關 tabledef 中所定義索引的各種資訊。

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
資料表之以零為基底的索引集合中，索引物件的數值索引，用來依其在集合中的位置進行查閱。

*indexinfo*<br/>
[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構的參考。

*dwInfoOptions*<br/>
指定要抓取之索引相關資訊的選項。 這裡列出可用的選項，以及它們會導致函式傳回的內容：

- `AFX_DAO_PRIMARY_INFO`[名稱]、[欄位資訊]、[欄位]。 使用此選項可達到最快的效能。

- `AFX_DAO_SECONDARY_INFO`主要資訊，加上：主要、唯一、叢集、忽略 Null、必要、外部

- `AFX_DAO_ALL_INFO`主要和次要資訊，加上：相異計數

*lpszName*<br/>
索引物件名稱的指標，用於依名稱查閱。

### <a name="remarks"></a>備註

函式的其中一個版本可讓您依其在集合中的位置來查閱索引。 另一個版本可讓您依名稱查閱索引。

如需所傳回信息的描述，請參閱[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構。 此結構的成員會對應至*dwInfoOptions*的描述中所列的資訊專案。 當您要求某一層級的資訊時，您也會取得任何先前層級的資訊。

如需相關資訊，請參閱 DAO 說明中的「屬性屬性」主題。

## <a name="cdaotabledefgetname"></a><a name="getname"></a>CDaoTableDef：： GetName

呼叫這個成員函式，以取得基礎資料表的使用者定義名稱。

```
CString GetName();
```

### <a name="return-value"></a>傳回值

資料表的使用者定義名稱。

### <a name="remarks"></a>備註

這個名稱是以字母開頭，且最多可包含64個字元。 它可以包含數位和底線字元，但不能包含標點符號或空格。

如需相關資訊，請參閱 DAO 說明中的「名稱屬性」主題。

## <a name="cdaotabledefgetrecordcount"></a><a name="getrecordcount"></a>CDaoTableDef：： GetRecordCount

呼叫這個成員函式可找出物件中有多少筆記錄 `CDaoTableDef` 。

```
long GetRecordCount();
```

### <a name="return-value"></a>傳回值

在 tabledef 物件中存取的記錄數目。

### <a name="remarks"></a>備註

`GetRecordCount`針對資料表類型 `CDaoTableDef` 物件呼叫會反映資料表中大約的記錄數目，而且會在加入和刪除資料表記錄時立即受到影響。 復原的交易將會顯示為記錄計數的一部分，直到您呼叫[CDaoWorkSpace：：壓縮](../../mfc/reference/cdaoworkspace-class.md#compactdatabase)。 `CDaoTableDef`沒有記錄的物件具有 [記錄計數] 屬性設定為0。 使用附加資料表或 ODBC 資料庫時，一律會傳回 `GetRecordCount` -1。

如需相關資訊，請參閱 DAO 說明中的「RecordCount 屬性」主題。

## <a name="cdaotabledefgetsourcetablename"></a><a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName

呼叫這個成員函式，以取得源資料庫中附加資料表的名稱。

```
CString GetSourceTableName();
```

### <a name="return-value"></a>傳回值

`CString`物件，指定附加資料表的來源名稱，如果是原生資料表，則為空字串。

### <a name="remarks"></a>備註

附加資料表是另一個連結至 Microsoft Jet 資料庫之資料庫中的資料表。 附加資料表的資料會保留在外部資料庫中，供其他應用程式操作。

如需相關資訊，請參閱 DAO 說明中的「SourceTableName 屬性」主題。

## <a name="cdaotabledefgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoTableDef::GetValidationRule

呼叫這個成員函式，以取得 tabledef 的驗證規則。

```
CString GetValidationRule();
```

### <a name="return-value"></a>傳回值

`CString`物件，在欄位變更或加入至資料表時，驗證其資料。

### <a name="remarks"></a>備註

驗證規則會用於與更新作業的連接。 如果 tabledef 包含驗證規則，該 tabledef 的更新必須符合預先決定的準則，然後才會變更資料。 如果變更不符合準則，則會擲回包含[GetValidationText](#getvalidationtext)值的例外狀況。 對於 `CDaoTableDef` 物件而言，此為 `CString` 附加資料表的唯讀，而且為基表的讀取/寫入。

如需相關資訊，請參閱 DAO 說明中的「ValidationRule 屬性」主題。

## <a name="cdaotabledefgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoTableDef::GetValidationText

呼叫此函式可在使用者輸入不符合驗證規則的資料時，取得要顯示的字串。

```
CString GetValidationText();
```

### <a name="return-value"></a>傳回值

`CString`物件，指定使用者輸入不符合驗證規則的資料時所顯示的文字。

### <a name="remarks"></a>備註

對於 `CDaoTableDef` 物件而言，此為 `CString` 附加資料表的唯讀，而且為基表的讀取/寫入。

如需相關資訊，請參閱 DAO 說明中的「有效性屬性」主題。

## <a name="cdaotabledefisopen"></a><a name="isopen"></a>CDaoTableDef：： IsOpen

呼叫這個成員函式，以判斷 `CDaoTableDef` 物件目前是否開啟。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果物件已開啟，則為非零， `CDaoTableDef` 否則為0。

### <a name="remarks"></a>備註

## <a name="cdaotabledefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoTableDef：： m_pDatabase

包含此資料表之[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件的指標。

### <a name="remarks"></a>備註

## <a name="cdaotabledefm_pdaotabledef"></a><a name="m_pdaotabledef"></a>CDaoTableDef：： m_pDAOTableDef

包含物件之 tabledef 物件的 OLE 介面的指標 `CDaoTableDef` 。

### <a name="remarks"></a>備註

如果您需要直接存取 DAO 介面，請使用此指標。

## <a name="cdaotabledefopen"></a><a name="open"></a>CDaoTableDef：： Open

呼叫這個成員函式，以開啟先前儲存在資料庫 TableDef's 集合中的 tabledef。

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
指定資料表名稱之字串的指標。

### <a name="remarks"></a>備註

## <a name="cdaotabledefrefreshlink"></a><a name="refreshlink"></a>CDaoTableDef::RefreshLink

呼叫這個成員函式，以更新附加資料表的連接資訊。

```cpp
void RefreshLink();
```

### <a name="remarks"></a>備註

您可以藉由在對應的物件上呼叫[SetConnect](#setconnect) `CDaoTableDef` ，然後使用成員函式 `RefreshLink` 來更新資訊，藉以變更附加資料表的連接資訊。 當您呼叫時 `RefreshLink` ，附加資料表的屬性不會變更。

若要強制修改的 connect 資訊生效，必須關閉以這個 tabledef 為基礎的所有開啟的[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件。

如需相關資訊，請參閱 DAO 說明中的「RefreshLink 方法」主題。

## <a name="cdaotabledefsetattributes"></a><a name="setattributes"></a>CDaoTableDef：： SetAttributes

設定值，指出物件的一或多個特性 `CDaoTableDef` 。

```cpp
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>參數

*lAttributes*<br/>
物件所代表之資料表的特性 `CDaoTableDef` ，而且可以是這些常數的總和：

|持續性|說明|
|--------------|-----------------|
|`dbAttachExclusive`|對於使用 Microsoft Jet 資料庫引擎的資料庫，表示資料表是已開啟供獨佔使用的附加資料表。|
|`dbAttachSavePWD`|對於使用 Microsoft Jet database engine 的資料庫，表示附加資料表的使用者識別碼和密碼會與連接資訊一併儲存。|
|`dbSystemObject`|表示資料表是 Microsoft Jet 資料庫引擎所提供的系統資料表。|
|`dbHiddenObject`|表示資料表是 Microsoft Jet 資料庫引擎所提供的隱藏資料表。|

### <a name="remarks"></a>備註

設定多個屬性時，您可以使用位 OR 運算子來加總適當的常數，以將它們結合在一起。 `dbAttachExclusive`未附加資料表上的設定會產生例外狀況。 結合下列值也會產生例外狀況：

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

如需相關資訊，請參閱 DAO 說明中的「屬性屬性」主題。

## <a name="cdaotabledefsetconnect"></a><a name="setconnect"></a>CDaoTableDef::SetConnect

對於 `CDaoTableDef` 代表附加資料表的物件，字串物件是由一或兩個部分（資料庫類型規範和資料庫的路徑）所組成。

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>參數

*lpszConnect*<br/>
字串運算式的指標，指定要傳遞至 ODBC 或可安裝之 ISAM 驅動程式的其他參數。

### <a name="remarks"></a>備註

下表所示的路徑是包含資料庫檔案之目錄的完整路徑，而且前面必須加上識別碼 "DATABASE ="。 在某些情況下（如同 Microsoft Jet 和 Microsoft Excel 資料庫），特定的檔案名會包含在資料庫路徑引數中。

> [!NOTE]
> 請不要在 "DATABASE = drive： \path" 格式的等號的路徑語句前後加上空白字元 \\ 。 這會導致擲回例外狀況，且連接失敗。

下表顯示可能的資料庫類型及其對應的資料庫規範和路徑：

|資料庫類型|規範|Path|
|-------------------|---------------|----------|
|使用 Jet 資料庫引擎的資料庫|"[ `database`];"|" `drive` ： \\ \  *path* \\ \  *filename*。.MDB|
|dBASE III|"dBASE III;"|" `drive` ： \\ \  *path*"|
|dBASE IV|"dBASE IV;"|" `drive` ： \\ \  *path*"|
|dBASE 5|"dBASE 5.0;"|" `drive` ： \\ \  *path*"|
|Paradox 3。x|「Paradox 3. x;」|" `drive` ： \\ \  *path*"|
|Paradox 4。x|「Paradox 4. x;」|" `drive` ： \\ \  *path*"|
|Paradox 5。x|「Paradox 5. x;」|" `drive` ： \\ \  *path*"|
|Excel 3。0|"Excel 3.0;"|" `drive` ： \\ \  *path* \\ \  *filename*。.XLS|
|Excel 4。0|"Excel 4.0;"|" `drive` ： \\ \  *path* \\ \  *filename*。.XLS|
|Excel 5.0 或 Excel 95|"Excel 5.0;"|" `drive` ： \\ \  *path* \\ \  *filename*。.XLS|
|Excel 97|"Excel 8.0;"|" `drive` ： \\ \  *path* \  *filename*。.XLS|
|HTML 匯入|"HTML Import;"|" `drive` ： \\ \  *path* \  *filename*"|
|HTML 匯出|"HTML Export;"|" `drive` ： \\ \  *path*"|
|Text|"Text;"|"drive： \\ \path"|
|ODBC|ODBC資料庫 = `database` ;UID = *user*;PWD = *password*;DSN = [*值];* LOGINTIMEOUT =*秒;*"（這可能不是所有伺服器的完整連接字串，只是其中一個範例。 參數之間不需要有空格）。|無|
|Exchange|固定匯率<br /><br /> MAPILEVEL = *folderpath*;<br /><br /> [TABLETYPE = {0 &#124; 1};]<br /><br /> [設定檔 =*設定檔*;]<br /><br /> [PWD = *password*;]<br /><br /> [DATABASE = `database` ;] "|「*磁片磁碟機*： \\ \  *路徑* \\ \  *檔案名*。.MDB|

> [!NOTE]
> 從 DAO 3.5，已不再支援 Btrieve。

您必須 \\ \\ 在連接字串中使用雙反斜線（）。 如果您已使用修改現有連接的屬性 `SetConnect` ，就必須接著呼叫[RefreshLink](#refreshlink)。 如果您使用來初始化連接屬性 `SetConnect` ，則不需要呼叫 `RefreshLink` ，但如果您選擇這樣做，請先附加 tabledef。

如果需要密碼但未提供，則在第一次存取資料表時，ODBC 驅動程式會顯示登入對話方塊，如果連接已關閉並重新開啟，則會再次出現。

您可以將 `CDaoTableDef` 來源引數提供給成員函式，以設定物件的連接字串 `Create` 。 您可以檢查設定，以決定資料庫的類型、路徑、使用者識別碼、密碼或 ODBC 資料來源。 如需詳細資訊，請參閱特定驅動程式的檔集。

如需相關資訊，請參閱 DAO 說明中的「連接屬性」主題。

## <a name="cdaotabledefsetname"></a><a name="setname"></a>CDaoTableDef：： SetName

呼叫這個成員函式可設定資料表的使用者定義名稱。

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
字串運算式的指標，指定資料表的名稱。

### <a name="remarks"></a>備註

名稱必須以字母開頭，且最多可包含64個字元。 它可以包含數位和底線字元，但不能包含標點符號或空格。

如需相關資訊，請參閱 DAO 說明中的「名稱屬性」主題。

## <a name="cdaotabledefsetsourcetablename"></a><a name="setsourcetablename"></a>CDaoTableDef::SetSourceTableName

呼叫這個成員函式可指定附加資料表的名稱，或物件所依據之基表的名稱 `CDaoTableDef` ，因為它存在於資料的原始來源中。

```cpp
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>參數

*lpszSrcTableName*<br/>
字串運算式的指標，指定外部資料庫中的資料表名稱。 若為基表，設定為空字串（""）。

### <a name="remarks"></a>備註

接著，您必須呼叫[RefreshLink](#refreshlink)。 基表的這個屬性設定是空的，而且在附加資料表或未附加至集合之物件的讀取/寫入。

如需相關資訊，請參閱 DAO 說明中的「SourceTableName 屬性」主題。

## <a name="cdaotabledefsetvalidationrule"></a><a name="setvalidationrule"></a>CDaoTableDef::SetValidationRule

呼叫這個成員函式，以設定 tabledef 的驗證規則。

```cpp
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>參數

*lpszValidationRule*<br/>
驗證作業之字串運算式的指標。

### <a name="remarks"></a>備註

驗證規則會用於與更新作業的連接。 如果 tabledef 包含驗證規則，該 tabledef 的更新必須符合預先決定的準則，然後才會變更資料。 如果變更不符合準則，則會顯示包含[GetValidationText](#getvalidationtext)文字的例外狀況。

只有使用 Microsoft Jet database engine 的資料庫才支援驗證。 運算式不能參考使用者自訂函數、網域彙總函式、SQL 彙總函式或查詢。 物件的驗證規則 `CDaoTableDef` 可以參考該物件中的多個欄位。

例如，對於名為*hire_date*和*termination_date*的欄位，驗證規則可能是：

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

如需相關資訊，請參閱 DAO 說明中的「ValidationRule 屬性」主題。

## <a name="cdaotabledefsetvalidationtext"></a><a name="setvalidationtext"></a>CDaoTableDef::SetValidationText

呼叫這個成員函式可針對 `CDaoTableDef` 具有 Microsoft Jet 資料庫引擎支援之基礎基表的物件，設定其驗證規則的例外狀況文字。

```cpp
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>參數

*lpszValidationText*<br/>
字串運算式的指標，指定輸入的資料無效時所顯示的文字。

### <a name="remarks"></a>備註

您不能設定附加資料表的驗證文字。

如需相關資訊，請參閱 DAO 說明中的「有效性屬性」主題。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)
