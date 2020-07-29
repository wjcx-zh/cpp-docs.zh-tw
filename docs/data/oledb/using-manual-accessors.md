---
title: 使用手動存取子
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: b76c6a2d0af404bc526fee8f511320a58ffd86ec
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218282"
---
# <a name="using-manual-accessors"></a>使用手動存取子

處理未知的命令時，有四件事要做：

- 判斷參數

- 執行命令

- 判斷輸出資料行

- 查看是否有多個傳回資料列集

若要使用 OLE DB 取用者範本來執行這些動作，請使用 `CManualAccessor` 類別，並遵循下列步驟：

1. 以 `CCommand` `CManualAccessor` 範本參數的形式開啟物件。

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. 查詢介面的會話 `IDBSchemaRowset` ，並使用 procedure 參數資料列集。 如果 `IDBSchemaRowset` 介面無法使用，請查詢 `ICommandWithParameters` 介面。 呼叫 `GetParameterInfo` 以取得資訊。 如果沒有可用的介面，您可以假設沒有任何參數。

1. 針對每個參數，呼叫 `AddParameterEntry` 以加入參數並加以設定。

1. 開啟資料列集，但將 bind 參數設為 **`false`** 。

1. 呼叫 `GetColumnInfo` 以取得輸出資料行。 使用將 `AddBindEntry` 輸出資料行加入至系結。

1. 呼叫 `GetNextResult` 來判斷是否有更多的資料列集可用。 重複步驟2到5。

如需手動存取子的範例，請參閱 `CDBListView::CallProcedure` [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer)範例中的。

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)
