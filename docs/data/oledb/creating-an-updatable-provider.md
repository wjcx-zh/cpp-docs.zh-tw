---
title: 建立可更新的提供者
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 2811cd56bdc87282b9d4395a9a79ba9b333dadee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211389"
---
# <a name="creating-an-updatable-provider"></a>建立可更新的提供者

Visual C++支援可更新（寫入）資料存放區的可更新提供者或提供者。 本主題討論如何使用 OLE DB 範本來建立可更新的提供者。

本主題假設您是從可行的提供者開始。 建立可更新的提供者有兩個步驟。 您必須先決定提供者將如何對資料存放區進行變更;具體而言，是要立即或延後變更，直到發出 update 命令為止。 「[使提供者可更新](#vchowmakingprovidersupdatable)的方式」一節說明您必須在提供者程式碼中執行的變更和設定。

接下來，您必須確定您的提供者包含所有功能，以支援取用者可能要求的任何專案。 如果取用者想要更新資料存放區，則提供者必須包含將資料保存至資料存放區的程式碼。 例如，您可以使用 C 執行時間程式庫或 MFC，在您的資料來源上執行這類作業。 「[寫入資料來源](#vchowwritingtothedatasource)」一節描述如何寫入資料來源、處理 Null 和預設值，以及設定資料行旗標。

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)是可更新的提供者的範例。 UpdatePV 與 MyProv 相同，但具有可更新的支援。

##  <a name="making-providers-updatable"></a><a name="vchowmakingprovidersupdatable"></a>讓提供者可更新

讓提供者可更新的關鍵在於瞭解您想要提供者在資料存放區上執行的作業，以及您希望提供者如何完成這些作業。 具體而言，主要的問題是資料存放區的更新會立即完成或延後（批次），直到發出 update 命令為止。

您必須先決定是否要從資料列集類別中的 `IRowsetChangeImpl` 或 `IRowsetUpdateImpl` 繼承。 根據您選擇要執行的功能而定，三種方法的功能會受到影響： `SetData`、`InsertRows`和 `DeleteRows`。

- 如果您繼承自[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)，則呼叫這三個方法會立即變更資料存放區。

- 如果您繼承自[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)，方法會將變更延遲到資料存放區，直到您呼叫 `Update`、`GetOriginalData`或 `Undo`為止。 如果更新牽涉到數個變更，則會在批次模式中執行（請注意，批次處理變更可能會增加相當大的記憶體額外負荷）。

請注意，`IRowsetUpdateImpl` 衍生自 `IRowsetChangeImpl`。 因此，`IRowsetUpdateImpl` 會提供變更功能加上批次功能。

### <a name="to-support-updatability-in-your-provider"></a>支援您提供者中的可更新性

1. 在您的資料列集類別中，繼承自 `IRowsetChangeImpl` 或 `IRowsetUpdateImpl`。 這些類別會提供適當的介面來變更資料存放區：

   **加入 IRowsetChange**

   使用下列格式，將 `IRowsetChangeImpl` 新增至您的繼承鏈：

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   此外，請將 `COM_INTERFACE_ENTRY(IRowsetChange)` 加入至資料列集類別中的 `BEGIN_COM_MAP` 區段。

   **加入 IRowsetUpdate**

   使用下列格式，將 `IRowsetUpdate` 新增至您的繼承鏈：

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > 您應該從繼承鏈中移除 `IRowsetChangeImpl` 行。 前述指示詞的這個例外狀況必須包含 `IRowsetChangeImpl`的程式碼。

1. 將下列內容新增至您的 COM 對應（`BEGIN_COM_MAP ... END_COM_MAP`）：

   |  如果您執行   |           新增至 COM 對應             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | 如果您執行 | 加入至屬性集對應 |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. 在您的命令中，將下列內容新增至您的屬性集對應（`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`）：

   |  如果您執行   |                                             加入至屬性集對應                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. 在您的屬性集對應中，您也應該包含下列所有設定，如下所示：

    ```cpp
    PROPERTY_INFO_ENTRY_VALUE(UPDATABILITY, DBPROPVAL_UP_CHANGE |
      DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)
    PROPERTY_INFO_ENTRY_VALUE(CHANGEINSERTEDROWS, VARIANT_TRUE)
    PROPERTY_INFO_ENTRY_VALUE(IMMOBILEROWS, VARIANT_TRUE)

    PROPERTY_INFO_ENTRY_EX(OWNINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OWNUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OTHERINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OTHERUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(REMOVEDELETED, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_FALSE, 0)
    ```

   您可以藉由查看為 atldb.h 中的屬性識別碼和值，尋找這些宏呼叫中使用的值（如果為 atldb.h 與線上檔不同，為 atldb.h 會取代檔）。

   > [!NOTE]
   > OLE DB 範本需要許多 `VARIANT_FALSE` 和 `VARIANT_TRUE` 設定;OLE DB 規格指出它們可以是可讀寫的，但 OLE DB 的範本只能支援一個值。

   **如果您執行 IRowsetChangeImpl**

   如果您執行 `IRowsetChangeImpl`，您必須在提供者上設定下列屬性。 這些屬性主要是用來透過 `ICommandProperties::SetProperties`來要求介面。

   - `DBPROP_IRowsetChange`：設定這會自動設定 `DBPROP_IRowsetChange`。

   - `DBPROP_UPDATABILITY`：位元遮罩，指定 `IRowsetChange`上支援的方法： `SetData`、`DeleteRows`或 `InsertRow`。

   - `DBPROP_CHANGEINSERTEDROWS`：取用者可以針對新插入的資料列呼叫 `IRowsetChange::DeleteRows` 或 `SetData`。

   - `DBPROP_IMMOBILEROWS`：資料列集不會重新排序已插入或已更新的資料列。

   **如果您執行 IRowsetUpdateImpl**

   如果您執行 `IRowsetUpdateImpl`，除了設定先前列出的 `IRowsetChangeImpl` 的所有屬性之外，您還必須在提供者上設定下列屬性：

   - `DBPROP_IRowsetUpdate`第 1 課：建立 Windows Azure 儲存體物件{2}。

   - `DBPROP_OWNINSERT`：必須 READ_ONLY 並 VARIANT_TRUE。

   - `DBPROP_OWNUPDATEDELETE`：必須 READ_ONLY 並 VARIANT_TRUE。

   - `DBPROP_OTHERINSERT`：必須 READ_ONLY 並 VARIANT_TRUE。

   - `DBPROP_OTHERUPDATEDELETE`：必須 READ_ONLY 並 VARIANT_TRUE。

   - `DBPROP_REMOVEDELETED`：必須 READ_ONLY 並 VARIANT_TRUE。

   - `DBPROP_MAXPENDINGROWS`第 1 課：建立 Windows Azure 儲存體物件{2}。

   > [!NOTE]
   > 如果您支援通知，可能也會有一些其他屬性;請參閱這份清單 `IRowsetNotifyCP` 的一節。

##  <a name="writing-to-the-data-source"></a><a name="vchowwritingtothedatasource"></a>寫入資料來源

若要從資料來源讀取，請呼叫 `Execute` 函數。 若要寫入至資料來源，請呼叫 `FlushData` 函數。 （一般來說，flush 表示將對資料表或索引所做的修改儲存到磁片上。）

```cpp
FlushData(HROW, HACCESSOR);
```

資料列控制碼（HROW）和存取子控制碼（HACCESSOR）引數可讓您指定要寫入的區域。 一般來說，您一次只會撰寫一個資料欄位。

`FlushData` 方法會以原先儲存的格式來寫入資料。 如果您未覆寫此函式，您的提供者將能正常運作，但變更不會排清到資料存放區。

### <a name="when-to-flush"></a>何時排清

每當資料需要寫入資料存放區時，提供者範本會呼叫 FlushData;這通常（但不一定）會因呼叫下列函式而發生：

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows` （如果有要插入資料列的新資料）

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>運作方式

取用者會進行需要排清的呼叫（例如 Update），而此呼叫會傳遞給提供者，其一律會執行下列動作：

- 每當有狀態值系結時，就會呼叫 `SetDBStatus`。

- 檢查資料行旗標。

- 呼叫 `IsUpdateAllowed`。

這三個步驟可協助提供安全性。 然後，提供者會呼叫 `FlushData`。

### <a name="how-to-implement-flushdata"></a>如何執行 FlushData

若要執行 `FlushData`，您必須考慮幾個問題：

確定資料存放區可以處理變更。

處理 Null 值。

### <a name="handling-default-values"></a>處理預設值。

若要執行您自己的 `FlushData` 方法，您需要：

- 移至您的資料列集類別。

- 在資料列集類別中，放置的宣告：

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- 提供 `FlushData`的執行。

良好的 `FlushData` 的執行，只會儲存實際更新的資料列和資料行。 您可以使用 HROW 和 HACCESSOR 參數來判斷目前要儲存的資料列和資料行，以進行優化。

一般來說，最大的挑戰是使用您自己的原生資料存放區。 可能的話，請嘗試：

- 儘量簡化寫入資料存放區的方法。

- 處理 Null 值（選擇性但建議）。

- 處理預設值（選擇性但建議）。

最佳做法是在您的資料存放區中擁有實際的指定值，以取得 Null 和預設值。 如果您可以推斷這種資料，最好這麼做。 如果沒有，建議您不要允許 Null 和預設值。

下列範例顯示如何在 `UpdatePV` 範例的 `RUpdateRowset` 類別中實作為 `FlushData` （請參閱範例程式碼中的 Rowset. h）：

```cpp
///////////////////////////////////////////////////////////////////////////
// class RUpdateRowset (in rowset.h)
...
HRESULT FlushData(HROW, HACCESSOR)
{
    ATLTRACE2(atlTraceDBProvider, 0, "RUpdateRowset::FlushData\n");

    USES_CONVERSION;
    enum {
        sizeOfString = 256,
        sizeOfFileName = MAX_PATH
    };
    FILE*    pFile = NULL;
    TCHAR    szString[sizeOfString];
    TCHAR    szFile[sizeOfFileName];
    errcode  err = 0;

    ObjectLock lock(this);

    // From a filename, passed in as a command text,
    // scan the file placing data in the data array.
    if (m_strCommandText == (BSTR)NULL)
    {
        ATLTRACE( "RRowsetUpdate::FlushData -- "
                  "No filename specified\n");
        return E_FAIL;
    }

    // Open the file
    _tcscpy_s(szFile, sizeOfFileName, OLE2T(m_strCommandText));
    if ((szFile[0] == _T('\0')) ||
        ((err = _tfopen_s(&pFile, &szFile[0], _T("w"))) != 0))
    {
        ATLTRACE("RUpdateRowset::FlushData -- Could not open file\n");
        return DB_E_NOTABLE;
    }

    // Iterate through the row data and store it.
    for (long l=0; l<m_rgRowData.GetSize(); l++)
    {
        CAgentMan am = m_rgRowData[l];

        _putw((int)am.dwFixed, pFile);

        if (_tcscmp(&am.szCommand[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szText[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szText);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szCommand2[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand2);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szText2[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szText2);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);
    }

    if (fflush(pFile) == EOF || fclose(pFile) == EOF)
    {
        ATLTRACE("RRowsetUpdate::FlushData -- "
                 "Couldn't flush or close file\n");
    }

    return S_OK;
}
```

### <a name="handling-changes"></a>處理變更

為了讓您的提供者處理變更，您必須先確定您的資料存放區（例如文字檔或影片檔案）有可讓您對其進行變更的功能。 如果沒有，您應該與提供者專案分開建立該程式碼。

### <a name="handling-null-data"></a>處理 Null 資料

終端使用者可能會傳送 Null 資料。 當您將 Null 值寫入資料來源中的欄位時，可能會有潛在的問題。 想像一下接受城市和郵遞區號值的訂單-採用應用程式;它可以接受其中一個或兩個值，但不能兩者都接受，因為在這種情況下，不可能進行傳遞。 因此，您必須在對應用程式有意義的欄位中限制某些 Null 值的組合。

身為提供者開發人員，您必須考慮儲存該資料的方式、您將如何從資料存放區讀取資料，以及如何將其指定給使用者。 具體來說，您必須考慮如何變更資料來源中的資料列集資料的資料狀態（例如，DataStatus = Null）。 當取用者存取包含 Null 值的欄位時，您可以決定要傳回的值。

查看 UpdatePV 範例中的程式碼;說明提供者可以如何處理 Null 資料。 在 UpdatePV 中，提供者會在資料存放區中寫入字串 "Null"，以儲存 Null 資料。 當它從資料存放區讀取 Null 資料時，它會看到該字串，然後清空緩衝區，並建立 Null 字串。 它也具有 `IRowsetImpl::GetDBStatus` 的覆寫，如果該資料值是空的，它會傳回 DBSTATUS_S_ISNull。

### <a name="marking-nullable-columns"></a>標記可為 Null 的資料行

如果您也要執行架構資料列集（請參閱 `IDBSchemaRowsetImpl`），則您的執行應該會在 DBSCHEMA_COLUMNS 資料列集中指定（通常是由 CxxxSchemaColSchemaRowset 在提供者中標示），該資料行可為 null。

您也需要指定所有可為 null 的資料行包含您 `GetColumnInfo`版本中的 DBCOLUMNFLAGS_ISNullABLE 值。

在 OLE DB 範本 中，如果您無法將資料行標示為可為 null，則提供者會假設它們必須包含值，而且不允許取用者將其傳送 null 值。

下列範例顯示如何在 UpdatePV 中 CUpdateCommand 函式（請參閱 UpProvRS）中的 `CommonGetColInfo` 函式。 請注意，資料行對於可為 null 的資料行有此 DBCOLUMNFLAGS_ISNullABLE。

```cpp
/////////////////////////////////////////////////////////////////////////////
// CUpdateCommand (in UpProvRS.cpp)

ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols, bool bBookmark)
{
    static ATLCOLUMNINFO _rgColumns[6];
    ULONG ulCols = 0;

    if (bBookmark)
    {
        ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,
                            sizeof(DWORD), DBTYPE_BYTES,
                            0, 0, GUID_NULL, CAgentMan, dwBookmark,
                            DBCOLUMNFLAGS_ISBOOKMARK)
        ulCols++;
    }

    // Next set the other columns up.
    // Add a fixed length entry for OLE DB conformance testing purposes
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Fixed"), 1, 4, DBTYPE_UI4,
                        10, 255, GUID_NULL, CAgentMan, dwFixed,
                        DBCOLUMNFLAGS_WRITE |
                        DBCOLUMNFLAGS_ISFIXEDLENGTH)
    ulCols++;

    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command"), 2, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szCommand,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text"), 3, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szText,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;

    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command2"), 4, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szCommand2,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text2"), 5, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szText2,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;

    if (pcCols != NULL)
    {
        *pcCols = ulCols;
    }

    return _rgColumns;
}
```

### <a name="default-values"></a>預設值

如同 Null 資料，您必須負責處理變更預設值。

`FlushData` 和 `Execute` 的預設值是傳回 S_OK。 因此，如果您未覆寫此函式，變更就會顯示為成功（S_OK 將會傳回），但不會傳送到資料存放區。

在 `UpdatePV` 範例（在 Rowset. h 中）中，`SetDBStatus` 方法會處理預設值，如下所示：

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* pdbStatus, CSimpleRow* pRow,
                            ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pRow != NULL && pColInfo != NULL && pdbStatus != NULL);

    void* pData = NULL;
    char* pDefaultData = NULL;
    DWORD* pFixedData = NULL;

    switch (*pdbStatus)
    {
        case DBSTATUS_S_DEFAULT:
            pData = (void*)&m_rgRowData[pRow->m_iRowset];
            if (pColInfo->wType == DBTYPE_STR)
            {
                pDefaultData = (char*)pData + pColInfo->cbOffset;
                strcpy_s(pDefaultData, "Default");
            }
            else
            {
                pFixedData = (DWORD*)((BYTE*)pData +
                                          pColInfo->cbOffset);
                *pFixedData = 0;
                return S_OK;
            }
            break;
        case DBSTATUS_S_ISNULL:
        default:
            break;
    }
    return S_OK;
}
```

### <a name="column-flags"></a>資料行旗標

如果您在資料行上支援預設值，您需要使用 \<提供者類別中的中繼資料來設定它\>SchemaRowset 類別。 設定 `m_bColumnHasDefault = VARIANT_TRUE`。

您也必須負責設定使用 DBCOLUMNFLAGS 列舉型別指定的資料行旗標。 資料行旗標會描述資料行特性。

例如，在 `UpdatePV` 的 `CUpdateSessionColSchemaRowset` 類別中（在 Session. h 中），會以這種方式設定第一個資料行：

```cpp
// Set up column 1
trData[0].m_ulOrdinalPosition = 1;
trData[0].m_bIsNullable = VARIANT_FALSE;
trData[0].m_bColumnHasDefault = VARIANT_TRUE;
trData[0].m_nDataType = DBTYPE_UI4;
trData[0].m_nNumericPrecision = 10;
trData[0].m_ulColumnFlags = DBCOLUMNFLAGS_WRITE |
                            DBCOLUMNFLAGS_ISFIXEDLENGTH;
lstrcpyW(trData[0].m_szColumnDefault, OLESTR("0"));
m_rgRowData.Add(trData[0]);
```

這段程式碼會指定資料行支援預設值0、它是可寫入的，而且資料行中的所有資料都具有相同的長度。 如果您想要資料行中的資料具有可變長度，則不會設定此旗標。

## <a name="see-also"></a>另請參閱

[建立 OLE DB 提供者](creating-an-ole-db-provider.md)
