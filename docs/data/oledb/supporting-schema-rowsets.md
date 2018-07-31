---
title: 支援結構描述資料列集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- schema rowsets
- OLE DB consumer templates, schema rowsets
- OLE DB providers, schema rowsets
- OLE DB, schema rowsets
ms.assetid: 71c5e14b-6e33-4502-a2d9-a1dc6d6e9ba0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7c0468a9df7b79e79b3e20074c43fc1621058d71
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339701"
---
# <a name="supporting-schema-rowsets"></a>支援結構描述資料列集
結構描述資料列集可讓取用者，而不需要知道其基礎結構描述取得的資料存放區的相關資訊。 例如，資料存放區可能不有組織成使用者定義階層，所以會有任何方式可以確保在閱讀本文的知道除了結構描述的資料表。 （另一個範例，請注意，Visual c + + 精靈會使用結構描述資料列，在產生取用者的存取子）。若要讓取用者若要這樣做，提供者的工作階段物件會公開方法上[IDBSchemaRowset](https://msdn.microsoft.com/library/ms713686.aspx)介面。 在 Visual c + + 應用程式，您可以使用[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)類別來實作`IDBSchemaRowset`。  
  
 `IDBSchemaRowsetImpl` 支援下列方法：  
  
-   [CheckRestrictions](../../data/oledb/idbschemarowsetimpl-checkrestrictions.md)檢查限制針對結構描述資料列集的有效性。  
  
-   [CreateSchemaRowset](../../data/oledb/idbschemarowsetimpl-createschemarowset.md)實作 COM 物件建立者函式的範本參數所指定的物件。  
  
-   [SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)指定您在特定結構描述資料列集支援的限制。  
  
-   [Idbschemarowset:: Getrowset](../../data/oledb/idbschemarowsetimpl-getrowset.md)傳回 （繼承自介面） 的結構描述資料列集。  
  
-   [GetSchemas](../../data/oledb/idbschemarowsetimpl-getschemas.md)會傳回一份結構描述資料列集可供存取`IDBSchemaRowsetImpl::GetRowset`（繼承自介面）。  
  
## <a name="atl-ole-db-provider-wizard-support"></a>ATL OLE DB 提供者精靈支援  
 [ATL OLE DB 提供者精靈] 建立工作階段標頭檔中的三個結構描述類別：  
  
-   **C** *ShortName* **SessionTRSchemaRowset**  
  
-   **C** *ShortName* **SessionColSchemaRowset**  
  
-   **C** *ShortName* **SessionPTSchemaRowset**  
  
 這些類別結構描述資訊; 的取用者要求回應請注意，OLE DB 規格需要這些三個結構描述資料列集必須支援：  
  
-   **C** *ShortName* **SessionTRSchemaRowset**處理資料表資訊的要求 (`DBSCHEMA_TABLES`結構描述資料列)。  
  
-   **C** *ShortName* **SessionColSchemaRowset**處理的資料行資訊的要求 (`DBSCHEMA_COLUMNS`結構描述資料列)。 精靈會提供這些類別，傳回 DOS 提供者的結構描述資訊的範例實作。  
  
-   **C** *ShortName* **SessionPTSchemaRowset**處理提供者類型的結構描述資訊的要求 (`DBSCHEMA_PROVIDER_TYPES`結構描述資料列)。 精靈所提供的預設實作會傳回`S_OK`。  
  
 您可以自訂這些類別來處理結構描述資訊適用於您的提供者：  
  
-   在  **C***ShortName***SessionTRSchemaRowset**，您必須填寫的目錄、 資料表名稱和描述欄位 (`trData.m_szType`， `trData.m_szTable`，和`trData.m_szDesc`)。 在精靈產生的範例會使用只有一個資料列 （資料表）。 其他提供者可能會傳回一個以上的資料表。  
  
-   在  **C***ShortName***SessionColSchemaRowset**，做為資料表名稱傳遞給`DBID`。  
  
## <a name="setting-restrictions"></a>設定限制  
 結構描述資料列集支援中的重要概念設定限制，您使用執行`SetRestrictions`。 限制允許消費者只擷取相符的資料列 (例如在資料表 "MyTable" 中尋找所有資料行)。 限制是選擇性的，在不支援任何限制的情況下 (預設)，一律會傳回所有資料。 如需支援限制的提供者的範例，請參閱 < [UpdatePV](http://msdn.microsoft.com/c8bed873-223c-4a7d-af55-f90138c6f38f)範例。  
  
## <a name="setting-up-the-schema-map"></a>設定結構描述對應  
 設定在 UpdatePV Session.h 這類結構描述對應：  
  
```  
BEGIN_SCHEMA_MAP(CUpdateSession)  
    SCHEMA_ENTRY(DBSCHEMA_TABLES, CUpdateSessionTRSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_COLUMNS, CUpdateSessionColSchemaRowset)  
    SCHEMA_ENTRY(DBSCHEMA_PROVIDER_TYPES, CUpdateSessionPTSchemaRowset)  
END_SCHEMA_MAP()  
```  
  
 若要支援`IDBSchemaRowset`，您必須支援`DBSCHEMA_TABLES`， `DBSCHEMA_COLUMNS`，和`DBSCHEMA_PROVIDER_TYPES`。 您可以自行新增額外的結構描述資料列集。  
  
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
  
 請注意，`CUpdateSession`繼承自`IDBSchemaRowsetImpl`，所以它沒有處理常式方法的所有限制。 使用`CSchemaRowsetImpl`，宣告三個 （列於上述的結構描述對應） 的子類別： `CUpdateSessionTRSchemaRowset`， `CUpdateSessionColSchemaRowset`，和`CUpdateSessionPTSchemaRowset`。 這些子類別的每個都有`Execute`處理個別組的限制 （搜尋條件） 的方法。 每個`Execute`方法會比較的值`cRestrictions`和`rgRestrictions`參數。 請參閱中的這些參數的說明[SetRestrictions](../../data/oledb/idbschemarowsetimpl-setrestrictions.md)。  
  
 了解哪種限制對應至特定的結構描述資料列集的詳細資訊，請參閱結構描述資料列集 Guid 的資料表中[IDBSchemaRowset](https://msdn.microsoft.com/library/ms713686.aspx)中*OLE DB 程式設計人員參考*中Windows SDK。  
  
 例如，如果您支援**TABLE_NAME**限制`DBSCHEMA_TABLES`，您會執行下列動作：  
  
 首先，查閱`DBSCHEMA_TABLES`並查看它支援四個的限制 （依順序）。  
  
|結構描述資料列集限制|限制值|  
|-------------------------------|-----------------------|  
|**TABLE_CATALOG 排列**|0x1 (二進位 1)|  
|**TABLE_SCHEMA**|0x2 (二進位 10)|  
|**TABLE_NAME**|0x4 (二進位 100)|  
|**TABLE_TYPE**|0x8 (二進位 1000)|  
  
 接下來，請注意，有一個位元的每個限制。 因為您想要支援**TABLE_NAME** ，您將會傳回在 0x4`rgRestrictions`項目。 如果您支援**table_catalog 排列**並**TABLE_NAME**，您將會傳回 0x5 (二進位 101)。  
  
 根據預設，實作會傳回的 0 （不支援任何限制） 的任何要求。 UpdatePV 是提供者支援限制的範例。  
  
### <a name="example"></a>範例  
 此程式碼取自[UpdatePV](http://msdn.microsoft.com/c8bed873-223c-4a7d-af55-f90138c6f38f)範例。 UpdatePv 支援三個必要的結構描述資料列集： `DBSCHEMA_TABLES`， `DBSCHEMA_COLUMNS`，和`DBSCHEMA_PROVIDER_TYPES`。 如何在您的提供者中實作結構描述支援的範例，本主題會引導您完成實作`DBSCHEMA_TABLE`資料列集。  
  
> [!NOTE]
>  範例程式碼可能會與不同功能為此處所列;您應該將範例程式碼做為較新版本。  
  
 新增結構描述支援的第一個步驟是決定您要支援的限制。 若要判斷哪些限制可供您的結構描述資料列，查看 OLE DB 規格定義的`IDBSchemaRowset`。 下列主要定義，您會看到包含結構描述資料列集名稱、 數目限制，以及限制資料行的資料表。 選取您想要支援，並記下的限制和限制資料行數目的結構描述資料列集。 例如，`DBSCHEMA_TABLES`支援四個的限制 (**table_catalog 排列**， **TABLE_SCHEMA**， **TABLE_NAME**，並**TABLE_TYPE**):  
  
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
  
 位元代表每個限制資料行。 如果您想要支援的限制 （也就是您可以查詢它），該位元設為 1。 如果您不想支援的限制，請該位元設定為零。 上述程式碼的行，從支援 UpdatePV **TABLE_NAME**並**TABLE_TYPE**限制`DBSCHEMA_TABLES`資料列集。 這些是 （位元遮罩 100） 的第三和第四個 （位元遮罩 1000年） 限制。 因此，UpdatePv 位元遮罩是 1100年 （或 0x0C）：  
  
```  
if (InlineIsEqualGUID(rguidSchema[l], DBSCHEMA_TABLES))  
    rgRestrictions[l] = 0x0C;  
```  
  
 下列`Execute`函式是類似於一般的資料列集。 您有三個引數： *pcRowsAffected*， *cRestrictions*，並*rgRestrictions*。 *PcRowsAffected*變數是一個 output 參數，提供者，可以在結構描述資料列中傳回的資料列計數。 *CRestrictions*參數是輸入的參數包含的提供者取用者所傳送的限制數目。 *RgRestrictions*參數是陣列`VARIANT`包含限制值的值。  
  
```  
HRESULT Execute(DBROWCOUNT* pcRowsAffected, ULONG cRestrictions,   
                const VARIANT* rgRestrictions)  
```  
  
 `cRestrictions`變數為基礎的結構描述資料列集，不論提供者是否支援這些限制的總數。 由於 UpdatePv 支援兩個的限制 （第三和第四個），此程式碼只會尋找`cRestrictions`值大於或等於 3。  
  
 值**TABLE_NAME**限制儲存在`rgRestrictions[2]`（同樣地，以零為起始的陣列中的第三個限制為 2）。 您需要檢查限制不是 VT_EMPTY 實際上支援它。 請注意 VT_NULL 不等於設為 VT_EMPTY。 VT_NULL 指定有效的限制值。  
  
 UpdatePv 定義的資料表名稱是文字檔案的完整的路徑名稱。 擷取限制值，並嘗試開啟檔案，以確保檔案確實存在。 如果檔案不存在，會傳回 S_OK。 這看起來似乎有點回溯，但其實程式碼的確會通知取用者會依指定名稱所不支援的資料表。 傳回 S_OK 表示正確執行的程式碼。  
  
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
  
 支援的第四個的限制 (**TABLE_TYPE**) 類似於第三個的限制。 請檢查值不是為 VT_EMPTY。 這項限制只會傳回資料表類型中，**資料表**。 若要判斷有效的值，如`DBSCHEMA_TABLES`，查看附錄 B *OLE DB 程式設計人員參考*中**資料表**資料列集一節。  
  
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
  
 這是實際建立的資料列集的資料列項目。 變數`trData`對應至`CTABLESRow`，OLE DB 提供者範本中定義的結構。 `CTABLESRow` 對應至**資料表**OLE DB 規格的附錄 B 中的資料列集定義。 您只需要一個資料列加入，因為您一次只能支援一個資料表。  
  
```cpp  
// Bring over the data:  
wcspy_s(trData.m_szType, OLESTR("TABLE"), 5);  

wcspy_s(trData.m_szDesc, OLESTR("The Directory Table"), 19);  

wcsncpy_s(trData.m_szTable, T2OLE(szFile), _TRUNCATE());  
```  
  
 UpdatePV 設定只有三個資料行： **TABLE_NAME**， **TABLE_TYPE**，並**描述**。 您應該記下傳回之資訊，資料行，因為當您實作時，您會需要這項資訊`GetDBStatus`:  
  
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
  
 `GetDBStatus`函式是很重要的結構描述資料列的正確運作。 因為您不會傳回每個資料行中的資料**資料表**資料列集，您必須指定哪些資料行傳回的資料，並不這麼做。  
  
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
  
 因為您`Execute`函式會傳回的資料**TABLE_NAME**， **TABLE_TYPE**，和**描述**欄位從**資料表**資料列集，您可以查詢的 OLE DB 規格的附錄 B，它們是序數 3、 4 和 6 （藉由向下，從上方算起） 所判斷。 對於每個資料行，會傳回 DBSTATUS_S_OK。 對於所有其他資料行，會傳回 DBSTATUS_S_ISNULL。 務必以傳回此狀態，因為取用者可能不了解您傳回的值是 NULL 或其他項目。 同樣地，請注意，NULL 不等於空。  
  
 如需有關 OLE DB 結構描述資料列集介面的詳細資訊，請參閱[IDBSchemaRowset](../../data/oledb/idbschemarowsetimpl-class.md) OLE DB 程式設計人員參考中的介面。  
  
 如需如何使用取用者`IDBSchemaRowset`方法，請參閱[取得中繼資料與結構描述資料列集](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)。  
  
 如需支援結構描述資料列集提供者的範例，請參閱 < [UpdatePV](http://msdn.microsoft.com/c8bed873-223c-4a7d-af55-f90138c6f38f)範例。  
  
## <a name="see-also"></a>另請參閱  
 [進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)