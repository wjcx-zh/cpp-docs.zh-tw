---
title: 擷取資料
ms.date: 10/19/2018
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
ms.openlocfilehash: 919eb059f5d3f29d491bf7a6598b0c77163bd783
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87184640"
---
# <a name="fetching-data"></a>擷取資料

在您開啟資料來源、會話和資料列集物件之後，就可以提取資料。 根據您所使用的存取子類型而定，您可能需要系結資料行。

## <a name="to-fetch-data"></a>若要提取資料

1. 使用適當的**開啟**命令來開啟資料列集。

1. 如果您使用 `CManualAccessor` ，請系結輸出資料行（如果尚未這麼做）。 下列範例取自[DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)範例。 若要系結資料行，請呼叫 `GetColumnInfo` ，然後使用系結建立存取子，如下列範例所示：

    ```cpp
    // From the DBViewer Sample CDBTreeView::OnQueryEdit
    // Get the column information
    ULONG ulColumns       = 0;
    DBCOLUMNINFO* pColumnInfo  = NULL;
    LPOLESTR pStrings      = NULL;
    if (rs.GetColumnInfo(&ulColumns, &pColumnInfo, &pStrings) != S_OK)
        ThrowMyOLEDBException(rs.m_pRowset, IID_IColumnsInfo);
    struct MYBIND* pBind = new MYBIND[ulColumns];
    rs.CreateAccessor(ulColumns, &pBind[0], sizeof(MYBIND)*ulColumns);
    for (ULONG l=0; l<ulColumns; l++)
    rs.AddBindEntry(l+1, DBTYPE_STR, sizeof(TCHAR)*40, &pBind[l].szValue, NULL, &pBind[l].dwStatus);
    rs.Bind();
    ```

1. 撰寫 **`while`** 迴圈來取得資料。 在迴圈中，呼叫 `MoveNext` 以推進游標，並針對 S_OK 測試傳回值，如下列範例所示：

    ```cpp
    while (rs.MoveNext() == S_OK)
    {
        // Add code to fetch data here
        // If you are not using an auto accessor, call rs.GetData()
    }
    ```

1. 在 **`while`** 迴圈內，您可以根據存取子類型來提取資料。

   - 如果您使用[CAccessor](../../data/oledb/caccessor-class.md)類別，您應該會有包含資料成員的使用者記錄。 您可以使用這些資料成員來存取資料，如下列範例所示：

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members directly. In this case, m_nFooID
            // is declared in a user record that derives from
            // CAccessor
            wsprintf_s("%d", rs.m_nFooID);
        }
        ```

   - 如果您使用 `CDynamicAccessor` 或 `CDynamicParameterAccessor` 類別，您可以使用存取函數和來提取資料 `GetValue` `GetColumn` ，如下列範例所示。 如果您想要判斷您所使用的資料類型，請使用 `GetType` 。

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the dynamic accessor functions to retrieve your data.

            ULONG ulColumns = rs.GetColumnCount();
            for (ULONG i=0; i<ulColumns; i++)
            {
                rs.GetValue(i);
            }
        }
        ```

   - 如果您使用 `CManualAccessor` ，則必須指定您自己的資料成員、自行系結，並直接存取它們，如下列範例所示：

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members you specified in the calls to
            // AddBindEntry.

            wsprintf_s("%s", szFoo);
        }
        ```

## <a name="see-also"></a>另請參閱

[使用 OLE DB 取用者範本](../../data/oledb/working-with-ole-db-consumer-templates.md)
