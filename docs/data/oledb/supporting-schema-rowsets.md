---
title: 支援結構描述資料列集
ms.date: 11/04/2016
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
ms.openlocfilehash: b49d53836179d765a72409d28304d7166dcf51d8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024617"
---
# <a name="supporting-schema-rowsets"></a>支援結構描述資料列集

結構描述資料列集可讓取用者取得的資料存放區的相關資訊，而不需要知道其基礎結構描述。 例如，資料存放區可能不有組織成使用者定義階層，所以會有任何方式可以確保在閱讀本文的知道除了結構描述的資料表。 （另舉一例，Visual c + + 精靈使用結構描述資料列集來產生取用者的存取子）。若要讓取用者若要這樣做，提供者的工作階段物件會公開方法上[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))介面。 在 Visual c + + 應用程式，您可以使用[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)類別來實作`IDBSchemaRowset`。

`IDBSchemaRowsetImpl` 支援下列方法：

- [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md)檢查限制針對結構描述資料列集的有效性。

- [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)實作 COM 物件建立者函式的範本參數所指定的物件。

- [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)指定您在特定結構描述資料列集支援的限制。

- [Idbschemarowset:: Getrowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)傳回 （繼承自介面） 的結構描述資料列集。

- [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)會傳回一份結構描述資料列集可供存取`IDBSchemaRowsetImpl::GetRowset`（繼承自介面）。

## <a name="atl-ole-db-provider-wizard-support"></a>ATL OLE DB 提供者精靈支援

**ATL OLE DB 提供者精靈**工作階段標頭檔中建立三個結構描述類別：

- **C**<em>ShortName</em>**SessionTRSchemaRowset**

- **C**<em>ShortName</em>**SessionColSchemaRowset**

- **C**<em>ShortName</em>**SessionPTSchemaRowset**

這些類別結構描述資訊; 的取用者要求回應請注意，OLE DB 規格需要這些三個結構描述資料列集必須支援：

- **C**<em>ShortName</em>**SessionTRSchemaRowset**會處理資料表資訊 （DBSCHEMA_TABLES 結構描述資料列） 的要求。

- **C**<em>ShortName</em>**SessionColSchemaRowset**處理要求的資料行資訊 （DBSCHEMA_COLUMNS 結構描述資料列）。 精靈會提供這些類別，傳回 DOS 提供者的結構描述資訊的範例實作。

- **C**<em>ShortName</em>**SessionPTSchemaRowset**會處理提供者類型 （DBSCHEMA_PROVIDER_TYPES 結構描述資料列） 的結構描述資訊的要求。 精靈所提供的預設實作會傳回 S_OK。

您可以自訂這些類別來處理結構描述資訊適用於您的提供者：

- 在  **C**<em>簡短名稱</em>**SessionTRSchemaRowset**，您必須填寫的目錄、 資料表名稱和描述欄位 (`trData.m_szType`， `trData.m_szTable`，以及`trData.m_szDesc`). 在精靈產生的範例會使用只有一個資料列 （資料表）。 其他提供者可能會傳回一個以上的資料表。

- 在  **C**<em>ShortName</em>**SessionColSchemaRowset**，做為資料表名稱傳遞給`DBID`。

## <a name="setting-restrictions"></a>設定限制

結構描述資料列集支援中的重要概念設定限制，您使用執行`SetRestrictions`。 限制允許消費者只擷取相符的資料列 (例如在資料表 "MyTable" 中尋找所有資料行)。 限制是選擇性的，在不支援任何限制的情況下 (預設)，一律會傳回所有資料。 如需支援限制的提供者的範例，請參閱 < [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)範例。

## <a name="setting-up-the-schema-map"></a>設定結構描述對應

設定在 UpdatePV Session.h 這類結構描述對應：

```cpp
BEGIN_SCHEMA_MAP(CUpdateSession)
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)
END_SCHEMA_MAP()
```

若要支援`IDBSchemaRowset`，您必須支援 DBSCHEMA_TABLES、 DBSCHEMA_COLUMNS 和 DBSCHEMA_PROVIDER_TYPES。 您可以自行新增額外的結構描述資料列集。

宣告具有的結構描述資料列集類別`Execute`方法，例如`CUpdateSessionTRSchemaRowset`在`UpdatePV`:

```cpp
class CUpdateSessionTRSchemaRowset :
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,
                              CTABLESRow, CUpdateSession >
...
// Execute looks like this; what pointers does the consumer use?
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,
                    ULONG cRestrictions, const VARIANT* rgRestrictions)
```

`CUpdateSession` 繼承自`IDBSchemaRowsetImpl`，所以它沒有處理常式方法的所有限制。 使用`CSchemaRowsetImpl`，宣告三個 （列於上述的結構描述對應） 的子類別： `CUpdateSessionTRSchemaRowset`， `CUpdateSessionColSchemaRowset`，和`CUpdateSessionPTSchemaRowset`。 這些子類別的每個都有`Execute`處理個別組的限制 （搜尋條件） 的方法。 每個`Execute`方法會比較的值*cRestrictions*並*rgRestrictions*參數。 請參閱中的這些參數的說明[SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)。

如需哪些限制對應至特定結構描述資料列集的詳細資訊，請參閱結構描述資料列集 Guid 的資料表中[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))中**OLE DB 程式設計人員參考**Windows SDK 中.

例如，如果您支援 DBSCHEMA_TABLES TABLE_NAME 限制，您會執行下列項目：

首先，查閱 DBSCHEMA_TABLES，並查看它支援四個的限制 （依順序）。

|結構描述資料列集限制|限制值|
|-------------------------------|-----------------------|
|TABLE_CATALOG|0x1 (二進位 1)|
|TABLE_SCHEMA|0x2 (二進位 10)|
|TABLE_NAME|0x4 (二進位 100)|
|TABLE_TYPE|0x8 (二進位 1000)|

下一步，是一個位元的每個限制。 因為您想要只支援 TABLE_NAME，您將會傳回在 0x4`rgRestrictions`項目。 如果您支援 table_catalog 排列，TABLE_NAME，則會傳回 0x5 (二進位 101)。

根據預設，實作會傳回的 0 （不支援任何限制） 的任何要求。 UpdatePV 是提供者支援限制的範例。

### <a name="example"></a>範例

此程式碼取自[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)範例。 `UpdatePv` 支援的三個必要的結構描述資料列集：DBSCHEMA_TABLES、 DBSCHEMA_COLUMNS 和 DBSCHEMA_PROVIDER_TYPES。 如何在您的提供者中實作結構描述支援的範例，本主題引導您實作 DBSCHEMA_TABLE 資料列集。

> [!NOTE]
> 範例程式碼可能會與不同功能為此處所列;您應該將範例程式碼做為較新版本。

新增結構描述支援的第一個步驟是決定您要支援的限制。 若要判斷哪些限制可供您的結構描述資料列，查看 OLE DB 規格定義的`IDBSchemaRowset`。 下列主要定義，您會看到持有結構描述資料列集名稱、 數目限制，以及限制資料行的資料表。 選取您想要支援，並記下的限制和限制資料行數目的結構描述資料列集。 比方說，DBSCHEMA_TABLES 支援四個的限制 （table_catalog 排列、 TABLE_SCHEMA、 TABLE_NAME 和 TABLE_TYPE）：

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

位元代表每個限制資料行。 如果您想要支援的限制 （也就是您可以查詢它），該位元設為 1。 如果您不想要支援的限制，請該位元設定為零。 從上面的程式碼行`UpdatePV`DBSCHEMA_TABLES 資料列集上支援 TABLE_NAME 和 TABLE_TYPE 限制。 這些是 （位元遮罩 100） 的第三和第四個 （位元遮罩 1000年） 限制。 因此，位元遮罩`UpdatePv`1100年 （或 0x0C）：

```cpp
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))
    rgRestrictions[l] = 0x0C;
```

下列`Execute`函式是類似於一般的資料列集。 您有三個引數： *pcRowsAffected*， *cRestrictions*，並*rgRestrictions*。 *PcRowsAffected*變數是一個 output 參數，提供者，可以在結構描述資料列中傳回的資料列計數。 *CRestrictions*參數是保存的提供者取用者所傳送的限制數目的輸入的參數。 *RgRestrictions*參數是保存的限制值的變數值的陣列。

```cpp
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,
                const VARIANT* rgRestrictions)
```

*CRestrictions*變數為基礎的結構描述資料列集，不論提供者是否支援這些限制的總數。 由於 UpdatePv 支援兩個的限制 （第三和第四個），此程式碼只會尋找*cRestrictions*值大於或等於 3。

TABLE_NAME 限制值會儲存在*rgRestrictions [2]* （同樣地，以零為起始的陣列中的第三個限制為 2）。 請檢查這項限制不 VT_EMPTY 實際上支援它。 請注意，VT_NULL 不等於設為 VT_EMPTY。 VT_NULL 指定有效的限制值。

`UpdatePv`資料表名稱的定義是文字檔案的完整的路徑名稱。 擷取限制值，然後再次嘗試開啟檔案，以確保檔案確實存在。 如果檔案不存在，會傳回 S_OK。 這看起來似乎有點回溯，但其實程式碼的確會通知取用者會依指定名稱所不支援的資料表。 傳回 S_OK 表示正確執行的程式碼。

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

支援的第四個的限制 (TABLE_TYPE) 是類似於第三個的限制。 請檢查此值不是為 VT_EMPTY。 這項限制只會傳回資料表的資料表類型。 若要判斷 DBSCHEMA_TABLES 有效的值，查看**附錄 B**的**OLE DB 程式設計人員參考**資料表資料列集一節。

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

這是實際建立的資料列集的資料列項目。 變數`trData`對應至`CTABLESRow`，OLE DB 提供者範本中定義的結構。 `CTABLESRow` 對應中的資料表資料列集定義**附錄 B**的 OLE DB 規格。 您只需要一個資料列加入，因為您一次只能支援一個資料表。

```cpp
// Bring over the data:
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());
```

`UpdatePV` 設定只有三個資料行：TABLE_NAME、 TABLE_TYPE 和描述。 請記下的傳回之資訊，資料行，因為當您實作時，您會需要這項資訊`GetDBStatus`:

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

`GetDBStatus`函式，請務必使用正確的結構描述資料列集的作業。 因為您不在資料表資料列集傳回每個資料行的資料，您必須指定哪些資料行，傳回的資料，並不這麼做。

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

因為您`Execute`從資料表資料列集函式會傳回的 TABLE_NAME、 TABLE_TYPE 和描述欄位的資料，您可以查看**附錄 B**的 OLE DB 規格，並判斷 （透過，從上方算起）它們會是 3、 4 和 6 的序數。 對於每個資料行，會傳回 DBSTATUS_S_OK。 對於所有其他資料行，會傳回 DBSTATUS_S_ISNULL。 務必以傳回此狀態，因為取用者可能不了解您傳回的值是 NULL 或其他項目。 同樣地，請注意，NULL 不是相當於空白。

如需有關 OLE DB 結構描述資料列集介面的詳細資訊，請參閱[IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md)介面中**OLE DB 程式設計人員參考**。

如需如何使用取用者`IDBSchemaRowset`方法，請參閱[取得中繼資料與結構描述資料列集](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)。

如需支援結構描述資料列集提供者的範例，請參閱 < [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)範例。

## <a name="see-also"></a>另請參閱

[進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)
