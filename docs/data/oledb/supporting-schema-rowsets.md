---
title: "支援結構描述資料列集 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b981af06f48834eef59103b872b8b07e75cd0065
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="supporting-schema-rowsets"></a>支援結構描述資料列集
結構描述資料列集可讓取用者取得的資料存放區的相關資訊，而不需要知道其基礎結構描述。 例如，資料存放區可能會不有組織成使用者定義階層，所以會有任何方式可以讀取它確保知識以外的結構描述的資料表。 （另一個範例，請注意，Visual c + + 精靈會產生取用者的存取子使用結構描述資料列）。若要讓取用者，若要這樣做，提供者的工作階段物件會公開方法上[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)介面。 在 Visual c + + 應用程式，您可以使用[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)類別來實作**IDBSchemaRowset**。  
  
 `IDBSchemaRowsetImpl`支援下列方法：  
  
-   [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md)檢查限制針對結構描述資料列集的有效性。  
  
-   [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)實作 COM 物件建立者函式的範本參數所指定的物件。  
  
-   [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)指定您在特定結構描述資料列集支援的限制。  
  
-   [Idbschemarowset:: Getrowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)傳回結構描述資料列集 （繼承自介面）。  
  
-   [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)會傳回一份結構描述資料列可供存取`IDBSchemaRowsetImpl::GetRowset`（繼承自介面）。  
  
## <a name="atl-ole-db-provider-wizard-support"></a>ATL OLE DB 提供者精靈支援  
 ATL OLE DB 提供者精靈工作階段標頭檔中建立結構描述的三個類別：  
  
-   **C** *ShortName* **SessionTRSchemaRowset**  
  
-   **C** *ShortName* **SessionColSchemaRowset**  
  
-   **C** *ShortName* **SessionPTSchemaRowset**  
  
 這些類別回應取用者要求的結構描述資訊;請注意，OLE DB 規格需要這些三個結構描述資料列集必須支援：  
  
-   **C** *ShortName* **SessionTRSchemaRowset**處理資料表資訊的要求 (`DBSCHEMA_TABLES`結構描述資料列)。  
  
-   **C** *ShortName* **SessionColSchemaRowset**會處理要求資料行資訊 ( **DBSCHEMA_COLUMNS**結構描述資料列)。 精靈會提供範例實作，這些類別，傳回 DOS 提供者的結構描述資訊。  
  
-   **C** *ShortName* **SessionPTSchemaRowset**處理提供者類型的結構描述資訊的要求 ( **DBSCHEMA_PROVIDER_TYPES**結構描述資料列）。 精靈所提供的預設實作會傳回`S_OK`。  
  
 您可以自訂這些類別來處理您的提供者適用的結構描述資訊：  
  
-   在**C***ShortName***SessionTRSchemaRowset**，您必須先填寫目錄、 資料表和描述欄位 (**trData.m_szType**，**trData.m_szTable**，和**trData.m_szDesc**)。 精靈產生的範例會使用只有一個資料列 （資料表）。 其他提供者可能會傳回一個以上的資料表。  
  
-   在**C***ShortName***SessionColSchemaRowset**，傳遞做為資料表的名稱**DBID**。  
  
## <a name="setting-restrictions"></a>設定限制  
 結構描述資料列集支援中的重要概念設定限制，您不要使用`SetRestrictions`。 限制允許消費者只擷取相符的資料列 (例如在資料表 "MyTable" 中尋找所有資料行)。 限制是選擇性的，在不支援任何限制的情況下 (預設)，一律會傳回所有資料。 如需支援限制的提供者的範例，請參閱[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)範例。  
  
## <a name="setting-up-the-schema-map"></a>設定結構描述對應  
 設定在 UpdatePV Session.h 這種結構描述對應：  
  
```  
BEGIN_SCHEMA_MAP(CUpdateSession)  
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)  
END_SCHEMA_MAP()  
```  
  
 若要支援**IDBSchemaRowset**，您必須支援`DBSCHEMA_TABLES`， **DBSCHEMA_COLUMNS**，和**DBSCHEMA_PROVIDER_TYPES**。 您可以自行斟酌加入額外的結構描述資料列集。  
  
 宣告具有的結構描述資料列集類別`Execute`方法，例如`CUpdateSessionTRSchemaRowset`UpdatePV 中：  
  
```  
class CUpdateSessionTRSchemaRowset :   
    public CSchemaRowsetImpl < CUpdateSessionTRSchemaRowset,   
                              CTABLESRow, CUpdateSession >  
...  
// Execute looks like this; what pointers does the consumer use?  
    HRESULT Execute(DBROWCOUNT* pcRowsAffected,   
                    ULONG cRestrictions, const VARIANT* rgRestrictions)  
```  
  
 請注意，`CUpdateSession`繼承自`IDBSchemaRowsetImpl`，所以其處理方法的所有限制。 使用`CSchemaRowsetImpl`，宣告三個子類別 （在上述的結構描述對應中列出）： `CUpdateSessionTRSchemaRowset`， `CUpdateSessionColSchemaRowset`，和`CUpdateSessionPTSchemaRowset`。 這些子類別的每個都有`Execute`處理個別組的限制 （搜尋條件） 的方法。 每個`Execute`方法比較的值`cRestrictions`和`rgRestrictions`參數。 請參閱中的這些參數的描述[SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)。  
  
 了解哪種限制對應至特定結構描述資料列集的詳細資訊，請參閱結構描述資料列集 Guid 的資料表中[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)中*OLE DB 程式設計人員參考*中Windows SDK。  
  
 例如，如果您支援**TABLE_NAME**限制`DBSCHEMA_TABLES`，您會執行下列動作：  
  
 首先，查閱`DBSCHEMA_TABLES`並查看它是否支援四個的限制 （依順序）。  
  
|結構描述資料列集限制|限制值|  
|-------------------------------|-----------------------|  
|**TABLE_CATALOG 排列**|0x1 (二進位 1)|  
|**TABLE_SCHEMA**|0x2 (二進位 10)|  
|**TABLE_NAME**|0x4 (二進位 100)|  
|**TABLE_TYPE**|0x8 (二進位 1000)|  
  
 接下來，請注意，有一個位元的每個限制。 因為您想要支援**TABLE_NAME** ，您會傳回在 0x4`rgRestrictions`項目。 如果您支援**table_catalog 排列**和**TABLE_NAME**，您將會傳回 0x5 (二進位 101)。  
  
 根據預設，實作會傳回的 0 （不支援任何限制），針對任何要求。 UpdatePV 是提供者支援限制的範例。  
  
### <a name="example"></a>範例  
 此程式碼取自[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)範例。 UpdatePv 支援三個必要的結構描述資料列集： `DBSCHEMA_TABLES`， **DBSCHEMA_COLUMNS**，和**DBSCHEMA_PROVIDER_TYPES**。 如何在您的提供者中實作結構描述支援的範例，為這個主題會引導您透過實作**DBSCHEMA_TABLE**資料列集。  
  
> [!NOTE]
>  從此處; 所列的範例程式碼可能會與不同您應該將範例程式碼視為最新的版本。  
  
 加入結構描述支援的第一個步驟是決定您要支援的限制。 若要判斷哪些限制可供您的結構描述資料列，查看 OLE DB 規格定義的**IDBSchemaRowset**。 下列主要定義，您會看到包含結構描述資料列集名稱、 的限制數目，以及限制資料行的資料表。 選取您想要支援，並記下的數目限制以及限制資料行的結構描述資料列集。 例如，`DBSCHEMA_TABLES`支援四個的限制 (**table_catalog 排列**， **TABLE_SCHEMA**， **TABLE_NAME**，和**TABLE_TYPE**):  
  
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
  
 位元表示每個限制資料行。 如果您想要支援的限制 （也就是說，您可以查詢它），該位元設為 1。 如果您不想支援的限制，請該位元設定為零。 從上述程式碼行，支援 UpdatePV **TABLE_NAME**和**TABLE_TYPE**限制`DBSCHEMA_TABLES`資料列集。 這些是 （位元遮罩 100） 的第三和第四個 （位元遮罩 1000年） 限制。 因此，UpdatePv 之位元遮罩是 1100年 （或 0x0C）：  
  
```  
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))  
    rgRestrictions[l] = 0x0C;  
```  
  
 下列`Execute`函式是類似於一般的資料列集。 您有三個引數： `pcRowsAffected`， `cRestrictions`，和`rgRestrictions`。 `pcRowsAffected`變數是輸出參數，提供者可以在結構描述資料列中傳回的資料列計數。 `cRestrictions`參數是輸入的參數，其中包含由取用者傳遞給提供者的限制數目。 `rgRestrictions`參數為陣列**VARIANT**包含限制值的值。  
  
```  
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,   
                const VARIANT* rgRestrictions)  
```  
  
 `cRestrictions`變數根據結構描述資料列，無論是否提供者會支援這些限制的總數。 由於 UpdatePv 支援兩個的限制 （第三和第四個），這段程式碼只會尋找`cRestrictions`值大於或等於三。  
  
 值**TABLE_NAME**限制儲存在`rgRestrictions[2]`（同樣地，在以零為起始的陣列中的第三個限制為 2）。 您需要檢查的限制不是`VT_EMPTY`實際上支援它。 請注意， **VT_NULL**不等於`VT_EMPTY`。 **VT_NULL**指定有效的限制值。  
  
 UpdatePv 定義的資料表名稱是文字檔案的完整的路徑名稱。 擷取限制值，然後嘗試開啟檔案，以確保檔案實際存在。 如果檔案不存在，傳回`S_OK`。 這看起來似乎有點回溯，而程式碼的確會通知取用者所指定的名稱所不支援的資料表。 `S_OK`傳回表示該程式碼正確執行。  
  
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
  
 支援的第四個的限制 (**TABLE_TYPE**) 類似於第三個的限制。 請檢查值不是`VT_EMPTY`。 這項限制只會傳回資料表類型**資料表**。 若要判斷正確值`DBSCHEMA_TABLES`，查詢中的 < 附錄 B *OLE DB 程式設計人員參考*中**資料表**資料列集 > 一節。  
  
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
  
 這是實際建立的資料列集的資料列項目。 變數`trData`對應至**CTABLESRow**，OLE DB 提供者範本中定義的結構。 **CTABLESRow**對應至**資料表**附錄 B 中的資料列集定義的 OLE DB 規格。 您只能有一個資料列加入，因為您一次只能支援一個資料表。  
  
```  
// Bring over the data:  
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);  
wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);  
wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());  
```  
  
 只有三個資料行都將 UpdatePV: **TABLE_NAME**， **TABLE_TYPE**，和**描述**。 您應該記下的資料行，您可以為其傳回的詳細資訊，因為只有在實作時，需要這項資訊`GetDBStatus`:  
  
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
  
 `GetDBStatus`函式是非常重要的結構描述資料列的正確運作。 因為您不會傳回每個資料行中的資料**資料表**資料列集，您必須指定哪些資料行傳回的資料，並不這麼做。  
  
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
  
 因為您`Execute`函式會傳回資料**TABLE_NAME**， **TABLE_TYPE**，和**描述**欄位從**資料表**資料列集，您可以查看附錄 B 的 OLE DB 規格中，並判斷 （由，從上方算起） 它們的序數 3、 4 和 6。 對於每個資料行，傳回**DBSTATUS_S_OK**。 所有其他資料行，傳回**DBSTATUS_S_ISNULL**。 請務必傳回此狀態，因為取用者可能不了解您所傳回的值是**NULL**或其他項目。 同樣地，請注意， **NULL**不相當於空白。  
  
 如需 OLE DB 結構描述資料列集介面的詳細資訊，請參閱[IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) OLE DB 程式設計人員參考中的介面。  
  
 如需有關如何使用取用者資訊**IDBSchemaRowset**方法，請參閱[取得中繼資料與結構描述資料列集](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)。  
  
 如需支援結構描述資料列集提供者的範例，請參閱[UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f)範例。  
  
## <a name="see-also"></a>請參閱  
 [進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)