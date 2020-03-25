---
title: CDynamicAccessor 類別
ms.date: 11/04/2016
f1_keywords:
- ATL.CDynamicAccessor
- ATL::CDynamicAccessor
- CDynamicAccessor
- ATL::CDynamicAccessor::AddBindEntry
- CDynamicAccessor.AddBindEntry
- CDynamicAccessor::AddBindEntry
- ATL.CDynamicAccessor.AddBindEntry
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
- ATL::CDynamicAccessor::Close
- ATL.CDynamicAccessor.Close
- CDynamicAccessor.Close
- CDynamicAccessor::Close
- ATL.CDynamicAccessor.GetBlobHandling
- CDynamicAccessor::GetBlobHandling
- ATL::CDynamicAccessor::GetBlobHandling
- GetBlobHandling
- CDynamicAccessor.GetBlobHandling
- ATL::CDynamicAccessor::GetBlobSizeLimit
- CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor::GetBlobSizeLimit
- GetBlobSizeLimit
- ATL.CDynamicAccessor.GetBlobSizeLimit
- CDynamicAccessor.GetBookmark
- GetBookmark
- CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetBookmark
- ATL::CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetColumnCount
- ATL::CDynamicAccessor::GetColumnCount
- CDynamicAccessor::GetColumnCount
- CDynamicAccessor.GetColumnCount
- GetColumnCount
- CDynamicAccessor.GetColumnFlags
- ATL::CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnFlags
- CDynamicAccessor::GetColumnFlags
- ATL.CDynamicAccessor.GetColumnInfo
- ATL::CDynamicAccessor::GetColumnInfo
- CDynamicAccessor.GetColumnInfo
- CDynamicAccessor::GetColumnInfo
- ATL::CDynamicAccessor::GetColumnName
- GetColumnName
- ATL.CDynamicAccessor.GetColumnName
- CDynamicAccessor::GetColumnName
- CDynamicAccessor.GetColumnName
- ATL.CDynamicAccessor.GetColumnType
- CDynamicAccessor::GetColumnType
- GetColumnType
- CDynamicAccessor.GetColumnType
- ATL::CDynamicAccessor::GetColumnType
- CDynamicAccessor.GetLength
- ATL.CDynamicAccessor.GetLength
- CDynamicAccessor::GetLength
- ATL::CDynamicAccessor::GetLength
- CDynamicAccessor.GetOrdinal
- ATL::CDynamicAccessor::GetOrdinal
- CDynamicAccessor::GetOrdinal
- ATL.CDynamicAccessor.GetOrdinal
- GetOrdinal
- ATL::CDynamicAccessor::GetStatus
- CDynamicAccessor.GetStatus
- ATL.CDynamicAccessor.GetStatus
- CDynamicAccessor::GetStatus
- GetValue
- CDynamicAccessor::GetValue<ctype>
- ATL.CDynamicAccessor.GetValue<ctype>
- CDynamicAccessor.GetValue
- CDynamicAccessor::GetValue
- ATL.CDynamicAccessor.GetValue
- ATL::CDynamicAccessor::GetValue
- ATL::CDynamicAccessor::GetValue<ctype>
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
- ATL::CDynamicAccessor::SetLength
- CDynamicAccessor.SetLength
- CDynamicAccessor::SetLength
- ATL.CDynamicAccessor.SetLength
- CDynamicAccessor::SetStatus
- ATL::CDynamicAccessor::SetStatus
- CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetStatus
- ATL.CDynamicAccessor.SetValue
- ATL::CDynamicAccessor::SetValue
- ATL::CDynamicAccessor::SetValue<ctype>
- CDynamicAccessor.SetValue
- ATL.CDynamicAccessor.SetValue<ctype>
- CDynamicAccessor::SetValue
- CDynamicAccessor::SetValue<ctype>
helpviewer_keywords:
- CDynamicAccessor class
- AddBindEntry method
- CDynamicAccessor class, constructor
- Close method
- GetBlobHandling method
- GetBlobSizeLimit method
- GetBookmark method
- GetColumnCount method
- GetColumnFlags method
- GetColumnInfo method
- GetColumnName method
- GetColumnType method
- GetLength method
- GetOrdinal method
- GetStatus method
- GetValue method
- SetBlobHandling method
- SetBlobSizeLimit method
- SetLength method
- SetStatus method
- SetValue method
ms.assetid: 374b13b7-1f09-457d-9e6b-df260ff4d178
ms.openlocfilehash: 160e5b6d8eb4b45850dc071299413d9ad2cfcee9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212054"
---
# <a name="cdynamicaccessor-class"></a>CDynamicAccessor 類別

讓您能在不知道資料庫結構描述 (資料庫的基礎結構) 的情況下，存取資料來源。

## <a name="syntax"></a>語法

```cpp
class CDynamicAccessor : public CAccessorBase
```

## <a name="requirements"></a>需求

**標頭檔**：atldbcli.h

## <a name="members"></a>成員

### <a name="methods"></a>方法

|||
|-|-|
|[AddBindEntry](#addbindentry)|覆寫預設存取子時，將系結專案加入至輸出資料行。|
|[CDynamicAccessor](#cdynamicaccessor)|具現化並初始化 `CDynamicAccessor` 物件。|
|[關閉](#close)|將所有資料行解除系結、釋放已配置的記憶體，並釋放類別中的[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))介面指標。|
|[GetBlobHandling](#getblobhandling)|抓取目前資料列的 BLOB 處理值。|
|[GetBlobSizeLimit](#getblobsizelimit)|抓取 BLOB 大小上限（以位元組為單位）。|
|[GetBookmark](#getbookmark)|抓取目前資料列的書簽。|
|[GetColumnCount](#getcolumncount)|抓取資料列集中的資料行數目。|
|[GetColumnFlags](#getcolumnflags)|抓取資料行特性。|
|[GetColumnInfo](#getcolumninfo)|抓取資料行中繼資料。|
|[GetColumnName](#getcolumnname)|抓取指定資料行的名稱。|
|[GetColumnType](#getcolumntype)|抓取指定資料行的資料類型。|
|[GetLength](#getlength)|抓取資料行的最大可能長度（以位元組為單位）。|
|[GetOrdinal](#getordinal)|根據指定的資料行名稱，抓取資料行索引。|
|[GetStatus](#getstatus)|抓取指定資料行的狀態。|
|[GetValue](#getvalue)|抓取緩衝區中的資料。|
|[SetBlobHandling](#setblobhandling)|設定目前資料列的 BLOB 處理值。|
|[SetBlobSizeLimit](#setblobsizelimit)|設定 BLOB 大小上限（以位元組為單位）。|
|[SetLength](#setlength)|設定資料行的長度（以位元組為單位）。|
|[SetStatus](#setstatus)|設定指定資料行的狀態。|
|[SetValue](#setvalue)|將資料儲存至緩衝區。|

## <a name="remarks"></a>備註

您可以使用 `CDynamicAccessor` 方法來取得資料行資訊，例如資料行名稱、資料行計數、資料類型等等。 接著，您可以使用此資料行資訊，在執行時間動態建立存取子。

資料行資訊儲存在此類別所建立及管理的緩衝區中。 使用[GetValue](../../data/oledb/cdynamicaccessor-getvalue.md)從緩衝區取得資料。

如需使用動態存取子類別的討論和範例，請參閱[使用動態存取](../../data/oledb/using-dynamic-accessors.md)子。

## <a name="cdynamicaccessoraddbindentry"></a><a name="addbindentry"></a>CDynamicAccessor：： AddBindEntry

將繫結項目加入至輸出資料行。

### <a name="syntax"></a>語法

```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();
```

#### <a name="parameters"></a>參數

*info*<br/>
在包含資料行資訊的 `DBCOLUMNINFO` 結構。 請參閱 OLE DB 程式設計*人員參考*的[IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))中的「DBCOLUMNINFO 結構」。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

覆寫以 `CDynamicAccessor` 建立的預設存取子時，請使用此方法（請參閱[如何提取資料？](../../data/oledb/fetching-data.md)）。

## <a name="cdynamicaccessorcdynamicaccessor"></a><a name="cdynamicaccessor"></a>CDynamicAccessor：： CDynamicAccessor

具現化並初始化 `CDynamicAccessor` 物件。

### <a name="syntax"></a>語法

```cpp
CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,
   DBLENGTH nBlobSize = 8000);
```

#### <a name="parameters"></a>參數

*eBlobHandling*<br/>
指定如何處理二進位大型物件（BLOB）資料。 預設值為 DBBLOBHANDLING_DEFAULT。 如需 DBBLOBHANDLINGENUM 值的說明，請參閱[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) 。

*nBlobSize*<br/>
最大 BLOB 的大小 (以位元組為單位)；此值的資料行資料被視為 BLOB。 預設值為8000。 如需詳細資訊，請參閱[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) 。

### <a name="remarks"></a>備註

如果您使用此函式來初始化 `CDynamicAccessor` 物件，您可以指定它要如何系結 Blob。 Blob 可以包含二進位資料，例如圖形、聲音或已編譯的程式碼。 預設行為是將資料行的8000位元組視為 Blob，並嘗試將它們系結至 `ISequentialStream` 物件。 不過，您可以指定不同的值做為 BLOB 大小。

您也可以指定 `CDynamicAccessor` 如何處理限定為 BLOB 資料的資料行資料：它可以用預設方式處理 BLOB 資料。它可以略過（不系結） BLOB 資料;或者，它可以將 BLOB 資料系結到提供者配置的記憶體中。

## <a name="cdynamicaccessorclose"></a><a name="close"></a>CDynamicAccessor：： Close

將所有資料行解除系結、釋放已配置的記憶體，並釋放類別中的[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))介面指標。

### <a name="syntax"></a>語法

```cpp
void Close() throw();
```

## <a name="cdynamicaccessorgetblobhandling"></a><a name="getblobhandling"></a>CDynamicAccessor：： GetBlobHandling

抓取目前資料列的 BLOB 處理值。

### <a name="syntax"></a>語法

```cpp
const DBBLOBHANDLINGENUM GetBlobHandling() const;
```

### <a name="remarks"></a>備註

傳回[SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md)所設定的 BLOB 處理值*eBlobHandling* 。

## <a name="cdynamicaccessorgetblobsizelimit"></a><a name="getblobsizelimit"></a>CDynamicAccessor：： GetBlobSizeLimit

抓取 BLOB 大小上限（以位元組為單位）。

### <a name="syntax"></a>語法

```cpp
const DBLENGTH GetBlobSizeLimit() const;
```

### <a name="remarks"></a>備註

傳回[SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md)所設定的 BLOB 處理值*nBlobSize* 。

## <a name="cdynamicaccessorgetbookmark"></a><a name="getbookmark"></a>CDynamicAccessor：： GetBookmark

抓取目前資料列的書簽。

### <a name="syntax"></a>語法

```cpp
HRESULT GetBookmark(CBookmark< >* pBookmark) const throw();
```

#### <a name="parameters"></a>參數

*pBookmark*<br/>
脫銷[CBookmark](../../data/oledb/cbookmark-class.md)物件的指標。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

您必須將 `DBPROP_IRowsetLocate` 設定為 VARIANT_TRUE，才能取得書簽。

## <a name="cdynamicaccessorgetcolumncount"></a><a name="getcolumncount"></a>CDynamicAccessor：： GetColumnCount

抓取資料行的數目。

### <a name="syntax"></a>語法

```cpp
DBORDINAL GetColumnCount() const throw();
```

### <a name="return-value"></a>傳回值

抓取的資料行數目。

## <a name="cdynamicaccessorgetcolumnflags"></a><a name="getcolumnflags"></a>CDynamicAccessor：： GetColumnFlags

抓取資料行特性。

### <a name="syntax"></a>語法

```cpp
bool GetColumnFlags(DBORDINAL nColumn,
   DBCOLUMNFLAGS* pFlags) const throw();
```

#### <a name="parameters"></a>參數

*nColumn*<br/>
[in] 資料行編號。 資料行編號的開頭為1。 值為0表示書簽資料行（如果有的話）。

*pFlags*<br/>
脫銷描述資料行特性的位元遮罩指標。 請參閱 OLE DB 程式設計*人員參考*的[IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))中的「DBCOLUMNFLAGS 列舉型別」。

### <a name="return-value"></a>傳回值

如果成功抓取資料行特性，則傳回**true** 。 否則會傳回 **false**。

### <a name="remarks"></a>備註

資料行編號是從1開始位移。 資料行零是特殊案例;這是書簽（如果有的話）。

## <a name="cdynamicaccessorgetcolumninfo"></a><a name="getcolumninfo"></a>CDynamicAccessor：： GetColumnInfo

傳回大部分消費者所需的資料行中繼資料。

### <a name="syntax"></a>語法

```cpp
HRESULT GetColumnInfo(IRowset* pRowset,
   DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo,
   OLECHAR** ppStringsBuffer) throw();
```

#### <a name="parameters"></a>參數

*pRowset*<br/>
在[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))介面的指標。

*pColumns*<br/>
脫銷要在其中傳回資料列集之資料行數目的記憶體指標;這個數位包含書簽資料行（如果有的話）。

*ppColumnInfo*<br/>
脫銷要在其中傳回 `DBCOLUMNINFO` 結構陣列的記憶體指標。 請參閱 OLE DB 程式設計*人員參考*的[IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\))中的「DBCOLUMNINFO 結構」。

*ppStringsBuffer*<br/>
脫銷記憶體的指標，用來傳回單一配置區塊內所有字串值（ *columnid*或 for *pwszName*內所使用的名稱）之儲存體的指標。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

如需 `DBORDINAL`、`DBCOLUMNINFO`和 `OLECHAR`資料類型的相關資訊，請參閱 OLE DB 程式設計*人員參考*中的[IColumnsInfo：： GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) 。

## <a name="cdynamicaccessorgetcolumnname"></a><a name="getcolumnname"></a>CDynamicAccessor：： GetColumnName

抓取指定資料行的名稱。

### <a name="syntax"></a>語法

```cpp
LPOLESTR GetColumnName(DBORDINAL nColumn) const throw();
```

#### <a name="parameters"></a>參數

*nColumn*<br/>
[in] 資料行編號。 資料行編號的開頭為1。 值為0表示書簽資料行（如果有的話）。

### <a name="return-value"></a>傳回值

指定之資料行的名稱。

## <a name="cdynamicaccessorgetcolumntype"></a><a name="getcolumntype"></a>CDynamicAccessor：： GetColumnType

抓取指定資料行的資料類型。

### <a name="syntax"></a>語法

```cpp
bool GetColumnType(DBORDINAL nColumn,
   DBTYPE* pType) const throw();
```

#### <a name="parameters"></a>參數

*nColumn*<br/>
[in] 資料行編號。 資料行編號的開頭為1。 值為0表示書簽資料行（如果有的話）。

*pType*<br/>
脫銷指定資料行之資料類型的指標。

### <a name="return-value"></a>傳回值

如果成功，則傳回**true** ，否則會傳回**false** 。

## <a name="cdynamicaccessorgetlength"></a><a name="getlength"></a>CDynamicAccessor：： GetLength

抓取指定資料行的長度。

### <a name="syntax"></a>語法

```cpp
bool GetLength(DBORDINAL nColumn,
   DBLENGTH* pLength) const throw();

bool GetLength(const CHAR* pColumnName,
   DBLENGTH* pLength) const throw();

bool GetLength(const WCHAR* pColumnName,
   DBLENGTH* pLength) const throw();
```

#### <a name="parameters"></a>參數

*nColumn*<br/>
[in] 資料行編號。 資料行編號的開頭為1。 值為0表示書簽資料行（如果有的話）。

*pColumnName*<br/>
[in] 指向包含資料行名稱之字元字串的指標。

*pLength*<br/>
脫銷整數的指標，其中包含資料行的長度（以位元組為單位）。

### <a name="return-value"></a>傳回值

如果找到指定的資料行，則傳回**true** 。 否則，此函數會傳回**false**。

### <a name="remarks"></a>備註

第一個覆寫會採用資料行編號，而第二個和第三個覆寫會分別採用 ANSI 或 Unicode 格式的資料行名稱。

## <a name="cdynamicaccessorgetordinal"></a><a name="getordinal"></a>CDynamicAccessor：： GetOrdinal

擷取指定資料行名稱的資料行數目。

### <a name="syntax"></a>語法

```cpp
bool GetOrdinal(const CHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();

bool GetOrdinal(const WCHAR* pColumnName,
   DBORDINAL* pOrdinal) const throw();
```

#### <a name="parameters"></a>參數

*pColumnName*<br/>
[in] 指向包含資料行名稱之字元字串的指標。

*pOrdinal*<br/>
[out] 指向資料行數目的指標。

### <a name="return-value"></a>傳回值

如果找到具有指定名稱的資料行，則傳回**true** 。 否則，此函數會傳回**false**。

## <a name="cdynamicaccessorgetstatus"></a><a name="getstatus"></a>CDynamicAccessor：： GetStatus

抓取指定資料行的狀態。

### <a name="syntax"></a>語法

```cpp
bool GetStatus(DBORDINAL nColumn,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const CHAR* pColumnName,
   DBSTATUS* pStatus) const throw();

bool GetStatus(const WCHAR* pColumnName,
   DBSTATUS* pStatus) const throw();
```

#### <a name="parameters"></a>參數

*nColumn*<br/>
[in] 資料行編號。 資料行編號的開頭為1。 值為0表示書簽資料行（如果有的話）。

*pColumnName*<br/>
[in] 指向包含資料行名稱之字元字串的指標。

*pStatus*<br/>
脫銷包含資料行狀態之變數的指標。 如需詳細資訊，請參閱 OLE DB 程式設計*人員參考*中的[DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) 。

### <a name="return-value"></a>傳回值

如果找到指定的資料行，則傳回**true** 。 否則，此函數會傳回**false**。

## <a name="cdynamicaccessorgetvalue"></a><a name="getvalue"></a>CDynamicAccessor：： GetValue

抓取指定資料行的資料。

### <a name="syntax"></a>語法

```cpp
void* GetValue(DBORDINAL nColumn) const throw();

void* GetValue(const CHAR* pColumnName) const throw();

void* GetValue(const WCHAR* pColumnName) const throw();

template < class ctype >
bool GetValue(DBORDINAL nColumn, ctype* pData) const throw();

template < class ctype >
bool GetValue(const CHAR* pColumnName, ctype* pData) const throw();

template < class ctype >
bool GetValue(const WCHAR* pColumnName, ctype* pData) const throw();
```

#### <a name="parameters"></a>參數

*ctype*<br/>
在樣板化參數，它會處理任何資料類型，但不包括字串類型（`CHAR*`、`WCHAR*`），而這需要特殊處理。 `GetValue` 會根據您在此處指定的內容，使用適當的資料類型。

*nColumn*<br/>
[in] 資料行編號。 資料行編號的開頭為1。 值為0表示書簽資料行（如果有的話）。

*pColumnName*<br/>
在資料行名稱。

*pData*<br/>
脫銷指定資料行內容的指標。

### <a name="return-value"></a>傳回值

如果您想要傳遞字串資料，請使用 `GetValue`的樣板版本。 這個方法的樣板版本會傳回 `void*`，這會指向包含指定資料行資料之緩衝區的一部分。 如果找不到資料行，則傳回 Null。

對於其他所有資料類型而言，使用樣板化版本的 `GetValue`比較簡單。 樣板化版本會在成功時傳回**true** ，否則會傳回**false** 。

### <a name="remarks"></a>備註

使用樣板版本來傳回包含字串的資料行，以及包含其他資料類型之資料行的樣板化版本。

在 [偵錯工具] 模式中，如果*pData*的大小與它指向的資料行大小不相等，您就會得到判斷提示。

## <a name="cdynamicaccessorsetblobhandling"></a><a name="setblobhandling"></a>CDynamicAccessor：： SetBlobHandling

設定目前資料列的 BLOB 處理值。

### <a name="syntax"></a>語法

```cpp
bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);
```

#### <a name="parameters"></a>參數

*eBlobHandling*<br/>
指定 BLOB 資料的處理方式。 它可以採用下列值：

- DBBLOBHANDLING_DEFAULT：將大於*nBlobSize* （由 `SetBlobSizeLimit`設定）的資料行資料處理為 BLOB 資料，並透過 `ISequentialStream` 或 `IStream` 物件加以取出。 此選項會嘗試系結包含大於*nBlobSize*之資料的每個資料行，或將其列為 DBTYPE_IUNKNOWN 做為 BLOB 資料。

- DBBLOBHANDLING_NOSTREAMS：處理大於*nBlobSize* （由 `SetBlobSizeLimit`設定）的資料行資料做為 BLOB 資料，並在提供者配置的取用者所擁有的記憶體中透過參考加以取出。 此選項適用于具有多個 BLOB 資料行的資料表，而且提供者只支援每個存取子的一個 `ISequentialStream` 物件。

- DBBLOBHANDLING_SKIP：略過（不系結）限定為包含 Blob 的資料行（存取子不會系結或抓取資料行值，但仍然會抓取資料行的狀態和長度）。

### <a name="remarks"></a>備註

您應該先呼叫 `SetBlobHandling`，然後再呼叫 `Open`。

此方法[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)會將 BLOB 處理值設定為 DBBLOBHANDLING_DEFAULT。

## <a name="cdynamicaccessorsetblobsizelimit"></a><a name="setblobsizelimit"></a>CDynamicAccessor：： SetBlobSizeLimit

設定 BLOB 大小上限（以位元組為單位）。

### <a name="syntax"></a>語法

```cpp
void SetBlobSizeLimit(DBLENGTH nBlobSize);
```

#### <a name="parameters"></a>參數

*nBlobSize*<br/>
指定 BLOB 大小限制。

### <a name="remarks"></a>備註

設定 BLOB 大小上限（以位元組為單位）;大於此值的資料行資料會被視為 BLOB。 有些提供者會為數據行提供極大的大小（例如 2 GB）。 您通常會嘗試將這些資料行系結為 Blob，而不是嘗試為此大小的資料行配置記憶體。 如此一來，您就不需要配置所有的記憶體，但是您仍然可以讀取所有資料，而不需要擔心截斷的情況。 不過，在某些情況下，您可能會想要強制 `CDynamicAccessor` 系結其原生資料類型中的大型資料行。 若要這麼做，請先呼叫 `SetBlobSizeLimit`，然後再呼叫 `Open`。

「函式方法[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)會將 BLOB 大小上限設定為預設值8000個位元組。

## <a name="cdynamicaccessorsetlength"></a><a name="setlength"></a>CDynamicAccessor：： SetLength

設定指定之資料行的長度。

### <a name="syntax"></a>語法

```cpp
bool SetLength(DBORDINAL nColumn,
   DBLENGTH nLength)throw();

bool SetLength(const CHAR* pColumnName,
   DBLENGTH nLength) throw();

bool SetLength(const WCHAR* pColumnName,
   DBLENGTH nLength) throw();
```

#### <a name="parameters"></a>參數

*nColumn*<br/>
[in] 資料行編號。 資料行編號的開頭為1。 值為0表示書簽資料行（如果有的話）。

*nLength*<br/>
在資料行的長度（以位元組為單位）。

*pColumnName*<br/>
[in] 指向包含資料行名稱之字元字串的指標。

### <a name="return-value"></a>傳回值

如果已成功設定指定的資料行長度，則傳回**true** 。 否則，此函數會傳回**false**。

## <a name="cdynamicaccessorsetstatus"></a><a name="setstatus"></a>CDynamicAccessor：： SetStatus

設定指定之資料行的狀態。

### <a name="syntax"></a>語法

```cpp
bool SetStatus(DBORDINAL nColumn,
   DBSTATUS status)throw();

bool SetStatus(const CHAR* pColumnName,
   DBSTATUS status) throw();

bool SetStatus(const WCHAR* pColumnName,
   DBSTATUS status) throw();
```

#### <a name="parameters"></a>參數

*nColumn*<br/>
[in] 資料行編號。 資料行編號的開頭為1。 值為0表示書簽資料行（如果有的話）。

*status*<br/>
在資料行狀態。 如需詳細資訊，請參閱 OLE DB 程式設計*人員參考*中的[DBSTATUS](/previous-versions/windows/desktop/ms722617(v=vs.85)) 。

*pColumnName*<br/>
[in] 指向包含資料行名稱之字元字串的指標。

### <a name="return-value"></a>傳回值

如果已成功設定指定的資料行狀態，則傳回**true** 。 否則，此函數會傳回**false**。

## <a name="cdynamicaccessorsetvalue"></a><a name="setvalue"></a>CDynamicAccessor：： SetValue

將資料儲存至指定的資料行。

### <a name="syntax"></a>語法

```cpp
template <class ctype>
bool SetValue(
   DBORDINAL nColumn,
   constctype& data) throw( );

template <class ctype>
bool SetValue(
   const CHAR * pColumnName,
   const ctype& data) throw( );

template <class ctype>
bool SetValue(
   const WCHAR *pColumnName,
   const ctype& data) throw( );
```

#### <a name="parameters"></a>參數

*ctype*<br/>
在樣板化參數，它會處理任何資料類型，但不包括字串類型（`CHAR*`、`WCHAR*`），而這需要特殊處理。 `GetValue` 會根據您在此處指定的內容，使用適當的資料類型。

*pColumnName*<br/>
[in] 指向包含資料行名稱之字元字串的指標。

*data*<br/>
在包含資料之記憶體的指標。

*nColumn*<br/>
[in] 資料行編號。 資料行編號的開頭為1。 值為0表示書簽資料行（如果有的話）。

### <a name="return-value"></a>傳回值

如果您想要設定字串資料，請使用樣板版本的 `GetValue`。 這個方法的樣板版本會傳回 `void*`，這會指向包含指定資料行資料之緩衝區的一部分。 如果找不到資料行，則傳回 Null。

對於其他所有資料類型而言，使用樣板化版本的 `GetValue`比較簡單。 樣板化版本會在成功時傳回**true** ，否則會傳回**false** 。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 類別](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)
