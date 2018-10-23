---
title: 正在擷取資料 |Microsoft Docs
ms.custom: ''
ms.date: 10/19/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data [C++], fetching
- rowsets [C++], fetching
- fetching
- OLE DB consumer templates [C++], fetching data
ms.assetid: b07f747f-9855-4f27-a03d-b1d5b10fa284
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4f0467d322242bb222e5365b45a57e1aa2fe2943
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807467"
---
# <a name="fetching-data"></a>擷取資料

開啟資料來源、 工作階段和資料列集物件之後，您可以擷取資料。 根據您使用的存取子的類型，您可能需要繫結資料行。

## <a name="to-fetch-data"></a>若要擷取資料

1. 開啟使用適當的資料列集**開啟**命令。

1. 如果您使用`CManualAccessor`，繫結之輸出資料行，如果您還尚未這麼做。 下列範例取自[DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)範例。 若要繫結資料行，呼叫`GetColumnInfo`，然後再建立存取子繫結，如下列範例所示：

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

1. 撰寫**雖然**迴圈來擷取資料。 在迴圈中，呼叫`MoveNext`演進資料指標，測試對 s_ok 時，傳回的值，如下列範例所示：

    ```cpp
    while (rs.MoveNext() == S_OK)
    {
        // Add code to fetch data here
        // If you are not using an auto accessor, call rs.GetData()
    }
    ```

1. 內**雖然**迴圈中，您可以根據您的存取子類型擷取資料。

   - 如果您使用[CAccessor](../../data/oledb/caccessor-class.md)類別，您應該有包含資料成員的使用者記錄。 下列範例所示，您可以存取您的資料，使用那些資料成員：

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members directly. In this case, m_nFooID
            // is declared in a user record that derives from
            // CAccessor
            wsprintf_s("%d", rs.m_nFooID);
        }
        ```

   - 如果您使用`CDynamicAccessor`或是`CDynamicParameterAccessor`類別，您可以使用存取函式擷取資料`GetValue`和`GetColumn`，如下列範例所示。 如果您想要判斷資料類型使用，請使用`GetType`。

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

   - 如果您使用`CManualAccessor`，您必須指定您自己的資料成員、 繫結，並直接存取它們，如下列範例所示：

        ```cpp
        while (rs.MoveNext() == S_OK)
        {
            // Use the data members you specified in the calls to
            // AddBindEntry.

            wsprintf_s("%s", szFoo);
        }
        ```

## <a name="see-also"></a>另請參閱

[使用 OLE DB 消費者範本](../../data/oledb/working-with-ole-db-consumer-templates.md)
