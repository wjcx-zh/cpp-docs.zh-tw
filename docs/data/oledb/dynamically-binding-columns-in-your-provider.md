---
title: 在提供者內動態繫結資料行
ms.date: 11/04/2016
helpviewer_keywords:
- columns [C++], dynamic column binding
- dynamic column binding
- providers [C++], dynamic column binding
ms.assetid: 45e811e3-f5a7-4627-98cc-bf817c4e556e
ms.openlocfilehash: 3eee52004e1418b3e756a78c8c2a04040d0bd7ff
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501854"
---
# <a name="dynamically-binding-columns-in-your-provider"></a>在提供者內動態繫結資料行

請確定您真的需要動態資料行系結。 您可能會因為下列原因而需要它：

- 未在編譯時期定義您的資料列集資料行。

- 您支援的專案（例如加入資料行的書簽）。

## <a name="to-implement-dynamic-column-binding"></a>若要執行動態資料行系結

1. `PROVIDER_COLUMN_MAP`從您的程式碼中移除任何。

1. 在 [使用者記錄] (您的結構) 中，新增下列宣告：

    ```cpp
    static ATLCOLUMNINFO* GetColumnInfo(void* pThis, ULONG* pcCols);
    ```

1. 執行 `GetColumnInfo` 函數。 此函數會配置資訊的儲存方式。 您可能需要取得此函數的屬性或其他資訊。 您可能會想要建立類似于 [COLUMN_ENTRY](./macros-and-global-functions-for-ole-db-consumer-templates.md#column_entry) 宏的宏，以新增您自己的資訊。

   下列範例顯示函式 `GetColumnInfo` 。

    ```cpp
    // Check the property flag for bookmarks, if it is set, set the zero
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
          ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0, sizeof(DWORD), DBTYPE_BYTES,
             0, 0, GUID_NULL, CAgentMan, dwBookmark, DBCOLUMNFLAGS_ISBOOKMARK)
          ulCols++;
       }
    }

    // Next, set up the other columns.
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

## <a name="see-also"></a>另請參閱

[使用 OLE DB 提供者範本](../../data/oledb/working-with-ole-db-provider-templates.md)
