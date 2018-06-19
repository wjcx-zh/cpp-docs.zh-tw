---
title: 書籤的提供者支援 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 139956fcd7d9244c486ad37797696817c7080fbd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112504"
---
# <a name="provider-support-for-bookmarks"></a>提供者書籤支援
本主題中的此範例會將`IRowsetLocate`介面`CMyProviderRowset`類別。 幾乎在所有情況下，在您開始將介面加入至現有的 COM 物件。 然後就可以測試它，藉由新增更多呼叫從取用者範本。 此範例示範如何：  
  
-   將介面加入至提供者。  
  
-   以動態方式判斷要傳回給取用者的資料行。  
  
-   加入書籤支援。  
  
 `IRowsetLocate` 介面繼承自 `IRowset` 介面。 若要加入`IRowsetLocate`介面、 繼承`CMyProviderRowset`從[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)。  
  
 加入`IRowsetLocate`介面是稍微不同於大部分介面。 若要讓 Vtable 排列，OLE DB 提供者樣板有樣板參數，來處理衍生的介面。 下列程式碼會顯示新的繼承清單：  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
// CMyProviderRowset  
class CMyProviderRowset : public CRowsetImpl< CMyProviderRowset,   
      CTextData, CMyProviderCommand, CAtlArray<CTextData>,   
      CSimpleRow,   
          IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate>>  
```  
  
 第四個、 第五和第六個都會加入參數。 這個範例會使用預設值的第四個和第五個參數但指定`IRowsetLocateImpl`做為第六個參數。 `IRowsetLocateImpl` 會採用兩個範本參數的 OLE DB 範本類別： 這些連結`IRowsetLocate`介面`CMyProviderRowset`類別。 若要新增更多介面，您可以略過此步驟，再移至下一個。 只有`IRowsetLocate`和`IRowsetScroll`介面需要以這種方式處理。  
  
 然後，您需要告訴`CMyProviderRowset`呼叫`QueryInterface`如`IRowsetLocate`介面。 將行加入`COM_INTERFACE_ENTRY(IRowsetLocate)`對應。 介面對應`CMyProviderRowset`應該會出現，如下列程式碼所示：  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
  
typedef CRowsetImpl< CMyProviderRowset, CTextData, CMyProviderCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CMyProviderRowset, IRowsetLocate>> _RowsetBaseClass;  
  
BEGIN_COM_MAP(CMyProviderRowset)  
   COM_INTERFACE_ENTRY(IRowsetLocate)  
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)  
END_COM_MAP()  
```  
  
 您也必須連結到對應`CRowsetImpl`類別。 增益集 COM_INTERFACE_ENTRY_CHAIN 巨集，才能攔截 (hook) 中`CRowsetImpl`對應。 此外，建立稱為 typedef`RowsetBaseClass`繼承資訊號所組成。 此 typedef 是任意的您可以忽略。  
  
 最後，處理**icolumnsinfo:: Getcolumnsinfo**呼叫。 您通常會使用 PROVIDER_COLUMN_ENTRY 巨集來執行這項操作。 不過，取用者可能會想要使用書籤。 您必須是能夠變更提供者會傳回根據取用者是否要求書籤的資料行。  
  
 若要處理**icolumnsinfo:: Getcolumnsinfo**呼叫時，刪除**PROVIDER_COLUMN**對應`CTextData`類別。 PROVIDER_COLUMN_MAP 巨集定義的函式`GetColumnInfo`。 您需要定義您自己`GetColumnInfo`函式。 函式宣告看起來應該像這樣：  
  
```cpp
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
  
 然後，實作`GetColumnInfo`函式在 MyProviderRS.cpp 檔案，如下所示：  
  
```cpp
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
  
 `GetColumnInfo` 若要查看是否有呼叫屬性會先檢查**DBPROP_IRowsetLocate**設定。 OLE DB 有每個資料列集物件選擇性介面屬性。 如果取用者想要使用其中一種選擇性介面，它會將屬性設定為 true。 提供者可以檢查這個屬性，並採取它為基礎的特殊動作。  
  
 在您實作中，您可以取得的屬性所使用的命令物件的指標。 `pThis`指標代表的資料列集或命令類別。 因為您在此使用範本，您必須傳遞為`void`指標或程式碼無法編譯。  
  
 指定要包含的資料行資訊的靜態陣列。 如果取用者不想書籤資料行，將會作廢陣列中的項目。 您可以動態地配置此陣列中，但您必須確定正確地終結。 此範例中定義，並將資訊插入陣列使用 ADD_COLUMN_ENTRY 和 ADD_COLUMN_ENTRY_EX 巨集。 您可以加入巨集 MyProviderRS.H 檔案，如下列程式碼所示：  
  
```cpp
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
  
 取用者測試程式碼，您需要進行一些變更以`OnRun`處理常式。 此函式的第一個變更是，您會加入程式碼，以將屬性加入至屬性集。 程式碼集**DBPROP_IRowsetLocate**屬性設定為 true，因此通知的提供者的書籤資料行。 `OnRun`處理常式程式碼應該會出現，如下所示：  
  
```cpp
//////////////////////////////////////////////////////////////////////  
// TestProv Consumer Application in TestProvDlg.cpp  
  
void CTestProvDlg::OnRun()   
{  
   CCommand<CAccessor<CProvider>> table;  
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
  
 While 迴圈包含程式碼呼叫`Compare`方法中的`IRowsetLocate`介面。 因為您要比較完全相同的書籤，應一律傳遞您的程式碼。 此外，儲存在暫存變數一個書籤，以便您可以使用它在一段時間之後迴圈完成呼叫`MoveToBookmark`消費者範本中的函式。 `MoveToBookmark`函式呼叫`GetRowsAt`方法中的`IRowsetLocate`。  
  
 您也需要更新使用者記錄取用者。 若要處理的書籤和中的項目類別中加入一個項目**COLUMN_MAP**:  
  
```cpp
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
  
 更新程式碼之後，您應該能夠建置並執行的提供者`IRowsetLocate`介面。  
  
## <a name="see-also"></a>另請參閱  
 [進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)