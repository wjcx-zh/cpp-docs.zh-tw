---
title: 建立可更新的提供者 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 317ccd043b3a69489f9cbd2737ad7741389863c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098637"
---
# <a name="creating-an-updatable-provider"></a>建立可更新的提供者
Visual c + + 支援可更新的提供者或可更新的提供者 （寫入） 資料存放區。 本主題討論如何建立可更新的提供者使用 OLE DB 樣板。  
  
 本主題假設您要啟動與可用的提供者。 有兩個步驟以建立可更新的提供者。 您必須先決定如何提供者時，將資料存放區; 進行變更具體來說，變更會立即進行還是延後，直到發出 update 命令時。 一節 「[讓提供者可更新](#vchowmakingprovidersupdatable)」 描述的變更和設定您需要在提供者程式碼中進行處理。  
  
 接下來，您必須確定您的提供者會包含所有用來支援取用者可能會要求它的任何功能。 如果取用者想要更新資料存放區，提供者必須包含保存到資料存放區資料的程式碼。 比方說，您可能會使用 MFC 的 C 執行階段程式庫來執行這類資料來源上的作業。 一節 「[寫入資料來源](#vchowwritingtothedatasource)」 說明如何寫入資料來源、 處理**NULL**預設值，並將設定資料行旗標。  
  
> [!NOTE]
>  UpdatePV 是可更新的提供者的範例。 為 MyProv，但具有可更新的支援 UpdatePV 都是相同的。  
  
##  <a name="vchowmakingprovidersupdatable"></a> 讓提供者可更新  
 讓提供者可更新的索引鍵了解您想要您的提供者在資料存放區和方式想要執行這些作業的提供者上執行哪些的作業。 具體來說，主要的問題是是否要立即完成或延後更新資料存放區 （批次處理） 直到發出 update 命令。  
  
 您必須先決定是否要繼承自`IRowsetChangeImpl`或`IRowsetUpdateImpl`在您的資料列集類別。 其中您選擇實作，根據三種方法的功能會受到影響： `SetData`， **InsertRows**，和`DeleteRows`。  
  
-   如果您繼承自[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)，立即呼叫這三個方法會變更資料存放區。  
  
-   如果您繼承自[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)，直到您呼叫到資料存放區變更延後的方法**更新**， `GetOriginalData`，或**復原**。 如果更新包括數項變更，它們會在批次模式執行 （請注意，批次變更可以加入相當多的記憶體負擔）。  
  
 請注意，`IRowsetUpdateImpl`衍生自`IRowsetChangeImpl`。 因此，`IRowsetUpdateImpl`可讓您變更功能加上批次功能。  
  
#### <a name="to-support-updatability-in-your-provider"></a>在您的提供者支援更新的能力  
  
1.  在您的資料列集類別繼承自`IRowsetChangeImpl`或`IRowsetUpdateImpl`。 這些類別會提供適當的介面，來變更資料存放區：  
  
     **加入 IRowsetChange**  
  
     新增`IRowsetChangeImpl`您使用這種形式的繼承鏈結：  
  
    ```  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     也新增`COM_INTERFACE_ENTRY(IRowsetChange)`至`BEGIN_COM_MAP`> 一節，在您的資料列集類別。  
  
     **加入 IRowsetUpdate**  
  
     新增`IRowsetUpdate`您使用這種形式的繼承鏈結：  
  
    ```  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  您應該移除`IRowsetChangeImpl`繼承鏈結中的行。 先前所述的指示詞這個一個例外狀況必須包含的程式碼`IRowsetChangeImpl`。  
  
2.  加入下列到 COM 對應 (**BEGIN_COM_MAP...END_COM_MAP**):  
  
    |如果您實作|將新增到 COM 對應|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  在命令中，加入下列屬性集對應 (**BEGIN_PROPSET_MAP...END_PROPSET_MAP**):  
  
    |如果您實作|加入至屬性集對應|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  在屬性集對應，您也應該包括下列設定的所有下面所列：  
  
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
  
     您可以找到這些巨集呼叫中使用的屬性識別碼和值為 atldb 中尋找的值 （如果為 atldb 不同於線上文件，為 atldb 取代文件）。  
  
    > [!NOTE]
    >  許多**VARIANT_FALSE**和`VARIANT_TRUE`設定所需的 OLE DB 範本; 它們可以是讀/寫，但 OLE DB 樣板只能支援一個值，指出 OLE DB 規格。  
  
     **如果您實作 IRowsetChangeImpl**  
  
     如果您實作`IRowsetChangeImpl`，您必須在您的提供者上設定下列屬性。 這些屬性主要是用來要求介面透過**icommandproperties:: Setproperties**。  
  
    -   `DBPROP_IRowsetChange`： 設定就會自動設定**DBPROP_IRowsetChange**。  
  
    -   `DBPROP_UPDATABILITY`： 指定支援的方法位元遮罩`IRowsetChange`: `SetData`， `DeleteRows`，或`InsertRow`。  
  
    -   `DBPROP_CHANGEINSERTEDROWS`： 取用者可以呼叫**irowsetchange:: Deleterows**或`SetData`新插入的資料列。  
  
    -   `DBPROP_IMMOBILEROWS`： 資料列集不會重新排列插入或更新資料列。  
  
     **如果您實作 IRowsetUpdateImpl**  
  
     如果您實作`IRowsetUpdateImpl`，您必須設定下列屬性上您的提供者，除了要設定的所有屬性`IRowsetChangeImpl`先前所列：  
  
    -   `DBPROP_IRowsetUpdate`.  
  
    -   `DBPROP_OWNINSERT`： 必須是 READ_ONLY 和 VARIANT_TRUE。  
  
    -   `DBPROP_OWNUPDATEDELETE`： 必須是 READ_ONLY 和 VARIANT_TRUE。  
  
    -   `DBPROP_OTHERINSERT`： 必須是 READ_ONLY 和 VARIANT_TRUE。  
  
    -   `DBPROP_OTHERUPDATEDELETE`： 必須是 READ_ONLY 和 VARIANT_TRUE。  
  
    -   `DBPROP_REMOVEDELETED`： 必須是 READ_ONLY 和 VARIANT_TRUE。  
  
    -   `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  如果您支援通知，您可能還有其他屬性。請參閱節`IRowsetNotifyCP`這個清單。  
  
     比方說的內容的設定方式，請參閱這個屬性中設定地圖**CUpdateCommand** （在 Rowset.h) 中[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)。  
  
##  <a name="vchowwritingtothedatasource"></a> 寫入資料來源  
 若要從資料來源讀取，呼叫**Execute**函式。 若要寫入的資料來源，請呼叫`FlushData`函式。 （一般的意義而言，排清方法來儲存您對資料表或索引到磁碟的修改）。  
  
```  
FlushData(HROW, HACCESSOR);  
```  
  
 資料列控制代碼 (*HROW*) 和存取子控制代碼 (*HACCESSOR*) 引數可讓您指定要寫入的區域。 一般而言，您一次寫入單一資料欄位。  
  
 `FlushData`方法會將資料寫入所在它一開始儲存的格式。 如果您不會覆寫這個函式，您的提供者將會正確運作，但變更並不會清除資料存放區。  
  
### <a name="when-to-flush"></a>排清的時機  
 提供者範本呼叫`FlushData`每當資料以供需要寫到資料存放區，這通常 （但並非一定） 會發生下列函式呼叫的結果：  
  
-   **IRowsetChange::DeleteRows**  
  
-   **IRowsetChange::SetData**  
  
-   **IRowsetChange::InsertRows** （如果沒有要插入資料列中的新資料）  
  
-   **IRowsetUpdate::Update**  
  
### <a name="how-it-works"></a>它的運作方式  
 取用者會呼叫需要排清 (例如**更新**) 和這個呼叫會傳遞給提供者，一律會進行下列作業：  
  
-   呼叫`SetDBStatus`即表示已繫結的狀態值 (請參閱*OLE DB 程式設計人員參考*，第 6 章*資料組件： 狀態*)。  
  
-   檢查資料行旗標。  
  
-   呼叫 `IsUpdateAllowed`。  
  
 這三個步驟會協助提供安全性。 接著，提供者會呼叫`FlushData`。  
  
### <a name="how-to-implement-flushdata"></a>如何實作 FlushData  
 若要實作`FlushData`，您需要考慮的幾個問題：  
  
-   確定資料存放區可處理變更。  
  
-   處理**NULL**值。  
  
-   處理預設值。  
  
 若要實作您自己`FlushData`方法，您需要：  
  
-   移至您的資料列集類別。  
  
-   在資料列集類別會將宣告：  
  
```  
HRESULT FlushData(HROW, HACCESSOR)  
{  
    // Insert your implementation here and return an HRESULT.  
}  
```  
  
-   提供的實作`FlushData`。  
  
 良好實作`FlushData`儲存只有資料列和實際更新的資料行。 您可以使用*HROW*和*HACCESSOR*參數，以判斷目前的資料列和資料行的儲存最佳化。  
  
 通常，最大的挑戰使用原生資料存放區。 可能的話，請嘗試：  
  
-   保留寫入資料存放區越簡單越好的方法。  
  
-   處理**NULL** values （選擇性但建議使用）。  
  
-   處理預設值 （選擇性但建議使用）。  
  
 最佳做法是讓實際的指定的值的資料存放區中**NULL**和預設值。 最好是如果可以推斷這項資料。 如果沒有，建議您在不允許**NULL**和預設值。  
  
 下列範例會示範如何`FlushData`中實作`RUpdateRowset`類別[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)範例 （在範例程式碼，請參閱 Rowset.h）：  
  
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
 針對您的提供者來處理的變更，您必須先以確定您的資料存放區 （例如文字檔案或視訊檔案中） 有可讓您對它進行變更的功能。 如果不存在，您應該在個別從提供者專案中建立該程式碼。  
  
### <a name="handling-null-data"></a>處理 NULL 的資料  
 很可能會傳送使用者**NULL**資料。 當您撰寫**NULL**值到資料來源中的欄位，可以是潛在的問題。 假設訂單處理應用程式可接受值縣市和郵遞區號。它可以接受或這兩個值，但無法兩者皆否，因為在此情況下將無法傳遞。 因此，您必須限制的特定組合**NULL**對您的應用程式有意義的欄位中的值。  
  
 提供者開發人員，您必須考慮如何儲存該資料、 如何從資料存放區讀取資料以及如何將它指定給使用者。 具體來說，您必須考慮如何變更資料來源中的資料列集資料的資料狀態 (例如，DataStatus = **NULL**)。 您決定何值時取用者存取欄位，包含要傳回**NULL**值。  
  
 查看中的程式碼[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)範例; 它會說明如何處理提供者**NULL**資料。 在 UpdatePV，提供者會儲存**NULL**資料存放區中寫入字串"NULL"的資料。 當讀取**NULL**資料從資料存放區，則會看見該字串，並清空緩衝區中，建立**NULL**字串。 它也會有的覆寫`IRowsetImpl::GetDBStatus`中傳回的**DBSTATUS_S_ISNULL**如果該資料值是空的。  
  
### <a name="marking-nullable-columns"></a>標示可為 Null 的資料行  
 如果您也可以實作結構描述資料列集 (請參閱`IDBSchemaRowsetImpl`)，您的實作應該指定在**DBSCHEMA_COLUMNS**資料列集 (通常標示為您的提供者中**C***xxx***SchemaColSchemaRowset**) 的資料行是可為 null。  
  
 您也需要指定可為 null 的所有資料行包含**DBCOLUMNFLAGS_ISNULLABLE**的版本中的值`GetColumnInfo`。  
  
 在 OLE DB 範本實作中，如果您無法標記為可為 null，資料行的提供者會假設他們都必須包含值，而且不允許取用者將它傳送 null 值。  
  
 下列範例會示範如何**CommonGetColInfo**函式中實作**CUpdateCommand** （請參閱 UpProvRS.cpp） UpdatePV 中。 請注意如何的資料行具有這**DBCOLUMNFLAGS_ISNULLABLE**可為 null 的資料行。  
  
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
 如同**NULL**資料，您必須將變更預設值。  
  
 預設值是`FlushData`和**Execute**會傳回`S_OK`。 因此，如果您不會覆寫這個函式，會顯示變更才會成功 (`S_OK`將傳回)，但不是會傳輸至資料存放區。  
  
 在[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)範例 （在 Rowset.h)`SetDBStatus`方法會處理預設值，如下所示：  
  
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
  
### <a name="column-flags"></a>資料行旗標  
 如果您在您的資料行上支援預設值，您需要設定它使用中繼資料中的 **\<***提供者類別***> SchemaRowset**類別。 設定*m_bColumnHasDefault* = `VARIANT_TRUE`。  
  
 您也可以設定資料行旗標，會使用指定的責任**DBCOLUMNFLAGS**列舉型別。 資料行旗標描述資料行的特性。  
  
 例如，在`CUpdateSessionColSchemaRowset`類別[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) （在 Session.h)，第一個資料行設定這種方式：  
  
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
  
 此程式碼指定在其他方面，資料行支援預設值是 0，可寫入的與資料行中的所有資料都具有相同的長度。 如果您想要具有可變長度的資料行中的資料，您就不會設定這個旗標。  
  
## <a name="see-also"></a>另請參閱  
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)