---
title: 存取子和資料列集
ms.date: 11/19/2018
helpviewer_keywords:
- accessors [C++]
- OLE DB consumer templates, rowset support
- OLE DB consumer templates, accessors
- rowsets [C++], accessing
- bulk rowsets
- CAccessorRowset class, accessor types
- single rowsets
- CArrayRowset class, accessors
- CBulkRowset class, accessors
- array rowsets
- CAccessorBase class
- CRowset class, accessors and rowsets
- accessors [C++], rowsets
- rowsets [C++], supported types
ms.assetid: edc9c8b3-1a2d-4c2d-869f-7e058c631042
ms.openlocfilehash: 45180b3ac2647c9f4f5d25a1322794552bd79004
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212377"
---
# <a name="accessors-and-rowsets"></a>存取子和資料列集

若要設定和抓取資料，OLE DB 範本會透過[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)類別來使用存取子和資料列集。 這個類別可以處理不同類型的多個存取子。

## <a name="accessor-types"></a>存取子類型

所有存取子皆衍生自[CAccessorBase](../../data/oledb/caccessorbase-class.md)。 `CAccessorBase` 同時提供參數和資料行系結。

下圖顯示存取子類型。

![存取子類型](../../data/oledb/media/vcaccessortypes.gif "存取子類型")<br/>
存取子類別

- [CAccessor](../../data/oledb/caccessor-class.md)當您在設計階段知道資料庫來源的結構時，請使用此存取子。 `CAccessor` 會以靜態方式將包含緩衝區的資料庫記錄系結至資料來源。

- [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)當您在設計階段不知道資料庫的結構時，請使用此存取子。 `CDynamicAccessor` 會呼叫 `IColumnsInfo::GetColumnInfo` 來取得資料庫資料行資訊。 它會建立和管理存取子和緩衝區。

- [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)使用此存取子來處理未知的命令類型。 當您準備命令時，如果提供者支援 `ICommandWithParameters`，`CDynamicParameterAccessor` 可以從 `ICommandWithParameters` 介面取得參數資訊。

- 當您不知道資料庫架構時， [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)、 [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)和[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)會使用這些類別。 `CDynamicStringAccessorA` 會將資料當做 ANSI 字串來抓取;`CDynamicStringAccessorW` 會以 Unicode 字串的形式抓取資料。

- [CManualAccessor](../../data/oledb/cmanualaccessor-class.md)使用這個類別時，如果提供者可以轉換類型，您就可以使用任何想要的資料類型。 它會處理結果資料行和命令參數。

下表摘要說明 OLE DB 範本存取子類型中的支援。

|存取子類型|動態|處理 params|Buffer|多個存取子|
|-------------------|-------------|--------------------|------------|------------------------|
|`CAccessor`|否|是|User|是|
|`CDynamicAccessor`|是|否|OLE DB 範本|否|
|`CDynamicParameterAccessor`|是|是|OLE DB 範本|否|
|`CDynamicStringAccessor[A,W]`|是|否|OLE DB 範本|否|
|`CManualAccessor`|是|是|User|是|

## <a name="rowset-types"></a>資料列集類型

OLE DB 範本支援三種資料列集（請參閱上圖）：單一資料列集（由[CRowset](../../data/oledb/crowset-class.md)所實）、bulk 資料列集（由[CBulkRowset](../../data/oledb/cbulkrowset-class.md)所實）和陣列資料列集（由[CArrayRowset](../../data/oledb/carrayrowset-class.md)實作為）。 單一資料列集會在呼叫 `MoveNext` 時，提取單一資料列控制碼。 大量資料列集可以提取多個資料列控制碼。 陣列資料列集是可以使用陣列語法來存取的資料列集。

下圖顯示資料列集類型。

![RowsetType 圖形](../../data/oledb/media/vcrowsettypes.gif "RowsetType 圖形")<br/>
資料列集類別

[架構](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)資料列集不會存取資料存放區中的資料，而是會存取資料存放區的相關資訊，稱為中繼資料。 架構資料列集通常用於在編譯時期不知道資料庫結構，而且必須在執行時間取得的情況。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)
