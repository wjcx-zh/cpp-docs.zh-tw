---
title: "提供者書籤支援 | Microsoft Docs"
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
  - "書籤, OLE DB"
  - "IRowsetLocate 類別"
  - "IRowsetLocate 類別, 提供者書籤支援"
  - "OLE DB 提供者樣板, 書籤"
  - "OLE DB 提供者, 書籤支援"
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 提供者書籤支援
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題的範例會將 `IRowsetLocate` 介面加入至 `CMyProviderRowset` 類別。  在大多數的情況下，一開始都會先將介面加入至現有的 COM 物件。  您可以接著從消費者樣板中加入更多呼叫來進行測試。  這個範例示範如何：  
  
-   加入介面至提供者。  
  
-   動態地決定要傳回至消費者的資料行。  
  
-   加入書籤支援。  
  
 `IRowsetLocate` 介面繼承自 `IRowset` 介面。  若要加入 `IRowsetLocate` 介面，請讓 `CMyProviderRowset` 繼承自 [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)。  
  
 加入 `IRowsetLocate` 介面和大多數的介面有點不同。  為了讓 VTABLE 貼齊，OLE DB 提供者樣板擁有一樣板參數來處理衍生的介面。  下列程式碼說明了新的繼承 \(Inheritance\) 清單：  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
// CMyProviderRowset  
class CMyProviderRowset : public CRowsetImpl< CMyProviderRowset,   
      CTextData, CMyProviderCommand, CAtlArray<CTextData>,   
      CSimpleRow,   
          IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate> >  
```  
  
 第四、第五和第六個參數已全部加入。  這個範例使用第四和第五個參數的預設值，但將 `IRowsetLocateImpl` 指定為第六個參數。  `IRowsetLocateImpl` 是需使用兩個樣板參數的 OLE DB 樣板類別：這些會將 `IRowsetLocate` 介面連結至 `CMyProviderRowset` 類別。  若要加入更多介面，您可略過此步驟，並移到下個步驟。  只有 `IRowsetLocate` 和 `IRowsetScroll` 介面需要以此方式來處理。  
  
 接著您需要通知 `CMyProviderRowset` 為 `IRowsetLocate` 介面呼叫 `QueryInterface`。  將 `COM_INTERFACE_ENTRY(IRowsetLocate)` 這一行程式碼加入至對應。  `CMyProviderRowset` 的介面對應應該如下列程式碼所示：  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
typedef CRowsetImpl< CMyProviderRowset, CTextData, CMyProviderCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate> > _RowsetBaseClass;  
  
BEGIN_COM_MAP(CMyProviderRowset)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 您也需要將對應攔截至 `CRowsetImpl` 類別。  加入 COM\_INTERFACE\_ENTRY\_CHAIN 巨集來在 `CRowsetImpl` 對應中攔截。  同時，建立名為 `RowsetBaseClass` 的 typedef，裡面包含了繼承資訊。  這個 typedef 可隨意設定，也可省略。  
  
 最後，請處理 **IColumnsInfo::GetColumnsInfo** 呼叫。  您通常可使用 PROVIDER\_COLUMN\_ENTRY 巨集來作這個動作。  然而，消費者可能會想要使用書籤。  您必須根據消費者是否要求書籤而定，加以變更提供者傳回的資料行。  
  
 若要處理 **IColumnsInfo::GetColumnsInfo** 呼叫，請刪除 `CTextData` 類別中的 **PROVIDER\_COLUMN** 對應。  PROVIDER\_COLUMN\_MAP 巨集定義了一個 `GetColumnInfo` 函式。  您需要定義自己的 `GetColumnInfo` 函式。  函式宣告應該如下：  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.H  
  
class CTextData  
{  
   ...  
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!  
   static ATLCOLUMNINFO* GetColumnInfo(CMyProviderRowset* pThis,   
        ULONG* pcCols);  
   static ATLCOLUMNINFO* GetColumnInfo(CMyProviderCommand* pThis,   
        ULONG* pcCols);  
...  
};  
```  
  
 接著實作 MyProviderRS.cpp 檔內的 `GetColumnInfo` 函式，如下所示：  
  
```  
////////////////////////////////////////////////////////////////////  
// MyProviderRS.cpp  
  
template <class TInterface>  
ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols)  
{  
   static ATLCOLUMNINFO _rgColumns[5];  
   ULONG ulCols = 0;  
  
   CComQIPtr<TInterface> spProps = pPropsUnk;  
  
   CDBPropIDSet set(DBPROPSET_ROWSET);  
   set.AddPropertyID(DBPROP_BOOKMARKS);  
   DBPROPSET* pPropSet = NULL;  
   ULONG ulPropSet = 0;  
   HRESULT hr;  
  
   if (spProps)  
      hr = spProps->GetProperties(1, &set, &ulPropSet, &pPropSet);  
  
   // Check the property flag for bookmarks, if it is set, set the   
// zero ordinal entry in the column map with the bookmark   
// information.  
  
   if (pPropSet)  
   {  
      CComVariant var = pPropSet->rgProperties[0].vValue;  
      CoTaskMemFree(pPropSet->rgProperties);  
      CoTaskMemFree(pPropSet);  
  
      if ((SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE)))  
      {  
         ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,   
                     sizeof(DWORD), DBTYPE_BYTES,  
            0, 0, GUID_NULL, CAgentMan, dwBookmark,         
                        DBCOLUMNFLAGS_ISBOOKMARK)  
         ulCols++;  
      }  
  
   }  
  
   // Next set the other columns up.  
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field1"), 1, 16, DBTYPE_STR,   
          0xFF, 0xFF, GUID_NULL, CTextData, szField1)  
   ulCols++;  
   ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Field2"), 2, 16, DBTYPE_STR,  
       0xFF, 0xFF, GUID_NULL, CTextData, szField2)  
   ulCols++;  
  
   if (pcCols != NULL)  
      *pcCols = ulCols;  
  
   return _rgColumns;  
}  
  
ATLCOLUMNINFO* CTextData::GetColumnInfo(CMyProviderCommand* pThis,   
     ULONG* pcCols)  
{  
   return CommonGetColInfo<ICommandProperties>(pThis->GetUnknown(),  
        pcCols);  
}  
  
ATLCOLUMNINFO* CAgentMan::GetColumnInfo(RUpdateRowset* pThis, ULONG* pcCols)  
{  
   return CommonGetColInfo<IRowsetInfo>(pThis->GetUnknown(), pcCols);  
}  
```  
  
 `GetColumnInfo` 會先檢查名為 **DBPROP\_IRowsetLocate** 的屬性是否已設定。  OLE DB 對每個選擇性介面有不同於資料列集物件的屬性。  如果消費者想要使用這些選擇性介面之一，它會將屬性設為 True。  然後提供者可以檢查這個屬性，並根據它來採取特殊動作。  
  
 您可以在實作中，使用命令物件指標來取得屬性。  `pThis` 指標代表資料列集或命令類別。  因為您在這裡使用了樣板，所以必須將它以 `void` 指標傳遞，否則程式碼將無法編譯。  
  
 指定靜態陣列來包含資料行資訊。  如果消費者不要書籤資料行，將浪費掉陣列中的一個項目。  您可動態配置此陣列，但您需要確定能適當地終結它。  此範例將定義並使用巨集 ADD\_COLUMN\_ENTRY 和 ADD\_COLUMN\_ENTRY\_EX 來將資訊插入陣列內。  您可將巨集加入至 MyProviderRS.H 檔內，如下列的程式碼所示：  
  
```  
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
#define ADD_COLUMN_ENTRY(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member) \  
   _rgColumns[ulCols].pwszName = (LPOLESTR)name; \  
   _rgColumns[ulCols].pTypeInfo = (ITypeInfo*)NULL; \  
   _rgColumns[ulCols].iOrdinal = (ULONG)ordinal; \  
   _rgColumns[ulCols].dwFlags = 0; \  
   _rgColumns[ulCols].ulColumnSize = (ULONG)colSize; \  
   _rgColumns[ulCols].wType = (DBTYPE)type; \  
   _rgColumns[ulCols].bPrecision = (BYTE)precision; \  
   _rgColumns[ulCols].bScale = (BYTE)scale; \  
   _rgColumns[ulCols].cbOffset = offsetof(dataClass, member);  
  
#define ADD_COLUMN_ENTRY_EX(ulCols, name, ordinal, colSize, type, precision, scale, guid, dataClass, member, flags) \  
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
  
 若要測試消費者內的程式碼，您需要對 `OnRun` 處理常式做一些變更。  針對函式所做的第一個變更是加入程式碼，以便將屬性加入屬性集 \(Property Set\) 內。  程式碼會將 **DBPROP\_IRowsetLocate** 屬性設為 True，提供者接著會被告知您需要書籤資料行的訊息。  `OnRun` 處理常式程式碼應如下所示：  
  
```  
//////////////////////////////////////////////////////////////////////  
// TestProv Consumer Application in TestProvDlg.cpp  
  
void CTestProvDlg::OnRun()   
{  
   CCommand<CAccessor<CProvider> > table;  
   CDataSource source;  
   CSession   session;  
  
   if (source.Open("MyProvider.MyProvider.1", NULL, NULL, NULL,   
          NULL) != S_OK)  
      return;  
  
   if (session.Open(source) != S_OK)  
      return;  
  
   CDBPropSet propset(DBPROPSET_ROWSET);  
   propset.AddProperty(DBPROP_IRowsetLocate, true);  
   if (table.Open(session, _T("c:\\public\\testprf2\\myData.txt"),   
          &propset) != S_OK)  
      return;  
  
   CBookmark<4> tempBookmark;  
   ULONG ulCount=0;  
   while (table.MoveNext() == S_OK)  
   {  
  
      DBCOMPARE compare;  
      if (ulCount == 2)  
         tempBookmark = table.bookmark;  
      HRESULT hr = table.Compare(table.dwBookmark, table.dwBookmark,  
                 &compare);  
      if (FAILED(hr))  
         ATLTRACE(_T("Compare failed: 0x%X\n"), hr);  
      else  
         _ASSERTE(compare == DBCOMPARE_EQ);  
  
      m_ctlString1.AddString(table.szField1);  
      m_ctlString2.AddString(table.szField2);  
      ulCount++;  
   }  
  
   table.MoveToBookmark(tempBookmark);  
   m_ctlString1.AddString(table.szField1);  
   m_ctlString2.AddString(table.szField2);  
}  
```  
  
 While 迴圈包含進行呼叫 `IRowsetLocate` 介面的 `Compare` 方法之程式碼。  您的程式碼永遠會通過，因為您是在比較完全相同的書籤。  同時，在暫存變數中儲存一個書籤，以便 While 迴圈完成後可使用它來呼叫消費者樣板內的 `MoveToBookmark` 函式。  `MoveToBookmark` 函式會呼叫 `IRowsetLocate` 內的 `GetRowsAt` 方法。  
  
 您也需要更新消費者的使用者資料錄。  在類別中加入一個項目，來處理書籤，和 **COLUMN\_MAP** 的項目：  
  
```  
///////////////////////////////////////////////////////////////////////  
// TestProvDlg.cpp  
  
class CProvider  
{  
// Attributes  
public:  
   CBookmark<4>    bookmark;  // Add this line  
   char   szCommand[16];  
   char   szText[256];  
  
   // Binding Maps  
BEGIN_ACCESSOR_MAP(CProvider, 1)  
   BEGIN_ACCESSOR(0, true)   // auto accessor  
      BOOKMARK_ENTRY(bookmark)  // Add this line  
      COLUMN_ENTRY(1, szField1)  
      COLUMN_ENTRY(2, szField2)  
   END_ACCESSOR()  
END_ACCESSOR_MAP()  
};  
```  
  
 當您更新程式碼以後，應該就可以建置 \(Build\) 和執行使用 `IRowsetLocate` 介面的提供者。  
  
## 請參閱  
 [進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)