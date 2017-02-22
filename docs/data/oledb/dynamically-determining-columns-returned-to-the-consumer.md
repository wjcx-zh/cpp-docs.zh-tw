---
title: "動態決定傳回給消費者的資料行 | Microsoft Docs"
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
  - "書籤 [C++], 動態決定資料行"
  - "動態決定資料行 [C++]"
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 動態決定傳回給消費者的資料行
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

PROVIDER\_COLUMN\_ENTRY 巨集一般會處理 **IColumnsInfo::GetColumnsInfo** 呼叫。  但是，因為消費者可能選擇使用書籤，提供者依據消費者是否要求書籤而定，必須要能變更資料行。  
  
 若要處理 **IColumnsInfo::GetColumnsInfo** 呼叫，請從 MyProviderRS.h 內的 `CAgentMan` 使用者資料錄中，刪除定義 `GetColumnInfo` 函式的 PROVIDER\_COLUMN\_MAP，並以您自己的 `GetColumnInfo` 函式定義來取代它：  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
class CAgentMan  
{  
public:  
   DWORD dwBookmark;  
   TCHAR szCommand[256];  
   TCHAR szText[256];  
   TCHAR szCommand2[256];  
   TCHAR szText2[256];  
  
   static ATLCOLUMNINFO* GetColumnInfo(void* pThis, ULONG* pcCols);  
   bool operator==(const CAgentMan& am)  
   {  
      return (lstrcmpi(szCommand, am.szCommand) == 0);  
   }  
  
};  
```  
  
 接下來，實作 MyProviderRS.cpp 內的 `GetColumnInfo` 函式，如以下的程式碼所示。  
  
 `GetColumnInfo` 會先檢查 OLE DB 屬性 **DBPROP\_BOOKMARKS**  是否已設定。  若要取得該屬性，`GetColumnInfo` 會使用資料列集物件的指標 \(`pRowset`\)。  `pThis` 指標代表建立該資料列集的類別，也就是儲存屬性對應的類別。  `GetColumnInfo` 會將 `pThis` 指標的型別轉換成 `RMyProviderRowset` 指標。  
  
 若要檢查 **DBPROP\_BOOKMARKS** 屬性，`GetColumnInfo` 會使用 `IRowsetInfo` 介面，而您可呼叫 `pRowset` 介面上的 `QueryInterface` 以取得此介面。  您也可以改用 ATL [CComQIPtr](../../atl/reference/ccomqiptr-class.md) 方法來作取代。  
  
```  
////////////////////////////////////////////////////////////////////  
// MyProviderRS.cpp  
ATLCOLUMNINFO* CAgentMan::GetColumnInfo(void* pThis, ULONG* pcCols)  
{  
   static ATLCOLUMNINFO _rgColumns[5];  
   ULONG ulCols = 0;  
  
   // Check the property flag for bookmarks; if it is set, set the zero   
   // ordinal entry in the column map with the bookmark information.  
   CAgentRowset* pRowset = (CAgentRowset*) pThis;  
   CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;  
  
   CDBPropIDSet set(DBPROPSET_ROWSET);  
   set.AddPropertyID(DBPROP_BOOKMARKS);  
   DBPROPSET* pPropSet = NULL;  
   ULONG ulPropSet = 0;  
   HRESULT hr;  
  
   if (spRowsetProps)  
      hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);  
  
   if (pPropSet)  
   {  
      CComVariant var = pPropSet->rgProperties[0].vValue;  
      CoTaskMemFree(pPropSet->rgProperties);  
      CoTaskMemFree(pPropSet);  
  
      if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))  
      {  
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),   
         DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,   
         DBCOLUMNFLAGS_ISBOOKMARK)  
         ulCols++;  
      }  
   }  
  
   // Next, set the other columns up.  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command"), 1, 256, DBTYPE_STR, 0xFF, 0xFF,   
      GUID_NULL, CAgentMan, szCommand)  
   ulCols++;  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text"), 2, 256, DBTYPE_STR, 0xFF, 0xFF,   
      GUID_NULL, CAgentMan, szText)  
   ulCols++;  
  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Command2"), 3, 256, DBTYPE_STR, 0xFF, 0xFF,   
      GUID_NULL, CAgentMan, szCommand2)  
   ulCols++;  
   ADD_COLUMN_ENTRY(ulCols, OLESTR("Text2"), 4, 256, DBTYPE_STR, 0xFF, 0xFF,   
      GUID_NULL, CAgentMan, szText2)  
   ulCols++;  
  
   if (pcCols != NULL)  
      *pcCols = ulCols;  
  
   return _rgColumns;  
}  
```  
  
 此範例使用靜態陣列以包含資料行資訊。  如果消費者不要書籤資料行，陣列中的一個項目將不會使用。  若要處理該資訊，可建立兩個陣列巨集，ADD\_COLUMN\_ENTRY 和 ADD\_COLUMN\_ENTRY\_EX。  如果您指定一個書籤資料行，ADD\_COLUMN\_ENTRY\_EX 需要採用額外的參數 `flags`。  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
#define ADD_COLUMN_ENTRY(ulCols, name, ordinal, colSize, type, precision,   
scale, guid, dataClass, member) \  
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \  
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \  
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \  
   _rgColumns[ulCols].dwFlags = 0; \  
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \  
   _rgColumns[ulCols].wType = (DBTYPE)type; \  
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \  
   _rgColumns[ulCols].bScale = (BYTE)scale; \  
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member);  
  
#define ADD_COLUMN_ENTRY_EX(ulCols, name, ordinal, colSize, type,   
precision, scale, guid, dataClass, member, flags) \  
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \  
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \  
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \  
   _rgColumns[ulCols].dwFlags = flags; \  
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \  
   _rgColumns[ulCols].wType = (DBTYPE)type; \  
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \  
   _rgColumns[ulCols].bScale = (BYTE)scale; \  
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member); \  
   memset(&(_rgColumns[ulCols].columnid), 0, sizeof(DBID)); \  
   _rgColumns[ulCols].columnid.uName.pwszName = (LPOLESTR)name;  
```  
  
 在 `GetColumnInfo` 函式中，書籤巨集的使用方式如下所示：  
  
```  
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),  
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,   
   DBCOLUMNFLAGS_ISBOOKMARK)  
```  
  
 您現在可編譯和執行增強的提供者。  若要測試提供者 \(Provider\)，請依[實作簡單消費者](../../data/oledb/implementing-a-simple-consumer.md)所述修改測試消費者。  同時執行測試消費者和提供者。  當您按一下 \[測試消費者\] 對話方塊中的 \[執行\] 按鈕時，會驗證測試消費者可從提供者內擷取正確的字串。  
  
## 請參閱  
 [增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)