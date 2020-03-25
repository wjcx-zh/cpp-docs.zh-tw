---
title: 提供者書籤支援
ms.date: 11/04/2016
helpviewer_keywords:
- IRowsetLocate class, provider support for bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- IRowsetLocate class
- OLE DB providers, bookmark support
ms.assetid: 1b14ccff-4f76-462e-96ab-1aada815c377
ms.openlocfilehash: e8ea949653c7e62f39ab9d1b181c419cf51fe3cb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209829"
---
# <a name="provider-support-for-bookmarks"></a>提供者書籤支援

本主題中的範例會將 `IRowsetLocate` 介面新增至 `CCustomRowset` 類別。 在大部分的情況下，您一開始會先將介面新增至現有的 COM 物件。 然後，您可以從取用者範本新增更多呼叫來進行測試。 此範例示範如何：

- 將介面加入至提供者。

- 以動態方式判斷要傳回給取用者的資料行。

- 新增書簽支援。

`IRowsetLocate` 介面繼承自 `IRowset` 介面。 若要新增 `IRowsetLocate` 介面，請從[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)繼承 `CCustomRowset`。

新增 `IRowsetLocate` 介面與大部分的介面有點不同。 為了讓 Vtable 行，OLE DB 提供者範本具有樣板參數，可處理衍生的介面。 下列程式碼會顯示新的繼承清單：

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

// CCustomRowset
class CCustomRowset : public CRowsetImpl< CCustomRowset,
      CTextData, CCustomCommand, CAtlArray<CTextData>,
      CSimpleRow,
          IRowsetLocateImpl<CCustomRowset, IRowsetLocate>>
```

第四、第五和第六個參數都會加入。 這個範例會使用第四個和第五個參數的預設值，但指定 `IRowsetLocateImpl` 做為第六個參數。 `IRowsetLocateImpl` 是採用兩個樣板參數的 OLE DB 範本類別：這些會將 `IRowsetLocate` 介面連結至 `CCustomRowset` 類別。 若要新增大部分的介面，您可以略過此步驟並移至下一個。 只有 `IRowsetLocate` 和 `IRowsetScroll` 介面需要以這種方式處理。

接著，您必須告訴 `CCustomRowset` 為 `IRowsetLocate` 介面呼叫 `QueryInterface`。 將行 `COM_INTERFACE_ENTRY(IRowsetLocate)` 新增至地圖。 `CCustomRowset` 的介面對應應該會如下列程式碼所示：

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

typedef CRowsetImpl< CCustomRowset, CTextData, CCustomCommand, CAtlArray<CTextData>, CSimpleRow, IRowsetLocateImpl<CCustomRowset, IRowsetLocate>> _RowsetBaseClass;

BEGIN_COM_MAP(CCustomRowset)
   COM_INTERFACE_ENTRY(IRowsetLocate)
   COM_INTERFACE_ENTRY_CHAIN(_RowsetBaseClass)
END_COM_MAP()
```

您也必須將對應連結到 `CRowsetImpl` 類別。 加入 COM_INTERFACE_ENTRY_CHAIN 宏以在 `CRowsetImpl` 對應中連結。 此外，建立稱為 `RowsetBaseClass` 的 typedef，其中包含繼承資訊。 此 typedef 是任意的，而且可以忽略。

最後，處理 `IColumnsInfo::GetColumnsInfo` 呼叫。 您通常會使用 PROVIDER_COLUMN_ENTRY 宏來執行這項操作。 不過，取用者可能會想要使用書簽。 您必須能夠根據取用者是否要求書簽，來變更提供者所傳回的資料行。

若要處理 `IColumnsInfo::GetColumnsInfo` 呼叫，請刪除 `CTextData` 類別中的 PROVIDER_COLUMN 對應。 PROVIDER_COLUMN_MAP 宏會定義函式 `GetColumnInfo`。 定義您自己的 `GetColumnInfo` 函數。 函式宣告看起來應該像這樣：

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H

class CTextData
{
   ...
     // NOTE: Be sure you removed the PROVIDER_COLUMN_MAP!
   static ATLCOLUMNINFO* GetColumnInfo(CCustomRowset* pThis,
        ULONG* pcCols);
   static ATLCOLUMNINFO* GetColumnInfo(CCustomCommand* pThis,
        ULONG* pcCols);
...
};
```

然後，在*自訂*RS .cpp 檔案中執行 `GetColumnInfo` 函式，如下所示：

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp

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

ATLCOLUMNINFO* CTextData::GetColumnInfo(CCustomCommand* pThis,
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

`GetColumnInfo` 先檢查是否已設定稱為 `DBPROP_IRowsetLocate` 的屬性。 OLE DB 具有資料列集物件之每個選擇性介面的屬性。 如果取用者想要使用其中一個選擇性介面，它會將屬性設定為 true。 然後，提供者可以檢查此屬性，並根據它採取特殊動作。

在您的執行中，您會使用命令物件的指標來取得屬性。 `pThis` 指標代表資料列集或命令類別。 因為您在這裡使用範本，所以您必須將此傳入做為**void**指標，否則程式碼不會編譯。

指定用來保存資料行資訊的靜態陣列。 如果取用者不想要書簽資料行，就會浪費陣列中的專案。 您可以動態配置此陣列，但您必須確定它已正確地摧毀。 這個範例會定義和使用宏 ADD_COLUMN_ENTRY，並 ADD_COLUMN_ENTRY_EX 將資訊插入陣列中。 您可以將宏新增至*自訂*RS。H 檔案，如下列程式碼所示：

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.h

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

若要測試取用者中的程式碼，您需要對 `OnRun` 處理常式進行一些變更。 函式的第一次變更是您加入程式碼，以將屬性新增至屬性集。 程式碼會將 `DBPROP_IRowsetLocate` 屬性設定為 true，藉此告知您想要書簽資料行的提供者。 `OnRun` 的處理常式程式碼應如下所示：

```cpp
//////////////////////////////////////////////////////////////////////
// TestProv Consumer Application in TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession   session;

   if (source.Open("Custom.Custom.1", NULL, NULL, NULL,
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

**While**迴圈包含用來在 `IRowsetLocate` 介面中呼叫 `Compare` 方法的程式碼。 您所擁有的程式碼應該一律通過，因為您比較的是完全相同的書簽。 此外，在暫存變數中儲存一個書簽，以便在**while**迴圈完成以呼叫取用者範本中的 `MoveToBookmark` 函式之後使用它。 `MoveToBookmark` 函數會在 `IRowsetLocate`中呼叫 `GetRowsAt` 方法。

您也需要更新取用者中的使用者記錄。 在類別中新增專案，以處理書簽和 COLUMN_MAP 中的專案：

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

當您更新程式碼時，您應該能夠使用 `IRowsetLocate` 介面來建立和執行提供者。

## <a name="see-also"></a>另請參閱

[進階的提供者技術](../../data/oledb/advanced-provider-techniques.md)
