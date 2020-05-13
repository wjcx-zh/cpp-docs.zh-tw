---
title: 建立可更新的提供者
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 720ceba397d17642402de4d44cbb4481852fa153
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365563"
---
# <a name="creating-an-updatable-provider"></a>建立可更新的提供者

可視C++支援可更新(寫入)數據存儲的可更新提供程式或提供程式。 本主題討論如何使用 OLE DB 樣本建立可更新的提供程式。

本主題假定您從可行的提供程式開始。 創建可增加提供程式有兩個步驟。 您必須首先決定提供程式將如何更改數據存儲;但是,您必須首先決定提供程式將如何對數據存儲進行更改。具體來說,更改是立即執行還是延遲,直到發佈更新命令。 「[使提供者可上可存取](#vchowmakingprovidersupdatable)」一節描述了在提供程式代碼中需要執行的更改和設置。

接下來,必須確保提供程式包含所有功能,以支援消費者可能請求的任何功能。 如果消費者想要更新數據存儲,則提供程式必須包含將數據保存到數據存儲的代碼。 例如,您可以使用 C 執行時庫或 MFC 對數據源執行此類操作。 寫[入資料來源](#vchowwritingtothedatasource)「部分介紹了如何寫入資料源、處理 NULL 和預設值以及設定欄標誌。

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)是可更新提供程式的範例。 更新PV與 MyProv 相同,但具有可更新的支援。

## <a name="making-providers-updatable"></a><a name="vchowmakingprovidersupdatable"></a>使提供者可上可

使提供程式正常運行的關鍵是瞭解您希望提供程式在數據存儲上執行哪些操作,以及您希望提供程式如何執行這些操作。 具體而言,主要問題是,在發佈更新命令之前,是否立即完成對數據存儲的更新或延遲(批處理)。

您必須首先決定是否繼承行`IRowsetChangeImpl`集類`IRowsetUpdateImpl`或行集類。 根據您選擇實現的這些功能,三種方法的功能將受到影響: `SetData``InsertRows`、`DeleteRows`和 。

- 如果從[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)繼承,調用這三種方法將立即更改數據存儲。

- 如果從[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)繼承,則這些方法將更改延遲到`Update`呼`GetOriginalData`叫`Undo`或 。 如果更新涉及多個更改,它們以批處理模式執行(請注意,批處理更改可能會增加相當大的記憶體開銷)。

從`IRowsetUpdateImpl`派生的請`IRowsetChangeImpl`注意 。 因此,`IRowsetUpdateImpl`為您提供更改功能和批次處理功能。

### <a name="to-support-updatability-in-your-provider"></a>支援提供者的升資料度

1. 在行集類別中,從`IRowsetChangeImpl`繼承`IRowsetUpdateImpl`或 。 這些類別為變更資料儲存提供適當的介面:

   **新增 IRowset 變更**

   使用此`IRowsetChangeImpl`表單新增到繼承鍊:

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   還要添加到`COM_INTERFACE_ENTRY(IRowsetChange)`排`BEGIN_COM_MAP`集 類中的節。

   **新增 IRowset 更新**

   使用此`IRowsetUpdate`表單新增到繼承鍊:

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > 應從繼承鏈`IRowsetChangeImpl`中刪除該行。 前面提到的指令的例外情況必須包括的代碼`IRowsetChangeImpl`。

1. 將以下內容加入 COM`BEGIN_COM_MAP ... END_COM_MAP`地圖( )

   |  如果實現   |           新增到 COM 地圖             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | 如果實現 | 新增到屬性集映射 |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. 在指令中,將以下內容加入到屬性集映射(`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`)

   |  如果實現   |                                             新增到屬性集映射                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. 在屬性集映射中,還應包括以下所有設置,如下所示:

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

   通過在 Atldb.h 中查找屬性 ED 和值(如果 Atldb.h 與聯機文檔不同,Atldb.h 將取代文檔),可以找到這些宏調用中使用的值。

   > [!NOTE]
   > OLE DB`VARIANT_FALSE``VARIANT_TRUE`範本需要許多 和設置;OLE DB 規範表示它們可以讀取/寫入,但 OLE DB 範本只能支援一個值。

   **如果實作 IRowsetChangeimpl**

   如果實現`IRowsetChangeImpl`,則必須在提供程式上設置以下屬性。 這些屬性主要用於通過`ICommandProperties::SetProperties`請求介面。

   - `DBPROP_IRowsetChange`:設定此自動設定`DBPROP_IRowsetChange`。

   - `DBPROP_UPDATABILITY``IRowsetChange`: 在`SetData`上 指定支援方法的`DeleteRows`位`InsertRow`遮罩 , 或 。

   - `DBPROP_CHANGEINSERTEDROWS`:消費者可以調用`IRowsetChange::DeleteRows``SetData`或 用於新插入的行。

   - `DBPROP_IMMOBILEROWS`:行集不會重新排序插入或更新的行。

   **如果實作 IRowset 更新**

   如果實現`IRowsetUpdateImpl`,除了`IRowsetChangeImpl`為 以前列出的設置所有屬性外,還必須在提供程式上設置以下屬性:

   - `DBPROP_IRowsetUpdate`.

   - `DBPROP_OWNINSERT`:必須READ_ONLY和VARIANT_TRUE。

   - `DBPROP_OWNUPDATEDELETE`:必須READ_ONLY和VARIANT_TRUE。

   - `DBPROP_OTHERINSERT`:必須READ_ONLY和VARIANT_TRUE。

   - `DBPROP_OTHERUPDATEDELETE`:必須READ_ONLY和VARIANT_TRUE。

   - `DBPROP_REMOVEDELETED`:必須READ_ONLY和VARIANT_TRUE。

   - `DBPROP_MAXPENDINGROWS`.

   > [!NOTE]
   > 如果您支援通知,您可能也擁有一些其他屬性;但是,如果支援通知,則可能還有其他屬性。請參閱此列表的`IRowsetNotifyCP`節。

## <a name="writing-to-the-data-source"></a><a name="vchowwritingtothedatasource"></a>寫入資料來源

要從資料來源讀取,請呼叫函數`Execute`。 要寫入資料來源,請呼叫 函`FlushData`數 。 (在一般意義上說,刷新意味著將對表或索引的修改保存到磁碟。

```cpp
FlushData(HROW, HACCESSOR);
```

行句柄 (HROW) 和訪問器句柄 (HACCESSOR) 參數允許您指定要寫入的區域。 通常,您一次編寫一個資料欄位。

該方法`FlushData`以最初存儲數據的格式寫入數據。 如果不重寫此函數,提供程式將正常運行,但不會將更改刷新到數據存儲。

### <a name="when-to-flush"></a>何時刷新

每當需要將數據寫入數據存儲時,提供程式範本都會調用 FlushData;這通常(但並非總是)是呼叫以下函數的結果:

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows`( 如果有要列中插入的新資料 )

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>運作方式

使用者發出需要刷新(如更新)的呼叫,並且此調用將傳遞給提供者,提供程式始終執行以下操作:

- 每當`SetDBStatus`您綁定了狀態值時,都會調用。

- 檢查列標誌。

- 呼叫 `IsUpdateAllowed`。

這三個步驟有助於提供安全。 然後提供程式呼叫`FlushData`。

### <a name="how-to-implement-flushdata"></a>如何實作刷新資料

要實現`FlushData`,您需要考慮幾個問題:

確保數據存儲可以處理更改。

處理 NULL 值。

### <a name="handling-default-values"></a>處理預設值。

要實現自己的`FlushData`方法,您需要:

- 轉到排設置類。

- 在行集類別中,將聲明放在:

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- 提供的`FlushData`實現。

良好的實現僅`FlushData`存儲實際更新的行和列。 您可以使用 HROW 和 HACCESSOR 參數來確定要儲存的當前行和列以進行優化。

通常,最大的挑戰是使用您自己的本機數據存儲。 如果可能,請嘗試:

- 儘可能簡單地將寫入數據存儲的方法保留。

- 處理 NULL 值(可選但建議)。

- 處理預設值(可選但建議)。

最好的辦法是在資料儲存中為 NULL 和預設值設定實際指定值。 最好可以推斷此數據。 如果沒有,建議您不要允許 NULL 和預設值。

下面的範例顯示如何`FlushData``RUpdateRowset``UpdatePV`在範例中的類別中實現(請參閱範例代碼中的 Rowset.h):

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

要使提供者處理更改,首先需要確保數據存儲(如文本檔或視頻檔)具有允許您對其進行更改的設施。 如果沒有,則應與提供程式項目分開創建該代碼。

### <a name="handling-null-data"></a>處理空資料

最終使用者可能會發送 NULL 資料。 將 NULL 值寫入資料來源中的欄位時,可能存在問題。 想像一下,接受城市和郵政編碼值的訂單受理應用程式;它可以接受任一或兩個值,但不能兩者,因為在這種情況下,交付是不可能的。 因此,您必須限制欄位中某些對應用程式有意義的 NULL 值群組。

作為提供程式開發人員,您必須考慮如何存儲該資料、如何從數據存儲中讀取數據以及如何向使用者指定這些數據。 具體而言,您必須考慮如何更改數據來源中排組數據的數據狀態(例如,資料狀態 = NULL)。 當使用者存取包含 NULL 值的欄位時,您可以決定返回什麼值。

查看 UpdatePV 範例中的代碼;它說明瞭提供者如何處理 NULL 資料。 在 UpdatePV 中,提供程式透過在資料儲存中寫入字串「NULL」來儲存 NULL 資料。 當它從資料儲存中讀取 NULL 資料時,它會看到該字串,然後清空緩衝區,創建 NULL 字串。 如果資料值為空,`IRowsetImpl::GetDBStatus`它還可以覆蓋該值DBSTATUS_S_ISNULL返回。

### <a name="marking-nullable-columns"></a>標記可標記列

如果還實現架構行集(請參閱`IDBSchemaRowsetImpl`),則實現應在DBSCHEMA_COLUMNS行集(通常由 CxxxSchemaColSchemaRowset 在提供程式中標記)中指定該列為空。

您還需要指定所有可空列在版本的`GetColumnInfo`中 包含DBCOLUMNFLAGS_ISNULLABLE值。

在 OLE DB 樣本實現中,如果無法將列標記為空,提供程式將假定它們必須包含值,並且不允許消費者將其發送為 null 值。

下面的範例展示如何在 UpdatePV 中的 CUpdate 命令(請參閱 UpProvRS.cpp) 中實現`CommonGetColInfo`該函數。 請注意列如何對空列DBCOLUMNFLAGS_ISNULLABLE。

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

與 NULL 資料一樣,您有責任處理更改的預設值。

的預設值`FlushData``Execute`是返回S_OK。 因此,如果不重寫此函數,更改似乎成功(S_OK將返回),但它們不會傳輸到數據存儲。

在`UpdatePV`範例(在 Rowset.h 中`SetDBStatus`),該方法處理預設值的方式如下:

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

### <a name="column-flags"></a>欄標號

如果支援列上的預設值,則需要使用提供程式類\<\>SchemaRowset 類中的中繼資料設定該值。 設定 `m_bColumnHasDefault = VARIANT_TRUE`。

您還負責設置列標誌,這些標誌是使用 DBCOLUMNFLAGS 枚舉類型指定的。 列標誌描述列特徵。

例如,在`CUpdateSessionColSchemaRowset`(`UpdatePV`在 Session.h 中)中的類別中,第一列的設定方式是這樣的:

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

此代碼指定列支援預設值 0、可寫入以及列中的所有資料具有相同的長度。 如果希望列中的數據具有可變長度,則不會設置此標誌。

## <a name="see-also"></a>另請參閱

[建立 OLE 資料庫提供者](creating-an-ole-db-provider.md)
