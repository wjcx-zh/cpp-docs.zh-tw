---
title: 動態決定資料行傳回給消費者 |Microsoft Docs
ms.custom: ''
ms.date: 10/26/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- bookmarks [C++], dynamically determining columns
- dynamically determining columns [C++]
ms.assetid: 58522b7a-894e-4b7d-a605-f80e900a7f5f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a2149c50f4dc8880e20bff2401adf0db46ad6588
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216496"
---
# <a name="dynamically-determining-columns-returned-to-the-consumer"></a>動態決定傳回給消費者的資料行

PROVIDER_COLUMN_ENTRY 巨集通常處理`IColumnsInfo::GetColumnsInfo`呼叫。 不過，取用者可能會選擇使用書籤，因為提供者必須要能夠變更傳回根據取用者是否要求書籤的資料行。

若要處理`IColumnsInfo::GetColumnsInfo`呼叫時，刪除 PROVIDER_COLUMN_MAP，其定義的函式`GetColumnInfo`，從`CAgentMan`使用者記錄中 CustomRS.h，並取代為您自己的定義`GetColumnInfo`函式：

```cpp
////////////////////////////////////////////////////////////////////////
// CustomRS.H
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

接下來，實作`GetColumnInfo`函式中*自訂*RS.cpp，如下列程式碼所示。

`GetColumnInfo` 檢查第一次，看看是否將 OLE DB 屬性`DBPROP_BOOKMARKS`設定。 要取得其屬性，`GetColumnInfo`會使用指標 (`pRowset`) 的資料列集物件。 `pThis`指標表示類別，用於建立資料列集，這是一個類別的屬性對應的儲存位置。 `GetColumnInfo` 類型轉換`pThis`指標`RCustomRowset`指標。

若要檢查`DBPROP_BOOKMARKS`屬性，`GetColumnInfo`會使用`IRowsetInfo`介面，您可以藉由呼叫取得`QueryInterface`上`pRowset`介面。 或者，您可以使用 ATL [CComQIPtr](../../atl/reference/ccomqiptr-class.md)方法改為。

```cpp
////////////////////////////////////////////////////////////////////
// CustomRS.cpp
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

此範例會使用靜態陣列以保存的資料行資訊。 如果取用者不想書籤資料行，在陣列中的一個項目未使用。 若要處理的資訊，您會建立兩個陣列巨集： ADD_COLUMN_ENTRY 和 ADD_COLUMN_ENTRY_EX。 ADD_COLUMN_ENTRY_EX 採用額外的參數，*旗標*，也就是如果您指定的書籤資料行所需。

```cpp
ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD),
   DBTYPE_BYTES, 0, 0, GUID_NULL, CAgentMan, dwBookmark,
   DBCOLUMNFLAGS_ISBOOKMARK)
```

您現在可以編譯並執行增強的提供者。 若要測試提供者，請修改中所述的測試消費者[實作簡單消費者](../../data/oledb/implementing-a-simple-consumer.md)。 提供者執行測試的取用者。 驗證，測試取用者的適當字串從提供者擷取當您按一下 [**執行**按鈕**測試消費者**] 對話方塊。

## <a name="see-also"></a>另請參閱

[增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)<br/>
