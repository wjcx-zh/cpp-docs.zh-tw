---
title: 支援結構描述資料列集
ms.date: 11/04/2016
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
ms.openlocfilehash: 1ad1a91e8a79238eee773d92a756b0238e8901d5
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707494"
---
# <a name="supporting-schema-rowsets"></a>支援結構描述資料列集

結構描述資料列集可讓消費者取得資料存放區的相關資訊，而不需要知道其基礎結構或結構描述。 例如，資料存放區可能會將資料表組織成使用者定義的階層，因此除了讀取結構描述之外，沒辦法確保知道結構描述 (另一個範例，Visual C++ 精靈會使用結構描述資料列產生存取子以供消費者使用)。若要讓消費者這樣做，提供者的工作階段物件會在 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 介面上公開方法。 在 Visual C++ 應用程式中，您可以使用 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) 類別實作 `IDBSchemaRowset`。

`IDBSchemaRowsetImpl` 支援下列方法：

- [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md) 會針對結構描述資料列集檢查限制的有效性。

- [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md) 會為範本參數所指定的物件實作 COM 物件建立者函式。

- [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) 會指定您在特定結構描述資料列集上支援的限制。

- [IDBSchemaRowset::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) 會傳回 (繼承自介面的) 結構描述資料列集。

- [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) 會傳回一份可供 (繼承自介面的) `IDBSchemaRowsetImpl::GetRowset` 存取的結構描述資料列集清單。

## <a name="atl-ole-db-provider-wizard-support"></a>ATL OLE DB 提供者精靈支援

::: moniker range="vs-2019"

Visual Studio 2019 及更新版本中未提供 ATL OLE DB 提供者精靈。

::: moniker-end

::: moniker range="<=vs-2017"

**ATL OLE DB 提供者精靈**會在工作階段標頭檔中建立三個結構描述類別：

- **C**<em>ShortName</em>**SessionTRSchemaRowset**

- **C**<em>ShortName</em>**SessionColSchemaRowset**

- **C**<em>ShortName</em>**SessionPTSchemaRowset**

這些類別會回應結構描述資訊的消費者要求；請注意，OLE DB 規格要求支援這三個結構描述資料列集：

- **C**<em>ShortName</em>**SessionTRSchemaRowset** 會處理資料表資訊的要求 (DBSCHEMA_TABLES 結構描述資料列)。

- **C**<em>ShortName</em>**SessionColSchemaRowset** 會處理資料行資訊的要求 (DBSCHEMA_COLUMNS 結構描述資料列)。 此精靈會為這些類別提供範例實作，以傳回 DOS 提供者的結構描述資訊。

- **C**<em>ShortName</em>**SessionPTSchemaRowset** 會處理提供者類型相關結構描述資訊的要求 (DBSCHEMA_PROVIDER_TYPES 結構描述資料列)。 此精靈所提供的預設實作會傳回 S_OK。

您可以自訂這些類別來處理適用於您提供者的結構描述資訊：

- 在 **C**<em>ShortName</em>**SessionTRSchemaRowset** 中，您必須填寫目錄、資料表和描述欄位 (`trData.m_szType`、`trData.m_szTable` 以及 `trData.m_szDesc`)。 精靈產生的範例僅會使用一個資料列 (資料表)。 其他提供者可能會傳回多個資料表。

- 在 **C**<em>ShortName</em>**SessionColSchemaRowset** 中，您會傳遞資料表名稱作為 `DBID`。

::: moniker-end

## <a name="setting-restrictions"></a>設定限制

結構描述資料列集支援中的重要概念是設定限制，您可以使用 `SetRestrictions` 完成。 限制允許消費者只擷取相符的資料列 (例如在資料表 "MyTable" 中尋找所有資料行)。 限制是選擇性的，在不支援任何限制的情況下 (預設)，一律會傳回所有資料。 如需支援限制之提供者的範例，請參閱 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 範例。

## <a name="setting-up-the-schema-map"></a>設定結構描述對應

在 UpdatePV 的 Session.h 中設定這類結構描述對應：

```cpp
BEGIN_SCHEMA_MAP(CUpdateSession)
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)
END_SCHEMA_MAP()
```

若要支援 `IDBSchemaRowset`，您必須支援 DBSCHEMA_TABLES、DBSCHEMA_COLUMNS 和 DBSCHEMA_PROVIDER_TYPES。 您可以自行新增額外的結構描述資料列集。

在 `UpdatePV` 中使用 `Execute` 方法宣告結構描述資料列集類別，例如 `CUpdateSessionTRSchemaRowset`：

```cpp
class CUpdateSessionTRSchemaRowset :
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,
                              CTABLESRow, CUpdateSession >
...
// Execute looks like this; what pointers does the consumer use?
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,
                    ULONG cRestrictions, const VARIANT* rgRestrictions)
```

`CUpdateSession` 繼承自 `IDBSchemaRowsetImpl`，因此它擁有處理方法的所有限制。 使用 `CSchemaRowsetImpl` 宣告三個子類別 (列在上述的結構描述對應中)：`CUpdateSessionTRSchemaRowset`、`CUpdateSessionColSchemaRowset` 和 `CUpdateSessionPTSchemaRowset`。 這些子類別中的每一個都有一個 `Execute`，可處理其個別一組限制 (搜尋條件)。 每個 `Execute` 方法都會比較 *cRestrictions* 和 *rgRestrictions* 參數的值。 請參閱 [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) 中這些參數的描述。

如需對應至特定結構描述資料列集之限制的詳細資訊，請參閱 Windows SDK 之 **OLE DB 程式設計人員參考**中的 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))。

例如，如果您支援 DBSCHEMA_TABLES 中的 TABLE_NAME 限制，您會執行下列項目：

首先，查閱 DBSCHEMA_TABLES，並查看它是否支援四個限制 (依順序)。

|結構描述資料列集限制|限制值|
|-------------------------------|-----------------------|
|TABLE_CATALOG|0x1 (二進位 1)|
|TABLE_SCHEMA|0x2 (二進位 10)|
|TABLE_NAME|0x4 (二進位 100)|
|TABLE_TYPE|0x8 (二進位 1000)|

接著，每個限制都有一個位元。 因為您只想要支援 TABLE_NAME，因此將會在 `rgRestrictions` 元素中傳回 0x4。 如果您支援 TABLE_CATALOG 和 TABLE_NAME，則會傳回 0x5 (二進位 101)。

根據預設，任何要求的實作都會傳回 0 (不支援任何限制)。 UpdatePV 是支援限制之提供者的範例。

### <a name="example"></a>範例

此程式碼取自 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 範例。 `UpdatePv` 支援三個必要的結構描述資料列集：DBSCHEMA_TABLES、DBSCHEMA_COLUMNS 和 DBSCHEMA_PROVIDER_TYPES。 作為如何在提供者中實作結構描述支援的範例，本主題將引導您實作 DBSCHEMA_TABLE 資料列集。

> [!NOTE]
> 範例程式碼可能會與此處所列的不同；您應該將範例程式碼視為更新版本。

新增結構描述支援的第一個步驟是決定您要支援的限制。 若要判斷哪些限制可供您的結構描述資料列使用，請查看 OLE DB 規格中的 `IDBSchemaRowset` 定義。 在主要定義之後，您會看到保存結構描述資料列集名稱、限制數目，以及限制資料行的資料表。 選取您想要支援的結構描述資料列集，並記下限制和限制資料行的數目。 例如，DBSCHEMA_TABLES 支援四個限制 (TABLE_CATALOG、TABLE_SCHEMA、TABLE_NAME 和 TABLE_TYPE)：

```cpp
void SetRestrictions(ULONG cRestrictions, GUID* rguidSchema,
   ULONG* rgRestrictions)
{
    for (ULONG l=0; l<cRestrictions; l++)
    {
        if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
            rgRestrictions[l] = 0x0C;
        else if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_COLUMNS))
                 rgRestrictions[l] = 0x04;
             else if (InlineIsEqualGUID(rguidSchema[l],
                                        DBSCHEMA_PROVIDER_TYPES))
                      rgRestrictions[l] = 0x00;
   }
}
```

一個位元代表每個限制資料行。 如果您想要支援限制 (也就是您可以透過它查詢)，請將該位元設為 1。 如果您不想要支援限制，請將該位元設定為零。 從上面一行程式碼，`UpdatePV` 在 DBSCHEMA_TABLES 資料列集上支援 TABLE_NAME 和 TABLE_TYPE 限制。 這些是第三個 (位元遮罩 100) 第四個 (位元遮罩 1000) 限制。 因此，`UpdatePv` 的位元遮罩為 1100 (或 0x0C)：

```cpp
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
    rgRestrictions[l] = 0x0C;
```

下列 `Execute` 函式類似於一般的資料列集。 您有三個引數：*pcRowsAffected*、*cRestrictions* 和 *rgRestrictions*。 *pcRowsAffected* 變數是一個輸出參數，可讓提供者在結構描述資料列中傳回資料列計數。 *cRestrictions* 參數是一個輸入參數，可保存消費者傳遞給提供者的限制數目。 *rgRestrictions* 參數是 VARIANT 值的一個陣列，可保存限制值。

```cpp
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,
                const VARIANT* rgRestrictions)
```

*cRestrictions* 變數是以結構描述資料列集的限制總數為基礎，而不管提供者是否支援這些限制。 UpdatePv 支援兩個限制 (第三個和第四個)，因此這個程式碼只會尋找大於或等於 3 的 *cRestrictions* 值。

TABLE_NAME 限制的值會儲存在 *rgRestrictions [2]* 中 (再次提醒，在以零為基礎的陣列中，第三個限制為 2)。 請檢查此限制不是 VT_EMPTY 以實際上支援它。 請注意，VT_NULL 不等於 VT_EMPTY。 VT_NULL 會指定有效的限制值。

資料表名稱的 `UpdatePv` 定義是文字檔的完整路徑名稱。 擷取限制值，然後嘗試開啟檔案，以確保檔案確實存在。 如果檔案不存在，則會傳回 S_OK。 這看起來似乎有點倒退，但此程式碼實際上是通知消費者指定的名稱沒有支援的資料表。 傳回 S_OK 表示程式碼正確執行。

```cpp
USES_CONVERSION;
enum {
            sizeOfszFile = 255
};
CTABLESRow  trData;
FILE        *pFile = NULL;
TCHAR       szFile[ sizeOfszFile ];
errcode     err = 0;

// Handle any restrictions sent to us. This only handles
// the TABLE_NAME & TABLE_TYPE restictions (the 3rd and 4th
// restrictions in DBSCHEMA_TABLES...look in IDBSchemaRowsets
// in part 2 of the prog. ref) so your restrictions are 0x08 & 0x04
// for a total of (0x0C)
if (cRestrictions >= 3 && rgRestrictions[2].vt != VT_EMPTY)
{
    CComBSTR bstrName = rgRestrictions[2].bstrVal;
    if ((rgRestrictions[2].vt == VT_BSTR) && (bstrName != (BSTR)NULL))
    {
        // Check to see if the file exists
        _tcscpy_s(&szFile[0], sizeOfszFile, OLE2T(bstrName));
        if (szFile[0] == _T('\0') ||
           ((err = _tfopen(&pFile, &szFile[0], _T("r"))) == 0))
        {
            return S_OK;// Their restriction was invalid return no data
        }
        else
        {
            fclose(pFile);
        }
    }
}
```

支援第四個限制 (TABLE_TYPE) 類似於第三個限制。 請檢查此值不是 VT_EMPTY。 此限制只會傳回資料表類型 TABLE。 若要判斷 DBSCHEMA_TABLES 的有效值，請查閱 **OLE DB 程式設計人員參考** **附錄 B** 中的 TABLES 資料列集一節。

```cpp
// TABLE_TYPE restriction:
if (cRestrictions >=4 && rgRestrictions[3].vt != VT_EMPTY)
{
    CComBSTR bstrType = rgRestrictions[3].bstrVal;
    if ((rgRestrictions[3].vt == VT_BSTR) && (bstrType != (BSTR)NULL))
    {
        // This is kind of a blind restriction.
        // This only actually supports
        // TABLES so if you get anything else,
        // just return an empty rowset.
        if (_tcscmp(_T("TABLE"), OLE2T(bstrType)) != 0)
            return S_OK;
    }
}
```

這是實際為資料列集建立資料列項目所在。 變數 `trData` 會對應至 `CTABLESRow`，這是在 OLE DB 提供者範本中定義的結構。 `CTABLESRow` 會對應至 OLE DB 規格**附錄 B** 中的 TABLES 資料列集定義。 您只需要加入一個資料列，因為您一次只能支援一個資料表。

```cpp
// Bring over the data:
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());
```

`UpdatePV` 僅會設定三個資料行：TABLE_NAME、TABLE_TYPE 和 DESCRIPTION。 請記下您傳回資訊的資料行，因為您在實作 `GetDBStatus` 時，會需要此資訊：

```cpp
    _ATLTRY
    {
        m_rgRowData.Add(trData);
    }
    _ATLCATCHALL()
    {
        return E_OUTOFMEMORY;
    }
    //if (!m_rgRowData.Add(trData))
    //    return E_OUTOFMEMORY;
    *pcRowsAffected = 1;
    return S_OK;
}
```

`GetDBStatus` 函式對於結構描述資料列集的正確操作非常重要。 您在 TABLES 資料列集中不會傳回每個資料行的資料，因此您必須指定您傳回哪些資料行的資料，以及您未傳回哪些資料行的資料。

```cpp
virtual DBSTATUS GetDBStatus(CSimpleRow* , ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pColInfo != NULL);

    switch(pColInfo->iOrdinal)
    {
    case 3:     // TABLE_NAME
    case 4:     // TABLE_TYPE
    case 6:     // DESCRIPTION
        return DBSTATUS_S_OK;
        break;
    default:
        return DBSTATUS_S_ISNULL;
    break;
    }
}
```

您的 `Execute` 函式會從 TABLES 資料列集傳回 TABLE_NAME、TABLE_TYPE 和 DESCRIPTION 欄位的資料，因此您可以查閱 OLE DB 規格的**附錄 B**，並判斷 (透過從上到下計算) 它們是否為 3、 4 和 6 的序數。 對於這些每個資料行，傳回 DBSTATUS_S_OK。 對於其他所有資料行，則傳回 DBSTATUS_S_ISNULL。 請務必傳回此狀態，因為消費者可能不了解您傳回的值是 NULL 還是其他值。 再次提請，請注意，NULL 不相當於空白。

如需有關 OLE DB 結構描述資料列集介面的詳細資訊，請參閱 **OLE DB 程式設計人員參考**中的 [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) 介面。

如需有關消費者如何使用 `IDBSchemaRowset` 方法的資訊，請參閱[使用結構描述資料列集取得中繼資料](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)。

如需支援結構描述資料列集之提供者的範例，請參閱 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 範例。

## <a name="see-also"></a>另請參閱

[進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)
