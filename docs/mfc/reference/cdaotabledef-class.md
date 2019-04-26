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
ms.openlocfilehash: 485fe3533916e5e59bc87084f58acfb37368ac32
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151211"
---
# <a name="cdaotabledef-class"></a>CDaoTableDef 類別

表示儲存的基底資料表或附加資料表定義。

## <a name="syntax"></a>語法

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|建構 `CDaoTableDef` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDaoTableDef::Append](#append)|將新的資料表加入資料庫中。|
|[CDaoTableDef::CanUpdate](#canupdate)|傳回非零值，如果可以更新資料表 （您可以修改欄位或資料表屬性的定義）。|
|[CDaoTableDef::Close](#close)|關閉開啟的 tabledef。|
|[CDaoTableDef::Create](#create)|建立可加入到資料庫時使用這些資料表[Append](#append)。|
|[CDaoTableDef::CreateField](#createfield)|呼叫以建立資料表的欄位。|
|[CDaoTableDef::CreateIndex](#createindex)|呼叫以建立資料表的索引。|
|[CDaoTableDef::DeleteField](#deletefield)|呼叫以從資料表中刪除欄位。|
|[CDaoTableDef::DeleteIndex](#deleteindex)|呼叫以從資料表中刪除索引。|
|[CDaoTableDef::GetAttributes](#getattributes)|傳回值，這個值，指出一或多個特性`CDaoTableDef`物件。|
|[CDaoTableDef::GetConnect](#getconnect)|傳回值，這個值，以提供來源資料表的相關資訊。|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|傳回的日期和時間的基底資料表的基礎`CDaoTableDef`建立物件。|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|傳回的日期和時間的最新的基底資料表的設計所做的變更。|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|傳回值，這個值表示資料表中的欄位數目。|
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|傳回資料表中的特定類型的欄位的相關資訊。|
|[CDaoTableDef::GetIndexCount](#getindexcount)|傳回資料表的索引數目。|
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|傳回特定類型的資料表索引的相關資訊。|
|[CDaoTableDef::GetName](#getname)|傳回使用者定義資料表的名稱。|
|[CDaoTableDef::GetRecordCount](#getrecordcount)|傳回資料表中的記錄數目。|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|傳回值，這個值，指定來源資料庫中的連結資料表的名稱。|
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|傳回值，這個值會驗證欄位中的資料，因為它已變更或加入至資料表。|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|傳回值，這個值，指定如果欄位物件的值不符合指定的驗證規則，會顯示您的應用程式之訊息的文字。|
|[CDaoTableDef::IsOpen](#isopen)|傳回非零值，如果資料表為開啟。|
|[CDaoTableDef::Open](#open)|開啟儲存在資料庫中現有的 tabledef 的 TableDef 的集合。|
|[CDaoTableDef::RefreshLink](#refreshlink)|更新連結資料表的連接資訊。|
|[CDaoTableDef::SetAttributes](#setattributes)|設定值，這個值，指出一或多個特性`CDaoTableDef`物件。|
|[CDaoTableDef::SetConnect](#setconnect)|設定值，這個值，以提供來源資料表的相關資訊。|
|[CDaoTableDef::SetName](#setname)|設定資料表的名稱。|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|設定值，這個值，指定來源資料庫中的連結資料表的名稱。|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|設定值，這個值會驗證欄位中的資料，因為它已變更或加入至資料表。|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|設定值，這個值，指定如果欄位物件的值不符合指定的驗證規則，會顯示您的應用程式之訊息的文字。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|基礎 tabledef 物件 DAO 介面的指標。|
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|這份資料表的來源資料庫。|

## <a name="remarks"></a>備註

每個 DAO 資料庫物件會維護名 TableDefs，包含所有已儲存的 DAO tabledef 物件的集合。

您操作資料表定義，使用`CDaoTableDef`物件。 例如，您可以：

- 檢查資料庫中的任何本機、 附加檔案、 或外部資料表的欄位和索引結構。

- 呼叫`SetConnect`並`SetSourceTableName`成員函式附加的資料表，並使用`RefreshLink`成員函式來更新連接到連結的資料表。

- 呼叫`CanUpdate`成員函式，來判斷是否您可以編輯資料表中的欄位定義。

- 取得或設定使用的驗證條件`GetValidationRule`並`SetValidationRule`，而`GetValidationText`和`SetValidationText`成員函式。

- 使用`Open`成員函式來建立資料表類型、 動態集或快照集類型`CDaoRecordset`物件。

    > [!NOTE]
    >  DAO 資料庫類別是開放式資料庫連接 (ODBC) 為基礎的 MFC 資料庫類別有所區別。 所有的 DAO 資料庫類別名稱有"CDao"前置詞。 您仍然可以使用 DAO 類別; 存取 ODBC 資料來源DAO 類別通常提供優異的功能，因為它們是特定 Microsoft Jet 資料庫引擎。

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>若要使用現有的資料表，或建立新的資料表，請使用 tabledef 物件

1. 在所有情況下，先建構`CDaoTableDef`物件，提供的指標[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)資料表所屬的物件。

1. 然後執行下列作業，取決於您想要：

   - 若要使用現有已儲存的資料表，可以呼叫 tabledef 物件的[開啟](#open)成員函式，提供已儲存的資料表名稱。

   - 若要建立新的資料表，請呼叫 tabledef 物件[建立](#create)成員函式，提供資料表的名稱。 呼叫[CreateField](#createfield)並[CreateIndex](#createindex)來加入資料表中的欄位和索引。

   - 呼叫[Append](#append)以將它附加到資料庫的 TableDefs 集合中儲存資料表。 `Create` tabledef 放在開啟狀態，因此之後呼叫`Create`您不能呼叫`Open`。

        > [!TIP]
        >  若要建立已儲存的資料表最簡單方式是建立 proxy，並將它們儲存在您使用 Microsoft Access 的資料庫。 然後您可以開啟，並在您的 MFC 程式碼中使用它們。

若要使用您已經開啟，或建立 tabledef 物件，建立並開啟`CDaoRecordset`物件，指定的名稱與 tabledef`dbOpenTable`中的值*nOpenType*參數。

若要使用 tabledef 物件來建立`CDaoRecordset`物件，您通常可以建立或開啟 tabledef，如上所述，然後建構資料錄集物件，當您呼叫時，就將指標傳遞至 tabledef 物件[cdaorecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)。 您傳遞 tabledef 必須處於開啟狀態。 如需詳細資訊，請參閱類別[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

當您完成使用 tabledef 物件時，呼叫其[關閉](../../mfc/reference/cdaorecordset-class.md#close)成員函式，然後終結 tabledef 物件。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>需求

**標頭：** afxdao.h

##  <a name="append"></a>  CDaoTableDef::Append

呼叫此成員函式之後您呼叫,[建立](#create)來建立新的 tabledef 物件，以在資料庫中儲存 tabledef。

```
virtual void Append();
```

### <a name="remarks"></a>備註

此函式會將物件附加至資料庫的 TableDefs 集合。 您可以為暫存物件使用 tabledef，同時還可定義未附加，但如果您想要儲存，並使用它，您必須呼叫`Append`。

> [!NOTE]
>  如果您嘗試附加未命名的 tabledef （包含 null 或空字串） 時，MFC 會擲回例外狀況。

如需相關資訊，請參閱 DAO [說明] 中的 「 附加方法 」。

##  <a name="canupdate"></a>  CDaoTableDef::CanUpdate

呼叫此成員函式，以判斷是否定義基礎資料表`CDaoTableDef`物件可以變更。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>傳回值

如果可以修改資料表結構 （結構描述） 為非零 （新增或刪除欄位和索引），否則為 0。

### <a name="remarks"></a>備註

根據預設，新建立的資料表，基礎`CDaoTableDef`物件可以更新，並附加的資料表基礎`CDaoTableDef`無法更新物件。 A`CDaoTableDef`物件可能是可更新，即使不是可更新結果的資料錄集。

如需相關資訊，請參閱 DAO [說明] 中的 「 可更新屬性 」。

##  <a name="cdaotabledef"></a>  CDaoTableDef::CDaoTableDef

建構 `CDaoTableDef` 物件。

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>參數

*pDatabase*<br/>
指標[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件。

### <a name="remarks"></a>備註

之後建構物件時，您必須呼叫[Create](#create)或是[開啟](#open)成員函式。 當您完成使用物件時，您必須呼叫其[關閉](#close)成員函式，並終結`CDaoTableDef`物件。

##  <a name="close"></a>  CDaoTableDef::Close

呼叫此成員函式，以關閉及釋放 tabledef 物件。

```
virtual void Close();
```

### <a name="remarks"></a>備註

通常在呼叫後`Close`，如果配置使用，會刪除 tabledef 物件**新**。

您可以呼叫[開放](#open)在呼叫之後，再次`Close`。 這可讓您重複使用 tabledef 物件。

如需相關資訊，請參閱 DAO [說明] 中的 「 關閉方法 」。

##  <a name="create"></a>  CDaoTableDef::Create

呼叫此成員函式，建立新的儲存的資料表。

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
包含的資料表名稱的字串指標。

*lAttributes*<br/>
值，對應至 tabledef 物件所表示之表格的特性。 您可以使用位元 OR 結合任何下列常數：

|常數|描述|
|--------------|-----------------|
|`dbAttachExclusive`|使用 Microsoft Jet 資料庫引擎的資料庫，表示資料表是附加的資料表開啟以供獨佔使用。|
|`dbAttachSavePWD`|使用 Microsoft Jet 資料庫引擎的資料庫，表示儲存的使用者識別碼和密碼附加的資料表，使用的連接資訊。|
|`dbSystemObject`|表示資料表是由 Microsoft Jet 資料庫引擎提供的系統資料表。|
|`dbHiddenObject`|表示資料表是由 Microsoft Jet 資料庫引擎提供隱藏的資料表。|

*lpszSrcTable*<br/>
包含來源資料表名稱的字串指標。 依預設這個值會初始化為 NULL。

*lpszConnect*<br/>
字串，包含預設的連接字串的指標。 依預設這個值會初始化為 NULL。

### <a name="remarks"></a>備註

一旦您已命名 tabledef，您就可以呼叫[Append](#append)儲存 tabledef 資料庫 TableDefs 集合中。 之後呼叫`Append`，tabledef 是處於開啟狀態，您可以使用它來建立[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件。

如需相關資訊，請參閱 DAO [說明] 中的 < CreateTableDef 方法 >。

##  <a name="createfield"></a>  CDaoTableDef::CreateField

呼叫此成員函式，將欄位加入至資料表。

```
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
指向的字串運算式，指定這個欄位的名稱。

*nType*<br/>
值，指出欄位的資料類型。 設定可以是下列值之一：

|類型|大小 (位元組)|描述|
|----------|--------------------|-----------------|
|`dbBoolean`|1 個位元組|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|貨幣 ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|日期/時間 ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|文字 ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|長二進位檔 （OLE 物件）， [CLongBinary](../../mfc/reference/clongbinary-class.md)或[CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|備忘 ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
值，指出最大的大小，以位元組為單位的欄位，包含文字或包含文字或數值的欄位的固定的大小。 *LSize*文字欄位以外，所有的參數會被忽略。

*lAttributes*<br/>
值，對應到 [特性] 欄位，可以使用位元 OR 結合起來。

|常數|描述|
|--------------|-----------------|
|`dbFixedField`|欄位大小被固定的 （數值欄位的預設值）。|
|`dbVariableField`|欄位大小是變數 （文字欄位）。|
|`dbAutoIncrField`|新的資料錄的欄位值無法變更的唯一的長整數，會自動遞增。 僅支援 Microsoft Jet 資料庫資料表。|
|`dbUpdatableField`|可以變更欄位值。|
|`dbDescending`|欄位以遞減排序 (Z-A 或 100-0) （僅適用於索引物件的欄位集合中的欄位物件） 的順序。 如果您省略這個常數時，欄位以遞增排序 (A-Z 或 0-100) 順序 （預設值）。|

*fieldinfo*<br/>
參考[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。

### <a name="remarks"></a>備註

A `DAOField` (OLE) 物件會建立並附加至的欄位集合`DAOTableDef`(OLE) 物件。 除了檢查物件屬性使用，您也可以使用`CDaoFieldInfo`建構 tabledef 中建立新欄位的輸入的參數。 第一版`CreateField`簡單好用，但如果想要更細微的控制，您可以使用第二版`CreateField`，這個方法會接受`CDaoFieldInfo`參數。

如果您使用新版`CreateField`採用`CDaoFieldInfo`參數，您必須仔細設定的下列成員的每個`CDaoFieldInfo`結構：

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

其餘的成員`CDaoFieldInfo`應該設定為**0**，FALSE 或空字串，視您的成員，或`CDaoException`可能會發生。

如需相關資訊，請參閱 DAO [說明] 中的 < CreateField 方法 >。

##  <a name="createindex"></a>  CDaoTableDef::CreateIndex

呼叫此函式可將索引加入資料表。

```
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>參數

*indexinfo*<br/>
參考[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構。

### <a name="remarks"></a>備註

索引會指定從資料庫資料表，以及接受重複的記錄存取記錄的順序。 索引也會提供有效率地存取資料。

您不需要建立索引的資料表，但在大型、 未編製索引的資料表中，存取特定的記錄或建立資料錄集可能需要很長的時間。 相反地，建立太多索引降低更新、 附加及刪除作業，因為所有的索引會自動更新。 當您決定哪一個要建立的索引，請考慮下列因素。

下列成員`CDaoIndexInfo`結構必須設定：

- `m_strName` 必須提供名稱。

- `m_pFieldInfos` 陣列必須指向`CDaoIndexFieldInfo`結構。

- `m_nFields` 必須指定陣列中的欄位數目`CDaoFieldInfo`結構。

其餘成員將會忽略設定為 FALSE 時。 颾魤 ㄛ`m_lDistinctCount`建立索引期間會忽略的成員。

##  <a name="deletefield"></a>  CDaoTableDef::DeleteField

呼叫此成員函式來移除欄位，並使其無法存取。

```
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
指標，是現有的欄位名稱的字串運算式。

*nIndex*<br/>
資料表的以零為起始的欄位集合中，依索引查閱欄位的索引。

### <a name="remarks"></a>備註

您可以使用此成員函式上新的物件未附加到資料庫，或當[CanUpdate](#canupdate)傳回非零值。

如需相關資訊，請參閱 DAO [說明] 中的 < 刪除方法 >。

##  <a name="deleteindex"></a>  CDaoTableDef::DeleteIndex

呼叫此成員函式來刪除基礎資料表中的索引。

```
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
指標，是現有的索引名稱的字串運算式。

*nIndex*<br/>
資料庫的以零為起始 TableDefs 集合中，依索引查閱的索引物件的陣列索引。

### <a name="remarks"></a>備註

您可以使用此成員函式上新的物件尚未附加到資料庫，或當[CanUpdate](#canupdate)傳回非零值。

如需相關資訊，請參閱 DAO [說明] 中的 < 刪除方法 >。

##  <a name="getattributes"></a>  CDaoTableDef::GetAttributes

針對`CDaoTableDef`物件，傳回的值會指定所表示之表格的特性`CDaoTableDef`物件，而且可以是加總兩個常數：

```
long GetAttributes();
```

### <a name="return-value"></a>傳回值

傳回值，這個值，指出一或多個特性`CDaoTableDef`物件。

### <a name="remarks"></a>備註

|常數|描述|
|--------------|-----------------|
|`dbAttachExclusive`|使用 Microsoft Jet 資料庫引擎的資料庫，表示資料表是附加的資料表開啟以供獨佔使用。|
|`dbAttachSavePWD`|使用 Microsoft Jet 資料庫引擎的資料庫，表示儲存的使用者識別碼和密碼附加的資料表，使用的連接資訊。|
|`dbSystemObject`|表示資料表是由 Microsoft Jet 資料庫引擎提供的系統資料表。|
|`dbHiddenObject`|表示資料表是由 Microsoft Jet 資料庫引擎提供隱藏的資料表。|
|`dbAttachedTable`|表示資料表是從非 ODBC 資料庫，例如 Paradox 資料庫連接的資料表。|
|`dbAttachedODBC`|表示資料表是來自 ODBC 資料庫，例如 Microsoft SQL Server 連接的資料表。|

系統資料表是由 Microsoft Jet 資料庫引擎，來包含各種不同的內部資訊的資料表。

隱藏的資料表是由 Microsoft Jet 資料庫引擎建立暫時使用的資料表。

如需相關資訊，請參閱 DAO [說明] 中的 「 屬性屬性 」。

##  <a name="getconnect"></a>  CDaoTableDef::GetConnect

呼叫此成員函式，以取得資料來源的連接字串。

```
CString GetConnect();
```

### <a name="return-value"></a>傳回值

A`CString`物件，包含資料表的路徑和資料庫類型。

### <a name="remarks"></a>備註

針對`CDaoTableDef`物件，表示附加的資料表，`CString`物件 （資料庫類型指定名稱和資料庫的路徑） 的一或兩個部分所組成。

下表所示的路徑是包含資料庫檔案的目錄的完整路徑和前面必須有識別項"資料庫 ="。 在某些情況 （如 Microsoft Excel 與 Microsoft Jet 資料庫） 中，特定的檔案名稱包含在資料庫路徑引數。

中的資料表[CDaoTableDef::SetConnect](#setconnect)顯示可能的資料庫類型和其對應的資料庫指定名稱和路徑：

Microsoft Jet 資料庫基底資料表的指定名稱是空字串 ("")。

如果密碼是必要，但未提供，ODBC 驅動程式會顯示登入對話方塊第一次資料表存取時，另一次，如果連接關閉又重新開啟。 如果附加的資料表有`dbAttachSavePWD`屬性，登入提示不會重新開啟資料表時。

如需相關資訊，請參閱 DAO [說明] 中的 [連接屬性]。

##  <a name="getdatecreated"></a>  CDaoTableDef::GetDateCreated

呼叫此函式以判斷時間與日期資料表基礎`CDaoTableDef`建立物件。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>傳回值

值，其中包含的日期和時間的基礎資料表建立`CDaoTableDef`物件。

### <a name="remarks"></a>備註

日期和時間設定被衍生自基底資料表已建立或上次更新的電腦。 在多使用者環境中，使用者應該直接從檔案伺服器，以避免不一致; 取得這些設定也就是說，所有的用戶端應該使用 「 標準 」 的時間來源，可能是從一部伺服器。

如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。

##  <a name="getdatelastupdated"></a>  CDaoTableDef::GetDateLastUpdated

呼叫此函式以判斷時間與日期資料表基礎`CDaoTableDef`上次更新物件。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>傳回值

值，包含的日期和時間的基礎資料表`CDaoTableDef`上次更新物件。

### <a name="remarks"></a>備註

日期和時間設定被衍生自基底資料表已建立或上次更新的電腦。 在多使用者環境中，使用者應該直接從檔案伺服器，以避免不一致; 取得這些設定也就是說，所有的用戶端應該使用 「 標準 」 的時間來源，可能是從一部伺服器。

如需相關資訊，請參閱 DAO 說明主題 「 DateCreated LastUpdated 屬性 」。

##  <a name="getfieldcount"></a>  CDaoTableDef::GetFieldCount

呼叫此成員函式可擷取的資料表中定義的欄位數目。

```
short GetFieldCount();
```

### <a name="return-value"></a>傳回值

在資料表中的欄位數目。

### <a name="remarks"></a>備註

如果其值為 0，則沒有物件儲存在集合上。

如需相關資訊，請參閱 DAO [說明] 中的 < 計數屬性 >。

##  <a name="getfieldinfo"></a>  CDaoTableDef::GetFieldInfo

呼叫此成員函式，以取得各種 tabledef 中定義欄位的相關資訊。

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
資料表的以零為起始的欄位集合中，依索引查閱欄位物件的索引。

*fieldinfo*<br/>
參考[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。

*dwInfoOptions*<br/>
指定要擷取的欄位相關資訊的選項。 以下列出可用的選項以及它們會導致此函數傳回：

- `AFX_DAO_PRIMARY_INFO` （預設值）屬性名稱、 類型、 大小。 使用此選項，以最快的效能。

- `AFX_DAO_SECONDARY_INFO` 主要的資訊，再加上：序數位置，所需，允許的長度為零，定序順序、 外部索引的名稱、 來源欄位、 來源資料表

- `AFX_DAO_ALL_INFO` 主要和次要的資訊，再加上：驗證規則，驗證文字的預設值

*lpszName*<br/>
物件的名稱欄位，依名稱查閱的指標。 最多 64 個字元的字串可唯一地命名欄位的名稱。

### <a name="remarks"></a>備註

一個版本的函式可讓您依索引查閱欄位。 另一個版本可讓您依名稱查閱欄位。

如需傳回資訊的說明，請參閱 < [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。 此結構具有上述描述中的資訊的項目所對應的成員*dwInfoOptions*。 當您要求一層級的資訊時，您會取得任何先前的層的資訊。

如需相關資訊，請參閱 DAO [說明] 中的 「 屬性屬性 」。

##  <a name="getindexcount"></a>  CDaoTableDef::GetIndexCount

呼叫此成員函式，以取得資料表的索引數目。

```
short GetIndexCount();
```

### <a name="return-value"></a>傳回值

資料表的索引數目。

### <a name="remarks"></a>備註

如果其值為 0，則沒有索引儲存在集合上。

如需相關資訊，請參閱 DAO [說明] 中的 < 計數屬性 >。

##  <a name="getindexinfo"></a>  CDaoTableDef::GetIndexInfo

呼叫此成員函式，以取得各種 tabledef 中定義索引的相關資訊。

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

*nIndex*<br/>
資料表的以零為起始的索引集合中，查閱所處的位置，集合中的索引物件的數值索引。

*indexinfo*<br/>
參考[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構。

*dwInfoOptions*<br/>
指定要擷取索引的相關資訊的選項。 以下列出可用的選項以及它們會導致此函數傳回：

- `AFX_DAO_PRIMARY_INFO` 名稱欄位資訊欄位。 使用此選項，以最快的效能。

- `AFX_DAO_SECONDARY_INFO` 主要的資訊，再加上：主要、 唯一的叢集化，忽略 null 值，需要的外部索引

- `AFX_DAO_ALL_INFO` 主要和次要的資訊，再加上：相異計數

*lpszName*<br/>
依名稱查閱的索引物件的名稱指標。

### <a name="remarks"></a>備註

一個版本的函式可讓您查詢依其在集合中的位置索引。 另一個版本可讓您依名稱查閱的索引。

如需傳回資訊的說明，請參閱 < [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構。 此結構具有上述描述中的資訊的項目所對應的成員*dwInfoOptions*。 當您要求一層級的資訊時，您會取得任何先前的層的資訊。

如需相關資訊，請參閱 DAO [說明] 中的 「 屬性屬性 」。

##  <a name="getname"></a>  CDaoTableDef::GetName

呼叫此成員函式，來取得使用者定義的基礎資料表的名稱。

```
CString GetName();
```

### <a name="return-value"></a>傳回值

使用者定義資料表的名稱。

### <a name="remarks"></a>備註

這個名稱會以字母為開頭，且可以包含最多 64 個字元。 它可以包含數字和底線字元，但不能包含標點符號或空格。

如需相關資訊，請參閱 DAO [說明] 中的 「 名稱屬性 」。

##  <a name="getrecordcount"></a>  CDaoTableDef::GetRecordCount

呼叫此成員函式，以找出多少筆記錄位於`CDaoTableDef`物件。

```
long GetRecordCount();
```

### <a name="return-value"></a>傳回值

存取 tabledef 物件中的記錄數目。

### <a name="remarks"></a>備註

呼叫`GetRecordCount`對資料表類型`CDaoTableDef`物件會反映近似數目的資料表中的記錄，以及新增和刪除資料表記錄時立即影響。 回復交易會出現的記錄計數的一部分，直到您呼叫[CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase)。 A`CDaoTableDef`物件沒有記錄已記錄計數 屬性設定為 0。 使用附加的資料表或 ODBC 資料庫時`GetRecordCount`一律會傳回-1。

如需相關資訊，請參閱 DAO [說明] 中的 < RecordCount 屬性 >。

##  <a name="getsourcetablename"></a>  CDaoTableDef::GetSourceTableName

呼叫此成員函式，以擷取附加來源資料庫中資料表的名稱。

```
CString GetSourceTableName();
```

### <a name="return-value"></a>傳回值

A`CString`物件，指定連結的資料表或空字串的來源名稱，如果原生資料的資料表。

### <a name="remarks"></a>備註

附加的資料表是連結到 Microsoft Jet 資料庫的另一個資料庫中的資料表。 連結資料表的資料會保留在外部資料庫，其中由其他應用程式操作。

如需相關資訊，請參閱 DAO [說明] 中的 < SourceTableName 屬性 >。

##  <a name="getvalidationrule"></a>  CDaoTableDef::GetValidationRule

呼叫此成員函式可擷取 tabledef 的驗證規則。

```
CString GetValidationRule();
```

### <a name="return-value"></a>傳回值

A`CString`驗證欄位中的資料，因為它已變更或加入至資料表的物件。

### <a name="remarks"></a>備註

與更新作業所使用驗證規則。 如果 tabledef 包含驗證規則，該 tabledef 的更新必須符合預先決定的準則，才能在資料變更。 如果變更不符合準則，包含的值的例外狀況[GetValidationText](#getvalidationtext)就會擲回。 針對`CDaoTableDef`物件，這`CString`是唯讀的附加的資料表，以及基底資料表的讀取/寫入。

如需相關資訊，請參閱 DAO [說明] 中的 < ValidationRule 屬性 >。

##  <a name="getvalidationtext"></a>  CDaoTableDef::GetValidationText

呼叫此函式可擷取使用者輸入不符合驗證規則的資料時所顯示的字串。

```
CString GetValidationText();
```

### <a name="return-value"></a>傳回值

A`CString`物件，指定如果使用者輸入不符合驗證規則的資料，所顯示的文字。

### <a name="remarks"></a>備註

針對`CDaoTableDef`物件，這`CString`是唯讀的附加的資料表，以及基底資料表的讀取/寫入。

如需相關資訊，請參閱 DAO [說明] 中的 < 驗證文字屬性 >。

##  <a name="isopen"></a>  CDaoTableDef::IsOpen

呼叫此成員函式，以判斷是否`CDaoTableDef`物件目前是否開啟。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

非零`CDaoTableDef`物件已開啟; 否則為 0。

### <a name="remarks"></a>備註

##  <a name="m_pdatabase"></a>  CDaoTableDef::m_pDatabase

包含的指標[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)這份資料表的物件。

### <a name="remarks"></a>備註

##  <a name="m_pdaotabledef"></a>  CDaoTableDef::m_pDAOTableDef

包含 DAO tabledef 物件基礎的 OLE 介面的指標`CDaoTableDef`物件。

### <a name="remarks"></a>備註

如果您需要直接存取的 DAO 介面，請使用這個指標。

##  <a name="open"></a>  CDaoTableDef::Open

呼叫此成員函式，以開啟 tabledef 先前儲存在資料庫中的 TableDef 的集合。

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
指定的資料表名稱的字串指標。

### <a name="remarks"></a>備註

##  <a name="refreshlink"></a>  CDaoTableDef::RefreshLink

呼叫此成員函式，以更新連結資料表的連接資訊。

```
void RefreshLink();
```

### <a name="remarks"></a>備註

您可以變更附加的資料表的連接資訊藉由呼叫[SetConnect](#setconnect)在相對應`CDaoTableDef`物件，然後使用`RefreshLink`成員函式來更新的資訊。 當您呼叫`RefreshLink`，附加的資料表屬性不會變更。

若要強制已修改連接資訊才會生效，所有已開啟[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)必須關閉這個 tabledef 為基礎的物件。

如需相關資訊，請參閱 DAO [說明] 中的 < RefreshLink 方法 >。

##  <a name="setattributes"></a>  CDaoTableDef::SetAttributes

設定值，這個值，指出一或多個特性`CDaoTableDef`物件。

```
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>參數

*lAttributes*<br/>
所表示之表格的特性`CDaoTableDef`物件，而且可以是加總兩個常數：

|常數|描述|
|--------------|-----------------|
|`dbAttachExclusive`|使用 Microsoft Jet 資料庫引擎的資料庫，表示資料表是附加的資料表開啟以供獨佔使用。|
|`dbAttachSavePWD`|使用 Microsoft Jet 資料庫引擎的資料庫，表示儲存的使用者識別碼和密碼附加的資料表，使用的連接資訊。|
|`dbSystemObject`|表示資料表是由 Microsoft Jet 資料庫引擎提供的系統資料表。|
|`dbHiddenObject`|表示資料表是由 Microsoft Jet 資料庫引擎提供隱藏的資料表。|

### <a name="remarks"></a>備註

在設定多個屬性，您可以將它們合併加適當使用位元 OR 運算子的常數。 設定`dbAttachExclusive`在未附加的資料表會在命令提示字元中產生例外狀況。 結合下列的值也產生的例外狀況：

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

如需相關資訊，請參閱 DAO [說明] 中的 「 屬性屬性 」。

##  <a name="setconnect"></a>  CDaoTableDef::SetConnect

針對`CDaoTableDef`物件，表示附加的資料表，字串物件 （資料庫類型指定名稱和資料庫的路徑） 的一或兩個部分所組成。

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>參數

*lpszConnect*<br/>
指向的字串運算式，指定要傳遞至 ODBC 或可安裝 ISAM 驅動程式的其他參數。

### <a name="remarks"></a>備註

下表所示的路徑是包含資料庫檔案的目錄的完整路徑和前面必須有識別項"資料庫 ="。 在某些情況 （如 Microsoft Excel 與 Microsoft Jet 資料庫） 中，特定的檔案名稱包含在資料庫路徑引數。

> [!NOTE]
>  在表單的路徑陳述式中不包含等號前後的空白字元"資料庫 = 磁碟機：\\\path"。 這會導致擲回例外狀況和連線失敗。

下表顯示可能的資料庫類型和其對應的資料庫指定名稱和路徑：

|資料庫類型|指定名稱|路徑|
|-------------------|---------------|----------|
|使用 Jet 資料庫引擎的資料庫|"[ `database`];"|「 `drive`:\\\ *路徑*\\\ *filename*。MDB"|
|dBASE III|「 dBASE III;"|「 `drive`:\\\ *路徑*"|
|dBASE IV|"dBASE IV;"|「 `drive`:\\\ *路徑*"|
|dBASE 5|"dBASE 5.0;"|「 `drive`:\\\ *路徑*"|
|Paradox 3.x|"Paradox 3.x;"|「 `drive`:\\\ *路徑*"|
|Paradox 4.x|"Paradox 4.x;"|「 `drive`:\\\ *路徑*"|
|Paradox 5.x|"Paradox 5.x;"|「 `drive`:\\\ *路徑*"|
|Excel 3.0|「 Excel 3.0";|「 `drive`:\\\ *路徑*\\\ *filename*。XLS"|
|Excel 4.0|「 Excel 4.0;"|「 `drive`:\\\ *路徑*\\\ *filename*。XLS"|
|Excel 5.0 或 Excel 95|「 Excel 5.0 」;|「 `drive`:\\\ *路徑*\\\ *filename*。XLS"|
|Excel 97|「 Excel 8.0 」;|「 `drive`:\\\ *路徑*\ *filename*。XLS"|
|HTML 匯入|「 HTML 匯入 」;|「 `drive`:\\\ *路徑*\ *filename*"|
|HTML 匯出|[匯出 HTML];|「 `drive`:\\\ *路徑*"|
|文字|"Text";|「 磁碟機：\\\path"|
|ODBC|"ODBC;DATABASE = `database`;UID =*使用者*;PWD =*密碼*;資料來源名稱 = *datasourcename;* LOGINTIMEOUT =*秒;*"（這可能不是所有伺服器的完整連接字串，而只是範例。 它是非常重要有參數之間的空格。）|None|
|Exchange|「 交換;<br /><br /> MAPILEVEL = *folderpath*;<br /><br /> [TABLETYPE={ 0 &#124; 1 };]<br /><br /> [PROFILE= *profile*;]<br /><br /> [PWD= *password*;]<br /><br /> [DATABASE= `database`;]"|*「 磁碟機*:\\\ *路徑*\\\ *filename*。MDB"|

> [!NOTE]
>  從 DAO 3.5 開始，已不再支援 Btrieve。

您必須使用雙反斜線 (\\\\) 中的連接字串。 如果您修改了現有的連接使用的屬性`SetConnect`，您必須在後續呼叫[RefreshLink](#refreshlink)。 如果您要初始化使用的連接屬性`SetConnect`，您需要不呼叫`RefreshLink`，但如果您選擇這樣做，首先會附加 tabledef。

如果密碼是必要，但未提供，ODBC 驅動程式會顯示登入對話方塊第一次資料表存取時，另一次，如果連接關閉又重新開啟。

您可以設定的連接字串`CDaoTableDef`藉由提供的來源引數物件`Create`成員函式。 您可以檢查來判斷型別、 路徑、 使用者識別碼、 密碼或資料庫的 ODBC 資料來源的設定。 如需詳細資訊，請參閱特定驅動程式的文件。

如需相關資訊，請參閱 DAO [說明] 中的 [連接屬性]。

##  <a name="setname"></a>  CDaoTableDef::SetName

呼叫此成員函式設定的使用者定義資料表的名稱。

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpszName*<br/>
指向的字串運算式，指定資料表的名稱。

### <a name="remarks"></a>備註

名稱必須以字母開頭，而且可以包含最多 64 個字元。 它可以包含數字和底線字元，但不能包含標點符號或空格。

如需相關資訊，請參閱 DAO [說明] 中的 「 名稱屬性 」。

##  <a name="setsourcetablename"></a>  CDaoTableDef::SetSourceTableName

呼叫此成員函式，來指定附加的資料表名稱或名稱的基底資料表所在`CDaoTableDef`物件為基礎，存在於原始資料來源中。

```
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>參數

*lpszSrcTableName*<br/>
指標，在外部資料庫中指定的資料表名稱的字串運算式。 基底資料表中，設定為空字串 ("")。

### <a name="remarks"></a>備註

然後您必須呼叫[RefreshLink](#refreshlink)。 此屬性設定值是空的基底資料表和讀取/寫入連接的資料表或未附加至集合的物件。

如需相關資訊，請參閱 DAO [說明] 中的 < SourceTableName 屬性 >。

##  <a name="setvalidationrule"></a>  CDaoTableDef::SetValidationRule

呼叫此成員函式設定 tabledef 的驗證規則。

```
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>參數

*lpszValidationRule*<br/>
指標，會驗證作業的字串運算式。

### <a name="remarks"></a>備註

與更新作業所使用驗證規則。 如果 tabledef 包含驗證規則，該 tabledef 的更新必須符合預先決定的準則，才能在資料變更。 如果變更不符合準則，包含文字的例外狀況[GetValidationText](#getvalidationtext)隨即出現。

驗證只支援使用 Microsoft Jet 資料庫引擎的資料庫。 運算式無法參考使用者定義函數、 網域彙總函式、 SQL 彙總函式或查詢。 驗證規則`CDaoTableDef`物件可以參考該物件中的多個欄位。

例如，對於名為的欄位*hire_date*並*termination_date*，驗證規則可能是：

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

如需相關資訊，請參閱 DAO [說明] 中的 < ValidationRule 屬性 >。

##  <a name="setvalidationtext"></a>  CDaoTableDef::SetValidationText

呼叫此成員函式設定的驗證規則的例外狀況文字`CDaoTableDef`具有 Microsoft Jet database engine 所支援的基礎基底資料表的物件。

```
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>參數

*lpszValidationText*<br/>
字串運算式，指定如果輸入資料顯示的文字指標無效。

### <a name="remarks"></a>備註

您無法設定驗證的文字附加的資料表。

如需相關資訊，請參閱 DAO [說明] 中的 < 驗證文字屬性 >。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)
