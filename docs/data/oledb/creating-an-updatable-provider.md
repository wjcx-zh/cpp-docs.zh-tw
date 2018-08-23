---
title: 建立可更新的提供者 |Microsoft Docs
ms.custom: ''
ms.date: 08/16/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fffc1ceef1f67dadde61190ccb12ce1cd5b7ba9b
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "42572552"
---
# <a name="creating-an-updatable-provider"></a>建立可更新的提供者

Visual c + + 支援可更新的提供者 」 或 「 可更新的提供者 （寫入） 資料存放區。 本主題討論如何建立可更新的提供者使用 OLE DB 範本。  
  
 本主題假設您要啟動的可運作的提供者。 有兩個步驟來建立可更新的提供者。 您必須先決定要如何提供者時，將資料存放區中，進行變更具體而言，變更會立即進行還是延後，直到發出 update 命令。 一節 「[讓提供者可更新](#vchowmakingprovidersupdatable)」 描述的變更與您只需要提供者程式碼中的設定。  
  
 接下來，您必須確定您的提供者包含所有的功能來支援取用者可能會要求它的任何項目。 如果取用者想要更新資料存放區，提供者必須包含資料保存到資料存放區的程式碼。 比方說，您可能會使用 MFC 的 C 執行階段程式庫來執行這類作業在資料來源。 一節 「[寫入至資料來源](#vchowwritingtothedatasource)」 說明如何寫入至資料來源，處理 NULL 和預設值，並設定資料行的旗標。  
  
> [!NOTE]
>  [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)是可更新的提供者的範例。 為 MyProv，但具有可更新的支援 UpdatePV 都是一樣的。  
  
##  <a name="vchowmakingprovidersupdatable"></a> 建立可更新的提供者  

 若要讓提供者可更新的索引鍵了解您想要您的提供者，在資料存放區和如何在您想要執行這些作業的提供者上執行哪些的作業。 具體而言，主要問題是是否要立即或延後更新資料存放區 （批次處理） 直到發出 update 命令。  
  
 您必須先決定是否要繼承自`IRowsetChangeImpl`或`IRowsetUpdateImpl`在您的資料列集類別。 根據這些您的選擇來實作，將會受到影響的三種方法的功能： `SetData`， `InsertRows`，和`DeleteRows`。  
  
- 如果您繼承自[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)，立即呼叫這三種方法會變更資料存放區。  
  
- 如果您繼承自[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)，方法會延遲到資料存放區的變更，直到您呼叫`Update`， `GetOriginalData`，或`Undo`。 如果更新涉及數項變更，他們會執行批次模式 （請注意，批次的變更可以加入大量的記憶體額外負荷）。  
  
 請注意，`IRowsetUpdateImpl`衍生自`IRowsetChangeImpl`。 因此，`IRowsetUpdateImpl`可讓您變更功能，以及批次功能。  
  
#### <a name="to-support-updatability-in-your-provider"></a>若要在您的提供者支援更新的能力  
  
1. 在您的資料列集類別，繼承自`IRowsetChangeImpl`或`IRowsetUpdateImpl`。 這些類別會提供適當的介面，來變更資料存放區：  
  
     **新增 IRowsetChange**  
  
     新增`IRowsetChangeImpl`您使用這種形式的繼承鏈結：  
  
    ```cpp  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     也加入`COM_INTERFACE_ENTRY(IRowsetChange)`至`BEGIN_COM_MAP`資料列集類別中的區段。  
  
     **新增 IRowsetUpdate**  
  
     新增`IRowsetUpdate`您使用這種形式的繼承鏈結：  
  
    ```cpp  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  您應該移除`IRowsetChangeImpl`繼承鏈結中的一行。 此一的例外狀況，以先前所述的指示詞必須包含的程式碼`IRowsetChangeImpl`。  
  
2.  將下列內容新增至 COM 對應 (`BEGIN_COM_MAP ... END_COM_MAP`):  
  
    |如果您實作|將新增到 COM 對應|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  在命令中，將下列內容新增至您的屬性集對應 (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`):  
  
    |如果您實作|將加入至屬性集合對應|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  在屬性集對應，您應該也包含下列設定的所有下面所列：  
  
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
  
     您可以找到這些巨集呼叫中使用，藉由尋找為 Atldb.h 中的屬性識別碼和值的值 （如果為 Atldb.h 和不同的線上文件，為 Atldb.h 取代文件）。  
  
    > [!NOTE]
    >  許多`VARIANT_FALSE`和`VARIANT_TRUE`設定所需的 OLE DB 範本; OLE DB 規格表示它們可以是讀取/寫入，但 OLE DB 範本只能支援一個值。  
  
     **如果您實作 IRowsetChangeImpl**  
  
     如果您實作`IRowsetChangeImpl`，您必須在您的提供者上設定下列屬性。 這些屬性主要用來要求介面傳遞`ICommandProperties::SetProperties`。  
  
    - `DBPROP_IRowsetChange`： 設定就會自動設定`DBPROP_IRowsetChange`。  
  
    - `DBPROP_UPDATABILITY`： 指定支援的方法位元遮罩`IRowsetChange`: `SetData`， `DeleteRows`，或`InsertRow`。  
  
    - `DBPROP_CHANGEINSERTEDROWS`： 取用者可以呼叫`IRowsetChange::DeleteRows`或`SetData`新插入的資料列。  
  
    - `DBPROP_IMMOBILEROWS`： 資料列集不會重新排列插入或更新的資料列。  
  
     **如果您實作 IRowsetUpdateImpl**  
  
     如果您實作`IRowsetUpdateImpl`，您必須設定下列屬性在您的提供者，另外設定的所有屬性`IRowsetChangeImpl`先前所列：  
  
    - `DBPROP_IRowsetUpdate`.  
  
    - `DBPROP_OWNINSERT`： 必須是 READ_ONLY 和為 VARIANT_TRUE。  
  
    - `DBPROP_OWNUPDATEDELETE`： 必須是 READ_ONLY 和為 VARIANT_TRUE。  
  
    - `DBPROP_OTHERINSERT`： 必須是 READ_ONLY 和為 VARIANT_TRUE。  
  
    - `DBPROP_OTHERUPDATEDELETE`： 必須是 READ_ONLY 和為 VARIANT_TRUE。  
  
    - `DBPROP_REMOVEDELETED`： 必須是 READ_ONLY 和為 VARIANT_TRUE。  
  
    - `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  如果您支援通知，您可能還有其他一些屬性以及;請參閱節`IRowsetNotifyCP`如這份清單。  
  
##  <a name="vchowwritingtothedatasource"></a> 寫入至資料來源  
 若要讀取的資料來源，請呼叫`Execute`函式。 若要寫入的資料來源，請呼叫`FlushData`函式。 （在一般狀況下，排清方法來儲存您對資料表或索引到磁碟進行的修改）。  

```cpp

FlushData(HROW, HACCESSOR);  

```

資料列控制代碼 (HROW) 和存取子控制代碼 (HACCESSOR) 引數可讓您指定要寫入的區域。 一般而言，您會一次寫入的單一資料欄位。

`FlushData`方法在其中它原本儲存的格式寫入資料。 如果您不會覆寫這個函式，您的提供者將會正確運作，但變更並不會清除資料存放區。

### <a name="when-to-flush"></a>排清的時機
提供者範本呼叫 FlushData，每當資料需要可寫入的資料存放區中;這通常 （但不是一定），就會發生因為下列函式的呼叫：

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows` （如果沒有要插入資料列中的新資料）

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>它的運作方式

取用者會呼叫要求 （例如更新） 的排清，這個呼叫會傳遞給提供者，一律會執行下列作業：

- 呼叫`SetDBStatus`即表示已繫結的狀態值。

- 檢查資料行旗標。

- 呼叫 `IsUpdateAllowed`。

這三個步驟會協助提供安全性。 然後在提供者呼叫`FlushData`。

### <a name="how-to-implement-flushdata"></a>如何實作 FlushData

若要實作`FlushData`，您需要考量幾個問題：

確定資料存放區可以處理變更。

處理 NULL 值。

### <a name="handling-default-values"></a>處理預設值。

若要實作您自己的 FlushData 方法，您需要：

- 請移至您的資料列集類別。

- 在 資料列集類別放置下列宣告：

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)  
   {  
      // Insert your implementation here and return an HRESULT.  
   }  
   ```

- 提供的實作`FlushData`。

只有資料列和實際更新的資料行，會將儲存的 FlushData 完善的實作。 您可以使用 HROW 和 HACCESSOR 參數來判斷目前的資料列和儲存最佳化的資料行。

一般而言，最大的挑戰使用您自己的原生資料存放區。 可能的話，請嘗試：

- 請寫入資料存放區越簡單越好的方法。

- 處理 NULL 值 （選擇性但建議使用）。

- 處理預設值 （選擇性但建議使用）。

最佳做法是在您的 NULL 和預設值的資料存放區中實際的指定的值。 最好是如果您可以進行推斷，這項資料。 如果沒有，建議您不允許 NULL，而且預設值。

下列範例顯示如何`FlushData`UpdatePV 範例中 RUpdateRowset 類別中實作 （程式碼範例，請參閱 Rowset.h）：

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

針對您的提供者來處理變更，必須先確定您的資料存放區 （例如文字檔或視訊檔案中） 具有可讓您對它進行變更的功能。 如果沒有，您應該從提供者專案分別建立該程式碼。

### <a name="handling-null-data"></a>處理 NULL 的資料

可以在終端使用者，會將 NULL 資料的傳送。 當您將 NULL 值寫入資料來源中的欄位時，可能會有潛在的問題。 假設訂單處理應用程式可接受值的城市和郵遞區號;它可以接受任一或兩個值，但無法兩者皆否，因為在此情況下會無法傳遞。 因此，您必須限制對您的應用程式有意義的欄位中的 NULL 值的特定組合。

為提供者開發人員，您必須考慮將儲存該項資料的方式、 如何從資料存放區讀取資料以及您指定的方式，向使用者。 具體來說，您必須考慮如何變更資料來源中的資料列集資料的資料狀態 (例如 DataStatus = NULL)。 您決定所取用者存取包含 NULL 值的欄位時要傳回的值。

查看 UpdatePV 範例; 中的程式碼這個範例說明提供者可以如何處理 NULL 的資料。 在 UpdatePV，提供者會儲存 NULL 資料寫入字串"NULL"資料存放區中。 從資料存放區讀取 NULL 的資料，它會看見該字串，並清空緩衝區，建立一個 NULL 字串。 它也會有的覆寫`IRowsetImpl::GetDBStatus`在它會傳回 DBSTATUS_S_ISNULL 如果該資料值是空的。

### <a name="marking-nullable-columns"></a>標記可為 Null 的資料行
如果您也可以實作結構描述資料列集 (請參閱`IDBSchemaRowsetImpl`)，您的實作應該指定 DBSCHEMA_COLUMNS 資料列集 （通常標示您的提供者所 CxxxSchemaColSchemaRowset） 中的資料行是可為 null。

您也需要指定可為 null 的所有資料行包含在您的版本中的 DBCOLUMNFLAGS_ISNULLABLE 值`GetColumnInfo`。

在 OLE DB 範本實作中，如果您無法將標示為可為 null，資料行的提供者會假設它們必須包含值，而且不允許取用者將它傳送 null 值。

下列範例顯示如何`CommonGetColInfo`CUpdateCommand 中實作函式 （請參閱 UpProvRS.cpp） UpdatePV 中。 請注意的資料行具有此 DBCOLUMNFLAGS_ISNULLABLE 可為 null 的資料行的方式。

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

如同 NULL 的資料，您必須負責處理變更預設值。

FlushData 和執行的預設值是傳回 S_OK。 因此，如果您不會覆寫這個函式，所做的變更會顯示成功 （會傳回 S_OK），但不是會傳輸到資料存放區。

在 UpdatePV 中的範例 （Rowset.h)`SetDBStatus`方法會處理預設值，如下所示：

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

如果您支援您的資料行上的預設值，您需要使用中繼資料中的設定它\<提供者類別\>w 類別。 設定`m_bColumnHasDefault`= VARIANT_TRUE。

您也必須將設定資料行旗標，指定使用 DBCOLUMNFLAGS 列舉型別。 資料行旗標會描述資料行的特性。

例如，在`CUpdateSessionColSchemaRowset`類別 （在 Session.h) UpdatePV，在第一個資料行設定這種方式：

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

此程式碼會指定，以及其他項目中，資料行支援預設值是 0，它是可寫入，以及資料行中的所有資料都具有相同的長度。 如果您想要具有可變長度的資料行中的資料，您就不會設定這個旗標。

## <a name="see-also"></a>另請參閱
[建立 OLE DB 提供者](creating-an-ole-db-provider.md)