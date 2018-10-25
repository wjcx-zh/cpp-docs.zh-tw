---
title: 存取子和資料列集 |Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3632a99e09104cba2916b3da7230dd2769b78b42
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066736"
---
# <a name="accessors-and-rowsets"></a>存取子和資料列集

若要設定及擷取資料，OLE DB 樣板會使用存取子和資料列集，透過[CAccessorRowset](../../data/oledb/caccessorrowset-class.md)類別。 這個類別可以處理不同類型的多個存取子。

## <a name="accessor-types"></a>存取子類型

所有存取子是衍生自[CAccessorBase](../../data/oledb/caccessorbase-class.md)。 `CAccessorBase` 提供參數和資料行繫結。

下圖顯示存取子類型。

![存取子的型別](../../data/oledb/media/vcaccessortypes.gif "vcaccessortypes")<br/>
存取子類別

- [CAccessor](../../data/oledb/caccessor-class.md)使用這個存取子，當您在設計階段知道資料庫來源的結構。 `CAccessor` 以靜態方式將資料庫的記錄，其中包含緩衝區，繫結至資料來源。

- [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)時您不知道資料庫的結構，在設計階段使用這個存取子。 `CDynamicAccessor` 呼叫`IColumnsInfo::GetColumnInfo`取得資料庫資料行資訊。 它會建立並管理存取子和緩衝區。

- [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md)使用這個存取子來處理未知的命令類型。 當您準備命令時`CDynamicParameterAccessor`可以取得參數資訊，從`ICommandWithParameters`介面，如果提供者支援`ICommandWithParameters`。

- [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md)， [CDynamicStringAccessorA](../../data/oledb/cdynamicstringaccessora-class.md)，以及[CDynamicStringAccessorW](../../data/oledb/cdynamicstringaccessorw-class.md)您不了解資料庫結構描述時使用這些類別。 `CDynamicStringAccessorA` 擷取資料視為 ANSI 字串。`CDynamicStringAccessorW`會以 Unicode 字串擷取資料。

- [CManualAccessor](../../data/oledb/cmanualaccessor-class.md)與這個類別中，您可以使用任何您想提供者可以將類型轉換的資料類型。 它會處理結果資料行和命令參數。

下表摘要說明中的 OLE DB 範本存取子類型的支援。

|存取子類型|動態|控制代碼參數|緩衝區|多個存取子|
|-------------------|-------------|--------------------|------------|------------------------|
|`CAccessor`|否|是|使用者|是|
|`CDynamicAccessor`|是|否|OLE DB 樣板|否|
|`CDynamicParameterAccessor`|是|是|OLE DB 樣板|否|
|`CDynamicStringAccessor[A,W]`|是|否|OLE DB 樣板|否|
|`CManualAccessor`|是|是|使用者|是|

## <a name="rowset-types"></a>資料列集的類型

OLE DB 範本都支援三種類型的資料列集 （請參閱上圖中）： 單一資料列集 (藉由將[CRowset](../../data/oledb/crowset-class.md))，大量資料列集 (藉由將[CBulkRowset](../../data/oledb/cbulkrowset-class.md))，和陣列 （實作的資料列集藉由[CArrayRowset](../../data/oledb/carrayrowset-class.md))。 單一資料列集提取單一資料列控制代碼`MoveNext`呼叫。 大量資料列集可以擷取多個資料列控制代碼。 陣列資料列集是可以使用陣列語法來存取的資料列集。

下圖顯示的資料列集的類型。

![RowsetType 圖形](../../data/oledb/media/vcrowsettypes.gif "vcrowsettypes")<br/>
資料列集類別

[結構描述資料列集](../../data/oledb/obtaining-metadata-with-schema-rowsets.md)不存取資料中的資料存放區，但改為存取資料存放區，稱為中繼資料的相關資訊。 結構描述資料列通常用於在資料庫結構不編譯時期已知和必須在執行階段取得的情況。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)