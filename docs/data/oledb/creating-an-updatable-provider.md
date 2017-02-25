---
title: "建立可更新的提供者 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "告知, 提供者中的支援"
  - "OLE DB 提供者, 建立"
  - "OLE DB 提供者, 可更新的"
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# 建立可更新的提供者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 6.0 只能支援唯讀的提供者 \(Provider\)。  Visual C\+\+ .NET 能支援可更新的提供者，或可更新 \(寫入\) 資料存放區的提供者。  本主題將討論如何使用 OLE DB 樣板來建立可更新的提供者。  
  
 本主題假設您從可用提供者開始建立。  建立可更新的提供者需要兩個步驟。  您必須先決定提供者變更資料存放區的方式，更明確地說就是，需要立即進行變更，或延後直到發出更新命令時。  [使提供者可更新](#vchowmakingprovidersupdatable)章節內容將說明需在提供者程式碼內進行的變更和設定。  
  
 接著，您必須確認提供者包含所有可支援消費者可能要求的功能。  如果消費者想要更新資料存放區，提供者就必須包含可讓資料保存於資料存放區的程式碼。  例如，您可使用 C 執行階段程式庫或 MFC 在資料來源上執行這類作業。  [寫入至資料來源](#vchowwritingtothedatasource)章節內容說明如何寫入至資料來源、處理 **NULL** 和預設值，以及設定資料行旗標。  
  
> [!NOTE]
>  UpdatePV 是可更新提供者的範例。  UpdatePV 和 MyProv 相同，但增加了可更新支援。  
  
##  <a name="vchowmakingprovidersupdatable"></a> 使提供者可更新  
 讓提供者可更新的關鍵，在於了解您希望提供者在資料存放區上執行什麼作業，以及希望提供者如何執行這些作業。  更明確地說，主要問題是資料存放區上的更新是要立即執行，或是延後 \(批次\) 直到更新命令發出時再執行。  
  
 您必須先決定是否繼承自資料列集類別的 `IRowsetChangeImpl` 或 `IRowsetUpdateImpl`。  根據您選擇實作的項目，以下三個方法的功能將受到影響：`SetData`、**InsertRows** 和 `DeleteRows`。  
  
-   如果您從 [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md) 繼承，立即呼叫這三個方法便會變更資料存放區。  
  
-   如果您繼承自 [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)，這些方法會延後您對資料存放區所做的變更，直到您呼叫 **Update**、`GetOriginalData` 或 **Undo**。  如果更新牽涉到多處變更，這些變更將會以批次模式執行 \(請注意，批次變更會增加大量的記憶體過載\)。  
  
 請注意，`IRowsetUpdateImpl` 是由 `IRowsetChangeImpl` 衍生。  因此，`IRowsetUpdateImpl` 賦予您變更功能以及批次功能。  
  
#### 若要在提供者內支援變更性  
  
1.  在您的資料列集類別內，繼承自 `IRowsetChangeImpl` 或 `IRowsetUpdateImpl`。  這些類別提供適當的介面來變更資料存放區：  
  
     **加入 IRowsetChange**  
  
     使用下列方式，將 `IRowsetChangeImpl` 加入至繼承 \(Inheritance\) 鏈結內：  
  
    ```  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     同時將 `COM_INTERFACE_ENTRY(IRowsetChange)` 加入至資料列集類別的 `BEGIN_COM_MAP` 區段。  
  
     **加入 IRowsetUpdate**  
  
     使用下列形式，將 `IRowsetUpdate` 加入繼承鏈結內：  
  
    ```  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  您應移除在繼承鏈結的 `IRowsetChangeImpl` 行。  這個對於先前所述的指示詞特例必須包含 `IRowsetChangeImpl` 程式碼。  
  
2.  將下列項目加入至 COM 對應 \(**BEGIN\_COM\_MAP ...END\_COM\_MAP**\):  
  
    |如果您實作|請加入至 COM 對應|  
    |-----------|-----------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  在您的命令中加入下列項目至屬性集 \(Property Set\) 對應 \(**BEGIN\_PROPSET\_MAP ...END\_PROPSET\_MAP**\)：  
  
    |如果您實作|請加入至屬性集對應|  
    |-----------|---------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  您也應該在屬性集對應內，包含下列所有設定：  
  
    ```  
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
  
     您可以尋找 Atldb.h 中的屬性 ID 和數值，找出這些巨集呼叫所使用的數值 \(如果 Atldb.h 與線上文件不同，Atldb.h 將取代文件\)。  
  
    > [!NOTE]
    >  OLE DB 樣板需要許多 **VARIANT\_FALSE** 和 `VARIANT_TRUE` 設定，OLE DB 規格提到它們可被讀取\/寫入，但是 OLE DB 樣板只支援一個值。  
  
     **如果要實作 IRowsetChangeImpl**  
  
     如果您要實作 `IRowsetChangeImpl`，必須在提供者內設定下列屬性。  這些屬性主要用於透過 **ICommandProperties::SetProperties** 來要求介面。  
  
    -   `DBPROP_IRowsetChange`：設定這個屬性就會自動設定 **DBPROP\_IRowsetChange**。  
  
    -   `DBPROP_UPDATABILITY`：指定 `IRowsetChange`: `SetData`、`DeleteRows` 或 `InsertRow` 支援方法的位元遮罩。  
  
    -   `DBPROP_CHANGEINSERTEDROWS`：消費者可為新插入的資料列呼叫 **IRowsetChange::DeleteRows** 或 `SetData`。  
  
    -   `DBPROP_IMMOBILEROWS`：資料列集無法重新排列插入或更新的資料列。  
  
     **如果您實作 IRowsetUpdateImpl**  
  
     若您實作 `IRowsetUpdateImpl`，除了設定先前所列的 `IRowsetChangeImpl` 所有屬性外，還必須在提供者上設定下列屬性：  
  
    -   `DBPROP_IRowsetUpdate`.  
  
    -   `DBPROP_OWNINSERT`：必須是 READ\_ONLY AND VARIANT\_TRUE。  
  
    -   `DBPROP_OWNUPDATEDELETE`：必須是 READ\_ONLY AND VARIANT\_TRUE。  
  
    -   `DBPROP_OTHERINSERT`：必須是 READ\_ONLY AND VARIANT\_TRUE。  
  
    -   `DBPROP_OTHERUPDATEDELETE`：必須是 READ\_ONLY AND VARIANT\_TRUE。  
  
    -   `DBPROP_REMOVEDELETED`：必須是 READ\_ONLY AND VARIANT\_TRUE。  
  
    -   `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  如果您支援告知，您可能也會有其他某些屬性，請參閱 `IRowsetNotifyCP` 中的章節以取得清單。  
  
     如需如何設定屬性的範例，請參閱 [UpdatePV](http://msdn.microsoft.com/zh-tw/c8bed873-223c-4a7d-af55-f90138c6f38f) 的 **CUpdateCommand** \(在 Rowset.h 內\) 屬性集設定對應。  
  
##  <a name="vchowwritingtothedatasource"></a> 寫入至資料來源  
 若要讀取資料來源，請呼叫 **Execute** 函式。  若要寫入至資料來源，請呼叫 `FlushData` 函式 \(就一般含意而言，flush 意味將您對資料表或索引所做的修改儲存至磁碟\)。  
  
```  
FlushData(HROW, HACCESSOR);  
```  
  
 資料列控制代碼 \(*HROW*\) 和存取子控制代碼 \(*HACCESSOR*\) 引數可讓您指定要寫入的區域。  通常您會一次寫入一個資料欄位。  
  
 `FlushData` 方法會以資料原本儲存的格式來寫入資料。  如果您沒有覆寫這個函式，提供者將可正常運作，但是變更並不會清除至資料存放區。  
  
### 何時儲存  
 提供者樣板會在需要將資料寫入資料存放區的任何時候，呼叫 `FlushData`；通常這會發生在 \(但並不總是\) 下列函式呼叫產生結果時：  
  
-   **IRowsetChange::DeleteRows**  
  
-   **IRowsetChange::SetData**  
  
-   **IRowsetChange::InsertRows** \(如果有新資料插入至資料列\)  
  
-   **IRowsetUpdate::Update**  
  
### 如何運作  
 消費者執行需要儲存變更 \(例如 **Update**\) 的呼叫，而這個呼叫會傳遞至一直執行下列工作的提供者：  
  
-   在您每次擁有繫結狀態值時呼叫 `SetDBStatus` \(請參閱《OLE DB 程式設計人員參考》第六章＜資料部分：狀態＞\)。  
  
-   檢查資料行旗標。  
  
-   呼叫 `IsUpdateAllowed`。  
  
 這三個步驟有助於提供安全性。  接著提供者將呼叫 `FlushData`。  
  
### 如何實作 FlushData  
 若要實作 `FlushData`，您需要考慮一些問題：  
  
-   確認資料存放區可處理變更。  
  
-   處理 **NULL** 值。  
  
-   處理預設值。  
  
 若要實作自己的 `FlushData` 方法，您需要：  
  
-   移至資料列集類別。  
  
-   在資料列集類別內放置下列宣告：  
  
```  
HRESULT FlushData(HROW, HACCESSOR)  
{  
    // Insert your implementation here and return an HRESULT.  
}  
```  
  
-   提供 `FlushData` 的實作。  
  
 良好的 `FlushData` 實作只會儲存實際完成更新的資料列和資料行。  您可使用 *HROW* 和 *HACCESSOR* 參數來決定目前儲存的資料列和資料行，以進行最佳化。  
  
 通常，最大的挑戰是使用您自己的原生資料存放區。  可能的話，請嘗試：  
  
-   盡可能簡化寫入資料存放區的方法。  
  
-   處理 **NULL** 值 \(選擇項，但建議使用\)。  
  
-   處理預設值 \(選擇項，但建議使用\)。  
  
 最佳作法是使資料存放區的 **NULL** 和預設值都有實際的指定值。  若您能推斷 \(Extrapolate\) 此資料，那就更好了。  若不能，則建議您不使用 **NULL** 和預設值。  
  
 下面範例會說明在 [UpdatePV](http://msdn.microsoft.com/zh-tw/c8bed873-223c-4a7d-af55-f90138c6f38f) 範例中 \(請參閱範例程式碼的 Rowset.h\)，`FlushData` 如何在 `RUpdateRowset` 類別內實作：  
  
```  
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
  
### 處理變更  
 為了讓提供者能處理變更，您需要先確認資料存放區 \(例如文字檔或視訊檔\) 擁有可讓您進行變更的設施。  如果沒有，您應該建立不同於提供者 \(Provider\) 專案的程式碼。  
  
### 處理 NULL 資料  
 使用者可能傳送 **NULL** 資料。  當您將 **NULL** 值寫入資料來源欄位時，可能存有潛在的問題。  試想，有一個可接受縣市和郵遞區號值的訂單處理應用程式；它可接受其中一個值或兩個值，但不能都沒有值，因為那樣不可能進行傳送。  因此您必須針對應用程式的實際需要，在欄位中限制某些 **NULL** 值的組合。  
  
 身為提供者開發人員，您必須考慮如何儲存該資料、如何從資料存放區讀取資料以及如何將它指定給使用者。  明確地說，您必須考量如何變更資料來源中資料列集資料的資料狀態 \(例如，DataStatus \= **NULL**\)。  您要決定當消費者存取包含 **NULL** 值的欄位時，需傳回何數值。  
  
 檢視 [UpdatePV](http://msdn.microsoft.com/zh-tw/c8bed873-223c-4a7d-af55-f90138c6f38f) 範例的程式碼；此程式碼將說明提供者如何處理 **NULL** 資料。  在 UpdatePV，提供者會將字串 NULL 寫入資料存放區來儲存 **NULL** 資料。  當它從資料來源讀取 **NULL** 資料時，一看到是該字串，就會清空緩衝區，建立一個 **NULL** 字串。  它也有一個 `IRowsetImpl::GetDBStatus` 覆寫，在此覆寫中，若該資料值是空的，它就會傳回 **DBSTATUS\_S\_ISNULL**。  
  
### 標記 Null 設定資料行  
 如果您也實作結構描述 \(Schema\) 資料列集 \(請參閱 `IDBSchemaRowsetImpl`\)，您的實作 \(Implementation\) 應指定於資料行為 Null 設定的 **DBSCHEMA\_COLUMNS** 資料列集 \(通常以 **C***xxx***SchemaColSchemaRowset** 的形式標記於您的提供者內\)。  
  
 您也需要指定，在 `GetColumnInfo` 版本內，所有的 Null 設定資料行都包含 **DBCOLUMNFLAGS\_ISNULLABLE** 值。  
  
 在 OLE DB 樣板實作中，如果您沒有將資料行標記成可為 Null，提供者就會假設它們必須包含值且不允許消費者傳送 null 值給它。  
  
 下列範例說明在 UpdatePV 中，**CommonGetColInfo** 函式如何實作於 **CUpdateCommand** \(請參閱 UpProvRS.cpp\)。  請注意，Null 設定的資料行如何擁有 **DBCOLUMNFLAGS\_ISNULLABLE**。  
  
```  
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
  
### 預設值  
 和 **NULL** 資料一樣，您必須負責變更預設值。  
  
 `FlushData` 和 **Execute** 預設為傳回 `S_OK`。  因此，如果您沒有覆寫這個函式，變更看起來似乎是成功了 \(傳回 `S_OK`\)，但事實上它們不會傳給資料存放區。  
  
 在 [UpdatePV](http://msdn.microsoft.com/zh-tw/c8bed873-223c-4a7d-af55-f90138c6f38f) 範例中 \(在 Rowset.h 內\)，`SetDBStatus` 方法將依下列方式處理預設值：  
  
```  
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
  
### 資料行旗標  
 如果支援在資料行的預設值，使用在 **\<***提供者類別***\>SchemaRowset** 類別，的中繼資料必須設定它。  設定 *m\_bColumnHasDefault* \= `VARIANT_TRUE`。  
  
 您也要負責設定資料行旗標，它是透過 **DBCOLUMNFLAGS** 列舉型別來指定的。  資料行旗標描述了資料行特性。  
  
 例如，在 [UpdatePV](http://msdn.microsoft.com/zh-tw/c8bed873-223c-4a7d-af55-f90138c6f38f) \(在 Session.h 中\) 的 `CUpdateSessionColSchemaRowset` 類別內，第一個資料行會依照下列方式來設定：  
  
```  
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
  
 這段程式碼指定了該資料行可支援預設值 0、是可寫入的，以及資料行中的所有資料都具有相同長度等特性。  若您希望資料行的資料具有可變的長度，您就不應設定這個旗標。  
  
## 請參閱  
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)