---
title: 決定使用哪一種存取子
ms.date: 05/09/2019
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
ms.openlocfilehash: d729e2cf5b08ae227d0cc2e4d5ab7f8ac865cdc4
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079648"
---
# <a name="determining-which-type-of-accessor-to-use"></a>決定使用哪一種存取子

您可以在編譯時期或執行階段決定資料列集上的資料類型。

如果您需要在編譯時期決定資料類型，請使用靜態存取子 (例如 `CAccessor`)。

如果您要在執行階段決定資料類型，則使用動態 (`CDynamicAccessor` 或其子系) 或手動存取子 (`CManualAccessor`)。 在這些情況下，您可以呼叫資料列集上的 `GetColumnInfo` 以傳回您可以從中決定類型的資料行繫結資訊。

下表列出消費者範本中提供之存取子的類型。 每個存取子都有優缺點。 根據您的情況，有一種存取子類別應該能符合您的需求。

|存取子類別|繫結|參數|註解|
|--------------------|-------------|---------------|-------------|
|`CAccessor`|使用 COLUMN_ENTRY 巨集建立使用者記錄。 這些巨集會將該記錄中的資料成員繫結至存取子。 建立資料列集時，無法取消繫結資料行。|是，使用 PARAM_MAP 巨集項目。 一旦繫結之後，就無法取消繫結參數。|因為程式碼少而使存取子最快。|
|`CDynamicAccessor`|自動。|否。|如果您不知道資料列集中的資料類型，則很有用。|
|`CDynamicParameterAccessor`|自動，但可以[覆寫](../../data/oledb/overriding-a-dynamic-accessor.md)。|是，如果提供者支援 `ICommandWithParameters`。 參數會自動繫結。|比 `CDynamicAccessor` 慢，但適用於呼叫一般預存程序。|
|`CDynamicStringAccessor[A,W]`|自動。|否。|擷取從資料存放區中存取的資料，作為字串資料。|
|`CManualAccessor`|使用 `AddBindEntry` 手動。|使用 `AddParameterEntry` 手動。|快速；參數和資料行僅繫結一次。 您可以決定要使用之資料的類型 （如需範例，請參閱[DBVIEWER](https://github.com/Microsoft/VCSamples)範例）。需要比 `CDynamicAccessor` 或 `CAccessor`更多的程式碼。 它比較像直接呼叫 OLE DB。|
|`CXMLAccessor`|自動。|否。|擷取從資料存放區中存取的資料，作為字串資料，然後將其格式化為 XML 標記的資料。|

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)