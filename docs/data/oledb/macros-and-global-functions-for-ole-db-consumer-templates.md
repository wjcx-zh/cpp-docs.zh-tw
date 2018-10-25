---
title: 巨集和全域函式的 OLE DB 消費者樣板 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8077714292929b66d7e03014aa567f524a2709dc
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069163"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>OLE DB 消費者樣板的巨集和全域函式

OLE DB 消費者範本包括下列巨集和全域函式：

## <a name="global-functions"></a>全域函式

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|如果傳回錯誤，傾印到傾印裝置的 OLE DB 錯誤記錄資訊。|

## <a name="accessor-map-macros"></a>存取子對應巨集

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|標記存取子項目的開頭。|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|標記存取子對應項目的開頭。|
|[END_ACCESSOR](#end_accessor)|標記存取子項目的結尾。|
|[END_ACCESSOR_MAP](#end_accessor_map)|標記存取子對應項目的結尾。|

## <a name="column-map-macros"></a>資料行對應巨集

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|標記資料行對應中的項目使用者記錄類別開頭。|
|[BLOB_ENTRY](#blob_entry)|使用繫結二進位大型物件 (BLOB)。|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|報告的 BLOB 資料行的長度。|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|報告的長度和 BLOB 資料行的狀態。|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|報告的 BLOB 資料行的狀態。|
|[BLOB_NAME](#blob_name)|用來將二進位大型物件繫結資料行名稱。|
|[BLOB_NAME_LENGTH](#blob_name_length)|報告的 BLOB 資料行的長度。|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|報告的長度和 BLOB 資料行的狀態。|
|[BLOB_NAME_STATUS](#blob_name_status)|報告的 BLOB 資料行的狀態。|
|[BOOKMARK_ENTRY](#bookmark_entry)|表示資料列集上的書籤項目。 書籤項目是一種特殊的資料行項目。|
|[COLUMN_ENTRY](#column_entry)|表示在資料庫中的特定資料行的繫結。|
|[COLUMN_ENTRY_EX](#column_entry_ex)|表示在資料庫中的特定資料行的繫結。 支援*型別*，*長度*，*精確度*，*擴展*，以及*狀態*參數。|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|表示在資料庫中的特定資料行的繫結。 支援*長度*變數。|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|表示在資料庫中的特定資料行的繫結。 支援*狀態*並*長度*參數。|
|[COLUMN_ENTRY_PS](#column_entry_ps)|表示在資料庫中的特定資料行的繫結。 支援*有效位數*並*擴展*參數。|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|表示在資料庫中的特定資料行的繫結。 支援*長度*變數*有效位數*並*擴展*參數。|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|表示在資料庫中的特定資料行的繫結。 支援*狀態*並*長度*變數，*精確度*並*擴展*參數。|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|表示在資料庫中的特定資料行的繫結。 支援*狀態*變數*有效位數*並*擴展*參數。|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|表示在資料庫中的特定資料行的繫結。 支援*狀態*變數。|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|表示在資料庫中的特定資料行的繫結。 支援*型別*參數。|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|表示在資料庫中的特定資料行的繫結。 支援*型別*並*大小*參數。|
|[COLUMN_NAME](#column_name)|表示繫結至資料庫中的特定資料行的名稱。|
|[COLUMN_NAME_EX](#column_name_ex)|表示繫結至資料庫中的特定資料行的名稱。 支援資料類型、 大小、 有效位數、 小數位數、 資料行的長度，以及資料行狀態的規格。|
|[COLUMN_NAME_LENGTH](#column_name_length)|表示繫結至資料庫中的特定資料行的名稱。 支援資料行長度的規格。|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|表示繫結至資料庫中的特定資料行的名稱。 支援的資料行的長度和狀態的規格。|
|[COLUMN_NAME_PS](#column_name_ps)|表示繫結至資料庫中的特定資料行的名稱。 支援的有效位數和小數位數的規格。|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|表示繫結至資料庫中的特定資料行的名稱。 支援有效位數、 小數位數和資料行的長度的規格。|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|表示繫結至資料庫中的特定資料行的名稱。 支援的有效位數、 小數位數、 資料行長度和資料行狀態的規格。|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|表示繫結至資料庫中的特定資料行的名稱。 支援有效位數、 小數位數和資料行的狀態的指定。|
|[COLUMN_NAME_STATUS](#column_name_status)|表示繫結至資料庫中的特定資料行的名稱。 支援的資料行狀態的規格。|
|[COLUMN_NAME_TYPE](#column_name_type)|表示繫結至資料庫中的特定資料行的名稱。 支援資料類型的規格。|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|表示繫結至資料庫中的特定資料行的名稱。 支援的資料類型、 有效位數和小數位數的規格。|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|表示繫結至資料庫中的特定資料行的名稱。 支援的資料類型和大小的規格。|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|表示繫結至資料庫中的特定資料行的名稱。 支援的資料類型和資料行狀態的規格。|
|[END_COLUMN_MAP](#end_column_map)|結束標記的資料行的對應項目。|

## <a name="command-macros"></a>命令巨集

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|指定將用於建立資料列集時使用的命令[CCommand](../../data/oledb/ccommand-class.md)類別。 只接受字串類型符合指定的應用程式類型 （ANSI 或 Unicode）。 建議您改用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是 DEFINE_COMMAND。|
|[DEFINE_COMMAND_EX](#define_command_ex)|指定將用於建立資料列集時使用的命令[CCommand](../../data/oledb/ccommand-class.md)類別。 支援 ANSI 和 Unicode 應用程式。|

## <a name="parameter-map-macros"></a>參數對應巨集

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|標記參數對應中的項目使用者記錄類別開頭。|
|[END_PARAM_MAP](#end_param_map)|標記參數對應項目的結尾。|
|[SET_PARAM_TYPE](#set_param_type)|指定依照 SET_PARAM_TYPE 巨集做為輸入、 輸出或輸入/輸出的 COLUMN_ENTRY 巨集。|

### <a name="atltraceerrorrecords"></a> AtlTraceErrorRecords

如果傳回錯誤，傾印到傾印裝置的 OLE DB 錯誤記錄資訊。

#### <a name="syntax"></a>語法

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>參數

*hErr*<br/>
[in]OLE DB 消費者樣板成員函式所傳回的 HRESULT。

#### <a name="remarks"></a>備註

如果*hErr*不是 s_ok 時，`AtlTraceErrorRecords`傾印到傾印裝置的 OLE DB 錯誤記錄資訊 (**偵錯** 索引標籤的 輸出 視窗或檔案)。 錯誤記錄資訊，這取自於提供者，包含每個錯誤記錄項目資料列數、 來源、 描述、 說明檔、 內容和 GUID。 `AtlTraceErrorRecords` 這項資訊只在偵錯組建會傾印。 在發行組建中，它是空白的虛設出最適合。

#### <a name="see-also"></a>另請參閱

[CDBErrorInfo 類別](../../data/oledb/cdberrorinfo-class.md)

### <a name="begin_accessor"></a> BEGIN_ACCESSOR

標記存取子項目的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>參數

*num*<br/>
[in]存取子，這個存取子對應中零位移數字。

*bAuto*<br/>
[in]指定這個存取子是否自動存取子或手動存取子。 如果**真**，存取子會是自動; 如果**false**，存取子是手動。 自動存取子會表示為您擷取的資料移動作業。

#### <a name="remarks"></a>備註

在多個資料列集的存取子，您需要指定 BEGIN_ACCESSOR_MAP BEGIN_ACCESSOR 巨集用於每個個別存取子。 BEGIN_ACCESSOR 巨集完成 END_ACCESSOR 巨集。 BEGIN_ACCESSOR_MAP 巨集完成 END_ACCESSOR_MAP 巨集。

#### <a name="example"></a>範例

請參閱[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="begin_accessor_map"></a> BEGIN_ACCESSOR_MAP

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

在多個資料列集的存取子，您需要在開頭指定 BEGIN_ACCESSOR_MAP BEGIN_ACCESSOR 巨集用於每個個別存取子。 BEGIN_ACCESSOR 巨集完成 END_ACCESSOR 巨集。 END_ACCESSOR_MAP 巨集完成存取子對應。

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

### <a name="end_accessor"></a> END_ACCESSOR

標記存取子項目的結尾。

#### <a name="syntax"></a>語法

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>備註

針對多個資料列集的存取子，您需要指定 BEGIN_ACCESSOR_MAP BEGIN_ACCESSOR 巨集用於每個個別存取子。 BEGIN_ACCESSOR 巨集完成 END_ACCESSOR 巨集。 BEGIN_ACCESSOR_MAP 巨集完成 END_ACCESSOR_MAP 巨集。

#### <a name="example"></a>範例

請參閱[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="end_accessor_map"></a> END_ACCESSOR_MAP

標記存取子對應項目的結尾。

#### <a name="syntax"></a>語法

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>備註

針對多個資料列集的存取子，您需要指定 BEGIN_ACCESSOR_MAP BEGIN_ACCESSOR 巨集用於每個個別存取子。 BEGIN_ACCESSOR 巨集完成 END_ACCESSOR 巨集。 BEGIN_ACCESSOR_MAP 巨集完成 END_ACCESSOR_MAP 巨集。

#### <a name="example"></a>範例

請參閱[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="begin_column_map"></a> BEGIN_COLUMN_MAP

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

BEGIN_COLUMN_MAP 巨集完成 END_COLUMN_MAP 巨集。 當使用者資料錄中只需要一個存取子時，就會使用此巨集。

資料行會對應至您想要繫結之資料列集中的欄位。

#### <a name="example"></a>範例

以下是範例資料行和參數對應︰

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a> BLOB_ENTRY

BEGIN_COLUMN_MAP 與 END_COLUMN_MAP 用以繫結的二進位大型物件 ([BLOB](/previous-versions/windows/desktop/ms711511))。

#### <a name="syntax"></a>語法

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>參數

*nOrdinal*<br/>
[in] 資料行編號。

*IID*<br/>
[in]介面的 GUID，例如`IDD_ISequentialStream`，用來擷取 BLOB。

*flags*<br/>
[in]儲存模式加上旗標所定義的 OLE 結構化儲存體模型 (例如`STGM_READ`)。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="example"></a>範例

請參閱[我要如何擷取 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_entry_length"></a> BLOB_ENTRY_LENGTH

BEGIN_COLUMN_MAP 與 END_COLUMN_MAP 用以繫結的二進位大型物件 ([BLOB](/previous-versions/windows/desktop/ms711511))。 類似於[BLOB_ENTRY](../../data/oledb/blob-entry.md)，只不過這個巨集也會取得長度以位元組為單位的 BLOB 資料行。

#### <a name="syntax"></a>語法

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>參數

*nOrdinal*<br/>
[in] 資料行編號。

*IID*<br/>
[in]介面的 GUID，例如`IDD_ISequentialStream`，用來擷取 BLOB。

*flags*<br/>
[in]儲存模式加上旗標所定義的 OLE 結構化儲存體模型 (例如`STGM_READ`)。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[out]BLOB 資料行 （實際） 長度，以位元組為單位。

#### <a name="example"></a>範例

請參閱[我要如何擷取 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_entry_length_status"></a> BLOB_ENTRY_LENGTH_STATUS

BEGIN_COLUMN_MAP 與 END_COLUMN_MAP 用以繫結的二進位大型物件 ([BLOB](/previous-versions/windows/desktop/ms711511))。 類似於[BLOB_ENTRY](../../data/oledb/blob-entry.md)，只不過這個巨集也會取得的長度和 BLOB 資料行的狀態。

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
[in]介面的 GUID，例如`IDD_ISequentialStream`，用來擷取 BLOB。

*flags*<br/>
[in]儲存模式加上旗標所定義的 OLE 結構化儲存體模型 (例如`STGM_READ`)。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[out]BLOB 資料行 （實際） 長度，以位元組為單位。

*status*<br/>
[out]BLOB 資料行的狀態。

#### <a name="example"></a>範例

請參閱[我要如何擷取 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_entry_status"></a> BLOB_ENTRY_STATUS

BEGIN_COLUMN_MAP 或 BEGIN_ACCESSOR_MAP 用以繫結的二進位大型物件 ([BLOB](/previous-versions/windows/desktop/ms711511))。 類似於[BLOB_ENTRY](../../data/oledb/blob-entry.md)，只不過這個巨集也會取得 BLOB 資料行的狀態。

#### <a name="syntax"></a>語法

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>參數

*nOrdinal*<br/>
[in] 資料行編號。

*IID*<br/>
[in]介面的 GUID，例如`IDD_ISequentialStream`，用來擷取 BLOB。

*flags*<br/>
[in]儲存模式加上旗標所定義的 OLE 結構化儲存體模型 (例如`STGM_READ`)。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*status*<br/>
[out]BLOB 欄位的狀態。

#### <a name="example"></a>範例

請參閱[我要如何擷取 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_name"></a> BLOB_NAME

BEGIN_COLUMN_MAP 與 END_COLUMN_MAP 用以繫結的二進位大型物件 ([BLOB](/previous-versions/windows/desktop/ms711511))。 類似於[BLOB_ENTRY](../../data/oledb/blob-entry.md)，只不過這個巨集接受的資料行名稱，而不是資料行編號。

#### <a name="syntax"></a>語法

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*IID*<br/>
[in]介面的 GUID，例如`IDD_ISequentialStream`，用來擷取 BLOB。

*flags*<br/>
[in]儲存模式加上旗標所定義的 OLE 結構化儲存體模型 (例如`STGM_READ`)。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="example"></a>範例

請參閱[我要如何擷取 BLOB？](../../data/oledb/retrieving-a-blob.md)。

### <a name="blob_name_length"></a> BLOB_NAME_LENGTH

BEGIN_COLUMN_MAP 與 END_COLUMN_MAP 用以繫結的二進位大型物件 ([BLOB](/previous-versions/windows/desktop/ms711511))。 類似於[BLOB_NAME](../../data/oledb/blob-name.md)，只不過這個巨集也會取得長度以位元組為單位的 BLOB 資料行。

#### <a name="syntax"></a>語法

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*IID*<br/>
[in]介面的 GUID，例如`IDD_ISequentialStream`，用來擷取 BLOB。

*flags*<br/>
[in]儲存模式加上旗標所定義的 OLE 結構化儲存體模型 (例如`STGM_READ`)。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[out]BLOB 資料行 （實際） 長度，以位元組為單位。

### <a name="blob_name_length_status"></a> BLOB_NAME_LENGTH_STATUS

BEGIN_COLUMN_MAP 與 END_COLUMN_MAP 用以繫結的二進位大型物件 ([BLOB](/previous-versions/windows/desktop/ms711511))。 類似於[BLOB_NAME](../../data/oledb/blob-name.md)，只不過這個巨集也會取得的長度和 BLOB 資料行的狀態。

#### <a name="syntax"></a>語法

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*IID*<br/>
[in]介面的 GUID，例如`IDD_ISequentialStream`，用來擷取 BLOB。

*flags*<br/>
[in]儲存模式加上旗標所定義的 OLE 結構化儲存體模型 (例如`STGM_READ`)。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[out]BLOB 資料行 （實際） 長度，以位元組為單位。

*status*<br/>
[out]BLOB 欄位的狀態。

### <a name="blob_name_status"></a> BLOB_NAME_STATUS

BEGIN_COLUMN_MAP 與 END_COLUMN_MAP 用以繫結的二進位大型物件 ([BLOB](/previous-versions/windows/desktop/ms711511))。 類似於[BLOB_NAME](../../data/oledb/blob-name.md)，只不過這個巨集也會取得 BLOB 資料行的狀態。

#### <a name="syntax"></a>語法

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*IID*<br/>
[in]介面的 GUID，例如`IDD_ISequentialStream`，用來擷取 BLOB。

*flags*<br/>
[in]儲存模式加上旗標所定義的 OLE 結構化儲存體模型 (例如`STGM_READ`)。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*status*<br/>
[out]BLOB 欄位的狀態。

### <a name="bookmark_entry"></a> BOOKMARK_ENTRY

繫結的書籤資料行。

#### <a name="syntax"></a>語法

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>參數

*變數*<br/>
[in]要繫結至書籤資料行的變數。

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

#### <a name="see-also"></a>另請參閱

[CBookmark 類別](../../data/oledb/cbookmark-class.md)<br/>
[DBPROP_BOOKMARKS](/previous-versions/windows/desktop/ms709728)

### <a name="column_entry"></a> COLUMN_ENTRY

表示資料列集的特定資料行繫結的資料列集。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>參數

請參閱[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程式設計人員參考*。

*nOrdinal*<br/>
[in] 資料行編號。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

COLUMN_ENTRY 巨集可在下列位置：

- 之間[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)並[END_COLUMN_MAP](../../data/oledb/end-column-map.md)巨集。

- 之間[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)並[END_ACCESSOR](../../data/oledb/end-accessor.md)巨集。

- 之間[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)並[END_PARAM_MAP](../../data/oledb/end-param-map.md)巨集。

#### <a name="example"></a>範例

主題中的範例巨集，請參閱 < [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)並[BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)。

### <a name="column_entry_ex"></a> COLUMN_ENTRY_EX

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>參數

請參閱[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程式設計人員參考*。

*nOrdinal*<br/>
[in] 資料行編號。

*wType*<br/>
[in]資料類型。

*nLength*<br/>
[in]資料大小 （位元組）。

*nPrecision*<br/>
[in]取得資料時所要使用的最大有效位數並*wType*是`DBTYPE_NUMERIC`。 否則，會忽略這個參數。

*nScale*<br/>
[in]要取得資料時所使用的縮放比例及*wType*是`DBTYPE_NUMERIC`或`DBTYPE_DECIMAL`。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

COLUMN_ENTRY_EX 巨集可在下列位置：

- 之間[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)並[END_COLUMN_MAP](../../data/oledb/end-column-map.md)巨集。

- 之間[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)並[END_ACCESSOR](../../data/oledb/end-accessor.md)巨集。

- 之間[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)並[END_PARAM_MAP](../../data/oledb/end-param-map.md)巨集。

#### <a name="example"></a>範例

請參閱[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。

### <a name="column_entry_length"></a> COLUMN_ENTRY_LENGTH

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>參數

請參閱[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程式設計人員參考*。

*nOrdinal*<br/>
[in]資料行編號，從一開始。 書籤會對應至零的資料行。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

#### <a name="remarks"></a>備註

這個巨集支援*長度*變數。 這個參數可以用於下列狀況：

- 之間[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)並[END_COLUMN_MAP](../../data/oledb/end-column-map.md)巨集。

- 之間[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)並[END_ACCESSOR](../../data/oledb/end-accessor.md)巨集。

- 之間[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)並[END_PARAM_MAP](../../data/oledb/end-param-map.md)巨集。

### <a name="column_entry_length_status"></a> COLUMN_ENTRY_LENGTH_STATUS

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>參數

請參閱[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程式設計人員參考*。

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

- 之間[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)並[END_COLUMN_MAP](../../data/oledb/end-column-map.md)巨集。

- 之間[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)並[END_ACCESSOR](../../data/oledb/end-accessor.md)巨集。

- 之間[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)並[END_PARAM_MAP](../../data/oledb/end-param-map.md)巨集。

### <a name="column_entry_ps"></a> COLUMN_ENTRY_PS

表示資料列集的特定資料行繫結的資料列集。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>參數

請參閱[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程式設計人員參考*。

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

- 之間[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)並[END_COLUMN_MAP](../../data/oledb/end-column-map.md)巨集。

- 之間[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)並[END_ACCESSOR](../../data/oledb/end-accessor.md)巨集。

- 之間[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)並[END_PARAM_MAP](../../data/oledb/end-param-map.md)巨集。

### <a name="column_entry_ps_length"></a> COLUMN_ENTRY_PS_LENGTH

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>參數

請參閱[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程式設計人員參考*。

*nOrdinal*<br/>
[in]資料行編號，從一開始。 書籤會對應至零的資料行。

*nPrecision*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

#### <a name="remarks"></a>備註

可讓您指定要繫結之資料行的精確度和小數位數。 這個巨集支援*長度*變數。 這個參數可以用於下列狀況：

- 之間[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)並[END_COLUMN_MAP](../../data/oledb/end-column-map.md)巨集。

- 之間[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)並[END_ACCESSOR](../../data/oledb/end-accessor.md)巨集。

- 之間[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)並[END_PARAM_MAP](../../data/oledb/end-param-map.md)巨集。

### <a name="column_entry_ps_length_status"></a> COLUMN_ENTRY_PS_LENGTH_STATUS

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>參數

請參閱[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程式設計人員參考*。

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

- 之間[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)並[END_COLUMN_MAP](../../data/oledb/end-column-map.md)巨集。

- 之間[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)並[END_ACCESSOR](../../data/oledb/end-accessor.md)巨集。

- 之間[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)並[END_PARAM_MAP](../../data/oledb/end-param-map.md)巨集。

### <a name="column_entry_ps_status"></a> COLUMN_ENTRY_PS_STATUS

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>參數

請參閱[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程式設計人員參考*。

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

可讓您指定要繫結之資料行的精確度和小數位數。 這個巨集支援*狀態*變數。 這個參數可以用於下列狀況：

- 之間[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)並[END_COLUMN_MAP](../../data/oledb/end-column-map.md)巨集。

- 之間[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)並[END_ACCESSOR](../../data/oledb/end-accessor.md)巨集。

- 之間[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)並[END_PARAM_MAP](../../data/oledb/end-param-map.md)巨集。

### <a name="column_entry_status"></a> COLUMN_ENTRY_STATUS

表示從資料列集至資料庫的特定資料行的繫結。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>參數

請參閱[DBBINDING](/previous-versions/windows/desktop/ms716845)中*OLE DB 程式設計人員參考*。

*nOrdinal*<br/>
[in] 資料行編號。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

這個巨集支援*狀態*變數。 這個參數可以用於下列狀況：

- 之間[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)並[END_COLUMN_MAP](../../data/oledb/end-column-map.md)巨集。

- 之間[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)並[END_ACCESSOR](../../data/oledb/end-accessor.md)巨集。

- 之間[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)並[END_PARAM_MAP](../../data/oledb/end-param-map.md)巨集。

### <a name="column_entry_type"></a> COLUMN_ENTRY_TYPE

表示在資料庫中的特定資料行的繫結。 支援*型別*參數。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>參數

*nOrdinal*<br/>
[in] 資料行編號。

*wType*<br/>
[in]資料行項目資料型別。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

這個巨集是特製化的變化[COLUMN_ENTRY](../../data/oledb/column-entry.md)巨集，提供指定的資料類型的方法。

### <a name="column_entry_type_size"></a> COLUMN_ENTRY_TYPE_SIZE

表示在資料庫中的特定資料行的繫結。 支援*型別*並*大小*參數。

#### <a name="syntax"></a>語法

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>參數

*nOrdinal*<br/>
[in] 資料行編號。

*wType*<br/>
[in]資料行項目資料型別。

*nLength*<br/>
[in]資料行項目，以位元組為單位的大小。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

這個巨集是特製化的變化[COLUMN_ENTRY](../../data/oledb/column-entry.md)巨集，提供指定的資料大小和類型的方法。

### <a name="column_name"></a> COLUMN_NAME

表示資料列集的特定資料行繫結的資料列集。 類似於[COLUMN_ENTRY](../../data/oledb/column-entry.md)，只不過這個巨集接受資料行名稱，而不是資料行編號。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

COLUMN_NAME_ * 巨集可在相同的位置，作為[COLUMN_ENTRY](../../data/oledb/column-entry.md):

- 之間[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)並[END_COLUMN_MAP](../../data/oledb/end-column-map.md)巨集。

- 之間[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)並[END_ACCESSOR](../../data/oledb/end-accessor.md)巨集。

- 之間[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)並[END_PARAM_MAP](../../data/oledb/end-param-map.md)巨集。

### <a name="column_name_ex"></a> COLUMN_NAME_EX

表示資料列集的特定資料行繫結的資料列集。 類似於[COLUMN_NAME](../../data/oledb/column-name.md)，只不過這個巨集也會在資料類型、 大小、 有效位數、 小數位數、 資料行長度和資料行狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*wType*<br/>
[in]資料類型。

*nLength*<br/>
[in]資料大小 （位元組）。

*nPrecision*<br/>
[in]取得資料時所要使用的最大有效位數並*wType*是`DBTYPE_NUMERIC`。 否則，會忽略這個參數。

*nScale*<br/>
[in]要取得資料時所使用的縮放比例及*wType*是`DBTYPE_NUMERIC`或`DBTYPE_DECIMAL`。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

請參閱[COLUMN_NAME](../../data/oledb/column-name.md)如需有關使用 COLUMN_NAME_ * 巨集的位置資訊。

### <a name="column_name_length"></a> COLUMN_NAME_LENGTH

表示資料列集的特定資料行繫結的資料列集。 類似於[COLUMN_NAME](../../data/oledb/column-name.md)，只不過這個巨集也會採用資料行長度。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

#### <a name="remarks"></a>備註

請參閱[COLUMN_NAME](../../data/oledb/column-name.md)如需有關使用 COLUMN_NAME_ * 巨集的位置資訊。

### <a name="column_name_length_status"></a> COLUMN_NAME_LENGTH_STATUS

表示資料列集的特定資料行繫結的資料列集。 類似於[COLUMN_NAME](../../data/oledb/column-name.md)，只不過這個巨集也會採用資料行的長度和資料行狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

請參閱[COLUMN_NAME](../../data/oledb/column-name.md)如需有關使用 COLUMN_NAME_ * 巨集的位置資訊。

### <a name="column_name_ps"></a> COLUMN_NAME_PS

表示資料列集的特定資料行繫結的資料列集。 類似於[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在於有效位數和小數位數，也會採用此巨集。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*nPrecision*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

請參閱[COLUMN_NAME](../../data/oledb/column-name.md)如需有關使用 COLUMN_NAME_ * 巨集的位置資訊。

### <a name="column_name_ps_length"></a> COLUMN_NAME_PS_LENGTH

表示資料列集的特定資料行繫結的資料列集。 類似於[COLUMN_NAME](../../data/oledb/column-name.md)，只不過這個巨集也會使用有效位數、 小數位數和資料行的長度。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*nPrecision*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*length*<br/>
[in] 要繫結至資料行長度的變數。

#### <a name="remarks"></a>備註

請參閱[COLUMN_NAME](../../data/oledb/column-name.md)如需有關使用 COLUMN_NAME_ * 巨集的位置資訊。

### <a name="column_name_ps_length_status"></a> COLUMN_NAME_PS_LENGTH_STATUS

表示資料列集的特定資料行繫結的資料列集。 類似於[COLUMN_NAME](../../data/oledb/column-name.md)，不同之處在於有效位數、 小數位數、 資料行長度和資料行的狀態，也會採用此巨集。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

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

請參閱[COLUMN_NAME](../../data/oledb/column-name.md)如需有關使用 COLUMN_NAME_ * 巨集的位置資訊。

### <a name="column_name_ps_status"></a> COLUMN_NAME_PS_STATUS

表示資料列集的特定資料行繫結的資料列集。 類似於[COLUMN_NAME](../../data/oledb/column-name.md)，只不過這個巨集也會使用有效位數、 小數位數和資料行的狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*nPrecision*<br/>
[in] 要繫結之資料行的最大精確度。

*nScale*<br/>
[in] 要繫結之資料行的小數位數。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

請參閱[COLUMN_NAME](../../data/oledb/column-name.md)如需有關使用 COLUMN_NAME_ * 巨集的位置資訊。

### <a name="column_name_status"></a> COLUMN_NAME_STATUS

表示資料列集的特定資料行繫結的資料列集。 類似於[COLUMN_NAME](../../data/oledb/column-name.md)，只不過這個巨集也會採用資料行狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

#### <a name="remarks"></a>備註

請參閱[COLUMN_NAME](../../data/oledb/column-name.md)如需有關使用 COLUMN_NAME_ * 巨集的位置資訊。

### <a name="column_name_type"></a> COLUMN_NAME_TYPE

表示資料列集的特定資料行繫結的資料列集。 類似於[COLUMN_NAME](../../data/oledb/column-name.md)，只不過這個巨集也會採用資料型別。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*wType*<br/>
[in]資料類型。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

請參閱[COLUMN_NAME](../../data/oledb/column-name.md)如需有關使用 COLUMN_NAME_ * 巨集的位置資訊。

### <a name="column_name_type_ps"></a> COLUMN_NAME_TYPE_PS

表示資料列集的特定資料行繫結的資料列集。 類似於[COLUMN_NAME](../../data/oledb/column-name.md)，只不過這個巨集也會在資料類型、 有效位數和小數位數。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*wType*<br/>
[in]資料類型。

*nPrecision*<br/>
[in]取得資料時所要使用的最大有效位數並*wType*是`DBTYPE_NUMERIC`。 否則，會忽略這個參數。

*nScale*<br/>
[in]要取得資料時所使用的縮放比例及*wType*是`DBTYPE_NUMERIC`或`DBTYPE_DECIMAL`。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

請參閱[COLUMN_NAME](../../data/oledb/column-name.md)如需有關使用 COLUMN_NAME_ * 巨集的位置資訊。

### <a name="column_name_type_size"></a> COLUMN_NAME_TYPE_SIZE

表示資料列集的特定資料行繫結的資料列集。 類似於[COLUMN_NAME](../../data/oledb/column-name.md)，只不過這個巨集也會在資料類型和大小。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*wType*<br/>
[in]資料類型。

*nLength*<br/>
[in]資料大小 （位元組）。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

請參閱[COLUMN_NAME](../../data/oledb/column-name.md)如需有關使用 COLUMN_NAME_ * 巨集的位置資訊。

### <a name="column_name_type_status"></a> COLUMN_NAME_TYPE_STATUS

表示資料列集的特定資料行繫結的資料列集。 類似於[COLUMN_NAME](../../data/oledb/column-name.md)，只不過這個巨集也會在資料類型和資料行的狀態。

#### <a name="syntax"></a>語法

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>參數

*pszName*<br/>
[in]在資料行名稱的指標。 名稱必須是 Unicode 字串。 您可以這麼做，例如放在名稱中前, 'L': `L"MyColumn"`。

*wType*<br/>
[in]資料類型。

*status*<br/>
[in] 要繫結至資料行狀態的變數。

*data*<br/>
[in] 使用者記錄中相對應的資料成員。

#### <a name="remarks"></a>備註

請參閱[COLUMN_NAME](../../data/oledb/column-name.md)如需有關使用 COLUMN_NAME_ * 巨集的位置資訊。

### <a name="end_column_map"></a> END_COLUMN_MAP

結束標記的資料行的對應項目。

#### <a name="syntax"></a>語法

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>備註

它用於資料列集的單一存取子。 BEGIN_COLUMN_MAP 巨集完成 END_COLUMN_MAP 巨集。

#### <a name="example"></a>範例

請參閱[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)。

### <a name="define_command"></a> DEFINE_COMMAND

指定將用於建立資料列集時使用的命令[CCommand](../../data/oledb/ccommand-class.md)類別。 只接受字串類型符合指定的應用程式類型 （ANSI 或 Unicode）。

> [!NOTE]
>  建議您改用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是 DEFINE_COMMAND。

#### <a name="syntax"></a>語法

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>參數

*x*<br/>
[in]使用者資料錄 (command) 類別的名稱。

*szCommand*<br/>
[in]將用於建立資料列集時使用的命令字串[CCommand](../../data/oledb/ccommand-class.md)。

#### <a name="remarks"></a>備註

如果您未指定命令文字中的，將做為預設使用您指定的命令字串[ccommand:: Open](../../data/oledb/ccommand-open.md)方法。

這個巨集接受 ANSI 字串，如果您要建置為 ANSI，應用程式或 Unicode 字串，如果您要建置您的應用程式為 Unicode。 建議您改用[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)而不是 DEFINE_COMMAND，因為前者接受 Unicode 字串，不論 ANSI 或 Unicode 應用程式類型。

#### <a name="example"></a>範例

請參閱[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。

### <a name="define_command_ex"></a> DEFINE_COMMAND_EX

指定將用於建立資料列集時使用的命令[CCommand](../../data/oledb/ccommand-class.md)類別。 支援 Unicode 和 ANSI 應用程式。

#### <a name="syntax"></a>語法

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>參數

*x*<br/>
[in]使用者資料錄 (command) 類別的名稱。

*wszCommand*<br/>
[in]將用於建立資料列集時使用的命令字串[CCommand](../../data/oledb/ccommand-class.md)。

#### <a name="remarks"></a>備註

如果您未指定命令文字中的，將做為預設使用您指定的命令字串[ccommand:: Open](../../data/oledb/ccommand-open.md)方法。

這個巨集接受 Unicode 字串，不論應用程式類型。 這個巨集就合用[DEFINE_COMMAND](../../data/oledb/define-command.md)因為它支援 Unicode 和 ANSI 應用程式。

#### <a name="example"></a>範例

請參閱[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)。

### <a name="begin_param_map"></a> BEGIN_PARAM_MAP

標記參數對應項目的開頭。

#### <a name="syntax"></a>語法

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>參數

*x*<br/>
[in] 使用者資料錄類別的名稱。

#### <a name="remarks"></a>備註

使用的參數[命令](/previous-versions/windows/desktop/ms724608)。

#### <a name="example"></a>範例

範例，請參閱[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)巨集。

### <a name="end_param_map"></a> END_PARAM_MAP

標記參數對應項目的結尾。

#### <a name="syntax"></a>語法

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>範例

範例，請參閱[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)巨集。

### <a name="set_param_type"></a> SET_PARAM_TYPE

指定依照 SET_PARAM_TYPE 巨集輸入、 輸出或輸入/輸出的 COLUMN_ENTRY 巨集。

#### <a name="syntax"></a>語法

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>參數

*type*<br/>
[in] 用來設定參數的類型。

#### <a name="remarks"></a>備註

提供者只支援基礎資料來源支援的參數輸入/輸出類型。 類型是由一或多個組成`DBPARAMIO`值 (請參閱 < [DBBINDING 結構](/previous-versions/windows/desktop/ms716845)中*OLE DB 程式設計人員參考*):

- `DBPARAMIO_NOTPARAM` 存取子沒有任何參數。 一般而言，您將設定`eParamIO`中資料列存取子，以提醒使用者參數被忽略此值。

- `DBPARAMIO_INPUT` 輸入的參數。

- `DBPARAMIO_OUTPUT` 輸出參數。

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT` 此參數為輸入和輸出參數。

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

[OLE DB 消費者範本的巨集和全域函式](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)