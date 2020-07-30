---
title: OLE DB 消費者樣板的巨集和全域函式
ms.date: 02/11/2019
f1_keywords:
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
- BEGIN_ACCESSOR
- BEGIN_ACCESSOR_MAP
- END_ACCESSOR
- END_ACCESSOR_MAP
- BEGIN_COLUMN_MAP
- BLOB_ENTRY
- BLOB_ENTRY_LENGTH
- BLOB_ENTRY_LENGTH_STATUS
- BLOB_ENTRY_STATUS
- BLOB_NAME
- BLOB_NAME_LENGTH
- BLOB_NAME_LENGTH_STATUS
- BLOB_NAME_STATUS
- BOOKMARK_ENTRY
- COLUMN_ENTRY
- COLUMN_ENTRY_EX
- COLUMN_ENTRY_LENGTH
- COLUMN_ENTRY_LENGTH_STATUS
- COLUMN_ENTRY_PS
- COLUMN_ENTRY_PS_LENGTH
- COLUMN_ENTRY_PS_LENGTH_STATUS
- COLUMN_ENTRY_PS_STATUS
- COLUMN_ENTRY_STATUS
- COLUMN_ENTRY_TYPE
- COLUMN_ENTRY_TYPE_SIZE
- COLUMN_NAME
- COLUMN_NAME_EX
- COLUMN_NAME_LENGTH
- COLUMN_NAME_LENGTH_STATUS
- COLUMN_NAME_PS
- COLUMN_NAME_PS_LENGTH
- COLUMN_NAME_PS_LENGTH_STATUS
- COLUMN_NAME_PS_STATUS
- COLUMN_NAME_STATUS
- COLUMN_NAME_TYPE
- COLUMN_NAME_TYPE_PS
- COLUMN_NAME_TYPE_SIZE
- COLUMN_NAME_TYPE_STATUS
- END_COLUMN_MAP
- DEFINE_COMMAND
- DEFINE_COMMAND_EX
- BEGIN_PARAM_MAP
- END_PARAM_MAP
- SET_PARAM_TYPE
helpviewer_keywords:
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
- AtlTraceErrorRecords function
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR_MAP macro
- END_ACCESSOR macro
- END_ACCESSOR_MAP macro
- BEGIN_COLUMN_MAP macro
- BLOB_ENTRY macro
- BLOB_ENTRY_LENGTH macro
- BLOB_ENTRY_LENGTH_STATUS macro
- BLOB_ENTRY_STATUS macro
- BLOB_NAME macro
- BLOB_NAME_LENGTH macro
- BLOB_NAME_LENGTH_STATUS macro
- BLOB_NAME_STATUS macro
- BOOKMARK_ENTRY macro
- COLUMN_ENTRY macro
- COLUMN_ENTRY_EX macro
- COLUMN_ENTRY_LENGTH macro
- COLUMN_ENTRY_LENGTH_STATUS macro
- COLUMN_ENTRY_PS macro
- COLUMN_ENTRY_PS_LENGTH macro
- COLUMN_ENTRY_PS_LENGTH_STATUS macro
- COLUMN_ENTRY_PS_STATUS macro
- COLUMN_ENTRY_STATUS macro
- COLUMN_ENTRY_TYPE macro
- COLUMN_ENTRY_TYPE_SIZE macro
- COLUMN_NAME macro
- COLUMN_NAME_EX macro
- COLUMN_NAME_LENGTH macro
- COLUMN_NAME_LENGTH_STATUS macro
- COLUMN_NAME_PS macro
- COLUMN_NAME_PS_LENGTH macro
- COLUMN_NAME_PS_LENGTH_STATUS macro
- COLUMN_NAME_PS_STATUS macro
- COLUMN_NAME_STATUS macro
- COLUMN_NAME_TYPE macro
- COLUMN_NAME_TYPE_PS macro
- COLUMN_NAME_TYPE_SIZE macro
- COLUMN_NAME_TYPE_STATUS macro
- END_COLUMN_MAP macro
- DEFINE_COMMAND macro
- DEFINE_COMMAND_EX macro
- BEGIN_PARAM_MAP macro
- END_PARAM_MAP macro
- SET_PARAM_TYPE macro
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
ms.openlocfilehash: 0263289e75dc79ecf0b75e484b4bb97aede87ea7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232127"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>OLE DB 消費者樣板的巨集和全域函式

OLE DB 取用者範本包含下列宏和全域函式：

## <a name="global-functions"></a>全域函式

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|如果傳回錯誤，請將 OLE DB 錯誤記錄資訊傾印到傾印裝置。|

## <a name="accessor-map-macros"></a>存取子對應宏

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|標記存取子專案的開頭。|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|標記存取子對應項目的開頭。|
|[END_ACCESSOR](#end_accessor)|標記存取子專案的結尾。|
|[END_ACCESSOR_MAP](#end_accessor_map)|標記存取子對應專案的結尾。|

## <a name="column-map-macros"></a>資料行對應宏

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|標記使用者記錄類別中資料行對應專案的開頭。|
|[BLOB_ENTRY](#blob_entry)|用來系結二進位大型物件（BLOB）。|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|報告 BLOB 資料行的長度。|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|報告 BLOB 資料行的長度和狀態。|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|報告 BLOB 資料行的狀態。|
|[BLOB_NAME](#blob_name)|用來系結二進位大型物件（依資料行名稱）。|
|[BLOB_NAME_LENGTH](#blob_name_length)|報告 BLOB 資料行的長度。|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|報告 BLOB 資料行的長度和狀態。|
|[BLOB_NAME_STATUS](#blob_name_status)|報告 BLOB 資料行的狀態。|
|[BOOKMARK_ENTRY](#bookmark_entry)|代表資料列集上的書簽專案。 書簽專案是特殊類型的資料行專案。|
|[COLUMN_ENTRY](#column_entry)|表示資料庫中特定資料行的系結。|
|[COLUMN_ENTRY_EX](#column_entry_ex)|表示資料庫中特定資料行的系結。 支援*類型*、*長度*、*有效**位數、小*數位數和*狀態*參數。|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|表示資料庫中特定資料行的系結。 支援*長度*變數。|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|表示資料庫中特定資料行的系結。 支援*狀態*和*長度*參數。|
|[COLUMN_ENTRY_PS](#column_entry_ps)|表示資料庫中特定資料行的系結。 支援*有效**位數和小*數位數參數。|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|表示資料庫中特定資料行的系結。 支援*長度**變數、有效*位數和*小*數位數參數。|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|表示資料庫中特定資料行的系結。 支援*狀態*和*長度**變數、有效*位數和*小*數位數參數。|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|表示資料庫中特定資料行的系結。 支援*狀態**變數、有效*位數和*小*數位數參數。|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|表示資料庫中特定資料行的系結。 支援*狀態*變數。|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|表示資料庫中特定資料行的系結。 支援*型*別參數。|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|表示資料庫中特定資料行的系結。 支援*type*和*size*參數。|
|[COLUMN_NAME](#column_name)|以名稱表示資料庫中特定資料行的系結。|
|[COLUMN_NAME_EX](#column_name_ex)|以名稱表示資料庫中特定資料行的系結。 支援資料類型、大小、有效位數、小數位數、資料行長度和資料行狀態的規格。|
|[COLUMN_NAME_LENGTH](#column_name_length)|以名稱表示資料庫中特定資料行的系結。 支援資料行長度的規格。|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|以名稱表示資料庫中特定資料行的系結。 支援資料行長度和狀態的規格。|
|[COLUMN_NAME_PS](#column_name_ps)|以名稱表示資料庫中特定資料行的系結。 支援精確度和小數位數的規格。|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|以名稱表示資料庫中特定資料行的系結。 支援有效位數、小數位數和資料行長度的規格。|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|以名稱表示資料庫中特定資料行的系結。 支援精確度、小數位數、資料行長度和資料行狀態的規格。|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|以名稱表示資料庫中特定資料行的系結。 支援有效位數、小數位數和資料行狀態的規格。|
|[COLUMN_NAME_STATUS](#column_name_status)|以名稱表示資料庫中特定資料行的系結。 支援資料行狀態的規格。|
|[COLUMN_NAME_TYPE](#column_name_type)|以名稱表示資料庫中特定資料行的系結。 支援資料類型的規格。|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|以名稱表示資料庫中特定資料行的系結。 支援資料類型、有效位數和小數位數的規格。|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|以名稱表示資料庫中特定資料行的系結。 支援資料類型和大小的規格。|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|以名稱表示資料庫中特定資料行的系結。 支援資料類型和資料行狀態的規格。|
|[END_COLUMN_MAP](#end_column_map)|標記資料行對應專案的結尾。|

## <a name="command-macros"></a>命令宏

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|指定使用[CCommand](../../data/oledb/ccommand-class.md)類別時，將用來建立資料列集的命令。 只接受符合指定之應用程式類型（ANSI 或 Unicode）的字串類型。 建議您使用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) ，而不要使用 DEFINE_COMMAND。|
|[DEFINE_COMMAND_EX](#define_command_ex)|指定使用[CCommand](../../data/oledb/ccommand-class.md)類別時，將用來建立資料列集的命令。 支援 ANSI 和 Unicode 應用程式。|

## <a name="parameter-map-macros"></a>參數對應宏

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|標記使用者記錄類別中參數對應專案的開頭。|
|[END_PARAM_MAP](#end_param_map)|標記參數對應專案的結尾。|
|[SET_PARAM_TYPE](#set_param_type)|指定 SET_PARAM_TYPE 宏後面 COLUMN_ENTRY 宏做為輸入、輸出或輸入/輸出。|

### <a name="atltraceerrorrecords"></a><a name="atltraceerrorrecords"></a>AtlTraceErrorRecords

如果傳回錯誤，請將 OLE DB 錯誤記錄資訊傾印到傾印裝置。

#### <a name="syntax"></a>語法

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>參數

*hErr*<br/>
在OLE DB 取用者範本成員函式所傳回的 HRESULT。

#### <a name="remarks"></a>備註

如果未 S_OK *hErr* ，則會將 `AtlTraceErrorRecords` OLE DB 的錯誤記錄資訊傾印到傾印裝置（[輸出] 視窗或檔案的 [ **Debug** ] 索引標籤）。 從提供者取得的錯誤記錄資訊，包括每個錯誤記錄專案的資料列編號、來源、描述、說明檔、內容和 GUID。 `AtlTraceErrorRecords`只在 debug 組建中傾印這項資訊。 在發行組建中，它是已優化的空白 stub。如需詳細資訊，請參閱[CDBErrorInfo 類別](../../data/oledb/cdberrorinfo-class.md)。

### <a name="begin_accessor"></a><a name="begin_accessor"></a>BEGIN_ACCESSOR

標記存取子專案的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>參數

*num*<br/>
在這個存取子對應中存取子的零位移數位。

*bAuto*<br/>
在指定此存取子是自動存取子或手動存取子。 如果為 **`true`** ，則存取子為 auto; 如果為 **`false`** ，則為手動存取子。 自動存取子表示會為您提取移動作業的資料。

#### <a name="remarks"></a>備註

在資料列集上有多個存取子的情況下，您必須指定 BEGIN_ACCESSOR_MAP，並針對每個個別存取子使用 BEGIN_ACCESSOR 宏。 BEGIN_ACCESSOR 宏是以 END_ACCESSOR 宏完成。 BEGIN_ACCESSOR_MAP 宏是以 END_ACCESSOR_MAP 宏完成。

#### <a name="example"></a>範例

請參閱[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="begin_accessor_map"></a><a name="begin_accessor_map"></a>BEGIN_ACCESSOR_MAP

標記存取子對應項目的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>參數

*x*<br/>
[in] 使用者資料錄類別的名稱。

*num*<br/>
[in] 此存取子對應中的存取子數目。

#### <a name="remarks"></a>備註

如果是在資料列集上有多個存取子，您必須在一開始指定 BEGIN_ACCESSOR_MAP，並針對每個個別存取子使用 BEGIN_ACCESSOR 宏。 BEGIN_ACCESSOR 宏是以 END_ACCESSOR 宏完成。 存取子對應是以 END_ACCESSOR_MAP 宏完成。

如果使用者資料錄中只有一個存取子，請使用巨集 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)。

#### <a name="example"></a>範例

```cpp
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
```

### <a name="end_accessor"></a><a name="end_accessor"></a>END_ACCESSOR

標記存取子專案的結尾。

#### <a name="syntax"></a>語法

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>備註

針對資料列集上的多個存取子，您必須指定 BEGIN_ACCESSOR_MAP，並使用每個個別存取子的 BEGIN_ACCESSOR 宏。 BEGIN_ACCESSOR 宏是以 END_ACCESSOR 宏完成。 BEGIN_ACCESSOR_MAP 宏是以 END_ACCESSOR_MAP 宏完成。

#### <a name="example"></a>範例

請參閱[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="end_accessor_map"></a><a name="end_accessor_map"></a>END_ACCESSOR_MAP

標記存取子對應專案的結尾。

#### <a name="syntax"></a>語法

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>備註

針對資料列集上的多個存取子，您必須指定 BEGIN_ACCESSOR_MAP，並使用每個個別存取子的 BEGIN_ACCESSOR 宏。 BEGIN_ACCESSOR 宏是以 END_ACCESSOR 宏完成。 BEGIN_ACCESSOR_MAP 宏是以 END_ACCESSOR_MAP 宏完成。

#### <a name="example"></a>範例

請參閱[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="begin_column_map"></a><a name="begin_column_map"></a>BEGIN_COLUMN_MAP

標記資料行對應項目的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>參數

*x*<br/>
[in] 衍生自 `CAccessor`之使用者資料錄類別的名稱。

#### <a name="remarks"></a>備註

如果資料列集上只有單一存取子，就會使用此巨集。 如果資料列集上有多個存取子，請使用 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

BEGIN_COLUMN_MAP 宏是以 END_COLUMN_MAP 宏完成。 當使用者資料錄中只需要一個存取子時，就會使用此巨集。

資料行會對應至您想要繫結之資料列集中的欄位。

#### <a name="example"></a>範例

以下是範例資料行和參數對應︰

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a><a name="blob_entry"></a>BLOB_ENTRY

與 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 搭配使用，以系結二進位大型物件（[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))）。

#### <a name="syntax"></a>語法

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>參數

*nOrdinal*<br/>
[in] 資料行編號。

*IID*<br/>
在用來抓取 BLOB 的介面 GUID （例如 `IDD_ISequentialStream` ）。

*flags*<br/>
在OLE 結構化儲存體模型所定義的儲存模式旗標（例如 `STGM_READ` ）。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="example"></a>範例

請參閱[如何取得 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_entry_length"></a><a name="blob_entry_length"></a>BLOB_ENTRY_LENGTH

與 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 搭配使用，以系結二進位大型物件（[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))）。 類似于[BLOB_ENTRY](../../data/oledb/blob-entry.md)，不同之處在于此宏也會取得 BLOB 資料行的長度（以位元組為單位）。

#### <a name="syntax"></a>語法

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>參數

*nOrdinal*<br/>
[in] 資料行編號。

*IID*<br/>
在用來抓取 BLOB 的介面 GUID （例如 `IDD_ISequentialStream` ）。

*flags*<br/>
在OLE 結構化儲存體模型所定義的儲存模式旗標（例如 `STGM_READ` ）。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
脫銷BLOB 資料行的（實際）長度（以位元組為單位）。

#### <a name="example"></a>範例

請參閱[如何取得 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_entry_length_status"></a><a name="blob_entry_length_status"></a>BLOB_ENTRY_LENGTH_STATUS

與 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 搭配使用，以系結二進位大型物件（[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))）。 類似于[BLOB_ENTRY](../../data/oledb/blob-entry.md)，不同之處在于此宏也會取得 BLOB 資料行的長度和狀態。

#### <a name="syntax"></a>語法

```cpp
BLOB_ENTRY_LENGTH_STATUS(
    nOrdinal,
    IID,
    flags,
    data,
    length,
    status )
```

#### <a name="parameters"></a>參數

*nOrdinal*<br/>
[in] 資料行編號。

*IID*<br/>
在用來抓取 BLOB 的介面 GUID （例如 `IDD_ISequentialStream` ）。

*flags*<br/>
在OLE 結構化儲存體模型所定義的儲存模式旗標（例如 `STGM_READ` ）。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
脫銷BLOB 資料行的（實際）長度（以位元組為單位）。

*status*<br/>
脫銷BLOB 資料行的狀態。

#### <a name="example"></a>範例

請參閱[如何取得 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_entry_status"></a><a name="blob_entry_status"></a>BLOB_ENTRY_STATUS

與 BEGIN_COLUMN_MAP 或 BEGIN_ACCESSOR_MAP 搭配使用，以系結二進位大型物件（[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))）。 類似于[BLOB_ENTRY](../../data/oledb/blob-entry.md)，不同之處在于此宏也會取得 BLOB 資料行的狀態。

#### <a name="syntax"></a>語法

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>參數

*nOrdinal*<br/>
[in] 資料行編號。

*IID*<br/>
在用來抓取 BLOB 的介面 GUID （例如 `IDD_ISequentialStream` ）。

*flags*<br/>
在OLE 結構化儲存體模型所定義的儲存模式旗標（例如 `STGM_READ` ）。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*status*<br/>
脫銷BLOB 欄位的狀態。

#### <a name="example"></a>範例

請參閱[如何取得 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_name"></a><a name="blob_name"></a>BLOB_NAME

與 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 搭配使用，以系結二進位大型物件（[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))）。 類似于[BLOB_ENTRY](../../data/oledb/blob-entry.md)，不同之處在于這個宏會接受資料行名稱，而不是資料行編號。

#### <a name="syntax"></a>語法

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*IID*<br/>
在用來抓取 BLOB 的介面 GUID （例如 `IDD_ISequentialStream` ）。

*flags*<br/>
在OLE 結構化儲存體模型所定義的儲存模式旗標（例如 `STGM_READ` ）。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="example"></a>範例

請參閱[如何取得 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_name_length"></a><a name="blob_name_length"></a>BLOB_NAME_LENGTH

與 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 搭配使用，以系結二進位大型物件（[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))）。 類似于[BLOB_NAME](../../data/oledb/blob-name.md)，不同之處在于此宏也會取得 BLOB 資料行的長度（以位元組為單位）。

#### <a name="syntax"></a>語法

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*IID*<br/>
在用來抓取 BLOB 的介面 GUID （例如 `IDD_ISequentialStream` ）。

*flags*<br/>
在OLE 結構化儲存體模型所定義的儲存模式旗標（例如 `STGM_READ` ）。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
脫銷BLOB 資料行的（實際）長度（以位元組為單位）。

### <a name="blob_name_length_status"></a><a name="blob_name_length_status"></a>BLOB_NAME_LENGTH_STATUS

與 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 搭配使用，以系結二進位大型物件（[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))）。 類似于[BLOB_NAME](../../data/oledb/blob-name.md)，不同之處在于此宏也會取得 BLOB 資料行的長度和狀態。

#### <a name="syntax"></a>語法

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*IID*<br/>
在用來抓取 BLOB 的介面 GUID （例如 `IDD_ISequentialStream` ）。

*flags*<br/>
在OLE 結構化儲存體模型所定義的儲存模式旗標（例如 `STGM_READ` ）。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
脫銷BLOB 資料行的（實際）長度（以位元組為單位）。

*status*<br/>
脫銷BLOB 欄位的狀態。

### <a name="blob_name_status"></a><a name="blob_name_status"></a>BLOB_NAME_STATUS

與 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 搭配使用，以系結二進位大型物件（[BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))）。 類似于[BLOB_NAME](../../data/oledb/blob-name.md)，不同之處在于此宏也會取得 BLOB 資料行的狀態。

#### <a name="syntax"></a>語法

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*IID*<br/>
在用來抓取 BLOB 的介面 GUID （例如 `IDD_ISequentialStream` ）。

*flags*<br/>
在OLE 結構化儲存體模型所定義的儲存模式旗標（例如 `STGM_READ` ）。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*status*<br/>
脫銷BLOB 欄位的狀態。

### <a name="bookmark_entry"></a><a name="bookmark_entry"></a>BOOKMARK_ENTRY

系結書簽資料行。

#### <a name="syntax"></a>語法

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>參數

*變*<br/>
在要系結至書簽資料行的變數。

#### <a name="example"></a>範例

```cpp
class CArtistsBookmark
{
public:
// Data Elements
   CBookmark<4> m_bookmark;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

// Output binding map
BEGIN_COLUMN_MAP(CArtistsBookmark)
   BOOKMARK_ENTRY(m_bookmark)
   COLUMN_ENTRY(1, m_nAge)
   COLUMN_ENTRY(2, m_szFirstName)
   COLUMN_ENTRY(3, m_szLastName)
END_COLUMN_MAP()

   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_BOOKMARKS, true);
   }

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsBookmark, L" \
   SELECT \
      Age, \
      FirstName, \
      LastName \
      FROM Artists")
};
```

如需詳細資訊，請參閱[使用書簽](using-bookmarks.md)和[CBookmark 類別](../../data/oledb/cbookmark-class.md)。

### <a name="column_entry"></a><a name="column_entry"></a>COLUMN_ENTRY

代表資料列集的系結至資料列集中的特定資料行。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
[in] 資料行編號。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

COLUMN_ENTRY 宏會用於下列位置：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- 在[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

#### <a name="example"></a>範例

請參閱宏主題中的範例， [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="column_entry_ex"></a><a name="column_entry_ex"></a>COLUMN_ENTRY_EX

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
[in] 資料行編號。

*wType*<br/>
在資料類型。

*nLength*<br/>
在資料大小（以位元組為單位）。

*nPrecision*<br/>
在取得資料和*wType*時所要使用的最大有效位數 `DBTYPE_NUMERIC` 。 否則，會忽略這個參數。

*nScale*<br/>
在取得資料和*wType*時要使用的尺規是 `DBTYPE_NUMERIC` 或 `DBTYPE_DECIMAL` 。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

COLUMN_ENTRY_EX 宏會用於下列位置：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- 在[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

#### <a name="example"></a>範例

請參閱[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。

### <a name="column_entry_length"></a><a name="column_entry_length"></a>COLUMN_ENTRY_LENGTH

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
在從1開始的資料行編號。 書簽對應至資料行零。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

#### <a name="remarks"></a>備註

這個宏支援*length*變數。 這個參數可以用於下列狀況：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- 在[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_entry_length_status"></a><a name="column_entry_length_status"></a>COLUMN_ENTRY_LENGTH_STATUS

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
[in] 資料行編號。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

當您想要支援長度和狀態變數時，可使用這個巨集。 這個參數可以用於下列狀況：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- 在[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_entry_ps"></a><a name="column_entry_ps"></a>COLUMN_ENTRY_PS

代表資料列集的系結至資料列集中的特定資料行。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
[in] 資料行編號。

*nPrecision*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

可讓您指定要繫結之資料行的精確度和小數位數。 這個參數可以用於下列狀況：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- 在[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_entry_ps_length"></a><a name="column_entry_ps_length"></a>COLUMN_ENTRY_PS_LENGTH

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
在從1開始的資料行編號。 書簽對應至資料行零。

*nPrecision*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

#### <a name="remarks"></a>備註

可讓您指定要繫結之資料行的精確度和小數位數。 這個宏支援*length*變數。 這個參數可以用於下列狀況：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- 在[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_entry_ps_length_status"></a><a name="column_entry_ps_length_status"></a>COLUMN_ENTRY_PS_LENGTH_STATUS

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
[in] 資料行編號。

*nPrecision*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

可讓您指定要繫結之資料行的精確度和小數位數。 當您想要支援長度和狀態變數時，可使用這個巨集。 這個參數可以用於下列狀況：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- 在[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_entry_ps_status"></a><a name="column_entry_ps_status"></a>COLUMN_ENTRY_PS_STATUS

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
[in] 資料行編號。

*nPrecision*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

可讓您指定要繫結之資料行的精確度和小數位數。 這個宏支援*狀態*變數。 這個參數可以用於下列狀況：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- 在[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_entry_status"></a><a name="column_entry_status"></a>COLUMN_ENTRY_STATUS

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) 。

*nOrdinal*<br/>
[in] 資料行編號。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

這個宏支援*狀態*變數。 這個參數可以用於下列狀況：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- 在[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_entry_type"></a><a name="column_entry_type"></a>COLUMN_ENTRY_TYPE

表示資料庫中特定資料行的系結。 支援*型*別參數。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>參數

*nOrdinal*<br/>
[in] 資料行編號。

*wType*<br/>
在資料行輸入的資料類型。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

這個宏是[COLUMN_ENTRY](../../data/oledb/column-entry.md)宏的特製化變體，可提供指定資料類型的方法。

### <a name="column_entry_type_size"></a><a name="column_entry_type_size"></a>COLUMN_ENTRY_TYPE_SIZE

表示資料庫中特定資料行的系結。 支援*type*和*size*參數。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>參數

*nOrdinal*<br/>
[in] 資料行編號。

*wType*<br/>
在資料行輸入的資料類型。

*nLength*<br/>
在資料行輸入的大小（以位元組為單位）。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

這個宏是[COLUMN_ENTRY](../../data/oledb/column-entry.md)宏的特製化變體，可提供指定資料大小和類型的方法。

### <a name="column_name"></a><a name="column_name"></a>COLUMN_NAME

代表資料列集的系結至資料列集中的特定資料行。 類似于[COLUMN_ENTRY](../../data/oledb/column-entry.md)，不同之處在于這個宏會採用資料行名稱，而不是資料行編號。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

COLUMN_NAME_ * 宏會在與[COLUMN_ENTRY](../../data/oledb/column-entry.md)相同的位置中使用：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- 在[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_name_ex"></a><a name="column_name_ex"></a>COLUMN_NAME_EX

代表資料列集的系結至資料列集中的特定資料行。 類似于[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在于此宏也會採用資料類型、大小、有效位數、小數位數、資料行長度和資料行狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*wType*<br/>
在資料類型。

*nLength*<br/>
在資料大小（以位元組為單位）。

*nPrecision*<br/>
在取得資料和*wType*時所要使用的最大有效位數 `DBTYPE_NUMERIC` 。 否則，會忽略這個參數。

*nScale*<br/>
在取得資料和*wType*時要使用的尺規是 `DBTYPE_NUMERIC` 或 `DBTYPE_DECIMAL` 。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

如需 COLUMN_NAME_ * 宏使用位置的詳細資訊，請參閱[COLUMN_NAME](../../data/oledb/column-name.md) 。

### <a name="column_name_length"></a><a name="column_name_length"></a>COLUMN_NAME_LENGTH

代表資料列集的系結至資料列集中的特定資料行。 類似于[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在于此宏也會採用資料行長度。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

#### <a name="remarks"></a>備註

如需 COLUMN_NAME_ * 宏使用位置的詳細資訊，請參閱[COLUMN_NAME](../../data/oledb/column-name.md) 。

### <a name="column_name_length_status"></a><a name="column_name_length_status"></a>COLUMN_NAME_LENGTH_STATUS

代表資料列集的系結至資料列集中的特定資料行。 類似于[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在于此宏也會採用資料行長度和資料行狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

如需 COLUMN_NAME_ * 宏使用位置的詳細資訊，請參閱[COLUMN_NAME](../../data/oledb/column-name.md) 。

### <a name="column_name_ps"></a><a name="column_name_ps"></a>COLUMN_NAME_PS

代表資料列集的系結至資料列集中的特定資料行。 類似于[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在于此宏也會採用精確度和小數位數。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*nPrecision*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

如需 COLUMN_NAME_ * 宏使用位置的詳細資訊，請參閱[COLUMN_NAME](../../data/oledb/column-name.md) 。

### <a name="column_name_ps_length"></a><a name="column_name_ps_length"></a>COLUMN_NAME_PS_LENGTH

代表資料列集的系結至資料列集中的特定資料行。 類似于[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在于此宏也會採用精確度、小數位數和資料行長度。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*nPrecision*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

#### <a name="remarks"></a>備註

如需 COLUMN_NAME_ * 宏使用位置的詳細資訊，請參閱[COLUMN_NAME](../../data/oledb/column-name.md) 。

### <a name="column_name_ps_length_status"></a><a name="column_name_ps_length_status"></a>COLUMN_NAME_PS_LENGTH_STATUS

代表資料列集的系結至資料列集中的特定資料行。 類似于[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在于此宏也會採用精確度、小數位數、資料行長度和資料行狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*nPrecision*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

如需 COLUMN_NAME_ * 宏使用位置的詳細資訊，請參閱[COLUMN_NAME](../../data/oledb/column-name.md) 。

### <a name="column_name_ps_status"></a><a name="column_name_ps_status"></a>COLUMN_NAME_PS_STATUS

代表資料列集的系結至資料列集中的特定資料行。 類似于[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在于此宏也會採用精確度、小數位數和資料行狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*nPrecision*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

如需 COLUMN_NAME_ * 宏使用位置的詳細資訊，請參閱[COLUMN_NAME](../../data/oledb/column-name.md) 。

### <a name="column_name_status"></a><a name="column_name_status"></a>COLUMN_NAME_STATUS

代表資料列集的系結至資料列集中的特定資料行。 類似于[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在于此宏也會採用資料行狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

如需 COLUMN_NAME_ * 宏使用位置的詳細資訊，請參閱[COLUMN_NAME](../../data/oledb/column-name.md) 。

### <a name="column_name_type"></a><a name="column_name_type"></a>COLUMN_NAME_TYPE

代表資料列集的系結至資料列集中的特定資料行。 類似于[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在于此宏也會採用資料類型。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*wType*<br/>
在資料類型。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

如需 COLUMN_NAME_ * 宏使用位置的詳細資訊，請參閱[COLUMN_NAME](../../data/oledb/column-name.md) 。

### <a name="column_name_type_ps"></a><a name="column_name_type_ps"></a>COLUMN_NAME_TYPE_PS

代表資料列集的系結至資料列集中的特定資料行。 類似于[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在于此宏也會採用資料類型、有效位數和小數位數。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*wType*<br/>
在資料類型。

*nPrecision*<br/>
在取得資料和*wType*時所要使用的最大有效位數 `DBTYPE_NUMERIC` 。 否則，會忽略這個參數。

*nScale*<br/>
在取得資料和*wType*時要使用的尺規是 `DBTYPE_NUMERIC` 或 `DBTYPE_DECIMAL` 。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

如需 COLUMN_NAME_ * 宏使用位置的詳細資訊，請參閱[COLUMN_NAME](../../data/oledb/column-name.md) 。

### <a name="column_name_type_size"></a><a name="column_name_type_size"></a>COLUMN_NAME_TYPE_SIZE

代表資料列集的系結至資料列集中的特定資料行。 類似于[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在于此宏也會採用資料類型和大小。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*wType*<br/>
在資料類型。

*nLength*<br/>
在資料大小（以位元組為單位）。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

如需 COLUMN_NAME_ * 宏使用位置的詳細資訊，請參閱[COLUMN_NAME](../../data/oledb/column-name.md) 。

### <a name="column_name_type_status"></a><a name="column_name_type_status"></a>COLUMN_NAME_TYPE_STATUS

代表資料列集的系結至資料列集中的特定資料行。 類似于[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在于此宏也會接受資料類型和資料行狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以在名稱前面加上 ' L ' 來完成這項工作，例如： `L"MyColumn"` 。

*wType*<br/>
在資料類型。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

如需 COLUMN_NAME_ * 宏使用位置的詳細資訊，請參閱[COLUMN_NAME](../../data/oledb/column-name.md) 。

### <a name="end_column_map"></a><a name="end_column_map"></a>END_COLUMN_MAP

標記資料行對應專案的結尾。

#### <a name="syntax"></a>語法

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>備註

它會與資料列集上的單一存取子搭配使用。 BEGIN_COLUMN_MAP 宏是以 END_COLUMN_MAP 宏完成。

#### <a name="example"></a>範例

請參閱[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)。

### <a name="define_command"></a><a name="define_command"></a>DEFINE_COMMAND

指定使用[CCommand](../../data/oledb/ccommand-class.md)類別時，將用來建立資料列集的命令。 只接受符合指定之應用程式類型（ANSI 或 Unicode）的字串類型。

> [!NOTE]
> 建議您使用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) ，而不要使用 DEFINE_COMMAND。

#### <a name="syntax"></a>語法

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>參數

*x*<br/>
在使用者記錄（命令）類別的名稱。

*szCommand*<br/>
在使用[CCommand](../../data/oledb/ccommand-class.md)時，將用來建立資料列集的命令字串。

#### <a name="remarks"></a>備註

如果您未在[CCommand：： Open](../../data/oledb/ccommand-open.md)方法中指定命令文字，則會使用您指定的命令字串做為預設值。

如果您將應用程式建立為 ANSI，此宏會接受 ANSI 字串，如果您將應用程式建立為 Unicode 字串，則會接受 Unicode 字串。 建議您使用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是 DEFINE_COMMAND，因為前者會接受 Unicode 字串，而不論 ANSI 或 Unicode 應用程式類型為何。

#### <a name="example"></a>範例

請參閱[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。

### <a name="define_command_ex"></a><a name="define_command_ex"></a>DEFINE_COMMAND_EX

指定使用[CCommand](../../data/oledb/ccommand-class.md)類別時，將用來建立資料列集的命令。 支援 Unicode 和 ANSI 應用程式。

#### <a name="syntax"></a>語法

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>參數

*x*<br/>
在使用者記錄（命令）類別的名稱。

*wszCommand*<br/>
在使用[CCommand](../../data/oledb/ccommand-class.md)時，將用來建立資料列集的命令字串。

#### <a name="remarks"></a>備註

如果您未在[CCommand：： Open](../../data/oledb/ccommand-open.md)方法中指定命令文字，則會使用您指定的命令字串做為預設值。

無論應用程式類型為何，這個宏都會接受 Unicode 字串。 這個宏優先于[DEFINE_COMMAND](../../data/oledb/define-command.md) ，因為它支援 UNICODE 和 ANSI 應用程式。

#### <a name="example"></a>範例

請參閱[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。

### <a name="begin_param_map"></a><a name="begin_param_map"></a>BEGIN_PARAM_MAP

標記參數對應項目的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>參數

*x*<br/>
[in] 使用者資料錄類別的名稱。

#### <a name="remarks"></a>備註

[命令](/previous-versions/windows/desktop/ms724608(v=vs.85))會使用參數。

#### <a name="example"></a>範例

請參閱[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)宏的範例。

### <a name="end_param_map"></a><a name="end_param_map"></a>END_PARAM_MAP

標記參數對應專案的結尾。

#### <a name="syntax"></a>語法

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>範例

請參閱[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)宏的範例。

### <a name="set_param_type"></a><a name="set_param_type"></a>SET_PARAM_TYPE

指定遵循 SET_PARAM_TYPE 宏輸入、輸出或輸入/輸出 COLUMN_ENTRY 宏。

#### <a name="syntax"></a>語法

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>參數

*type*<br/>
[in] 用來設定參數的類型。

#### <a name="remarks"></a>備註

提供者只支援基礎資料來源支援的參數輸入/輸出類型。 類型是一或多個值的組合 `DBPARAMIO` （請參閱 OLE DB 程式設計*人員參考*中的[DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))）：

- `DBPARAMIO_NOTPARAM`存取子沒有任何參數。 一般來說，您會 `eParamIO` 在資料列存取子中將設定為此值，以提醒使用者參數被忽略。

- `DBPARAMIO_INPUT`輸入參數。

- `DBPARAMIO_OUTPUT`輸出參數。

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT`參數同時為輸入和輸出參數。

#### <a name="example"></a>範例

```cpp
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
```

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="see-also"></a>另請參閱

[OLE DB 取用者範本的宏和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
