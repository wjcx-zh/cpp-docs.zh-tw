---
title: "支援結構描述資料列集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE DB 消費者樣板, 結構描述資料列集"
  - "OLE DB 提供者, 結構描述資料列集"
  - "OLE DB, 結構描述資料列集"
  - "結構描述資料列集"
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 支援結構描述資料列集
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

結構描述 \(Schema\) 資料列集可讓消費者取得資料存放區資訊，而不需知道其基礎結構或是結構描述。  例如，資料存放區可能將資料表組織成使用者定義的架構，因此只有讀取它，才能確定結構描述知識 \(請注意，在另一個範例中 Visual C\+\+ 精靈會使用結構描述資料列集來產生消費者的存取子\)。為了讓消費者達成這個目的，提供者的工作階段物件會在 [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) 介面顯露方法。  在 Visual C\+\+ 應用程式中，您可使用 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) 類別來實作 **IDBSchemaRowset**。  
  
 `IDBSchemaRowsetImpl` 支援下列方法：  
  
-   [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md) 會根據結構描述資料列集來檢查限制的有效性。  
  
-   [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md) 會為樣板參數指定的物件實作一個 COM 物件建立者函式。  
  
-   [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md) 指定您在特定的結構描述資料列集上支援哪些限制。  
  
-   [IDBSchemaRowset::GetRowset](../../data/oledb/idbschemarowsetimpl-getrowset.md) 傳回結構描述資料列集 \(繼承自介面\)。  
  
-   [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md) 將傳回可由 `IDBSchemaRowsetImpl::GetRowset` \(繼承自介面\) 存取的結構描述資料列集清單。  
  
## ATL OLE DB 提供者精靈支援  
 ATL OLE DB 提供者精靈會在工作階段標頭檔 \(Header File\) 內建立三個架構類別：  
  
-   **C** *ShortName* **SessionTRSchemaRowset**  
  
-   **C** *ShortName* **SessionColSchemaRowset**  
  
-   **C** *ShortName* **SessionPTSchemaRowset**  
  
 這些類別會回應結構描述資訊的消費者要求；請注意，OLE DB 規格要求支援這三個結構描述資料列集：  
  
-   **C** *ShortName* **SessionTRSchemaRowset** 會處理資料表資訊的要求 \(`DBSCHEMA_TABLES` 結構描述資料列集\)。  
  
-   **C** *ShortName* **SessionColSchemaRowset** 會處理資料行資訊的要求 \(**DBSCHEMA\_COLUMNS** 結構描述資料列集\)。  精靈提供會傳回 DOS 提供者結構描述資訊的類別之範例實作。  
  
-   **C** *ShortName* **SessionPTSchemaRowset** 會處理有關提供者類型的結構描述資訊的要求 \(**DBSCHEMA\_PROVIDER\_TYPES** 結構描述資料列集\)。  精靈提供的預設實作會傳回 `S_OK`。  
  
 您可根據提供者，適切地自訂這些類別來處理結構描述資訊：  
  
-   在 **C***ShortName***SessionTRSchemaRowset** 內，您必須填寫資料庫目錄 \(Catalog\)、資料表和描述欄位 \(**trData.m\_szType**、**trData.m\_szTable** 和 **trData.m\_szDesc**\)。  精靈產生的範例只會使用一個資料列 \(資料表\)。  其他提供者可能會傳回一個以上的資料表。  
  
-   在 **C***ShortName***SessionColSchemaRowset** 中，您可將資料表的名稱以 **DBID** 傳遞。  
  
## 設定限制  
 結構描述資料列集中的重要概念為設定限制，您可透過 `SetRestrictions` 來達到這個目的。  限制可讓消費者只擷取符合的資料列 \(例如，在 "MyTable" 資料表內尋找所有的資料行\)。  限制是選擇性的，在不支援任何限制的狀況下 \(預設值\)，會一直傳回所有資料。  如需的確可支援限制的提供者之範例，請參閱 [UpdatePV](http://msdn.microsoft.com/zh-tw/c8bed873-223c-4a7d-af55-f90138c6f38f) 範例。  
  
## 設定結構描述對應  
 依照 UpdatePV 的 Session.h 的這段程式碼來設定一個結構描述對應：  
  
```  
BEGIN_SCHEMA_MAP(CUpdateSession)  
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)  
END_SCHEMA_MAP()  
```  
  
 若要支援 **IDBSchemaRowset**，您必須支援 `DBSCHEMA_TABLES`、**DBSCHEMA\_COLUMNS** 和 **DBSCHEMA\_PROVIDER\_TYPES**。  您可以自行決定是否加入其他的結構描述資料列集。  
  
 使用類似於 UpdatePV 內的 `CUpdateSessionTRSchemaRowset` 之 `Execute` 方法，宣告結構描述資料列集類別：  
  
```  
class CUpdateSessionTRSchemaRowset :   
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,   
                              CTABLESRow, CUpdateSession >  
...  
// Execute looks like this; what pointers does the consumer use?  
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,   
                    ULONG cRestrictions, const VARIANT* rgRestrictions)  
```  
  
 請注意，`CUpdateSession` 繼承自 `IDBSchemaRowsetImpl`，因此它具有所有的限制處理方法。  使用 `CSchemaRowsetImpl` 來宣告三個子系類別 \(列於上述結構描述對應\)：`CUpdateSessionTRSchemaRowset`、`CUpdateSessionColSchemaRowset` 和 `CUpdateSessionPTSchemaRowset`。  這些子系類別每個都有可處理個別一組限制 \(搜尋條件\) 的 `Execute` 方法。  每種 `Execute` 方法都會比較 `cRestrictions` 和 `rgRestrictions` 的參數值。  如需這些參數說明的詳細資訊，請參閱 [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)。  
  
 如需哪些限制對應至特定結構描述資料列集的詳細資訊，請參閱 [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) \(在 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 的《OLE DB 程式設計人員參考》中\) 內的結構描述資料列集 GUID 表格。  
  
 例如，如果您支援 `DBSCHEMA_TABLES` 的 **TABLE\_NAME** 限制，便需執行下列步驟：  
  
 首先，請查詢 `DBSCHEMA_TABLES`，並檢視它所支援的四個限制 \(依序\)。  
  
|結構描述資料列集限制|限制值|  
|----------------|---------|  
|**TABLE\_CATALOG**|0x1 \(二進位 1\)|  
|**TABLE\_SCHEMA**|0x2 \(二進位 10\)|  
|**TABLE\_NAME**|0x4 \(二進位 100\)|  
|**TABLE\_TYPE**|0x8 \(二進位 1000\)|  
  
 接下來，請注意每個限制都對應一位元。  由於您只要支援 **TABLE\_NAME**，您便可以用 `rgRestrictions` 元件傳回 0x4。  如果您支援 **TABLE\_CATALOG** 和 **TABLE\_NAME**，便可傳回 0x5 \(二進位 101\)。  
  
 預設情況下，實作將為任何要求傳回 0 \(不支援任何限制\)。  UpdatePV 是支援限制的提供者範例。  
  
### 範例  
 這段程式碼摘自 [UpdatePV](http://msdn.microsoft.com/zh-tw/c8bed873-223c-4a7d-af55-f90138c6f38f) 範例。  UpdatePv 支援三個必要的結構描述資料列集：`DBSCHEMA_TABLES`、**DBSCHEMA\_COLUMNS** 和 **DBSCHEMA\_PROVIDER\_TYPES**。  做為在提供者內實作結構描述支援的範例，這個主題會帶您實作 **DBSCHEMA\_TABLE** 資料列集。  
  
> [!NOTE]
>  範例程式碼可能會與此處所列的有所不同，您應該視範例程式碼為最新的版本。  
  
 加入結構描述支援的第一步是決定要支援哪些限制。  若要決定哪些限制可用於結構描述資料列集，請在 OLE DB 規格內檢視 **IDBSchemaRowset** 的定義。  在主要定義之後，您會看到包含結構描述資料列集名稱、限制個數和限制資料行的資料表。  選取想要支援的結構描述資料列集，並記下限制個數和限制資料行。  例如，`DBSCHEMA_TABLES` 可支援四個限制 \(**TABLE\_CATALOG**、**TABLE\_SCHEMA**、**TABLE\_NAME** 和 **TABLE\_TYPE**\)：  
  
```  
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
  
 一個位元代表每個限制資料行。  如果想要支援某個限制 \(也就是使用限制來查詢\)，請將該位元設定成 1。  如果不想支援某個限制，則將該位元設定成零。  由上述程式碼可知，UpdatePV 會在 `DBSCHEMA_TABLES` 資料列集 \(Rowset\) 中支援 **TABLE\_NAME** 和 **TABLE\_TYPE** 限制。  這些是第三個 \(位元遮罩 100\) 和第四個 \(位元遮罩 1000\) 限制。  因此，UpdatePv 的位元遮罩為 1100 \(或 0x0C\)：  
  
```  
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))  
    rgRestrictions[l] = 0x0C;  
```  
  
 下列的 `Execute` 函式與一般資料列集函式相似。  您擁有三個引數：`pcRowsAffected`、`cRestrictions` 和 `rgRestrictions`。  `pcRowsAffected` 變數是輸出參數，提供者可透過它傳回結構描述資料列集內的資料列數。  `cRestrictions` 參數是輸入參數，裡面包含了消費者傳給提供者的限制個數。  `rgRestrictions` 參數為包含限制值的 **VARIANT** 值陣列。  
  
```  
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,   
                const VARIANT* rgRestrictions)  
```  
  
 `cRestrictions` 變數是以結構描述資料列集的限制總數為基礎，無論提供者是否支援它們。  因為 UpdatePv 支援兩個限制 \(第三個和第四個\)，所以程式碼只會尋找大於或等於三的 `cRestrictions` 值。  
  
 **TABLE\_NAME** 限制的值會儲存於 `rgRestrictions[2]` \(在以零起始陣列中的第三個限制會為 2\)。  您需要檢查該限制是否為 `VT_EMPTY` 以確實支援它。  請注意，**VT\_NULL** 並不等於 `VT_EMPTY`。  **VT\_NULL** 會指定一個有效的限制值。  
  
 資料表名稱的 UpdatePv 定義為文字檔的完整路徑名稱。  擷取限制值，然後嘗試開啟檔案，以確定檔案確實存在。  如果檔案不存在，就傳回 `S_OK`。  這看起來似乎有點顛倒步驟，其實程式碼的確會通知消費者該指定名稱並不支援的資料表。  傳回的 `S_OK` 表示該程式碼已正確執行。  
  
```  
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
  
 支援第四個限制 \(**TABLE\_TYPE**\) 類似於第三個限制。  請檢查該數值並非 `VT_EMPTY`。  此限制只會傳回資料表類型，**TABLE**。  若要決定 `DBSCHEMA_TABLES` 的有效值，請查閱《OLE DB 程式設計人員》附錄 B 的 **TABLES** 資料列集章節。  
  
```  
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
  
 此處是實際您可為資料列集建立資料列項目的地方。  `trData` 變數會對應至 **CTABLESRow**，這是定義於 OLE DB 提供者樣板的結構。  **CTABLESRow** 會對應至 OLE DB 規格＜附錄 B＞的 **TABLES** 資料列集定義。  您只能加入一個資料列，因為您一次只支援一個資料表。  
  
```  
// Bring over the data:  
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);  
wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);  
wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());  
```  
  
 UpdatePV 只能設定三個資料行：**TABLE\_NAME**、**TABLE\_TYPE** 和 **DESCRIPTION**。  您應該記下傳回資訊的資料行，因為當您實作 `GetDBStatus` 時會需要這個資訊：  
  
```  
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
  
 `GetDBStatus` 函式對於結構描述資料列集的正確操作很重要。  因為不針對 **TABLES** 資料列集的每個資料行傳回資料，所以需要指定哪些資料行要傳回資料以及哪些資料行不要。  
  
```  
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
  
 由於您的 `Execute` 函式會從 **TABLES** 資料列集傳回 **TABLE\_NAME**、**TABLE\_TYPE** 和 **DESCRIPTION** 欄位的資料，您可檢視 OLE DB 規格內的＜附錄 B＞，並決定 \(透過由上而下地計數\) 它們為序數 3、4 和 6。  對於這些資料行的每一個都要傳回 **DBSTATUS\_S\_OK**。  其他所有的資料行則傳回 **DBSTATUS\_S\_ISNULL**。  傳回這個狀態相當重要，因為消費者可能不了解您傳回的值為 **NULL** 或其他資料。  再次提醒，請注意 **NULL** 並不等於空白值。  
  
 如需 OLE DB 結構描述資料列集介面的詳細資訊，請參閱《OLE DB 程式設計人員》的 [IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) 介面。  
  
 如需消費者如何使用 **IDBSchemaRowset** 的詳細資訊，請參閱[以結構描述資料列集取得中繼資料](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)。  
  
 如需支援結構描述資料列集的提供者範例，請參閱 [UpdatePV](http://msdn.microsoft.com/zh-tw/c8bed873-223c-4a7d-af55-f90138c6f38f) 範例。  
  
## 請參閱  
 [進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)