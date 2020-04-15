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
ms.openlocfilehash: 8b898990672f590f6047eef6fdfd1ed7eecb3f92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369817"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>OLE DB 消費者樣板的巨集和全域函式

OLE DB 使用者範本包括以下宏和全域函數:

## <a name="global-functions"></a>全域功能

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|如果返回錯誤,則將 OLE DB 錯誤記錄資訊轉儲到轉儲設備。|

## <a name="accessor-map-macros"></a>存取器對應巨集

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|標記訪問器條目的開始。|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|標記存取子對應項目的開頭。|
|[END_ACCESSOR](#end_accessor)|標記訪問器條目的末尾。|
|[END_ACCESSOR_MAP](#end_accessor_map)|標記訪問器映射條目的末尾。|

## <a name="column-map-macros"></a>列對應巨集

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|在用戶記錄類中標記列映射條目的開頭。|
|[BLOB_ENTRY](#blob_entry)|用於綁定二進位大型物件 (BLOB)。|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|報告 BLOB 資料列的長度。|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|報告 BLOB 資料列的長度和狀態。|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|報告 BLOB 資料列的狀態。|
|[BLOB_NAME](#blob_name)|用於按列名稱綁定二進位大型物件。|
|[BLOB_NAME_LENGTH](#blob_name_length)|報告 BLOB 資料列的長度。|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|報告 BLOB 資料列的長度和狀態。|
|[BLOB_NAME_STATUS](#blob_name_status)|報告 BLOB 資料列的狀態。|
|[BOOKMARK_ENTRY](#bookmark_entry)|表示行集中的書籤條目。 書籤條目是一種特殊的列條目。|
|[COLUMN_ENTRY](#column_entry)|表示對資料庫中特定列的綁定。|
|[COLUMN_ENTRY_EX](#column_entry_ex)|表示對資料庫中特定列的綁定。 支援*類型*、*長度*、*精度*、*縮放*與*狀態*參數。|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|表示對資料庫中特定列的綁定。 支援*長度*變數。|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|表示對資料庫中特定列的綁定。 支援*狀態*和*長度*參數。|
|[COLUMN_ENTRY_PS](#column_entry_ps)|表示對資料庫中特定列的綁定。 支援*精度*和*縮放*參數。|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|表示對資料庫中特定列的綁定。 支援*長度*變數、*精度*和*比例*參數。|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|表示對資料庫中特定列的綁定。 支持*狀態*和*長度*變數、*精度*和*比例*參數。|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|表示對資料庫中特定列的綁定。 支持*狀態*變數、*精度*和*縮放*參數。|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|表示對資料庫中特定列的綁定。 支持*狀態*變數。|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|表示對資料庫中特定列的綁定。 支持*類型*參數。|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|表示對資料庫中特定列的綁定。 支援*類型*和*大小*參數。|
|[COLUMN_NAME](#column_name)|按名稱表示對資料庫中特定列的綁定。|
|[COLUMN_NAME_EX](#column_name_ex)|按名稱表示對資料庫中特定列的綁定。 支援資料類型、大小、精度、比例、列長度和列狀態的規範。|
|[COLUMN_NAME_LENGTH](#column_name_length)|按名稱表示對資料庫中特定列的綁定。 支援列長度的規範。|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|按名稱表示對資料庫中特定列的綁定。 支援列長度和狀態的規範。|
|[COLUMN_NAME_PS](#column_name_ps)|按名稱表示對資料庫中特定列的綁定。 支援精度和刻度的規格。|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|按名稱表示對資料庫中特定列的綁定。 支援精度、刻度和柱長的規格。|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|按名稱表示對資料庫中特定列的綁定。 支援精度、比例、列長度和列狀態的規範。|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|按名稱表示對資料庫中特定列的綁定。 支援精度、縮放和列狀態的規範。|
|[COLUMN_NAME_STATUS](#column_name_status)|按名稱表示對資料庫中特定列的綁定。 支援列狀態的規範。|
|[COLUMN_NAME_TYPE](#column_name_type)|按名稱表示對資料庫中特定列的綁定。 支持數據類型的規範。|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|按名稱表示對資料庫中特定列的綁定。 支持數據類型、精度和縮放的規範。|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|按名稱表示對資料庫中特定列的綁定。 支援數據類型和大小的規範。|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|按名稱表示對資料庫中特定列的綁定。 支援數據類型和列狀態的規範。|
|[END_COLUMN_MAP](#end_column_map)|標記列地圖條目的末尾。|

## <a name="command-macros"></a>命令巨集

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|指定在使用[CCommand](../../data/oledb/ccommand-class.md)類時將用於建立行集的命令。 僅接受與指定應用程式類型(ANSI 或 Unicode)匹配的字串類型。 建議您使用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是DEFINE_COMMAND。|
|[DEFINE_COMMAND_EX](#define_command_ex)|指定在使用[CCommand](../../data/oledb/ccommand-class.md)類時將用於建立行集的命令。 支援 ANSI 和 Unicode 應用程式。|

## <a name="parameter-map-macros"></a>參數對應巨集

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|在用戶記錄類中標記參數映射條目的開頭。|
|[END_PARAM_MAP](#end_param_map)|標記參數映射條目的末尾。|
|[SET_PARAM_TYPE](#set_param_type)|指定COLUMN_ENTRY宏,這些宏遵循SET_PARAM_TYPE宏作為輸入、輸出或輸入/輸出。|

### <a name="atltraceerrorrecords"></a><a name="atltraceerrorrecords"></a>AtlTrace錯誤記錄

如果返回錯誤,則將 OLE DB 錯誤記錄資訊轉儲到轉儲設備。

#### <a name="syntax"></a>語法

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>參數

*先生*<br/>
[在]由 OLE DB 消費者範本成員函數返回的 HRESULT。

#### <a name="remarks"></a>備註

如果未S_OK *hErr,* 則`AtlTraceErrorRecords`將 OLE DB 錯誤記錄資訊轉印到轉儲裝置(輸出視窗或檔的**調試**選項卡)。 從提供程式獲取的錯誤記錄資訊包括每個錯誤記錄條目的行號、源、說明、説明檔、上下文和 GUID。 `AtlTraceErrorRecords`僅在調試生成中轉儲此資訊。 在版本版本中,它是優化出來的空存根。有關詳細資訊,請參閱[CDBErrorInfo 類別](../../data/oledb/cdberrorinfo-class.md)。

### <a name="begin_accessor"></a><a name="begin_accessor"></a>BEGIN_ACCESSOR

標記訪問器條目的開始。

#### <a name="syntax"></a>語法

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>參數

*num*<br/>
[在]此訪問器映射中訪問器的零偏移數。

*bAuto*<br/>
[在]指定此訪問器是自動存取器還是手動存取器。 如果**為 true,** 則訪問器是自動的;如果為 true,則訪問器為自動訪問器。如果**為 false,** 則訪問器是手動的。 自動存取器意味著在行動操作中為您獲取資料。

#### <a name="remarks"></a>備註

對於行集中的多個訪問器,您需要為每個單獨的訪問器指定BEGIN_ACCESSOR_MAP並使用BEGIN_ACCESSOR宏。 BEGIN_ACCESSOR宏END_ACCESSOR宏一起完成。 BEGIN_ACCESSOR_MAP宏與END_ACCESSOR_MAP宏一起完成。

#### <a name="example"></a>範例

請參考[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="begin_accessor_map"></a><a name="begin_accessor_map"></a>BEGIN_ACCESSOR_MAP

標記存取子對應項目的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>參數

*X.*<br/>
[in] 使用者資料錄類別的名稱。

*num*<br/>
[in] 此存取子對應中的存取子數目。

#### <a name="remarks"></a>備註

對於行集中的多個訪問器,您需要在開始時指定BEGIN_ACCESSOR_MAP,並為每個單獨的訪問器使用BEGIN_ACCESSOR宏。 BEGIN_ACCESSOR宏END_ACCESSOR宏一起完成。 訪問器映射使用END_ACCESSOR_MAP宏完成。

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

標記訪問器條目的末尾。

#### <a name="syntax"></a>語法

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>備註

對於行集中的多個訪問器,您需要指定BEGIN_ACCESSOR_MAP,並為每個單獨的訪問器使用BEGIN_ACCESSOR宏。 BEGIN_ACCESSOR宏END_ACCESSOR宏一起完成。 BEGIN_ACCESSOR_MAP宏與END_ACCESSOR_MAP宏一起完成。

#### <a name="example"></a>範例

請參考[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="end_accessor_map"></a><a name="end_accessor_map"></a>END_ACCESSOR_MAP

標記訪問器映射條目的末尾。

#### <a name="syntax"></a>語法

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>備註

對於行集中的多個訪問器,您需要指定BEGIN_ACCESSOR_MAP,並為每個單獨的訪問器使用BEGIN_ACCESSOR宏。 BEGIN_ACCESSOR宏END_ACCESSOR宏一起完成。 BEGIN_ACCESSOR_MAP宏與END_ACCESSOR_MAP宏一起完成。

#### <a name="example"></a>範例

請參考[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="begin_column_map"></a><a name="begin_column_map"></a>BEGIN_COLUMN_MAP

標記資料行對應項目的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>參數

*X.*<br/>
[in] 衍生自 `CAccessor`之使用者資料錄類別的名稱。

#### <a name="remarks"></a>備註

如果資料列集上只有單一存取子，就會使用此巨集。 如果資料列集上有多個存取子，請使用 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

BEGIN_COLUMN_MAP宏END_COLUMN_MAP宏一起完成。 當使用者資料錄中只需要一個存取子時，就會使用此巨集。

資料行會對應至您想要繫結之資料列集中的欄位。

#### <a name="example"></a>範例

以下是範例資料行和參數對應︰

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a><a name="blob_entry"></a>BLOB_ENTRY

與BEGIN_COLUMN_MAP和END_COLUMN_MAP一起使用,以綁定二進位大型物件[(BLOB)。](/previous-versions/windows/desktop/ms711511(v=vs.85))

#### <a name="syntax"></a>語法

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>參數

*恩·奧迪納爾*<br/>
[in] 資料行編號。

*IID*<br/>
[在]介面 GUID,`IDD_ISequentialStream`如檢查的搜尋的 。

*標誌*<br/>
[在]由 OLE 結構化儲存模型定義的儲存模式標誌(`STGM_READ`例如。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="example"></a>範例

請參閱[如何檢索 BLOB?](../../data/oledb/retrieving-a-blob.md)

### <a name="blob_entry_length"></a><a name="blob_entry_length"></a>BLOB_ENTRY_LENGTH

與BEGIN_COLUMN_MAP和END_COLUMN_MAP一起使用,以綁定二進位大型物件[(BLOB)。](/previous-versions/windows/desktop/ms711511(v=vs.85)) 與[BLOB_ENTRY](../../data/oledb/blob-entry.md)類似 ,只不過此宏也獲取 BLOB 列的長度( 以位元組為單位)。

#### <a name="syntax"></a>語法

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>參數

*恩·奧迪納爾*<br/>
[in] 資料行編號。

*IID*<br/>
[在]介面 GUID,`IDD_ISequentialStream`如檢查的搜尋的 。

*標誌*<br/>
[在]由 OLE 結構化儲存模型定義的儲存模式標誌(`STGM_READ`例如。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*長度*<br/>
[出]BLOB 列的(實際)長度(以位元組為單位)。

#### <a name="example"></a>範例

請參閱[如何檢索 BLOB?](../../data/oledb/retrieving-a-blob.md)

### <a name="blob_entry_length_status"></a><a name="blob_entry_length_status"></a>BLOB_ENTRY_LENGTH_STATUS

與BEGIN_COLUMN_MAP和END_COLUMN_MAP一起使用,以綁定二進位大型物件[(BLOB)。](/previous-versions/windows/desktop/ms711511(v=vs.85)) 與[BLOB_ENTRY](../../data/oledb/blob-entry.md)類似 ,只不過此宏還可以獲取 BLOB 列的長度和狀態。

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

*恩·奧迪納爾*<br/>
[in] 資料行編號。

*IID*<br/>
[在]介面 GUID,`IDD_ISequentialStream`如檢查的搜尋的 。

*標誌*<br/>
[在]由 OLE 結構化儲存模型定義的儲存模式標誌(`STGM_READ`例如。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*長度*<br/>
[出]BLOB 列的(實際)長度(以位元組為單位)。

*狀態*<br/>
[出]BLOB 資料列的狀態。

#### <a name="example"></a>範例

請參閱[如何檢索 BLOB?](../../data/oledb/retrieving-a-blob.md)

### <a name="blob_entry_status"></a><a name="blob_entry_status"></a>BLOB_ENTRY_STATUS

與BEGIN_COLUMN_MAP或BEGIN_ACCESSOR_MAP一起使用,以綁定二進位大型物件[(BLOB)。](/previous-versions/windows/desktop/ms711511(v=vs.85)) 與[BLOB_ENTRY](../../data/oledb/blob-entry.md)類似 ,只不過此宏也獲取 BLOB 列的狀態。

#### <a name="syntax"></a>語法

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>參數

*恩·奧迪納爾*<br/>
[in] 資料行編號。

*IID*<br/>
[在]介面 GUID,`IDD_ISequentialStream`如檢查的搜尋的 。

*標誌*<br/>
[在]由 OLE 結構化儲存模型定義的儲存模式標誌(`STGM_READ`例如。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*狀態*<br/>
[出]BLOB 欄位的狀態。

#### <a name="example"></a>範例

請參閱[如何檢索 BLOB?](../../data/oledb/retrieving-a-blob.md)

### <a name="blob_name"></a><a name="blob_name"></a>BLOB_NAME

與BEGIN_COLUMN_MAP和END_COLUMN_MAP一起使用,以綁定二進位大型物件[(BLOB)。](/previous-versions/windows/desktop/ms711511(v=vs.85)) 與[BLOB_ENTRY](../../data/oledb/blob-entry.md)類似 ,只不過此宏採用列名而不是列號。

#### <a name="syntax"></a>語法

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*IID*<br/>
[在]介面 GUID,`IDD_ISequentialStream`如檢查的搜尋的 。

*標誌*<br/>
[在]由 OLE 結構化儲存模型定義的儲存模式標誌(`STGM_READ`例如。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="example"></a>範例

請參閱[如何檢索 BLOB?](../../data/oledb/retrieving-a-blob.md)

### <a name="blob_name_length"></a><a name="blob_name_length"></a>BLOB_NAME_LENGTH

與BEGIN_COLUMN_MAP和END_COLUMN_MAP一起使用,以綁定二進位大型物件[(BLOB)。](/previous-versions/windows/desktop/ms711511(v=vs.85)) 與[BLOB_NAME](../../data/oledb/blob-name.md)類似 ,只不過此宏還可以獲取 BLOB 資料列的長度( 以位元組為單位)。

#### <a name="syntax"></a>語法

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*IID*<br/>
[在]介面 GUID,`IDD_ISequentialStream`如檢查的搜尋的 。

*標誌*<br/>
[在]由 OLE 結構化儲存模型定義的儲存模式標誌(`STGM_READ`例如。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*長度*<br/>
[出]BLOB 列的(實際)長度(以位元組為單位)。

### <a name="blob_name_length_status"></a><a name="blob_name_length_status"></a>BLOB_NAME_LENGTH_STATUS

與BEGIN_COLUMN_MAP和END_COLUMN_MAP一起使用,以綁定二進位大型物件[(BLOB)。](/previous-versions/windows/desktop/ms711511(v=vs.85)) 與[BLOB_NAME](../../data/oledb/blob-name.md)類似 ,只不過此宏還可以獲取 BLOB 數據列的長度和狀態。

#### <a name="syntax"></a>語法

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*IID*<br/>
[在]介面 GUID,`IDD_ISequentialStream`如檢查的搜尋的 。

*標誌*<br/>
[在]由 OLE 結構化儲存模型定義的儲存模式標誌(`STGM_READ`例如。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*長度*<br/>
[出]BLOB 列的(實際)長度(以位元組為單位)。

*狀態*<br/>
[出]BLOB 欄位的狀態。

### <a name="blob_name_status"></a><a name="blob_name_status"></a>BLOB_NAME_STATUS

與BEGIN_COLUMN_MAP和END_COLUMN_MAP一起使用,以綁定二進位大型物件[(BLOB)。](/previous-versions/windows/desktop/ms711511(v=vs.85)) 與[BLOB_NAME](../../data/oledb/blob-name.md)類似 ,只不過此宏也獲取 BLOB 數據列的狀態。

#### <a name="syntax"></a>語法

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*IID*<br/>
[在]介面 GUID,`IDD_ISequentialStream`如檢查的搜尋的 。

*標誌*<br/>
[在]由 OLE 結構化儲存模型定義的儲存模式標誌(`STGM_READ`例如。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*狀態*<br/>
[出]BLOB 欄位的狀態。

### <a name="bookmark_entry"></a><a name="bookmark_entry"></a>BOOKMARK_ENTRY

綁定書簽列。

#### <a name="syntax"></a>語法

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>參數

*變動*<br/>
[在]要綁定到書籤列的變數。

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

有關詳細資訊,請參閱[使用書籤](using-bookmarks.md)和[CBookmark 類別](../../data/oledb/cbookmark-class.md)。

### <a name="column_entry"></a><a name="column_entry"></a>COLUMN_ENTRY

表示行集上對行集中特定列的綁定。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>參數

請參閱*OLE DB 程式師參考中的* [DBBINDING。](/previous-versions/windows/desktop/ms716845(v=vs.85))

*恩·奧迪納爾*<br/>
[in] 資料行編號。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

COLUMN_ENTRY巨集用於以下位置:

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- [在BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

#### <a name="example"></a>範例

請參閱宏主題中的範例[,BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="column_entry_ex"></a><a name="column_entry_ex"></a>COLUMN_ENTRY_EX

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>參數

請參閱*OLE DB 程式師參考中的* [DBBINDING。](/previous-versions/windows/desktop/ms716845(v=vs.85))

*恩·奧迪納爾*<br/>
[in] 資料行編號。

*wType*<br/>
[在]數據類型。

*N 長度*<br/>
[在]數據大小(以位元組為單位)。

*n精密*<br/>
[在]取得資料與*wType*時使用的最大精確`DBTYPE_NUMERIC`度為 。 否則,將忽略此參數。

*nScale*<br/>
[在]取得資料與*wType*時要使用`DBTYPE_NUMERIC`的比例`DBTYPE_DECIMAL`為或 。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*長度*<br/>
[in] 要繫結至資料行長度的變數。

*狀態*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

COLUMN_ENTRY_EX巨集用於以下位置:

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- [在BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

#### <a name="example"></a>範例

請參考[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。

### <a name="column_entry_length"></a><a name="column_entry_length"></a>COLUMN_ENTRY_LENGTH

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>參數

請參閱*OLE DB 程式師參考中的* [DBBINDING。](/previous-versions/windows/desktop/ms716845(v=vs.85))

*恩·奧迪納爾*<br/>
[在]列號,以 1 開頭。 書籤對應於列零。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*長度*<br/>
[in] 要繫結至資料行長度的變數。

#### <a name="remarks"></a>備註

此宏支援*長度*變數。 這個參數可以用於下列狀況：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- [在BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_entry_length_status"></a><a name="column_entry_length_status"></a>COLUMN_ENTRY_LENGTH_STATUS

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>參數

請參閱*OLE DB 程式師參考中的* [DBBINDING。](/previous-versions/windows/desktop/ms716845(v=vs.85))

*恩·奧迪納爾*<br/>
[in] 資料行編號。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*長度*<br/>
[in] 要繫結至資料行長度的變數。

*狀態*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

當您想要支援長度和狀態變數時，可使用這個巨集。 這個參數可以用於下列狀況：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- [在BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_entry_ps"></a><a name="column_entry_ps"></a>COLUMN_ENTRY_PS

表示行集上對行集中特定列的綁定。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>參數

請參閱*OLE DB 程式師參考中的* [DBBINDING。](/previous-versions/windows/desktop/ms716845(v=vs.85))

*恩·奧迪納爾*<br/>
[in] 資料行編號。

*n精密*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

可讓您指定要繫結之資料行的精確度和小數位數。 這個參數可以用於下列狀況：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- [在BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_entry_ps_length"></a><a name="column_entry_ps_length"></a>COLUMN_ENTRY_PS_LENGTH

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>參數

請參閱*OLE DB 程式師參考中的* [DBBINDING。](/previous-versions/windows/desktop/ms716845(v=vs.85))

*恩·奧迪納爾*<br/>
[在]列號,以 1 開頭。 書籤對應於列零。

*n精密*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*長度*<br/>
[in] 要繫結至資料行長度的變數。

#### <a name="remarks"></a>備註

可讓您指定要繫結之資料行的精確度和小數位數。 此宏支援*長度*變數。 這個參數可以用於下列狀況：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- [在BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_entry_ps_length_status"></a><a name="column_entry_ps_length_status"></a>COLUMN_ENTRY_PS_LENGTH_STATUS

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>參數

請參閱*OLE DB 程式師參考中的* [DBBINDING。](/previous-versions/windows/desktop/ms716845(v=vs.85))

*恩·奧迪納爾*<br/>
[in] 資料行編號。

*n精密*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*長度*<br/>
[in] 要繫結至資料行長度的變數。

*狀態*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

可讓您指定要繫結之資料行的精確度和小數位數。 當您想要支援長度和狀態變數時，可使用這個巨集。 這個參數可以用於下列狀況：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- [在BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_entry_ps_status"></a><a name="column_entry_ps_status"></a>COLUMN_ENTRY_PS_STATUS

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>參數

請參閱*OLE DB 程式師參考中的* [DBBINDING。](/previous-versions/windows/desktop/ms716845(v=vs.85))

*恩·奧迪納爾*<br/>
[in] 資料行編號。

*n精密*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*狀態*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

可讓您指定要繫結之資料行的精確度和小數位數。 此宏支持*狀態*變數。 這個參數可以用於下列狀況：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- [在BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_entry_status"></a><a name="column_entry_status"></a>COLUMN_ENTRY_STATUS

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>參數

請參閱*OLE DB 程式師參考中的* [DBBINDING。](/previous-versions/windows/desktop/ms716845(v=vs.85))

*恩·奧迪納爾*<br/>
[in] 資料行編號。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*狀態*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

此宏支持*狀態*變數。 這個參數可以用於下列狀況：

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- [在BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_entry_type"></a><a name="column_entry_type"></a>COLUMN_ENTRY_TYPE

表示對資料庫中特定列的綁定。 支持*類型*參數。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>參數

*恩·奧迪納爾*<br/>
[in] 資料行編號。

*wType*<br/>
[在]列條目的數據類型。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

此宏是[COLUMN_ENTRY](../../data/oledb/column-entry.md)宏的專用變體,它提供了指定數據類型的方法。

### <a name="column_entry_type_size"></a><a name="column_entry_type_size"></a>COLUMN_ENTRY_TYPE_SIZE

表示對資料庫中特定列的綁定。 支援*類型*和*大小*參數。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>參數

*恩·奧迪納爾*<br/>
[in] 資料行編號。

*wType*<br/>
[在]列條目的數據類型。

*N 長度*<br/>
[在]列條目的大小(以位元組為單位)。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

此宏是[COLUMN_ENTRY](../../data/oledb/column-entry.md)宏的專用變體,它提供了指定數據大小和類型的方法。

### <a name="column_name"></a><a name="column_name"></a>COLUMN_NAME

表示行集上對行集中特定列的綁定。 與[COLUMN_ENTRY](../../data/oledb/column-entry.md)類似 ,只不過此宏採用列名稱而不是列號。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

COLUMN_NAME_* 宏在與[COLUMN_ENTRY](../../data/oledb/column-entry.md)相同的位置使用:

- 在[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)和[END_COLUMN_MAP](../../data/oledb/end-column-map.md)宏之間。

- [在BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)和[END_ACCESSOR](../../data/oledb/end-accessor.md)宏之間。

- 在[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)和[END_PARAM_MAP](../../data/oledb/end-param-map.md)宏之間。

### <a name="column_name_ex"></a><a name="column_name_ex"></a>COLUMN_NAME_EX

表示行集上對行集中特定列的綁定。 與[COLUMN_NAME](../../data/oledb/column-name.md)類似 ,只不過此宏還採用數據類型、大小、精度、比例、列長度和列狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*wType*<br/>
[在]數據類型。

*N 長度*<br/>
[在]數據大小(以位元組為單位)。

*n精密*<br/>
[在]取得資料與*wType*時使用的最大精確`DBTYPE_NUMERIC`度為 。 否則,將忽略此參數。

*nScale*<br/>
[在]取得資料與*wType*時要使用`DBTYPE_NUMERIC`的比例`DBTYPE_DECIMAL`為或 。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*長度*<br/>
[in] 要繫結至資料行長度的變數。

*狀態*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

有關COLUMN_NAME_* 宏的使用位置的資訊,請參閱[COLUMN_NAME。](../../data/oledb/column-name.md)

### <a name="column_name_length"></a><a name="column_name_length"></a>COLUMN_NAME_LENGTH

表示行集上對行集中特定列的綁定。 與[COLUMN_NAME](../../data/oledb/column-name.md)類似 ,只不過此宏也採用列長度。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*長度*<br/>
[in] 要繫結至資料行長度的變數。

#### <a name="remarks"></a>備註

有關COLUMN_NAME_* 宏的使用位置的資訊,請參閱[COLUMN_NAME。](../../data/oledb/column-name.md)

### <a name="column_name_length_status"></a><a name="column_name_length_status"></a>COLUMN_NAME_LENGTH_STATUS

表示行集上對行集中特定列的綁定。 與[COLUMN_NAME](../../data/oledb/column-name.md)類似 ,只不過此宏也採用列長度和列狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*長度*<br/>
[in] 要繫結至資料行長度的變數。

*狀態*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

有關COLUMN_NAME_* 宏的使用位置的資訊,請參閱[COLUMN_NAME。](../../data/oledb/column-name.md)

### <a name="column_name_ps"></a><a name="column_name_ps"></a>COLUMN_NAME_PS

表示行集上對行集中特定列的綁定。 與[COLUMN_NAME](../../data/oledb/column-name.md)類似 ,只不過此宏也需要精度和縮放。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*n精密*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

有關COLUMN_NAME_* 宏的使用位置的資訊,請參閱[COLUMN_NAME。](../../data/oledb/column-name.md)

### <a name="column_name_ps_length"></a><a name="column_name_ps_length"></a>COLUMN_NAME_PS_LENGTH

表示行集上對行集中特定列的綁定。 與[COLUMN_NAME](../../data/oledb/column-name.md)類似 ,只不過此宏也採用精度、縮放和列長度。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*n精密*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*長度*<br/>
[in] 要繫結至資料行長度的變數。

#### <a name="remarks"></a>備註

有關COLUMN_NAME_* 宏的使用位置的資訊,請參閱[COLUMN_NAME。](../../data/oledb/column-name.md)

### <a name="column_name_ps_length_status"></a><a name="column_name_ps_length_status"></a>COLUMN_NAME_PS_LENGTH_STATUS

表示行集上對行集中特定列的綁定。 與[COLUMN_NAME](../../data/oledb/column-name.md)類似 ,只不過此宏也採用精度、縮放、列長度和列狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*n精密*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*長度*<br/>
[in] 要繫結至資料行長度的變數。

*狀態*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

有關COLUMN_NAME_* 宏的使用位置的資訊,請參閱[COLUMN_NAME。](../../data/oledb/column-name.md)

### <a name="column_name_ps_status"></a><a name="column_name_ps_status"></a>COLUMN_NAME_PS_STATUS

表示行集上對行集中特定列的綁定。 與[COLUMN_NAME](../../data/oledb/column-name.md)類似 ,只不過此宏也採用精度、縮放和列狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*n精密*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*狀態*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

有關COLUMN_NAME_* 宏的使用位置的資訊,請參閱[COLUMN_NAME。](../../data/oledb/column-name.md)

### <a name="column_name_status"></a><a name="column_name_status"></a>COLUMN_NAME_STATUS

表示行集上對行集中特定列的綁定。 與[COLUMN_NAME](../../data/oledb/column-name.md)類似 ,只不過此宏也採用列狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

*狀態*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

有關COLUMN_NAME_* 宏的使用位置的資訊,請參閱[COLUMN_NAME。](../../data/oledb/column-name.md)

### <a name="column_name_type"></a><a name="column_name_type"></a>COLUMN_NAME_TYPE

表示行集上對行集中特定列的綁定。 與[COLUMN_NAME](../../data/oledb/column-name.md)類似 ,只不過此宏也採用數據類型。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*wType*<br/>
[在]數據類型。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

有關COLUMN_NAME_* 宏的使用位置的資訊,請參閱[COLUMN_NAME。](../../data/oledb/column-name.md)

### <a name="column_name_type_ps"></a><a name="column_name_type_ps"></a>COLUMN_NAME_TYPE_PS

表示行集上對行集中特定列的綁定。 與[COLUMN_NAME](../../data/oledb/column-name.md)類似 ,只不過此宏也採用數據類型、精度和縮放。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*wType*<br/>
[在]數據類型。

*n精密*<br/>
[在]取得資料與*wType*時使用的最大精確`DBTYPE_NUMERIC`度為 。 否則,將忽略此參數。

*nScale*<br/>
[在]取得資料與*wType*時要使用`DBTYPE_NUMERIC`的比例`DBTYPE_DECIMAL`為或 。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

有關COLUMN_NAME_* 宏的使用位置的資訊,請參閱[COLUMN_NAME。](../../data/oledb/column-name.md)

### <a name="column_name_type_size"></a><a name="column_name_type_size"></a>COLUMN_NAME_TYPE_SIZE

表示行集上對行集中特定列的綁定。 與[COLUMN_NAME](../../data/oledb/column-name.md)類似 ,只不過此宏也採用數據類型和大小。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*wType*<br/>
[在]數據類型。

*N 長度*<br/>
[在]數據大小(以位元組為單位)。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

有關COLUMN_NAME_* 宏的使用位置的資訊,請參閱[COLUMN_NAME。](../../data/oledb/column-name.md)

### <a name="column_name_type_status"></a><a name="column_name_type_status"></a>COLUMN_NAME_TYPE_STATUS

表示行集上對行集中特定列的綁定。 與[COLUMN_NAME](../../data/oledb/column-name.md)類似 ,只不過此宏也採用數據類型和列狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[在]指向列名稱的指標。 名稱必須是 Unicode 字串。 例如,可以通過在名稱前面放置一個"L"來實現此目的`L"MyColumn"`。

*wType*<br/>
[在]數據類型。

*狀態*<br/>
[in] 要繫結至資料行狀態的變數。

*資料*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

有關COLUMN_NAME_* 宏的使用位置的資訊,請參閱[COLUMN_NAME。](../../data/oledb/column-name.md)

### <a name="end_column_map"></a><a name="end_column_map"></a>END_COLUMN_MAP

標記列地圖條目的末尾。

#### <a name="syntax"></a>語法

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>備註

它與行集中的單個訪問器一起使用。 BEGIN_COLUMN_MAP宏END_COLUMN_MAP宏一起完成。

#### <a name="example"></a>範例

請參閱[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)。

### <a name="define_command"></a><a name="define_command"></a>DEFINE_COMMAND

指定在使用[CCommand](../../data/oledb/ccommand-class.md)類時將用於建立行集的命令。 僅接受與指定應用程式類型(ANSI 或 Unicode)匹配的字串類型。

> [!NOTE]
> 建議您使用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是DEFINE_COMMAND。

#### <a name="syntax"></a>語法

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>參數

*X.*<br/>
[在]使用者記錄(命令)類的名稱。

*szCommand*<br/>
[在]使用[CCommand](../../data/oledb/ccommand-class.md)時將用於建立列集的命令字串。

#### <a name="remarks"></a>備註

如果不在[CCommand::open](../../data/oledb/ccommand-open.md)方法中指定命令文本,則指定的命令字串將用作預設值。

如果將應用程式構建為 ANSI,則此宏接受 ANSI 字串;如果將應用程式構建為 Unicode,則此宏接受 Unicode 字串。 建議您使用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是DEFINE_COMMAND,因為前者接受 Unicode 字串,而不考慮 ANSI 或 Unicode 應用程式類型。

#### <a name="example"></a>範例

請參考[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。

### <a name="define_command_ex"></a><a name="define_command_ex"></a>DEFINE_COMMAND_EX

指定在使用[CCommand](../../data/oledb/ccommand-class.md)類時將用於建立行集的命令。 支援 Unicode 和 ANSI 應用程式。

#### <a name="syntax"></a>語法

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>參數

*X.*<br/>
[在]使用者記錄(命令)類的名稱。

*wszCommand*<br/>
[在]使用[CCommand](../../data/oledb/ccommand-class.md)時將用於建立列集的命令字串。

#### <a name="remarks"></a>備註

如果不在[CCommand::open](../../data/oledb/ccommand-open.md)方法中指定命令文本,則指定的命令字串將用作預設值。

此宏接受 Unicode 字串,而不考慮應用程式類型。 此宏優先於[DEFINE_COMMAND](../../data/oledb/define-command.md)因為它支援 Unicode 和 ANSI 應用程式。

#### <a name="example"></a>範例

請參考[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。

### <a name="begin_param_map"></a><a name="begin_param_map"></a>BEGIN_PARAM_MAP

標記參數對應項目的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>參數

*X.*<br/>
[in] 使用者資料錄類別的名稱。

#### <a name="remarks"></a>備註

參數由[命令](/previous-versions/windows/desktop/ms724608(v=vs.85))使用。

#### <a name="example"></a>範例

請參閱[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)宏的示例。

### <a name="end_param_map"></a><a name="end_param_map"></a>END_PARAM_MAP

標記參數映射條目的末尾。

#### <a name="syntax"></a>語法

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>範例

請參閱[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)宏的示例。

### <a name="set_param_type"></a><a name="set_param_type"></a>SET_PARAM_TYPE

指定COLUMN_ENTRY宏遵循SET_PARAM_TYPE宏輸入、輸出或輸入/輸出。

#### <a name="syntax"></a>語法

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>參數

*型別*<br/>
[in] 用來設定參數的類型。

#### <a name="remarks"></a>備註

提供者只支援基礎資料來源支援的參數輸入/輸出類型。 該類型是一個或多個`DBPARAMIO`值的組合(請參閱 OLE DB*程式設計師參考*中的[DBBINDING 結構](/previous-versions/windows/desktop/ms716845(v=vs.85))):

- `DBPARAMIO_NOTPARAM`訪問器沒有參數。 通常,在行`eParamIO`訪問器中設置為此值以提醒使用者參數被忽略。

- `DBPARAMIO_INPUT`輸入參數。

- `DBPARAMIO_OUTPUT`輸出參數。

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT`該參數既是輸入參數,也是輸出參數。

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

[OLE DB 使用者範本的巨集和全域函數](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
