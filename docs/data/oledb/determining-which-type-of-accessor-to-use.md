---
title: 決定要使用的存取子的類型 |Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 591d3a3bee554fd87a8c48aea67611e6cc6e5111
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066380"
---
# <a name="determining-which-type-of-accessor-to-use"></a>決定使用哪一種存取子

在編譯時期或執行階段，您可以判斷資料列集的資料類型。

如果您需要在編譯時期判斷資料類型，請使用靜態存取子 (例如`CAccessor`)。 您可以判斷資料類型，以手動方式或使用**ATL OLE DB 消費者精靈**。

如果您要在執行階段決定的資料類型，請使用 動態 (`CDynamicAccessor`或 子系) 或手動存取子 (`CManualAccessor`)。 在這些情況下，您可以呼叫`GetColumnInfo`上傳回的資料行繫結資訊，從中您可以判斷類型的資料列集。

下表列出提供的消費者範本的存取子的類型。 每個存取子都有其優缺點。 根據您的情況中，一個存取子的型別應能滿足您的需求。

|存取子類別|繫結|參數|註解|
|--------------------|-------------|---------------|-------------|
|`CAccessor`|COLUMN_ENTRY 巨集建立的使用者記錄。 巨集在該記錄中繫結的資料成員，至存取子。 建立資料列集時，則無法解除繫結資料行。|是，使用 PARAM_MAP 巨集項目。 一旦完成繫結參數不得為未繫結的。|因為少量的程式碼最快的存取子。|
|`CDynamicAccessor`|自動的。|否。|如果您不知道的資料列集中的資料型別很有用。|
|`CDynamicParameterAccessor`|自動的但可以是[覆寫](../../data/oledb/overriding-a-dynamic-accessor.md)。|是，如果提供者支援`ICommandWithParameters`。 會自動繫結的參數。|低於`CDynamicAccessor`但適用於呼叫一般的預存程序。|
|`CDynamicStringAccessor[A,W]`|自動的。|否。|擷取從資料存放區，做為字串資料存取的資料。|
|`CManualAccessor`|手動使用`AddBindEntry`。|使用手動`AddParameterEntry`。|快速;參數和資料行繫結一次。 您決定要使用資料的類型。 (請參閱[DBVIEWER](https://github.com/Microsoft/VCSamples)範例的範例。)需要更多的程式碼比`CDynamicAccessor`或`CAccessor`。 它會比較像直接呼叫 OLE DB。|
|`CXMLAccessor`|自動的。|否。|擷取從資料存放區，做為字串資料存取的資料，並將其格式化為 XML 標記的資料。|

## <a name="see-also"></a>另請參閱

[使用存取子](../../data/oledb/using-accessors.md)