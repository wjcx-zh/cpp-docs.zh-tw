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
ms.openlocfilehash: 063d0b795c7e4f6af901f52563295883ef81de7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377130"
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
|[CDaoTableDef:cdaoTableDef](#cdaotabledef)|建構 `CDaoTableDef` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDaoTableDef::附加](#append)|向資料庫添加新錶。|
|[CDaoTableDef:可以更新](#canupdate)|如果可以更新表(您可以修改欄位或表屬性的定義),則返回非零。|
|[CDaoTableDef:關閉](#close)|關閉打開的表def。|
|[CDaoTableDef:建立](#create)|建立表,該表可以使用[附加程式](#append)添加到資料庫中。|
|[CDaoTableDef:建立欄位](#createfield)|呼叫以建立表的欄位。|
|[CDaoTableDef:建立索引](#createindex)|調用以創建表的索引。|
|[CDaoTableDef::DeleteField](#deletefield)|呼叫以從表中刪除欄位。|
|[CDaoTableDef::DeleteIndex](#deleteindex)|呼叫以從表中刪除索引。|
|[CDaoTableDef:取得屬性](#getattributes)|返回指示`CDaoTableDef`物件的一個或多個特徵的值。|
|[CDaoTableDef:取得連線](#getconnect)|返回提供有關表源的資訊的值。|
|[CDaoTableDef:取得日期建立](#getdatecreated)|返回創建物件基礎的基表的`CDaoTableDef`日期和時間。|
|[CDaoTableDef:取得更新日期](#getdatelastupdated)|返回對基表設計進行的最新更改的日期和時間。|
|[CDaoTableDef:取得欄位計數](#getfieldcount)|返回表示表中的欄位數的值。|
|[CDaoTableDef:取得菲爾德資訊](#getfieldinfo)|返回有關表中欄位的特定類型的資訊。|
|[CDaoTableDef:取得索引計數](#getindexcount)|返回表的索引數。|
|[CDaoTableDef:取得索引資訊](#getindexinfo)|返回有關表索引的特定類型的資訊。|
|[CDaoTableDef:取得名稱](#getname)|傳回表的使用者定義名稱。|
|[CDaoTableDef:取得記錄計數](#getrecordcount)|返回表中的記錄數。|
|[CDaoTableDef:取得來源表名稱](#getsourcetablename)|返回指定源資料庫中附加表名稱的值。|
|[CDaoTableDef:取得認證規則](#getvalidationrule)|返回一個值,用於在欄位中驗證數據在更改或添加到表中時。|
|[CDaoTableDef:取得認證文字](#getvalidationtext)|返回一個值,該值指定如果 Field 物件的值不符合指定的驗證規則,則應用程式顯示的消息文本。|
|[CDaoTableDef:即開放](#isopen)|如果表處於打開狀態,則返回非零。|
|[CDaoTableDef::開啟](#open)|開啟存儲在資料庫的 TableDef 集合中的現有表def。|
|[CDaoTableDef::刷新連結](#refreshlink)|更新附加表的連接資訊。|
|[CDaoTableDef:設定屬性](#setattributes)|設置指示`CDaoTableDef`物件的一個或多個特徵的值。|
|[CDaoTableDef:set連接](#setconnect)|設置提供有關表源的資訊的值。|
|[CDaoTableDef:set 名稱](#setname)|設置表的名稱。|
|[CDaoTableDef::設定原始表名稱](#setsourcetablename)|設置指定源資料庫中附加表名稱的值。|
|[CDaoTableDef:設定驗證規則](#setvalidationrule)|設置一個值,在欄位中的數據被更改或添加到表中時對其進行驗證。|
|[CDaoTableDef:set 驗證文字](#setvalidationtext)|設定一個值,用於指定如果 Field 物件的值不符合指定的驗證規則,則應用程式顯示的消息文本。|

### <a name="public-data-members"></a>公用資料成員

|名稱|描述|
|----------|-----------------|
|[CDaoTableDef:m_pDAOTableDef](#m_pdaotabledef)|指向 tabledef 物件基礎的 DAO 介面的指標。|
|[CDaoTableDef:m_pDatabase](#m_pdatabase)|此表的源資料庫。|

## <a name="remarks"></a>備註

每個 DAO 資料庫物件維護一個集合,稱為 TableDefs,其中包含所有保存的 DAO 表def物件。

使用`CDaoTableDef`物件操作表定義。 例如，您可以：

- 檢查資料庫中任何本地表、附加表或外部表的欄位和索引結構。

- 調用`SetConnect``SetSourceTableName`附加 表 和成員函數`RefreshLink`,並使用成員函數更新到附加表的連接。

- 呼叫`CanUpdate`成員函數以確定是否可以編輯表中的欄位定義。

- 使用`GetValidationRule`和`SetValidationRule`和`GetValidationText``SetValidationText`成員函數獲取或設定驗證條件。

- 使用`Open`成員函數創建表、動態集或快照類型`CDaoRecordset`物件。

    > [!NOTE]
    >  DAO 資料庫類不同於基於開放資料庫連接 (ODBC) 的 MFC 資料庫類。 所有 DAO 資料庫類名稱都有「CDao」首碼。 您仍可以使用 DAO 類訪問 ODBC 資料來源;DAO 類通常提供卓越的功能,因為它們特定於 Microsoft Jet 資料庫引擎。

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>使用 tabledef 物件處理現有表或建立新表

1. 在所有情況下,首先構造一個`CDaoTableDef`物件,提供指向表所屬的[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)物件的指標。

1. 然後執行以下操作,具體取決於所需內容:

   - 要使用現有的已保存表,請調用 tabledef 物件的[Open](#open)成員函數,提供已保存表的名稱。

   - 要建立新表,請調用 tabledef 物件的[「創建](#create)成員」函數,提供表的名稱。 呼叫[CreateField](#createfield)和[CreateIndex](#createindex)將欄位和索引添加到表中。

   - 呼叫[附加程式](#append),透過將表追加到資料庫的 TableDefs 集合來儲存表。 `Create`將表def置於開啟狀態,因此在呼叫`Create`後不呼`Open`叫 。

        > [!TIP]
        >  創建保存的表的最簡單方法是創建它們並使用 Microsoft Access 將它們存儲在資料庫中。 然後,您可以在 MFC 代碼中打開並使用它們。

要使用已打開或創建的表def物件,請建立並打開`CDaoRecordset`物件,`dbOpenTable`在*nOpenType*參數中指定具有值的表def的名稱。

要使用 tabledef`CDaoRecordset`物件建立 物件,通常建立或打開如上所述的表def,然後構造記錄集物件,在調用[CDaoRecordset:::打開](../../mfc/reference/cdaorecordset-class.md#open)時將指標傳遞給表def物件。 傳遞的表def必須處於打開狀態。 有關詳細資訊,請參閱類[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)。

使用 tabledef 物件完成後,呼叫其[Close](../../mfc/reference/cdaorecordset-class.md#close)成員函數;如果使用表def 物件,則調用其 Close 成員函數。然後銷毀表def物件。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>需求

**標題:** afxdao.h

## <a name="cdaotabledefappend"></a><a name="append"></a>CDaoTableDef::附加

呼叫[Create](#create)後呼叫此成員函數以建立新的表def物件以將表def儲存在資料庫中。

```
virtual void Append();
```

### <a name="remarks"></a>備註

函數將物件追加到資料庫的 TableDefs 集合中。 在定義 tabledef 時,可以透過不追加表定義表def,但如果要儲存和使用表def,則`Append`必須呼叫 。

> [!NOTE]
> 如果嘗試追加未命名的表def(包含空字串或空字串),MFC將引發異常。

有關相關信息,請參閱 DAO 説明中的主題"附加方法"。

## <a name="cdaotabledefcanupdate"></a><a name="canupdate"></a>CDaoTableDef:可以更新

調用此成員函數以確定是否可以更改`CDaoTableDef`物件基礎表的定義。

```
BOOL CanUpdate();
```

### <a name="return-value"></a>傳回值

如果可以修改表結構(架構)(模式)(添加或刪除欄位和索引),則非零,否則為 0。

### <a name="remarks"></a>備註

默認情況下,可以更新物件基礎的新`CDaoTableDef`創建的表,並且無法更新物件基礎的附加`CDaoTableDef`表。 物件`CDaoTableDef`可能是可向上的,即使生成的記錄集不可升。

有關相關信息,請參閱 DAO 説明中的主題"可使用屬性」。

## <a name="cdaotabledefcdaotabledef"></a><a name="cdaotabledef"></a>CDaoTableDef:cdaoTableDef

建構 `CDaoTableDef` 物件。

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>參數

*p 資料庫*<br/>
指向[CDao 資料庫](../../mfc/reference/cdaodatabase-class.md)物件的指標。

### <a name="remarks"></a>備註

建構物件後,必須呼叫["或](#create)["打開](#open)"成員函數。 完成該物件後,必須調用其[Close](#close)成員函數並銷`CDaoTableDef`毀該 物件。

## <a name="cdaotabledefclose"></a><a name="close"></a>CDaoTableDef:關閉

調用此成員函數以關閉和釋放表def物件。

```
virtual void Close();
```

### <a name="remarks"></a>備註

通常在調用`Close`後,如果表def物件是使用**new**分配的,則刪除該物件。

呼叫 後可以再次呼`Close`叫[Open。](#open) 這允許您重用表def物件。

有關相關信息,請參閱 DAO 説明中的主題" 關閉方法"

## <a name="cdaotabledefcreate"></a><a name="create"></a>CDaoTableDef:建立

呼叫此成員函數以創建新的儲存表。

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
指向包含表名稱的字串的指標。

*l 屬性*<br/>
對應於表def物件表示的表特徵的值。 您可以使用位-OR 組合以下任一常量:

|持續性|描述|
|--------------|-----------------|
|`dbAttachExclusive`|對於使用 Microsoft Jet 資料庫引擎的資料庫,指示該表是打開供獨佔用途的附加表。|
|`dbAttachSavePWD`|對於使用 Microsoft Jet 資料庫引擎的資料庫,指示附加表的使用者 ID 和密碼與連接資訊一起保存。|
|`dbSystemObject`|指示該表是Microsoft Jet資料庫引擎提供的系統表。|
|`dbHiddenObject`|指示該表是Microsoft Jet資料庫引擎提供的隱藏表。|

*lpszSrcTable*<br/>
指向包含原始表名稱的字串的指標。 預設情況下,此值初始化為 NULL。

*lpszConnect*<br/>
指向包含預設連接字串的字串的指標。 預設情況下,此值初始化為 NULL。

### <a name="remarks"></a>備註

命名表def後,可以調用[Append](#append)將表def保存在資料庫的TableDefs集合中。 呼叫`Append`後,tabledef 處於開啟狀態,您可以使用它創建[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)物件。

有關相關信息,請參閱 DAO 説明中的主題"創建TableDef 方法"。

## <a name="cdaotabledefcreatefield"></a><a name="createfield"></a>CDaoTableDef:建立欄位

調用此成員函數以向表添加欄位。

```
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
指定此欄位名稱的字串表示式的指標。

*nType*<br/>
指示欄位數據類型的值。 該設定可以是以下值之一:

|類型|大小 (位元組)|描述|
|----------|--------------------|-----------------|
|`dbBoolean`|1 個位元組|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|貨幣 ( [COle 金錢](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|FLOAT|
|`dbDouble`|8|double|
|`dbDate`|8|日期/時間 ( [COleDatetime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|文字 ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|長二進位 (OLE 物件[)、CLongBinary](../../mfc/reference/clongbinary-class.md)或[CBytearray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|備忘錄 ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
指示包含文本或包含文本或數值的欄位的最大大小(以位元組為單位)的值。 除了文字欄位外,所有欄位都忽略*lSize*參數。

*l 屬性*<br/>
與欄位的特徵對應的值,可以使用位-OR 進行組合。

|持續性|描述|
|--------------|-----------------|
|`dbFixedField`|欄位大小是固定的(數位欄位的預設值)。|
|`dbVariableField`|欄位大小是可變的(僅限文字欄位)。|
|`dbAutoIncrField`|新記錄的欄位值將自動遞增為無法更改的唯一長整數。 僅支援 Microsoft Jet 資料庫表。|
|`dbUpdatableField`|可以更改欄位值。|
|`dbDescending`|該欄位按降序(Z - A 或 100 - 0)順序排序(僅適用於 Index 物件的欄位集合中的欄位物件)。 如果省略此常量,則欄位按升序(A - Z 或 0 - 100)順序排序(預設值)。|

*菲爾德資訊*<br/>
對[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構的引用。

### <a name="remarks"></a>備註

將`DAOField`創建 (OLE) 物件並將其追加到 (OLE)`DAOTableDef`物件的欄位集合中。 除了用於檢查物件屬性外,您還可以使用`CDaoFieldInfo`建構輸入參數以在 tabledef 中建立新欄位。 的第`CreateField`一個版本更易於使用,但如果要進行更精細的控制,可以`CreateField`使用的第二個版本,該版本需要一`CDaoFieldInfo`個 參數。

如果使用此參數的版本`CreateField`,`CDaoFieldInfo`則必須仔細`CDaoFieldInfo`設定 結構的每個以下成員:

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

其餘成員`CDaoFieldInfo`應設置為 0、FALSE 或空字串(適用於成員**0**)`CDaoException`或可能發生。

有關相關信息,請參閱 DAO 説明中的主題"創建欄位方法"。

## <a name="cdaotabledefcreateindex"></a><a name="createindex"></a>CDaoTableDef:建立索引

調用此函數以向表添加索引。

```
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>參數

*索引資訊*<br/>
對[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構的引用。

### <a name="remarks"></a>備註

索引指定從資料庫表訪問的記錄的順序,以及是否接受重複記錄。 索引還提供對數據的有效訪問。

您不必為表創建索引,但在大型未編製索引的表中,訪問特定記錄或創建記錄集可能需要很長時間。 另一方面,創建過多的索引會降低更新、追加和刪除操作的速度,因為所有索引都會自動更新。 在決定要創建哪些索引時,請考慮這些因素。

必須設定結構的`CDaoIndexInfo`以下成員:

- `m_strName`必須提供名稱。

- `m_pFieldInfos`必須指向結構陣列`CDaoIndexFieldInfo`。

- `m_nFields`必須指定結構陣列的欄位數`CDaoFieldInfo`。

如果設置為 FALSE,將忽略其餘成員。 此外,在`m_lDistinctCount`創建索引期間將忽略該成員。

## <a name="cdaotabledefdeletefield"></a><a name="deletefield"></a>CDaoTableDef::DeleteField

呼叫此成員函數以刪除欄位並使它無法訪問。

```
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
指向字串表達式的指標,該指標運算式是現有欄位的名稱。

*nIndex*<br/>
表的零基欄位集合中的欄位索引,用於按索引查找。

### <a name="remarks"></a>備註

您可以在尚未追加到資料庫的新物件上或[CanUpdate](#canupdate)傳回非零時使用此成員函數。

有關相關信息,請參閱 DAO 説明中的主題"刪除方法"。

## <a name="cdaotabledefdeleteindex"></a><a name="deleteindex"></a>CDaoTableDef::DeleteIndex

呼叫此成員函數以刪除基礎表中的索引。

```
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
指向字串表達式的指標,該指標運算式是現有索引的名稱。

*nIndex*<br/>
資料庫的零基表Defs集合中索引對象的陣列索引,用於按索引查找。

### <a name="remarks"></a>備註

您可以在尚未追加到資料庫的新物件上或[CanUpdate](#canupdate)傳回非零時使用此成員函數。

有關相關信息,請參閱 DAO 説明中的主題"刪除方法"。

## <a name="cdaotabledefgetattributes"></a><a name="getattributes"></a>CDaoTableDef:取得屬性

對於`CDaoTableDef`物件,返回值指定由物件表示`CDaoTableDef`的 表的特徵,並且可以是這些常量的總和:

```
long GetAttributes();
```

### <a name="return-value"></a>傳回值

返回指示`CDaoTableDef`物件的一個或多個特徵的值。

### <a name="remarks"></a>備註

|持續性|描述|
|--------------|-----------------|
|`dbAttachExclusive`|對於使用 Microsoft Jet 資料庫引擎的資料庫,指示該表是打開供獨佔用途的附加表。|
|`dbAttachSavePWD`|對於使用 Microsoft Jet 資料庫引擎的資料庫,指示附加表的使用者 ID 和密碼與連接資訊一起保存。|
|`dbSystemObject`|指示該表是Microsoft Jet資料庫引擎提供的系統表。|
|`dbHiddenObject`|指示該表是Microsoft Jet資料庫引擎提供的隱藏表。|
|`dbAttachedTable`|指示表是來自非 ODBC 資料庫(如 Paradox 資料庫)的附加表。|
|`dbAttachedODBC`|指示表是來自 ODBC 資料庫(如 Microsoft SQL Server)的附加表。|

系統表是 Microsoft Jet 資料庫引擎創建的包含各種內部資訊的表。

隱藏表是為 Microsoft Jet 資料庫引擎臨時使用而創建的表。

有關相關信息,請參閱 DAO 説明中的主題「屬性屬性」。

## <a name="cdaotabledefgetconnect"></a><a name="getconnect"></a>CDaoTableDef:取得連線

呼叫此成員函數以獲取資料來源的連接字串。

```
CString GetConnect();
```

### <a name="return-value"></a>傳回值

包含`CString`表的路徑和資料庫類型的物件。

### <a name="remarks"></a>備註

對於表示`CDaoTableDef`附加表的物件`CString`, 該物件由一個或兩個部分(資料庫類型指定器和資料庫路徑)組成。

下表所示的路徑是包含資料庫檔的目錄的完整路徑,前面必須前面有標識符"DATABASE_"。 在某些情況下(與 Microsoft Jet 和 Microsoft Excel 資料庫一樣),資料庫路徑參數中包含特定的檔名。

[CDaoTableDef:setConnect](#setconnect)中的表顯示可能的資料庫類型及其相應的資料庫指定和路徑:

對於 Microsoft Jet 資料庫基錶,指定器是一個空字串 ("")。

如果需要密碼但未提供密碼,ODBC 驅動程式會在首次訪問表時顯示一個登錄對話方塊;如果連接已關閉並重新打開,則再次顯示登錄對話方塊。 如果附加的表具有該`dbAttachSavePWD`屬性,則重新打開表時不會顯示登錄提示。

有關相關信息,請參閱 DAO 説明中的主題"連接屬性」。。

## <a name="cdaotabledefgetdatecreated"></a><a name="getdatecreated"></a>CDaoTableDef:取得日期建立

呼叫此函數以確定創建物件基礎的表的`CDaoTableDef`日期和時間。

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>傳回值

包含創建物件基礎`CDaoTableDef`表的日期和時間的值。

### <a name="remarks"></a>備註

日期和時間設置派生自創建或上次更新基表的計算機。 在多用戶環境中,使用者應直接從文件伺服器獲取這些設置,以避免差異;也就是說,所有用戶端都應使用"標準"時間源 - 可能來自一台伺服器。

有關相關信息,請參閱 DAO 説明中的主題"創建日期,上次更新的屬性"。

## <a name="cdaotabledefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoTableDef:取得更新日期

調用此函數以確定上次更新物件基礎的表的`CDaoTableDef`日期和時間。

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>傳回值

包含上次更新物件基礎表的`CDaoTableDef`日期和時間的值。

### <a name="remarks"></a>備註

日期和時間設置派生自創建或上次更新基表的計算機。 在多用戶環境中,使用者應直接從文件伺服器獲取這些設置,以避免差異;也就是說,所有用戶端都應使用"標準"時間源 - 可能來自一台伺服器。

有關相關信息,請參閱 DAO 説明中的主題"創建日期,上次更新的屬性"。

## <a name="cdaotabledefgetfieldcount"></a><a name="getfieldcount"></a>CDaoTableDef:取得欄位計數

調用此成員函數以檢索表中定義的欄位數。

```
short GetFieldCount();
```

### <a name="return-value"></a>傳回值

表中的欄位數。

### <a name="remarks"></a>備註

如果其值為 0,則集合中沒有物件。

有關相關信息,請參閱 DAO 説明中的主題"計數屬性」。。

## <a name="cdaotabledefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoTableDef:取得菲爾德資訊

呼叫此成員函數以獲取有關表def中定義的欄位的各種資訊。

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
表的零基欄位集合中欄位物件的索引,用於按索引查找。

*菲爾德資訊*<br/>
對[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構的引用。

*dwInfoOptions*<br/>
指定要檢索的欄位的資訊的選項。 此處列出可用的選項以及它們導致函數傳回的內容:

- `AFX_DAO_PRIMARY_INFO`( 預設 )名稱、類型、大小、屬性。 使用此選項可獲得最快的性能。

- `AFX_DAO_SECONDARY_INFO`主要資訊,加上:序號位置、必需位置、允許零長度、分詞順序、外名、原始欄位、源表

- `AFX_DAO_ALL_INFO`主要和輔助資訊,以及:驗證規則、驗證文本、預設值

*lpsz名稱*<br/>
指向欄位物件名稱的指標,用於按名稱查找。 該名稱是一個字串,最多 64 個字元,用於唯一命名字段。

### <a name="remarks"></a>備註

函數的一個版本允許您按索引查找欄位。 另一個版本允許您按名稱查找欄位。

有關返回的信息的說明,請參閱[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md)結構。 此結構的成員對應於*dwInfoOptions*描述中列出的資訊項。 當您在一個級別請求資訊時,您也獲取任何先前級別的資訊。

有關相關信息,請參閱 DAO 説明中的主題「屬性屬性」。

## <a name="cdaotabledefgetindexcount"></a><a name="getindexcount"></a>CDaoTableDef:取得索引計數

調用此成員函數以獲取表的索引數。

```
short GetIndexCount();
```

### <a name="return-value"></a>傳回值

表的索引數。

### <a name="remarks"></a>備註

如果其值為 0,則集合中沒有索引。

有關相關信息,請參閱 DAO 説明中的主題"計數屬性」。。

## <a name="cdaotabledefgetindexinfo"></a><a name="getindexinfo"></a>CDaoTableDef:取得索引資訊

調用此成員函數以獲取有關表def中定義的索引的各種資訊。

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
表中的零基索引集合中索引物件的數位索引,用於按其在集合中的位置進行查找。

*索引資訊*<br/>
對[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構的引用。

*dwInfoOptions*<br/>
指定要檢索的索引的資訊的選項。 此處列出可用的選項以及它們導致函數傳回的內容:

- `AFX_DAO_PRIMARY_INFO`名稱,欄位資訊,欄位。 使用此選項可獲得最快的性能。

- `AFX_DAO_SECONDARY_INFO`主要資訊,加上:主資訊、唯一資訊、群集、忽略空值、必需資訊、外資訊

- `AFX_DAO_ALL_INFO`主要和次要資訊,加上:不同的計數

*lpsz名稱*<br/>
指向索引物件名稱的指標,用於按名稱查找。

### <a name="remarks"></a>備註

函數的一個版本允許您按索引在集合中的位置查找索引。 另一個版本允許您按名稱查找索引。

有關返回的資訊的說明,請參閱[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md)結構。 此結構的成員對應於*dwInfoOptions*描述中列出的資訊項。 當您在一個級別請求資訊時,您也獲取任何先前級別的資訊。

有關相關信息,請參閱 DAO 説明中的主題「屬性屬性」。

## <a name="cdaotabledefgetname"></a><a name="getname"></a>CDaoTableDef:取得名稱

呼叫此成員函數以獲取基礎表的使用者定義名稱。

```
CString GetName();
```

### <a name="return-value"></a>傳回值

表的使用者定義名稱。

### <a name="remarks"></a>備註

此名稱以字母開頭,最多可包含 64 個字元。 它可以包括數位和下劃線字元,但不能包括標點符號或空格。

有關相關信息,請參閱 DAO 説明中的主題"名稱屬性"。

## <a name="cdaotabledefgetrecordcount"></a><a name="getrecordcount"></a>CDaoTableDef:取得記錄計數

調用此成員函數以瞭解`CDaoTableDef`物件中有多少條記錄。

```
long GetRecordCount();
```

### <a name="return-value"></a>傳回值

在 tabledef 物件中訪問的記錄數。

### <a name="remarks"></a>備註

調用`GetRecordCount`表`CDaoTableDef`類型 物件反映表中記錄的近似數量,並且隨著表記錄的添加和刪除而立即受到影響。 回滾的事務將作為紀錄計數的一部份出現,直到您呼叫[CDaoWorkSpace:壓縮資料庫](../../mfc/reference/cdaoworkspace-class.md#compactdatabase)。 沒有`CDaoTableDef`記錄的物件的記錄計數屬性設置為 0。 使用附加的表或 ODBC`GetRecordCount`資料庫 時,始終返回 -1。

有關相關信息,請參閱 DAO 説明中的主題"記錄計數屬性」。。

## <a name="cdaotabledefgetsourcetablename"></a><a name="getsourcetablename"></a>CDaoTableDef:取得來源表名稱

調用此成員函數以檢索源資料庫中附加表的名稱。

```
CString GetSourceTableName();
```

### <a name="return-value"></a>傳回值

指定`CString`附加表的來源名稱的物件,或指定本機資料表的空字串。

### <a name="remarks"></a>備註

附加的表是另一個資料庫中連結到 Microsoft Jet 資料庫的表。 附加表的數據將保留在外部資料庫中,可以由其他應用程式對其進行操作。

有關相關信息,請參閱 DAO 説明中的主題「源表名稱屬性」。

## <a name="cdaotabledefgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoTableDef:取得認證規則

調用此成員函數以檢索表def的驗證規則。

```
CString GetValidationRule();
```

### <a name="return-value"></a>傳回值

在`CString`欄位中更改資料或添加到表中時驗證資料的物件。

### <a name="remarks"></a>備註

驗證規則用於與更新操作有關。 如果 tabledef 包含驗證規則,則對該表def 的更新必須在更改數據之前匹配預定的條件。 如果更改與條件不匹配,則會引發包含[Get驗證文本](#getvalidationtext)值的異常。 對於`CDaoTableDef`物件,`CString`這是附加表的唯讀表和基表的讀/寫。

有關相關信息,請參閱 DAO 説明中的主題"驗證規則屬性」。

## <a name="cdaotabledefgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoTableDef:取得認證文字

呼叫此函數以檢索在使用者輸入與驗證規則不匹配的數據時顯示的字串。

```
CString GetValidationText();
```

### <a name="return-value"></a>傳回值

指定`CString`使用者輸入的數據與驗證規則不匹配時顯示的文本的物件。

### <a name="remarks"></a>備註

對於`CDaoTableDef`物件,`CString`這是附加表的唯讀表和基表的讀/寫。

有關相關信息,請參閱 DAO 説明中的主題"驗證文本屬性」。。

## <a name="cdaotabledefisopen"></a><a name="isopen"></a>CDaoTableDef:即開放

調用此成員函數以確定`CDaoTableDef`物件當前是否打開。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>傳回值

如果對象處於`CDaoTableDef`打開 狀態,則非零;否則 0。

### <a name="remarks"></a>備註

## <a name="cdaotabledefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoTableDef:m_pDatabase

包含指向此表的[CDao 資料庫](../../mfc/reference/cdaodatabase-class.md)物件的指標。

### <a name="remarks"></a>備註

## <a name="cdaotabledefm_pdaotabledef"></a><a name="m_pdaotabledef"></a>CDaoTableDef:m_pDAOTableDef

包含指向物件基礎的 DAO 表def物件的 OLE 介面的`CDaoTableDef`指標。

### <a name="remarks"></a>備註

如果需要直接訪問 DAO 介面,請使用此指標。

## <a name="cdaotabledefopen"></a><a name="open"></a>CDaoTableDef::開啟

呼叫此成員函數以打開以前儲存在資料庫的 TableDef 集合中的表def。

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
指向指定表名稱的字串的指標。

### <a name="remarks"></a>備註

## <a name="cdaotabledefrefreshlink"></a><a name="refreshlink"></a>CDaoTableDef::刷新連結

調用此成員函數以更新附加表的連接資訊。

```
void RefreshLink();
```

### <a name="remarks"></a>備註

透過在相應`CDaoTableDef`物件上調用[SetConnect,](#setconnect)然後使用成員函數`RefreshLink`更新資訊, 可以更改附加表的連接資訊。 調用`RefreshLink`時,不會更改附加表的屬性。

要強制修改後的連線資訊生效,必須關閉基於此表def的所有開啟[的 CDaoRecordset 物件](../../mfc/reference/cdaorecordset-class.md)。

有關相關信息,請參閱 DAO 説明中的主題"刷新連結方法」。。

## <a name="cdaotabledefsetattributes"></a><a name="setattributes"></a>CDaoTableDef:設定屬性

設置指示`CDaoTableDef`物件的一個或多個特徵的值。

```
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>參數

*l 屬性*<br/>
由`CDaoTableDef`物件表示的表的特徵,可以是這些常量的總和:

|持續性|描述|
|--------------|-----------------|
|`dbAttachExclusive`|對於使用 Microsoft Jet 資料庫引擎的資料庫,指示該表是打開供獨佔用途的附加表。|
|`dbAttachSavePWD`|對於使用 Microsoft Jet 資料庫引擎的資料庫,指示附加表的使用者 ID 和密碼與連接資訊一起保存。|
|`dbSystemObject`|指示該表是Microsoft Jet資料庫引擎提供的系統表。|
|`dbHiddenObject`|指示該表是Microsoft Jet資料庫引擎提供的隱藏表。|

### <a name="remarks"></a>備註

設置多個屬性時,可以使用位-OR 運算符求和適當的常量來組合它們。 在`dbAttachExclusive`未連接的表上設置會產生異常。 組合以下值也會產生異常:

- **dbAttach 獨家&#124; dbattachODBC**

- **dbAttachsavePWD&#124; dbattach錶**

有關相關信息,請參閱 DAO 説明中的主題「屬性屬性」。

## <a name="cdaotabledefsetconnect"></a><a name="setconnect"></a>CDaoTableDef:set連接

對於表示`CDaoTableDef`附加表的物件,字串物件由一個或兩個部分組成(資料庫類型指定器和資料庫路徑)。

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>參數

*lpszConnect*<br/>
指向字串表示式的指標,用於指定要傳遞給 ODBC 或可安裝 ISAM 驅動程式的其他參數。

### <a name="remarks"></a>備註

下表所示的路徑是包含資料庫檔的目錄的完整路徑,前面必須前面有標識符"DATABASE_"。 在某些情況下(與 Microsoft Jet 和 Microsoft Excel 資料庫一樣),資料庫路徑參數中包含特定的檔名。

> [!NOTE]
> 請勿在窗體「DATABASE_驅動器:_path」\\的等號登錄路徑語句周圍包含空格。 這將導致引發異常和連接失敗。

下表顯示了可能的資料庫類型及其相應的資料庫指定器和路徑:

|資料庫類型|規範|Path|
|-------------------|---------------|----------|
|使用 Jet 資料庫引擎的資料庫|"[ `database`];"|`drive`\\\  : 路徑 檔名 。\\ \  * * * *MDB"|
|dBASE III|"dBASE III;"|`drive` \\" \ :*路徑*"|
|dBASE IV|"dBASE IV;"|`drive` \\" \ :*路徑*"|
|dBASE 5|"dBASE 5.0;"|`drive` \\" \ :*路徑*"|
|已比音效 3.x|"悖論 3.x;"|`drive` \\" \ :*路徑*"|
|已比音效 4.x|"悖論 4.x;"|`drive` \\" \ :*路徑*"|
|已比音效 5.x|"悖論 5.x;"|`drive` \\" \ :*路徑*"|
|Excel 3.0|"Excel 3.0;"|`drive`\\\  : 路徑 檔名 。\\ \  * * * *XLS"|
|Excel 4.0|"Excel 4.0;"|`drive`\\\  : 路徑 檔名 。\\ \  * * * *XLS"|
|Excel 5.0 或 Excel 95|"Excel 5.0;"|`drive`\\\  : 路徑 檔名 。\\ \  * * * *XLS"|
|Excel 97|"Excel 8.0;"|\  `drive`: 路徑檔\\名\ *filename**path*。XLS"|
|HTML 匯入|"HTML 導入;"|`drive` \\:\ \ 路徑*檔名**path*"|
|HTML 匯出|"HTML 匯出;"|`drive` \\" \ :*路徑*"|
|Text|"文字;"|"驅動器:\path"\\|
|ODBC|"ODBC;資料庫* `database`;UID+*使用者*;PWD=*密碼*;DSN=*資料源名稱;* 登錄時間+*秒數;*"(這可能不是所有伺服器的完整連接字串;它只是一個示例。 參數之間不要有空格是非常重要的。|None|
|Exchange|交換;<br /><br /> MAPILEVEL=*資料夾路徑*;<br /><br /> [表類型] 0 &#124; 1 {;}<br /><br /> 【*設定檔;]*<br /><br /> [PWD]*密碼*;]<br /><br /> [資料庫];" `database`|*磁碟*\\\ *路徑*\\\ *檔名*。MDB"|

> [!NOTE]
> 從 DAO 3.5 起,Btrieve 不再受支援。

必須在連接字串中使用雙反斜槓\\\\( ) 。 如果已使用`SetConnect`修改了現有連線的屬性,則必須隨後呼叫[RefreshLink](#refreshlink)。 如果使用 初始化連接`SetConnect`屬性 ,則不需要`RefreshLink`調用 ,但如果選擇這樣做,請先追加表def。

如果需要密碼但未提供密碼,ODBC 驅動程式會在首次訪問表時顯示一個登錄對話方塊;如果連接已關閉並重新打開,則再次顯示登錄對話方塊。

可以通過`Create`向成員函數提供源參數`CDaoTableDef`來 設置物件的連接字串。 您可以檢查該設定以確定資料庫的類型、路徑、使用者 ID、密碼或 ODBC 數據來源。 有關詳細資訊,請參閱特定驅動程序的文檔。

有關相關信息,請參閱 DAO 説明中的主題"連接屬性」。。

## <a name="cdaotabledefsetname"></a><a name="setname"></a>CDaoTableDef:set 名稱

呼叫此成員函數以設置表的使用者定義的名稱。

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>參數

*lpsz名稱*<br/>
指向指定表名稱的字串表示式的指標。

### <a name="remarks"></a>備註

名稱必須以字母開頭,最多包含 64 個字元。 它可以包括數位和下劃線字元,但不能包括標點符號或空格。

有關相關信息,請參閱 DAO 説明中的主題"名稱屬性"。

## <a name="cdaotabledefsetsourcetablename"></a><a name="setsourcetablename"></a>CDaoTableDef::設定原始表名稱

呼叫此成員函數以指定附加表的名稱或`CDaoTableDef`物件所基於的基表的名稱,因為它存在於資料的原始源中。

```
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>參數

*lpszSrcTable 名稱*<br/>
指向在外部資料庫中指定表名稱的字串表達式的指標。 對於基表,該設置為空字串 (")。

### <a name="remarks"></a>備註

然後,您必須呼叫[刷新連結](#refreshlink)。 此屬性設置對於基表為空,對於附加的表或未追加到集合的物件,則讀/寫。

有關相關信息,請參閱 DAO 説明中的主題「源表名稱屬性」。

## <a name="cdaotabledefsetvalidationrule"></a><a name="setvalidationrule"></a>CDaoTableDef:設定驗證規則

調用此成員函數以設置表def的驗證規則。

```
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>參數

*lpsz 驗證規則*<br/>
指向驗證操作的字串表達式的指標。

### <a name="remarks"></a>備註

驗證規則用於與更新操作有關。 如果 tabledef 包含驗證規則,則對該表def 的更新必須在更改數據之前匹配預定的條件。 如果更改與條件不匹配,將顯示包含[Get驗證文本文本](#getvalidationtext)的異常。

僅支援使用 Microsoft Jet 資料庫引擎的資料庫驗證。 表達式不能引用使用者定義的函數、域聚合函數、SQL 聚合函數或查詢。 `CDaoTableDef`對象的驗證規則可以引用該物件的多個字段。

例如,對於名為*hire_date*和*termination_date*的欄位,驗證規則可能是:

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

有關相關信息,請參閱 DAO 説明中的主題"驗證規則屬性」。

## <a name="cdaotabledefsetvalidationtext"></a><a name="setvalidationtext"></a>CDaoTableDef:set 驗證文字

呼叫此成員函數為具有 Microsoft Jet 資料庫引擎`CDaoTableDef`支援的基礎 基表的物件設定驗證規則的異常文本。

```
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>參數

*lpsz 驗證文字*<br/>
指向字串表示式的指標,用於指定如果輸入的數據無效時顯示的文本。

### <a name="remarks"></a>備註

不能設置附加表的驗證文本。

有關相關信息,請參閱 DAO 説明中的主題"驗證文本屬性」。。

## <a name="see-also"></a>另請參閱

[CObject 類別](../../mfc/reference/cobject-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase 類別](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset 類別](../../mfc/reference/cdaorecordset-class.md)
